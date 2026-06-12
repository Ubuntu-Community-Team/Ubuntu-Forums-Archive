---
title: "nautilus only opens files in /home folder"
date: 2021-04-26
forum: Desktop Environments
---

### Post by knight69 on 2021-04-26
I am running Ubuntu 20.04 with Gnome flashback. When I open the "Places" menu the only options available are files in my home directory. If I select "Computer", nothing happens. I cannot access any files outside of /home.

If I open nautilus with sudo, I have complete access to all files.

From the terminal I have complete access to all files on my computer without using sudo.  

Only being able to use nautilus for file management in my home directory is new and is a very annoying restriction. Is there any way around this stupid restriction?

---

### Post by grahammechanical on 2021-04-26
> Only being able to use nautilus for file management in my home directory  is new and is a very annoying restriction. Is there any way around this  stupid restriction?

I do not have this feature, if we can call it that, on my installs of 20.04, 20.10 or 21.04. It is an annoying restriction but it is not standard. The big change that comes with 21.04 is that the user's home folder is now private and cannot be viewed by other users on the OS.

I can only guess that somehow the permissions for root have been altered. As a standard user we normally have permission to access and read but not delete or read/write to the folders and files in root.

Regards

---

### Post by knight69 on 2021-04-26
Well, this is dumb. With Nautilus open, you can find "Preferences" in the menu under the 3 bars at the top. Click on "Preferences" and under the "Views" tab check the box beside "Show Sidebar". The next time you open Nautilus, the sidebar will be displayed and at the bottom is "+Other locations". Clicking on that, you can then select "Computer" and it will take you to the root folder where you can see all the folders off the root.

Now who in blazes dreamed that one up and why can't you access it directly from the drop down "Places" menu?

---

### Post by zebra2 on 2021-04-27
I use 21.04 (at least for the next two days) and I have "show sidebar" checked off but I don't remember doing that. I have access to root files under the conditions stated in post #2. Seems to me that I think that is normal behavior. Its my chosen "preference" and either I chose it or it became default as the result of an upgrade or new release.  What I'm seeing is normal, at least with 21.04. If it changes in 21.10 I'll let you know.

---

### Post by grahammechanical on 2021-04-27
> Now who in blazes dreamed that one up and why can't you access it directly from the drop down "Places" menu?

If it is now default in 20.04 and later not to show the side panel unless the user activates it then blame the Gnome developers. I have never needed to activate it. Let me tell you another weird change. There is no drop down menu in Gnome terminal that will allow Copy & Paste. You have a to use shortcut keys. And you find them by clicking the 3 bars icon (called hamburger by some), Selecting preferences and then shortcuts.

Regards

---

### Post by TheFu on 2021-04-27
I have 21.04, installed a few days ago.
Running Nautilus for the first time, the sidebar is displayed. Hidden files are not shown.
In the sidebar, selecting the "+ Other Locations" has "Computer" ... which displays / with everything expected.  No sudo needed. Running GUI programs with sudo is generally a bad idea, especially when the undesirable side-effects aren't understood.

I generally run a **rmdir ~/*** to clean up all those empty, unused, directories. The sidebar in Nautilus still shows the ones that are gone for some reason.

Because I'm running nautilus remotely, using **ssh -X u2104 nautilus**, the time from start until it gets displayed is about 15 seconds, which just shows how bloated it is.  Further, it is ignoring window borders, title bars, which is fairly obnoxious too, IMHO.

I'm remembering more and more why I dislike Gnome DEs. They assume all sorts of things that aren't true rather than showing the truth and honoring standards.  Ended up having to edit: ~/.config/user-dirs.dirs to remove all those XDG places ... and they still showed up in Nautilus, but at least each could be deleted.  Except "Downloads", which isn't in the XDG AND cannot be removed from nautilus.  

**Pro Tip for Gnome developers: /tmp/ is for downloads**

So much for Gnome trying to de-complicate and declutter things. 
Where are my standard Window borders and titlebar?!!!

---

