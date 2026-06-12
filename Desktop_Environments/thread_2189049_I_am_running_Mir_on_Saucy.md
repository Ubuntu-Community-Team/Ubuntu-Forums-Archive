---
title: "I am running Mir on Saucy"
date: 2013-11-20
forum: Desktop Environments
---

### Post by fondatommaso2 on 2013-11-20
Hi folks,
just to try it, I've installed unity-system-compositor. Then I rebooted my pc. Now I'm running mir and everything is working. Unity is as fast as before and I can do all the things that I could do before. is it possible?
on the Mir wiki ([http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)) I read that I'm "Using Mir as a system compositor with X".
What does this mean?
Thanks in advance

---

### Post by grahammechanical on 2013-11-20
What you are using is not full Mir that will in future replace the X stack and Light Display Manager and Compiz but Xmir which is being used instead of Xserver. By the way, are you using a proprietary video driver? Then you may not be running on Xmir. Try running this command

```
 grep -i xmir LoadModule /var/log/Xorg.0.log
```

You need to see something that tells you that the xmir module is loaded. During the saucy development cycle I tried running all the flavours on Xmir. The only one that failed was Ubuntu Gnome and I worked out that it was because Ubuntu Gnome used GDM and not LightDM.

There is a big issue with using Xmir with proprieatary video drivers and many machines need the proprietary drivers. I use Nouveau and I am satisfied with the performance.

Regards.

---

### Post by fondatommaso2 on 2013-11-21
Here is the command output
```

grep: LoadModule: no such file or directory
/var/log/Xorg.0.log:[    31.325] (II) "xmir" will be loaded by default./var/log/Xorg.0.log:[    31.472] (II) LoadModule: "xmir"
/var/log/Xorg.0.log:[    31.472] (II) Loading /usr/lib/xorg/modules/extensions/libxmir.so
/var/log/Xorg.0.log:[    31.504] (II) Module xmir: vendor="X.Org Foundation"
/var/log/Xorg.0.log:[    37.861] (II) [XMir] Handling focus event, new_focus = TRUE

```

And no, I'm not using any closed source driver 'cause I've got an intel graphic card.
But I didn't understand well the difference between "Using mir as a compositor with Xorg" and "Using Mir natively" on this page: [http://unity.ubuntu.com/mir/using_mir_on_pc.html](http://unity.ubuntu.com/mir/using_mir_on_pc.html)
Thank you again

---

### Post by grahammechanical on 2013-11-21
Some of us were testing MIr/Xmir during the saucy development cycle. I found the information in that link to be confusing and it was difficult to get things working. Later I was able to use the information in this blog to install and get Xmir running.

[http://www.olli-ries.com/running-mir/](http://www.olli-ries.com/running-mir/)

But the information there has been superceded by this

[https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing)

As a point of interest, I am now running Trusty Tahr and yesterday I tried installing unity-system-compositor (mir/xmir) from the software centre and although it installs it does not run. This command

```
grep -i xmir /var/log/Xorg.0.log
```

gives this report

> [    18.707] (WW) "xmir" is not to be loaded by default. Skipping.

I have not yet found a way around this.  It does seem that you have mir/xmir installed and the module is loading on 13.10. Commands we can use to check if the xmir module is loaded are

> ps aux | grep unity-system-compositor
grep -i xmir /var/log/Xorg.0.log
ls -l /var/log/lightdm/unity-system-compositor.log
[SIZE=2][FONT=arial][COLOR=#333333]cat /var/log/Xorg.0.log | grep -i xmir[/COLOR][/FONT][/SIZE]

Regards.

Edit: Since posting this I have found out that in Trusty Tahr we have to install ubuntu-desktop-mir to get Xmir. It is in the software centre.

---

