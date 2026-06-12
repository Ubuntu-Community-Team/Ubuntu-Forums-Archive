---
title: "Help with the administration options?"
date: 2006-01-13
forum: General Help
---

### Post by BitTorrentBuddha on 2006-01-13
ok, I tried to use the network gui, but after being prompted to enter my password, nothing opens, the same is true for the rest of the options under administration, can anybody help me?

---

### Post by BitTorrentBuddha on 2006-01-13
can somebody please help, I just installed today and I have no idea how to adjust my clock or access the networking gui

---

### Post by BitTorrentBuddha on 2006-01-13
bump :confused:

---

### Post by dcstar on 2006-01-13
[QUOTE=BitTorrentBuddha]ok, I tried to use the network gui, but after being prompted to enter my password, nothing opens, the same is true for the rest of the options under administration, can anybody help me?[/QUOTE]
Open a user terminal, and enter "su", and then your password, report the results.

---

### Post by BitTorrentBuddha on 2006-01-13
the input line changes to root@Ubuntu... so on and so forth, is there a way i can access the networking gui now that i have root command?

---

### Post by dcstar on 2006-01-13
[QUOTE=BitTorrentBuddha]the input line changes to root@Ubuntu... so on and so forth, is there a way i can access the networking gui now that i have root command?[/QUOTE]
That shows the root password is correct, and it is allowing you to log in.

Try gnome-nettool, select the LAN interface and then "Configure".

---

### Post by BitTorrentBuddha on 2006-01-13
:confused:  come again?
I just installed today, please take it nice and easy, I've been using windows for far too long

---

### Post by BitTorrentBuddha on 2006-01-13
ok, I entered nettool but it disabled the configure button :(

---

### Post by BitTorrentBuddha on 2006-01-13
I'm gonna try a fresh install, see if that fixes anything :( please post any information you might have, I'll come back and check it in the morning

---

### Post by Reveriee on 2006-01-14
I have the exact same problem! Do let me know if you manage to fix it! Thanks!

---

### Post by Reveriee on 2006-01-14
this is driving me crazy. i've reinstalled a couple of times already but it's still the same problem. help!!!

---

### Post by Reveriee on 2006-01-14
[B]> root@ubuntu:/home/reveriee# gnome-nettool

(gnome-nettool:1405): Gdk-WARNING **: locale not supported by Xlib

(gnome-nettool:1405): Gdk-WARNING **: cannot set locale modifiers

(gnome-nettool:1405): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-nettool:1405): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(network-admin:1411): Gdk-WARNING **: locale not supported by Xlib

(network-admin:1411): Gdk-WARNING **: cannot set locale modifiers

(network-admin:1411): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.[/B]

does this mean anything?

---

### Post by MJSOnline on 2006-01-14
I to have problems with the admin options.  Mine are the Disks option.  Can see or format my 2nd drive.

Anyone?
Matthew

---

### Post by NiceGuy on 2006-01-14
You could try this, first enable your root account by typing in a terminal window ```
sudo passwd root
``` and entering a root password (ref: [https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d]("https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d"))

then log out and log back in as root, then go to System > Administration > Users and Groups then click on your user name and click on properties and go to the User Privileges tab and ensure that all the check boxes are ticked (except 'Send and recieve faxes' and 'Use tape drives' - well thats how it is on my system).

