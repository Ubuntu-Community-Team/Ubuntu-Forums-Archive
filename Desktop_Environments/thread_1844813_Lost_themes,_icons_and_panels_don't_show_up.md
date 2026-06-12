---
title: "Lost themes, icons and panels don't show up"
date: 2011-09-15
forum: Desktop Environments
---

### Post by vbnmu on 2011-09-15
Firstly, apologies if this has been asked before, I tried a google search and I searched this forum without much success.

Am new to Ubuntu: I have been playing around with 10.04 for a few weeks and decided to make it my main system. Today I decided to uninstall all the themes that I downloaded and start looking again as I wanted a darker theme. What I did was to go to the Ubuntu Software Centre, search for themes under installed apps and uninstalled **all** of them!

I wrongly thought that the only things that would go would be my additional themes. After that I lost my panels and I couldn't open the main menu which I had assigned to the 'windows' key. 'Alt+F2' wouldn't bring up anything. And I believe I tried 'Ctrl+Alt+t' as well, which didn't work.

I restarted the system, tried logging in but it was going in a loop, going back to the login screen every time. It went to terminal at some point and I tried 'startx' which didn't bring up anything.

I am now booting using my live cd.

Any help would be greatly appreciated as I had customised Ubuntu almost to perfection (for me, anyway). I already have a custom live cd but that does not reflect the latest changes I made.

Edit: Further research leads me to believe that I accidentally removed Gnome as well. If  that's the conclusion then should I install KDE or Gnome? Am not looking for any fancy stuff, just the lighter of the two.

---

### Post by wildmanne39 on 2011-09-15
Hi, run this in a terminal it may restore you desktop.
```
sudo apt-get install gdm
```
Then restart your computer.
Thank you

---

### Post by garvinrick4 on 2011-09-15
> Any help would be greatly appreciated as I had customised Ubuntu almost  to perfection (for me, anyway). I already have a custom live cd but that  does not reflect the latest changes I made.Live CD's will not hold changes they do not have what is called  persistence (live usb's can have up to 4 gig of persistence. (startup  disk creator in Ubuntu)

> Edit: Further research leads me to believe that I accidentally removed  Gnome as well. If  that's the conclusion then should I install KDE or  Gnome? Am not looking for any fancy stuff, just the lighter of the two.There are quite a few choices to try, if you have a few CD's around download some different types of
Ubuntu there is kubuntu there is lubuntu (nice light weight install, I enjoy using it.) there is xubuntu,
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
As I understand it Lubuntu will be part of Ubuntu as of 11.10 version
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

## Take a few of these that you find interesting and download .iso file and burn a CD or create a USB flash drive and take for a spin. I think you will find it enjoyable.
Enjoy your Ubuntu and welcome to these Forums, hope to see you around vbnmu.

---

### Post by vbnmu on 2011-09-15
> **wildmanne39 said:**
> Hi, run this in a terminal it may restore you desktop.
```
sudo apt-get install gdm
```
Then restart your computer.
Thank you

Hi, I tried ```
sudo apt-get install ubuntu-desktop
``` which seemed to have fixed it. Should I also follow the above steps for a proper fix?

---

### Post by vbnmu on 2011-09-15
> **garvinrick4 said:**
> Live CD's will not hold changes they do not have what is called  persistence (live usb's can have up to 4 gig of persistence. (startup  disk creator in Ubuntu)


There are quite a few choices to try, if you have a few CD's around download some different types of
Ubuntu there is kubuntu there is lubuntu (nice light weight install, I enjoy using it.) there is xubuntu,
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)
As I understand it Lubuntu will be part of Ubuntu as of 11.10 version
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

## Take a few of these that you find interesting and download .iso file and burn a CD or create a USB flash drive and take for a spin. I think you will find it enjoyable.

Please explain what u mean by usb/persistence etc..or point me to a guide if possible. It will be useful to me on my Elonex webbook which took me a lot of time to fix - problems with the VIA chipset.

I tried them all at some point, mainly due to my Webbook where I wanted to try the lightest build, Lubuntu I believe. The fact that there was a clear guide on how to setup Ubuntu meant I went for that.

I also tried Fedora, Mint, Puppy and Debian. Among the more 'well-known' distros Kubuntu was the only one I didnt try. The rather different looks of some of them, made me go for Ubuntu. It would have been too much of a step away from Windows otherwise - I needed to keep a balance. But probably more importantly, I found a lot more support around Ubuntu.

---

### Post by vbnmu on 2011-09-15
I have to say, the Ubuntu community has been amazing! I found an answer to all my questions so far through a simple Google search.

---

### Post by wildmanne39 on 2011-09-15
Hi, the command I gave you should be enough the other one you suggested I believe is only needed for ubuntu 11.04.

If everything is working I would not do any more to try to fix it.

If I helped you would you click on the link in my signature and support me for ubuntu membership? would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by garvinrick4 on 2011-09-15
> Please explain what u mean by usb/persistence etc..or point me to a guide if possible
You like to google search so if you google "casper -rw" File system and or Persistence you will get lots of info. Glad you got your machine back in order.

---

### Post by Krytarik on 2011-09-15
> **vbnmu said:**
> Please explain what u mean by usb/persistence etc..or point me to a guide if possible.
One guide is here:

[http://www.tuxgarage.com/2011/06/create-persistent-bootable-usb-drive.html](http://www.tuxgarage.com/2011/06/create-persistent-bootable-usb-drive.html)

And, you were perfectly right in reinstalling "ubuntu-desktop", trying to install "gdm" wouldn't have fixed it at all, not at least because it most probably wasn't removed in the first place.

You may want to check the APT log for more theme packages that have been removed, and weren't intended to: "/var/log/apt/history.log".

Greetings.

---

### Post by vbnmu on 2011-09-16
wildmanne39 Thanks buddy. Already posted my support.

garvinrick4 & Krytarik Thanks to both of you. Ubuntu started out as a sort of project, I was getting utterly bored of computers/windows. Am now really liking Ubuntu/Linux and how flexible it is. I would ditch Windows entirely but for certain things that I have yet to find a solution for in Ubuntu, Blackberry shrink os, Wii backup software, Football Manager :)...

Am loving it though!

---

### Post by wildmanne39 on 2011-09-16
Hi, your welcome! enjoy ubuntu.

Also you can have a look at this link it will allow you to run windows at the same time as ubuntu so no more shutting down and restarting.
[http://www.virtualbox.org/](http://www.virtualbox.org/)
Thank you

---

### Post by vbnmu on 2011-09-16
Am I right in saying that this method is resource heavy? I imagine running virtualbox, windows and football manager would be overkill?  unless my understanding of virtualbox is wrong!
I have a Compaq nx7300 Intel T5600 and 1gb ram.

---

### Post by wildmanne39 on 2011-09-16
Hi, no you are right it takes more resources, but I did not know if you had the resources or not so I thought I would mention it.
Thank you

---

