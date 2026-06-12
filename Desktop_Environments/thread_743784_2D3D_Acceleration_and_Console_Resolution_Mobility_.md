---
title: "2D/3D Acceleration and Console Resolution Mobility Radeon 9700"
date: 2008-04-03
forum: Desktop Environments
---

### Post by rickatnight11 on 2008-04-03
Well, in my attempt to get better (and by better I mean anything more than 1fps) out of CS:S in Wine I have injured my Gnome performance.  I originally tried [this]("http://ubuntuforums.org/showthread.php?t=580748&highlight=ati+mobility+9700") thread which got desktop effects working wonderfully.  Native games like Tux Racer and America's Army ran just fine, but I got terrible performance in Wine.  I tried installing the driver from ATI's website, and upon reinstall I lost my supported resolutions.  I disabled and then reenabled the Restricted ATI Driver, and then rebooted again which got me my resolution back, but lost all 2D/3D acceleration.  Desktop effects are extremely choppy and something is obviously not right.   Can anyone help me get my Mobility Radeon 9700 configured properly again?

Another issue that may be related and might certainly hinder this process is that pressing ctrl+alt+f1 to get the console displays only the top left portion of the text with a skewed strange resolution.  How can I fix how the console renders the screen?  Attached is a picture of what it looks like.  Thanks in advance!

[ATTACH]64789[/ATTACH]

---

### Post by warp99 on 2008-04-04
You most likely need to remove any of the old files that the installer from ATI left behind. Here is a link on how to do that:

[http://www2.ati.com/drivers/linux/linux_8.24.8.html#179310](http://www2.ati.com/drivers/linux/linux_8.24.8.html#179310)

Then once this is done reinstall the packages for the restricted ATI drivers from the repositories:

```
sudo apt-get install --reinstall xorg-driver-fglrx linux-restricted-modules-generic 
```

here is guide that can help you after you've taken these steps if there are problems:

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

### Post by rickatnight11 on 2008-04-04
Great links, warp99.  Thanks so much.  I'll let you know how it goes.  Do you know if it will fix the console resolution?  I think I had that issue even when the drivers were working previously.

---

### Post by rickatnight11 on 2008-04-04
Hurray!  Desktop effects are back!  Thanks so much.  My console still is all out of whack like above though.  Any ideas on how to fix that?

---

### Post by warp99 on 2008-04-04
Sure that's an easy fix. just do the following:

```
sudo gedit /etc/usplash.conf
```

Check to make sure that's the resolution you would like. If that's what you want just exit, if not change it and save the file. Then issue the following:

```
sudo dpkg-reconfigure usplash
```

This will generate a new initrd.img file setting the resolution for the splash screen and your bash sessions.

Edit:

If you want better performance with Wine make sure you have the latest version. You can get deb files directly [here.]("http://www.winehq.org/site/download-deb") Just follow the directions to install the repositories and viola, some fresh Wine.

---

### Post by rickatnight11 on 2008-04-04
You are the *man*, Warp.  My Terminal looks normal!  I did install the latest version of Wine, however, and I'm still getting really poor performance.  When I start Counter-Strike Source from the Steam menu, it do get this error:

[IMG]http://techdocrx.com/images/Counter-Strike%20Source.jpg[/IMG]

Is this normal, or could this have to do with my 1fps performance?

---

### Post by warp99 on 2008-04-04
Hmm... according to Codeweavers, the commercial version of Wine, Counter-Strike Source only works with Steam:

[http://www.codeweavers.com/compatibility/browse/name/?app_id=2036](http://www.codeweavers.com/compatibility/browse/name/?app_id=2036)

[http://www.steampowered.com/v/index.php](http://www.steampowered.com/v/index.php)

Sine Wine and Codeweavers use the same codebase compatibility in one program in general means compatibility in the other. They both function pretty much the same with the difference being Codeweavers has some additional GUI dialogs and setup tools. Hope this answers your question.

---

### Post by rickatnight11 on 2008-04-04
Well I have been using Steam.  That's where that error comes from above when I launch CS:S from the Steam menu.

---

### Post by warp99 on 2008-04-05
Check the forums over at Codeweavers and do a search for steam here on this board. I think there are some forums over at winehq.com, so check there also.

If you can't find anything start a new thread over in gaming & leisure. Sorry if I couldn't help you anymore.

---

### Post by rickatnight11 on 2008-04-05
Please don't apologize, you have been a great help.  I really appreciate it.

---

