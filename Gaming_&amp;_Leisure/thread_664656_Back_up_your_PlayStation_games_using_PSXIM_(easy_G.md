---
title: "Back up your PlayStation games using PSXIM (easy GUI)"
date: 2008-01-11
forum: Gaming &amp; Leisure
---

### Post by verb3k on 2008-01-11
[B][COLOR="Red"]NOTE: If you prefer a command line version, you can get it here:
[http://ubuntuforums.org/showthread.php?t=545546](http://ubuntuforums.org/showthread.php?t=545546)[/COLOR][/B]


I would like to introduce you to PSXIM, a PlayStation CD backup tool that rips PSX game CDs to your hard drive into a format that can be played by PSX emulators.

[IMG]http://i192.photobucket.com/albums/z123/verb3k/psxim.png[/IMG]

With PSXIM, you can play your PlayStation games on your PC using a PSX emulator like ePSXe while keeping the CDs in a safe place. For the emulator, you can search these forums and you'll find many HOWTOs about installing them.

[SIZE="5"]Installation:[/SIZE]
Simple!
Just download the .deb package from here:

[http://psxim.googlecode.com/files/psxim-0.1.deb](http://psxim.googlecode.com/files/psxim-0.1.deb)

and double-click it to start the installation. When the installation is finished, you'll find the PSXIM icon in the "Sound & Video" menu you can see below:

[IMG]http://i192.photobucket.com/albums/z123/verb3k/menu.png[/IMG]

If you want PSXIM to be more verbose, start it from the command line:
```
user@ubuntu:~$ psxim
```
and you will see more output about the state of the ripping process.

[COLOR="DarkOrange"]Note: Using CD-RW drives to back your games is preferred, as they can read the sub-channel.[/COLOR]

The official website: [http://psxim.googlecode.com](http://psxim.googlecode.com)

PSXIM is written in Python and PyGTK and uses cdrdao as a backend. PSXIM should work with most ubuntu releases as well as Debian. For other distributions, see below.

[SIZE="5"]PSXIM for Other Distributions:[/SIZE]
 If you are using another distribution that doesn't use the **Debian package management system**, you can get the source code from here:
[http://code.google.com/p/psxim/downloads/list](http://code.google.com/p/psxim/downloads/list)
It needs no compilation, it's a python script which means you can run it directly as you do with any other script.
If you can package  PSXIM for your non-debian distribution, please let me know by sending me a Private Message and I will add them to download list.



Please if you have any questions, suggestions, bugs or issues, please post them here and I will try my best ;)

Thanks in advance,
verb3k

---

### Post by acoustibop on 2008-01-11
This looks interesting, verb3k.  What format(s) does it rip to?

And more specifically, with regard to your note that> [COLOR="DarkOrange"]Note: Using CD-RW drives to back your games is preferred, as they can read the sub-channel.[/COLOR]
Do the images ripped with this utility include the subcode from the CD, then?  As you probably know, this is often needed to bypass copy protection, and at present there seem to be no applications that run in Linux that will rip to formats that include subcode.

---

### Post by Rinzwind on 2008-01-11
Cool.I am so going to experiment with this :D

---

### Post by verb3k on 2008-01-11
> **acoustibop said:**
> This looks interesting, verb3k.  What format(s) does it rip to?

And more specifically, with regard to your note that
Do the images ripped with this utility include the subcode from the CD, then?  As you probably know, this is often needed to bypass copy protection, and at present there seem to be no applications that run in Linux that will rip to formats that include subcode.

I don't really deal with cdrdao that much,  but until now I haven't run into a game that refused to be backed up correctly because of copy protection.

PSXIM includes a TOC file with every ripped image, so I guess subcode info should go there. This makes me wonder if you have ever encountered a game that was protected and didn't rip properly. If you have an game that you think is copy protected, please  try PSXIM with it and let me know.

Also, all images are ripped as raw data, not really a specific format afaik.

---

### Post by disturbedite on 2008-01-11
not to steal anyone's thunder here, but...
there is another tool that does this, its been around for a while, its called PSXrip.

---

### Post by acoustibop on 2008-01-11
It's not so much a matter of copying games as of playing the ripped images, verb3k - copy protection is usually found on European PAL games rather than NTSC-US ones, so many Americans may not encounter it.  Unless you're using a ripper that will warn you about missed sectors, a copy protected game will appear to give a normal image; however the image will be unplayable.

No, I doubt that the subcode would go into the TOC file; looking at my CloneCD .ccd/.img/.sub files, the .sub file, which is where the subcode goes, is typically 20-30MB.  Additionally, I don't know of any Playstation emulators that read a .toc file.  With .bin or .img files, some emulators (eg pSX) read the .cue or .ccd file, or the .mds file in the case of pSX reading an .mdf/.mds image, and most (like ePSXe) don't read the descriptor files at all; they just read the main image file.

For this reason, while pSX will play the image of a copy protected game directly if subcode is included, ePSXe won't - if a copy protected game is to be played, you must use a CDR plugin such as Pete's (in Windows, anyway), with which you can read the subcode from the CD and save it as a separate file, which must be run with the main image to play it.

In the US, if there is any protection (comparatively unusual) it will be mod protection.

And, @disturdedite, PSXrip seems to be another frontend for cdrdao, only it's Qt.  But I don't think that will include subcode in the image, either.

---

### Post by verb3k on 2008-01-11
> **disturbedite said:**
> not still anyone's thunder here, but...
there is another tool that does this, its been around for a while, its called PSXrip.

That's true, the difference is that PSXrip uses Qt (KDE) for the GUI and PSXIM uses GTK+ (GNOME), but the backend is the same, cdrdao.

---

### Post by verb3k on 2008-01-11
> **acoustibop said:**
> It's not so much a matter of copying games as of playing the ripped images, verb3k - copy protection is usually found on European PAL games rather than NTSC-US ones, so many Americans may not encounter it.  Unless you're using a ripper that will warn you about missed sectors, a copy protected game will appear to give a normal image; however the image will be unplayable.

No, I doubt that the subcode would go into the TOC file; looking at my CloneCD .ccd/.img/.sub files, the .sub file, which is where the subcode goes, is typically 20-30MB.  Additionally, I don't know of any Playstation emulators that read a .toc file.  With .bin or .img files, some emulators (eg pSX) read the .cue or .ccd file, or the .mds file in the case of pSX reading an .mdf/.mds image, and most (like ePSXe) don't read the descriptor files at all; they just read the main image file.

For this reason, while pSX will play the image of a copy protected game directly if subcode is included, ePSXe won't - if a copy protected game is to be played, you must use a CDR plugin such as Pete's (in Windows, anyway), with which you can read the subcode from the CD and save it as a separate file, which must be run with the main image to play it.

In the US, if there is any protection (comparatively unusual) it will be mod protection.

And, @disturdedite, PSXrip seems to be another frontend for cdrdao, only it's Qt.  But I don't think that will include subcode in the image, either.

Thanks for your reply, acoustibop
I understand your point, but copy protection wasn't really pervasive at the time of PSX. I have many NTSC games that I backed up this way, so I will really appreciate it if you can give me a title (NTSC or PAL) that is copy protected so that I try to figure out a means to do something about it. 
It's said that unless you experience the bug, you can't fix it :lolflag:

---

### Post by acoustibop on 2008-01-12
I don't know of any NTSC-US titles that are copy-protected (as opposed to mod protected: when NTSC-US games are protected, it always seems to be mod protection), but many PAL titles are.  PAL versions of Final Fantasies VIII and XI usually are, for instance.

See the [Playstation Copy Protection List]("http://www.geocities.com/psxcplist/"), an excellent resource for checking out the protected status of Playstation games.  You may have to disable ad blocking to access the index.  There are patches available for many protected games: [MegaGames]("http://www.megagames.com/") is a good place to find these.

---

### Post by verb3k on 2008-01-12
Thanks acoustibop, really useful links indeed.
MegaGames is one of the best out there.

---

### Post by disturbedite on 2008-01-12
well, i prefer Qt as i'm on Kubuntu/KDE...

---

### Post by verb3k on 2008-01-13
I guess I'm going to look for a kde-apps-like website for GNOME to register this program :)

---

### Post by verb3k on 2008-01-18
If anyone prefers to use a command line tool instead of a GUI program, I've writtern a small script to do the job. See this topic for more info:[http://ubuntuforums.org/showthread.php?t=545546](http://ubuntuforums.org/showthread.php?t=545546)

---

### Post by anjilslaire on 2008-01-18
AcetoneISO rips ps1 games as well,as a frontend for cdrdao.
Interestingly enough, it does indicaet reading the subchannel on my system:

```

/dev/cdrom: LITE-ON DVDRW LDW-811S      Rev: HS0R
Using driver: Generic SCSI-3/MMC (raw writing) - Version 2.0 (options 0x0000)

Reading toc and track data...

Track   Mode    Flags  Start                Length
------------------------------------------------------------
 1      DATA    4      00:00:00(     0)     45:49:12(206187)
Leadout DATA    4      45:49:12(206187)

PQ sub-channel reading (data track) is supported, data format is BCD.
Raw P-W sub-channel reading (data track) is supported.
Cooked R-W sub-channel reading (data track) is supported.

```

---

### Post by acoustibop on 2008-01-18
However, the .bin/.cue format and (I think) the .iso format don't include subcode in their specifications.  So it doesn't make any difference whether the ripper reads the subcode; if the image format doesn't support it, it won't be included in the image.

At a guess, I'd say that reading the subcode from the the CD may still help with ripping an accurate image, even though it's not included in the image.  Certainly, if you're ripping a protected CD so you can apply a patch to it to defeat the protection, you'll need to be reading the subcode to rip an accurate enough image for the patch to work.

---

### Post by disturbedite on 2008-01-18
> **acoustibop said:**
> However, the .bin/.cue format and (I think) the .iso format don't include subcode in their specifications.  So it doesn't make any difference whether the ripper reads the subcode; if the image format doesn't support it, it won't be included in the image.

At a guess, I'd say that reading the subcode from the the CD may still help with ripping an accurate image, even though it's not included in the image.  Certainly, if you're ripping a protected CD so you can apply a patch to it to defeat the protection, you'll need to be reading the subcode to rip an accurate enough image for the patch to work.
so you're saying PSXIM is the only ripper that saves the subcode right?

---

### Post by verb3k on 2008-01-18
> **disturbedite said:**
> so you're saying PSXIM is the only ripper that saves the subcode right?

No, he didn't say that....he was talking generally.
In fact, he said that he thought PSXIM isn't able to rip subcode data :)

---

### Post by acoustibop on 2008-01-19
Exactly, verb3k - it may be able to read the subcode from the CD (and this may sometimes be necessary), but it can't include subcode in the images it creates because these formats can't include subcode.

Unfortunately, the only formats that do include subcode (CloneCD's .ccd/.img/.sub and Alcohol's .mdf/.mds ones - I think both were specifically developed for ripping game CDs) are proprietary and all the applications that can rip to them are Windows only.  :(

---

### Post by verb3k on 2008-01-19
> **acoustibop said:**
> Exactly, verb3k - it may be able to read the subcode from the CD (and this may sometimes be necessary), but it can't include subcode in the images it creates because these formats can't include subcode.

Unfortunately, the only formats that do include subcode (CloneCD's .ccd/.img/.sub and Alcohol's .mdf/.mds ones - I think both were specifically developed for ripping game CDs) are proprietary and all the applications that can rip to them are Windows only.  :(

I don't think it will be difficult to develop a format that includes subcde data, but the problem is that most free software hackers aren't interested in game emulation and ripping. That's why I've done this app to serve an under-served community, that is the Linux gamers.
I don't claim to be a real competent hacker, but I am just trying to simplify things for people and make their lives easier. If I can find any way to rip subcode data freely (speech), I would certainly implement it in this program.

---

### Post by acoustibop on 2008-01-19
The problem is not just developing a format to include subcode, verb3k, it's getting application developers to include recognition of it (and its subcode inclusion) in their software.  Even mounting the image won't AFAIK be successful if the OS doesn't recognise it as a CD format. :(

---

### Post by disturbedite on 2008-01-19
> **acoustibop said:**
> Exactly, verb3k - it may be able to read the subcode from the CD (and this may sometimes be necessary), but it can't include subcode in the images it creates because these formats can't include subcode.
ok.  that was my understanding, which is why i asked my previous question, i was a bit confused.  but thats all cleared up now.

---

### Post by acoustibop on 2008-03-26
> **verb3k said:**
> ... PSXIM is written in Python and PyGTK and uses cdrdao as a backend... 

You only had to read the first post in the thread to find out, Xaraki.

---

### Post by verb3k on 2008-03-26
> **Xaraki said:**
> Thanks man , But which program did u use in making this ?

As acoustibop pointed out, it's written in Python and PyGTK. Python is a *programming language* . I don't know whether you can call Python a *program*.
(probably we can refer to the interpreter as a program :) )

---

### Post by verb3k on 2008-03-28
I've updated the thread, it now includes the source code for other distributions that do not use the Debian package management system.
If you are packaging software for a different package management system, please consider packaging PSXIM for it. I would add your package to the download list with pleasure.

---

### Post by acoustibop on 2008-03-28
> Actually , i knew that he used python ,,, i was pretending that i don't know
???

---

### Post by verb3k on 2008-03-30
> **Xaraki said:**
> Actually , i knew that he used python  ,,, i was pretending that i don't know ;) 

:guitar:

:confused:

---

### Post by cmike2 on 2008-06-09
very handy. It would be nice to have a progres bar. Thanks!

---

### Post by verb3k on 2008-06-09
> **cmike2 said:**
> very handy. It would be nice to have a progres bar. Thanks!

If you start it from the command line, you will be able to see more information about the copying process in the terminal window, including the progress.
Thanks for your feed back.

---

### Post by GSZX1337 on 2008-06-09
Is there an app like this for Sega Saturn games? I'd use this app but I don't have a modded PSX/2.

---

### Post by dfreer on 2008-06-10
I'll have to give this a try and see if it's any different from the guide I used to use online, but from looking at the psxim.sh script I don't think it's any different (still rips in .bin/.toc format eh?).

Old guides I used:
[http://www.megagames.com/psx/psx_copy_patch_linux.shtml](http://www.megagames.com/psx/psx_copy_patch_linux.shtml)
[http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1058](http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1058)
(Very bottom of thread).

I just wanted to add to the discussion: As well as most emulators not being able to read the .toc extension (I believe there is a way to convert it to a .cue), there are several games that I myself have experienced that need a proper rip in order to work:

Jet Moto SCUS-94309 == If not ripped correctly, no music will play when racing.

Tomb Raider II SCUS-00437 == If not ripped correctly, no music will play in the main menu. And if you select to enter Lara's House or Start a Game (new or old), the game will freeze.

Note, that when I was experimenting with different ways to back these games to the hard drive, that I was unable to back them up at all using the cdrdao in Linux. Furthermore, I wasn't even able to rip them in windows after trying 2-3 DVD/CD drives, until I finally found one that read them correctly.

Just my thoughts.

---

### Post by verb3k on 2008-06-10
> **dfreer said:**
> I'll have to give this a try and see if it's any different from the guide I used to use online, but from looking at the psxim.sh script I don't think it's any different (still rips in .bin/.toc format eh?).

Old guides I used:
[http://www.megagames.com/psx/psx_copy_patch_linux.shtml](http://www.megagames.com/psx/psx_copy_patch_linux.shtml)
[http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1058](http://psxemulator.proboards54.com/index.cgi?board=rules&action=display&thread=1058)
(Very bottom of thread).

I just wanted to add to the discussion: As well as most emulators not being able to read the .toc extension (I believe there is a way to convert it to a .cue), there are several games that I myself have experienced that need a proper rip in order to work:

Jet Moto SCUS-94309 == If not ripped correctly, no music will play when racing.

Tomb Raider II SCUS-00437 == If not ripped correctly, no music will play in the main menu. And if you select to enter Lara's House or Start a Game (new or old), the game will freeze.

Note, that when I was experimenting with different ways to back these games to the hard drive, that I was unable to back them up at all using the cdrdao in Linux. Furthermore, I wasn't even able to rip them in windows after trying 2-3 DVD/CD drives, until I finally found one that read them correctly.

Just my thoughts.

Yes, the script uses cdrdao with the almost the same options as the MegaGames guide. However, I managed to rip many games with cdrdao but I haven't run into many problems, and most titles rip correctly. It is possible that some CD/DVD drives rip better than others. (for me that's true, I have one CD drive that rarely rips correct images)

Please remember, I am not a professional programmer :) 
I only wanted to make it easy for gamers who are newcomers to Linux to find a point-and-click way to do rip their games, as they can easily do with windows (which BTW has a huge amount of such tools) It is also more convenient as the script will put the image files in a folder and save you the time it takes to type the command and create folders for the images (especially if you rip a lot of games)

---

### Post by dfreer on 2008-06-10
Just thought you might want to let people know that it will not rip every game correctly, YMMV. You might also want to implement the .toc -> .cue converter, as well. I like the GUI interface, much better than the script :D

---

### Post by verb3k on 2008-06-12
> **dfreer said:**
> Just thought you might want to let people know that it will not rip every game correctly, YMMV. You might also want to implement the .toc -> .cue converter, as well. I like the GUI interface, much better than the script :D

I am happy you liked it :)
Thanks for your feed back.

---

### Post by Infinite Indefinite on 2009-02-21
Just thought I'd add that I used it to back up both King's Field II and Carnage Heart without any issues.  Also Dragon Seeds - that seems to work as well.

A very helpful program.

---

### Post by boglio on 2009-02-21
Pretty neat program, I just used it to rip TombRaiderIII and FIFA2002WC.


Worked flawlessly.

---

### Post by verb3k on 2009-04-10
@**Infinite Indefinite** and **boglio**: I'm glad you liked it :)

---

### Post by RealG187 on 2009-09-25
Are they in standard BIN/ISO format? Can I convert them for my PSP?

---

### Post by mister_playboy on 2009-09-26
I will give this a try.  Currently, I use Alcohol 120% on my Win2000 box to rip, and then mount the MDF/MDS in Ubuntu with CDEmu.

---

### Post by RealG187 on 2009-09-27
> **mister_playboy said:**
> I will give this a try.  Currently, I use Alcohol 120% on my Win2000 box to rip, and then mount the MDF/MDS in Ubuntu with CDEmu.

You have a Win 2000 box? Is it an older machine?

If it is old, why would you use an old machine to do that? If it's not how could you use 2000 on a newer computer, doing almosr everything makes you "upgrade" to XP, yet another reason to hate the .Net Framework...

---

### Post by mister_playboy on 2009-09-28
> **RealG187 said:**
> You have a Win 2000 box? Is it an older machine?

If it is old, why would you use an old machine to do that? If it's not how could you use 2000 on a newer computer, doing almosr everything makes you "upgrade" to XP, yet another reason to hate the .Net Framework...

Yeah, it's an old laptop (1999) I got for free.  160MB of RAM... Win2000 is the best fit.  I had Xubuntu 8.10 on it, but the DVD drive and sound wouldn't work and the WiFi was very spotty.

It's taken a turn for the worse recently, though.  The backlight quit working, so it's VGA out only now... and something about the applet for the wireless card gimps after about 3 days without a reboot, and messes up explorer.exe.

I don't use it for anything serious otherwise... but I am not aware of a way to install and use Alcohol 120% successfully in WINE.

---

### Post by RealG187 on 2009-09-28
Can't you use a virtual machine?

---

### Post by mister_playboy on 2009-09-29
> **RealG187 said:**
> Can't you use a virtual machine?

I haven't tried it recently, but it didn't work on my first attempt.  Alcohol wasn't able to communicate with the disk drive correctly.  The program would seem to be reading/writing, but nothing was actually being output as a file.

---

### Post by cyrexxx on 2010-05-28
Hey there
I tried to use PSXIM but actually the GUI doesn't recognize my CD/DVD drive on my notebook. Any suggestions how to solve this problem?

EDIT: 
Ok seems like i got it working so far.
Since my drive isn't in the fstab i had to alter the code a bit:

def drive_detect():
    #detection=os.popen("awk '/cdrom/{print $1}' /etc/fstab").read().split()
    #for item in detection:
        combo.append_text("/dev/sr0")

Now i'm gonna check if it worked :P

---

### Post by unused_bagels on 2010-08-05
> **cyrexxx said:**
> Hey there
I tried to use PSXIM but actually the GUI doesn't recognize my CD/DVD drive on my notebook. Any suggestions how to solve this problem?

EDIT: 
Ok seems like i got it working so far.
Since my drive isn't in the fstab i had to alter the code a bit:

def drive_detect():
    #detection=os.popen("awk '/cdrom/{print $1}' /etc/fstab").read().split()
    #for item in detection:
        combo.append_text("/dev/sr0")

Now i'm gonna check if it worked :P
I'm having the same problem, but I have no idea what this workaround of yours means.  Can someone tell me how to put this in the code so I can get this program to work? I've got a scratched disc, and every download of it is a .ccd and I just want to back it up... ;-;

---

### Post by Mazukambax on 2010-12-05
> **unused_bagels said:**
> I'm having the same problem, but I have no idea what this workaround of yours means.  Can someone tell me how to put this in the code so I can get this program to work? I've got a scratched disc, and every download of it is a .ccd and I just want to back it up... ;-;

I'm having the same problem here, don't understand whats happening.

---

### Post by phetre on 2010-12-12
Hi unused_bagels and Mazukambax,

Cyrexxx's edit works for me. Press Alt-F2 to open the "run command" dialog, then type: ```
gksu gedit /usr/bin/psxim
``` Enter your password to continue (this gives you permission to edit the script), and you'll get a text editor with the contents of the file /usr/bin/psxim (which is in fact the entire PSXIM program).

Now find the section that begins with the line "def drive_detect():" and change it to look like cyrexxx's example. (Lines beginning with # are comments and may be omitted, but make sure you don't change the indentation: Python will know.) Mine reads:

```
def drive_detect():
    # Edited according to Ubuntuforums thread 664656, post #43 (cyrexxx)
    # detection = os.popen("awk '/cdrom/{print $1}' /etc/fstab").read().split()
    # for item in detection:
    #     combo.append_text(item)
    combo.append_text('/dev/sr0')

```

Then save the file, close the text editor, and restart PSXIM. The selection box should be pre-filled and ready to go.

In the long term, it would be better to replace the drive-detection function with something like the df command, which shows drives mounted via fstab, mtab, and other means. I'll give that a try, once I finish re-playing all my PS1 games. :)

Thanks, cyrexxx!

---

### Post by malkavsheir on 2010-12-12
> **phetre said:**
> 

```
def drive_detect():
    # Edited according to Ubuntuforums thread 664656, post #43 (cyrexxx)
    # detection = os.popen("awk '/cdrom/{print $1}' /etc/fstab").read().split()
    # for item in detection:
    #     combo.append_text(item)
    combo.append_text('/dev/sr0')

```

I feel dumb... I tried Cyrexxx's edit and got nothing... When I revisited today, I saw that I forgot the final ")"... just sad

---

