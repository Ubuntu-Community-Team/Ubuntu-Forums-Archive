---
title: "Inspiron 1525 dvd playback problems"
date: 2008-04-13
forum: Dell  Ubuntu Support
---

### Post by posey on 2008-04-13
I have a new Insprion 1525 (bought with vista, but loaded with ubuntu with the dell iso). It is my sibling's laptop. The purchaser picked the options the ubuntu ones had.

DVD playback is choppy and distorted in vlc; totem won't even play dvds. It's distorted enough that you can't tell what you're watching, but the sound is choppy. libdvdcss2, libdvdread, ubuntu-restricted, and all that stuff is installed so it looks like it should work. The DVD, Sweeney Todd, plays fine on my Gentoo box with vlc. 

I'm not sure what else to do to get it to work. It appears that opengl is on.
It has the Intel video (Mobile GM965/GL960 integrated) using the intel driver (it appears). 

Please help me.

[Screenshot]("http://home.earthlink.net/~pureawesome/dvdplayback.png")

---

### Post by posey on 2008-04-14
No one has any idea?

I've tried all the different video drivers in VLC. Some of them change around the colors on the title screen (which shows up ok), but actually playing the movie still results in a jumbled mess.

I had been thinking video driver, but I just tried another DVD, an older one, and it worked fine. So maybe the problem lies with the codecs?

All the DVD related codecs I could find references about needing to have installed are installed. I used synaptic to install them, so probably nothing odd happened with the actual installs.

I'm not sure what else I should check or mess with.

---

### Post by notwen on 2008-04-15
> It has the Intel video (Mobile GM965/GL960 integrated) using the intel driver (it appears). 

Are you running Compiz?  Enabling the blacklisted Intel X3100 chipset can screw video output for just about all applications, if you do have Compiz running on this and have bypassed the blacklisting then perhaps you can try to change the video output to 'No Xv' and see if that resolves your issue.  Post back and give us more info/updates.  =]

---

### Post by posey on 2008-04-15
No Compiz. It seemed more crippling than cool or useful. 

So it is the x3100. I thought I had seen that somewhere but then couldn't find it again.

Without compiz, is the no Xv video output still something to try? Where is it located?

---

### Post by notwen on 2008-04-15
> **posey said:**
> No Compiz. It seemed more crippling than cool or useful. 

So it is the x3100. I thought I had seen that somewhere but then couldn't find it again.

Without compiz, is the no Xv video output still something to try? Where is it located?

This issue is only introduced when you enable Compiz-Fusion on blacklisted hardware(ie. X3100 chipset), so I don't believe this would be affecting your sibling's machine.  You have the main 3 packages for DVD playback installed, only thing I can think of to try is maybe adding the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo and seeing if that resolves the issue.  You may want to consult other users w/ Inspiron 1525n machines to see if they are having issues as well.  I'm not seeing any browsing over the Dell-Ubuntu sub-forum or any issues posted on Dell's Linux Wiki.  Best of luck and please post back should you find something more.

---EDIT---
If you wish to try the 'No Xv' then you can locate it in VLC's video settings under Video Output or just change it in gstreamer-properties I believe.

---

### Post by posey on 2008-04-15
It does have the Medibuntu repo, I used it to get libdvdcss. I was hoping to avoid strange and dependency related problems by adding the repo.

I've tried all the VLC video output modules. But it could play the Invader Zim DVD just fine, so that says to me it probably isn't video related. 

I was hoping this forum would have people with either the 1525 or the 1525n who would know something. 
This laptop isn't officially a 1525n, but I think it would qualify (aside from the vista key on the bottom).

---

### Post by posey on 2008-04-15
I found patched libdvdread and libdvdnav here: [http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

I installed those and there isn't any change. 

I'm guessing at this point that it's debian/ubuntu codec related. 

Uninstalling and reinstalling the codecs doesn't make a difference either.

I don't think it's video because older DVDs play fine. The DVD itself isn't bad because it plays fine on a Sony DVD player, and on a Gentoo box (64bit, stays updated, nothing special with codecs or anything else). The Gentoo box and the Ubuntu laptop have the same versions of the codecs, so evidently the codecs themselves work and theres just a problem with them on the Ubuntu laptop. 

Anyone have any ideas?

---

### Post by notwen on 2008-04-16
You may want to start a thread in the [Multimedia & Video sub-forum]("http://ubuntuforums.org/forumdisplay.php?f=138") and see if anyone else on a broader spectrum is having similar issues.  I've never had issues w/ DVD playback on my Inspiron 1420n, so I'm baffled.  Wish I could be of more assistance. =\

---

### Post by posey on 2008-04-16
Thank you

---

### Post by pablo180 on 2008-06-27
> **posey said:**
> I found patched libdvdread and libdvdnav here: [http://tobias.rautenkranz.ch/debian/](http://tobias.rautenkranz.ch/debian/)

I installed those and there isn't any change. 

I'm guessing at this point that it's debian/ubuntu codec related. 

Uninstalling and reinstalling the codecs doesn't make a difference either.

I don't think it's video because older DVDs play fine. The DVD itself isn't bad because it plays fine on a Sony DVD player, and on a Gentoo box (64bit, stays updated, nothing special with codecs or anything else). The Gentoo box and the Ubuntu laptop have the same versions of the codecs, so evidently the codecs themselves work and there's just a problem with them on the Ubuntu laptop. 

Anyone have any ideas?

Don't you have LinDVD in your installation? I have the 1525n and that came with LinDVD which plays all DVDs flawlessly. I also have VLC, Totem etc, they play DVDs too but the playback is choppy, pixelated and unwatchable. 

I also find that I cannot encode DVDs with Mencoder either and the resulting video is choppy, pixelated etc.

I assume this is something to do with LinDVD or the codecs that it uses and they interfere with the other players somehow. You may well have the necessary codecs for LinDVD but not LinDVD itself. 

I'd suggest you try and install/get hold of LinDVD as that may solve your problem.

---

### Post by alof8k on 2008-07-04
Hi, 

I just ordered the same laptop the other day (can't wait till it arrives!).  Mines too will include vista which I found to be a better deal for the money (3GB of ram, 250GB HD, Creative Earbuds, integrated 2.0 Megapixel camera, etc). Anyway the issue between the 1525n and the 1525 (vista) is that when you buy the 1525 you get dvd playback via LinDVD which is included part of the package.  Downloading the ISO doesn't give you LinDVD because that's something Dell buys extra and then gives to the 1525n buyers part of their package. 

so the issue is the software.  My only suggestion is to try other software, mainly [MPlayer ]("http://www.mplayerhq.hu/homepage/design7/news.html")which should give you a much better performance and if not MPlayer, then definitely [Xine]("http://www.xinehq.de/").  Totem uses GStreamer and I think that's not the best video playback engine. LinDVD uses something totally different (based on WinDVD).  The other thing you can try is [Ogle ]("http://www.dtek.chalmers.se/groups/dvd/")which is old but sometimes reliable (for some people). 

Hope one of them works! Let us know if you find anything that works...

---

### Post by fedora389 on 2008-07-04
I just got a dell Inspiron with vista installed from dell. I installed ubuntu
gusty and all works fine do not know about wireless just have not had time to mess with as for as dvd playing I have got it to work with dvdread and all that stuff from ubuntu but it will not work with the compiz extras on so what I do  is every time I play a dvd I go to( system-preferences-appearance- then  click on visual effects then click on none that let me watch them hope it works for you. Let us know if you fine a better way or fix to this problem:popcorn:

---

