---
title: "USB modem on Ubuntu"
date: 2009-03-26
forum: General Help
---

### Post by GrayFoxNZ on 2009-03-26
Hi guys,

I dual booted ubuntu with xp a little over 6 months ago.  I really want to use ubuntu alot more but havent mostly due to no internet.

Currently my only access to the internet is through a mobile wireless usb modem.  (telstra prepaid next g modem for those interested)  If you need exact details of modem I will post them when I get home from work.

I am wanting to use this connection on ubuntu, but of course my ISP tells me it can only work on mac osx or windows.  We all know this is not true, not with linux. Could someone please tell me how to configure and use this modem in ubuntu so I can browse and access the net and join the linux community full time.

thankyou in adavance.

---

### Post by Rohan Kapoor on 2009-03-26
> **GrayFoxNZ said:**
> Hi guys,

I dual booted ubuntu with xp a little over 6 months ago.  I really want to use ubuntu alot more but havent mostly due to no internet.

Currently my only access to the internet is through a mobile wireless usb modem.  (telstra prepaid next g modem for those interested)  If you need exact details of modem I will post them when I get home from work.

I am wanting to use this connection on ubuntu, but of course my ISP tells me it can only work on mac osx or windows.  We all know this is not true, not with linux. Could someone please tell me how to configure and use this modem in ubuntu so I can browse and access the net and join the linux community full time.

thankyou in adavance.
It is very simple to configure. With it hooked up right click on the network manager in ubuntu and select 'edit connections' From there select mobile broadband and add. Then fill in your settings and you should be set!

---

### Post by GrayFoxNZ on 2009-03-26
Hmmmmm last I checked it didnt have that option.  Had wired and PPP or p2p connection.

Ill have to have a look again to be sure.

My version of ubuntu is not up to date as of 6 months agao, if that would make a difference.

---

### Post by Rohan Kapoor on 2009-03-26
Yeah, this is the new network manager for 8.10 that has the features. You could try updating to 8.10 or try to find ```
NetworkManager Applet 0.7.0
``` for ubuntu 8.04 which would give you those options.

---

### Post by GrayFoxNZ on 2009-03-26
Ok I downloaded network manager applet 0.7.0 rc2.  Not sure how to install etc.

Is their a way to download an update for ubuntu which will update my ubuntu to the latest version through windows then update on ubuntu?

Or do I have to downloa the full 8.10 ubuntu and then install from cd again

---

### Post by Rohan Kapoor on 2009-03-26
Well you could install the network manager. It should end in a .deb which you can double click on to install, then click install, reboot and it should be there. If you need to upgrade I would recommend installing 8.10 by downloading the whole disk.

---

### Post by GrayFoxNZ on 2009-03-26
Ok I downloaded .tar.bz2 file hope thats the one with install in it.

Try this tonight and let know what happens, thanks for your help.

---

### Post by GrayFoxNZ on 2009-03-27
I get a configure:2970: error: C compiler cannot create executables 
See `config.log' for more details.

error im stuck what does this usually mean?

---

### Post by GrayFoxNZ on 2009-03-28
Ok I downloaded 8.10.  Then mounted in ubuntu so I can upgrade my ubuntu, but nothing happens, how to I run the mounted iso?

I used

sudo mount -o loop ~/Desktop/ubuntu-8.10-alternate-i386.iso /media/cdrom0

which mounted it but nothing happend after that, I then tried

gksu "sh /cdrom/cdromupgrade" after alt f2 and it came up for me to give my admin password and then still nothing after that, please help?

---

### Post by Chemical Imbalance on 2009-03-28
burn it to a cd or use the usb creation tool to put the image onto a thumbdrive and boot it.

---

### Post by Rohan Kapoor on 2009-03-28
> **GrayFoxNZ said:**
> I get a configure:2970: error: C compiler cannot create executables 
See `config.log' for more details.

error im stuck what does this usually mean?
You don't have the compiler to compile the source code. Just use teh 8.10 cd and boot with it.

---

### Post by geekygirl on 2009-04-17
I was in the same situation about getting my Telstra Pre Paid Next G dongle to work until reading through the archives of the ubuntu-au mailing list (thanks people it was a HUGE help!) and cam across this link about getting it running:

[http://www.matt-barrett.com/?p=5]("http://www.matt-barrett.com/?p=5")

As you said you also run XP it should be nice and easy for you to get it running  :D

---

