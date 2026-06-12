---
title: "Menubar has disappeared from all apps"
date: 2013-11-17
forum: Desktop Environments
---

### Post by tomasvanverrewegen on 2013-11-17
I just got a new laptop, installed kubuntu 13.10, all went well... for a few days.
I played with the setting: "System Settings/Application Appearance/Style/Finetuning/Menubar style" and now the menubar has disappeared from all my applications. 
Rebooting or changing the setting again doesn't help. 

In the screenshot you can see some apps without menu bar, also no menubar at the top of the screen.

Any ideas?

---

### Post by PaulW2U on 2013-11-17
Two questions for you:

[LIST=1]
[*]What setting is shown against Menubar style? Mine says "In application".
[*]Have you tried resetting that screen to the default settings with the "Default" button?
[/LIST]

---

### Post by tomasvanverrewegen on 2013-11-18
1. Right now it says: In application, but it doesn't really matter, changing the settings doesn't seem to do work. I do get a notification saying : "Setting changes will take effect on appication restart" but that's all.
2. same thing as 1: no go

Does anyone know what component is responsible for the menubar? Plasma/KWIn...

---

### Post by PaulW2U on 2013-11-18
Does [https://forum.kde.org/viewtopic.php?f=66&t=109594](https://forum.kde.org/viewtopic.php?f=66&t=109594) help?

I'm seeing certain similarities between what you're seeing and what is being reported in the KDE Forums post.

I know this doesn't help but I love KDE and Kubuntu but whenever I install Kubuntu I tend to leave it installed with most of its default settings intact. :rolleyes:

---

### Post by tomasvanverrewegen on 2013-11-18
It certainly looks the same, I was already goinig in that direction myself, since I had seen "MenuBar=Disabled" in some config files...
But, the solution given doesn't work for me:
1. I change the setting in system settins to "In application"
2. vim.tiny ~/.kde/share/config/katerc 
3. Change the line "MenuBar=Disabled" to "MenuBar=Enabled" (or just delete the line)
4. start kate -> still no menubar

I did try creating a new user account -> here everything works just fine

It's a shame, I really liked the Menubar on top of the screen....

---

### Post by public3 on 2013-11-19
what about if you move that file entirely and allow kate to create a new config file.
$ mv [COLOR=#000000]~/.kde/share/config/katerc [/COLOR][COLOR=#000000]~/.kde/share/config/katerc.old

Also, i haven't used this, but isn't the menubar systemwide, and not specific to KATE?[/COLOR]

---

### Post by tomasvanverrewegen on 2013-11-20
Changing config files (or moving them doesn't help).

The menubar is system-wide, that's why this is so annoying: none of my applications have a menubar anymore. Kate is just an example...

---

