---
title: "Having trouble installing new themes"
date: 2012-03-15
forum: Desktop Environments
---

### Post by l1ghtchaos on 2012-03-15
Well, I'm trying to install some new themes but I can't seem to find the .themes folder anywhere. Can anyone tell me what directory it is listed under? I even googled it too but I just get a bunch of crap that doesn't put me in any better situation. 

Thanks!

Oh yeah also, will setting up a new theme mess with my top panel? I have it setup with the tabs the way I want it.. I don't care if it jumbles things around, that's easy to fix, but will some of them stop working or something?

---

### Post by Rodney9 on 2012-03-15
What Version of Ubuntu are you using ?

In general terms you need to show 'Hidden Files' [https://help.ubuntu.com/11.10/ubuntu-help/files-hidden.html](https://help.ubuntu.com/11.10/ubuntu-help/files-hidden.html)

You may have to create the folder.

Instructions and cool themes - 

[http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html](http://www.techdrivein.com/2011/09/top-10-gnome-shell-themes.html)

Rodney

---

### Post by 3Miro on 2012-03-15
Open Nautilus where is says "Home Folder". Then hit Ctrl + H to see the "hidden" files. Anything starting with . is considered "hidden" by Linux and it will not show by default. Those are usually system files, so be careful when you mess with them.

---

### Post by NikTh on 2012-03-15
> **l1ghtchaos said:**
> Well, I'm trying to install some new themes but I can't seem to find the .themes folder anywhere. 

Hi , 
Also if you don't have the folder you can create it ```
mkdir .themes
``` 
:)

---

### Post by Frogs Hair on 2012-03-15
The .themes and .icons folder need to be created in 11.10.

---

### Post by l1ghtchaos on 2012-03-15
Thanks so much guys! I'm going to give that all a go right now.

---

### Post by lolpenguin on 2012-03-16
> **3Miro said:**
> Open Nautilus where is says "Home Folder". Then hit Ctrl + H to see the "hidden" files. Anything starting with . is considered "hidden" by Linux and it will not show by default. Those are usually system files, so be careful when you mess with them.

Oops. You got kinda confused with Windows. System files are NOT hidden in Linux (/usr/, /var/, /sys/, /etc/, /bin/). The stuff in your home folder is hidden to keep it looking nice.

OP: Also consider moving the themes to /usr/share/themes/ and /usr/share/icons/, otherwise they won't be available to other users and your windows won't display properly when running an application as root. You will also need GNOME Tweak Tool (gnome-tweak-tool) or Ubuntu Tweak (ubuntu-tweak, in ppa:tualatrix/next) to apply themes.

---

