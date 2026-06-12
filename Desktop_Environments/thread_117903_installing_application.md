---
title: "installing application"
date: 2006-01-15
forum: Desktop Environments
---

### Post by ibarro on 2006-01-15
Hi, Im new to linux-ubuntu, been using it for 5 days now. I ve downloaded mplayer source and binary, and reading from other post on how to install seems greek to me. I can't get it. So used to windows just point and click the program and will install by itself. However its a different thing in linux. Can anyone help me install mplayer in simple terms? im using ubuntu 5.10 and downloaded the files on my desktop.:(

---

### Post by probe45 on 2006-01-15
"sudo apt-get install mplayer" should do the trick just make sure you have set universe in your sources.list (/etc/apt/sources.list)

---

### Post by zoiks on 2006-01-15
It's likely easiest to install mplayer from the repositories.  IIRC, you need to find the line in /etc/apt/sources.list that looks like this

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

and add the word "multiverse" to the end of the line.  Once you've done that, run Synaptic, click on "reload", and search for mplayer.  Don't forget to instyall the mplayer fonts.  Then you should be good.

---

### Post by aysiu on 2006-01-15
[QUOTE=probe45]"sudo apt-get install mplayer" should do the trick just make sure you have set universe in your sources.list (/etc/apt/sources.list)[/QUOTE] It's Multiverse you need.

To enable extra repositories, follow the directions in the first link of my sig. This is more or less a one-time command-line deal.

Then open up System > Administration > Synaptic Package Manager, and it's all point-and-click from there to install MPlayer.

---

### Post by ibarro on 2006-01-15
Thanks for the help guys. install mplayer with just a click of the button. will test if if it.
thanks again

---

### Post by probe45 on 2006-01-16
[QUOTE=aysiu]It's Multiverse you need.

To enable extra repositories, follow the directions in the first link of my sig. This is more or less a one-time command-line deal.

Then open up System > Administration > Synaptic Package Manager, and it's all point-and-click from there to install MPlayer.[/QUOTE]
:???:  My mistake

---

### Post by ibarro on 2006-01-20
After installing mplayer with the apt-get commands, only thing that plays is the audio there is some video coming out but mostly in unviewable forms or blank screen.  Did i forger to install some components? Im using and nvidia geforce 64mb or is it a video card problems?:confused:

---

### Post by Burning Bronx on 2006-01-20
Have you installed the video codecs? What format are you trying to play?

---

### Post by albertoramirez on 2006-01-20
Hello:

Installing packages from synaptic is very easy, just pick them and go.  But when a program is downloaded in a tar file or other similar, it is like reading chinese for me, I don't understand nothing at all.  And sometimes, in the readme files comes instructions, but they don´t work.

Can anyone post a ABC about installing programs from such files, the do's and don't's pleaaase.

Thanks

---

### Post by ibarro on 2006-01-21
Bronx
divx, vcd, dvd and windows streaming are the video format im trying to play. only get the audio.  I do not know if i have all the video codecs ijust use the apt get, not so sure if i installed all codecs. How could i check the codecs if they are install?:confused:

---

