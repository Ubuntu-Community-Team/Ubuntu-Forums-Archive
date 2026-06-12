---
title: "Video Game Console Recordings"
date: 2011-05-22
forum: Gaming &amp; Leisure
---

### Post by Admiral5264 on 2011-05-22
My friend and I make Let's Play videos for YouTube and I manage the actual recording and editing of the videos. I'm stuck with Windows because of this. I can get used to using a replacement for Sony Vegas 10, but I need to get our capture cards working. We currently have a Hauppauge Colossus Model # 01414 PCI-Express x1 capture card, as well as an older Dazzle DVC100. I have tried a few attempts with the Dazzle, but with no avail. I would like to get these working, and want to know how to do that. I should also mention I will be using Ubuntu 11.04 as well as Linux Mint 10, soon to be LM 11. I understand they are basically the same OS, but feel it's best to provide more information than less. :) Essentially, I want to know if it would be a simple matter of using console commands or if I would have to learn, then perform a kernel compile. If anyone with information on this could help me, that would be great. Thanks.

---

### Post by HolgerB on 2011-05-23
So your question is initially how to get a Hauppauge Colossus running under a recent Ubuntu based distro ?
:confused:

Edit: I checked out Linux support for the Colossus and it seems to be pretty non-existent. In regard to capturing game video on Linux you might be better off with ffmpeg's X11 recording capabilities. This works perfectly. Of course for bigger resolutions and demanding games you should consider a more beefy system with dual/quad core.

---

### Post by mrbandersnatch on 2011-05-23
Just to chime in here - Admiral is correct, there is currently no support for the Colossus which is annoying since the HD-PVR drivers were available more or less at launch. I can't even find any groups who are working on support for this.

You should have better luck with the dazzle - it is supported (check if you have /dev/video0 with the adaptor plugged in) but I'm unfamiliar with the steps required to get it working - sadly though, with the dazzle you will be restricted to SD recordings which are....poor to say the least.

---

### Post by Admiral5264 on 2011-05-24
> **mrbandersnatch said:**
> Just to chime in here - Admiral is correct, there is currently no support for the Colossus which is annoying since the HD-PVR drivers were available more or less at launch. I can't even find any groups who are working on support for this.

You should have better luck with the dazzle - it is supported (check if you have /dev/video0 with the adaptor plugged in) but I'm unfamiliar with the steps required to get it working - sadly though, with the dazzle you will be restricted to SD recordings which are....poor to say the least.

Well, I suppose that means that I am stuck with Windows until there becomes a suitable replacement that is compatible under Linux. Thank you for your help mrbandersnatch, and you as well HolgerB. If anyone is interested in seeing what I actually do, the URL is my signature.

---

### Post by BuntuNooob on 2011-07-01
I found a tutorial on youtbe that might help. 
 
[http://youtu.be/ijz-OWYsOqE](http://youtu.be/ijz-OWYsOqE)

---

### Post by Admiral5264 on 2011-07-01
> **BuntuNooob said:**
> I found a tutorial on youtbe that might help. 
 
[http://youtu.be/ijz-OWYsOqE](http://youtu.be/ijz-OWYsOqE)

Thanks for posting this. If only they had one for the colossus haha. That would make my day.

---

