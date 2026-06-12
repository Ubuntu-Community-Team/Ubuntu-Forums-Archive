---
title: "Shortcuts don't work any more"
date: 2016-09-08
forum: Desktop Environments
---

### Post by edward8 on 2016-09-08
I upgraded my Lubuntu installation to 16.04 and the keyboard shortcuts I had set up to switch between monitors stopped working. These were saved in the file ~/.config/openbox/lubuntu-rc.xml.

This used to work fine - I used the Windows key plus a number to switch monitors. Now nothing happens when I press the keys.

Thanks for any help you can give me!

```
    <!-- Internal monitor only -->    <keybind key="W-1">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --mode 1024x600 --rate 60.0 --output VGA-0 --off --output DVI-0 --off</command>
          </action>
    </keybind>
    <!-- External VGA monitor only -->
    <keybind key="W-2">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --off --output VGA-0 --mode 1024x768 --rate 60.0</command>
          </action>
    </keybind>
    <!-- TV (720p) only -->
    <keybind key="W-3">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --off --output DVI-0 --mode 1280x720 --rate 60.0</command>
          </action>
    </keybind>
    <!-- TV (1080p) only -->
    <keybind key="W-4">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --off --output DVI-0 --mode 1920x1080 --rate 60.0</command>
         </action>
    </keybind>
```

---

### Post by vasa1 on 2016-09-08
I don't have multiple monitors and so can't help with xrandr.

But just to eliminate the obvious ... 
Do other keyboard shortcuts in your lubuntu-rc.xml work as before?
Does ```
openbox --reconfigure
``` throw up any messages?
Do the xrandr commands work as expected if you run them from a terminal?
Have you tried something like 
```
<command>sh -c 'xrandr --output LVDS-0 --mode 1024x600 --rate 60.0 --output VGA-0 --off --output DVI-0 --off'</command>
```
instead of 
 ```
<command>xrandr --output LVDS-0 --mode 1024x600 --rate 60.0 --output VGA-0 --off --output DVI-0 --off</command>
```because there maybe some changes in how the Openbox version in 16.04 parses your code compared to the Openbox version in 14.04?

---

### Post by edward8 on 2016-09-08
Thanks for your reply!
openbox --reconfigure returned no messages of any kind

Putting the xrandr commands straight into the terminal gave some errors. Should I change something?

> :~$ xrandr --output LVDS-0 --off --output VGA-0 --mode 1024x768 --rate 60.0
warning: output LVDS-0 not found; ignoring
warning: output VGA-0 not found; ignoring
~$ sh -c 'xrandr --output LVDS-0 --off --output VGA-0 --mode 1024x768 --rate 60.0'
warning: output LVDS-0 not found; ignoring
warning: output VGA-0 not found; ignoring


---

### Post by vasa1 on 2016-09-08
> **edward8 said:**
> Thanks for your reply!
openbox --reconfigure returned no messages of any kind

Putting the xrandr commands straight into the terminal gave some errors. Should I change something?

That openbox --reconfigure didn't give you anything is a good sign. No parsing errors in your rc.xml.

Would you expect those commands to work from the command line? I have no experience with xrandr but I hope someone who knows comes along. But, as a general principle, you should test things first in the terminal before including them in your rc.xml.

---

### Post by edward8 on 2016-09-08
Not a Linux expert - but I'd made the shortcuts work before - it's only the update that changed things.

---

### Post by edward8 on 2016-09-08
But thanks for your help nonetheless!

---

### Post by vasa1 on 2016-09-08
You can ask here: [https://lists.ubuntu.com/mailman/listinfo/lubuntu-users](https://lists.ubuntu.com/mailman/listinfo/lubuntu-users)

You'll have to sign up first.

One more thing is to look at **man xrandr** to see if the syntax you used in the past is still valid.

---

### Post by edward8 on 2016-09-13
OK, I managed to fix it (at least for the internal and VGA monitor - haven't tried the HDMI-connected TV yet).


Firstly, I used the command


> xrandr --query


...to show the connected monitors, and it seems that the names of the internal and external monitors have changed from LVDS-0 and VGA-0 to LVDS-1 and VGA-1.

Changing this in the configuration file make the whole thing work again.

---

