---
title: "desktop brightness changed by random keystrokes"
date: 2010-06-30
forum: Desktop Environments
---

### Post by kingbirdy on 2010-06-30
whenever I type certain things (backspace when nothing left to delete, tab to autocomplete in terminal, etc.) the screen will randomly go dim and then go back after a few seconds. it also happens when I try to use the rain or write with fire options.(though this might be normal)

---

### Post by kingbirdy on 2010-07-01
it seems to especially happen in terminal. if I press any kind of keystroke that it deems invalid (backspace to much, type when shouldn't, etc.) it dims for about 5 seconds.

---

### Post by yorkshire bloke on 2010-07-01
I was having screen brightness issues on an Asus netbook running Ubuntu netbook remix. Solved by doing this:

Brightness control doesn't work properly. Pressing Fn-F5 or Fn-F6  changes the brightness randomly. 
[LIST]
[*]To get best support for hotkeys, update your BIOS to  the latest version then add some kernel parameters to the grub config.  Run sudo gedit /etc/default/grub 
[*]Edit the line with  GRUB_CMDLINE_LINUX_DEFAULT and add " acpi_osi=Linux acpi_backlight=vendor".  The line should then look like -> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"  
[*]Save and then run sudo update-grub 
[*]Reboot 
[*]xbacklight, and xgamma work  too..
[/LIST]
I have NO idea if this is relevant to your query, but it might give you a jumping in / off point!

---

### Post by yorkshire bloke on 2010-07-01
By the way, I found all that [here]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Ubuntu%2010.4%20Lucid%20Netbook%20Edition").

---

### Post by mcduck on 2010-07-01
Do you have desktop effects enabled? If you do, the open CompizConfig Settings Manager (install it if you haven't already done that), go to "Fading Windows"-plugin's settings and turn off "Visual Bell" and "Fullscreen Visual Bell". 

You might also want to disable the bell in your terminal itself, for Gnome Terminal this setting is in profile preferences, under General tab (just disable the "Terminal Bell" option.

(the beeper would usually give you a sound warning if you try to do something that can't be done, and this happens very often in a terminal. As the beeper sound is quite annoying it's often replaces by using a visual bell, meaning some kind of visual effect to give you the same warning without the beeper sound. Personally I prefer turning both the bell sound and visual bell off...)

---

### Post by kingbirdy on 2010-07-02
> **mcduck said:**
> Do you have desktop effects enabled? If you do, the open CompizConfig Settings Manager (install it if you haven't already done that), go to "Fading Windows"-plugin's settings and turn off "Visual Bell" and "Fullscreen Visual Bell". 

You might also want to disable the bell in your terminal itself, for Gnome Terminal this setting is in profile preferences, under General tab (just disable the "Terminal Bell" option.

(the beeper would usually give you a sound warning if you try to do something that can't be done, and this happens very often in a terminal. As the beeper sound is quite annoying it's often replaces by using a visual bell, meaning some kind of visual effect to give you the same warning without the beeper sound. Personally I prefer turning both the bell sound and visual bell off...)
while this seems like it should work, they were already disabled. I tried messing with the settings there, but to no avail. however, i couldn't find the Terminal settings. where would I go for these?

yorkshire: well, I'm not on a netbook, and I just got in to this tree  days ago, so I'm not really comfortable editing my BIOS.

EDIT: the fire thing works now. It turns out that last time I changed the brightness settings for it, they just hadn't stuck. Rain still doesn't though.

---

### Post by mcduck on 2010-07-02
For the terminal options just open a terminal and select Edit->Profile Preferences (or right-click in the terminal and Profiles->Profile Preferences if you have the menu bar hidden).

..Although if you really don't have visual bell enabled anywhere then you shouldn't be getting the visual bell effect but just the normal PC beeper sound instead. You should probably check all the Compiz plugins you have enabled to see if some other plugin than the "Fading Windows" has the visual bell feature.

---

### Post by kingbirdy on 2010-07-02
> **mcduck said:**
> For the terminal options just open a terminal and select Edit->Profile Preferences (or right-click in the terminal and Profiles->Profile Preferences if you have the menu bar hidden).

..Although if you really don't have visual bell enabled anywhere then you shouldn't be getting the visual bell effect but just the normal PC beeper sound instead. You should probably check all the Compiz plugins you have enabled to see if some other plugin than the "Fading Windows" has the visual bell feature.
I changed it in Terminal, and it's fixed! Thank you!

---

