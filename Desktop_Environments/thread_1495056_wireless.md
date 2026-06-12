---
title: "wireless?"
date: 2010-05-27
forum: Desktop Environments
---

### Post by sm4sh1t on 2010-05-27
Hello, im new to ubuntu jaunty 9.04 and i installed it to my toshiba l450-02n and i updated the updates. one thing is the wireless does not work :( if you can help me thank you.

---

### Post by sm4sh1t on 2010-05-27
when i go to updates there is no more to take, im not sure how to find what wireless card i even need to update. im on wired now and it is great :P thanks for reading and hope to get some help thanks.

just want to add the speed on my computer went from poor to lightning speed online, very nice.

---

### Post by SunnyRabbiera on 2010-05-27
Actually you should try to install lucid, the most recent version if possible.

---

### Post by sm4sh1t on 2010-05-27
> **SunnyRabbiera said:**
> Actually you should try to install lucid, the most recent version if possible.

thank you for the reply, can i install this lucid from synaptic manager? and is it just an install or would i need to set it up with commands some how? thanks.

ok i have installed lucid 6 now im unsure on what comes next.

---

### Post by sm4sh1t on 2010-05-27
I rebooted and see a sun java 6 start under apps internet, started it i think but no wireless at all. btw do i need to rebbot after installs like i did on windows? thanks.

---

### Post by st0kes on 2010-05-27
Sun Java 6 is nothing to do with wireless. 

You should have an icon for Network Manager in your notification area (top right, if you are using Gnome). Try left click and right click on there and see if you have any options to configure your network card, or even if it is detected. 

If it is not detected, tell us about your wireless network card and your computer setup and we can help you confgure it.

---

### Post by sm4sh1t on 2010-05-27
> **st0kes said:**
> Sun Java 6 is nothing to do with wireless. 

You should have an icon for Network Manager in your notification area (top right, if you are using Gnome). Try left click and right click on there and see if you have any options to configure your network card, or even if it is detected. 

If it is not detected, tell us about your wireless network card and your computer setup and we can help you confgure it.
 
thanks, my wireless cards not detecting at all. im not sure what to do. i dont even no what lucid does.

---

### Post by WinRiddance on 2010-05-27
> **sm4sh1t said:**
> thanks, my wireless cards not detecting at all. im not sure what to do. i dont even no what lucid does.
.
There are different versions of Ubuntu just as there are different versions of Windows such as Windows7, Windows Vista, and so on. Well, you mentioned that you installed Ubuntu 9.04 which is also called Jaunty or Jaunty Jackalope (if you want to use the whole Ubuntu 9.04 name). However, that version is now "old" since a new release of Ubuntu comes out every 6 months. Of course that doesn't mean that you "must" use the newest version. That's entirely up to you ....

The next newest version of Ubuntu was version 9.10 also known as Karmic or Karmic Koala. This too was replaced at the end of **April 2010** with the current **Ubuntu version 10.04 also known as Lucid** or Lucid Lynx.

Because of the _many many many_ different network devices out there, some versions of Ubuntu work better than others, especially where WiFi access is concerned. Normally newer is better which is why [COLOR=Navy]st0kes[/COLOR] mentioned that you should **upgrade your current older version** of Ubuntu. So, go ahead and click on the Ubuntu Start logo, then click on system, followed by administration (or something like that anyway). One of the available symbols that you should see off to the right is the _Update Manager_ ...** click on that** ... and then click on _refresh_ if it isn't already doing "something" in the window that you just opened up.

Once the Update Manager has been refreshed there may be an _option at the top right_ of the update Manager with a button which will permit you to upgrade your current Ubuntu version automatically. If you can see that button, go ahead and click on it. All told this can take some time from beginning to end, like a couple of hours ....

---

### Post by fredbird67 on 2010-05-27
I just looked up what the make and model is for the wireless card that comes with your laptop.  It's a RealTek RTL8191SE.  There are quite a few threads that came up when I searched "RTL8191SE" here on the Ubuntu forums.  I'd recommend seeing if you can find some answers there.

There's something else I can recommend as well.  My wife's laptop, a Dell Inspiron 6000 that we've had for five years (about as long as we've been married), has a Broadcom 4311 wireless card in it, and that too has traditionally been a real BEAR to get working under Linux.  But about a month or so ago, I happily discovered that  [PC/OS]("http://www.pc-os.org") automatically detects the Broadcom chip in that laptop, allowing me to just pick the network and off I go surfing the web! :-D  

What's more, PC/OS is based on Ubuntu, although it comes with the Xfce desktop instead of GNOME (although I think there's a GNOME version available -- but I personally prefer Xfce).  I can't guarantee that it will work in your particular situation, but it's something I would recommend trying out to see if it works for you.  If it does, you can save yourself the headache of getting the RealTek RTL8191SE to work with Ubuntu.

Hope this helps!
Fred in St. Louis

---

### Post by Rodney9 on 2010-05-27
On my Toshiba L500 Ubuntu 10.4 wireless (realtec) worked well at first, but after updates it stopped.
I am now using Xubuntu 10.4 and all, including wireless, works well, although I am worried each time the update manager launches.

---

### Post by v1ad on 2010-05-27
you could do

```
 sudo apt-get dist-upgrade 
```

but i would really recommend that you just do a new install.

---

### Post by sm4sh1t on 2010-05-29
hi again :P i just installed ubuntu netbook edition and i love it :) but the wireless still does not work. am i missing something? im so new to this.

---

### Post by sm4sh1t on 2010-05-29
i can"t make this work, please help :(

---

### Post by WinRiddance on 2010-05-29
There are numerous replies in this thread with things that you can do. If you tried all of these things you should be happy by now. If not, then go back and rad through the answers again. Earlier you asked how to install Ubuntu and you got several answers. Another thing that you can try is to install **wicd** directly from the software center. Wicd is an alternative to the default Network Manager which works better on some laptops that have WiFi problems ....
However, when you _install a different type_ of Ubuntu then you'll be less likely to receive fast answers. That's why I stick with the mothership, straight Ubuntu with tweaks and features that are designed for Ubuntu ...

---

### Post by sm4sh1t on 2010-05-29
thank you so much :) it works now :P wicd connects to my wireless now. i was up all night long trying to make it work and you just made a friend for life :)

---

