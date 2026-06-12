---
title: "Numbat, Kubuntu, and I think openjdk"
date: 2024-05-18
forum: Gaming &amp; Leisure
---

### Post by dennislarge-al on 2024-05-18
My issue I'm sure is my knowledge of Linux GUIs. Lots of experience server-side, but all cli.
Fresh install of 24.04 Kubuntu. Trying to run a jar file. Ran with no effort on 22.04 GNOME. Installed openjdk app and openjdk-11, right-click the jar, runwith that, all good.
The jar file in question is a sites' custom modded Minecraft launcher
On this build however, not so good. I can manage to start the launcher in Konsole (java -jar filename.jar) then tries but can't actually launch any of the options.

Other apps run just fine, even Steam.
Thanks for looking.

---

### Post by maximge on 2024-05-21
It seems like you're encountering issues with running a custom modded Minecraft launcher jar file on a fresh install of Kubuntu 24.04, despite it working fine on GNOME in Kubuntu 22.04. Here are some steps and considerations that might help you troubleshoot and resolve this issue:


**Check Java Version Compatibility**
   - If the versions differ, try installing the exact version you had on 22.04. For example, if it was OpenJDK 11, install it with:

     sudo apt-get install openjdk-11-jdk



**If it doesn't work, try it reinstall Java**
  
     sudo apt-get remove --purge openjdk-11-jdk
     sudo apt-get install openjdk-11-jdk

---

