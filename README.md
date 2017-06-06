# VIMediaCache

[中文说明](https://mp.weixin.qq.com/s/v1sw_Sb8oKeZ8sWyjBUXGA)

AVPlayer 音视频缓存方案

已知问题

    播到一半声音停了，视频正常播

    比较低概率，在美拍上测试时有短视频会出现

    弱网下一直loading到超时，但是文件都是已经下载好了

    没有调用 AVPlayer 的 play 在弱网下会造成，AVPlayerLayer 一直无法达到 readyForDisplay 的情况
    
    以上问题暂时没有很好的解决方案，因为 ResourceLoader 的实现只能做到控制缓存，但 AVPlayer 内的具体实现机制并不清楚，
    在缓存没有问题的情况下出现问题，很难去追根溯源寻找问题的根本原因。

Cache media file while play media using AVPlayerr.

VIMediaCache use AVAssetResourceLoader to control AVPlayer download media data.

### CocoaPods

`pod 'VIMediaCache'`

### Usage

    NSURL *url = [NSURL URLWithString:@"https://mvvideo5.meitudata.com/571090934cea5517.mp4"];
    
    VIResourceLoaderManager *resourceLoaderManager = [VIResourceLoaderManager new];
    self.resourceLoaderManager = resourceLoaderManager;
    
    AVPlayerItem *playerItem = [resourceLoaderManager playerItemWithURL:url];
    AVPlayer *player = [AVPlayer playerWithPlayerItem:playerItem];

### Contact

vvitozhang@gmail.com

### License

MIT
