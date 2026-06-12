---
title: "keyboard layout switcher missing"
date: 2011-09-11
forum: Desktop Environments
---

### Post by liatodua on 2011-09-11
I just installed Xubuntu 11.04 on IBM thinkpad T30.

I regularly need to use two different keyboard layouts. I easily added a new layout through Settings>Keyboard>Layout. 

But can find no way to have: 
1) Some easy way for switching between the layouts (ex. shortcut keys)
2) Desktop indicator of the active layout

Any suggestions?

---

### Post by Krytarik on 2011-09-11
How is this!?:

[http://ubuntuforums.org/showthread.php?p=11133449#post11133449](http://ubuntuforums.org/showthread.php?p=11133449#post11133449)

 At least for the panel item switch method, as the keyboard shortcut is apparently lost after reboot.

Greetings.

---

### Post by liatodua on 2011-09-11
Thanks a lot! it works. And shortcuts can aso be added through the same switcher (just right-click and select properties)

---

### Post by liatodua on 2011-09-14
Ooops! the shortcut for layout switching is lost after computer reboot. Tried again. with shutdown it dissappears :(

---

### Post by Krytarik on 2011-09-14
> **liatodua said:**
> Ooops! the shortcut for layout switching is lost after computer reboot. Tried again. with shutdown it dissappears :(
Yep, as prospected. ;-)

---

### Post by detronator on 2011-10-09
Here are two possible ways of switching between keyboard layouts in **xubuntu **(and they work after reboot as well):

[COLOR=DimGray]=== *First method is to assign a shortcut (in my case ALT+SHIFT) that will switch between your preferred layouts (in my case english, french and bulgarian phonetic)*[/COLOR]

1) Go to Start Menu > Settings > Settings manager > Session and Startup > Application Autostart (tab)
2) Click on the add button
3) Type anything you want for name and description (for exam: KBD_LAYOUT_SWITCHING)
4) In the Command field, you have to insert this:
setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,fr,bg"(phonetic)"

[COLOR=DarkGreen]--Note: This command is an example and sets the shortcut combination ALT+SHIFT to switch between english, french and bulgarian phonetic layouts, but feel free to use anything you want.

[COLOR=Black]5) Click OK[/COLOR][/COLOR] and that's it, but if you also need an icon in the tray read below[COLOR=DimGray]*: *[I]Extra touch to both methods

[/I][/COLOR][COLOR=DimGray]=== *Second method is to assign a global shortcut for each layout*[/COLOR]

1) Go to Start Menu > Settings > Settings manager > Keyboard > Application Shortcuts (tab)
2) Click on the add button
3) Insert the following command: "setxkbmap us" (without the quotes) and click OK.
4) A new dialog window will pop-up waiting for you to type the shortcut combination (for example: ALT+1)
5) You can add another shortcut (for example ALT+2) for switching to a different layout, assigning command: "setxkbmap de" for german or "setxkbmap fr" for french etc..
6) That's it, but if you also need an icon in the tray read below[COLOR=DimGray]*: *[I]Extra touch to both methods

[/I][/COLOR][COLOR=DimGray][COLOR=Red]*****[/COLOR]* Extra touch to both methods:*[/COLOR]
Since both methods just add the functionality to switch between layouts and they don't show an icon in the tray, indicating the current language, here is a good way to do this:

1) Open terminal and type: sudo apt-get install xfce4-xkb-plugin
[COLOR=DarkGreen]Note: In theory this is the perfect solution for layout switching, but it has this weird problem of not remembering the shortcut combination for kbd layout switching after reboot, therefore we need to use both previous methods as well.. I hope this will change in future. We will use this plug-in only to indicate in tray which layout is currently used.[/COLOR]
2) Right click any panel and choose Panel > Add new items
3) Search for **Keyboard Layouts** (this is our new xfce plugin) and add it to the panel
4) By right-clicking on the plugin icon and choosing **properties** you can set different cool things like using text instead of a flag icon and Manage layout:globally. Most important is to add your preferred kbd layouts(if needed).
5) That's it, now you have an indication of the current layout in your panel.

[COLOR=DarkGreen][COLOR=DimGray]==========[/COLOR]
Note: Both ways continue to work after reboot. [/COLOR]

---