Then you can if you wish, disable the root account again (as described in the wiki ([https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d]("https://wiki.ubuntu.com/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d"))


Let me know if this works!

---

### Post by NiceGuy on 2006-01-14
Oops, just realised you'll have to activate the root graphical login to do this (sorry, my bad)

To do this, type 'sudo su' and then 'gdmsetup', Click on the security tab and Check Allow root login



Edit: *sorry that was wrong, now correct*

---

### Post by MJSOnline on 2006-01-14
Hi NiceGuy.

Sorry to bother you, but can you take a look at my post, /root damaged, as I cant seem to get my head around it.

Thanks in advance.
Matthew

---

### Post by Reveriee on 2006-01-14
[QUOTE=NiceGuy]Oops, just realised you'll have to activate the root graphical login to do this (sorry, my bad)

To do this, type 'sudo su' and then 'gdmsetup', Click on the security tab and Check Allow root login



Edit: *sorry that was wrong, now correct*[/QUOTE]

when i follow this instructions, after typing gdmsetup, it says that i'll have to be root user to configure gdm... :/

---

### Post by NiceGuy on 2006-01-14
? what does it do when you type: sudo su ?

It 'should' change to look like: root@yourpc:/home/user

---

### Post by Reveriee on 2006-01-14
oh dear you're my saviour!!!

nothing happened when i did a sudo su so what i did was i logged out and in again.

then i went to terminal, typed 'su' and entered my root password (the one specified during installation).

and then 'gdmsetup'

followed your instructions, and now i'm logged in as root!!!

thanks a million! i hope this helps the others having the same problem too! thanks!

---

### Post by NiceGuy on 2006-01-14
Glad it worked, so have you gone to 'Users and Groups'? Were your users privileges setup correctly (ie. all checkboxes ticked)?

---

### Post by kosmic on 2006-01-14
Atention : using your computer as Root is a potenciall risk, you can make your system unbootalbe or by mistake install rootkits, do not use your workstation as root.

---

### Post by NiceGuy on 2006-01-14
[QUOTE=kosmic]Atention : using your computer as Root is a potenciall risk, you can make your system unbootalbe or by mistake install rootkits, do not use your workstation as root.[/QUOTE] I agree but I've found it easier to fix problems like this by using the root account BUT **don't use it as your user account!** To be really safe, disable it again when you've got your problem fixed!

---

### Post by Reveriee on 2006-01-14
[QUOTE=NiceGuy]I agree but I've found it easier to fix problems like this by using the root account BUT **don't use it as your user account!** To be really safe, disable it again when you've got your problem fixed![/QUOTE]

Will do! Thanks! Love you guys over here!

---

### Post by BitTorrentBuddha on 2006-01-14
Hey, A fresh install fixed my admin problem, but now I don't know what to put for IP, subnet, and gateway. Is it the same for each as I would find when executing the ipconfig /all command in windows?

---

### Post by BitTorrentBuddha on 2006-01-14
Can anybody help me?:confused:

---

### Post by NiceGuy on 2006-01-14
Urm, I'm not sure - I guess so...  try it! :D

---

### Post by NiceGuy on 2006-01-14
Sorry, that wasn't a very helpful reply :p 

I would think that the values should be the same as the ones in windows.

What exactly is the problem? Can you not access the internet/your network?

are you behind a router or connecting via a modem?

are you using dialup or broadband?

---

### Post by BitTorrentBuddha on 2006-01-14
I'm using a Trendnet TEW-445PI PCI card to try and access my wireless router. The values from ipconfig /all didn't work and when I try to access the internet in either gaim or firefox, I don't have any connection at all.

---

### Post by slimsam1 on 2006-01-14
You should use a unique IP address for each system on the network, but the DNS and gateway and subnet can probably be set to the same as your windows computer.

If the windows machine's IP is 192.168.1.2, then set your Ubuntu machine's IP to something unique but sharing the same first three sets of digits. For example, 192.168.1.5

(Just realized you are using wireless... could be a more low-level problem like making the card work at all..)

---

### Post by NiceGuy on 2006-01-14
Have you tried setting your wireless card to use DHCP? (ie. let your router assign your IP etc)

System > Administration > Networking, click on your wireless card, (make sure its activated - if not click activate) then click properties. Ensure 'enable this connection' check box is ticked and change 'Configuration' to DHCP

---

### Post by BitTorrentBuddha on 2006-01-14
Thanks a million for that DHCP tip, that got it up and running and I think that I can finally start using my new PC!:D

---

### Post by NiceGuy on 2006-01-14
Glad to help! :D

---

