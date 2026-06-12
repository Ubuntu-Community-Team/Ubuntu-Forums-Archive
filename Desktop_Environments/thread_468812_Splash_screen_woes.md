---
title: "Splash screen woes"
date: 2007-06-09
forum: Desktop Environments
---

### Post by niteblind on 2007-06-09
Hi all,

Can anyone help me here? I am trying to set the boot splash screen (usplash) back to the original ubuntu one after install Kubuntu. I was having a look around and found this entry on the forums here:

shai1
June 19th, 2006, 11:33 PM
To change back to the Ubuntu brown boot progress (usplash) theme type this in terminal

sudo update-alternatives --config usplash-artwork.so

Well i have done that and the file now looks like this:

niteblind@Wolverine:~$ sudo update-alternatives --config usplash-artwork.so 
There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-default.so). Nothing to configure.

Now this is because i did have 2 in there the one above and also a file called kubuntu-splash.so which i have since deleted whilst trying to fiddle my way through this :p. The wierd thing is that no matter what i did the same result happened which is this::

PC Boots up with kubuntu style blue themed splash
PC shuts down with ubuntu brown and orange splash

I may be puttin 2 and 2 together and coming up with 5 but from this I assume that the usplash-alternatives file is dealing with the shutdown screen only so what do I have to edit to change the start up splash?

cheers
niteblind

---

### Post by FuturePilot on 2007-06-09
I think you need to update your boot image. Try this
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
If that doesn't work try reinstalling the ubuntu-artwork-usplash package with synaptic.

---

### Post by niteblind on 2007-06-10
hi

thanks futurepilot, even though when it went through the reset it said no image found and skipped this when i restarted i now have the normal ubuntu splash as i wanted.

cheers

---

### Post by xkribble on 2007-06-21
I had nearly the same issue except with Xubuntu.  I could switch the usplash to Edubuntu Kubuntu and Xubuntu ... but this got my Ubuntu back!

Thanks!

.X.

---

