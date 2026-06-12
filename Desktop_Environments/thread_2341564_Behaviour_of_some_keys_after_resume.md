---
title: "Behaviour of some keys after resume"
date: 2016-10-29
forum: Desktop Environments
---

### Post by Chip88 on 2016-10-29
Hey there,

I realzied two strange behaviours after suspending my notebook:
1. When I send my notebook to "sleep" (suspending by closing the monitor) and then resume it, I have the numlock turned off, although it was turned on before suspending.
I have to press the "num &#8595;" key to enable it again.

2. I'm using the win-key (SUPER L) to open the KMenu. To do so, I have a script in *~/.kde/Autostart *which contains*:*
```
#!/bin/bash
xmodmap -e 'keycode 133 = F13'

```

I followed the [instructions here]("https://cvalcarcel.wordpress.com/2012/01/07/kubuntu-11-10-mapping-the-windows-key-to-activate-kmenu/") to map the SUPER_L to the KMenu.

But the function of the script is lost after sending my notebook to "sleep" in the same way as mentioned above: suspending by closing the monitor. When I resume the notebook, the win key has no functionality at all. I have to restart it via the console typing *~/.kde/Autostart/win-key.sh* in.

I searched with Google and find some hints. For example, to create a file in */etc/pm/sleep.d/* and put the following hard code (because of the path) in it:
```
#!/bin/bash


case "$1" in
    thaw|resume)
    /home/mark/.kde/Autostart/win-key.sh restart 2>/dev/null
    ;;
esac
exit $?

```

But, unfortunately, it doesn&#8217;t work.

&#8594; For sure, there is a way to have the numlock and the script for win key enabled on resume.

I'm running **Kubuntu 14.04.5 LTS**
and as Kernel: **3.13.0-100-generic**.

Thank you very much in advance for your help!

Regards,
Chipy

---

