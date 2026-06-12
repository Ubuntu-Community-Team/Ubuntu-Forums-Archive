---
title: "Display problems"
date: 2011-09-28
forum: Desktop Environments
---

### Post by AJ4PH on 2011-09-28
I have the ubuntu 10.04/ backtrack 5 on my laptop. Ive some minor issues with it but nothing I cant search through the forums and find how to fix. Well, I went to install the same thing on my desktop and ran into some problems. Ran fine off the live cd, no problems at all. So I took the plunge and went for the full install. Everything went fine, restarted the pc and when I got to the point where you type startx to load the interface my monitor went to sleep. Does it everytime I try to start it. I found one fix where you hit E at the boot screen and edit the boot file ( I believe) typed something like quite splash nomodeset then restarted. It loaded the desktop fine so Im assuming I need to update a driver or something so thats where Im stuck. Im not sure how to find what my drivers are. Where to find em or anything. 

I have a P4 2.4 ghz
             1.5 ghz ram
             ATI Radeon 9600 all in wonder
             Ubuntu 10.04 backtrack5 gnome
Hopin to fix or get started on it before I go to work in a few hours so thats why I came here. Thanks alot guys.

---

### Post by realzippy on 2011-09-28
Just add the "nomodeset" to your grub and it should work...
There are no graphic drivers for your old card to install.

---

### Post by AJ4PH on 2011-09-28
Ok, so that should save and thats the last time I have to change it? I wasnt sure about the drivers. I noticed it looks a lil diffrent from the laptop. The laptop has a more crisp look to it, if that makes sense. Anyway thanks for the help.

---

### Post by realzippy on 2011-09-28
Yes,run

```
gksudo gedit /etc/default/grub
```

and add "nomodeset" ,like

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

Then run

```
sudo update-grub

```

---

### Post by AJ4PH on 2011-09-29
Well, everything was going good. I done all that before I left for work yesterday and I got to playing on the computer this morning and then I restarted it. Now Im back to the start again. Still doing the same thing. Cant figure out why it worked yesterday and I typed the same exact thing I did to get it to start and now it wont do anything.

---

### Post by realzippy on 2011-09-29
...no idea.
Please post your
/var/log/Xorg.0.log file
...it should give a hint.

---

### Post by AJ4PH on 2011-09-29
Well, I went back into the boot editor and removed the nomodeset and it fired right up. Guess Ill see where it goes lol. Thanks again

---

