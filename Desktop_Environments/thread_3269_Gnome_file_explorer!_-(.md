---
title: "Gnome file explorer! :-("
date: 2004-11-04
forum: Desktop Environments
---

### Post by senectus on 2004-11-04
Is there any way to change the horrid file manager system that Gnome uses?

Productivity for me is dropped down to a tenth of what it would normally be when I'm forced to use this abysmal interface.

I like Gnomes clean crisp feel, but I really need a KDE style explorer to be productive.
Can anyone recommend a hack or maybe another application all together?

---

### Post by fjleal on 2004-11-04
I think you're referring to the spacial mode. Try typing in a terminal:

```
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
```

---

### Post by az on 2004-11-04
Applications - System tools - configuration editor - nautilus - preferences - always use browser.
Click click true and you are off!

Basically, no need for console in Ubuntu!

---

### Post by Verlager on 2004-11-04
[QUOTE=azz]Applications - System tools - configuration editor - nautilus - preferences - always use browser.[/QUOTE]Applications - System tools - configuration editor - **apps** - nautilus - preferences - always use browser.

_- always use browser_. ?[SIZE=3]** I don't see this... Instead I see **[/SIZE]
[COLOR=DarkRed]
[B]preferences_version = 2
sound_state = 0[/B][/COLOR]  

I am on a fresh ubuntu install, btw.

---

### Post by jts on 2004-11-04
Verlager, I was curious about this too.  Expand the nautilus folder, and click on the "Preferences" folder.    You should get a list of options on the right.  The first option in the list is "always_use_browser".

---

### Post by Verlager on 2004-11-05
[QUOTE=jts]Verlager, I was curious about this too.  Expand the nautilus folder, and click on the "Preferences" folder.    You should get a list of options on the right.  The first option in the list is "always_use_browser".[/QUOTE]Right you are! Thanks!

---

### Post by senectus on 2004-11-07
[QUOTE=fjleal]I think you're referring to the spacial mode. Try typing in a terminal:

```
gconftool-2 --type bool --set /apps/nautilus/preferences/always_use_browser true
```[/QUOTE]

thank you VERY much... that was very helpfull :-)

---

### Post by fjleal on 2004-11-07
Glad it helped! ;)

Actually, azz and jts are right: that option is now accessible in the Nautilus preferences screen in Gnome 2.8, so there's no need to use the shell. I hadn't realized that when I first posted, been using Ubuntu for a short time...

---

### Post by nuopus on 2004-11-07
[QUOTE=Verlager]Applications - System tools - configuration editor - **apps** - nautilus - preferences - always use browser.
 
 _- always use browser_. ?[size=3]** I don't see this... Instead I see **[/size]
 [color=DarkRed]
 [b]preferences_version = 2
 sound_state = 0[/b][/color]  
 
 I am on a fresh ubuntu install, btw.[/QUOTE]  A more direct way to do it that WILL work. Launch Applications --> System Tools --> Configuration Editor.
 
 Then go to apps --> nautilus --> preferences and check "always_use_browser"
 
 EDIT: Should have read the rest of messages where this problem was ALREADY solved! LOL sorry for the post.

---

### Post by Slapdash on 2004-11-08
Also try maybe right clicking on the folder you want to access ( or drive ) and say browse. it looks and works like Windows then.

---

### Post by slux on 2004-11-08
You might still want to give the spatial nautilus a chance, you might like it after getting used to. You've probably more familiar with a navigator-style system but the spatial model does have potential advantages.

See [this Ars Technica article](http://arstechnica.com/articles/paedia/finder.ars)  for details about the idea behind it.

---

### Post by andy_sp1ke on 2004-11-08
windows ..... hiss ...... :p

---

### Post by jeffjj on 2004-12-11
>>Also try maybe right clicking on the folder you want to access ( or drive ) and say browse. it looks and works like Windows then.

Sweet, I didn't know I could do that. I really like spatial browsing, except when I have to dig deep into the file structure and am not sure what I am looking for.

---

### Post by poptones on 2004-12-11
[QUOTE=jeffjj]>>Sweet, I didn't know I could do that. I really like spatial browsing, except when I have to dig deep into the file structure and am not sure what I am looking for.[/QUOTE]

Pssssst....

Open a command prompt and type "locate *whatever*" Then just do ctrl-l in any nautilus window and type the path. Or type "nautilus *path*&" right there in the terminal.

---

### Post by Freakwitch on 2004-12-11
gads, I agree that default setting is horrid. For a moment, I thought I was in Windows 3.11...

:-D

---

