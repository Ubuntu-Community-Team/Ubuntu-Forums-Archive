---
title: "Ubuntu/Kubuntu desktop confused?"
date: 2006-06-28
forum: Desktop Environments
---

### Post by Physicist on 2006-06-28
:mad: 

I had an Ubuntu 6.06. then I installed almost all the available packages related to KDE in the Synaptic package manager, since I wanted to installed Kile, an IDE for tex typesetting which needs some KDE stuff which I wasn't sure what they exactly are(therefore I choosed to install all packages under category of KDE), then after I restart the system, it initially boot as before then at the last step a login window with a logo of Kubuntu come up and it fails if I try to login with my original login and password with my old Ubuntu. The behavior is it seems sort of accept my login and password is valid then it turns to a black screen for a couple of seconds then the blue Kubuntu login window come up again asking me to input my login and pasword. I can login with console login or failsafe session, but I don't have much intersting to do as logged on as such.

Now I just want to get back my old Ubuntu, how?

This is emergent since I have important work to finish with the laptop by midnight.

Piles of thanks in advance.

---

### Post by barisurum on 2006-06-28
On the login screen where you type your username n password there must be a session menu. Choose gnome in that menu n try to login.

---

### Post by Physicist on 2006-06-28
[QUOTE=barisurum]On the login screen where you type your username n password there must be a session menu. Choose gnome in that menu n try to login.[/QUOTE]

Thanks for reply.

In the blue Kubuntu login window, 
menu 
>session type 
>default 
  GNOME
  KDE
  failsafe

I tried all these types, 
default, GNOME and KDE give me the same behavior as I described above:
 become black screen for a couple of seconds then return back to the blue Kutuntu login window asking me to login

the failsafe session type bring me into the system while I don't have much useful things to do in such a mode.

---

### Post by Keith Hedger on 2006-07-22
I had a similer problem it turned out to be the ownership of my home folder had been changed to root, so just go into the failsafe shell and try "sudo chown -R XXX ZZZ" where XXX is your username/loginname and ZZZ is the path to your home folder usually /home/XXX

then logout of the shell and try again

hope this helps

---

