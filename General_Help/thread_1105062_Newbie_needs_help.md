---
title: "Newbie needs help"
date: 2009-03-24
forum: General Help
---

### Post by Streamlined on 2009-03-24
Hi,

I'm new to Ubuntu, and i'm having problems opening files, specifically video files.

Whenever i try to open a video file, the program opens but then abruptly closes.

I've tried downloading VLC and installing that, but it also does the same thing....is there something i'm not doing right?

This problem used to happen with Open Office as well, but that spontaneously stopped.

Please help!

---

### Post by .:Justus:. on 2009-03-24
> **Streamlined said:**
> Hi,

I'm new to Ubuntu, and i'm having problems opening files, specifically video files.

Whenever i try to open a video file, the program opens but then abruptly closes.

I've tried downloading VLC and installing that, but it also does the same thing....is there something i'm not doing right?

This problem used to happen with Open Office as well, but that spontaneously stopped.

Please help!

What type of file are you trying to open? Does the same thing happen with any other type of media file?

---

### Post by lindsay7 on 2009-03-24
Take a look at this. You need these downloads.

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html)

---

### Post by kanikilu on 2009-03-24
Try running vlc from the command line, go to Applications > Accessories > Terminal, then type *vlc* and press enter. You should see some output in the terminal, which is normal. Then try to play a file and look in the terminal for any errors.

If that doesn't yield anything useful, I would start looking through the logs (/var/log/) to see if anything shows up in there. I would probably start with Xorg.0.log, messages, and syslog...

---

### Post by prem1er on 2009-03-24
> **lindsay7 said:**
> Take a look at this. You need these downloads.

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html)

How do you know that, you don't even know what type of file he is trying to open or if the file that he is opening is corrupt.

---

### Post by kanikilu on 2009-03-24
> **lindsay7 said:**
> Take a look at this. You need these downloads.

[http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/install-mplayer-and-multimedia-codecs-libdvdcss2w32codecsw64codecs-in-ubuntu-810-intrepid-ibex.html) Missing codecs was my first thought as well, but it sounds more like vlc is "crashing" (maybe not, but that's what it sounds like to me), and especially since Open Office was doing this makes me think there's something else up...

---

### Post by Streamlined on 2009-03-24
Thanks for the help, i will try your suggestions.

Here is some more information, i don't know if it will help.

The file i'm opening is an .avi and it currently opens and works fine on other operating systems like Windows, unfortunately, i haven't had the opportunity to try it on another Ubuntu system.

Also, when the Open Office program was doing the same thing, i was trying to open a .doc file OR i was trying to cut and paste from the internet.

But like i was saying before, that problem has somehow stopped on its own.

I tried Kanikilu's suggestion and this is what it says:

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 140.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  140 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  83
  Current serial number in output stream:  84

I'm not sure what this means...anyone else?

Thanks again.

---

### Post by kanikilu on 2009-03-24
A [couple](http://www.google.com/search?q=x11+video+output+error%3A+X11+request+140.19+failed+with+error+code+11[/url) [searches](http://www.google.com/search?q=X+Error+of+failed+request%3A+BadAlloc+(insufficient+resources+for+operation)[/url) came up with a lot of hits (particularly the first one)...see if you can find anything.

This bug report sounds very similar:

[https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/281743)

Admittedly, I didn't read through the whole thing, but see if you can find anything out, or add to the report if necessary...

---

### Post by lindsay7 on 2009-03-24
I know that because, I could not get any of the media player to work correctly until I installed,  

sudo apt-get install w32codecs libdvdcss2

It may not fix the problem he has but if he does not have this he will still need it.

---

