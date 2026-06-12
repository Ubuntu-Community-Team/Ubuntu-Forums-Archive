---
title: "white blank screen on startup"
date: 2007-09-08
forum: Desktop Environments
---

### Post by gogogadget on 2007-09-08
I am (or was) running ubuntu 7.07 Feisty Fawn
I am using my old 6.10 Efty for this post

I am getting a similar problem. When I start up I get a white screen
What is most perplexing is that I can still restart. I have marked on my screen where the logout button is and the restart icon and although I cant see anything I can still reboot by going through the motions. So it appears that there is a full working system underneath a screen full of white.
I tried sudo dpkg-reconfigure -phigh xserver-xorg but no change in outcome.
I would like to use sudo apt-get uninstall <packagename> or similar.
So my question is how to restore the screen to normal. The only way for me to do this is to start in terminal mode. So I will need instructions to use Linux terminal.

My graphics card is an NVidia GeForce 6800

thanks :(

---

### Post by gogogadget on 2007-09-10
I HAVE SOLVED MY PROBLEM

Log in to recovery mode and when it is finished you will be at the command prompt and logged in as root.

change directory 

cd /etc/X11

create a backup of the file we are going to alter
cp xorg.conf xorg.conf.backup

use you favorite editor and edit xorg.conf
gedit xorg.conf

looking through the file you might see Load	"glx"
simply comment this line out be putting a hash (#) in 1st column of the line so it reads
#	Load	"glx"

reboot

and all should be ok

---

