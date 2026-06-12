---
title: "Switching monitors with keyboard shortcut"
date: 2015-03-10
forum: Desktop Environments
---

### Post by edward8 on 2015-03-10
I've been trying to make it so I can switch my internal/external monitors using keyboard shortcuts (Super+1 = internal only; Super+2 = external only). I added this to my lubuntu-rc.xml file:-

```

 <!-- Internal monitor only -->
    <keybind key="W-1">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --off --mode 1024x600 --rate 60.0</command>
          </action>
    </keybind>
    <!-- External VGA monitor only -->
    <keybind key="W-2">
      <action name="Execute">
        <command>xrandr --output LVDS-0 --off --output VGA-0 --mode 1024x768 --rate 60.0</command>
          </action>
    </keybind>

```

When switching to external, the internal switches off, as I wanted. However, when switching to internal, the external remains on - which I don't want.

Could anyone give me some help as to how to change the code to switch the external off?

Thanks for your help!

Ed

---

### Post by tgalati4 on 2015-03-10
What is the hardware?  Typically there are settings in the BIOS for how this switching occurs.  Sometimes it is hardwired to be round-robin, so it cycles between modes and one of those modes is dual display.  So you may be able to assign a hot-key, but it will simply cycle, in order, between 4 modes:  Laptop Screen only, Both, External Screen only, Both off.

What is the special key function (blue keys) that cycles the display?  What modes does it offer?

---

### Post by edward8 on 2015-03-10
Thanks for your reply

I've got an Acer Aspire One. I'm not sure exactly which hotkey is supposed to cycle the monitors - maybe Fn-F5, but the hotkey has no effect.

I can achieve the effect I want using the Preferences>Monitor Settings dialog, but I really wanted a keyboard shortcut.

---

### Post by tgalati4 on 2015-03-10
According this link is it Fn-F5.  [http://acer--uk.custhelp.com/app/answers/detail/a_id/3009/~/hotkeys-and-key-combinations-on-aspire-one-netbooks](http://acer--uk.custhelp.com/app/answers/detail/a_id/3009/~/hotkeys-and-key-combinations-on-aspire-one-netbooks)

Press Fn-F5 slowly 4 times and describe what happens at each press.

---

### Post by CantankRus on 2015-03-10
Similar thread where you might find something useful....
[http://ubuntuforums.org/showthread.php?t=2246932](http://ubuntuforums.org/showthread.php?t=2246932)

---

### Post by edward8 on 2015-03-11
tgalati4 - Fn-F5 doesn't seem to do anything at all.
CantankRus- I think that's given me the answer. I haven't got the 2nd monitor here, so I'll check on Friday. Thanks!

/edit - it worked. Thanks for your help, everyone!

---

