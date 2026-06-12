---
title: "Minecraft for Linux?"
date: 2013-07-15
forum: Gaming &amp; Leisure
---

### Post by BghMc on 2013-07-15
Hey guys! I'm new to the forums and I was wondering; Is there Minecraft for Ubuntu and how do I get it.

P.S:
I don't know where to post this but; Do you know if the Logitech G500s would work on Ubuntu (Just the normal functions not the programmable keys) and also the Razer DeathAdder 2013.

---

### Post by Horbo on 2013-07-15
> **BghMc said:**
> Hey guys! I'm new to the forums and I was wondering; Is there Minecraft for Ubuntu and how do I get it.

P.S:
I don't know where to post this but; Do you know if the Logitech G500s would work on Ubuntu (Just the normal functions not the programmable keys) and also the Razer DeathAdder 2013.

[https://help.ubuntu.com/community/InstallMinecraft147](https://help.ubuntu.com/community/InstallMinecraft147)

---

### Post by DarkAmbient on 2013-07-15
check out the link in my sig.

---

### Post by soloman469 on 2013-07-15
Here are some pretty easy steps for you if none of those work.
[I]
1.Goto [/I]_Minecraft.net_
2.[I]Click the _download it here_ button on the website.
3.Download the Minecraft.jar file to your Downloads folder.
4.Open a terminal.
5.Enter the following commands in order:[/I][COLOR=#000000]
5.a. [/COLOR][COLOR=#000000]cd ~/Downloads
5.b. [/COLOR][COLOR=#000000]sudo chmod a+x minecraft.jar
5.c  [/COLOR][COLOR=#000000]java -Xmx256M -Xms256M -cp minecraft.jar net.minecraft.LauncherFrame

You're all set!

(P.S. You may be prompted to enter your password, so be prepared...)[/COLOR]

---

### Post by soloman469 on 2013-07-15
You realize that 1.4.7 is HEAVILY outdated right?

---

### Post by soloman469 on 2013-07-15
> **Horbo said:**
> [https://help.ubuntu.com/community/InstallMinecraft147](https://help.ubuntu.com/community/InstallMinecraft147)

You realize that 1.4.7 is HEAVILY outdated right?

---

### Post by Horbo on 2013-07-15
> **soloman469 said:**
> You realize that 1.4.7 is HEAVILY outdated right?

Of course.  The installation guide though is the same for the current version.

---

### Post by efflandt on 2013-07-16
The current version does not use the same launcher. There is a new launcher that can launch current version (by default) or previous versions or snapshots of future versions by configuring other profiles.

Once you download Minecraft.jar from minecraft.net (assuming to ~/Downloads), there is no need to give it execute permission, simply do:```
java -jar ~/Downloads/Minecraft.jar
```Assuming you have openjdk-6-jre or openjdk-7-jre and optimal video driver installed, that is all there is to it. I have not found any need to use Oracle Java, in fact some people have had trouble using Oracle Java 7 for minecraft (unless they had some other issue).

If you have **Main Menu** (alacarte) installed you can set up a launcher for Dash to run the following in a terminal and then lock that to the Unity bar if you want to: [B]sh -c 'java -jar ~/Downloads/Minecraft.jar'
[/B]
PS: If you want to use more or less than the default 1 GB of RAM you can **Edit Profile** within the launcher or **Add Profile** for other versions or snapshots.

---

