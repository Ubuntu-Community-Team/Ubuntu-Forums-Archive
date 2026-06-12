---
title: "Kaffeine: how to install proprietary codecs?"
date: 2005-04-08
forum: Desktop Environments
---

### Post by Jagasian on 2005-04-08
Is it possible to install Windows, Real Media, and Quicktime codecs via Kynaptic?  If not, can somebody please right an easy to follow howto that describes how to install said codecs?

---

### Post by roadrash on 2005-04-08
not sure if this will work but go here: [http://www.mplayerhq.hu/homepage/design6/dload.html](http://www.mplayerhq.hu/homepage/design6/dload.html) & download the win32 codecs then put them into a folder /etc/win32

---

### Post by Alexandr on 2005-04-09
[QUOTE=roadrash]not sure if this will work but go here: [http://www.mplayerhq.hu/homepage/design6/dload.html](http://www.mplayerhq.hu/homepage/design6/dload.html) & download the win32 codecs then put them into a folder /etc/win32[/QUOTE]

Why /etc/win32 ?

...into a folder /usr/lib/win32 ?

---

### Post by digby on 2005-04-09
Did you try "apt-get install w32codecs"?

---

### Post by kb00heda on 2005-04-09
I downloaded the w32codecs package from the Ubuntu backports. Then I installed them manually. Did the same for libdvdcss2 and java. The packages can be fetched from:

[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/) 

since I have a i386 setup. The installation was as simple as

```
dpkg -i w32codecs_20050216-0.0_i386.deb
```
in my case. Otherwise have a look at

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

under section "How to install Multimedia Codecs?". Make sure to read "How to add extra repositories?" to get access to the Marillat repositories. If you do I think you will have w32codecs up and running in no time!  :-)

Also, the Ubuntu Starter Guide contains much information about tweaking Ubuntu, besides multimedia support. Give it a few minutes -- it will certainly pay back.

---

### Post by F for Fragging on 2005-04-14
I downloaded the w32codecs with kynaptic from the marillat repository, but it still doesn't seem to work. I double checked that all the codecs are placed in /usr/lib/win32, Kaffeine's Xine config also says that Xine checks for the codecs in that directory, but it still doesn't work.

I used this page to test: [http://www.nos.nl/nosjournaal/archief/index.html](http://www.nos.nl/nosjournaal/archief/index.html) (click "(BB)" to open a windows media stream) I opened the stream, Konqueror then asks if I want to play it with Kaffeine, I click yes, then it gives an error message saying that there "isn't a plugin to handle this resource".

trailers.apple.com works fine though, so I think that it's only a problem with the windows media and real codecs?

---

### Post by F for Fragging on 2005-04-16
*kick*

Am I the only one experiencing this problem?

---

### Post by !nkubus on 2005-04-16
[QUOTE=F for Fragging]*kick*

Am I the only one experiencing this problem?[/QUOTE]<


i'm having the same error even with mozilla and totem


so it might be a xine trouble since i'ts the same backend.

---

### Post by benobi on 2006-04-25
Same problem, Kaffeine just won't play anything even if w32codecs is installed.

---

### Post by mtron on 2006-04-28
sorry, wrong post

---

### Post by TitusDalwards on 2006-04-29
[QUOTE=digby]Did you try "apt-get install w32codecs"?[/QUOTE]

it isn't work for me.
console told me:
> package couldn't find
i changed my respitories and nothing changed.

---

### Post by SableSlayer on 2006-11-07
The PLF repository has a deb containing the Win32 Codecs. Once i installed the deb everything worked fine with Kaffeine. So you mite wanna give that a try. 

Link: [http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/](http://packages.freecontrib.org/ubuntu/plf/dists/edgy-plf/non-free/)

---

### Post by Qew on 2006-11-07
Look for libxine-extracodecs in Multiverse. After doing that, things should become peachy.

---

### Post by ziggig on 2007-08-24
this is what worked for me.

1. open a terminal window
2.type su
3.enter your root password (if you have one)
4.type sudo apt-get install libxine-extracodecs
5.open kaffeine and try to open your movies.
 worked for me hopefully you to.
bye.

---

### Post by SeePU on 2007-10-21
I get this:

apt-get install libxine-extracodecs
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libxine-extracodecs is not available, but is referred to by another pack                         age.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxine1-ffmpeg
E: Package libxine-extracodecs has no installation candidate

Is 'libxine-extracodecs' not applicable anymore?   I think I already have all my codecs installed but still have a video issue but I'm not sure if it's codec-related or not.

---

### Post by mtron on 2007-10-24
since gusty libxine-extracodecs is called "libxine1-ffmpeg" 

It was also ffmpeg with the old name, so it should work

---

### Post by analox on 2007-10-25
Hi all,

I install Kubuntu Gusty from the CD and have w32codecs + "libxine1-ffmpeg" with Kaffeine. I can play .mp3 in Amarok. However, only the sound appears when I open an AVI (or wmv, mpg...) but not the video...

Any solution suggested for this problem? ;)

---

### Post by analox on 2007-10-25
phew, i guess the problem comes with the desktop effect (compiz) or graphic driver... 
After going through the error message from mplayer (old but still great media player), i use this command to get the video played: > $ mplayer -vo x11
Finally done :D

---

