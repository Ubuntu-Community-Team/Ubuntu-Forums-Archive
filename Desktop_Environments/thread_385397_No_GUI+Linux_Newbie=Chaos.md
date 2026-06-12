---
title: "No GUI+Linux Newbie=Chaos"
date: 2007-03-15
forum: Desktop Environments
---

### Post by shadow049 on 2007-03-15
I installed Ubuntu 5_10 (whatever its called) on my ailing laptop (that has no floppy/cd drive and will not boot from USB)
I finally got it to work, booted it up, and lo and behold....
There is no Graphic User Interface
Oh damn.
Am I screwed? Or is there something I can do to install something that actually has a normal looking desktop?

---

### Post by FruitieX on 2007-03-15
Hi!
Log in with your username and enter the pasword you specified in the installation. After this you will be at the command line. Type: "sudo aptitude install xserver-xorg" The Linux "GUI" is the X server, once you have it running you have to install a desktop envirnoment. You can chose between Gnome, KDE, Xfce4, fluxbox and some others. The command you should have ran is installing the xserver, this might take a while. And, what actually happens when you boot? A black screen or a black screen with white text? And what hardware are you using? Mostly I'm going to need to know your graphics card here... After the package has installed, try running "sudo aptitude install ubuntu-desktop" (Or if you want kubuntu, well you might figure out what to type :). Also you can replace it with xubuntu but i belive you want Ubuntu :)) then run "sudo aptitude install gnome gdm" (I don't remember if gnome depends on gdm, and this is just in case so everything we need will be installed). After all this try tunning "gdm" and see what happens. If it gives you a graphical login screen then we are all set so far, jump to GDM WORKED. If it doesn't work and you don't get to the command line, press CTRL+ALT+Backspace to kill the X server. After this you can try to run "sudo dpkg-reconfigure xserver-xorg" and set your driver to vesa instead of what ever it was. Try to set the rest of the settings as good as you can, otherwise use enter to use defaults (tab to switch to an OK button). Then try running "startx" and see what happens. If you can move the mouse around an empty "GUI" then jump to GDM WORKED. If not, continue. Well, if it didn't work I suppose it gave you some error messages. Type them here into the forum so we can help you...

GDM WORKED section... Proceed by entering your username & the password into the fields and press enter. It should now enter Gnome. You might want to download the graphics card drivers first of all... After you have said what kind of hardware you have, i might be able to help you further.

Good luck!
FruitieX.

---

