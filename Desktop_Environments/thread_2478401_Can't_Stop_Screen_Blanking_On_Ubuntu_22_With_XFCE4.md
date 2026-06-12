---
title: "Can't Stop Screen Blanking On Ubuntu 22 With XFCE4"
date: 2022-08-25
forum: Desktop Environments
---

### Post by mdiemer on 2022-08-25
I'm guessing this should go in the Desktop Section? So, I have a minimal Ubuntu 22.04 install, and I added XFCE4, since I don't like Gnome. (Why not use Xubuntu? I want the full 5 year LTS support). No matter what I do, I can't prevent the screen from blanking after only a few minutes. It's irritating, because I usually have two computers going, both using the same monitor. So I have to not only jiggle the mouse, but press a button on the monitor to get back on the Ubuntu computer. (The monitor will switch to the other computer, which has Bodhi on it). This is very irritating, and not actually easy to do, so I really need to fix it!

I have of course disabled every setting I could find, not only on the XFCE session, but I also logged in to both the Ubuntu and Xorg sessions, and disabled stuff there. the problem remains. Is this an XFCE4 bug?

Thank you.

---

### Post by &amp;KyT$0P# on 2022-08-25
> **mdiemer said:**
> (Why not use Xubuntu? I want the full 5 year LTS support). 

:confused:
Xubuntu **_is_** Ubuntu + Xfce packages.  What doesn't have the full 5 year support is the Xfce packages, you get these same packages regardless of whether they came from your installation media or you installed them yourself later.

Xubuntu 22.04 support time is identical to what you have.

Your current setup will have a mix of GNOME and Xfce services, which could significantly complicate these type of problems compared to if you had just used Xubuntu.  So to make your system maintenance easier on you and increase the odds that people here can help with the screen blanking issue, can you do a new clean install of Xubuntu 22.04?  Or do you have another reason why you sometimes need or want to use GNOME?

---

### Post by mdiemer on 2022-08-25
Thank you for your reply. I was under the impression that the life cycle of Xubuntu was 3 years, but I see from your remark i may have been wrong. I might have gone with Xubuntu had I known that.

The reason I did this, in addition to what I previously stated, was also to have a minimal install, so I'm not updating Thunderbird, Libre Office etc every time there's an update. This system is only to create music on. I use the DAW Reaper For Linux, and compose classical music with it. 

To get everything working, via wine, is a process, so now that I have it up and running I'm just going to have to live with it. The only real issue is the screen thing, and that is very minor, compared to a complete reinstall.

---

### Post by QIII on 2022-08-25
The standard support period for Xubuntu is 3 years, which is true of all the flavors -- including Kubuntu.  The base Ubuntu packages may enjoy 5 years, but with Xubuntu you have Xfce packages that are supported by the community developers for only 3 years.  Thus, standard support for Xubuntu is 3 years.  A base, minimal install of Ubuntu with the Xfce DE will still only be supported for 3 years, which is why Xubuntu would have the same support period as your setup.

The flavors are maintained by their communities, which do not have the resources even of a small company like Canonical.

---

### Post by &amp;KyT$0P# on 2022-08-25
> **mdiemer said:**
> The reason I did this, in addition to what I previously stated, was also to have a minimal install, so I'm not updating Thunderbird, Libre Office etc every time there's an update.

For what it's worth, Xubuntu 22.04 has a minimal install option.  I used it and it didn't include either Thunderbird, LibreOffice etc.

> To get everything working, via wine, is a process, so now that I have it up and running I'm just going to have to live with it. The only real issue is the screen thing, and that is very minor, compared to a complete reinstall. 

Which of these have you already tried so far:
 - GNOME settings
 - Xfce power manager settings > Display
 - xfce4-screensaver settings (if you have it installed): explicitly deactivating both "Activate screensaver when computer is idle" and "Enable Screensaver"
 - As a workaround, although maybe not a real solution, enable Presentation mode in Xfce power manager

If all of the above failed, check output from running the following command in Terminal -
```
xset q
```

---

### Post by mdiemer on 2022-08-25
> **halogen2 said:**
> For what it's worth, Xubuntu 22.04 has a minimal install option.  I used it and it didn't include either Thunderbird, LibreOffice etc.



Which of these have you already tried so far:
 - GNOME settings
 - Xfce power manager settings > Display
 - xfce4-screensaver settings (if you have it installed): explicitly deactivating both "Activate screensaver when computer is idle" and "Enable Screensaver"
 - As a workaround, although maybe not a real solution, enable Presentation mode in Xfce power manager

If all of the above failed, check output from running the following command in Terminal -
```
xset q
```

I can't find XFCE4 power manager, don't think it's installed. I did not install the full XFCE desktop, just the basic one. 

Here's the output of vset q:


michael@michael-To-be-filled-by-O-E-M:~$ xset q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  XKB indicators:
    00: Caps Lock:   off    01: Num Lock:    on     02: Scroll Lock: off
    03: Compose:     off    04: Kana:        off    05: Sleep:       off
    06: Suspend:     off    07: Mute:        off    08: Misc:        off
    09: Mail:        off    10: Charging:    off    11: Shift Lock:  off
    12: Group 2:     off    13: Mouse Keys:  off
  auto repeat delay:  500    repeat rate:  20
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  50    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  no    allow exposures:  no
  timeout:  300    cycle:  300
Colors:
  default colormap:  0x20    BlackPixel:  0x0    WhitePixel:  0xffffff
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/Type1,built-ins
DPMS (Energy Star):
  Standby: 600    Suspend: 600    Off: 600
  DPMS is Enabled
  Monitor is On

---

### Post by &amp;KyT$0P# on 2022-08-26
> **mdiemer said:**
> I can't find XFCE4 power manager, don't think it's installed. 

Can you try installing it and configuring settings there?

If that doesn't help, or you specifically don't want Xfce power manager, there should be other [FONT=Courier New]xset[/FONT] commands to disable the "Screen Saver" and "DPMS" timeouts (which on your system are set to 5 minutes and 10 minutes, respectively).  But I haven't done this in a long time and don't remember how, sorry.  Refer to [FONT=Courier New]man xset[/FONT] for more info

Once you got working [FONT=Courier New]xset[/FONT] commands, you can make the effects persistent by setting up to run the commands at login: Xfce settings > Session and Startup > Application Autostart

---

### Post by mdiemer on 2022-08-26
> **halogen2 said:**
> Can you try installing it and configuring settings there?

If that doesn't help, or you specifically don't want Xfce power manager, there should be other [FONT=Courier New]xset[/FONT] commands to disable the "Screen Saver" and "DPMS" timeouts (which on your system are set to 5 minutes and 10 minutes, respectively).  But I haven't done this in a long time and don't remember how, sorry.  Refer to [FONT=Courier New]man xset[/FONT] for more info

Once you got working [FONT=Courier New]xset[/FONT] commands, you can make the effects persistent by setting up to run the commands at login: Xfce settings > Session and Startup > Application Autostart

Great, thanks, I'll give that a try.

---

