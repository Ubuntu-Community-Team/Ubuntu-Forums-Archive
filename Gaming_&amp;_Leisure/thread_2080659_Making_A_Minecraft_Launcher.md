---
title: "Making A Minecraft Launcher"
date: 2012-11-04
forum: Gaming &amp; Leisure
---

### Post by Trusted Developer on 2012-11-04
Hello,
I've been using Ubuntu for a couple of years now and decided that I'd make my first guide. This guide will tell you how to make your own Minecraft launcher and add it to Unity! :D
*(Guide made using Ubuntu 12.10)*

**Perquisites**
Before starting make sure you have...
[LIST=1]
[*]Java
[*]Minecraft.jar File
[/LIST]
If not you can download Java at [www.java.com]("http://www.java.com") and Minecraft at [minecraft.net]("http://www.minecraft.net") respectively.
I'd also recommend storing both your minecraft.jar file and the icon in a folder that isn't going to be moved or tampered with.

**Create A Unity Launcher**
1. Open Terminal and input this line.
```
nautilus ~/.local/share/applications
```
2. Now, create a Unity launcher file.
```
gedit ~/.local/share/applications/Minecraft.desktop

```
3. Copy and paste this into the text file.
```

[Desktop Entry]
Type=Application
Name=Minecraft
Comment=Minecraft game launcher.
Icon=**/location/of/an/icon4minecraft.png**
Exec=**/the/java/file/you/downloaded/from/mc.jar**
Terminal=true
Categories=Games;
```
4. Save and right click the launcher file you just made and click...
Properties -> Permissions -> Allow Execution
5. Finally, drag and drop the document to Unity!

**Create A Desktop Launcher**
Good if you're trying to avoid the Terminal. ;)

1. Right click the desktop and select Create New Document -> Empty Document
2. Name the file. Open it in GEdit and copy and paste the following.
```
#!/bin/bash
cd **/folder/where/minecraft/is**
./minecraft.jar
```
Save it and and right click the launcher file you just made and click...
Properties -> Permissions -> Allow Execution
You can also choose an icon by clicking the box with text file image under the "Basic" field.

---

### Post by dayspring1978 on 2012-11-06
Thanks for writing this tutorial. I am having an issue unfortunately. I am using Mint 13 and I can't get the created document to launch Minecraft. I followed this tutorial to make a launcher for Tekkit and it works perfectly. I'm lost. :( Any help is greatly appreciated.

---

### Post by Trusted Developer on 2012-11-18
Hey Dayspring, I didn't see your reply immediately, sorry about that. Are you talking about the desktop version of the launcher or the Unity launcher version? I'm not sure if this would work on Mint because it uses the Cinnamon desktop environment. Can you please tell me which environment you're using? Additionally, I found this link that might help you. Hope it helps! [Link: Adding or Removing Icons from Gnome and Cinnamon]("https://ask.fedoraproject.org/question/1021/adding-or-removing-icons-from-the-application")

---

