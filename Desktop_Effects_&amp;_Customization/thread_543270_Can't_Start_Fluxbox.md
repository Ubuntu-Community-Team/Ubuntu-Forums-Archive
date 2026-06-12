---
title: "Can't Start Fluxbox"
date: 2007-09-04
forum: Desktop Effects &amp; Customization
---

### Post by Wanabe on 2007-09-04
Hello All:

I'm running Server 7 which does not have a desktop by default.  Originally I wasn't going to install one but Fluxbox has me very curious.

I've installed Fluxbox (apt-get) but when I type "startfluxbox" I get the following error:

Warning: Failed to open file (/usr/share/fluxbox/nls/en_US.UTF-8/fluxbox.cat)
for translation, using default messages.
Error: Couldn't connect to XServer


I've checked the directory listed in the error message and the directory en_US.UTF-8 doesn't exist amongst those that are there.

I'm wondering if I must first install the Ubuntu desktop prior to installing Fluxbox.

Any assistance much appreciated.

Thanks,
Wanabe

---

### Post by kerry_s on 2007-09-04
you got to get "X" as well>

sudo apt-get install xorg
startx

---

### Post by gtrtx on 2007-09-04
It doesn't sound as if you've got an X server installed. I'm not sure what the apt-get command is to install everything you need. At one point I installed just server and was going to put only flux as my Desktop just as you are trying to do. I ended up doing "sudo apt-get install xubuntu-desktop"  

That installed everything I needed then flux worked after that. However, that installs XFCE and several apps that you may not want. But it was a quick and dirty way to get everything I needed for a GUI. 

I suspect you could do "sudo apt-get install xorg" just to get an xserver installed. 

I'm sure someone that is a bit more knowledgeable will be by soon with a better answer.

---

### Post by Wanabe on 2007-09-04
Thanks folks.  

Just tried installing xorg and received the same error.  I'll try installing xubuntu-desktop and see where that gets me.

Thanks again!

---

### Post by Rupertronco on 2007-09-05
you don't need the whole xubuntu-desktop meta package. also, use aptitude to install it, it makes it much easier to get rid of if you ever have the desire. 

i'd use 

```
sudo aptitude install xfce4
```

---

### Post by Wanabe on 2007-09-05
Dang.  Already installed the full xubuntu desktop.  It sure took a while.   That's OK.  I may rebuild the entire server anyway at some point in the near future.

---

### Post by kerry_s on 2007-09-05
> **Wanabe said:**
> Dang.  Already installed the full xubuntu desktop.  It sure took a while.   That's OK.  I may rebuild the entire server anyway at some point in the near future.

on you next build, just remember X has to be installed before the WM.
example:
sudo apt-get install xorg fluxbox
startx

---

### Post by Wanabe on 2007-09-05
Got it.  Wil do.

Thanks!

---

### Post by Wanabe on 2007-09-05
Thanks kerry_s!  

I have Server 7 installed in a virtual environment as well.  I tried as you suggested 
(sudo apt-get install xorg fluxbox) and it seems to be working great.

Thanks again

---

