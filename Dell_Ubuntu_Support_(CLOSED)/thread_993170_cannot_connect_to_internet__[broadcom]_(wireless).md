---
title: "cannot connect to internet  [broadcom] (wireless)"
date: 2008-11-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sean9461 on 2008-11-25
Hi, firstly this is my first post and i would like to say thanks to the ubutu team for a great operating system.

Now, i have a dell inspiron 1501 laptop. i cannot access the internet. i do not have a wired connection. Although i can download anything on this computer i am on now running windows and put them on a usb stick.

when i type  lspci | grep Broadcom\ Corporation into a terminal i get this:
Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

Also, i am new to ubuntu and command lines so can it please be explained in detail. 

Thanks.

---

### Post by ytsejam1138 on 2008-11-25
Have you checked for Proprietary Hardware Drivers?  You will need a wired connection if possible for this to work.  
Click System>Administration>Hardware Drivers  This should look for and download the appropriate drivers, you will then need to click the Activate button.

---

### Post by notgeekenough on 2008-11-25
Had the same problem: Dell Inspiron 1501 with Broadcom wireless. Broadcom devices are not supported by linux so basically, you have two choices, you can either install ndiswrapper which is at [http://sourceforge.net/projects/ndiswrapper](http://sourceforge.net/projects/ndiswrapper) or you can install the b43 driver. It depends what you want to do. If you just want to browse the internet, go for the ndiswrapper, its pretty easy to install, just search for it on google. If however, you want to put your card in monitor mode for example to use kismet or aircrack-ng, you'll need to install the b43. I have instructions on [http://corpuscallosum.homelinux.net/notgeekenough/hippocampus_broadcom.php](http://corpuscallosum.homelinux.net/notgeekenough/hippocampus_broadcom.php)
It should be easy enough to follow along even for one new to ubuntu/command line. If you have any problems or my site goes down (which it does often) email me (notgeeknough@gmail.com).

Hope this helps.

---

### Post by sean9461 on 2008-11-26
Hi thanks for the help notgeekenough but, how do i install it, i have no internet connection on the laptop. do i jus download the file put it on a usb stick and open it within ubuntu and it will install?

and after that will my internet just work?

Thanks. 
Also i am trying this now, i will edit this post if it works.

EDIT: im sorry but i love the style and theme of ubuntu but it is just far to complicated for me, the command lines and having to everything by terminal is hard enough and then i have the added problem of my internet not working.
i am probably going to go back to windows

---

### Post by Tea4all on 2008-11-26
You really don't have to do everything by terminal. We only post the commands because it is easier, in my opinion, to copy and paste than to follow things by gui. The firmware for the card can't be included because of licensing issues with Broadcom. To install the driver, you must get a wired connection to the laptop. Then you can go to System > Administration > Hardware Drivers. Then highlight the Broadcom driver and press "Activate". Ubuntu will then download and install the driver. Then you can restart the computer and use wireless. You can also open a terminal and paste ```
sudo aptitude install b43-fwcutter
```These are two different ways, but the terminal way takes up less time to read and do. If you need help, the website [https://help.ubuntu.com/](https://help.ubuntu.com/) is a great place to start. You can use Ubuntu with the terminal only, and many people choose to. You can also use all GUI, or a mix of the two. The terminal can do many more things to your computer than a GUI ever can. That is why we post terminal commands. Just ask for GUI instructions if you prefer them! I also have some pictures to help you out.

---

### Post by Tea4all on 2008-11-26
:popcorn:

---

### Post by scottmac112 on 2008-11-26
Are you using Intrepid or Hardy or Gutsy? What version are you on?

---

### Post by notgeekenough on 2008-11-27
The only issue is the downloads, but I have them on my site. Given that you have the same pc and ubuntu 8.04 you should be able to just download everything from my site that you need except for build-essential. This package should be on your CD, if its not, I think you could download it off of ubuntu's site. Get everything on your Windows and transfer it to your usb, they should be pretty small. You are also going to need build-essential eventually, its a good package and if you don't have it, you'll get errors trying to install many programs.

---

### Post by notgeekenough on 2008-11-28
Hey, don't go back to windows. As I state on my site, I have been using windows since 97 starting with 98 all the way up to XP and a bad experience with vista. Of course it all depends what you want to do. If you just want to play games or search the net or write papers use windows. I enjoy the ease of use of windows: stick a cd in the drive and it works. Linux sucks initially. I spent a month with no internet and nothing working on linux that should have been but I stuck with it, and linux starts to grow on you. You get used to the terminal and eventually, you start using it more and more. The best thing about Linux is you get a better grasp of computing, networking, whatever it is your tinkering around with but most importantly there is a sense of satisfaction when you finally get something right. I understand what your going thru, especially without a wired connection you're at a real disadvantage.

---

