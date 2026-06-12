---
title: "PLS HELP: I just got converted to Ubuntu-ism. I got problem with screen resolution."
date: 2007-07-28
forum: Desktop Effects &amp; Customization
---

### Post by october3rd on 2007-07-28
I use Ubuntu 7.04.
On the first 2 days everything is working okay and neat in 1028 x 768 px resolution.
Today, on startup the screen appeared in 640 x 480.
I went to the System > Preferences > Desktop Resolution, clicked on the drop down menu. 
But there's no other option there but 640 x 480.
What do you think might go wrong?
I use dual OS. WinXP (genuine) and Ubuntu 7.04 (from Canonical).
I don't use any third party VGA card, just one on board with the Intel chipset.

My computer specs:
IBM Thinkcenter E54.
Intel Pentium 4 3.4GHz.
Intel Chipset (Intel Graphic Accelerator -onboard)
512MB RAM. (1GB RAM soon).

Please respond a.s.a.p..
Thanks in advance..

---

### Post by roaldz on 2007-07-28
Have you updated your software on ubuntu? Like Xorg of something?

---

### Post by tekkenlord on 2007-07-28
I suggest you install xserver-xorg-video-intel and then restart your X server.

---

### Post by eddierd on 2007-08-08
Hi, let me tell you how I solved this mystery. 

Open a Terminal (under accessories)
Type:
sudo apt-get install xserver-xorg-video-intel

There is a place were Ubuntu gets this files (Repository) and you need to register it, I got an error and I was able to get the file from Skype!!! This is how I added this:

1. add this line to the end of your /etc/apt/sources.list file:

sudo deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

2. Then run: 
sudo apt-get install xserver-xorg-video-intel

It fixed the problem, it was that easy . . .

---

