---
title: "Xfce4-notes"
date: 2017-07-24
forum: Desktop Environments
---

### Post by piotrpatrzylas on 2017-07-24
Hi all,

First of all sorry if I posted in wrong part of the forum.

My problem is XFCE4-notes program.
When I installed it first time it worked perfectly (fresh installation of Ubuntu 16.04 LTS + wine with dependencies).
When I reboot system and I've tried to open it nothing happened. 
I searched for the solution - the only thing I found was to try deleting files in .config/xfce/ for this program.
This didn't helped much.
I've tried to remove it, to purge it, re-install etc.
I discovered that xfce4-notes.rc file in folder mentioned above change visibility to false every couple second.
When I manually change it to true program works, although not saving any notes.
After few seconds/1-2 minutes visibility is changed again to false.

How can I fix it, please?

log when I try to open it with terminal:
user@user-ThinkPad-X220:~$ xfce4-notes

** (xfce4-notes:18199): WARNING **: main-status-icon.vala:37: Status Icon is not embedded
user@user-ThinkPad-X220:~$ 


Big Thank You for your help!

---

### Post by him610 on 2017-07-24
> My problem is XFCE4-notes program.

It is listed as xfce-notes 1.8.1 in the repository. There is also xfce-notes-plugin that goes along with it. They are both installed by default when one installs Xubuntu. It is possible there is some misconfiguration between Ubuntu and an XFCE program.

Notes on my machine appears to have NO option to save a note; however, there is an option to Rename a note (F2). If you desire to save your notes, you could consider using the default text editor whichever one that may be for Ubuntu.

---

### Post by again? on 2017-07-25
Are you using the xfce desktop or Ubuntu/unity?
There are many note taking apps for linux you can try.
If using the Unity desktop you can try [indicator-sticky notes]("http://www.webupd8.org/2012/11/pin-notes-on-your-desktop-with.html") which is similar to XFCE4-notes.
[ATTACH=CONFIG]276128[/ATTACH]

Another simple method is to add quicklist menu items to the gedit launcher that addto and open a "Notes" text file.
I have this and by using xsel, can add a note to the my Notes file by simply highlighting some text and clicking on the "Add to Notes" quicklist item.
[ATTACH=CONFIG]276129[/ATTACH]

---

