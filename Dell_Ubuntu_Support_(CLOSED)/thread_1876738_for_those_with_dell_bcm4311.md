---
title: "for those with dell bcm4311"
date: 2011-11-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by linuxaddix on 2011-11-06
if you are like me and catch no wifi whatsoever after installation of linux distros and have a dell bcm4311 wireless card here is the solution.there are 2 ways of doing this one by terminal and one by synaptic.ill show you guys the synaptic way:
make sure you have an ethernet or tethering internet connection
(in previous versions before 11.10 synaptic is installed already)
to get synaptic in 11.10 go to ubuntu software and type in synaptic and install it.
1.in terminal
sudo apt-update
its to make sure the packages in the synaptic are up to date
2.open up synaptic and in search type in:
bcm
3.scroll down until you see:
firmware-b43-installer
and mark it for installation
window will pop-up about installing
fw-cutter
click ok
4.apply installations by clicking apply tab.
5.after installation is complete unplug your internet connection and click on the wifi icon and it should now show wireless connections.
note:additional drivers for sta wont work
        this is for the broadcom b4311 wireless card installation
if you have any disputes of this tut please start your own thread
as ive said,this is for broadcom b4311 wireless cards

---

