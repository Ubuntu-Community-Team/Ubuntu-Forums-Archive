---
title: "panel application launchers not working"
date: 2009-01-28
forum: Desktop Environments
---

### Post by scottgrumm on 2009-01-28
I upgraded from Ubuntu 8.04 to 8.10 and now the application launchers in the panel on the second display are not working.

I have two monitors configured in xorg.cof.  Xinerama and TwinView are both disabled.  The system has a NVIDIA Quadro NVS 290 graphics card with the NVIDIA UNIX x86_64 Kernel Module 177.82.  I tried deleting xorg.conf and let `nvidia-settings` create a new xorg.conf file and enabled the second monitor but it had the same behavior.  Compiz is installed.

When I click on the Firefox Application Launcher icon in the top panel on Screen 0 Firefox launches and runs as expected.  When I do the same thing on Screen 1 I get a dialog box with the title "Error" but there is no text or button.  Attempts to close the dialog by clicking on the X in the upper right corner or from the Window Menu in the top left both fail.  The same problem happens if I click on the Application Launchers for Evolution, Help and Terminal that I had added that I have had in the top panel.  Once this happens the top and bottom panels on both screens no longer respond to mouse clicks.  If I Log out while the Error dialog is up I get a warning that "A program is still running:", "Panel", "Not Responding".  If I Logout anyway the log out works.

Starting all of the applications from the Applications menu works as expected.

The same problem happens when I log in as Guest so this should not be a problem with a user environment.

Help resolving this is greatly appreciated.

---

