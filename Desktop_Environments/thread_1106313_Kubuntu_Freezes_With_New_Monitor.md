---
title: "Kubuntu Freezes With New Monitor"
date: 2009-03-25
forum: Desktop Environments
---

### Post by elb0w on 2009-03-25
Hello all, I am having a problem finding an answer. I have a kubuntu 8.10 machine ive been working on. I recently moved the box to a new work station and a new monitor. When I login into the KDE enviornment it freezes after awhile with my mouse still able to move (The pc is completely frozen though, cant get out).

I can login into gnome and it works fine. Normaly I would not care and just use gnome but I have alot of kde tools setup that make my job alot easier and want to get this working. When I plug my pc back into the old monitor it works. 

Thanks if anyone has any ideas

---

### Post by inobe on 2009-03-25
welcome

sounds like some sort of conflict between desktops !

have you changed any resolution settings while in kde's session ?

---

### Post by smoothdave on 2009-03-26
I'm having a very similar problem; however, I am running gnome.  Several times a week, gnome appears to freeze up.  I can move the mouse, but everything else about the desktop is locked up.  I can log in remotely and the system seems to be fine.  Restarting gdm remotely does nothing.  It just restarts normally, but my screen remains the same.  The only fix I've found so far is a reboot.

Thank you.

---

### Post by smoothdave on 2009-03-26
I've got a bit more information.

ps aux | grep gdm 

produces this output, but I can't see anything on my screen...

root      3512  0.0  0.0   1776   416 ?        Ss   11:06   0:00 /usr/lib/gdm/gdmopen -l /bin/sh -c /usr/bin/whiptail --yesno 'There already appears to be an X server running on display :0.  Should another display number by tried?  Answering no will cause GDM to attempt starting the server on :0 again.  (You can change consoles by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7 to go to console 7.  X servers usually run on consoles 7 and higher.)' 16 70

---

### Post by elb0w on 2009-03-27
Its extremely odd. I was running 1920 res on the old monitor, new monitor supports less. But to test I went back to the old monitor and lowered the resolution. Then went back onto new monitor and same error. Im at a loss, since my work is upgrading all their systems and these are the new monitors I sort of have to find a fix. other than reinstalling

---

### Post by elb0w on 2009-03-28
no ideas?

---

