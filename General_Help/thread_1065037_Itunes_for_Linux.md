---
title: "Itunes for Linux"
date: 2009-02-09
forum: General Help
---

### Post by draxz on 2009-02-09
Hello,

I have an Iphone 3G and want to connect it to Ubuntu and transffer music,photos etc back and forth

Is there a Itunes for Ubuntu or any other software

---

### Post by LowSky on 2009-02-09
itunes isn't made for Linux. You can try to get it running with a application called WINE, but It doesn't work so well.

Best option is using Windows in a Virtual machine or dual booting

---

### Post by personjerry on 2009-02-09
if you jailbreak your iphone (basically breaking the security mechanisms made by apple, allowing downloading of apps not from app store... jailbreaking IS reversible), you can use SSH to transfer files from your computer to iphone.

See this link on how to jailbreak:
[https://help.ubuntu.com/community/PortableDevices/iPhone]("https://help.ubuntu.com/community/PortableDevices/iPhone")

---

### Post by epqr on 2009-02-09
iTunes work thru wine, but wine has no usb support. ergo you will not be able to sync you iphone with itunes under wine.

Read [this]("https://help.ubuntu.com/community/PortableDevices/iPhone#Syncing%20iPhones%20and%20iPods%20Touch%20w/%20Firmware%202.x") . It tells you how you cans sync your iphone with programs like amarok and gtkpod. Its a little complicated, but its worth a try.

---

### Post by Therion on 2009-02-09
Don't know about connectivity, but Songbird is the Linux "iTunes" application.

[http://getsongbird.com/](http://getsongbird.com/)

---

### Post by gjoellee on 2009-02-09
Amarok:
```
sudo apt-get install amarok
```

GTKPOD: 
[http://www.getdeb.net/app.php?name=gtkpod](http://www.getdeb.net/app.php?name=gtkpod)

Songbird: (I recommend this Songbird)
[https://help.ubuntu.com/community/Songbird](https://help.ubuntu.com/community/Songbird)

---

### Post by personjerry on 2009-02-09
amarok and other similar programs only work with iphones that have been 'jailbroke' and require some more programs in order to sync. the main point is still that you have to jailbreak it, which requires a windows or mac system.

---

### Post by draxz on 2009-02-09
I have already jailbroken my phone and have XP

the problem is I have allocated only 3 gb for XP since I dont use it.

I seem to be loosing interest in Ubuntu and thinking of uninstalling it because I have to swtich to XP for voice and video chat on msn and yahoo, I am having lots of problems like the wireless not showing up and not letting me choose the wireless, most applications are for windows

---

### Post by mb_webguy on 2009-02-09
> **draxz said:**
> I have already jailbroken my phone and have XP

the problem is I have allocated only 3 gb for XP since I dont use it.

I seem to be loosing interest in Ubuntu and thinking of uninstalling it because I have to swtich to XP for voice and video chat on msn and yahoo, I am having lots of problems like the wireless not showing up and not letting me choose the wireless, most applications are for windows

If you your phone is jailbroken you should be able to get it to work with the various applications mentioned in this thread.

Voice and video chat over MSN is supposedly in the works for Pidgin, but yes, as far as I know it is not currently available for Linux.

Wireless issues can be fixed.  Once the problem is identified, the solution is often fairly simple.  I have installed Ubuntu on several different laptops with several different wireless cards, most of which unfortunately weren't natively supported by Linux (darn you, Broadcom!).  In every case, I was able to get the wireless running just as well under Linux as it did under Windows.  In matters of using a Windows wireless driver with ndiswrapper, the solution is usually to simply disable conflicting modules.

And I would have to disagree that "most applications are for Windows".  Most *commercial* applications are designed for Windows, but for every commercial Windows application, there are usually two or three free alternatives available for Linux.  In over two years of using Linux as my primary desktop OS, I have yet to have a need for which I couldn't find a free software solution for Linux, where as in the numerous years I have used Windows as my desktop OS, there were many occasions when the only available software solutions to a particular need were commercial applications that would have cost me considerably more that I was willing or able to pay.

Having said that, there's no such thing as a perfect OS.  Some OSes are a better fit for some people than others.  If voice and video chat is a deal-breaker for you, then Linux probably isn't (currently) the ideal OS for you.

---

### Post by williane on 2009-02-09
I recommend using a VM (virtualbox or VMware are good/free) and installing XP with iTunes.

---

### Post by DougieFresh4U on 2009-02-09
I don't know how I really did it, but I opened amarok and clicked devices. Plugged my Ipod Shuffle into the USB and created a list, right clicked the list and choices popped up, one being 'start transfer' and when it finished, I put headphones on and music was there!! I didn't have to do any 'tinkering', maybe it was luck, but 'amarok' just worked.
By the way, 'amarok' has been my choice of music player since I started using 'Ubuntu', and I am sticking with the 1.4.10 version as I think the new version is 'horrible'.

---

