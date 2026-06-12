---
title: "When starting my computer, it doesn't start gnome, just goes to terminal"
date: 2008-04-23
forum: Desktop Environments
---

### Post by thebrotherofasis on 2008-04-23
Hello,

Last night I turned off my ubuntu 7.10 machine, and went to have a comfortable night's sleep. This morning, I woke up and turned it on to start a day of work... and wooops!!! After loading the initial stages, ubuntu just doesn't go to gnome... it goes to the terminal and asks me for my username and password. I provide them, and it just stays in the terminal!

I am utterly confused... everything was perfect yesterday, and today... I just can access the terminal. I have restarted my machine many times already, and I just get to the same point.

What could be wrong?

And most importantly: how can I get back to where I was before...? How can I just login to my gnome session and work as I have been doing on a normal basis?

This is surprising, and kind of annoying to say the truth.

I had to start in windows, and I am writing from here... It's been ages since I last used windows... everything I have is in ubuntu... so please, if anyone can shed some light on this issue, it would be very grateful

Thank you for your kind support.

---

### Post by Cannaregio on 2008-04-23
What happens if you type in your terminal
```
startx
```
does the GUI start or not?

And what happens if you, instead, press the three keys
```
CTRL+ALT+F7
```
do you get your GUI?

---

### Post by thebrotherofasis on 2008-04-23
1) I typed startx, and I get the following error:

> Giving up
xinit: connection refused (errno 111): unable to connect to X server
xinit: no such process (errno 3): server error

2) I held CTRL+ALT+F7 and nothing happens...

Is this serious? How can I get my GUI back to work?

Thanks in advance

---

### Post by markjensen on 2008-04-23
Sounds like something was changed in your X configuration during last boot session, so when you rebooted, it took effect, but is non-functional.  Have you set or removed any desktop effect options recently?

---

### Post by thebrotherofasis on 2008-04-23
Well... I hardly can think of something I changed: My screen resolution... However after I canged it, it was working perfectly. But I didn't change it yesterday, nor any time recently, probably a week ago at the soonest. 

No desktop effects I have touched, for I prefer a  better performance over apperiance. Now, is there a way in which I can reconfigure the X configuration?, or what should be done instead?

---

### Post by markjensen on 2008-04-23
Well, you can manually browse and check for a backup xorg.conf file in your /etc/X11/ directory.   It may have a .backup appended, or likely a tilde (~) if it was edited.

If a backup exists, and the problem was with your xorg.conf, then this will fix you right back up.

If you want to reconfigure yourself, **sudo dpkg-reconfigure xserver-xorg** should get the process started.

---

