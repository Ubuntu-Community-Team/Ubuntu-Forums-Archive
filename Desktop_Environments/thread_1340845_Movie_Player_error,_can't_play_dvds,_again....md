---
title: "Movie Player error, can't play dvds, again..."
date: 2009-11-29
forum: Desktop Environments
---

### Post by jaime256 on 2009-11-29
Is anyone else having this problem. My friend gave me a dvd set and I'm trying to watch it on my Ubuntu 9.04, but it keeps giving me this error. I have installed the Ubuntu restricted packages, but still having no luck. I hadn't used any dvd's so I didn't know this was still not working. I know, the message is not very helpful so I can't tell what else is missing.

---

### Post by Locutus_of_Borg on 2009-11-29
mplayer dvd://

try that, if it works, then the problem is you are using totem

---

### Post by jaime256 on 2009-11-29
No that didn't work. I got this and installed mplayer, but still doesn't work.

---

### Post by Locutus_of_Borg on 2009-11-29
what does it say after installing mplayer and running that command?

---

### Post by jaime256 on 2009-11-29
It install fine. In any case I went and removed all my video programs just to see if anything was conflicting. Then I tried other dvd movies I have but all the dvd's aren't working. So I re-installed the player and it plays all my avi files fine, even a vob that's on the hard drive so I think I found my culprit. I can't test another dvd drive because I don't have one so until I find one I won't know for sure. But I'm almost convinced it's that. Thanks for trying though. I don't want to keep you guys trying until I'm sure of what it is. Now I just have to remember that. :)

---

### Post by jaime256 on 2009-11-29
Okay, I just thought of something. The drive reads the data disks fine but not the dvds. I think they used to work, can't remember for sure. But was there any updates for viewing dvds specifically on 9.04? I'm just curious now. If so then I may not need to look into getting another dvd burner which is what I currently have. Well, let me know what your thoughts are since I'm just thinking through this.

---

### Post by Locutus_of_Borg on 2009-11-29
apt-get install ubuntu-restricted-extras should get you what you need to watch DVD's

i remember that totem sometimes was a pain in the *** to use with anything though, thats why i recommended mplayer, xine is another program useful for DVD watching as it allows you to use the mouse in the menu selection screens

the files you need though are libdvdread, libdvdnav, and libdvdcss

---

### Post by jolx on 2009-11-29
[does this help?]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by jaime256 on 2009-11-30
I typed in the first line and the system change to manual but told me that I already have the latest and to do autoremove to remove other stuff I no longer needed. I did the autoremove but still can't play a dvd.

> **jolx said:**
> [does this help?]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by jaime256 on 2009-11-30
The system tells me it's already the latest version that's installed. Even though I did this after the autoremove. Weird.

> **Locutus_of_Borg said:**
> apt-get install ubuntu-restricted-extras should get you what you need to watch DVD's

i remember that totem sometimes was a pain in the *** to use with anything though, thats why i recommended mplayer, xine is another program useful for DVD watching as it allows you to use the mouse in the menu selection screens

the files you need though are libdvdread, libdvdnav, and libdvdcss

---

### Post by jacobs444 on 2009-11-30
you need libdvdcss2.deb and vlc media player. Mplayer is a pain

---

### Post by jaime256 on 2009-11-30
I had VLC installed but was not working either. I'll check that other file. Apparently libdvd is part of the restricted packages that I already have installed. So I have no idea what else might be other than the drive itself. Will let you guys know whenever I get a chance to try another drive.

> **jacobs444 said:**
> you need libdvdcss2.deb and vlc media player. Mplayer is a pain

---

### Post by Digikid on 2009-11-30
Try this.  Hopefully it works in 32 bit as well.

