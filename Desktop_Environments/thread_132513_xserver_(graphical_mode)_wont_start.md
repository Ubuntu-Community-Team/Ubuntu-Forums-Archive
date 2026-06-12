---
title: "xserver (graphical mode) wont start"
date: 2006-02-18
forum: Desktop Environments
---

### Post by QOLIM on 2006-02-18
Because I changed something I shouldent in ubuntu grafical mode
the cant start up xserver anymore at startup,
so he starts text based mode.

What can I do to put the settings back to default so grafical mode can start up again.

I tried
> sudo dpkg-reconfigure xserver-xorg
and set all thing to the default and autodetect etc
but it still wont work

Any sugestions except reinstalling?

---

### Post by nalmeth on 2006-02-18
sudo dpkg-reconfigure xserver-xorg

set driver to 'vesa', and when setting resolution, give yourself 1024 x 768 as maximum for now

> Because I changed something I shouldent in ubuntu grafical mode
what did you do?

---

### Post by Treebeard on 2006-02-18
A look in /var/log/Xorg.0.log could give you an idea what went wrong..

---

### Post by QOLIM on 2006-02-19
@nalmeth
tried but it didnt help

what i did i dont really know
but there was a window you can open under administraton on the taskbar at the top of the screen. then it said  something like warning the changes you make have effect on your system and you should now what you are doing or something like that. then i accidently clicked the remove button (yes, accidently :( ) And closed it, reopende it but saw it was still gone, so i clicked add and add something there and picked standard. that's all i did i think. 
Since then it gives the error failed to start xserver at startup

@Treebeard
It sais path not found

---

### Post by QOLIM on 2006-02-20
I don't know, but isn't there a way to just removing all xserver files (and any others if that's necesairy, dunno).
And then just reinstall it so I get the default settings.

I just don't want to install ubuntu all over again :/

---

### Post by dcostelloe on 2006-02-23
I have the same problem I just replaced a video card and nothing works. Xserver-xorg won't work using the reconfigure.
Followed the recommendations from google and now I have managed to uninstall xserver-xorg. When I try to re-install I get told to put the disk in the CD. I do so and now the cd can't be found either....

Any ideas of how to re-install this without deleted or overwriting the OS?

Thanks
:confused:

---

### Post by Treebeard on 2006-02-24
You can force a reinstall with apt-get:
```
$ sudo apt-get --reinstall install <package>
``` 
@QOLIM:
Since I'm not sure what you've deleted, I would recommend a reinstall of several xorg packages:
```

Fetch newest package list:
$ sudo apt-get update

Force to reinstall some packages (this will also overwrite files):
$ sudo apt-get --reinstall install xserver-xorg x-common xorg-common xutils xbase-clients

Reconfigure xorg configuration:
$ sudo dpkg-reconfigure xserver-xorg

``` 
@dcostelloe : 
I think you can do pretty much the same thing..

I hope this helps.

---

### Post by dcostelloe on 2006-02-24
Is there a way to force it to update via the internet rather than the cd as I can't get the cd to work asks me to put ubuntu cd in /cdrom when I do I hit enter and it loops

---

### Post by QOLIM on 2006-02-26
@Treebeard

didn't help :( 

I still get the same error at startup
I looked what could be wrong and it said 
> Option not found : myoption

myoption is the thing I added after I deleted the default option (I think it was in login screen configuration you could choose a tab xserver in the graphical interface)

So how can I delete that option?

---

### Post by cdsboy on 2006-02-26
if you want to do it using the cd you have to mount if it isn't auto mounting. just type 
> mount /media/cdrom0
with the cd in the drive. that should fix your no cd problem

---

