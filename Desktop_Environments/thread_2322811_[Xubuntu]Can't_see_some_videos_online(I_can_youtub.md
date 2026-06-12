---
title: "[Xubuntu]Can't see some videos online(I can youtube but no others)"
date: 2016-04-30
forum: Desktop Environments
---

### Post by david517 on 2016-04-30
I've tried to install flash player but I can't ( I am new on linux) and I tried to install pepper flash with the console, but I think there's an error or something, because nothing changes.
When I see YouTube, there's no problem, but when I want to see a film or some series, the media players don't run, they say I need to have the necessary complement.
I tried to search pepper flash or something on the software store, but I didn't found it ( I don't know if it's only on ubuntu store, or it was erased from markets or something...)

---

### Post by egeezer on 2016-04-30
If you have Synaptic, you can find the approved version of flash player by searching for flash.  If Synaptic is not available in your System menu (it really should be!), you can get it from:
```
sudo apt-get synaptic
```
As simple as that!

---

### Post by ajgreeny on 2016-04-30
It is impossible to give you an answer without more info on the sites, with links, that you can not get to play, the browser you use and the version of flash, if any that you already have. Youtube no longer needs flash as it can use html5, but many sites do still need Adobe flash.

I suspect it may be a DRM type of problem, similar to the netflix problem many users see, where Chrome will play videos without added extensions, but chromium needs extras.

I have a problem here in the UK playing Channel-5 TV which is related to this requirement for DMR enabled browsers; it seems there is no solution for that and your problem may be the same.

---

### Post by $yl9pAR%t on 2016-04-30
Google Chrome is bundled with pepper flash, no need to install it. If you want to install flash plugin for FF run in terminal:

```
sudo apt install flashplugin-installer
```

Before you will do above, you can check if you have already got this plugin installed running this command:

```
apt-cache policy flashplugin-installer
```

Perhaps these sites you have mentioned need Silverlight?

---

### Post by david517 on 2016-04-30
I was trying to see videos on animeflv.net, but I can't, I was using Chrominium, but now I tried to use Firefox, and now It works, I think that maybe pepper flash or something that I've tried to install too see the videos on chrominium have helped for see them on Firefox, so better I use Firefox for now for not to have these problems anymore.
Whatever, I've installed synaptics as you said, and the flashplugin, so thank you, now I think I won't have more problems with this :D

---

