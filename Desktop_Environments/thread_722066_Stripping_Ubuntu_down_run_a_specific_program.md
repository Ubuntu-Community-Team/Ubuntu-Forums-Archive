---
title: "Stripping Ubuntu down run a specific program?"
date: 2008-03-12
forum: Desktop Environments
---

### Post by hseiken on 2008-03-12
Hi, I looked at some of the threads involving stripping down Ubuntu, but what I really want to do is run a set of programs without going to Gnome...is this possible?  

What I would like to do is initialize the sound and video cards, then activate ALSA, then right after execute jack, and then right after that, run ReNoise.  According to the devs, it doesn't require any specific GUI (like Gnome and what not) because it uses it's own code for that.  After ALL of this, I want to add a menu option to GRUB to go to this specifically focused Ubuntu.

Is this possible?  I'm still a linux noob, but even doing things like simply not loading processes that ReNoise simply won't use would be good as well...

If anyone can point me to literature on how to do this or at least where to start, I'd be appreciative.  

Thanks.

---

### Post by spupy on 2008-03-12
You can set up the X server so that it runs only one graphical app instead of Gnome. It is just a matter of writing a simple script that activates Alsa, jack, and whatever you want, and then start Renoise fullscreen without **any** other GUI program running.
Is that what you need?

---

### Post by cenwesi on 2008-03-13
Yep, i am also interested on this. Is there a howto out there that can explain this?

---

### Post by spupy on 2008-03-13
When i get back home, I will write you a simple howto.

---

### Post by spupy on 2008-03-13
Ok, here it goes.

I think it is possible to do this with GDM running, but i don't use GDM, so i will tell you how i do it.

If you press Ctrl+Alt+F1, you will go to the first virtual console. From there you can type
```
sudo kill X gdm
```
to kill the X server if it is running. You can start GDM again by typing gdm (or "sudo gdm"), or you can start Gnome directly by typing "startx". The command startx starts the X server and executes the script ".xinitrc" from your home folder (if it exists). See, Gnome is actually a program that runs in the X server just like Firefox or Synaptic.
If you don't have the xinitrc file create it:
```
touch .xinitrc
```
If it already exists better back it up:
```
cp .xinitrc .xinitrc.bak
```
Now open the xinitrc file with your favorite text editor. The files is actually a normal bash script. Put in it any commands you want - execute jack for example. (Note: ALSA, video cards, and other stuff gets initialized at startup of the PC, so no need to anything in here. I just said jack because i have no idea what it is.) Make sure to put "&" at the end of each command you put in.
See [here]("http://www.unix.org.ua/orelly/linux/run/ch11_01.htm") for examples of other things that are useful to have in the xinitrc.
After putting your commands in this file, the **last** line should be like that:
```
exec programname
```
For example "exec firefox".
Save the file, and go to the first virtual console as i explained at the start, and kill GDM and X (make sure to save all open things, so you don't loose data!).
Now type
```
startx
```
xinitrc gets executed, and at the end your programs will start up with no Gnome, KDE or whatever.
Possible troubles: 
- When your app starts, it will probably be the size it had last time running - it wont be full screen. To fix this, go to gnome, make your app fullscreen and stop it while it is still fullscreen. This is because some apps remember their dimensions.
- If after meddling with startx and stuff, if GDM doesn't start (try also "sudo gdm"), you can fix GDM with this command:
```
sudo dpkg-reconfigure gdm 
```

---

