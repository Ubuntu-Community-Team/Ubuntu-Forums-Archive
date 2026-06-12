---
title: "Ricoh webcam on a hp dv6000 problem"
date: 2009-04-09
forum: General Help
---

### Post by pieta9999 on 2009-04-09
Hi guys, 

I am kind of new in linux and i can't have my integrated webcam recognized by my laptop. I will  

The webcam is per lsusb: Bus 002 Device 003: ID 05ca:1810 Ricoh Co., Ltd 
My laptop is an hp pavillion dv6000 (more specifically it's a dv6436nr).

I am using Ubuntu 8.10, Intrepid Ibex.

i ve tried several things i have found online without any success...
i cannot detect/use my webcam in skype, ekiga etc...
i would deeply appreciate any help.

thanks!!!!!!

---

### Post by soltanis on 2009-04-09
You, sir, possibly suffer from the same problem that I do. My computer also has a Ricoh integrated webcam (id is 05ca:1835) in my Vaio laptop.

There is only one driver that can work this webcam, if yours is on the list of cursed drivers (and currently its been broken for me, giving me weird images). It's called r5u870.

I just read on the list, yes, it seems like your webcam is one of those which only works with this driver.

Googling can find you some download links, but the driver itself isn't maintained anymore (its quite possible there wont be a compatible one for you). Recently a new project called r5u87x was started, which enables the uvcvideo kernel module to work using a userland utility. I don't think packages are available for that in .deb format; if you want to use it, you'll have to compile it yourself.

EDIT.
[http://lists.mediati.org/archives/r5u870-list/2008-September/000053.html](http://lists.mediati.org/archives/r5u870-list/2008-September/000053.html)

Read that. If you are willing to do a bit of simple compiling, install build-essential, gcc and automake if you haven't already, then download the repository (you don't need mercurial, there's a button on the upper right of the web page that links to that lets you download the repository as a .zip/.bz2 file, the .gz option is broken), extract it somewhere handy, cd to the directory and run make. Then simply run sudo ./loader, and with luck it will load the firmware into your camera.

That'll make it appear in basically all your applications (there are a few bugs; some applications don't like the uvcvideo module, so sometimes you'll have to unload it to get them to work; and with my camera, when I open up the image, I get this strange blur that seems to be caused by not syncing up the image correctly, that seems to be solved (sometimes) when I resize the window I'm looking at).

---

### Post by pieta9999 on 2009-04-09
thanks for your prompt answer soltanis, i really appreciate it.

i kind of found an answer just 5 minutes ago, even though i have been looking for it for the past weeks.

It is the following and it did make my webcam work!!!!!!!!:

Found an old thread with a suggestion I tried and got the webcam working. For those still trying to get theirs working, you may want to try this:

Firstly:
* Verify that you have svn installed.
* Remove any instance of r5u870 or the ry5u870 modules you may already have from previous attempts.

Code: 

svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) ~/r5u870
cd ~/r5u870
sudo make
sudo make install
sudo modprobe r5u870

Then try xawtv to see if the cam works (sudo apt-get install xawtv)

test is using code: xawtv /dev/video0

[SIZE="6"]**the problem now is that its image is very dark and i am unable to correcty it. any ideas???? any help would be deeply appreciated![/SIZE]**

---

### Post by burro on 2009-05-26
Any solution to this?

---

### Post by pieta9999 on 2009-05-27
Unfortunately, my webcam is still dark intermittently. Sometimes it also keeps producing green lines in the middle of the screen. It also freezes or the video stops working with skype every 5 minutes or so. Then i have to choose "stop video" and "start my video" again to restart my video. All these issues are somewhat annoying, but at least i have a functional webcam...

---

