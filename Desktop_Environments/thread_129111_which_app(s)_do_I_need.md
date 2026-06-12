---
title: "which app(s) do I need?"
date: 2006-02-12
forum: Desktop Environments
---

### Post by ardchoille on 2006-02-12
I have a small collection of DVD's that I'd like to be able to make one copy of each so as not to harm the original, some are dual layer and some are single layer. I have heard about different ways and apps that can copy a DVD but I am a bit confused as to which app to use. I don't mind buying dual layer blank DVD's if I know that the copy from a dual layer to dual layer will actually work, not sure if it's a good idea to shrink a dual layer DVD down to single layer DVD but I am a newbie on this point.

So, which app(s) do I install to be able to make backup copies of the DVD's I purchase **without having to use wine**? dvd::rip? dvdbackup? other?

---

### Post by nalmeth on 2006-02-12
I don't have experience with dual layer DVD's so I can't recommend anything that way. If you'd like to save the DVD on your computer, you can use a program like acidrip to rip it to an avi, the size of your choice (700 megs is default i think).

DVD shrink works well for shrinking DVD's to fit on a DVD-R. It can either give you smaller size VIDEO_TS and AUDIO_TS folders, or give you an ISO image, either of which you can burn to a DVD. I use k3b for the actual burning of the DVD. Sometimes the VIDEO_TS burning doesn't work, so I tend to use ISO's instead. This is just my experience though, it may differ for you.

For DVD shrink, you need the newest version of wine, and the .exe installer for DVD Shrink. DVD shrink will install fine, but there are a couple of things to do to make sure it works. When you have wine and DVD Shrink installed, hit ALT-F2, and type:
winecfg

Go to the applications tab, then hit add application, and find the DVD shrink exe in its folder on your fake C:/ Drive. Add it to the list and select it. Further below in the winecfg menu you can select which windows version to emulate for each program. Pick Windows XP for DVD Shrink. 

Then go to the drives tab. If there is no visible CD-ROM drive, select add drive, and call it /cdrom. Then click the advanced settings button, and make sure the device type selected is cdrom. 

All this may come out right out of the box for you, but if not, this is what you have to do to get it to work.

For more detailed instructions see here: [http://ubuntuforums.org/showthread.php?t=78611](http://ubuntuforums.org/showthread.php?t=78611)

---

### Post by ardchoille on 2006-02-12
thank you for your post, however, I won't use wine. Wine is subject to all the same viruses/trojans/worms/etc which plague Windows and I don't want to have to re-install a wine environment over and over again.

---

### Post by nalmeth on 2006-02-12
Ah. Well I've used wine extensively and have not encountered any kind of malware. If you use it only for off-network duties, I don't bet on seeing anything nasty. I don't know of any native DVD shrinkers, unless DVD::RIP can do it.. You may be able to burn direct to a dual layer DVD with k3b, but I can't confirm this.

---

### Post by RAOF on 2006-02-13
I **believe** you should be able to just binary-copy your dual-layer discs using the "copy disc" mode of k3b or gnomebaker or your favourite burning software.  The worst that can happen is you burn a single dual-layer coaster :)

Also, wine isn't easily infectible with windows stuff - it doesn't run the same vulnerable services, and it just plain doesn't implement a lot of the obscure (and not so obscure :() stuff that viruses/worms/whatever use to propogate.

---

### Post by ardchoille on 2006-02-13
[QUOTE=RAOF]I **believe** you should be able to just binary-copy your dual-layer discs using the "copy disc" mode of k3b or gnomebaker or your favourite burning software.  The worst that can happen is you burn a single dual-layer coaster :)[/QUOTE]
Ah, ok, I didn't think about that. I'll see what gnomebaker can do. Thank you :)

