---
title: "Login Loop After Update"
date: 2015-03-12
forum: Desktop Environments
---

### Post by dave133 on 2015-03-12
Following an update this afternoon and subsequent reboot, I am no longer able to login.  The system boots fine, but instead of logging me in automatically, I'm taken to the login screen.  I enter my password, but all that happens is that the screen goes blank for a moment and I'm taken right back to the login screen with no explanation.  On top of it, I have no problem logging in as a guest, but otherwise I can do not work except through the command line.

I've tried fixing the problem in recovery mode through the Grub menu.  If I try to use failsafeX mode, I get a screen that says "The system is running in low-graphics mode.  Your screen, graphics car, and input device settings could not be detected correctly.  You will need to configure these yourself."  However, when I hit OK, I'm taken to a menu screen where I can't traverse the menu.

I want to assure you that THIS IS (PROBABLY) NOT A DUPLICATE!  I have spent the day checking countless forums and trying dozens of suggested solutions to a similar problem with no working solution so far.  This is my last resort.  So before hitting me with somebody else's answer, please be aware that I have already tried (among many other suggestions):

- Reconfiguring, uninstalling, and reinstalling lightdm
- Installing and trying gdm
- Reinstalling ubuntu desktop
- Removing .Xauthority
- Booting on an older version of the kernel
- Checking the available memory (I have plenty of memory available)

The list goes on and on, and I've been trying to fix the problem for hours.  In addition, I have checked the files under /etc/lightdm/.  lightdm.conf does not contain a line concerning "greeter-session=..." and the lightdm.conf.d repository is empty.

Any other suggestions out there would be helpful, as my next step is downloading Ubuntu onto a thumb drive through another computer and attempting to reinstall it.

Thanks.

---

### Post by ian-weisser on 2015-03-13
What you are describing seems a lot like X trying to start...and crashing, dumping you back to lightdm.

Have you checked the syslog and X logs in /var/log?
Have you looked for a crash report in /var/crash?

---

### Post by dave133 on 2015-03-13
Looking in the syslog doesn't seem to reveal anything telling, but I'm not really sure what I'm looking for.

Looking in Xorg.0.log, I'm not catching any errors, but I am getting a few warnings that seem to center around the graphics chip (mine is Intel 965GM) that all read as some variation of:
[FONT=courier new](WW) Falling back to old probe method for...[/FONT]

Also, looking under /var/crash, I see three files from yesterday around the time of the crash:

[FONT=courier new]dave whoopsie 10151932 Mar 12 12:25 _usr_bin_compiz.1000.crash
root  whoopsie   357329 Mar 12 15:22 _usr_bin_Xorg.0.crash
root  whoopsie   413716 Mar 12 20:38 _usr_lib_gdm_gdm-session-worker.0.crash
[/FONT]
Judging from the date signatures, I'm guessing that the first is probably the problem, the second one may have stemmed from my removal of .Xauthority (before I resinstalled it), and the third stemmed from trying to see if gdm would fix the problem (it didn't).  However, I'm not real sure what to look for or how to pinpoint the problem.

---

### Post by ccbmailroom on 2015-04-18
Ubuntu won't let me login at tty1 even if trying as guest.  Is my machine with countless hours of college information collected and created doomed for a reimage?  I have removed the remainder of this post due to swearing. edit: it's late at night and I have school in a few hours.  I am so lost on. Xauthority and so on but I was able to login to the shell.

---

### Post by ian-weisser on 2015-04-18
If you are able to login to a console, but logging into the GUI results in a return to the login screen, the first step is to see post #2 above.

If that's not what is happening, then please describe as best you can. We can help a lot, but we're not psychic.

---

### Post by grahammechanical on 2015-04-18
I keep my important (do not want to lose) data on a separate partition. Then I can re-install without loosing data that is important to me.

It is also possible to re-install Ubuntu without loosing what is in the /home folder. I did this recently. I had a long standing installation of 15.04 that was taking an excessive time to load. I shifted any data that I did not want to loose on to my Data partition and I re-installed using the Something Else option but I did not tick the box labelled "Format the partition." This meant that the /home folder was not over-written.

I lost the Libreoffice Recent Files list but not much else. I did not lose the data in /home at all. And I fixed the long loading time problem. During the re-install we are warned about over-writing certain system folders. But that is what we would expect to happen and we would want to to happen to fix what is wrong.

Regards.

---

### Post by MikeCyber on 2015-04-19
Had such yesterday and it only needed a reinstall of Nvidia driver.

---

### Post by ccbmailroom on 2015-04-19
I was able to get into a console/terminal full screen environment but I followed the link [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop) where some said to ctrl+alt+f2 then do a "sudo apt-get install gdm" then "sudo dpkg-reconfigure gdm" then back to the login screen.  Now I have a blank screen.  I see the glow of the black screen as it is getting power.  Hitting ctrl+shift+F3 no longer works as the screen looks like it's about to give me a prompt then goes black again.

