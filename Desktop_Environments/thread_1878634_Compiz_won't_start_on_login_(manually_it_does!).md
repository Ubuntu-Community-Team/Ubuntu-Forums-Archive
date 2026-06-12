---
title: "Compiz won't start on login (manually it does!)"
date: 2011-11-10
forum: Desktop Environments
---

### Post by jasmines on 2011-11-10
Hi all,
after one of last upgrades (don't ask which one, I couldn't figure out) Compiz started to give problems.
It didn't load correctly at startup, and at the beginning I thought it was for unity, because I could get it working with a: 

```
unity --replace
```

Since it was too annoying to give this command each time I logged, I wanted to investigate and I discovered that problem could be solved also with a simple

```
compiz
```

So I tried to start my Ubuntu 11.10 with the Gnome Classic, and saw that Compiz didn't start automatically again.

With compiz-check script I get:

```
Gathering information about your system...

 Distribution:          Ubuntu 11.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use

```


And this make me a bit worried, because I don't understand what could have enabled the vesa mode, or if I had always had that driver, or maybe one of last upgrade could have the "good" drivers corrupted.

Let's close my post with a little more infos, hoping you could help to solve:

```

lspci | grep -i vga

^[[5~00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)


sudo lshw -c display | grep driver
configuration: driver=i915 latency=0

glxinfo | grep render 
direct rendering: Yes
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset x86/MMX/SSE2
    GL_EXT_vertex_array_bgra, GL_NV_conditional_render,

```

Thank you all!

---

### Post by typhoon_tip on 2011-11-10
What is starting at all at Desktop level after login, only one Nautilus bar on top which let you run the terminal ?

If that is the case, do:
```
ccsm
```

Find out Unity plugin and enable it. Resolve each conflict in favor of Unity plugin, and everything should be restored back.

---

### Post by jasmines on 2011-11-10
> **typhoon_tip said:**
> What is starting at all at Desktop level after login, only one Nautilus bar on top which let you run the terminal ?

If that is the case, do:
```
ccsm
```

Find out Unity plugin and enable it. Resolve each conflict in favor of Unity plugin, and everything should be restored back.

I could give it a try.
But first, please answer this: now I'm running Gnome Shell (gnome3) with no problems. Will activating unity plugin and solve conflicts have any issues on gnome3?

---

### Post by typhoon_tip on 2011-11-10
> **jasmines said:**
> I could give it a try.
But first, please answer this: now I'm running Gnome Shell (gnome3) with no problems. Will activating unity plugin and solve conflicts have any issues on gnome3?

No issues with Gnome 3, but you need to activate it in Unity shell and not in Gnome 3. Can you access the terminal when you login as Unity or nothing at all ?

---

### Post by jasmines on 2011-11-10
> **typhoon_tip said:**
> No issues with Gnome 3, but you need to activate it in Unity shell and not in Gnome 3. Can you access the terminal when you login as Unity or nothing at all ?

Yes, I can right click on the desktop and do "open in a terminal...". If there are no other windows, I can write in the terminal.

---

### Post by jasmines on 2012-01-01
Nothing yet, here. My unity isn't working :(

---

### Post by grahammechanical on 2012-01-01
Ubuntu 3D (unity) uses Compiz as the compositing or window manager. This is why the Compiz Configuration Settings Manager (CCSM) has a plugin for Unity to let us adjust Unity.

Ubuntu 2D does not use Compiz, neither does Gnome shell and I do not think that classic Gnome does either.

Sometimes going into Unity 2D or Gnome Shell or classic will make it easier to fix problems or conflicts in Compiz but you then have to log back into Ubuntu 3D for Unity and Compiz to work.

Remember, Ubuntu 2D and Classic Gnome (Gnome Session Fallback) are there for machines that lack the hardware to run 3D effects. We can still use these on machines that do have the hardware to run 3D effects but we will not be able to have 3D effects because these two user interfaces are not designed to give 3D effects.

To get 3D effects we need either Ubuntu Unity with Compiz as the window manager or Gnome shell with metacity as the window manager.

So, Compiz will not start when logging to Gnome Classic.

Check to see what video driver is being used. If it should be a proprietary driver makes sure it is activated and in use. Something may have deactivated the video driver and you may now be using an open source driver that is not running Unity too well or even capable of running it.

You may need to do a deactivate and then an activate.

Regards.

---

### Post by wildmanne39 on 2012-01-01
Hi, you also mention unity so if you are trying to get compiz to start automatically in unity also and it refusing we can add it to the startup applications.

Click on startup applications>Add in the window that opens for name type compiz,for command type compiz --replace then click add and close, then reboot.
Thanks

---

### Post by jasmines on 2012-01-02
I use normally Gnome Shell, so my 3D works perfectly. I can also use Unity (Ubuntu 3D) BUT I have to launch compiz manually. I tried everything, such as purging ccsm, compiz and unity itself, but the issue still remains.
If some output can help, please ask, but don't suggest to add compiz to autoruns, because it MUST start automatically.

---

### Post by qwill on 2012-01-06
I am experiencing exactly the same problem. 
The weird thing is that I created an other user in the system, and when I log with that new user, Unity/Compiz starts automatically.

I tried to compare the .gconf, .config and .local directories between users but I couldn't get a clue.

I suspect there is something in dconf-settings that cause compiz to crash at first start, but I can't confirm it.

Where hould I look to get any other ideas of what is misconfigured ?

Thanks,
Qwill

---

