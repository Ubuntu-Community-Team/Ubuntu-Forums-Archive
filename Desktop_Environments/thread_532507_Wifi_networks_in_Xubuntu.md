---
title: "Wifi networks in Xubuntu"
date: 2007-08-22
forum: Desktop Environments
---

### Post by cudds on 2007-08-22
I used to run Kubuntu but I felt like a change so I got rid of that partition and ran Wubi to give me Xubuntu (I won't bore you with the problems I'm having with GRUB!)

The problem is I don't have access to a wired network at the mo so all must go through me wifi 
Now in Kbunutu there was this fancy lil KDE tool that showed me all the networks it saw - I could the connect to my WPA and surf.

The thing with Xbunutu is I can't see my wifi networks - there's a network program but that is asking me to enter in the ESID and the WEP password. I can see from synaptics I have some sort of support for WPA but I can't see how to use it, nor can I see how to scan for available networks.

My ath0 is up and running as far as I can see.

Advice greatfully received.

---

### Post by jimrz on 2007-08-22
> **cudds said:**
> I used to run Kubuntu but I felt like a change so I got rid of that partition and ran Wubi to give me Xubuntu (I won't bore you with the problems I'm having with GRUB!)

The problem is I don't have access to a wired network at the mo so all must go through me wifi 
Now in Kbunutu there was this fancy lil KDE tool that showed me all the networks it saw - I could the connect to my WPA and surf.

The thing with Xbunutu is I can't see my wifi networks - there's a network program but that is asking me to enter in the ESID and the WEP password. I can see from synaptics I have some sort of support for WPA but I can't see how to use it, nor can I see how to scan for available networks.

My ath0 is up and running as far as I can see.

Advice greatfully received.

probably the easiest solution would be to install (from synaptic) network-manager and network-manager-gnome, which will allow wpa and does not bring with it nearly as many additional libs as the kde one you are used to when installing to xubuntu. you might also look into "wifi radar" as another possible solution.

---

### Post by cudds on 2007-08-23
> **jimrz said:**
> probably the easiest solution would be to install (from synaptic) network-manager and network-manager-gnome, which will allow wpa and does not bring with it nearly as many additional libs as the kde one you are used to when installing to xubuntu. you might also look into "wifi radar" as another possible solution.

Thanks for the tips - the problem is I don't have a net connection other than my windows boot until I get this sorted - is there a way I can download the debs for this and move them across?

---

### Post by jimrz on 2007-08-23
> **cudds said:**
> Thanks for the tips - the problem is I don't have a net connection other than my windows boot until I get this sorted - is there a way I can download the debs for this and move them across?

you can find them [[COLOR="Sienna"]**_here_**[/COLOR]]("http://packages.ubuntu.com/")

---

### Post by cudds on 2007-08-24
safe - got it all on guys - thanks
The only problem I now have as a newbie it where is the network-manager :(

I've looked over all the menus I can't find it.

Do i need to run the gnome thingy?

---

### Post by ugm6hr on 2007-08-24
This might help with Network Manager:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

The other (and my now preferred option) is to use Wicd (see my signature link).  You will have to uninstall Network Manager to use Wicd.

---

### Post by cudds on 2007-08-24
> **ugm6hr said:**
> This might help with Network Manager:
[http://ubuntuforums.org/showthread.php?t=448952](http://ubuntuforums.org/showthread.php?t=448952)

The other (and my now preferred option) is to use Wicd (see my signature link).  You will have to uninstall Network Manager to use Wicd.

Sweet - that thread is really useful.
Should I run it as a session to make it run without holding a terminal open? How can I get it to run without staying there in a terminal?

Does Wicd have then? Will that solve all those mental icon problem?

---

### Post by ugm6hr on 2007-08-25
> **cudds said:**
> Sweet - that thread is really useful.
Should I run it as a session to make it run without holding a terminal open? How can I get it to run without staying there in a terminal?

Does Wicd have then? Will that solve all those mental icon problem?

Wicd will just work.  No problems with multiple icons!  And more stable from my viewpoint, as well as requiring less resources (NM is very Gnome dependent).

---

