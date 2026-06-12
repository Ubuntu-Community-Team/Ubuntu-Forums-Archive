---
title: "Installed Ubuntu Desktop, how can I turn it into Ubuntu Server (remove GUI)?"
date: 2014-10-10
forum: Desktop Environments
---

### Post by James_Spinella on 2014-10-10
Hey all,

I have Ubuntu 12.04 Desktop on a PS3, and Swap is being utilized heavily since the PS3 has only 256MB of RAM. It takes about 10 minutes to load the desktop once I type in my password, and then another five minutes or so to load Terminal.

It's obvious the PS3 can't handle Ubuntu's GUI, but the single-user/terminal mode ought to work fine.

Without reinstalling Ubuntu with a Server CD, how can I convert Ubuntu Desktop to Ubuntu Server? I tried a command I found when Googling around, but that broke the Ubuntu install to the point where it would no longer boot.

Here's the catch: I don't have GRUB (Petitboot on a PS3!), it just boots straight to Ubuntu.

---

### Post by ibjsb4 on 2014-10-10
> I tried a command I found when Googling around, but that broke the Ubuntu install to the point where it would no longer boot.
How do you plan on doing anything if it will not boot?
> Without reinstalling Ubuntu with a Server CD, how can I convert Ubuntu Desktop to Ubuntu Server?
You would have to remove the ubuntu-desktop package.  Which means removing not all, but just about everything in this list.
[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)
So you would end up with a functional command-line system like this.
[http://packages.ubuntu.com/precise/ubuntu-minimal](http://packages.ubuntu.com/precise/ubuntu-minimal)
Or a comfortable command-line Unix-like environment.
[http://packages.ubuntu.com/precise/ubuntu-standard](http://packages.ubuntu.com/precise/ubuntu-standard)
But again, if it won't boot ..

---

### Post by James_Spinella on 2014-10-11
To clarify, I've since reinstalled Ubuntu 12.04 Desktop... I mentioned that so you'll know that I've tried, and haven't just posted to waste someone's time. Hopefully you don't feel that way.

I don't recall exactly what command I used, I actually sudo apt-get installed something, and then that asked me if I wanted to remove ubuntu-desktop, I said y (yes), and it did its thing. And then it would no longer boot.

I'm definitely willing to try removing everything one-by-one when I get in tomorrow.... Is that what you recommend? Thank you for your assistance by the way.

---

### Post by ibjsb4 on 2014-10-11
> I'm definitely willing to try removing everything one-by-one when I get in tomorrow.... Is that what you recommend?
No, not at all.  I posted a answer to your question.  I would not recommend this to anyone as it will be time consuming and a big pain in the ..

Your better off doing a reinstall of what you want.  Are you sure that a 'console' (terminal only) install is the solution?  I know what a ps3 is, but have never owned one.  What will you use a server install for?

---

### Post by James_Spinella on 2014-10-11
A PS3 has 256MB of RAM, it seems to me like my best bet is running a Server install, which wouldn't have the RAM-intensive Desktop/GUI. Granted 256MB is still not ideal, it's better with Server.

I'm out of blank CDs, so I can't go and burn a copy of 12.04 Server, and USB installers don't work with the PS3. Otherwise, I agree, just reinstalling with what I want is the best option.


I found this: [http://askubuntu.com/questions/511463/can-i-convert-ubuntu-desktop-14-04-to-server](http://askubuntu.com/questions/511463/can-i-convert-ubuntu-desktop-14-04-to-server) which I'm going to try now... I know it's for 14.04, but worth a shot.

---

### Post by James_Spinella on 2014-10-12
That broke it, too... Off to the store for more blank CDs, I'm going to give a Server PPC iso a go.

Thanks again for your help sir!

---

### Post by stretch4 on 2014-10-13
Maybe you should try Lubuntu? I haven't used it myself, but I hear the requirements are a lot lower.

---

### Post by Mike_Walsh on 2014-10-13
Stretch4 DOES have a valid point. 

Lubuntu is the lightest of the 'Buntu 'flavours'. It uses Openbox as its Desktop Manager, and is only 2D. Unity requires hardware acceleration to function correctly, as it is 3D.

Your entire PS3 RAM is about the same as the 'system-reserved' chunk that MY graphics adapter uses out of my 3 GB of RAM.....and 3 GB doesn't appear to be very much by today's standards.

I have Lubuntu installed on an elderly Dell Inspiron laptop. It only had 128 MB of RAM when it was first purchased, but I increased that to 1 GB, the maximum the motherboard will accept. Lubuntu works well on this setup.

The key to cutting down 'swap' use and maximising uage of your RAM is controlled by what's known as the 'swappiness' setting. Most of the 'Buntu distros ship with this set to 60. I usually decrease this to about 10, which works well with my desktop; on the Dell, I've taken this down to 5.

Try installing Lubuntu (I would imagine you would want the 32-bit version); and then have a look at [this page]("https://sites.google.com/site/easylinuxtipsproject/lubuntu"). The link for the page that describes how to decrease the swap usage is almost the first thing mentioned, partway down the left-hand column.

Hope this helps.

Regards,

Mike.

EDIT: I understand it's impossible to increase the amount of RAM on a PS3, as you would need to solder it to the motherboard..??

---

