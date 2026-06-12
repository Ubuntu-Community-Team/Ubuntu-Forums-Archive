---
title: "X crashed after XGL attempt"
date: 2007-09-09
forum: Desktop Environments
---

### Post by WolfLust on 2007-09-09
Hello all, 
I was trying to install XGL to get all the eye candy effects, but I think something went wrong during that.

Now whenever I am at the session logon screen, the monitor flashes for about 10 seconds and then I get a message saying: 

FAILED TO START THE X SERVER IT IS LIKELY THAT IT IS NOT SET UP CORRECTLY, and I can either check the log or continue.

Everything works fine and I can start Ubuntu but I always get this error and the flashing screen at first, and XGL doesn't work, no eye candy at all.

Here's the Xorg.0.log hosted on [http://www.metalje.com/Xorglog.txt](http://www.metalje.com/Xorglog.txt)

Thanks in advance guys :)

---

### Post by schauerlich on 2007-09-09
I have the same problem, but I was trying to install Beryl on my MacBook.

---

### Post by WolfLust on 2007-09-09
I installed Beryl and Emerald theme manager too, one of the tutorials asked for it for XGL.

---

### Post by WolfLust on 2007-09-09
Help, anyone?

---

### Post by WolfLust on 2007-09-11
I removed Beryl, but it's still the same.

I'm on GNOME if that helps.

---

### Post by Jouke74 on 2007-09-11
People should really learn to check their hardware first, and subsequently the scripts and recipes to install Beryll or compiz before applying them. (And also try to figure out what they are doing at each step).

@Wolflust with Raedon 9800
You are using the **open-source ATI raedon driver**. Which does not need XGL(!). You can run it with AIXGL and basically the only thing you really need to do is turn on the desktop effects. That gives you the old compiz, and it should be working fine. Subsequently, you can install Beryl (after deleting the old compiz) or Compiz fusion. No need for XGL or any other extra stuff.

The scripts for XGL assume that you have installed the **closed-source ATI FGLRX driver** ,which is not active or installed on your system. Hence, the first startxgl script, which assumes that there is an FGLRX driver, will fail when initialising the XGL server. As a failsafe Gnome GDM subsequently starts another normal Gnome session. 

To get rid of this, select the normal gnome session at the inlog screen and make this default. 

Delete the scripts that you have made probably in usr/local/bin... 
/usr/local/bin/startxgl.sh
/usr/local/bin/startxgl.sh

That will remove the error.


@ Others :
ATI video cards ranges Raedon 9### - X800 > should use opensource ATI drivers with AIGLX.
X1#000 series ATi Raedon cards > can use FGLRX drivers only (install them using the restricted drivers manager). 
Subsequently redo the recipe you tried.

---

### Post by WolfLust on 2007-09-11
thank you for replying
your recommendation is to get AIXGL, download the scripts, and then install compiz fusion? 

should I update to X11R7.3 too?

---

### Post by Jouke74 on 2007-09-11
Did it work out, what I wrote? Is the error gone?

1. Delete the scripts and set the session back to normal.
2. Log into normal Gnome.
3. Go to Preferences > Desktop effects.
4. Click on enable.
5. Write here what happened.

---

### Post by WolfLust on 2007-09-11
I deleted the scripts, reinstalled X and reconfigured it, did not choose XGL in the X installation list, restarted and got the same error.

How to use AiXgl ? I couldn't figure out how to download or configure it.

I don't see Desktop Effects either, I downloaded compiz-freedesktop-gnome and got GL Desktop instead.

---

### Post by Jouke74 on 2007-09-12
"Desktop effects" is under your preferences menu as an option. Nothing to download for that. The other comments you gave are more troublesome. There is something wrong in your Xorg.conf under /etc/X11, the question is what. Could you post the log that it gives when you get the error, and if possible the xorg.conf itself. 

The desktop effects are easy to set-up after X-server is working. AIGLX is an option you need to add in your Xorg.conf file, and it will turn on the possibility for the composite extension. If you have composite you can run the desktop effects afterwards.

---

### Post by WolfLust on 2007-09-12
Thank you again for your reply Jouke74, but I found nothing titled "Desktop effects" in the preferences menu.

Are you talking about this log? [http://www.metalje.com/Xorglog.txt](http://www.metalje.com/Xorglog.txt)

How/where do I add the AIGLX option?

Thank you very much.

---

### Post by Jouke74 on 2007-09-12
- No desktop effects, then which version of Ubuntu are you using? Feisty Fawn or other?
Check this site : [http://www.neohide.com/ubuntu-desktopeffects-default-in-feisty-fawn](http://www.neohide.com/ubuntu-desktopeffects-default-in-feisty-fawn)
In order to find it under Feisty Fawn. If you need to download and install new programs I will write about that :)

- I have read your logfile earlier. However I need to know what text is in the following file xorg.conf; Open a terminal and type:

cd \etc\X11 [enter]

sudo cp xorg.conf xorgoutput.txt [enter]

sudo gedit xorgoutput.txt [enter]

Copy and paste the text into a reply here.

- The AIGLX option I will go into later, after this error is gone because now it will only make things more difficult.

- Please also read the output log when the X-server shows the crash and type that information here.

Read also: [http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)
At the bottom of this page there also links to AIGLX en XGL.

You need to know this stuff otherwise I can't help you. I can't make it happen if you don't understand what you are doing and just basically trying if random things work (I am sorry). How old is your ubuntu install and what did you do with it already? Because a reinstall might be a better option to start with. At least I know what is on there already (and what not).

---

### Post by WolfLust on 2007-09-12
I'm on dapper

I am not on my pc at the moment, I will paste it as soon as i can :)

Thanks for your reply

---

### Post by Jouke74 on 2007-09-12
Ahhhh.... now I understand. With Dapper you can forget the desktop effects. Most of the software you need is not installed or is too old to be compatible (newer X-server > 7.2 with support for AIGLX). It probably lacks the proper dependenvcies of XGL, and indeed no Desktop effects aka Compiz 0.3.6 to be found in the menu. 

Then my first suggestion is to install Feisty Fawn. Basically, download a new Feisty Iso and burn it to CD. Backup all your pesonal files, or even your complete home folder with all your settings and install the new OS. To test how the distro is going to work out, you can download the desktop CD and start Ubuntu from this one (costs you only one CD and here you can also try to enable the desktop effects).

---

### Post by WolfLust on 2007-09-12
Will do.
Thanks 4 your help

---

### Post by pheonixind on 2007-09-12
All I know is that beryl, nor xgl works on my x64 Feisty.  Here are my system specs.

Dell Inspiron 1501
2GB RAM
ATI 256MB card. (on board, not discreet)
Feisty Fawn x64

---

### Post by Jouke74 on 2007-09-12
@ pheonixind : I also run 64 bit, but it should not make a difference with 32 bit in this case. You need to be more specific about your video card, as that determines everything.

---

### Post by WolfLust on 2007-09-16
Alright finally on Feisty, now where to go? I tried to follow a few tutorials regarding compiz-fusion but they didn't work.

---