> 
Also, wine isn't easily infectible with windows stuff - it doesn't run the same vulnerable services, and it just plain doesn't implement a lot of the obscure (and not so obscure :() stuff that viruses/worms/whatever use to propogate.
[http://blogs.zdnet.com/Ou/index.php?p=146](http://blogs.zdnet.com/Ou/index.php?p=146)

I just don't want to mess with anything related to wine/CXoffice/VMware/etc.

---

### Post by nalmeth on 2006-02-13
> The most feasible way this could happen is via a malicious WMF file embedded into a Word document, opened in Microsoft Office and running under Cross-Over Office.
> 
Marcus Meissner (meissner@suse.de) contacted the Wine development team and sent them a patch to fix this flaw.

You're not getting any word documents from anybody, and in fact you're not getting any foreign data at all except the installer for DVD shrink. Again, I have never seen anything exploited with my wine, and I use it for a lot of different things. 
All this aside, I would prefer to use native linux applications aswell. Maybe DVD shrink will be ported soon, or a clone of some sort. 

> I just don't want to mess with anything related to wine/CXoffice/VMware/etc.

Yeah, I have no use for CXoffice, because openoffice and GIMP do more than enough for me, although supposedly not for others. 

I recommend k3b for any CD burning, and it just might copy onto a dual layer DVD properly after all. Either way, let everyone know how it goes.

BTW are dual layers getting any cheaper? I couldn't afford to be backing up to dual layer all the time.

---

### Post by ardchoille on 2006-02-13
[QUOTE=nalmeth]I recommend k3b for any CD burning, and it just might copy onto a dual layer DVD properly after all. Either way, let everyone know how it goes.

BTW are dual layers getting any cheaper? I couldn't afford to be backing up to dual layer all the time.[/QUOTE]
I am checking out gnomebaker as I write this and it seems to be able to do more than graveman. I'll check out K3b as well. Either way, I'll post back here about how everything goes.

Dual layer blank DVD's aren't getting much cheaper in my area, but I don't mind paying for them as long as the DVD copy process actually works - it's cheaper than paying $25.00 for a 2nd copy of the DVD in my opinion - which is why I asked for some advice before burning too many coasters.

I'll post back with my experiences and findings :)

---

### Post by ardchoille on 2006-02-13
OK, here is what I have found thus far. I am using an older DVD of the movie Clue which I purchased. This DVD is clean and free of scratches. I simply want to copy a DVD that, I have purchased, to a blank DVD so I can keep the original DVD from being destroyed. The laws allow me to make one backup copy of any DVD that I have purchased. I do not want to use wine/CXoffice/VMware.

**gnomebaker:**
I tried to copy the DVD to an ISO file for burning to a blank DVD and got this error

INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
mkisofs: Input/output error. cannot read from '/media/cdrom1/video_ts/vts_01_0.vob'

**Findings:** gnomebaker cannot perform this task.


**graveman:**
Graveman won't even let you add directories to a DVD ISO and I got this error when trying to copy the DVD to an ISO (see screenshot 1)
You can see from the screenshot that I am duplicating from a DVD in the DVD drive and writing to an ISO file, but graveman wants me to insert a cd into the DVD drive. Why must I insert a CD into the DVD writer when I am writing to an ISO file?

**Findings:** graveman cannot perform this task.


**mkisofs:**
mkisofs cannot read the '/media/cdrom1/video_ts/vts_01_0.vob' file.

**Findings:** mkisofs cannot perform this task.


I will try with dvd::rip (available in the repos) and post my findings.

---

### Post by nalmeth on 2006-02-13
Sucks about your progress man, but keep with it
I've heard all kinds of great things about DVD::RIP, but never got it to work right. I never put much effort into figuring it out though. I think it's supposed to be able to do the burning aswell, but I can't confirm this as I said. Again, for encoding a DVD to avi I use acidrip exclusively, but this isn't what your after! Please do share your experience with DVD::RIP

If you have still not tried it, I must again recommend k3b. 

BTW you said you tried to copy DVD to ISO with gnomebaker. Did you try simply copy DVD, which should do it on the fly (meaning when its done copying it should pop open DVD drive and ask for a blank). I was sure gnomebaker did this, but since I rarely use it I'm not positive after all (I'm on KDE at work right now, so I can't check) I know that k3b does this.

---

### Post by ardchoille on 2006-02-14
[QUOTE=nalmeth]Sucks about your progress man, but keep with it
I've heard all kinds of great things about DVD::RIP, but never got it to work right. I never put much effort into figuring it out though. I think it's supposed to be able to do the burning aswell, but I can't confirm this as I said. Again, for encoding a DVD to avi I use acidrip exclusively, but this isn't what your after! Please do share your experience with DVD::RIP[/QUOTE]
I don't give up easily :)

> 
If you have still not tried it, I must again recommend k3b. 
Yes, because of all the nice things I hear about K3b, I will be trying it out regardless of how I end up copying my DVD's :)

> 
BTW you said you tried to copy DVD to ISO with gnomebaker. Did you try simply copy DVD, which should do it on the fly (meaning when its done copying it should pop open DVD drive and ask for a blank). I was sure gnomebaker did this, but since I rarely use it I'm not positive after all (I'm on KDE at work right now, so I can't check) I know that k3b does this.
Yes, I did try that. gnomebaker uses mkisofs and mkisofs cannot read a CSS encrypted DVD title, which is why it failed.

---

### Post by ardchoille on 2006-02-14
OK, I installed dvd::rip using [this wiki information]("https://wiki.ubuntu.com/DVDRippingandEncoding?highlight=%28dvdrip%29").
dvd::rip worked and it processed everything rather quickly - which made me initially think it wouldn't work at all. But, dvd::rip ripped the entire movie to my hard drive and I am watching it from my hard drive as I write this. Now, I just need to learn more about dvd::rip and how it works.. I need to learn how to burn the entire movie to a blank DVD that is compatible with my regular DVD player (the one on top of my TV set). Looks like I will be using dvd::rip to make backup copies of my entire DVD collection.

To do:
1) Buy more blank DVD's
2) Contact the dvd::rip author and thank him/her for an outstanding app

