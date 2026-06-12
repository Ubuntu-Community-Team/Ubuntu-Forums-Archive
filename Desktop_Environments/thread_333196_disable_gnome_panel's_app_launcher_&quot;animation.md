---
title: "disable gnome panel's app launcher &quot;animations&quot;"
date: 2007-01-07
forum: Desktop Environments
---

### Post by vicarious on 2007-01-07
Whenever I launch an application from gnome panel it flashes some yellow lines on the screen expanding with the border of the application (I'm guessing) in some attempt at animation. It does not matter what window manager I am using. Is there any way to disable this? I took a peek in gconf-editor and disabled "enable_animations" but that didn't have any effect.

It's driving me nuts. I'd appreciate it if anyone can help, sorry it's hard to explain but I'm sure you know what I am talking about.

---

### Post by mcduck on 2007-01-07
This is the global animations key for gnome, it should do the trick:
'desktop/gnome/interface/enable_animations'

If that doesn't work for you try these too:
'apps/panel/global/enable_animations'
'apps/metacity/general/reduced_resources'

Reduced resources for Metacity also turns hides window contents when moving. But turning on accessibility fixes that:
'desktop/gnome/interface/accessibility'

---

### Post by vicarious on 2007-01-07
> **mcduck said:**
> 'apps/panel/global/enable_animations'

That was it, thank you.

---

### Post by geoffDeGeoffGeoff on 2007-01-16
thanks for that, it was embarassing showing non ubuntu people stuff on my computer with that lame animation flash

---

### Post by emsiv82 on 2007-02-18
I didn't understand how to do this.... :confused: Thanks!

---

### Post by kanha on 2007-02-18
> **emsiv82 said:**
> I didn't understand how to do this.... :confused: Thanks!

open configuration editor from accessories then follow the above discription. :guitar:

---

### Post by mcduck on 2007-02-18
> **emsiv82 said:**
> I didn't understand how to do this.... :confused: Thanks!

press Alt-F2 and run 'gconf-editor' if you can't find Configuration Editor from your Applications-menu.

---

### Post by emsiv82 on 2007-02-18
Ok, It did the trick :) THANKS!!

---

### Post by bandoba on 2007-07-21
I tried all above settings and it still doesn't work. I have also noticed that when I run gconf-editor I get following error:

$ sudo gconf-editor

(gconf-editor:18262): GnomeUI-WARNING **: While connecting to session manager:
Could not open network socket.

I did try to restart GDM by stopping and starting it as well as Ctrl+Alt+Bkspace. But in any case I still see animations when I minimize any window. Does anybody know what can be wrong here?

---

### Post by crjackson on 2007-07-22
> **mcduck said:**
> This is the global animations key for gnome, it should do the trick:
'desktop/gnome/interface/enable_animations'

If that doesn't work for you try these too:
'apps/panel/global/enable_animations'
'apps/metacity/general/reduced_resources'

Reduced resources for Metacity also turns hides window contents when moving. But turning on accessibility fixes that:
'desktop/gnome/interface/accessibility'

**[SIZE="2"]This is awesome, thanks.  Do you know were I can find the settings that control the window delay times?  Like when in the applications menu, and rolling the mouse over a category, the delay time setting before the sub-category opens the next menu?  Thanks again...[/SIZE]**

---

### Post by mcduck on 2007-07-23
> **bandoba said:**
> I tried all above settings and it still doesn't work. I have also noticed that when I run gconf-editor I get following error:

$ sudo gconf-editor

(gconf-editor:18262): GnomeUI-WARNING **: While connecting to session manager:
Could not open network socket.

I did try to restart GDM by stopping and starting it as well as Ctrl+Alt+Bkspace. But in any case I still see animations when I minimize any window. Does anybody know what can be wrong here?

Do not start the Configuration Editor with 'sudo'. That would start it as root, changing settings for root and not for your own user.

Just run 'gconf-editor' without the 'sudo'.

---

### Post by mcduck on 2007-07-23
> **crjackson said:**
> **[SIZE="2"]This is awesome, thanks.  Do you know were I can find the settings that control the window delay times?  Like when in the applications menu, and rolling the mouse over a category, the delay time setting before the sub-category opens the next menu?  Thanks again...[/SIZE]**
That delay comes from the time it takes for your computer to load contents and icons of the menu. There is no hardcoded delay anywhere.

---

### Post by bandoba on 2007-07-23
> **mcduck said:**
> Do not start the Configuration Editor with 'sudo'. That would start it as root, changing settings for root and not for your own user.

Just run 'gconf-editor' without the 'sudo'.

I tried that as well but no luck. In fact I do see correct settings when I run gconf-editor now (i.e. animations are disabled and reduced resources is enabled) but my desktop still shows rectangles when I minimize any window.

---

### Post by phinn on 2008-04-30
Wow nice. I too was looking to disable that stupid dotted line for a while. I just did these two and it worked:

'apps/metacity/general/reduced_resources'  (unchecked)
'desktop/gnome/interface/accessibility'  (checked)


Thanks  :)

---

