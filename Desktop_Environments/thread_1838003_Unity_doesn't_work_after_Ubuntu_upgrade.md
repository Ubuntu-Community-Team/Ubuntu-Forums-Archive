---
title: "Unity doesn't work after Ubuntu upgrade"
date: 2011-09-02
forum: Desktop Environments
---

### Post by r.darwish on 2011-09-02
Until recently, my laptop was running Ubuntu 10.04 LTS just fine. I waned to try Unity since it's very spoken about, so I decided to upgrade my Ubuntu version from 10.04 LTS to 11.04. I ran the upgrade manager to upgrade to 10.10 and then upgrade to 11.04.
When 11.04 first booted I tried to log in and didn't see anything but a shadow placed where the top bar should appear (screenshot attached). I restarted X and tried to log in again and got the same thing. I am able to login to a classical gnome session with desktop effects, but the whole propose of upgrading was to try Unity.

---

### Post by grahammechanical on 2011-09-03
I get that effect on 11.04 Unity. The shadow is an effect brought about by the Compiz Config Settings Manager Windows Decoration utility.

May I suggest that you used the Software Centre to install Unity 3D or Unity 2D or both? You upgraded to 11.04 but did it upgrade to Unity? See, if Unity 3D is installed. Even a fresh install of 11.04 will not boot into Unity until without suitable drivers.

I also suggest that you remove most, if not all, the special effects that you enabled in 10.04. If you did have any enabled. Some of these effects mess up Unity. The wobbly windows effect turn the top panel from one colour into a rainbow of colours and the indicators and icons disappear. Although the same parts of the the top panel are still sensitive to the mouse click. You just have to guess where to click.

Have you checked Additional Drivers to see if there is a later driver that will work better with Unity?

Regards.

---

### Post by raja.genupula on 2011-09-03
> **r.darwish said:**
> Until recently, my laptop was running Ubuntu 10.04 LTS just fine. I waned to try Unity since it's very spoken about, so I decided to upgrade my Ubuntu version from 10.04 LTS to 11.04. I ran the upgrade manager to upgrade to 10.10 and then upgrade to 11.04.
When 11.04 first booted I tried to log in and didn't see anything but a shadow placed where the top bar should appear (screenshot attached). I restarted X and tried to log in again and got the same thing. I am able to login to a classical gnome session with desktop effects, but the whole propose of upgrading was to try Unity.


try to reset unity 

```
unity --reset
```

---

### Post by r.darwish on 2011-09-03
I tried that and still got no luck. Finally I gave up and did a fresh installation of Ubuntu 11.04. Now Unity works on my laptop. Before marking this thread as solved I would still like to know what may have caused the problem. My PC is still running the LTS version of Ubuntu, and I would also like to upgrade the OS to Ubuntu 11.04 at some point. I rather do upgrade instead of preforming a fresh installation like I did on my laptop, so maybe someone can tell me if I did something wrong in the upgrade process. I just ran *upgrade-manager -d* and did 2 distribution updates, but maybe it's impossible to convert the LTS version of Ubuntu to the latest release?

---

