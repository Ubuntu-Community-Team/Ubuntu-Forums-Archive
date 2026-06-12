---
title: "Helping creating launchers on AWN Navigator"
date: 2007-11-29
forum: Desktop Effects &amp; Customization
---

### Post by nandorj78 on 2007-11-29
Hi
Im very new to Ubuntu and I have no idea on how to create launchers.

What exectly to put in the fields:

Name:
Command:
Comment:

In the command field I have the browse option, but I can seem to find the file I want the launcher to open. What am I doing wrong?

Let's supose I want to create a launcher to rhythmbox and GIMP, how do I do it?

---

### Post by lian1238 on 2007-11-29
For rhythmbox, put
```
rhythmbox
```
into the command field. (the icon should change to rhythmbox)
For gimp, same thing. ;)

AWN's launcher works like any other launcher (e.g on the desktop). If you want to know the command of a program, drag the launcher onto the desktop. Rightclick->properties, then go to the "launcher" tab. You'll find the command there.

---

### Post by nandorj78 on 2007-11-29
Oh nice, thanks!

Just one more question, how do I set up AWN to start automatically when I log in?

---

### Post by daengbo on 2007-11-29
You can also just drag the launcher from the menu to the launchers tab or to the dock itself.

---

### Post by nandorj78 on 2007-11-29
ok thanks, what about starting awn on startup?

---

### Post by lian1238 on 2007-11-29
Go to System->Preferences->Sessions
Under Startup Programs tab, click Add.
The command is
```

avant-window-navigator

```

---

### Post by nandorj78 on 2007-11-29
now, that's weird...

I put all the launchers I wanted in the dock, then when I restarted the computer the launchers disappeared. Is there a fix for this?

thanks!

---

### Post by nandorj78 on 2007-11-29
Ok, it's getting even weirder now! 

I simply can't re-add the launchers anymore.

help!

---

### Post by nandorj78 on 2007-11-29
This is simply getting in my nerves! I've uninstalled awn, re-installed again, and it still doesn work. I CAN'T ADD launchers to it, not even dragging them, they simply don't appear.

Does anyone know what's going on?

---

### Post by lian1238 on 2007-11-30
How did you uninstall/install? Are you using the bzr or the stable version?

---

### Post by nandorj78 on 2007-11-30
I removed it using the synaptic manager and then installed agaig. I have no idea which version I'm running. Where can I download the stable version?

---

### Post by spiff95 on 2007-12-03
> **nandorj78 said:**
> I removed it using the synaptic manager and then installed agaig. I have no idea which version I'm running. Where can I download the stable version?

I don't know enough about it, but I just stumbled on this thread: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)
It may contain the answer you're looking for. Good Luck! :)

---

### Post by CJ56 on 2007-12-03
If it's any help - I keep a panel at the top of the desktop (System, Places, Clock etc.). For any application I want to add to the AWN launcher, I first add the application icon to the panel using right click on the menu; then drag the icon onto the dock; then remove the first icon from the panel. 

This seems to work; I too had problems with launchers showing on the dock then disappearing next time I started the dock up. So far it's been pretty steady...

---

