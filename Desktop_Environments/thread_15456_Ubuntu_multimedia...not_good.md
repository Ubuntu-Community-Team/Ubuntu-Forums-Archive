---
title: "Ubuntu multimedia...not good"
date: 2005-02-14
forum: Desktop Environments
---

### Post by sharkzf6 on 2005-02-14
Multimedia and Ubuntu, the use of these 2 words in the same sentence is starting to sound like an oxymoron. I've stepped back from Hoary to Warty on my main P4 rig due to some issues with Hoary that lead me to believe Warty would be more stable. Performed various updates with synaptic, installed nVidia drivers, even un-installed totem and replaced it with xine which gave me DVD playback. WOW, I thought I was really getting somewhere. To make a long story short, there are so many issues with much of Ubuntu's multimedia, I'm about ready to give up. It's little things like not being able to play .wmv files and have the sound and video both operate correctly. Here's another good one: for some reason my SB live has decided to ignore the master volume control!?  It use to work, but apparently something I did or installed changed that. At least it works to some degree, I never did get my Audigy LS to work even though ALSA and all libraries were up to date. The support is supposedly built-in on ALSA versions 1.0.6a and higher, but I never got any sound out of the damn thing. It wasn't even listed under the ALSA mixer...duh. There have been some bright spots. I got the nVidia drivers loaded no problem, something which proved near impossible with Debian Sarge despite the fact I know it can be done. I tried several procedures but none worked for me (another Linux failure  :( ). I even got DooM 3 to load and play perfectly with Ubuntu, even the sound...probably the highlight of my Linux experience so far :).  Ya know, I'm no dummy when it comes to computers but Linux sure has a way of making you feel dumb. All my hardware and programs work so well in Windows XP...hmmm...I got to do some serious thinking...

---

### Post by rkn on 2005-02-14
Yes!
I deal with the same thing every week doing computer support with senior citizens (most of them are using m$ XP).  It can be very frustrating at times, but as you learn to administer your system it will become much easier.   Think of how much more you know than you did a few month ago.  Keep trying, and you will soon be able to make more efficent use of your computer.   The important thing is not to give up!

Bob

---

### Post by sharkzf6 on 2005-02-14
[QUOTE=rkn]Yes!
I deal with the same thing every week doing computer support with senior citizens (most of them are using m$ XP).  It can be very frustrating at times, but as you learn to administer your system it will become much easier.   Think of how much more you know than you did a few month ago.  Keep trying, and you will soon be able to make more efficent use of your computer.   The important thing is not to give up!

Bob[/QUOTE] Interesting. Actually, I'm not giving up, I'm still using Warty on my old P3 rig where it seems to be quite at home. At this point, I'm installing Debian Sarge back on my P4 rig. I figure, if Linux is going to make me jump through hoops, I might as well learn something...Ubuntu is a little boring when you look at it this way  ;)
cheers

BTW - something I failed to mention in my previous post, Ubuntu seems a little sluggish compared to Debian. I'm sure it's not the nVidia drivers, it's that way using the standard vesa drivers or the nVidia drivers. Wierd!?

---

### Post by ritger on 2005-02-14
[QUOTE=sharkzf6]BTW - something I failed to mention in my previous post, Ubuntu seems a little sluggish compared to Debian. I'm sure it's not the nVidia drivers, it's that way using the standard vesa drivers or the nVidia drivers. Wierd!?[/QUOTE]
Not weird, i noticed this too. I have a GeForce 2 (VIA KT400 mobo), and was experiencing lock-ups (about twice a day). Turns out to be the agpgart driver distributed with the Ubuntu default kernel. After changing the XFree86-4 file to use NvAGP and removing the agpgart module from the kernel (i know, ugly solution) things sped up significantly and became stable again. Something worth trying?

As for the wmv support, if you can't get that to work in Ubuntu it probably won't work in debian either. I needed to install the win32 codec pack from mplayer and point xine to use it. After that i can even play .rm files. Also, replacing totem-gstreamer with totem-xine made totem play all my media files the way they should. 

Hope this helps.

---

### Post by sharkzf6 on 2005-02-14
[QUOTE=ritger]Not weird, i noticed this too. I have a GeForce 2 (VIA KT400 mobo), and was experiencing lock-ups (about twice a day). Turns out to be the agpgart driver distributed with the Ubuntu default kernel. After changing the XFree86-4 file to use NvAGP and removing the agpgart module from the kernel (i know, ugly solution) things sped up significantly and became stable again. Something worth trying?

As for the wmv support, if you can't get that to work in Ubuntu it probably won't work in debian either. I needed to install the win32 codec pack from mplayer and point xine to use it. After that i can even play .rm files. Also, replacing totem-gstreamer with totem-xine made totem play all my media files the way they should. 

