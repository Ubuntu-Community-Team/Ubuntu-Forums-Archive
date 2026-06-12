---
title: "Xsplash configeration help"
date: 2009-11-25
forum: Desktop Environments
---

### Post by apeitup on 2009-11-25
Hi all I am a newbie when it comes to linux and almost any code (well other than HTML, and being able to hack PHP about). I have been searching the Internet for hours trying to find out where the configuration  file is for Xsplash, and to be more precise the config file that sets the throbber/animation frame rate, size, and position. I have no problem with the designs or creating an animation but for the life of me I can not find out how to position the progress animation in the right position over the background image.

Any and all help is greatly appreciated.

---

### Post by scorp123 on 2009-11-25
I searched as well ... and I gave up. It's easier and less complicated to replace that stupid "xplash" with something that's easier to configure such as "splashy".

[http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25](http://maketecheasier.com/create-install-your-own-usplash-theme-in-ubuntu/2009/01/25)

Instead of removing "usplash" as mentioned in that article, you'd have to remove "xplash" ...

Maybe you better test this on a virtual machine before you try this for real, OK? It's easy to hose your system with this if you're not 100% sure what you're doing and why ...

---

### Post by apeitup on 2009-11-28
Well I am still trawling the web in hope. There is lots of post on how to customise your xsplash but they are mainly about changing backgrounds. I am going to have a look into splashy now. I am looking forward to the Grub2 gfxmenu being added. I have had a good look around the web and found the link to the developer that has some detailed information. Would be nice to get rid of the text based boot. 

I have managed to completely rework the desktop so that it now looks and feels like a Windows 7 gui. Now I know you purist out there will be saying "why? Just use windows if that what you want!". But most people have become so accustomed to this type of interface. and they run at the site of something different. So far I have managed to get people to navigate around without realising that they were not using a M$ product. 

As I said I am very new to Linux, I have tried over the years but always found it a very hard switch. Ubuntu has made it very easy for me and I am now beginning to have a poke around and actually  beginning to enjoy it.

So far I have installed it on all my home machines and have a usb boot stick for repairing the M$ computers at work when they crash (frequently).

---

### Post by scorp123 on 2009-11-28
> **apeitup said:**
>  I have managed to completely rework the desktop so that it now looks and feels like a Windows 7 gui. Yuuuck. ](*,)

Make sure you install the **"xscreensaver-data-extra"** package too. This will give you a nice ***"Blue Screen of Death"*** ... as screensaver :D 

(... you said you wanted to have a Windows feeling ... :D  ...)

---

### Post by apeitup on 2009-11-28
> **scorp123 said:**
> Yuuuck. ](*,)

Make sure you install the **"xscreensaver-data-extra"** package too. This will give you a nice ***"Blue Screen of Death"*** ... as screensaver :D 


mmmmmmmm I just reinstalling my nephews computer and am dual booting it XP Pro and Ubuntu. That is a very very good idea :twisted:

---

### Post by apeitup on 2009-11-29
ok after some searching I found out that basically you can't reposition the throbber/animation on xsplash as it is in a fixed position. There does seem to be some sort of hack where you make the throbber animation larger so the it will appear in the correct Y position ( well kind of )

Now having said that there is a development branch of the xsplah group that has coded an x,y position. Here is the link [https://code.launchpad.net/~redteam316/+junk/xsplash-config]("https://code.launchpad.net/%7Eredteam316/+junk/xsplash-config") . Now I need to know if I can add this to my current 9.10 which is fully up to date. Oh and the little thing of how to. I am going to ask them to explain it to me as you would a child :) then I may be in with a chance.

---

### Post by rdnrvn on 2010-08-05
> **apeitup said:**
> Now having said that there is a development branch of the xsplah group that has coded an x,y position. Here is the link [https://code.launchpad.net/~redteam316/+junk/xsplash-config]("https://code.launchpad.net/%7Eredteam316/+junk/xsplash-config") . Now I need to know if I can add this to my current 9.10 which is fully up to date. 

Anybody knows how to go about with this?

---

