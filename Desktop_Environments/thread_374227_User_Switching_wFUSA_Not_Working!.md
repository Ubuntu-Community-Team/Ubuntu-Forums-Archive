---
title: "User Switching w/FUSA Not Working!"
date: 2007-03-02
forum: Desktop Environments
---

### Post by alinsenb on 2007-03-02
So, I'm trying to set up Ubuntu Edgy to switch between my default user account and a new one I created for my wife.  I created her account, she has a Home folder created, and I can log in as her with no problem.  I use the "Fast User Switch Applet" to switch over to her user account.  It logs in just fine, but then I start getting lots of error messages, generally following this format:

"An error occurred while loading or saving configuration information for gnome-session.  Some of your configuration settings may not work properly."

Where it says "gnome-session," that also goes for "power manager," "nautilus"...and anything else used by Gnome in the initial set-up of the desktop.  As I click through for details, I get the following:

"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: IOR file '/tmp/gconfd-<username>/lock/ior' not opened successfully, no gconfd located: Permission denied 2: IOR file '/tmp/gconfd-<username>/lock/ior' not opened successfully, no gconfd located: Permission denied)

In looking through other threads on the subject, I deleted .gnome, .gnome2, and .gnome2_private, with no help.  I tried logging in after restarting the system as her, before I logged in on my account, and got the same thing...  Originally, I thought it was some issue with sharing gconf settings between two accounts that are logged in at the same time, but I would have thought that logging in as her directly, without tying up gconf with my account, would have averted that issue...  I think the problem lies with gconf, but I have no clue what to do about it...  

This should be a simple fix, because others can do this with no problem!    

So yeah, any help would be provided!  Ubuntu Forums has been great for me in the past!  Much appreciated!

---

