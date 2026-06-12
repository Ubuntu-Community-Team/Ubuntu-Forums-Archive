---
title: "Ok... So similar problem has been posted before, I must be &quot;thick&quot; (ET &amp; permissions)"
date: 2007-05-15
forum: Gaming &amp; Leisure
---

### Post by sloggerkhan on 2007-05-15
So I have ET installed, I think it's @ 2.60b (linux goes 2.55 -> 2.56 -> 2,60b?)
It works with sound and all. Have punkbuster active. (Though maybe only for root? Unsure about PB permissions.)

However, ET must run w/ sudo. So far I've tried chown and chmod to make the etmain and .etwolf folders writable by my user, but still won't work correctly as a regular user.

Running on feisty.

On a side note, On feisty, when full screen apps quit, instead of going back to full screen, it goes to that mode where the resolution is full screen, but the pixel resolution is not, so you have to pan around the screen. (Can reset by switching res in preferences once, but is kinda weird.)

---

### Post by Nesnej Trick on 2007-05-15
> **sloggerkhan said:**
> So I have ET installed, I think it's @ 2.60b (linux goes 2.55 -> 2.56 -> 2,60b?)
It works with sound and all. Have punkbuster active. (Though maybe only for root? Unsure about PB permissions.)

However, ET must run w/ sudo. So far I've tried chown and chmod to make the etmain and .etwolf folders writable by my user, but still won't work correctly as a regular user.
Could you be a bit more specific? Does the game not start at all or is punkbuster kicking you out for inadequate O/S permissions?
> 
On a side note, On feisty, when full screen apps quit, instead of going back to full screen, it goes to that mode where the resolution is full screen, but the pixel resolution is not, so you have to pan around the screen. (Can reset by switching res in preferences once, but is kinda weird.)
That sounds like some kind of driver problem. Are you running ET at a resolution different from your desktop resolution?

---

### Post by sloggerkhan on 2007-05-15
My problem is that is I run the game w/o sudo, I can't connect to games (program dies after connecting to server) or create new player profiles.

---

### Post by Memory.Dump on 2007-05-15
I had a problem with permissions and crashing when I tried to downlaod when giong to a server and the solution was psted at th end fo this thread

[http://ubuntuforums.org/showthread.php?t=440041](http://ubuntuforums.org/showthread.php?t=440041)

now it sounds slightly different but possibly the same, give it a go and see what happens I know the the sudo terminal command I was given towards the end worked for me with setting permissions that way

```
sudo rm -rf ~/.etwolf

```

note: you do not need to be in any specific dir to type that command it will work from anywhere in the terminal

---

### Post by houstonbofh on 2007-05-15
You should never have run the game as root.  Now the settings and prefs are owned by root.  If you just install it, and then run it as a user, it creates a prefs directory in you home.  I would remove and reinstall with the driections at [http://www.katanoon.nl/ubu-e/install.php](http://www.katanoon.nl/ubu-e/install.php)

---

### Post by sloggerkhan on 2007-05-15
I have a pref dir in my home.

I installed w/sudo 'cause I wanted it installed system wide.
I ran it first as a regular user. Only after problems there did I verify that it worked w/ gksudo.

Memory Dump, your advice worked, only now it says it can't find an official pak file and to make sure installation is updated to latest version. I think I just have to run updates and I'll be OK.

---

### Post by sloggerkhan on 2007-05-16
Thanks mem dump. Turns out most of my problem was updating ET in the wrong order. 
All is working. Only thing now is that sometimes it freezes in mid game and the same second or so of sound loops indefinately until I do a hard restart. 
I think it's related to ET using OSS. I'm going to try reducing bitrate and hope for the best.

---

### Post by Memory.Dump on 2007-05-16
heh, NP, I recently had the same issue and somebody had given me that advice and it worked, so I figured I'd share the love lol

---

### Post by Nesnej Trick on 2007-05-16
> **sloggerkhan said:**
> Thanks mem dump. Turns out most of my problem was updating ET in the wrong order. 
All is working. Only thing now is that sometimes it freezes in mid game and the same second or so of sound loops indefinately until I do a hard restart. 
I think it's related to ET using OSS. I'm going to try reducing bitrate and hope for the best.

If you have an ATI card and use the fglrx drivers, you'll need to paste this into the video card device section in your xorg.conf file:
```
Option "Capabilities" "0x00000800"
Option "KernelModuleParm" "locked-userpages=0"

```

---

### Post by sloggerkhan on 2007-05-16
I'm using ATI card with ati driver, actually...

---