Specs:  **HP 15-g012dx **laptop with 750GB hard drive AMD A8-6410 with quad core processor based on AMD Kaveri architecture.  2MB of L2 cashe.  Radeon 5 graphics 

***** to clarify, I have a lot of information on this laptop I don't want to lose as finals for HCCS are coming up.

---

### Post by MikeCyber on 2015-04-20
Yea that's not lightdm related. Boot failsafe, remove gdm and reinstall your graphics driver.

---

### Post by ccbmailroom on 2015-04-20
[FONT=arial]***scratch the blank screen thing with gdm, I think I got at least that sorted out... I did the 

[/FONT][FONT=arial]sudo apt-get remove gdm
sudo apt-get purge gdm

Then I did the 

sudo apt-get update
sudo apt-get install lightdm
sudo dpkg-reconfigure lightdm

Now... I'm back to the login loop situation before the blank screen issue.  Any advise/help?  

Ubuntu computer down for day 2
[/FONT]

---

### Post by ian-weisser on 2015-04-20
Can you login to the guest account? Or any other account?
Do they also crash?

If not, then the problem is a setting in your /home.
Are there any crash reports or X logs?

---

### Post by MikeCyber on 2015-04-21
If you can login into xfce etc. anything that doesn't need opengl (lightdm?), it must be your graphics driver to reinstall.

---

### Post by ccbmailroom on 2015-04-21
Attempting to access Guest Session brings the login loop back with no success.  I tried ls -ld in ctrl-alt-F3 and looked at the /tmp file and it did read dwrxrwxrwt as stated on [http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop) and it looks okay.  Concerning reinstalling the graphics driver, 1) which one do I use and 2) how do I do that through terminal?

I don't know how to look at .xsession-errors nor do I know what to look for in it.  Could it possibly be an .Xauthority issue?

[FONT=arial] Ubuntu computer down for day 3[/FONT]

---

### Post by MikeCyber on 2015-04-22
Three days ago I had the latest Nvidia driver already downloaded (from Nvidia) before I've updated. So I only did: chmod +x and executed it for login to work again. I could have used also xfce for download as it doesn't need opengl. Maybe try to install xfce? As simple as: 
sudo apt-get install xubuntu-desktop

---

### Post by CantankRus on 2015-04-22
See if you can install and login to the flashback session.
At the greeter hit ctrl+alt+F1 , login and the run...
```
sudo apt-get install gnome-session-flashback
```

When finished enter
```
sudo reboot
```
and at the greeter choose the
[LIST]
[*]Gnome Flashback (metacity)
[/LIST]
session.

---

### Post by ccbmailroom on 2015-04-22
I did the sudo apt-get gnome-session-flashback and rebooted but no  option to choose "Gnome Flashback" at all.  I still remained at the  login loop.  I then tried 'sudo apt-get install xubuntu-desktop' and  now, instead of a login loop on Ubuntu 14.04, I'm at a login loop at  Xubuntu.  Still can't get in.  

Through terminal, I logged in and  copied my files to a hard drive and will be putting them on a dated  Windows XP computer to print.

[FONT=arial] Ubuntu computer down for day 4
[/FONT]

---

### Post by ccbmailroom on 2015-04-23
While I appreciate the input, my Ubuntu laptop is out of commision until the end of finals.  I've copied all of my documents and other files to a portable hard drive and will be working off a non connected Windows computer.  Hopefully after a few weeks I can possibly get some assistance as I try to re image my laptop again to make it useful.  Thank you again for all of your help.

---

### Post by MikeCyber on 2015-04-23
Have a look at the logs in /var/log foremost dmesg etc.:
cat /var/log/dmesg

---

### Post by ccbmailroom on 2015-05-20
Okay, I'm back.  My computer has been down for four weeks now.  The Nvidia driver I think was replaced with the Omega driver by HP.  I removed the Nvidia driver all together and installed the Omega driver.  The login loop issue still remains however the installation of Xubuntu did give me the option to login with XFCE so I could at least access my files.  Any thoughts on this?  I own a 2000 something Windows XP PC that is not connected to the internet that currently has all of my files/music/videos but I would like to use Ubuntu.  I am under the impression that it will work one way or another, I REAALLY don't want to instal Windows 8 back onto that laptop but if I can't get it to work by June, that's probably going to be the route I'm going to have to take as I need a portable computer.

---

### Post by CantankRus on 2015-05-20
If you say you have backed up all your personal files, just do a reinstall because
more often than not the situation you are in is caused by the user and without knowing what you have done
this is the easiest option.
half an hour versus 4 weeks. :p

---

### Post by ccbmailroom on 2015-05-26
Okay, I'm on the Ubuntu 14.04 laptop again writing this.  However I do want the most up to date video driver to get this laptop back up to speed.  I'll take this off of this forum topic and I do thank you all for the help.  Thank you

---