[http://ubuntuforums.org/showthread.php?t=1322148](http://ubuntuforums.org/showthread.php?t=1322148)

---

### Post by jaime256 on 2009-11-30
I tried that and this still not playing. Haven't installed vlc again, but I'm getting this error after I did this.


> **Digikid said:**
> Try this.  Hopefully it works in 32 bit as well.

[http://ubuntuforums.org/showthread.php?t=1322148](http://ubuntuforums.org/showthread.php?t=1322148)

---

### Post by Locutus_of_Borg on 2009-12-01
can you please paste the output of: 

mplayer dvd://

---

### Post by jaime256 on 2009-12-01
Well, good news, I restarted the computer, and it didn't work, but then I did it again, and now I can watch the dvd. Really weird, don't know why, but it seems to work now after that. Thank you guys even though I'm not sure what worked. Here's the output to that...

jaime@Z:~$ mplayer dvd://
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer-nogui
Try: sudo apt-get install <selected package>
bash: mplayer: command not found

---

### Post by jaime256 on 2009-12-01
I just finished a clean install on another computer, a Dell D600 laptop of Ubuntu 9.04 and after all the updates which took forever I tried playing the same DVD on this computer, but it won't play either so I know it was not the hardware itself. Here are the errors after all updates finished and the computer was rebooted. I just updated the 5400 HD with a 7200RPM HD. Because this is an old laptop it tells me the battery is low or that it's old. Never seen that since I took out one of the batteries out and put in the dvd drive on it. Funny thing with the battery, but I thought you guys would like to know it has something to do with the OS not the hardware.

---

### Post by JBAlaska on 2009-12-01
You have to this everytime you do a fresh install.

 ```
sudo apt-get install libdvdread4
```

Then open a terminal window and execute: 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by Locutus_of_Borg on 2009-12-01
> **jaime256 said:**
> Well, good news, I restarted the computer, and it didn't work, but then I did it again, and now I can watch the dvd. Really weird, don't know why, but it seems to work now after that. Thank you guys even though I'm not sure what worked. Here's the output to that...

jaime@Z:~$ mplayer dvd://
The program 'mplayer' can be found in the following packages:
 * mplayer
 * mplayer-nogui
Try: sudo apt-get install <selected package>
bash: mplayer: command not found

chist, install the damn program, and THEN tell me what the output is :|

---

### Post by jaime256 on 2009-12-01
Sorry, didn't know what you meant. I thought you meant the output I got when I looked for it which obviously is not there. I don't need to install that since it already works.

chist, install the damn program, and THEN tell me what the output is

---

### Post by jaime256 on 2009-12-01
Thank you, this seems to work. Here's what it looks like, I did the autoremove after these steps and still works fine. I should note that in the previous set up for the desktop, when I try to fast forward, the cd just tries to go, but then it hangs and you can't do anything except restart the player and start over. You can use the chapter forward though.

On these last steps, the regular fast forward works fine and the dvd does not hang when I use it on the laptop. Again, the regular fast forward does hang the movie when I use it on the desktop with the other steps before these. I thought you guys should know.

> **JBAlaska said:**
> You have to this everytime you do a fresh install.

 ```
sudo apt-get install libdvdread4
```

Then open a terminal window and execute: 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by jolx on 2009-12-01
> **JBAlaska said:**
> You have to this everytime you do a fresh install.

 ```
sudo apt-get install libdvdread4
```

Then open a terminal window and execute: 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

lol
is this not exactly the same as what was in the link i posted after doing a google search? :popcorn:

---

### Post by jaime256 on 2009-12-01
I followed the links on the desktop and it made it worked, but the movie stops if I try to fast forward. When I followed just the last two lines on the clean install on the laptop, then everything works just fine. So basically even though I try following many of these, I got two separate results which is why I wanted to make sure I put everything down so you could see the difference. I may have to go back and re-read my thread but I guess instead of trying every link, just try the last two suggestions and that may work without having to try to follow all the instructions of all the links, if that makes any sense. I just like to document things so that it will hopefully help others too. Or at least see what I've done so they won't make the same mistakes when I do make them. Now I got a whole other problem ripping a cd. I'm about to make that thread. :)

You are right, that's what you posted earlier, but it didn't work on the workstation I was working on at the time I was writing. I then tried it on the clean install I did on the laptop and I was at the end and didn't check back so I missed it. That's when it did worked, on my laptop install. So I was checking two different computers and that's probably why I said it didn't work. Just went back and checked and well, I should re-read my thread in case I miss something and stop doing so many things at once. :)

---

### Post by d0ubl3a on 2010-02-13
Hello, I encountered the same problem. The difference is that I can't  make it work whatever I try. I installed the Medibuntu repositories, I  installed libdvdcss, I tryed installing libdvdcss2... etc. I tried quite  a lot of multimedia players. I played non-encrypted dvds with VLC and  it worked just fine. But when I start this one... or these ones...  because it is a 14 DVD piano course...  I  get the menu... but I can't press any of the buttons. If I open the  dvds and go to video... there are a couple of .bup, .info and .vob  files, and I can't open them with VLC.
I tried to play them with totem, but it does not work. If I want to open  the disc I get the error:
"Could not open location; you might not have permission to open the  file."
And if I try to open the .vob files I get the error:
"Could not read from resource"
I tried opening the disc with totem from the terminal... and this is  what I get:


```
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: no file info
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists

libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists
```Please help me... it's really bugging me... and I need those courses...

---

### Post by jaime256 on 2010-02-14
Make sure you reboot after the changes. I noticed that just doing them or logging out didn't do much. Also, try doing the sudo autoremove, sometimes other stuff gets stuck or left that didn't quite finished and this sometimes helps. One way to find out if things are working okay is check for the new updates. If that doesn't work, something else is not working correctly. I know this is very general but I'm trying to think about just the simple stuff right now without getting too deep into what happened since you can go nuts doing that too. By the way, do the dvds work okay on other players? Sometimes the actual media can be pretty picky. Just another thing that I remember, but if you see the vob files and actually browse them, then it may just be your program,so that's a good thing.

> **d0ubl3a said:**
> Hello, I encountered the same problem. The difference is that I can't  make it work whatever I try. I installed the Medibuntu repositories, I  installed libdvdcss, I tryed installing libdvdcss2... etc. I tried quite  a lot of multimedia players. I played non-encrypted dvds with VLC and  it worked just fine. But when I start this one... or these ones...  because it is a 14 DVD piano course...  I  get the menu... but I can't press any of the buttons. If I open the  dvds and go to video... there are a couple of .bup, .info and .vob  files, and I can't open them with VLC.
I tried to play them with totem, but it does not work. If I want to open  the disc I get the error:
"Could not open location; you might not have permission to open the  file."
And if I try to open the .vob files I get the error:
"Could not read from resource"
I tried opening the disc with totem from the terminal... and this is  what I get:


```
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: no file info
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists

libdvdread: Using libdvdcss version 1.2.10 for DVD  access
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.IFO failed
libdvdnav:grin:VDOpenFileUDF:UDFFindFile  /VIDEO_TS/VIDEO_TS.BUP failed
libdvdread: Can't open file VIDEO_TS.IFO.
** Message: Error: Could not read title information for DVD.
resindvdsrc.c(361): rsn_dvdsrc_start (): /GstPlayBin2:razz:lay/GstURIDecodeBin:uridecodebin0/RsnDvdBin:source/resinDvdSrc:dvdsrc:
system error: File exists
```Please help me... it's really bugging me... and I need those courses...

---

