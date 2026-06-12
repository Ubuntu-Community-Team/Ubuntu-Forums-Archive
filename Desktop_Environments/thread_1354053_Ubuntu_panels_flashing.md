---
title: "Ubuntu panels flashing"
date: 2009-12-13
forum: Desktop Environments
---

### Post by BoJaN111 on 2009-12-13
Ok, I was looking for a way to restart Compiz, because when I boot my computer or restart gdm my second monitor(running a seperate X Screen) is just black, my cursor is able to move over to it though. I had a command that was something like ```
DISPLAY=:0.0 compiz --only-current-display
``` and this worked good, it enabled compiz on my primary display and my secondary display was now showing properly but had no desktop effects. 

So I was then looking for a way to restart it entirely, ```
compiz --replace
``` seemed to restart it but I had no desktop effects on either X Screen.

Then I came across this
```
export DISPLAY=:0.0sudo your_user_id fusion-icon & 
```
when I ran it, it screwed everything up.. now when my second X Screen is enabled my panels flicker on/off over and over.. and over as if compiz is restarting every second until I disable my second X Screen and restart gdm.

I've tried deleting my xorg.conf file and it did not help, once I enable my second X Screen it just does the same thing as before. I'm thinking the export at the front of the command is exporting it somewhere it's running the command every second.

I'm using the nvidia settings application to setup my displays.

---

### Post by BoJaN111 on 2009-12-15
bump

---

### Post by tonywhelan on 2009-12-25
Can't help with a solution, but I have the same problem.
I just installed  AMD64 bit version of Karmic Koala.
Set up nvidia driver (with some difficulty) to run my two screens and it worked. 
But then I deleted an icon on the top panel and now the panels just flash on and off continually.

Its going to be an interesting day ...

---

### Post by Spainface on 2009-12-28
Same  here... I had audio icons on the panel and when I tried to remove one they began flashing.  Rebooting doesn't help.

---

### Post by Spirrwell on 2010-01-05
The same thing happened to me when I installed this Kino program so I could use firewire. A friend of mine uses Ubuntu and he came up with a solution, but I think he screwed up something that wrote for me to put in so I'll tell you and see if you can make something of it. He told me to go to the recovery console and type this in:```
init 3
sudo -i
cd ~
ls -a l grep ".login"
cat >> .login
init 3
Ctrl + Z or Ctrl + D
```

Hope this inspires an idea or something because I don't know what the heck it means.

---