By the way, I only install apps from the official Ubuntu repos and only follow advice from the ubuntuforums and ubuntuwiki and I have never had a problem with any of my Ubuntu machines (11 of them). It is my opinion that people start having problems when they a) fail to read the docs, b) install packages from sources outside the official repos or c) follow procedures which conflict with the ubuntuwiki.

Signed,
A happy camper :)

EDIT: number 2 in the above "To do" section is done :)

---

### Post by nalmeth on 2006-02-14
did you install CSS with automatix or anything yet? I should have picked this out! 
sudo apt-get install libdvdcss2

EDIT:
just read your DVD::RIP = + post!
Did you use it to rip to a single file like an avi or mpeg? I ask because transcode (which you know dvdrip uses) always had problems for me.

If you have the Hard Drive space, try copying over all the files on to the drive, opening up k3b, selecting "make video DVD", and dragging the VIDEO_TS and AUDIO_TS (from the copied DVD) into the alloted spaces and burn, all this with a dual-layer of yours.

---

### Post by ardchoille on 2006-02-14
[QUOTE=nalmeth]did you install CSS with automatix or anything yet? I should have picked this out! 
sudo apt-get install libdvdcss2[/QUOTE]
I installed libdvdcss with this info:
```

  sudo apt-get install libdvdread3
  sudo /usr/share/doc/libdvdread3/examples/install-css.sh

```
which is in the wiki [here]("https://wiki.ubuntu.com/RestrictedFormats").

> 
just read your DVD::RIP = + post!
Did you use it to rip to a single file like an avi or mpeg? I ask because transcode (which you know dvdrip uses) always had problems for me.
I ripped to avi

> 
If you have the Hard Drive space, try copying over all the files on to the drive, opening up k3b, selecting "make video DVD", and dragging the VIDEO_TS and AUDIO_TS (from the copied DVD) into the alloted spaces and burn, all this with a dual-layer of yours.
I tried that first and it failed because the first encrypted vob file in the VIDEO_TS folder could not be read by the system.


**EDIT: **I should add that I don't know if it ripped the subtitles because I don't use subtitles. I am deaf and I only rent movies which contain closed captiion (which are different from subtitles). So, dvd::rip works and rips the closed captions too. Hearing people probably don't need subtitles or closed captions so it's not a problem. And deaf people usually rent movies which are closed captioned so dvd::rip should work for everyone. However, it's entirely possible that dvd::rip ripped the susbtitles too and I just haven't found out about it yet. I will be checking this out too.

---

### Post by nalmeth on 2006-02-14
I'm sorry to keep at you, but when you say you copied it over, you mean the way you did it with gnomebaker? If so, can you open the DVD with nautilus, and manually copy and paste them over? I have heard that DVD's contain hidden files that may prevent this from working, so this* may be a problem*. The actual burning would be done with k3b for me, I don't know if gnomebaker can burn video DVD's (the ones that work in your dvd player).
Also, I have not done my dvdcss this way, but I can't say its the right or wrong way. I was almost positive that it was done with apt-get libdvdcss2. 
A good way to be sure would be with automatix, which can setup DVD CSS, and put that part of the issue to rest 
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
One more thing, and I promise I won't bother you again!
Did you try the DVD copy (on-the-fly) function in k3b yet?

*EDITED*

---

### Post by ardchoille on 2006-02-14
[QUOTE=nalmeth]I'm sorry to keep at you, but when you say you copied it over, you mean the way you did it with gnomebaker? If so, can you open the DVD with nautilus, and manually copy and paste them over?[/QUOTE]
No problem, I don't mind keeping at a problem until it is solved. I tried copying with nautilus and it failed. I tried using the cp command and it failed. I have used a few apps that use mkisofs to make the DVD ISO file and mkisofs itself cannot copy or read a CSS'd file, which is why some apps cannot copy a CSS encrypted DVD movie.

> 
 I have heard that DVD's contain hidden files that may prevent this from working, so this* may be a problem*. The actual burning would be done with k3b for me, I don't know if gnomebaker can burn video DVD's (the ones that work in your dvd player).
