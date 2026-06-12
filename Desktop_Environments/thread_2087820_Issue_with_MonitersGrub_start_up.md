---
title: "Issue with Moniters/Grub start up"
date: 2012-11-24
forum: Desktop Environments
---

### Post by lovelinuxlol on 2012-11-24
First: If this isn't in the right forum can a admin please move it to the correct section. Also Edit my Topic for any misuses of terms.


So I had originally used a Duel Monitor  set up, with my main being my smaller 1440x900 resolution 19inch Monitor and my secondary being a 45inch TV (can't remember the resolution. Anyways I knew I was gonna be losing the monitor so I changed it back to just the 19inch and it looked like everything worked, so I use my computer turn it off and the next time and every time since then it's only loaded the grub (hope I'm using the term correctly, you know it's just commandline basically, so maybe I should use the term terminal).  


So now I have no idea what commands I can use to make it recognize my monitor/get back to the desktop. 

My system is a duel boot set up so now I just log into my windows 7 (W7) because I can't do anything in my Linux portion. The problem with that is I only used W7 for gaming/MP3 Player (I had used Linux for gaming before, but my MP3 never worked so now i just use W7 for both).  

But my Linux Portion is what I use mainly, so now I have pictures, Music, Movies, I can't access. I'm hoping i can fix this other wise I'm gonna have to wipe and start over. :( 

Edit: I've been a Linux user for years and can get around and solve most of the problems for the most part but I don't consider myself a high-end advanced user. My system is 10.10 I never upgraded because when I heard about Unity being used (which I loved for my netbook) I didn't see it as a good upgrade compared to my current desktop.

---

### Post by ranger1021994 on 2012-11-24
Sorry mate..still cant understand your question

Your linux is showing you black terminal like screen after booting ? or is it something else ?

---

### Post by lovelinuxlol on 2012-11-24
> **ranger1021994 said:**
> Sorry mate..still cant understand your question

Your linux is showing you black terminal like screen after booting ? or is it something else ?
 You know when you do a Duel install and when you turn on your computer and it gives you an Option of starting up your Linux, Safe Mode Linux, Grub, and Windows 7. 


Well when I click the Linux (or even safe mode) it loads and then after the loading screen it brings up command line only no graphical interface (gnome). Now it will ask for my usual login information, I can input the information and then I'm stuck in just the command line. I can still input commands but I need to know how to make my computer go back to the GUI. 


So my question is essentially what are the commands where I can change monitor specifications so when I boot up it detects it properly and will boot up the GUI without issue. 

I need to know the commands to change resolution, 

make this 19inch Monitor the main monitor (I believe it's Secondary)  

The command to make my linux detect my monitor (I'd prefer this because I assume it would set everything up for me). 

The command to go from the commandline to gnome.  

and the command to SAVE these settings.

---

### Post by ranger1021994 on 2012-11-24
Press Ctrl+Alt+F8 or F7
That should take you to GUI mode.
If you go into GUI mode once , try rebooting and see which mode does linux boot into again.

---

### Post by lovelinuxlol on 2012-11-24
ok I'm On my ubuntu right now, it's running in safe mode. I'm trying to run the moniters program but it just gives me the Nvidia section only. 

it says "You Do not appear to be using the NVIDIA X DRIVER. PLease Edit your X Configueration fil (just run `niviaxcong` as root and restart the X Server." 


now I know how to run the command but I Don't want to before i Know how to restart the X server. 


Edit: Wait I'm figuring it all out, lol I haven't had to done anything with the terminal for awhile,  I think I can solve this on my own.

---

### Post by ranger1021994 on 2012-11-24
Try reinstalling your NVIDIA drivers.
To restart X server 
Type :
```
sudo pkill X
```
Killing X server simply reboots the Linux system (Computer does not restart but the Linux session restarts)

---

### Post by lovelinuxlol on 2012-11-25
Figured it out. thanks for the help. :guitar:

---

