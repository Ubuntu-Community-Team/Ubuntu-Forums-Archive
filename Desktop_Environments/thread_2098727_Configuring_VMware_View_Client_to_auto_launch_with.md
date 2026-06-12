---
title: "Configuring VMware View Client to auto launch without full GUI"
date: 2012-12-27
forum: Desktop Environments
---

### Post by ITGuyChris on 2012-12-27
[CENTER][CENTER]Mods: Please sticky this. I have yet to find more complete directions. 

[LEFT]Pre-Installation Why I'm doing this notes:

We are currently moving to a VMware View environment within the next 2 months and we were looking for a low cost solution to provide end users with the VMware View Client on DevonIT TC2 and Wyse C90LEW thin clients. We do not want to spend the money if we do not need to, and for us to upgrade all of our thin clients, it would be in the 5 figure dollar amount. The Wyse clients worked, but we were not able to get the DevonIT TC2 thin clients to run the VMware View Client. So this prompted the question of "How do we get our users to run the same OS with different hardware configurations and allow them connnect up to the VMware View environment we have in place?"

Without getting into to much more detail of our setup (which I would like to do), I have built a test VM to see if I was even able to get the VMware View Client to automatically launch without to resource hog GUI (GNOME or KDE). 


Thus begins the project: 


[/LEFT]
 ** Part 1: Installing the VMware View Client on Ubuntu 12.04 Desktop**[/CENTER]
[/CENTER]
   
  1. Download Ubuntu 12.04.1 Desktop (32bit or 64bit).
   
  2. Install OS using default selections. Remove CD when prompted and reboot.
   
  3. After reboot and initial logon, install all updates by selecting the gear in the upper right corner, choosing  Updates Available, then selecting Install Updates. Enter your password to authenticate.
   
  4. Reboot after updates have been installed.
   
  5. After logging back into the desktop, go to Dash Home  and type in Ubuntu Software Center. Select it when the USC appears. You can also find this on the left side toolbar on the dektop.
   
  6. Search for Synaptic Package Manager. Select it, then install. You will be prompted to authenticate.
   
  7. Close out of the USC window, then select the SPM from the left side toolbar. Authenticate again.
   
  8. In order to install the VMware View Client, you will need to allow the SPM to search Canonical Partners. To do this, go to Settings, then Repositories. A Software Sources window will now open. Select the Other Software Tab, and select the square next to Canonical Partners. Select close, then when the Software Sources window closes, select Reload.
   
  9. Select Search and type in VMware. You will need to scroll down until you find vmware-view-client. Select vmware-view-client and mark it for installation. Select Apply twice (a second window will open with the option). The software will now automatically install.
  *_Note:  As of this writing, the latest version is 1.6.0-0ubuntu0.12.04._*
   
   
  [CENTER][CENTER]**Part 2: Configuring the desktop to boot into text only mode**[/CENTER]
[/CENTER]
  1. Log into the Desktop (if you have not done so already).
  

2. Go to Dash Home and search for Terminal. Select the terminal icon when it appears. A terminal window will now launch.
  

3. Type the command **sudo nano /etc/default/grub** and press enter. You can use any text editor for this.
  

4. Locate the line **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"** and replace **"quiet splash"** with **"text"**. Save the file and update Grub by typing **sudo update-grub**. 
  

5. Reboot the workstation. Now the OS is configured to boot into Runlevel 2 (N 2).
   
   
  [CENTER][CENTER]**Part 3: Configuring VMware View Client to automatically launch without full GUI**[/CENTER]
[/CENTER]
  

1. Log into console (if you have not done so already). 
  

2. Type the command **sudo nano /etc/rc.local** and press enter. You can use any text editor for this.
  

3. While in the rc.local file, type **in xinit /usr/bin/vmware-view** ** -fullscreen **above exit 0 to allow the VMware View Client to automatically launch in full screen after all services and drivers have been loaded. You will not be prompted to log in to the OS after this change is made. Once you are in the VMware View Client and the user selects File -> Quit, they will be brought to the console login.





Finally, I will continue to update these steps if someone wants to help share tips/ideas/etc.

---

### Post by mripra on 2013-03-12
I tired you method but it didn't work for me. After editing the rc.local i reboot the machine it just came back to login screen in text mode.
I typed following in RC.LOCAL above exit 0 > in xinit /usr/bin/vmware-view -fullscreen
I am running LUBUNTU 12.04 desktop.

Can you please let me know what I am doing wrong.

Also please let me know if need more Info that i have provided.

Thanks
Mri

---

### Post by ITGuyChris on 2013-03-12
Mripa,

I think I found a typo in my directions. Under Part 3, step 3 where you edit the rc.local file, just type in the following:

xinit /usr/bin/vmware-view -fullscreen


For some reason, I must have bolded the in before xinit. Change your rc.local to what I typed above and let me know the outcome.

---

### Post by mripra on 2013-03-12
Thanks it working now.

---

### Post by mripra on 2013-03-13
Chris,
I have question for you, have you figure out a way VMware to not to quit to console log in when client exit or logoff other then coming back up as a Vmware log in full-screen?
I am thinking of make a cron job to keep checking for VMware client if up or not if its not up reboot the unit? What you think of this idea?
Thanks

---

### Post by jamesaussies on 2013-03-19
Chris

Great stuff - thank you for the post.

I noticed that the View Virtual Desktop windows does not resize - meaning if you were logged in from another computer the screen size is set and this session with the newly built "Ubuntu Thin Client" using that setting. Any suggestions?

---

