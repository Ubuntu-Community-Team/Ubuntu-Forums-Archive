---
title: "HW graphics acceleration working with Unity, but not Gnome-Shell"
date: 2014-10-24
forum: Desktop Environments
---

### Post by sgarman on 2014-10-24
Hello,

I did a fresh install of 14.10 yesterday on my desktop system which has an Intel Haswell i7-4790K processor with HD4600 graphics. I use gnome-shell, and previously when I ran it with Ubuntu 14.04 everything ran smoothly.

However, now with 14.10 I get very slow graphics behavior with gnome-shell - playing videos is choppy, and simple animations such as when you move a terminal window to the right of left of the screen and it maximizes the hight of the window is choppy and takes a full second to complete. I feel a slight overall lagginess even typing into terminal windows. 

I switched my DE to Unity and now everything runs smoothly. Back to gnome-shell, and it's choppy again. I'm at a loss to explain this, as I thought my Xorg configuration handles graphics acceleration and would work regardless of which DE I'm using. Can anyone give me suggestions on how to troubleshoot this further?

Also, I have a Haswell laptop with HD4000 graphics that I installed the release candidate of 14.10 on last week, and it runs quite smoothly with gnome-shell. So I have a working and non-working system I can make comparisons with if needed. 

The intel graphics installer you can get from 01.org apparently has not yet been updated to work with 14.10, and reports that the distro is not compatible. But I figure 14.10 should have the very latest Intel drivers anyway. 

Any help would be appreciated. Thanks!

Scott

---

### Post by sgarman on 2014-10-24
I just wanted to add that I have downloaded the UbuntuGNOME 14.10 release ISO and booted the live environment on my desktop system, and the graphics acceleration works. However, if I then install it and log in, the graphics acceleration is broken again! This is with a completely clean install and brand new user account. I'm totally baffled.

Someone else on the #gnome Freenode IRC channel with Intel graphics has encountered the same problem - graphics acceleration is not working with gnome-shell on an Ubuntu 14.10 install.

I've compared my Xorg log files from the working and non-working setups, and there are no significant differences. I still could use some advice on other things to examine more closely.

---

### Post by sgarman on 2014-10-25
I spent a long day trying to figure this out, with no luck. I found a workaround and am going to use it - upgrade to Gnome Shell 3.14:

	sudo apt-add-repository ppa:gnome3-team/gnome3
	sudo apt-add-repository ppa:gnome3-team/gnome3-staging
	sudo apt-add-repository ppa:ricotz/testing
	sudo apt-get update
	sudo apt-get dist-upgrade

Graphics acceleration is now working, and I can get other things done.

---

### Post by massimilianoadamo on 2014-11-07
thanks for sharing your findings. 
Indeed it worked also for me.

---

