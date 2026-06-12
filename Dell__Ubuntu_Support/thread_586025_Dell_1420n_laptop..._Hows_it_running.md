---
title: "Dell 1420n laptop... Hows it running?"
date: 2007-10-21
forum: Dell  Ubuntu Support
---

### Post by misfitpierce on 2007-10-21
How is it running with upgrade or fresh install on GUTSY... let me know which you chose to do and how it is running and whats not working... My friend she has one and is having a bit of trouble so im checking to see what is giving headaches... :)

---

### Post by syssyphus on 2007-10-22
mine is running fine... i did an online upgrade... not a fresh install.

---

### Post by dnvikram on 2007-12-20
I have Ubuntu 7.10 (Final) installed on my Inspiron 1420N.I used the Ubuntu 7.10 (Alternate) Install media to install .A fresh install with alternate cd is completely out of the box ,except the webcam which I am trying to get it up and running.

---

### Post by notwen on 2007-12-20
> **dnvikram said:**
> I have Ubuntu 7.10 (Final) installed on my Inspiron 1420N.I used the Ubuntu 7.10 (Alternate) Install media to install .A fresh install with alternate cd is completely out of the box ,except the webcam which I am trying to get it up and running.

When you say 1420n do you mean the pre-installed Dell-buntu Inspiron 1420n or the standard Inspiron 1420?  I only ask because you mention a webcam which was not available on the Ubuntu pre-installed 1420n.  I have a 1420n w/ the Intel X3100 chipset(which Compiz has blacklisted), not the 1420 which offers Nvidia gfx.

---

### Post by dnvikram on 2007-12-20
It is not the one with preinstalled ubuntu..It came with vista.Since,I cant stand vista and am a hard core unix/linux user,I swiped the hdd clean and installed ubuntu 7.10 with alternate cd.Btw,now I got the webcam also working .It was damn simple,installed Cheese and webcam started in a jiffy.

Trust me,1420N + Ubuntu 7.10 = Simply superb

---

### Post by notwen on 2007-12-20
Has anyone w/ the 1420n w/ the Intel X3100 chipset installed the new Gutsy image?  I was wondering if there is any work around to get Compiz to work w/o video issues on it.  I tend to use AWN(which requires composite WM).  I could install the new Gutsy and let Gnome revert back from Compiz to Metacity, but if at all possible I would like ot be running Compiz w/o any issue.

---

### Post by natehall on 2007-12-20
I have a pre-installed Fiesty 1420.  Since I downloaded the Linux Kernel updates its been taking much longer to load and i have to reset the network manager every time I turn the machine on if I want to surf wirelessly (Like now) I tried doing the update awhile back but it it would not load the X window. (Just a terminal , so I just rebooted the factory install.) I've since seen the workarounds to this but I was waiting for the offical Dell version of 7.10 . ( Which I just made a DVD for yeserday) I need to find out if this wipes out the factory partition or replaces it before I mess with that.

---

### Post by dnvikram on 2007-12-22
I see many folks complaining of having to do lot of post install steps to get the gutsy up and running completely on 1420N...To precisely avoid that,I installed gutsy on 1420N using the alternate install cd..If ur having problems,install using the alternate cd..all 1420N(s) obviously have the same hardware..so it shud b truly out of the box and will b that.

---

### Post by natehall on 2007-12-22
> **dnvikram said:**
> I see many folks complaining of having to do lot of post install steps to get the gutsy up and running completely on 1420N...To precisely avoid that,I installed gutsy on 1420N using the alternate install cd..If ur having problems,install using the alternate cd..all 1420N(s) obviously have the same hardware..so it shud b truly out of the box and will b that.Now have  the factory Gutsy 
with a fresh install. The only bugs I've noticed so far is no english help for Gimp or any kind of help for the keyring manager. ( Which still does not seem to do much anyways)

---

### Post by fragos on 2007-12-22
Doing the factory install from the Dell DVD removed the extra partitions that came with the 1420n.  I think that was the right thing to do since I now have a DVD for reinstall anyway and I have no interest in going backward to 7.04.  Install went well and everything works as it did with pre-installed 7.04.

---

### Post by UObean on 2007-12-23
Does that include Compiz?

---

### Post by fragos on 2007-12-23
Compiz is blacklisted for the 1420n because of some incompatibility with the Intel video.  I have heard that the black list can be overridden in a configuration file.  I enjoy Compiz on my 19" wide screen desktop but don't really miss it on a smaller screen.  This URL tells you how to do it [http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

---

### Post by jotacebusta on 2007-12-23
Hi every one,
I have a new Inspiron 1420n, wchich came with ubuntu 7.04. I installed 7.10 using a CD. I cleared the entire hard disk, so I can not restore the "factory settings". I've installed some programs (amarok, texmacs, maxima, latex...)  but I'm having problems with some features:

I can not listen to my music, I have the codecs, amarok knows what to do with the files, but no sound goes out of my laptop. I tried the headphones, with the same result. No other program produces a single noise!

The desktop effects can not be enabled. These were working fine with the original "factory configuration", but it's not the case anymore. I have compiz, compiz-fusion, but I'm not able to enable the effects.

If someone could help, that would be great.

regards,

JC

---

### Post by natehall on 2007-12-24
> **jotacebusta said:**
> Hi every one,
I have a new Inspiron 1420n, wchich came with ubuntu 7.04. I installed 7.10 using a CD. I cleared the entire hard disk, so I can not restore the "factory settings". I've installed some programs (amarok, texmacs, maxima, latex...)  but I'm having problems with some features:

