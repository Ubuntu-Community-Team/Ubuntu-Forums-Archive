---
title: "KDE keyboard problems"
date: 2006-09-19
forum: Desktop Environments
---

### Post by Scheater5 on 2006-09-19
Today, inexplicably (to me, anyway), my keyboard stopped responding in KDE.  I had already logged in, and had actually been working for a few hours, when I returned from a break and could no longer type.  The mouse worked, the desktop responded, programs opened and closed, but no keyboard response.  I rebooted, could enter my name and password fine, KDE loaded up and the same problem.  It works fine in Gnome (which is where I am typing this from) on the same system (A Dell Inspiron 9300, KDE and Gnome installed on the same Ubuntu).  Anyone know what this problem is?  
Googling it was difficult to find any similar problems.

---

### Post by Scheater5 on 2006-09-20
Googled it again, found a couple more similar problems but none of the solutions worked for me.  My region is in fact set to US, and the "keyboard layout" is set to Dell 104 key keyboard (I've tried some others, including some generic ones, but to no avail).  The keyboard responds during login normally - and, as in the cases I found on google, will react when I hold the key down by repeating, but simply pressing a key gets no response.  It's very annoying to type, and I am almost to the point where I use KDE exclusively when this glitch showed itself.  One topic suggested adding Option "XkbVariant" "nodeadkeys" to /ect/x11/xorg.conf, however, I "do not have permission" to change this file - I would assume that requires sudo priviliges, but how do you "sudo" a save command from a text editor?

---

### Post by editrix on 2006-09-21
> **Scheater5 said:**
> One topic suggested adding Option "XkbVariant" "nodeadkeys" to /ect/x11/xorg.conf, however, I "do not have permission" to change this file - I would assume that requires sudo priviliges, but how do you "sudo" a save command from a text editor?

Open the file as root. e.g., sudo nano <name of file> on the directory where it lives.

---

### Post by Scheater5 on 2006-09-21
Well, good news and bad news.  What I was missing was a knowledge of the command "nano" - thanx for that, it will likely come in handy often.  I opened that conf file, added the suggested line, and saved succesfully.
The bad news is that it didn't fix the problem.  I don't understand how "repeat" could work, but not the initial keystroke?

---

### Post by Scheater5 on 2006-09-21
Ok, how about this:
What would happen if I uninstalled and reinstalled "kubuntu-desktop"?  
I use several programs and packages from KDE and Gnome when I am in the other desktop environment.  Would I lose any of the KDE programs (i.e. the programs that use the QT toolkit, for instance) and would they still function?  I had not gotten around to customizing the environment itself, so that is no big loss, but will my programs and files remain intact, assuming a succesful instalation?

---

### Post by Scheater5 on 2006-09-24
[http://dot.kde.org/1109582845/1109607846/1111656918/](http://dot.kde.org/1109582845/1109607846/1111656918/)

Would there need to be any modification to these instructions for Ubuntu from Suse??

---

### Post by vaetor on 2006-09-25
This may seem simplistic, but you may have the 'slow keys' function enabled.  To disable this try (Kubuntu): System Settings -> Regional and Access. -> Access. -> Key Filters(or something there abouts) -. untick "Slow Keys".

Symptoms sound about right.

Hope that helps anyone that finds this.

---

### Post by Scheater5 on 2006-09-26
THAT'S WHERE THAT THING IS!  I had suspected it might be something along those lines, but I couldn't find it - so I assumed that suspicion was wrong.  "Keyboard repeat" is under "keyboard" in "system settings" - so that's what I tried.  When altering those setting didn't help, I thought it must be something more complex.  Doesn't it seem a bit counterintuitive that a keyboard setting would be under "region and accessability"?  Well, it turns out it was "slow keys," and now KDE is usuable again!  Thanx vaetor

---

### Post by dsmithhfx on 2008-01-14
I'm having the same problem testing out the kubuntu 7.10 live cd on a "white box" desktop pc wiht PS2 kb... it boots up fine, but no keyboard. The "slow keys" was not on when I checked, but I turned it on and off to see if it would fix the problem. It didn't. Any ideas?

---

### Post by Scheater5 on 2008-01-16
Have you tried another keyboard?  Your problem may be that the keyboard type, or possibly the PS2 port on that computer (although I have never heard of mouse but not keyboard working on any motherboard with linux).  Try a usb keyboard.  
Either way, you have a different problem than me - you would be well served to start a different thread.

---

