---
title: ":confused:  xfce4, how to reinstall"
date: 2005-10-22
forum: Desktop Environments
---

### Post by minh on 2005-10-22
hi,
how do you reinstall xfce4, i just tried it and would love it because of its simplicity and efficace
i have installed xfce4 for a few day, then there was a trouble with desktop background, so i deleted /usr/lib/xfce and some folder else, and tried to reinstall it
:rolleyes: 
now my xfce don't have any menu, right buton mouse didn't work, :???: 
so the question is
how do you remove xfce COMPLETELY, and then reinstall it?
any helps would be greatly appreciated

---

### Post by Xian on 2005-10-22
Just do a search for "xfce4" in Synaptic and remove all those pkgs.
The following command would also probably do the job:

$ sudo apt-get remove libxfce4util-1

---

### Post by minh on 2005-10-22
> 
Just do a search for "xfce4" in Synaptic and remove all those pkgs.
The following command would also probably do the job:

$ sudo apt-get remove libxfce4util-1

thank you
i'll give a try

---

### Post by minh on 2005-10-22
hi,
i've reinstalled xfce4
a good thing is that now there is a splash screen appear
a bad thing that nothing change, they don't have any menu and background,:( 
and right buton doesn't work either
Do you have an idea to fix it?

---

### Post by minh on 2005-10-22
hi,
anyway now i'm on xfce4, and i don't know how to get back to gnome:???: 
can you tell me how to do it?

---

### Post by Xian on 2005-10-22
[QUOTE=minh]Do you have an idea to fix it?[/QUOTE]

Not really. You could see if it is a user config issue.
Go into you /home/username directory.

Rename those hidden .xfce folder(s) then login again.

---

### Post by Xian on 2005-10-22
[QUOTE=minh]anyway now i'm on xfce4, and i don't know how to get back to gnome:???: 
can you tell me how to do it?[/QUOTE]
Ctrl + Alt + F1

Login as user
$ sudo /etc/init.d/gdm restart

---

### Post by minh on 2005-10-22
now i can get back to gnome
but can you please tell me how to make a click right buton work under xfce4 ?

---

### Post by onestep on 2005-10-22
[QUOTE=minh]hi,
i've reinstalled xfce4
a good thing is that now there is a splash screen appear
a bad thing that nothing change, they don't have any menu and background,:( 
and right buton doesn't work either
Do you have an idea to fix it?[/QUOTE]

I have the same problem. 
To get my right click menu & background back I have to copy / paste / run this in a terminal: 

killall nautilus
killall xfdesktop
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
xfdesktop &

It will restore your menu and background... till you log out and back in again:
So, not to hijack this thread, does anyone else have a fix?
If not, how can I run this automatically at login?

---

### Post by minh on 2005-10-22
> 
To get my right click menu & background back I have to copy / paste / run this in a terminal:

killall nautilus
killall xfdesktop
gconftool-2 -s /apps/nautilus/preferences/show_desktop -t bool false
xfdesktop &

thank you Xian, thank you so much onestep 
it works now
even i don't know why it fixed it, but it works:)

---

### Post by minh on 2005-10-22
> If not, how can I run this automatically at login?
maybe you would ask your commands in /home/usernam/.bashrc, it will run at the beginning when start xfce

---

### Post by Xian on 2005-10-22
killall nautilus? What is nautilus running for in xfce?
I assume you are using it for some type of desktop management?

Eek. :)

---

