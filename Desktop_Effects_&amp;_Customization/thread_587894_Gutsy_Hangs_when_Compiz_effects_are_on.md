---
title: "Gutsy Hangs when Compiz effects are on"
date: 2007-10-23
forum: Desktop Effects &amp; Customization
---

### Post by shijirou on 2007-10-23
Ever since the beta releases I've been trying Gutsy and I've been having problems when compiz effects (cube, window effects, etc) are on. My PC hangs randomly and I need to reset it often. I have the restricted drivers on and even tried the ones from the Nvidia Site.I thought with the official release of Gutsy it would be fixed. Could this be my video card? I have Gutsy installed on another PC that has an ATI video card and I've no problems with that. 

A little input and help would be appreciated. Thank you! *bows*

Here are my specs btw:
AMD Athlon X2 3600+
1.5 GB DDR2 PC667 RAM.
Nvidia Geforce 7300 GS PCI-E 256mb vid card

---

### Post by harro0209 on 2007-10-23
I had similar problems with the 7300GS. As soon as the desktop effects were enabled I had random freezes.
The only way I found to avoid this problem was to install an older version of the nvidia driver. With 100.14.09 I did not have any freezes for three days.

Hope this helps

---

### Post by shijirou on 2007-10-25
Oh cool will try this over the weekend. Thanks!

---

### Post by FuturePilot on 2007-10-25
Apparently there's been a regression in the Nvidia driver for people with a GeForce 7 series card and a dual core processor that causes freezing. The one workaround would be to install the 100.14.09 driver.

---

### Post by akshayas1986 on 2007-11-01
Hi 
@ FuturePilot
But I want to know if the 100.14.09 driver solves this problem as this driver just adds support to GeForce 8 series cards. Does not say it solves 7 series cards issues.

---

### Post by akshayas1986 on 2007-11-02
Hey guys

Initially I tried to install 100.14.09 driver from Nvidia site but somehow it did not configure xorg.conf properly and hence X windows got into issues. I had a backup of the xorg.conf fine which I used and got my GDM working again.

After that I used Envy from the below link
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html).

Install it and run
> envy -g and it works brilliantly.

No more hanging of my machine. Envy installed the latest driver-100.14.23.

Hope this helps

---

### Post by FuturePilot on 2007-11-02
> **akshayas1986 said:**
> Hi 
@ FuturePilot
But I want to know if the 100.14.09 driver solves this problem as this driver just adds support to GeForce 8 series cards. Does not say it solves 7 series cards issues.

Nvidia was not aware of the problem at the time. The 100.14.11 caused a regression and they didn't find out about it right away. So the problem was introduced with 100.14.11 and 100.14.19 still has the problem. Nvidia is now aware of the problem. Hopefully they have fixed this in 100.14.23

---

### Post by beesthorpe on 2007-11-02
>  After that I used Envy
Quote:
sudo apt-get install envy
And run
Quote:
envy -g
and it works brilliantly.

No more hanging of my machine. Envy installed the latest driver-100.14.23.

Hi Akshaya - I would love to know how you did this -apt-get says I've got the latest version of Envy but it's only got the 100.14.19 driver.  "Envy" is the word :)

---

### Post by FuturePilot on 2007-11-02
You need to remove the version you have installed then download the latest version from here
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
You want the Envy New version.

---

