---
title: "No desktop"
date: 2007-06-16
forum: Desktop Environments
---

### Post by Ajiah on 2007-06-16
Good evening, fellow Ubuntu citizens!

  I took my dive into linux not too long ago, and I clearly have much to learn. Today I tried to log-in (multiple times, I might add), and my desktop is blank. The log-in prompt disappears, but that is about it. No top navigation bar, no bottome bar, and no icons on my desktop. My wallpaper wont even show! 

  I checked the console, and the last thing it says is 'Running local boot scripts /etc/rc.local . No error is given or anything.

  Another odd observance is that a square box - gray in color - eventually pops up in the top left corner of the screen. I can do nothing with it, but when my cursor goes over it, it turns into the symbol that usually shows over text fields. (Still, I can't type anything in it.)

 Anyone have any idea why my desktop is gone?

---

### Post by ShareBuntu on 2007-06-16
I have the same problem. The only solution that works for me at this point is to reboot. [http://ubuntuforums.org/showthread.php?p=2850234]("http://ubuntuforums.org/showthread.php?p=2850234")

---

### Post by bigken on 2007-06-16
at the prompt try this 

sudo aptitude install ubuntu-desktop

then sudo apt-get update

sudo apt-get upgrade

---

### Post by ShareBuntu on 2007-06-16
> **bigken said:**
> at the prompt try this 

sudo aptitude install ubuntu-desktop

then sudo apt-get update

sudo apt-get upgrade
I don't think that's the problem. It's a bug in gnome-panel and/or nautilus.

---

### Post by bigken on 2007-06-16
> **'Ace[of]Bytes said:**
> I don't think that's the problem. It's a bug in gnome-panel and/or nautilus.

cant hurt to try ;)

---

### Post by Ajiah on 2007-06-16
Well, I first tried the advice that Ace got when he posted his question. After typing killall gnome-panel nautilus, I recieved something stating that 0 processes had been killed. (So, my desktop - essentially - is not even running? Odd.)

 I then attempted your adive, bigken. I was able to execute the first and last command successfully, but I can't seem to get a connection in order to update anything.

  Keep in mind that I am doing this all from the command prompt. (Reached by pressing ctrl+alt+F1 .) I can not get anything in graphic-mode.

 I tried to run things - just to see if I could. I was unable to get anything to run from prompt, an error stating "Cannot open display" shows up every time.

EDIT:

 Also, right now I am running from Live CD. Anything I can do from here to try and correct the problem?

---

### Post by ShareBuntu on 2007-06-16
I gave that a shot but it's already installed.

---

### Post by Ajiah on 2007-06-16
Not even a reboot helps me, Ace. Lucky! 
:D

 I hope we get this sorted out soon. Live CD is slow.

---

### Post by bigken on 2007-06-16
try booting in recovery mode then run the comands 

also try startx

---

### Post by ShareBuntu on 2007-06-16
> **Ajiah said:**
> Not even a reboot helps me, Ace. Lucky! 
:D

 I hope we get this sorted out soon. Live CD is slow.
It's completely random. I don't reboot often but multiple reboots eventually loads everything.

---