I can not listen to my music, I have the codecs, amarok knows what to do with the files, but no sound goes out of my laptop. I tried the headphones, with the same result. No other program produces a single noise!

The desktop effects can not be enabled. These were working fine with the original "factory configuration", but it's not the case anymore. I have compiz, compiz-fusion, but I'm not able to enable the effects.

If someone could help, that would be great.

regards,

JC

I'm listening to music on my 1420N right now. I just loaded Gutsy on
a few days ago with a clean install. I figure one of those programs you loaded on is the source of your problem, However you might try  looking into the list of known problems on the botton of this link.
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by fragos on 2007-12-24
Sounds like you used a standard Ubuntu 7.10 Live CD.  I also have a 1420n which I upgraded to 7.10 using the Dell created 7.10 DVD.  Dell has gone past making things work and has done things like change mouse preferences to have a touchpad tab.  I recommend downloading the Dell DVD.  The 1420n only comes with an Intel graphics card.  Compiz has blacklisted this chip because of issues of having video output working.  I assume they mean the external monitor port.  There is a configuration work around that disables Compiz from checking it's blacklist.  I haven't tried that but everthing else that worked in 7.04 works with the Dell 7.10.

---

### Post by closey on 2007-12-25
The 1420N can now be configured with either Intel or Nvidia graphics, hence the two different DVD ISOs you can download.

---

### Post by Yoke &amp; Chung on 2007-12-25
> **closey said:**
> The 1420N can now be configured with either Intel or Nvidia graphics, hence the two different DVD ISOs you can download.

Well, I am using the standard 1420 preloaded with Vista and many supposedly non-ubuntu compatible hardware. 

Feisty didn't work, however, Gutsy (standard version downloaded from website) runs like a charm on my Dell 1420 now, all hardwares are automatically configured. So I guessed with a carefully selected linux compatible hardware on 1420n, it should not any problems at all.

---

### Post by clove on 2007-12-27
Installed Gutsy on my 1420n (Intel video) a few weeks ago.  I first installed Gutsy using the official Dell iso file, but wiped that off and ended up installing with the Gutsy alternate CD because I wanted the encryption which the Dell installer doesn't offer.

Everything works fine except sound after waking up from sleep (which I know there's a fix for but haven't gotten around to it yet).

Compiz doesn't work until you do the config file fix, then it works great.  Video plays fine after switching VLC to the X11 video output.  My only disappointment with Compiz is that Google Earth is very choppy (same problem I had with Compiz under Fiesty).

---

### Post by jotacebusta on 2007-12-28
> **clove said:**
> Installed Gutsy on my 1420n (Intel video) a few weeks ago.  I first installed Gutsy using the official Dell iso file, but wiped that off and ended up installing with the Gutsy alternate CD because I wanted the encryption which the Dell installer doesn't offer.

Everything works fine except sound after waking up from sleep (which I know there's a fix for but haven't gotten around to it yet).

Compiz doesn't work until you do the config file fix, then it works great.  Video plays fine after switching VLC to the X11 video output.  My only disappointment with Compiz is that Google Earth is very choppy (same problem I had with Compiz under Fiesty).


So you do not recommend to make the installation using the reintallation DVD from [http://linux.dell.com/files/ubuntu/iso-images/ubuntu-dell-1420n-intelvideo-reinstall.iso](http://linux.dell.com/files/ubuntu/iso-images/ubuntu-dell-1420n-intelvideo-reinstall.iso) 

What do you mean by "encryption"?

I've been trying to download it but my net access is not as fast as i would like. I have gutsy installed from the standard CD.

Sound is working fne. Video almost fine: can play mpeg and mp4 files, buy not DVD's.

Compiz has a strange beheavor: If I enable the special desktop effects, things seem to work fine. But later i loose the top of each window, so there's no more a "minimize", "maximize", or "quit" button... If I disable the effects, everything comes to normality again, and I can re-enable the effects, but later on I have the same problem.

Thanks

JC

---

### Post by fragos on 2007-12-28
I recommend you install package "ubuntu-restricted-extras" which includes libraries to play DVDs as well as all the commonly used restricted packages from the multiverse repository.

---

### Post by jotacebusta on 2007-12-28
Thank you fragos, 

Well, I do have these libraries... This is not the onloy problem when dealing with "video": I cannot see flash animations, despite the fact that I do have the plug-ins installed...

What do I do about compiz?

thanks again

JC

---

### Post by fragos on 2007-12-29
There's a compatability problem with the current Intel driver and Compiz.  This link will tell you how to get it working but there is a trade off.  I like the eye candly on my large screen desktop but decided it isn't that critical with a smaller screen.  I'll wait for the eventual fix.

[http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility](http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility)

---

### Post by jotacebusta on 2008-01-03
Ok. Thanks,

I've re-installed Ubuntu7.10 using the Dell DVD, Now it works fine.

The "patch" for compiz works but just for a little. I cannot produce the problem again, but when working with several windows I just loose the top bar of each window (so no buttons are available). I think I will not use compiz.fusion, at leat for the time beeing.

Did someone tried the old desktop effects libraries? 3d-desktop, or beryl on an inspiron 1420n, with ubuntu preloaded?

---

### Post by fragos on 2008-01-03
Beryl merged back into Compiz.  I'm not sure experimentg with older software will give you a better result.  The problem with the Intel video chip set is understood and reproducable which is a big step toward a solution.

---

### Post by devi on 2008-01-16
Would this same problem cause Second Life to crash? The one thing I'm missing that I want on my factory-installed Feisty Dell 1420n is Second Life...

---