Also, I have not done my dvdcss this way, but I can't say its the right or wrong way. I was almost positive that it was done with apt-get libdvdcss2. 
Yes, if you have the PLF repo enabled you can apt-get install libdvdcss2, but I did not use that method to install it.

> 
A good way to be sure would be with automatix, which can setup DVD CSS, and put that part of the issue to rest 
[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)
One more thing, and I promise I won't bother you again!
Did you try the DVD copy (on-the-fly) function in k3b yet?
*EDITED*
Well, I know I have libdvdcss set up correctly because I am able to watch CSS'd movies, so libdvdcss2 is not the problem. I have not tried K3b yet.. I am not sure I want to put all the KDE deps for K3b on this system. I have other computers that I will try K3b on. Also, I only have one dvd burner and one cd burner on all my systems so I have to make an ISO of the DVD before I can burn it.. making the ISO is the problem because of mkisofs.

I don't know exactly what dvd::rip does, but it works even on CSS encrypted DVD's. I'll learn how it does what it does in time.

**EDIT:** You're not bothering me, I don't mind questions.. I like helping others figure things out :)

---

### Post by ardchoille on 2006-02-14
Here is something a bit weird. I tried creating an ISO of my DVD with gnomebaker yesterday and it didn't work. So, I installed dvd::rip. This morning I tried, just for kicks, to burn an ISO of the same DVD using gnomebaker and it worked. This makes me think that something was installed with dvd::rip that enabled gnomebaker to complete the task this time.


EDIT: I found that gnomebaker can burn a DVD to an ISO file. However, when you burn the ISO to a blank DVD it doesn't play.

I also found that dvd::rip doesn't create a VIDEO_TS.ifo file and transcode needs this file in order to do its job. So, I am back at square one.. I need an app that can copy a DVD.

---

### Post by Ramses de Norre on 2006-02-14
Just as an addition: there is a linux version of DVD Shrink. You can just apt-get it, name= dvdshrink. So no need to use wine for it;)

---

### Post by ardchoille on 2006-02-14
[QUOTE=Ramses de Norre]Just as an addition: there is a linux version of DVD Shrink. You can just apt-get it, name= dvdshrink. So no need to use wine for it;)[/QUOTE]
I searched for dvdshrink and got no returns. Which repo is it in?

---

### Post by Ramses de Norre on 2006-02-14
I used the attached repo's, don't know which did the trick but you can replace yours by mine just for the download;)

---

### Post by ardchoille on 2006-02-14
[QUOTE=Ramses de Norre]I used the attached repo's, don't know which did the trick but you can replace yours by mine just for the download;)[/QUOTE]
The only difference between your sources.list and mine is that you have the wine.sourceforge.net repos listed and enabled.. which makes me think you have a Windows version of dvdshrink, dvdshrink is not available for Linux unless you use wine AFAIK.

---

### Post by ardchoille on 2006-02-15
I have found an app that serves my purpose. The app is called xdvdshrink and is available [here]("http://dvdshrink.sourceforge.net/").

I burn one of my DVD movies with this app and it works for what I needed - produces a full backup of a DVD.

You'll have to install some things but all the required apps are in the repos. You can run the xdvdshrink installer.sh script (as root) and it will tell you what you need to install. After installer the apps run the installer.sh script again and it will install.

To run xdvdshrink, open a term and type 'xdvdshrink.pl' and the gui will open up and you can go to work :)

---

### Post by GrammatonCleric on 2006-03-01
[FONT=Verdana]If all you are doing is making backups of DVDs you could just do...

```


sudo apt-get install dvd+rw-tools


``` 

Then create and image of the DVD you want by doing the following from a terminal.  Substitute /dev/hdc with the correct drive for the location of the DVD you wish to image.

```


dd if=/dev/hdc of=/some/path_to_image/whatever.iso


``` 
Now to burn the iso...again replace /dev/hdc with the correct location of your DVD Burner.

```


growisofs -Z /dev/hdc=/some/path_to_image/whatever.iso


``` 

[/FONT]

---

### Post by tenjin1 on 2006-03-07
The DVDShrink _for Linux_ is called.......... XDVDShrink......

[http://dvdshrink.sourceforge.net/](http://dvdshrink.sourceforge.net/)


I have it on my system but haven't played with it much (seemed alot different than DVDShrink, but then again haven't played with it much). I use NeroLinux to burn any and every format and a program called tovid to transcode to DVD (which had produced great looking dvds w/ menus that are playing in my dvd player at this moment)

NeroLinux--->[http://www.nero.com/en/NeroLINUX.html](http://www.nero.com/en/NeroLINUX.html)
tovid--->[http://tovid.berlios.de//en/index.html](http://tovid.berlios.de//en/index.html)

---

