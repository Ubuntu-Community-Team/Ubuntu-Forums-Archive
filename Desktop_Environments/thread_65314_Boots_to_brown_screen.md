---
title: "Boots to brown screen"
date: 2005-09-13
forum: Desktop Environments
---

### Post by chris86wm on 2005-09-13
alright well, i have been running ubuntu for about a month now without any problems. i have been using the updates regularly and today i saw that there were 49 ready to be installed. i did the update and it finished fine. later on today i restarted the computer. it brought me up to the login screen then after that all i got was the "brown screen." after messing around a bit i decided to "reinstall" my nvidia graphics card. i used this as a guide [URL=http://www.ubuntuguide.org/#installnvidiadriver] . i went through that and it didnt really update anything or reinstall anything different than what i installed the first time. well i rebooted and now it works?!? I am not satisfied at leaving it like that without figuring out what happened.

so here are my questions....
1)what caused the problem and could i have prevented it?
2) could the "reinstall" have fixed it?
3) is it normal to get 49 updates all in one day?

thanks so much for all the help guys. this is the nicest board i have ever been on. O:)

---

### Post by Ride Jib on 2005-09-13
The only one I can semi-answer is #3, by saying that I had 67 updates today. I wouldn't worry about it. It just means some people have been busy lately programming  :smile:

---

### Post by plefno on 2005-09-13
The exact same thing happened to me.  But reinstalling the nvidia drivers seemed to fix it.  I did notice that the Nvidia splash screen wasn't showing up before login after i installed all the updates it downloaded.  But after reinstalling the drivers all is well.  Oh well.

---

### Post by chris86wm on 2005-09-13
mine did exactly that, no nvidia screen before reinstall, but after the reinstall they showed up. this is just gonna bug the heck outta me.  ](*,)

---

### Post by professor_chaos on 2005-09-13
you can get rid of the logo by adding the logo option as such

```
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
        Driver          "nvidia"
        Option          "NoLogo" "true"
        BusID           "PCI:1:0:0"
EndSection
```

---

### Post by bsussman on 2005-09-13
[QUOTE=chris86wm]
3) is it normal to get 49 updates all in one day?

[/QUOTE]

This was a heavy day.
I was in the 50s I think.
There will be days when there are none.
Or more.

I have a habit of refreshing and upgrading every day or two.

Ubuntu has a very good strategy /policy.  I wouldn't worry - watch it over some weeks - I think you will find that, while linux is prone to be very dynamic, it is not dangerously so.

Often a change in a line in a lib will factor out to many packages.  Consider for instance, if a property is added to an object for which no default should be assumable.  All the instantiations of that object might have to be changed.  Thus many downloads would be needed.

Some packages are very small.  This is deliberate and actually will have the effect of minimizing the total downloaded when a change occurs.

---

