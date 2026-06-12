---
title: "No Unity after update on 16.04 with Nvidia GFX (CCSM doesn't start Unity plugin)."
date: 2016-09-18
forum: Desktop Environments
---

### Post by batmanmanbat on 2016-09-18
I have 16.04
Nvidia Geforce GTX 750i
Got drivers from Additional Drivers Proprietary drivers list following this [https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus](https://linuxconfig.org/how-to-install-the-latest-nvidia-drivers-on-ubuntu-16-04-xenial-xerus)

So it was working with 16.04 until the last update. Then unity vanished. CCSM can't restart the plugin when ticked.

Ctrl-alt-T doesn't even bring up the terminal. I have to right click on the background. Apps work fine. Just Unity is gone.

I tried this...

dconf reset -f /org/compiz/
setsid unity


and

rm -rf ~/.config/compiz-1/compizconfig/*

and

export DISPLAY=:0
ccsm


and

initctl restart unity-panel-service

Still nothing

Any ideas what is going on?

---

### Post by batmanmanbat on 2016-09-18
Just solved it.

[http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login/481620#481620](http://askubuntu.com/questions/449845/problems-after-upgrading-to-14-04-only-background-and-pointer-after-login/481620#481620)

---

### Post by Bashing-om on 2016-09-18
batmanmanbat; Hello;

Have you tried re-installing the graphic's driver ? The supposition here is that the update broke the driver that was built on an older kernel.
Also as a for-your-info :
[http://www.nvidia.com/download/driverResults.aspx/106780/en-us](http://www.nvidia.com/download/driverResults.aspx/106780/en-us)
nVidia recommends the 367 version driver . That driver is available from our trusted PPA.

But, if 361 versions works for ya why change ?

[INDENT][INDENT]maybe Yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

