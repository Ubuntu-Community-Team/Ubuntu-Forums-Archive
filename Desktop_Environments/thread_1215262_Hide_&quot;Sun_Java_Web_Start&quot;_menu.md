---
title: "Hide &quot;Sun Java Web Start&quot; menu"
date: 2009-07-16
forum: Desktop Environments
---

### Post by igsen on 2009-07-16
How can i remove "Sun Java 6 web Start" menu under Applications>>Network on my desktop?
I have already do  search for *java*.desktop and put
```
NoDisplay=true
``` on every occurence of it.
I prefer hiding as removing java may have an effect on my already "system functional" desktop.
Any help is highly appreciated.

---

### Post by kerry_s on 2009-07-17
you only need to change the 1 in /usr/share/applictions
just add:
```
**OnlyShowIn=;**
```

and it will be hidden from the menu.

---

### Post by mcduck on 2009-07-17
> **igsen said:**
> How can i remove "Sun Java 6 web Start" menu under Applications>>Network on my desktop?
I have already do  search for *java*.desktop and put
on every occurence of it.
I prefer hiding as removing java may have an effect on my already "system functional" desktop.
Any help is higly appreciated.

Why not simply use the menu editor to hide it? Right-click on the Applications-menu and select "Edit Menus"..

---

### Post by igsen on 2009-07-17
> **kerry_s said:**
> you only need to change the 1 in /usr/share/applictions
just add:
```
**OnlyShowIn=;**
```and it will be hidden from the menu.

I followed this one and reboot.The said menu is still there.

---

### Post by igsen on 2009-07-17
> **mcduck said:**
> Why not simply use the menu editor to hide it? Right-click on the Applications-menu and select "Edit Menus"..

For some reason or another I can't seem to do this. There is no "Edit menus" showing on a right-click.
Am I missing something?

---

### Post by mcduck on 2009-07-17
> **igsen said:**
> For some reason or another I can't seem to do this. There is no "Edit menus" showing on a right-click.
Am I missing something?

Oh, sorry, my  mistake. I didn't notice you are using Xubuntu. Although I remember XFCE having some kind of menu editor as well..

edit: yep, I was right. "xfce4-menueditor". You should be able to start it by clicking the "Edit Desktop Menu"-button in the Menu-tab of the Desktop Settings-dialog.

---

### Post by kerry_s on 2009-07-17
> **mcduck said:**
> Oh, sorry, my  mistake. I didn't notice you are using Xubuntu. Although I remember XFCE having some kind of menu editor as well..

edit: yep, I was right. "xfce4-menueditor". You should be able to start it by clicking the "Edit Desktop Menu"-button in the Menu-tab of the Desktop Settings-dialog.

thats for the old xfce4, the current no longer has a working editor.

---

### Post by kerry_s on 2009-07-17
> **igsen said:**
> I followed this one and reboot.The said menu is still there.

try:
```
OnlyShowIn=N/A;
```

you shouldn't need to reboot, just log out & back in.

---

### Post by igsen on 2009-07-17
> **kerry_s said:**
> try:
```
OnlyShowIn=N/A;
```you shouldn't need to reboot, just log out & back in.
I'm still not able to achieve my goal. This is the content of my sun-java6-javaws.desktop

```
[Desktop Entry]
Encoding=UTF-8
Name=Sun Java 6 Web Start
Comment=Sun Java 6 Web Start
Exec=/usr/lib/jvm/java-6-sun-1.6.0.14/bin/javaws %u
Terminal=false
Type=Application
Icon=sun-java6
Categories=Application;Network;
MimeType=application/x-java-jnlp-file;
OnlyShowIn=N/A;
```I appreciate all the help.

---

### Post by kerry_s on 2009-07-17
bummer, don't know what to tell you. i removed several from my menu using that method.

---

### Post by igsen on 2009-08-15
Atlast! I finally got it hidden.
1. In terminal 
     ```
locate javaws
```2. ```
sudo mousepad /home/"somename"/.local/share/applications/sun-java6-javaws.desktop
```3. 

```
[Desktop Entry]
Categories=Application;Network;
Comment=Sun Java 6 Web Start
Encoding=UTF-8
Exec=/usr/lib/jvm/java-6-sun-1.6.0.10/bin/javaws %u
Icon=sun-java6
MimeType=application/x-java-jnlp-file;
Name=Sun Java 6 Web Start
[COLOR=Red]NoDisplay=true<<-----change from false to true[/COLOR]
Terminal=false
Type=Application
```):P

---

