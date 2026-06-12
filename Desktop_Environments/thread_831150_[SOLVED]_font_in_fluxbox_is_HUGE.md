---
title: "[SOLVED] font in fluxbox is HUGE"
date: 2008-06-16
forum: Desktop Environments
---

### Post by LinuX-M@n1@k on 2008-06-16
How do I fix it? Look at the screen shots.

Old:
[ATTACH]74249[/ATTACH]

Current:
[ATTACH]74248[/ATTACH]

---

### Post by Happy_Man on 2008-06-16
Run ```
gnome-appearance-properties
``` and check to make sure that the font settings there are the right ones. 

For the slit, I'm not sure, but ~/.fluxbox/init may have a setting for fonts. And also, while you're in the Appearance Properties, make sure the DPI is set to 96.

---

### Post by LinuX-M@n1@k on 2008-06-17
Still the same.

The font settings are the right ones - Sans 10; I changed them to Sans 8, but it didn't worked.

Also, The DPI is set to 96:
```
$ xrdb -query | grep dpi
Xft.dpi:	96
$ 
```

And I can't find anything about fonts in .fluxbox/init (I'm not using slit).

Any other suggestions ? Thanks!

---

### Post by LinuX-M@n1@k on 2008-06-17
bump

---

### Post by LinuX-M@n1@k on 2008-06-17
buuump

---

### Post by LinuX-M@n1@k on 2008-06-17
bump

---

### Post by LinuX-M@n1@k on 2008-06-17
bump... LoLz RoFlcOpt3r! ;\ ??

&#1040;&#1077; &#1084;&#1072;&#1084;&#1072; &#1074;&#1080; &#1089;&#1090;&#1072;&#1088;&#1072; &#1090;&#1088;&#1072;&#1074;&#1077;&#1089;&#1090;&#1080;&#1090;&#1080; &#1075;&#1088;&#1086;&#1079;&#1085;&#1080; :). &#1065;&#1077; &#1074;&#1080; &#1082;&#1086;&#1085;&#1089;&#1090;&#1088;&#1091;&#1080;&#1088;&#1072;&#1084; &#1089;&#1077;&#1088;&#1075;&#1080;&#1080; &#1074; &#1079;&#1072;&#1076;&#1085;&#1080;&#1094;&#1080;&#1090;&#1077; :lol: RofL (?)

---

### Post by kerry_s on 2008-06-17
can you be more specific about what you want to fix?

the toolbar will fonts will be part of your fluxbox theme:
[http://fluxbox-wiki.org/index.php/Howto_change_font](http://fluxbox-wiki.org/index.php/Howto_change_font)

---

### Post by LinuX-M@n1@k on 2008-06-17
Okay, I want to change the fonts of the fluxbox menu, fluxbox toolbar, conky, skype and gnome-terminal...

In every application the font is bigger (in fluxbox). I think it has to do something with the DPI. I haven't tried to reinstall the nvidia drivers or fluxbox, but I tried to rename the folder .fluxbox to .fluxbox.old. And the font is still huge.

Other ideas?

---

### Post by RedSquirrel on 2008-06-17
I see what you mean. All of your fonts are much larger in the new screenshot. Strange.

Do you recall changing anything? Is this the same system?

Is there any chance the DPI was lower than 96 in the old screenshot (86 maybe...)?

Are you using GNOME settings to handle the fonts when you run Fluxbox, or do you set DPI in ~/.Xdefaults or ~/.Xresources? If you don't use GNOME for the fonts, I would think you would end up with a DPI of 86 until you change it manually.

---

### Post by LinuX-M@n1@k on 2008-06-18
- The system is the same.

- I have installed kubuntu-kde4-desktop and kubuntu-desktop, but I removed them. After that, my fonts became larger.

- I dont have ~/.Xdefaults and ~/.Xresources.

- I'm not using the GNOME settings.

---

### Post by kerry_s on 2008-06-18
okay then then try using a xdefaults file.
in term:
**echo "Xft.dpi: 96" > ~/.Xdefaults**

you'll need to add this to your fluxbox startup:
**xrdb -merge ~/.Xdefaults &**

---

### Post by LinuX-M@n1@k on 2008-06-18
Yay!
I've just upgraded the kernel to 2.6.24-19-generic. Everything is fixed now.

Thanks everyone for the help!

---

### Post by MedellinManDem on 2009-02-05
I used the font settings on the Flux-wiki to change my menu/toolbar fonts, then used:

```
gnome-appearance-properties
``` 

to change the font in firefox, which was still using that ugly generic ubuntu font. 

Can anyone explain why editing my style overlay file as explained [here](http://fluxbox-wiki.org/index.php?title=Style_overlay) wasn't enough to alter the settings for Firefox, and why I had to use the Gnome Appearance command?

---

### Post by MedellinManDem on 2009-02-05
And then when I restart, the gnome appearance properties doesn't restart with it. Also, now when I logout of fluxbox using "exit" on the menu, it just goes to a black screen i.e. the splash screen doesn't show up, even though I can hear the little ubuntu drum thing indicating that it should be there.

can anyone help me?

:rolleyes:

---

### Post by MedellinManDem on 2009-02-05
Anyone?

---

### Post by MedellinManDem on 2009-02-08
hello???????????

---

### Post by RedSquirrel on 2009-02-08
> **MedellinManDem said:**
> I used the font settings on the Flux-wiki to change my menu/toolbar fonts, then used:

```
gnome-appearance-properties
```to change the font in firefox, which was still using that ugly generic ubuntu font. 

Can anyone explain why editing my style overlay file as explained [here]("http://fluxbox-wiki.org/index.php?title=Style_overlay") wasn't enough to alter the settings for Firefox, and why I had to use the Gnome Appearance command?

  The font settings specified in the ~/.fluxbox/overlay file only affect the Fluxbox window manager (that is, the Fluxbox menu, toolbar, and window titlebar). Application fonts are set elsewhere. 

As for your other issue, I'm not currently using Ubuntu, so I'm not sure if I can be of much help. I would try restarting gdm (the service that gives you the fancy login screen) to see if that helps at all.  Press Ctrl-Alt-F2 to go to a virtual console. Login there. Then run:  ```
sudo /etc/init.d/gdm restart
```If that didn't help, I would reboot the machine: ```
sudo shutdown -r now
```If that didn't help, I would advise you to start a new thread so that people using Ubuntu can help you sort out the issue. 

(This thread was marked [SOLVED] by the OP. Many forum participants would skip reading this thread since they would think the issue was resolved. ;))

---

