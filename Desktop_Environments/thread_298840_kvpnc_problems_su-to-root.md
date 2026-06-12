---
title: "kvpnc problems su-to-root"
date: 2006-11-13
forum: Desktop Environments
---

### Post by Altrego on 2006-11-13
After installing KVpnc on ubuntu 6.10, I try to load it and get the following error:

Could not launch menu item
Failed to execute child process "su-to-root" (No such file or directory)

I have been using ubuntu for 2 weeks now, so sorry if this ranks as one of the dumber questions that arise.

---

### Post by Chonnawonga on 2006-11-19
Altrego,

I'm having this problem too. You might want to repost to the Absolute Beginners forum and see if you get any help.

I'm a beginner myself, but I think this has to do with permissions levels. i.e. you usually don't have enough access to run this program. If you go into the terminal and type

> sudo kvpnc

that might help, although it's not much as a long-term solution.

---

### Post by Altrego on 2006-11-20
I think you may be right. I've got one of my slick ops guys working on a solution for me. I'll post up any conclusions I find. 

My next project is getting the wireless card to work...

---

### Post by dgoel on 2007-03-16
Hi Altrego:

Did you ever find a solution to the kvpnc "su-to-root" problem?

Thank you.

---

### Post by scudsweep on 2007-03-17
I just figured out a solution for this issue myself.  The problem is the wrong command to call sudo is used for the kvpnc shortcut in the applications menu.  To fix it, right click on 'Applications' on the top task bar, and click 'Edit Menu'.  When the new window pops up, browse in the window to the location of the KVpnc shortcut.  For me its under Internet.  Once in there, right click on KVpnc and hit Properties.  Finally change the line next to Command from 'su-to-root -X' to 'gksudo -S'.

So the line in the Command box should look like: gksudo -S /usr/bin/kvpnc

Hope that helps!

---

### Post by CIDM on 2007-04-10
Hi !

I solved it myself by using right clicking on the Kvpnc icon. I used the command '/usr/bin/kvpnc' and used the last check box to run as user : root

It worked that way for me.

---

