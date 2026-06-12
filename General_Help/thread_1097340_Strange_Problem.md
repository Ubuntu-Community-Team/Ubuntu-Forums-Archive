---
title: "Strange Problem"
date: 2009-03-15
forum: General Help
---

### Post by rockstone on 2009-03-15
I am running intrepid 64 and have been experiencing a strange problem where gnome-do and application windows become graphically distorted as seen in this picture.

[IMG]http://img150.imageshack.us/img150/7060/screenshotb.png[/IMG]
[http://img150.imageshack.us/img150/7060/screenshotb.png](http://img150.imageshack.us/img150/7060/screenshotb.png)

It seems that this happens when an office program (OpenOffice or Office 2007) is running and the window is open to a file where the user has write access. If I close or minimise the program, or if I change permissions so that the user has only read access, the problem goes away.

If anyone has any idea what might be causing this problem and/or how to fix it I would be very appreciative.

Thanks in advance.

---

### Post by dusan.saiko on 2009-03-15
What card and driver are you using ?

Can you check System - Administration - Hardware Drivers
and try change it ?

---

### Post by rockstone on 2009-03-15
I am using the Nvidia accelerated graphics driver (version 177) and the card is a Nvidia Go 7700.

---

### Post by rockstone on 2009-03-16
Any more ideas on what could be causing this problem?

The strange thing seems to be that write access to the file seems to matter. I can even change the file permissions to chmod 577, giving the user everything but write access and giving everyone else full permissions without running into this problem. Once I try to give the user write permissions though it will start again. That seems kind of bizarre. 

Also it appears not to be a problem with the user settings either since I get the same problem if I try with another user (that's actually how I managed to figure out that permissions mattered).

---

### Post by rockstone on 2009-03-18
Anyone?

---

### Post by rockstone on 2009-03-23
bump

---

### Post by jo4hnc on 2009-03-23
Hey Rockstone,

I just changed the appearance settings on my machine using Preferences>appearance. I set the visual effects to Extra. A while after doing so I typed out an email in Thunderbird. The problem wasn't as severe as yours but as I typed the message the title bar at the top and a bit of the status bar flickered with the same kind of aberrations. If you have things set to a high level of special effects, you might want to drop it back a notch and see if that helps. Just a thought.

J

---