Hope this helps.[/QUOTE] Hmmm....well I installed the w32codec and did replace totem-gstreamer with totem-xine as well as installing xine. I didn't point xine to the codec though...how do you do that?

---

### Post by sharkzf6 on 2005-02-14
[QUOTE=sharkzf6]Hmmm....well I installed the w32codec and did replace totem-gstreamer with totem-xine as well as installing xine. I didn't point xine to the codec though...how do you do that?[/QUOTE] Oh yeah, I knew about the agp thing...makes sense. Right now I've got Debian Sarge up and running, in the process of setting things up. It's definitely faster and, all the sound works great. All I have to do is figure out how to get the nVidia 66.29 drivers installed without pulling my hair out. Probably end up building a new kernel...yikes!!!

---

### Post by sharkzf6 on 2005-02-15
[QUOTE=ritger]<snip>...As for the wmv support, if you can't get that to work in Ubuntu it probably won't work in debian either. I needed to install the win32 codec pack from mplayer and point xine to use it. After that i can even play .rm files. Also, replacing totem-gstreamer with totem-xine made totem play all my media files the way they should. 

Hope this helps.[/QUOTE] Update - I have Debian Sarge installed and have installed the w32codecs for Totem movie player. It works great! It did not work with Ubuntu. This leads me to believe Ubuntu really *does* have issues with multimedia specific to the distro, unfortunate. I was really juiced about Ubuntu when I first started using it. Turns out, the only good thing about it was the simple install of the nVidia 66.29 driver package.  :(

---

### Post by ritger on 2005-02-16
[QUOTE=sharkzf6]Hmmm....well I installed the w32codec and did replace totem-gstreamer with totem-xine as well as installing xine. I didn't point xine to the codec though...how do you do that?[/QUOTE]

I installed xine-ui as well, it has some more advanced options to configure. On one of the pages (i think it's codecs) you can specify the location for the win32 codecs. This writes out the xine config to .xine/ in your home dir ... and i ***ume this is what is being used by totem-xine. Just a hunch though, but it works for me.

---

### Post by imdeemvp on 2005-02-16
I got xmms, totem, mplayer and mplayerplug-in working in my first installation.

---

### Post by sharkzf6 on 2005-02-16
> **ritger]I installed xine-ui as well, it has some more advanced options to configure. On one of the pages (i think it's codecs) you can specify the location for the win32 codecs. This writes out the xine config to .xine/ in your home dir ... and i ***ume this is what is being used by totem-xine. Just a hunch though, but it works forme.[/QUOTE] Interesting. Like I said, I'm using Debian Sarge now and **it** works perfectly, all my multimedia, nVidia driver, networking, all of it - so I can't look at the settings you're talking about since I no longer have it installed. I'm glad it worked for you though...   said:**
> I got xmms, totem, mplayer and mplayerplug-in working in my first installation. I'm glad you also experienced no problems like ritger...
I realize there are a lot of people that Ubuntu has worked well for and that's a good thing. I was not one of them, and, the real kicker is, Debian runs much faster, Ubuntu is sluggish. Someone speculated it was because Ubuntu uses a plain vanilla AGP driver vs the nVidia flavor, well, so does Debian. Considering my install resides on a 3 gig P4 with 1 gig of RAM and uses an nVidia GF 6800, that's a big deal for me. Cheers.

---

### Post by MetalMusicAddict on 2005-02-16
[QUOTE=sharkzf6]
I realize there are a lot of people that Ubuntu has worked well for and that's a good thing. I was not one of them, and, the real kicker is, Debian runs much faster, Ubuntu is sluggish. Someone speculated it was because Ubuntu uses a plain vanilla AGP driver vs the nVidia flavor, well, so does Debian. Considering my install resides on a 3 gig P4 with 1 gig of RAM and uses an nVidia GF 6800, that's a big deal for me. Cheers.[/QUOTE]
If you use a nVidia driver this isnt a issue right? Only if you stick with the default(install) one.

---

### Post by sharkzf6 on 2005-02-16
[QUOTE=MetalMusicAddict]If you use a nVidia driver this isnt a issue right? Only if you stick with the default(install) one.[/QUOTE]
I don't think it's an issue period. Like I said, I use Debian and it doesn't feel sluggish at all with the default AGP driver. The answer to your question is, if you want to use the nVidia AGP driver, you have to install it separately, it doesn't install with the graphics card driver and people have reported having the problem after the nVidia install, that's why I think there's something else going on. Personally, I wouldn't do it unless you have issues with sluggish behavior. Chances are, if your system does not appear sluggish now, it won't after installing the nVidia graphics card driver either. If it is sluggish now, installing the nVidia drivers probably won't help until you install the nVidia AGP driver.

---

