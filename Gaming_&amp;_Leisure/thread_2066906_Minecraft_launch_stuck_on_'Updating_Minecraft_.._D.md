---
title: "Minecraft launch stuck on 'Updating Minecraft .. Done Loading'"
date: 2012-10-05
forum: Gaming &amp; Leisure
---

### Post by whitey_1 on 2012-10-05
Hi

Im trying to install and run Minecraft on Ubuntu 10.04. 

When i click on the minecraft.jar file and select 'open with OpenJDK Java 6 runtime' it loads the login screen, I enter my login details , then i click on the 'play demo' button then it goes to a loading screen saying 'Updating minecraft  ... done loading' The loading bar stops just short of the end and thats all that happens.

I have tried the Minecraft installer, all seemed to go well but it still doesnt load. Instead now i go to terminal and type 'minecraft' i then go to sign in , but i still end up stuck on the same loading screen.

I have been looking at other threads with this error but nothing seems to work.

I am trying it on demo mode to see if it works, then if it does i want to go premium.

Can anyone help? im not very techy

---

### Post by whitey_1 on 2012-10-06
This guide would be good if the instructions were clearer;

[http://www.minecraftforum.net/topic/1413715-minecraft-demo-crash-fix-for-ubuntu/](http://www.minecraftforum.net/topic/1413715-minecraft-demo-crash-fix-for-ubuntu/)

I dont understand the point about downloading the demo version. Surely that is the same version as the full version. There is detail about downloading 2 different minecraft.jar files, but i find the instructions there very hard to follow. 

Could anyone give me some help with this ?

Thanks

---

### Post by DarkAmbient on 2012-10-06
Try update to openjdk-7 ?

sudo apt-get install openjdk-7-jre

But my guess would be that you need to update/change your graphicdrivers.

---

### Post by whitey_1 on 2012-10-08
Hi ,

I tried to update the openJDK , this messege came back;

Building dependency tree       
Reading state information... Done
Package openjdk-7-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package openjdk-7-jre has no installation candidate


How do i know if my graphics drivers are up to date, is there a terminal command for that?

thanks

---

### Post by efflandt on 2012-10-08
I don't recall if I have successfully run minecraft in 10.04.  When I tried it earlier in 64-bit 10.04 on an old single core computer from 2004 with legacy ATI X1300 graphics it did not seem to run completely, although, I forget how far it got.

It did run in 64-bit 10.10 on a 1.66 GHz dual core laptop from 2006 with legacy ATI mobile X1300 video, and has run fine on other computers running 64-bit 10.10, 11.10, and 12.04, all using openjdk-6.  It probably helps to have more than one core, but I have played it on a 1GHz 2 core tablet PC w/2GB RAM on 11.10 booted from SD card.

Older integrated Intel video may be slow.

To see what video you have and modules loaded for it in a terminal type: **sudo lspci -v**

When you post the video related part of that output, highlight it and click # at top of message window to wrap it with code tags and preserve formatting.

---

### Post by Horbo on 2013-02-02
Tried every solution I could find - the only thing that worked was running with Java 6 instead of Java 7 (which is what I was originally trying with.  (That's Oracle, btw. No idea about openjava.)

See here: [http://ubuntuforums.org/showthread.php?p=12487873](http://ubuntuforums.org/showthread.php?p=12487873)

Installing Java 6: [http://www.liberiangeek.net/2012/11/install-oracle-java-jrejdk-6-in-ubuntu-12-10-quantal-quetzal/](http://www.liberiangeek.net/2012/11/install-oracle-java-jrejdk-6-in-ubuntu-12-10-quantal-quetzal/)

---

