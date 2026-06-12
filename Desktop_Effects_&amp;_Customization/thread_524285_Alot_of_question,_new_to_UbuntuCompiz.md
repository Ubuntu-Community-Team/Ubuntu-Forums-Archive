---
title: "Alot of question, new to Ubuntu/Compiz"
date: 2007-08-12
forum: Desktop Effects &amp; Customization
---

### Post by Aslanov on 2007-08-12
I thought this would be a less intimidating transition from windows, but its not.

First is the nvidia driver. on Windows, my 6800GS could get 1600x1200 resolution, and iwh thte "restricted driver" stuff it only gets 1028.  Can someone direct me to an nvidia driver for the GeForce 6 Series that will allo wme to have 1600x1200 resolution?

Secondly, after installing compiz fusion, everything in my windows, like in firefox is HUGE, WAY bigger than teh 1028 resolution settings, i try Ctrl+ -, but that only changes the text size but the window, everything in windows is ridiculously large

thirdly, How can i install a DOCK inplace of the taskbar that i see in all these screenshots of Compiz.

Help would greatly be appreciated.

---

### Post by scrooge_74 on 2007-08-12
Well I am not a big fan of using Compiz, but probably you need to correct your driver problem so the other problem will probably resolve itself.

Check this [link]("http://albertomilone.com/latest_nvidia_udsf_feisty.html") for a solution

---

### Post by Aslanov on 2007-08-13
it didnt work.....i still have the same resolution options.

---

### Post by Brezeck on 2007-08-13
Hey Aslanov! I also used to have this problem. It's easy to solve!

First, you should get the newest graphic card driver
Then, if you want to use compiz of beryl, you should install them first, i think.

Next:

sudo gedit /etc/X11/xorg.conf      (in terminal)

now, edit the file:

find the paragraph of Section &#8220;Screen&#8221;
Mine is like this:


Section &#8220;Screen&#8221;
Identifier &#8220;Default Screen&#8221;
Device &#8220;Generic Video Card&#8221;
Monitor &#8220;SyncMaster&#8221;
Defaultdepth 24
SubSection &#8220;Display&#8221;  
Depth 1
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 4
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 8
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 15
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 16
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 24
Modes &#8220;1440×900&#8243; &#8220;1280×1024&#8243; &#8220;1280×960&#8243; &#8220;1152×864&#8243; &#8220;1024×768&#8243; &#8220;832×624&#8243; &#8220;800×600&#8243; &#8220;720×400&#8243; &#8220;640×480&#8243;
EndSubSection
EndSection

(Yours may be different but it is not important)

Look, the "n x n" is just the resolutions the system can give you. Now edit one you don't need to the resolution you want. (Maybe you can also add one)
Then save it and restart the Xserver, now you can easily change the screen resolution! :lolflag:

---

### Post by Aslanov on 2007-08-13
AWESOME, resolution fix worked!

now can anyone tell me how to get a Dock inplace of the taskbar?

---

### Post by praet on 2007-08-13
The dock is called Avant Window Navigator, or awn for short.

[http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)

Which has now moved to:

[https://launchpad.net/awn](https://launchpad.net/awn)

I installed it from Trevino's eyecandy repo. [http://3v1n0.tuxfamily.org/](http://3v1n0.tuxfamily.org/)
```
$ sudo apt-get -s install avant-window-navigator
```

---

### Post by Aslanov on 2007-08-13
hey guys, i got the resolution working as you know, and installed the new driver. but now for some reason Compiz wont work
i get the

Failed Composite..something or other
It is impossible for compiz to run on your system.

i tried uninstalling and reinstalling, but i still get hte same error, how do i COMPLETELY remove Beryl and Compiz then reinstall it?

---

### Post by Brezeck on 2007-08-13
I suggested you to install compiz fusion first before you solve your resolution problems, cuz' when i was facing the same problem like you, i did it wrong, got the same result.

What graphic card do you use? ATI? If so, remember to setup XGL

---

