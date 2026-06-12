---
title: "firefox and thunderbird in tray"
date: 2005-11-05
forum: Desktop Environments
---

### Post by Axios on 2005-11-05
Hello

I haven't been able to find a good thread with info on how to get firefox and thunderbird in the tray.

How is it possible to get an icon in the tray and have the programs running when i log in.

Thanks.

---

### Post by mustang on 2005-11-05
Have you tried dragging the firefox and thunderbird icons to your panel?

EDIT: oh, and to answer your second question. Go into System->Preference->Sessions and you should be able to add firefox and thunderbird there.

---

### Post by 23meg on 2005-11-05
You can also use alltray to put any app into your notification area.

[http://alltray.sourceforge.net/](http://alltray.sourceforge.net/)

---

### Post by Axios on 2005-11-05
What do you mean by dragging the icons?

I mean that firefox and thunderbird is in the tray beside the clock, just like gaim..

---

### Post by Axios on 2005-11-05
if i search for alltray with aptitude, i get no output..

---

### Post by 23meg on 2005-11-05
There's an ubuntu package on the alltray site I linked above which works fine.

---

### Post by Axios on 2005-11-05
Nice, it works.

Only problem now is that I can't "save current setup"

it says that firefox and thunderbird doesn't support this, is there a way to get that working also?

---

### Post by 23meg on 2005-11-05
I don't know what exactly you mean but if the documentation says it's unsupported there's little chance.

---

### Post by Axios on 2005-11-05
when i go to System > Log Out

I mark the "Save Current Setup" with firefox and thunderbird in the tray, then there comes an error when i try to log out, it says that the programs doesn't support this ( firefox, and thunderbird) and that i manually have to start them at next start up.

---

### Post by manicka on 2005-11-05
Go to System-->Preferences-->Sessions

Go to the Startup Programs Tab and add these two commands as session items

click on the add button for each one

```
alltray firefox

alltray thunderbird
```

---

### Post by fnando on 2005-11-05
I loved this app! ;)

One question: Isn't possible to add XMMS? XMMS has this option by itself?

Cheers!

---

### Post by Axios on 2005-11-06
I did something like that, I followed the alltray faq. It works !

thanks all!

---

### Post by 23meg on 2005-11-06
XMMS has a tray plugin I think, but if you're having problems with that (like I once had) you can use alltray instead.

---

### Post by LinuxWiz83 on 2005-11-20
[QUOTE=manicka]Go to System-->Preferences-->Sessions

Go to the Startup Programs Tab and add these two commands as session items

click on the add button for each one

```
alltray firefox

alltray thunderbird
```[/QUOTE]

Just one correction on your instructions that is thunderbird you need to add it as > alltray mozilla-thunderbird

---

### Post by manicka on 2005-11-20
[QUOTE=LinuxWiz83]Just one correction on your instructions that is thunderbird you need to add it as[/QUOTE]

Thanks, I'm not a thunderbird user and was taking an educated guess at the command.

---

### Post by LinuxWiz83 on 2005-11-20
Your welcome and you were close :smile:.

---

