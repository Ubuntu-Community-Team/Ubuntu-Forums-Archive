---
title: "power management, frequency scaling in Xubuntu feisty"
date: 2007-08-03
forum: Desktop Environments
---

### Post by flexus on 2007-08-03
Hi, I installed xubuntu a couple of days ago on my aging toshiba portege 3440 CT with a P3 500 mhz processor. I love it, exept from the fact that I am unable to configure power settings. 

Someone told me about laptop-mode-tools but I could not get that working. I downloaded kpowersave for a nice graphical interface, and I like it. The problem is I am unable to set the frequency of the cpu. When I try to change any of the frequency schemes in kpowersave it just says "CPU freq policy <chosen policy> could not be set." 

Does anyone know what the problem might be? Are there any other software more suitable or xubuntu but does the same things? Basicly, Kpowersave has the functions I want. 

Lastly are there any specific programs for toshiba? Anyone know about wmpower?

Thank you all very much in advance 

regards
k

---

### Post by orawax on 2008-01-10
xfce4-cpu-freq-plugin perhaps?

> [packages.ubuntu.com](http://packages.ubuntu.com/feisty/x11/xfce4-cpu-freq-plugin): 

The CpuFreq Plugin shows in the Xfce Panel the following, chooseable informations:

 * current CPU frequency
 * current used governor

In a separate dialog it provides you following informations of all available informations:

 * all available CPU frequencies
 * all available governors
 * used driver for the cpu

Homepage: [http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-cpufreq-plugin)


---

### Post by bjrnfrdnnd on 2008-01-24
Well, let's say the description of xfce4-cpu-freq-plugin seems to say that it does what one wants. However, at least in my case, this thing does not change anything. It only monitors. 
When I do something like 
```
echo "powersave" |sudo tee /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```
, 
the applet correctly states that I have been switching to powersave governor. 
However, using the mouse to change the governor to whatever thing, and then hitting close, does not change a thing. 
Anyone has observed this?

BTW, similarly, when trying to use Applications->Settings->Keyboard Settings, 
and then choosing the Layouts tab, you can add all the languages and layouts you want...
Whenever you close the thing, it goes back to the "Use X configuration" checked state, with only us Layout in the Keyboard Layout field...
So, it seems to me to behave in the same way as the xfce4-cpu-freq-plugin: All changes disappear once pressed "Close"

I am running xubuntu 7.10 on an i386 machine, Samsung x20
Thanks, B

---

### Post by bostjan on 2008-02-14
I found this link 
[http://lists.alioth.debian.org/pipermail/pkg-xfce-commits/2005-October/000200.html](http://lists.alioth.debian.org/pipermail/pkg-xfce-commits/2005-October/000200.html)
there is written what xfce4-cpu-freq-plugin cannot yet do
> -WHAT IT SHOULD DO BUT DOESN'T
------------------------------
-
-* Somehow use the panel plugin as an interface to set the clock speed.
-* Provide more information in tool tips.

Instead you governer plugin can be used but you can't change the cpu freq alone. Still does it's job though.
[http://packages.ubuntu.com/hardy/x11/xfce4-governor-plugin](http://packages.ubuntu.com/hardy/x11/xfce4-governor-plugin)

---

### Post by chochem on 2008-03-04
The panel plugins are nice but how do I change the default setting? I found a [howto]("http://ubuntuforums.org/showthread.php?t=597998") but it's GNOME-centric (I don't think I'd be using the GNOME power manager in XFCE, right?) How do I do it in XFCE?

---

### Post by jeffus_il on 2008-03-04
> **flexus said:**
> Hi, I installed xubuntu a couple of days ago on my aging toshiba portege 3440 CT with a P3 500 mhz processor. I love it, exept from the fact that I am unable to configure power settings. 

Someone told me about laptop-mode-tools but I could not get that working. I downloaded kpowersave for a nice graphical interface, and I like it. The problem is I am unable to set the frequency of the cpu. When I try to change any of the frequency schemes in kpowersave it just says "CPU freq policy <chosen policy> could not be set." 

Does anyone know what the problem might be? Are there any other software more suitable or xubuntu but does the same things? Basicly, Kpowersave has the functions I want. 

Lastly are there any specific programs for toshiba? Anyone know about wmpower?

Thank you all very much in advance 

regards
k

There is no problem running the Gnome power manager/daemon in XFCE, you probably are running gnome support by default. See the "Settings Manager"->"Sessions and Startup"->"Advanced tab"

---

### Post by chochem on 2008-03-04
I guess the point is that I'd rather not (it's a pretty big package). The plugins show that you don't need gnome stuff to change this setting, so surely there must be sone configuration file somehere that I can edit?

---

### Post by chochem on 2008-03-10
To answer my own question: Instead of using the cpufreq governors, the job of cpu frequency scaling can be handed to the powernowd daemon (the governor setting will appear as 'userspace'). 
1) make sure you have powenowd installed (might require uninstalling gnome-power-manager and/or cpudyn) 
2) add a powernowd line to /etc/rc.local, e.g. 'powernowd -m 0 -l 40 -u 80' (check the powernowd man page for details on settings)
3) restart

---

