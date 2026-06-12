---
title: "dolphin mount smb-share on the fly (gvfs-like for kde)"
date: 2009-08-18
forum: Desktop Environments
---

### Post by tobias81 on 2009-08-18
Hi there,

I'm totally new to KDE but I've been using Gnome / Ubuntu for quite a few years now... so I'm trying to switch to KDE but one of the major drawbacks compared to gnome is that dolphin doesn't seem to be able to mount network shares on the fly like nautilus does using the gvfs service

What I'm trying to do is to open a file (i.e. an movie .avi whatever) direktly over the network share without downloading it first.
I have file server with movies, mp3s etc on it and I connect to it via Samba.
In gnome I simply had to navigate to my movie folder and double-click the avi and it would play right away in any movie player of my choice (cause gvfs would mount it temporarely behind the schenes and nautilus didn't even really know about it being remote)
in dolphin however I can navigate to the share, find my file (that all works great) but when I try to open the actual avi file dolphin starts to download it first... 

basically I'm looking for a gvfsd clone for kde/dolphin

---

### Post by krazyd on 2009-08-18
KIO is the gvfs equivalent for kde.

If you right-click the file in dolphin > open with... > Dragon Player, then the file will stream. This also works in Kaffeine (another KDE player).

Alternatively, if you would like to mount the remote shares transparently so that you can view videos in vlc, smplayer etc., you need to install smb4k.
```
sudo apt-get install smb4k
```
Then run smb4k, browse to the folder you want and click it. It's now mounted and visible in the 'Mounted Shares' tab in smb4k, or in ~/smb4k/

I agree, this could be easier and hopefully it'll be incorporated into dolphin eventually.

---

### Post by tobias81 on 2009-08-19
thanks, well in the meantime I actually found smb4k myself ... well let's just say it does the job but it could really be more implemented into dolphin... 

the other possibility you mentioned: right click -> open with ... -> dragon/kaffein player works only halfways for me ... 
basically it does not try to download the file and immediatly launches the player, which is good... but the file does not play - dragonplayer just sits there doing nothing (even when I click play and even though "play file" lists the correct file in the playlist etcetc), 
and Kaffeine trys to go out and install the right codec but than stops with an error saying the codec is already installed. movie still not playing. (when I download the movie locally it works just fine)... all a little weird...

in any case I can go back to smb4k which I guess works it's just a little annoying always having to mount it manually first etc. but whatever, could be worse...

---

### Post by NTolerance on 2009-08-28
> **krazyd said:**
> KIO is the gvfs equivalent for kde.

If you right-click the file in dolphin > open with... > Dragon Player, then the file will stream. This also works in Kaffeine (another KDE player).


I'm running KDE 4.3 from a PPA and this doesn't work for me unfortunately.  Dragon Player and KMPlayer just give me a black screen and do nothing when I press the "play" button.

---

