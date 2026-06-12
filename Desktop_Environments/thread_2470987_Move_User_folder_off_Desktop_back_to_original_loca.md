---
title: "Move User folder off Desktop back to original location between Home and Desktop"
date: 2022-01-18
forum: Desktop Environments
---

### Post by ozark_hillbilly on 2022-01-18
Ubuntu 20.04 LTS

issue: My User [my name "Ed"] folder normally located in Files display between Home and Desktop has somehow moved onto the Desktop.

No, I have no freakin' idea how I managed this rookie goof. Lol

You cannot delete it by a right click option.

I have attached a Desktop screenshot that shows the folder properties. 

Name   Ed
Folder (inode /directory)
42,817 items, totalling 2.2*GB

With terminal it shows it as being a sub directory under: /home

I did search for a related issue in the forum so if one exists please direct me.

any suggestions are appreciated....

---

### Post by tea for one on 2022-01-19
Your screenshot shows nine folders on your Desktop.
I would think that you have inadvertently activated [COLOR="#0000FF"]Show the personal folder on the desktop[/COLOR]

Have a look in your extension [COLOR="#0000FF"]Desktop Icons[/COLOR] or similar if you have installed an alternative.

If you open a terminal:-
```
cd /home
```
```
ls
```
Do you see your user name Ed?

---

### Post by pushbike06 on 2022-01-19
On my desktop, the users home directory appeared on the Desktop as a result of the upgrade to Ubuntu 20.04.
This seems to be implemented from "deep" system programming as it occurs with all user log ins.
This icon/link does not appear in the users Desktop folder and File Manager/ Preferences does not have a switch.
I find that it is redundant as my desktop has a side bar with all my preferred shortcuts. This side bar is always visible whereas the Desktop icon is usually obscured by an open application.
Maybe a Ubuntu developer can explain this implementation.

Have a look at this solution:
https://askubuntu.com/questions/1230877/how-to-remove-home-folder-icon-from-desktop-in-ubuntu-20-04

---

### Post by ozark_hillbilly on 2022-01-20
Thank you for sharing this information. I was trying to figure out what I inadvertently did 
to have the folder on the Desktop. I agree it is redundant.

---

