---
title: "Java Apps and Destkop Launcher"
date: 2007-08-09
forum: Desktop Environments
---

### Post by dali77 on 2007-08-09
Hello guys,

After upgrade to feisty, I am not able to start any java application from Gnome Menu or from Gnome Destkop using Launcher. 

Example: 

I have a general java command in launcher: 

java -jar /home/bin/anyapp.jar

when I click on icon(launcher) nothing happens. 

But when I call exactly the same command from console (Gnome Terminal), it always works correctly. This happens with all java apps I have (currently 4). Any idea, what might be wrong.

My java version: 

Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

Thanks
Dali

---

### Post by capt scroggins on 2007-08-15
I am having a similar problem and would like to see if there is a way to do this.

The command I run is a Java command that starts the media server for my Xbox 360. If I go into a terminal session it works perfectly but if I try to create an executable launcher and choose "run in terminal" it starts but then the terminal window closes and so the process stops.

This is directory I run it from and the command:

Directory: /home/ubuntu/x360mediaserve

Command: ./start xxx.xxx.xxx.xxx (where x is the IP of my PC)

I have tried using & at the end to no avail. I read about "nohup" but am not sure of where to put the command.

Thanks

---

### Post by capt scroggins on 2007-09-06
Anyone with ideas on this?

---

### Post by capt scroggins on 2007-09-15
This can be closed (at least for me) as I followed the suggestion in this thread and it works perfectly.

[http://ubuntuforums.org/showthread.php?t=518309](http://ubuntuforums.org/showthread.php?t=518309)

---

