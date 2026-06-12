---
title: "Ubuntu crashes constantly"
date: 2009-05-15
forum: General Help
---

### Post by Luffer on 2009-05-15
I moved to Ubuntu because it's supposed to be more stable but I'm experiencing constant crashes with Ubuntu. Literally every 5-10 mins the desktop just goes black and then it shows me the login screen.

Anything I was working on is lost and I have to start again. I can't work in this environment, the crashes are too frequent.

How can I track down what the problem is? Please don't make me go back to Windows, at the moment that seems to be my only option. Save me!

Regards

---

### Post by PetterDK on 2009-05-15
That is very difficult.. Are you doing the same thing every time it crashes?

---

### Post by leandromartinez98 on 2009-05-15
Which version of Ubuntu are you using and which hardware?

Also, is there any chance you are typing Control-Alt-Backspace 
by mistake?

---

### Post by drubin on 2009-05-15
This does seem like a graphics card issue. I had the same issue with my ATI card on Jaunty with the proprietary drivers.

What card are you running?
give the output of ```
lspci | grep -i vga
```

Also with version of ubuntu are you running?

---

### Post by drubin on 2009-05-15
Forgot to add take a look at the output of 
```
dmesg
``` to see if there are any errors that relate to the time when this happens.

---

### Post by Luffer on 2009-05-15
> What card are you running?

01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)

> is there any chance you are typing Control-Alt-Backspace by mistake?

No, definitely not.

> Which version of Ubuntu are you using and which hardware?

Ubuntu 9.04

> Are you doing the same thing every time it crashes?

Seems to be when I'm using Firefox, but not sure if that is directly related to it.

---

### Post by Luffer on 2009-05-15
Output of dmesg:

[http://pastebin.com/m526f636f](http://pastebin.com/m526f636f)

Don't know what I'm looking for, but anything there to give any clues?

---

### Post by KhurramM on 2009-05-15
What exactly do u do in firefox, that makes it crash.

Try midori, opera, epiphany to see if the problem retains itself.

---

### Post by leandromartinez98 on 2009-05-15
Probably there is a restricted driver available for your video card
(system -> administration -> hardware drivers). If it is not activated,
try activating it.

---

### Post by drubin on 2009-05-15
> 10.294446] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009

That line makes me believe those drivers are installed.

---

### Post by Luffer on 2009-05-15
> Probably there is a restricted driver available for your video card

I'm already using the restricted driver for the video card.

> What exactly do u do in firefox, that makes it crash.

I'm just browsing, sometimes editing my website, browsing forums. Nothing specific that I can tell. But why would Firefox cause the whole OS to crash? Even Windows doesn't do that anymore and hasn't done for years!

---

### Post by dslink on 2009-05-15
im having the same issues with jaunty, crashing (lock ups) system is just idle after login.  switched video drives and ect, but with apt/dpkg crashing every time you go to use them.  makes you wonder if they did any testing before this release or was it just for them to push a new kernel and file system out.... really disapointed, going back to debian because of this, ill take the extra hour to configure everything to work (sound flash video) just to have a system that doesnt lockup every 20 mins or be able to update the system.

---

### Post by leandromartinez98 on 2009-05-15
You may try disabling the proprietary driver. I mean, just to know if it is an video driver issue. On the other side, I have the feeling that these Nvidia cards should work fine. Therefore, if it is a driver issue, I would bet for a corrupted instalation.

dslink: There is a known bug in Jaunty for some Intel video cards. If you have one them yes, it would had been better not to update. I fell into the same issue.

---

### Post by purduepilot on 2009-05-18
Mine's been having the same problem since I upgraded to 9.04.  It's really frustrating.  Only happens when I'm using Firefox.  I never had problems like this with 8.04 or 8.10, though installing 9.04 was a lot easier than getting everything working with 8.04 and 8.10...

---

### Post by drubin on 2009-05-18
Since you did an upgrade you might have some stale configs.

run this 
1) Close firefox
2) run the code below 
```
mv ~/.mozilla ~/mozilla.bak
```
3) start firefox again.

This will basically remove all your bookmarks, settings plugisns and any thing else that might be causing issues. If this doesn't solfe your issue or you would like to return back to your old setting just replace your ~/mozilla.bak folder back to ~/.mozilla

---

### Post by dslink on 2009-05-21
are any of you guys running jfs or ext4 ?  i went back to hardy and had no problems with jfs or ext3.  

In jaunty with jfs or ext4 (havent tried ext3 yet about to)  i get file system errors like crazy, bad inodes and everything, corruption all over the place, and this happens when the system is RUNNING not even after a reboot or a powerfailure.  

Wondering if this is a bigger issue beond ubuntu.

Also im using x64 release's for 9.04 and 8.04

---

### Post by Bigneil on 2009-05-21
Why not try a different version of ubuntu   like Hardy Heron 8.04 that is the lts one, and see what happens.   

I am pretty sure that on my pc for example that the new Jaunty ubuntu wont like my graphics card because it's quite old.

Oh, and i had similar freeze ups related to compiz. i just have all the eye candy disabled now.

---

### Post by dslink on 2009-05-21
i did try hardy, and i have been using hardy on this laptop for a while and no problems, same with intrepid.  soon as i move to jaunty the problems started.  I also did a fresh install of jaunty.  And reinstalling jaunty right now debating if i should use ext3 and see if i still have the same issues.  Just very strange to get file sys corropption only in jaunty.   with my laptop that had intrepid on it running jfs, i used to always just unplug it and the system would come back all the time wiht no fs errors or dataloss.

after looking at the forms im not the only one having problems like this in jaunty, im going to try a more current kernel in the testing/unstable branch of ubuntu and if that doesnt do it ill just rebuild the latest or .28 and see what happens.

---

