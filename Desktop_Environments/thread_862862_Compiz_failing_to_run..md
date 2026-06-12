---
title: "Compiz failing to run."
date: 2008-07-17
forum: Desktop Environments
---

### Post by blue.monday on 2008-07-17
First time Ubuntu user is trying to utilize the full usage of this OS.

My problem:
 I'm using the latest version of Ubuntu, I installed today. Noticed that the nvidia drivers were needed to run the 'desktop features' so I installed them. I was browsing the add/remove... and installed Compiz. It installed find but it looks like nothing had happened. under the system tab has no evidence of Compiz being installed.

What Ive done:
 After searching these forums I have tried some things to no avail. Ive tried the Compiz check and all the checks were ok but the last one was skipped but it said that it could not read the graphics memory. 
 The most important thing to mention is that when  
I type compiz in the terminal it gives me this:
blue@Spoof:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I ve also tried doing a command to disable that file but it said it was missing, probably the wrong command. To be frank I don't know how to search for this type of error. Any help is greatly appreciated.
-blue.monday

---

### Post by nikgare on 2008-07-18
You can enable compiz by enabeling **Desktop Effects** in **System->Preferences->Appearance->Visual Effects**

---

### Post by Potatoj316 on 2008-07-18
You could alternativly install the compiz settings manager, in the terminal type (no quotes) "aptitude search compiz" find the one that sounds like an effects settings manager and type "sudo aptitude install compiz-[whichever one it was]" then enter your password.  Now go to System -> Prefrences -> Compiz Effects manager (or something like that)

---

### Post by overdrank on 2008-07-18
> **blue.monday said:**
> First time Ubuntu user is trying to utilize the full usage of this OS.

My problem:
 I'm using the latest version of Ubuntu, I installed today. Noticed that the nvidia drivers were needed to run the 'desktop features' so I installed them. I was browsing the add/remove... and installed Compiz. It installed find but it looks like nothing had happened. under the system tab has no evidence of Compiz being installed.

What Ive done:
 After searching these forums I have tried some things to no avail. Ive tried the Compiz check and all the checks were ok but the last one was skipped but it said that it could not read the graphics memory. 
 The most important thing to mention is that when  
I type compiz in the terminal it gives me this:
blue@Spoof:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1920x1200) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I ve also tried doing a command to disable that file but it said it was missing, probably the wrong command. To be frank I don't know how to search for this type of error. Any help is greatly appreciated.
-blue.monday

Hi and a good place to start is the link in my signature
Comp-Fusion FAQ'S

---

### Post by blue.monday on 2008-07-18
> **overdrank said:**
> Hi and a good place to start is the link in my signature
Comp-Fusion FAQ'S

For some reason when I installed the settings manager it worked. Strange when I typed compiz in the terminal and it would not start because a file was messed up. I would try to type in in again but I'm afrade i'll break it... everything I mess with breaks.Thanks to potato for the help, and everyone else.

---

