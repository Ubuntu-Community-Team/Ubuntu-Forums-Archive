---
title: "Minecraft Panel Launcher?"
date: 2011-03-20
forum: Gaming &amp; Leisure
---

### Post by jfed on 2011-03-20
I love me some minecraft. I play it on Ubuntu, (10.10) but what I'd love to do is have it launch from the panel, you know, the little panel launcher things you can have to launch a program just by clicking? I'm sick and tired of navigating to the minecraft folder, right clicking, and selecting run with java runtime.

So I made a panel launcher with a nice little creeper face and everything. Only problem is, it won't actually load minecraft when i click on it. I think it's probably because it's a .jar and not an actual application... anyway, do you think there is a way i could get the panel launcher to work? or am i just going to have to suck it up and navigate to it every time i wanna play?

P.S. I'm selecting the launcher jar file to run, not the actual minecraft jar file from the bin folder, do you think running that instead would work?

---

### Post by Perfect Storm on 2011-03-20
Do as launcher:
```
sh -c "cd <path> && <java execution command>"
```

---

### Post by jfed on 2011-03-20
Thank you! I didn't think to use the terminal, I will try this.

---

### Post by shmup on 2011-03-20
Why not just launch from the jar? Maybe you know something I don't.

You should be able to just create a launcher, and add:

```
java -Xmx1024M -Xms512M -cp ~/minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

But naturally point to wherever your .jar is.

---

### Post by Veikk0 on 2011-03-21
> **shmup said:**
> You should be able to just create a launcher, and add:

```
java -Xmx1024M -Xms512M -cp ~/minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

But naturally point to wherever your .jar is.

For some reason that alone doesn't work for me, I have to add "-jar" after the "-cp" switch:

```
java -Xmx1024M -Xms512M -cp -jar ~/minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

After that it works perfectly! :p

---

### Post by markb69 on 2013-01-19
If you want to get fancy you can add a desktop file and it display a Minecraft icon which you can add to either Unity launcher or Gnome Shell. Save the Minecraft image here to a folder such as Pictures and adjust the icon path as needed. I like to use magiclauncher since it is easy to add mods. Then open a text editor and create a desktop file using the below code and save it as Minecraft.desktop

```
[Desktop Entry]
Type=Application
Exec=java -jar  /home/mark/minecraft/MagicLauncher_1.0.0.jar
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=false
Name=Minecraft
Comment=Minecraft Launcher
Name[en]=Minecraft
Icon=/home/mark/Pictures/minecraft.png
Comment[en]=Minecraft

```

[IMG]http://markbokil.com/images/minecraft.png[/IMG]

Copy the Minecraft.desktop file to /usr/share/applications to make it accesible to your launcher.

Instead of using magiclauncher use the already suggested command:
```
java -Xmx1024M -Xms512M -cp -jar ~/minecraft/Minecraft.jar net.minecraft.LauncherFrame
```

Add your application to the launcher as you normally would. In Gnome shell it will appear under Applications -> Others in the Overview. In Unity select all applications and it will appear as an icon. Now get back to mining more diamonds!

---

