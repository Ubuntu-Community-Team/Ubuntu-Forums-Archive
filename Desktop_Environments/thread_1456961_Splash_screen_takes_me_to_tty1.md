---
title: "Splash screen takes me to tty1"
date: 2010-04-17
forum: Desktop Environments
---

### Post by 61811 on 2010-04-17
_Background_
I was tinkering with my sound settings as had no sound, and deleted ALSA (which deleted some related files along with it) via Synaptic Manager.

_Problem_
After rebooting, the Splash screen starts properly with the Ubuntu logo and the orange progress bar below, but instead of proceeding to the login screen, it takes me to tty1 (terminal screen), with the message "No resume image, doing normal boot ...". I can, then, login properly, and I am in terminal mode with no GUI.

_Questions_
1) Can I launch GUI from terminal mode so I can reinstall ALSA and troubleshoot better?
2) If not, what can I do via the terminal mode to rectify this issue and get my GUI back?

_System Config._
Have two hard drives - one with Ubuntu and the other with WinXP. Grub option to select between the two works fine - that's how I am able to get into the Ubuntu HDD, though in Terminal Mode. When I select WinXP during bootup, everything works fine with that drive.

Please help. 

Thank you.

---

### Post by 61811 on 2010-04-18
Managed to get into my GUI desktop with "startx &" command in terminal mode.

Now I get this error if I try to run: 
System > Administration > StartUp-Manager, or
System > Administration > Synaptic Package Manager, or
Install Updates from Update Manager

_Error Msg_
"Failed  to run /usr/sbin/...
Unable to copy the user's Xauthorization file."

How can this be corrected?

Thank you.

---

### Post by 61811 on 2010-04-18
"Unable to copy the user's Xauthorization file" problem resolved.

However, the original issue still persists. Though I can enter GUI mode via "startx &" command from the terminal mode during startup due to lack of Splash, when I exit Ubuntu and restart, I am back to the same issue; i.e. 

The Splash screen starts properly with the Ubuntu logo and the orange progress bar below, but instead of proceeding to the login screen, it takes me to tty1 (terminal screen), with the message "No resume image, doing normal boot ...". I can, then, login properly, and I am in terminal mode with no GUI.

Any ideas what may help?

Thank you.

---

### Post by garvinrick4 on 2010-04-18
> **61811 said:**
> Managed to get into my GUI desktop with "startx &" command in terminal mode.

Now I get this error if I try to run: 
System > Administration > StartUp-Manager, or
System > Administration > Synaptic Package Manager, or
Install Updates from Update Manager

_Error Msg_
"Failed  to run /usr/sbin/...
Unable to copy the user's Xauthorization file."

How can this be corrected?

Thank you.Could be gdm package 

Description: GNOME Display Manager
 gdm provides the equivalent of a "login:" prompt for X displays- it pops up a
 login window and starts an X session. 
 
Code:

sudo apt-get install gdm

Or check first with Code:

aptitude show gdm

---

### Post by garvinrick4 on 2010-04-18
Here is for your sound:

sound Code:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base
sudo apt-get install pulseaudio

---

### Post by 61811 on 2010-04-18
Thank you garvinrick4!

gdm had somehow got uninstalled. Login splash now back in action.

Have to muster a lot of courage to purge the audio files/drivers again, since that's what got me into this mess. When I don't have a pressing need for my machine, I will try it and report back.

For now, the highly inconvenient issue is solved.

Thanks again!

---

