---
title: "Converting to Linux"
date: 2009-03-03
forum: General Help
---

### Post by PFRules on 2009-03-03
**Hi everyone**

I feel pretty comfy using Ubuntu and already know that MySQL, JBuilder 2006 and JUDE exist for Linux (I'm a Java programmer).

If I'll find out that the following programs also exist (or their equivalents):

- Winzip 12
- Nero 7
- Alcohol 120%
- DivX 7 (specially Converter for converting DVD rips to DivX files)
- ConvertXtoDVD (converts DivX files to DVD format)
- Ares
- Download Accelerator Pro 5 (resumes stopped downloads - Firefox download manager doesn't always work)
- Paint Shop Pro 7
- Pazera MOV to AVI Converter
- Windows Movie Maker
- Smart Ripper (rips RPC-protected-commercial DVDs)
- DVD Shrink 3.2
- PowerQuest Drive Image 7 (performs whole hdd backups)
- Windows Live Messenger 14.0.8064.206

I'll have no problem giving up on Windows and exclusively use Ubuntu.
I also heard that Wine could be a great resource to execute Windows programs.

Thanks for your recommendations.

**Mario.**

**P.S.:** Can you recommend any video capturing utility? I want to show off my full-compiz-effects desktop to my Windows friends -and hopefully try to 'convert' them to Ubuntu- ;)

---

### Post by jARLAXL on 2009-03-03
Well i dont know all these windows programs.
In linux there are alternatives and as Linux is not windows therefore i wouldnt expect it to run programs which were written absolutely for windows. Nevertheless there is wine [http://www.winehq.org/](http://www.winehq.org/)
If you need to run windows programs and dont feel good enough running these alternatives (some of them are better in linux according to my opinion) then run them in windows.

Winzip-->fileroller(already installed in your ubuntu)
Nero-->Brazero(already installed)/k3b 
Paintshop-->Gimp(already installed)(?)
Backup your system: you can find many programs for doing this or tutorials such as [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)
Alcohol-->there are many programs but i prefer this tweak: [http://ubuntuforums.org/showthread.php?t=704350](http://ubuntuforums.org/showthread.php?t=704350)
Format converter-->ffmpeg
video capturing:recordmydesktop, byzans

About dvd ripping-i dont even know what is this
but in general have a look here: [http://www.linuxalt.com/](http://www.linuxalt.com/)
you can also try to go to add/remove or synaptic (for advanced usage) and see what programs are available

---

### Post by cogadh on 2009-03-03
Okay, lets see:

- Winzip 12: Archive functions are already handled natively within the window manager and OS.
- Nero 7: There is a [Linux version of Nero]("http://www.nero.com/enu/linux3.html"), but I've never used it myself, so I can't really comment on its quality
- Alcohol 120%: No native version that I am aware of, but basic mounting of virtual disk images is supported within the OS already
- DivX 7: You can add DivX support to Linux with one of the media format packages, but to my knowledge, DivX itself does not produce a Linux version of the full software suite
- ConvertXtoDVD: No idea
- Ares: Don't know what that is
- Download Accelerator Pro 5: No native version I am aware of, but there are alternatives like [ProZilla]("http://prozilla.genesys.ro/") (first one that popped up in a Google search)
- Paint Shop Pro 7: GIMP
- Pazera MOV to AVI Converter: No idea
- Windows Movie Maker: Obviously no native version, but there are some very good media apps for Linux. You should check out the [Medibuntu project]("http://www.medibuntu.org/") for details. They might also have solutions for some of the other media related apps that I have no ideas on.
- Smart Ripper: Since discussing methods of circumventing copy protection is a no-no on the forums, I can't really offer any advice on this
- DVD Shrink 3.2: [K9Copy]("http://k9copy.sourceforge.net/")/[Vamps]("http://vamps.sourceforge.net/")
- PowerQuest Drive Image 7: Creating drive images is supported by the OS through the use of the "dd" command
- Windows Live Messenger: Again, obviously there is no native version, but there are numerous IM apps for Linux. I personally recommend Pidgin, which does support MSN as well as AIM, ICQ, Jabber and any number of other IM protocols.

---

### Post by hikaricore on 2009-03-03
As an alternative to Nero I suggest K3B.  It's quite a complete CD/DVD burning suite.

---

### Post by Twitch6000 on 2009-03-03
- Winzip 12: 6zip and the inbuilt windows manager will do.
- Nero 7: There is a linux version on the nero site.
- Alcohol 120%: never tried this program so don't ask me lol.
- DivX 7 (specially Converter for converting DVD rips to DivX files): I think ther is a native version of this or a program that does this,not sure though.
- ConvertXtoDVD (converts DivX files to DVD format): look above lol
- Ares: never heard of(wow i suck at helping lol)
- Download Accelerator Pro 5 (resumes stopped downloads - Firefox download manager doesn't always work): wget and opera are what I use for that sort of thing
- Paint Shop Pro 7: Gimp or use wine to run Paint Shop Pro 7
- Pazera MOV to AVI Converter: there are converters for this not sure of the names.
- Windows Movie Maker: we dont ave this program,but we have our own movie makers like open movie maker and cinerlla.
- Smart Ripper (rips RPC-protected-commercial DVDs): no comment
- DVD Shrink 3.2: wine runs this
- PowerQuest Drive Image 7 (performs whole hdd backups): I forget the program for this
- Windows Live Messenger 14.0.8064.206: aMSN

Oh and for screen recording just look in add/remove.

---

### Post by crapple on 2009-03-03
There are many programs in ubuntu that do similar things.  For example kino is similar to windows movie maker.  
If you want to use those programs just dual boot ubuntu and windows.

---

### Post by sloggerkhan on 2009-03-03
[QUOTE=PFRules;6832320]**Hi everyone**

- Winzip 12 -- There are archivers for nearly every format on linux. I prefer tar.gz or 7zip myself.

- Nero 7 -- Lots of alternatives. Base system comes with brasero. KDE's burn app is better than brasero IMO, though.

- Alcohol 120% -- You can make ISOs and mount them/read them, etc. for any disk linux can read. Command lines and GUIs abound.

- DivX 7 --
- ConvertXtoDVD -- Thoggen will rip DVDs to ogg/theora via gui, mendcoder and ffmpeg will convert between whatever formats you desire from command line. If you are happy to convert via command line, there's or lots of possibilities.

- Ares -- Don't know what it is.

- Download Accelerator Pro 5 (resumes stopped downloads - Firefox download manager doesn't always work) No idea if there's anything like this. There are download managers available, but I've never had stopped DLs outside of torrenting.

- Paint Shop Pro 7 -- krita, gimp, inkscape... some combination can probably do what you want. Will it be the same? No.


- Pazera MOV to AVI Converter -- Once again, mencoder can do anything.

- Windows Movie Maker -- search repos for movie editors or search for linux movie makers on google. Last I checked there were 3-5 different GUIs around.

- Smart Ripper (rips RPC-protected-commercial DVDs) -- Not sure about DVD regions, but with decss I haven't had a DVD I couldn't play.

- DVD Shrink 3.2 -- Once again, just rip the damn DVD and convert with mencoder, ffmpg, etc. There are lots of command line video conversion utilities.

- PowerQuest Drive Image 7 (performs whole hdd backups) -- lots of ways to do this. If you have space to store a whole drive, dd image it and compress. Otherwise lookup backup solutions. On ubuntu it's often easier to backup stuff like /etc /home and use apt to create a list of installed packages, as you can reinstall ubuntu, reinstall package list, restore /etc and /home and be back where you were.

- Windows Live Messenger 14.0.8064.206 -- Pidgin, I think there's another more MSN-like alternative. aMSN, maybe? Not to mention gnome's IM app.

---

### Post by david_kt on 2009-03-04
> **PFRules said:**
> **Hi everyone**

I feel pretty comfy using Ubuntu and already know that MySQL, JBuilder 2006 and JUDE exist for Linux (I'm a Java programmer).

If I'll find out that the following programs also exist (or their equivalents):

Check below website:

[http://www.linuxlinks.com/article/20070701111340544/Equivalents.html](http://www.linuxlinks.com/article/20070701111340544/Equivalents.html)



DK

---

### Post by oldrocker99 on 2009-03-04
I've used Nero Linux, and it doesn't offer a lot that K3B does. 

If Nero Linux had all the features of Nero 7, ESPECIALLY the CD cover creator, I'd buy it in a heartbeat. It will not run under wine, unfortunately.

THE Linux program I'd most like to see is a program like Nero Cover Creator, with support for commercially-available cover media. My attempts to build a Memorex template for Scribus has, so far, failed...

I'll also mention that there's an Alcohol clone called Acetone, and that WinRAR and QuickPAR run great under wine.
Try AVIDemux for conversion from one video format to another. 

:guitar:

---

### Post by TheHolm on 2009-03-05
- Nero 7  --  Brasero  
- DivX 7 (specially Converter for converting DVD rips to DivX files) -- AcidRip DVD Ripper.
- ConvertXtoDVD (converts DivX files to DVD format) Hmmm. NO idea, but I have seen some tools for DVD authoring.

- Ares
- Download Accelerator Pro 5 (resumes stopped downloads - Firefox download manager doesn't always work)
- Paint Shop Pro 7
- Pazera MOV to AVI Converter
- Windows Movie Maker
- Smart Ripper (rips RPC-protected-commercial DVDs)
- DVD Shrink 3.2
- PowerQuest Drive Image 7 (performs whole hdd backups)
- Windows Live Messenger 14.0.8064.206

- Nero 7  --  Brasero  
- DivX 7 (specially Converter for converting DVD rips to DivX files) -- AcidRip DVD Ripper.
- ConvertXtoDVD (converts DivX files to DVD format) Hmmm. Brasero again, but it depends what do you want..

- Ares - what does it do?

- Download Accelerator Pro 5 - plenty of this kinds around.  wget  as classic example.

- Pazera MOV to AVI Converter --- mencoder (part of mplayer distro) can do it. No GUI. 

- Smart Ripper (rips RPC-protected-commercial DVDs) - AcidRip DVD Ripper

- DVD Shrink 3.2 - what does it do? 

- PowerQuest Drive Image 7 (performs whole hdd backups) - you can use copy command for it... 

- Windows Live Messenger 14.0.8064.206 - Pigin

---

### Post by attilab on 2009-03-13
- I have also tons of DVDrip on my network HDD, can't watch them in ubuntu, and the codec's are not free? or unsupported?
- how can I transfer the pictures from my Canon 40D DSLR? in XP using Lightroom2 for postprocessing from RAW?
- I don't want to go further now, just step by step
thanks in advance

---

### Post by oldos2er on 2009-03-13
Enable the Medibuntu repository ([http://medibuntu.org/](http://medibuntu.org/)) to install codecs for DVD playback.

---

### Post by Therion on 2009-03-13
Instead of **Ares** you would use **Frostwire** in Ubuntu.

---

### Post by david_kt on 2009-03-13
> **attilab said:**
> - I have also tons of DVDrip on my network HDD, can't watch them in ubuntu, and the codec's are not free? or unsupported?


Check below steps to play restricted formats:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And below is special for DVD:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

DK

---

### Post by mb_webguy on 2009-03-14
> **PFRules said:**
> **Hi everyone**

I feel pretty comfy using Ubuntu and already know that MySQL, JBuilder 2006 and JUDE exist for Linux (I'm a Java programmer).

If I'll find out that the following programs also exist (or their equivalents):

- Winzip 12
- Nero 7
- Alcohol 120%
- DivX 7 (specially Converter for converting DVD rips to DivX files)
- ConvertXtoDVD (converts DivX files to DVD format)
- Ares
- Download Accelerator Pro 5 (resumes stopped downloads - Firefox download manager doesn't always work)
- Paint Shop Pro 7
- Pazera MOV to AVI Converter
- Windows Movie Maker
- Smart Ripper (rips RPC-protected-commercial DVDs)
- DVD Shrink 3.2
- PowerQuest Drive Image 7 (performs whole hdd backups)
- Windows Live Messenger 14.0.8064.206

I'll have no problem giving up on Windows and exclusively use Ubuntu.
I also heard that Wine could be a great resource to execute Windows programs.

Thanks for your recommendations.

**Mario.**

**P.S.:** Can you recommend any video capturing utility? I want to show off my full-compiz-effects desktop to my Windows friends -and hopefully try to 'convert' them to Ubuntu- ;)

Others have probably covered this pretty well, but I'm feeling lazy right now and don't feel like reading all of the other posts. ;)

**Winzip:** File Roller is the default Archive Manager in Ubuntu, and can handle just about every archive type you could want.  Install the p7zip-rar package to enable support for rar and 7z archives.

**Nero 7:**  Brasero (the default disc burning app for Ubuntu) and k3b (the default burning app for Kubuntu) can do most if not all of what Nero can do.  I personally prefer k3b, but YMMV.

**Alcohol 120%:**  You don't need an app to mound ISOs on Linux.  You can mount them directly from the terminal with the "mount" command, and if you want a GUI to do it, you can install the gmountiso package.

**DivX 7**:  There are numerous apps available in Linux for ripping DVDs (e.g. dvd::rip, OGMrip) and converting video to and from almost any format (e.g. the various front-ends for mencoder and ffmpeg), but the best in my opinion is Handbrake.  It can rip DVDs to various formats, can convert videos to and from numerous formats, and has several presets for converting videos for use on specific media devices (such as an iPod or PS3).  You'll definitely want to add the non-free-codecs and libdvdcss2 packages from the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repository.

**ConvertXtoDVD:**  Again, several apps are available, but I suggest DeVeDe, ManDVD, or DVD Styler.

**Ares:**  I'm not sure which Ares you're talking about, since there's also a game called Ares, but if you're talking about the Ares Galaxy p2p file-sharing client, it will apparently run fairly well under Wine.  There are numerous file-sharing clients available for other p3p networks, however.  For bittorrent, there's Transmission (the default for Ubuntu), Deluge (my personal favorite), Azureus, gTorrent, kTorrent, and many others.  For Gnutella, there's gtk-gnutella, LimeWire, and FrostWire.

**Download Accelerator Pro 5:**  I user the DownThemAll extension for Firefox, which works extremely well for me.  Some websites don't like multi-thread downloads, however, so for those you'd have to either change the number of threads used by DTA, or use Firefox's download manager.  I don't have any experience with any other download managers.

**Paint Shop Pro 7**:  It takes a bit to get used to the interface, but GIMP can do anything PaintShop can do.  And if it can't do something you want, you can probably find a filter or script for it.

**Pazera MOV to AVI Converter**:  Again, there are numerous conversion utilities available, and again, I'd suggest Handbrake.

**Windows Movie Maker:**  Eh... Here's where we run into one minor snag.  It's not that there aren't plenty of video editing applications available for Linux -- because there are -- it's just that none that I know of have as intuitive an interface.  Avidemux is good for simple editing.  For more than that, you'd need to look into something like Open Movie Editor, KdenLive, Cinelerra, or Kino.

**Smart Ripper**  Again, look to Handbrake.  As long as you installed that libdvdcss2 package from Medibuntu I previously mentioned, you don't have to worry about region codes in Linux.

**DVD Shrink 3.2:**  dvd95 and k9copy both are designed to backup dual-layer DVDs to single-layer DVDs.

**PowerQuest Drive Image 7:**  There are easier ways of backing up files, but you can use the dd command from the terminal to make a disk image.

**Windows Live Messenger:**  For general messaging, I suggest Pidgin, but it doesn't currently support video or voice messaging.  aMSN is essentially a clone of the Windows Live Messenger, so you might want to give it a try if video or voice chat is a priority.

**Video capture:**  I use xvidcap.  It can take video or still images in several formats.  I personally didn't like the default settings though, so you may want to take a look at them before you start.

---

