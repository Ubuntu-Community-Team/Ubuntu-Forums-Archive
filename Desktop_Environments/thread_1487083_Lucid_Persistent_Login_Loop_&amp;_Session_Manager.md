---
title: "Lucid Persistent Login Loop &amp; Session Manager"
date: 2010-05-18
forum: Desktop Environments
---

### Post by deBeaujeu on 2010-05-18
Ubuntu Lucid Lynx 10.04 is currently running following a problem free upgrade process from previous version 9.10. The VirtualBox program with WinXP virtual guest OS is also running with no apparent anomalies. The desktop is an Intel DG33FB motherboard driven by an Intel Core2 Duo E8400 processor and a SATA 500GB Western Digital Caviar Black.
 
 The environment worked just fine until hit by the Lucid Persistent Login Loop, a few days ago.
 During the login process, when your password is accepted, instead of moving to normal user session, the login screen (user selection) is presenrted again. You stay in that loop forever...
 
 After reviewing numerous Login Loop threads on the Ubuntu Forums, I decided to remove and install a fresh copy of gdm. When the Login Loop occurs you normally have no Internet connection and you need to use the Lucid install Alternate CD (the normal install CD will not work) from your local CD /DVD drive to install any package.
 Enter tty login with Ctrl+Alt+F1.

 To purge gdm:
 sudo stop gdm
sudo apt-get purge gdm  
 
 To re-install gdm
 sudo apt-cdrom add
 sudo aptitude update
 sudo aptitude install gdm
 
 Your CD/DVD drive needs to be seen by the terminal program before you start the install process.
 Two attempts were needed to end up with a successful gdm installation (all dependencies satisfied).
 
 At that point, the Persistent Login Loop anomaly was gone but a new problem with the user session appears.On the very bottom of the screen where you enter the password , you now find 3 additional boxes: Language, Keyboard and Sessions.The Sessions box allows you to select KDE or xterm.
 KDE take you to a black screen with a movable cursor. Xterm takes you to the terminal program.
 In KDE, Ctrl+Alt+Delete will open small window (on the black screen) asking you to close the session.
 
 So, there is a session, but my purge effort did more then I call for. The session manager may be gone or damaged. I thought that the normal Ubuntu 10.04 installer program was installing GNOME session manager and not KDE.
 
 Any suggestions to repair or install GNOME session manager (package name) or other solutions to this problem?

***deBeaujeu***

---

### Post by dabl on 2010-05-18
Login loop has a couple of known causes:

1. Full filesystem.

2. "sudo" prefix used to run KDE or Gnome packages (changes permissions on ~.Xauthority and ~.ICEauthority).

3. "Root" ownership of files saved in user's home directory.

4. Some forms of semi-broken video driver installation.

---

### Post by W3ird_N3rd on 2010-07-02
I have a remarkable case of #4. I have a laptop with SiS 630 integrated video. When I downgrade the memory for the integrated video (shared with RAM) to 8MB in the BIOS, I go into the famous login loop. Actually, when this happens I can't get a virtual terminal either. If I upgrade the memory again, it'll boot.

---

