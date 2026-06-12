---
title: "Restart X from a command window"
date: 2008-09-15
forum: Desktop Environments
---

### Post by naugiedoggie on 2008-09-15
Hello,

Every couple of weeks, it seems, something will happen while I'm in Gnome that will cause Xorg to peg the cpu and freeze the GUI.

The one thing I know is that ssh'ing to the box and then killing processes has no effect.  The only process that is manhandling the CPU is Xorg, which is run up to 97-99% CPU and stays there indefinitely.

Stopping/starting gdm has no effect, either.  Ctrl-Alt-Backspace doesn't work.

I'd like to know if there is some way that I can restart the X process without having to reboot the whole system -- which is currently my only option.

Thanks.

mp

---

### Post by iponeverything on 2008-09-15
do a ctl-alt-F2 login and do a:

killall -v -9 xinit

should knock off X for you.

Though I can't imagine that problem is with the xserver. Something else
is probably cause it spin out control. Maybe java?  

post a "ps auxwwww" , if you want to try to find out what causing it..

---

### Post by bingoUV on 2008-09-15
If ctrl-alt-backspace does not work, it is likely that ctrl-alt-F1 will also not work. You seem to be able to ssh to the box. Try killing Xorg from here, maybe it will work. 
```

sudo killall Xorg

```

---

### Post by naugiedoggie on 2008-09-15
> **iponeverything said:**
> do a ctl-alt-F2 login and do a:

killall -v -9 xinit

should knock off X for you.

Though I can't imagine that problem is with the xserver. Something else
is probably cause it spin out control. Maybe java?  

post a "ps auxwwww" , if you want to try to find out what causing it..

Thank you, I will put that on a postit note and try it next time.

The UI is locked up, and that includes the keyboard, although sometimes the mouse pointer will move but you can't click anything.

I switch to another system and ssh onto the errant box from there.  From the CL, I can kill all the processes running on the desktop  -- seamonkey, emacs, netbeans ... without any problem but with no effect.

Thanks.

mp

---

### Post by naugiedoggie on 2008-09-15
> **bingoUV said:**
> If ctrl-alt-backspace does not work, it is likely that ctrl-alt-F1 will also not work. You seem to be able to ssh to the box. Try killing Xorg from here, maybe it will work. 
```

sudo killall Xorg

```

Thanks for the reply.  kill -9 doesn't work ... is killall any different in the important respect (should have used killall but I forgot and just fell back to brute force).

Thanks.

mp

---

### Post by bingoUV on 2008-09-16
> **naugiedoggie said:**
> Thanks for the reply.  kill -9 doesn't work ... is killall any different in the important respect (should have used killall but I forgot and just fell back to brute force).

Thanks.

mp

killall is the same. Only difference is that it takes process name as input, and kills all processes with the name. No hassle of looking up PID of the process. You may also use -9 in killall
```

killall -9 Xorg

```

but if kill -9 did not work, killall -9 is not more likely to work.

---

### Post by ahbart on 2008-09-17
Next time you need a brute force: try a sys request first.
You see the button on your keyboard, probably under the prtscrn. ;)

If your keyboard is locked to frozen x; press: alt + sysrq + r
This will give you your keyboard back. And then the next:
alt + sysrq + e
alt + sysrq + i
alt + sysrq + s
alt + sysrq + u
alt + sysrq + b
reisub or eisub
More information: [here](http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+)
Good luck.

---

### Post by naugiedoggie on 2008-10-05
> **ahbart said:**
> Next time you need a brute force: try a sys request first.
You see the button on your keyboard, probably under the prtscrn. ;)

If your keyboard is locked to frozen x; press: alt + sysrq + r
This will give you your keyboard back. And then the next:
alt + sysrq + e
alt + sysrq + i
alt + sysrq + s
alt + sysrq + u
alt + sysrq + b
reisub or eisub
More information: [here](http://www.freesoftwaremagazine.com/columns/closing_down_gnu_linux_safely_with_sysrq+)
Good luck.

Thanks for this notice, I will try this stuff out.  Just a few days ago, it went south again, and the killall options suggested earlier did not work.

Thanks.

mp

---

### Post by Kapitän Rotbart on 2008-10-29
Ah, the trick to safely reboot Linux (spelling BUSIER backwards while holding Ctrl+Alt+Prt Scr). It will do more than restart X. It'll safely reboot the computer and take down all the drivers while doing so. Better than doing a hard reboot by holding the power key (or for some desktops, flicking the power switch). Still does more than restart X.

What's the command I could put in the command line to do exactly what Ctrl+Alt+Backspace does? My backspace key won't work (it's a laptop...I can live without the backspace key but I can't do just a "restart X").

---

