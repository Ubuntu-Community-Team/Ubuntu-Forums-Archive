---
title: "Minecraft Graphical Tearing / Shearing"
date: 2012-03-08
forum: Gaming &amp; Leisure
---

### Post by rowan_m on 2012-03-08
Minecraft shows this flashing tear / shear on the screen when running. I think it's a graphic card / driver related thing, as if you drag another window over the effect applies there as well.

Running Minecraft from a clean install.
Java installed from: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

```

$ uname -a
Linux Pickle 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

$ cat /etc/issue
Ubuntu 11.10 \n \l

$ java -version
java version "1.7.0_03"
Java(TM) SE Runtime Environment (build 1.7.0_03-b04)
Java HotSpot(TM) 64-Bit Server VM (build 22.1-b02, mixed mode)

$ grep -i Chipset /var/log/Xorg.0.log
[    19.937] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
[    19.937] (II) VESA: driver for VESA chipsets: vesa
[    19.944] (II) intel(0): Integrated Graphics Chipset: Intel(R) Sandybridge Mobile (GT2+)
[    19.944] (--) intel(0): Chipset: "Sandybridge Mobile (GT2+)"

```

**Any ideas on what settings to change, libs to install, configs to tweak?**

---

### Post by regor210 on 2012-03-08
Intel i810 is a low spec video adapter.

You can check your BIOS and see if you can make more ram available to your graphics adapter.

Here's a thread with an similar Intel issue.  
[http://ubuntuforums.org/showthread.php?t=1891511](http://ubuntuforums.org/showthread.php?t=1891511)

You could try running Minecraft 

$ java -Dsun.java3d.opengl=true -Xmx1024M -Xms512M -cp minecraft.jar net.minecraft.LauncherFrame


More help here for low spec systems
[http://www.minecraftforum.net/topic/158692-howto-optimize-minecraft-for-linux/](http://www.minecraftforum.net/topic/158692-howto-optimize-minecraft-for-linux/)

I used OptiFine
[http://www.minecraftforum.net/topic/249637-123-optifine-hd-b-fps-boost-hd-textures-aa-af-and-more/](http://www.minecraftforum.net/topic/249637-123-optifine-hd-b-fps-boost-hd-textures-aa-af-and-more/)

---

