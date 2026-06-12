---
title: "Howto start stop services"
date: 2005-04-14
forum: Desktop Environments
---

### Post by anando on 2005-04-14
Hi 

I just installed Ubuntu 5.4 - it looks grea so far (apart from the RealPlayer issue, I have not had any serious problems). However, now I would like to look at the services that are running on my computer and enable/disable them ... is there a tool for doing this on Ubuntu ?

On Fedora 3 (my previous bloated distro). I could go to menu->system->services (or something like that) and browse through all the services. 

Any help will be greatly appreciated. I am not an expert - so if you explain in detail :) it will be very nice.

Thanks,
Anand.

---

### Post by Gandalf on 2005-04-14
[QUOTE=anando]Hi 

I just installed Ubuntu 5.4 - it looks grea so far (apart from the RealPlayer issue, I have not had any serious problems). However, now I would like to look at the services that are running on my computer and enable/disable them ... is there a tool for doing this on Ubuntu ?

On Fedora 3 (my previous bloated distro). I could go to menu->system->services (or something like that) and browse through all the services. 

Any help will be greatly appreciated. I am not an expert - so if you explain in detail :) it will be very nice.

Thanks,
Anand.[/QUOTE]
 the services that runs are in /etc/rcX.d folder (where X is 0 -> 6)
to add a service (services must be in /etc/init.d folder
sudo update-rc.d nameoftheservice defaults
to remove it
sudo update-rc.d nameoftheservice remove

to customise it, man update-rc.d and read what is writen there

---

### Post by luca_linux on 2005-04-14
The wpa_supplicant service automatically starts on my box.
But then I have to type this command at the console when I log in:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
In which script file should I add this line to get it automatically starting?

---

### Post by Gandalf on 2005-04-14
[QUOTE=luca_linux]The wpa_supplicant service automatically starts on my box.
But then I have to type this command at the console when I log in:
```
sudo wpa_supplicant -B -i eth1 -c /etc/wpa_supplicant.conf -D ipw -w -dd
```
In which script file should I add this line to get it automatically starting?[/QUOTE]
 well try putting it in /etc/init.d/the_script_that_turn_wpa_service_on in the start section, or create yours (same template with start and stop etc...) and update-rc.d it

---

### Post by yanik on 2005-04-14
to start or stop services under any debian based distro;

get the name of the service you want to start or stop

```
ls /etc/init.d
```
then
```
sudo invoke-rc.d servicename start|stop
```
which is only a shortcut to 
```

sudo /etc/init.d/servicename start|stop
```

---

### Post by Gandalf on 2005-04-14
[QUOTE=yanik]to start or stop services under any debian based distro;

get the name of the service you want to start or stop

```
ls /etc/init.d
```
then
```
sudo invoke-rc.d servicename start|stop
```
which is only a shortcut to 
```

sudo /etc/init.d/servicename start|stop
```[/QUOTE]
 yes but he's not talking about starting stoping it after boot, but during boot!

---

### Post by yanik on 2005-04-14
oups, I didn't actually read his post, only the title (Howto start stop services).

I should've RTFP :)

Yanik

---

### Post by speedman on 2005-04-14
It's worth noting that update-rc.d is primarily intended to be a devloper tool for usage in scripts.  When a service is removed with update-rc.d the next time an upgrade comes down for the daemon the default startup symlinks will be automatically restored.

If you want to use:

update-rc.d -f <service_name> remove

... and you want the results to be permanent you should also add a K symlink to /etc/rc2.d/ or /etc/rcS.d/, which will prevent upgrades from putting the default startup symlinks back in place.

Example ... to prevent mdadm (RAID monitoring daemon) from starting on boot:

sudo update-rc.d -f mdadm remove

And to prevent any upgrades to the mdadm daemon from re-enabling the daemon on boot:

sudo ln -s /etc/init.d/mdadm /etc/rc2.d/K99mdadm

Instead of using update-rc.d it is probably better for most users to utilize the console app rcconf, which will insert the proper K symlinks when removing a service from starting automatically on boot.

sudo apt-get install rcconf

Then ...

sudo rcconf

... in a term to use this run level config tool.


Regards,

SM

---

### Post by yanik on 2005-04-14
I didn't know, very interesting.

thanks speedman

---

### Post by Glanz on 2005-04-14
"Allez voir vos députés et dites leurs que notre gouvernement doit arreter de payer pour des liscences de Microsoft."
Impossible, ils sont un tas de twits. Ils n'écoutent que le froissement des billets dans leur poches.

Also you should check "man update-rcconf-guide" after installation of rcconf.

---

### Post by jerome bettis on 2005-04-14
the easiest way (my opinion) to do all this is to use this nice little app here.

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

very simple

---

### Post by Roberto Rosselli on 2005-04-15
[QUOTE=jerome bettis]the easiest way (my opinion) to do all this is to use this nice little app here.

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

very simple[/QUOTE]
 But wasn't there a "services-admin" application in the gnome-system-tools package? How comes it is not included in Ubuntu (the app, not the package which seems to be installed).

CIao

---

### Post by speedman on 2005-04-15
Good point Roberto.  The upstream version of GST does include a run level editor for configuring whether daemons launch on boot, or not.

[http://www.gnome.org/projects/gst/](http://www.gnome.org/projects/gst/)


Regards,

SM

---

### Post by Glanz on 2005-04-15
[QUOTE=jerome bettis]the easiest way (my opinion) to do all this is to use this nice little app here.

sudo apt-get install sysv-rc-conf
sudo sysv-rc-conf

very simple[/QUOTE]
 That's "rcconf" and not "rc-conf"...

---

### Post by yanik on 2005-04-15
[QUOTE=Glanz]That's "rcconf" and not "rc-conf"...[/QUOTE]

You're wrong, Jerome is right.

Yanik

---

### Post by yanik on 2005-04-15
oups, actually, you're both right.  But sysv-rc-conf is easier to use IMHO.

---

### Post by Glanz on 2005-04-15
[QUOTE=yanik]You're wrong, Jerome is right.

Yanik[/QUOTE]
**OMG**!!!!! I was wrong.... everyone else was right!:-#
It seems to me that the "sysv-" wasn't there when I first read that post. All I saw was "rc-conf"... Either I am getting old, or I am totally bonkers...., or perhaps both.:grin:

---

### Post by Rohan on 2005-04-15
hmm.. if I want to stop, start, or restart a service and I know the name of it.. i use wajig

apt-get install wajig

then if you want to say start apache.. do

wajig start apache

---

### Post by ACK!! on 2005-04-15
[QUOTE=speedman]Good point Roberto.  The upstream version of GST does include a run level editor for configuring whether daemons launch on boot, or not.

[http://www.gnome.org/projects/gst/](http://www.gnome.org/projects/gst/)


Regards,

SM[/QUOTE]

Upstream version has two tools that are not included with Ubuntu.

It has a boot-admin for setting grub/lilo options and it has the runlevel-admin to start/stop and set the runlevel of various services.

I am not sure why.  

I think at the very least the run-level admin would make a fine edition.

---

### Post by speedman on 2005-04-15
[QUOTE=ACK!!]Upstream version has two tools that are not included with Ubuntu.

It has a boot-admin for setting grub/lilo options and it has the runlevel-admin to start/stop and set the runlevel of various services.[/QUOTE]

Interestingly the Sid package for GST has the boot admin app, but not the run level one:

[http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-system-tools&version=unstable&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-system-tools&version=unstable&arch=i386)


Regards,

SM


EDIT - fixed a typo.

---

### Post by anando on 2005-04-17
Thanks every one - and especially you SM !! Wonderful forum.

- Anando.

---

### Post by saltydog on 2005-04-27
[QUOTE=speedman]

update-rc.d -f <service_name> remove


SM[/QUOTE]

If you need to change init configuration, you can use Ubuntu Bootup Manager:
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

### Post by Gandalf on 2005-04-27
[QUOTE=saltydog]If you need to change init configuration, you can use Ubuntu Bootup Manager:
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)[/QUOTE]
 really nice proggy
thanks

---

### Post by kamstrup on 2005-04-27
[QUOTE=speedman]Interestingly the Sid package for GST has the boot admin app, but not the run level one:

[http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-system-tools&version=unstable&arch=i386](http://packages.debian.org/cgi-bin/search_contents.pl?searchmode=filelist&word=gnome-system-tools&version=unstable&arch=i386)[/QUOTE]

There are problems with Debian compatibility with a few of the GST apps. Runlevel and Bootadmin are among these. There was a long thread about this somewhere... Let me see... Here!

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271859](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=271859)

Sad reading... :´-( I'd really (like *really REALLY*) love to see a graphical service/runlevel editor in Ubuntu..

---

### Post by kamstrup on 2005-04-27
[QUOTE=saltydog]If you need to change init configuration, you can use Ubuntu Bootup Manager:
[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)[/QUOTE]

WOW! That is a *great* app! -- Assuming it is working :D - I haven't rebooted yet.

You might want to suggest it for Breezy..?

---

### Post by seven on 2005-04-27
you can manage services with sysv-rc-conf
install it:
> 
sudo apt-get install sysv-rc-conf

and run it
> 
sudo sysv-rc-conf


enjoy :)

---

### Post by kamstrup on 2005-04-27
Question: Is it safe to turn of lvm and evms? It has always seemed extremely weird to me that raid-stuff was running by default. Especially since EVMS is taking quite some time to start during boot. 

How many ordinary users use raids? I have yet to meet one!

EDIT: Why does lvm and evms not show up in UbuntuBootManager, only in sysv-rc-conf?

---

### Post by kamstrup on 2005-04-27
[QUOTE=kamstrup]Question: Is it safe to turn of lvm and evms? It has always seemed extremely weird to me that raid-stuff was running by default. Especially since EVMS is taking quite some time to start during boot. 

How many ordinary users use raids? I have yet to meet one![/QUOTE]

EDIT: Why does lvm and evms not show up in UbuntuBootManager, only in sysv-rc-conf?

---

### Post by speedman on 2005-04-27
[QUOTE=kamstrup]Why does lvm and evms not show up in UbuntuBootManager, only in sysv-rc-conf?[/QUOTE]

Perhaps UbuntuBootManager only picks up symlinks in /etc/rc2.d/ - I haven't looked at the app.  evms, lvm and mdadm-raid are started from /etc/rcS.d/.


Regards,

SM

---

### Post by kamstrup on 2005-04-27
Yes, but can I disable them without destroying my system. My girlfriend will go nuts if I am "fixing" it again :)

---

### Post by saltydog on 2005-04-27
[QUOTE=speedman]Perhaps UbuntuBootManager only picks up symlinks in /etc/rc2.d/ [/QUOTE]


Correct. As it is for Ubuntu (and not generally for Debian) it only picks up those services that are "up" in runlevel 2-3-4-5 and "down" in runlevel 0-1

From debian-policy manual, anyway, it is STRONGLY recommended not to play with symlinks in rcS.d unless you really know what are you doing. They are main scipts to let the system start...

---

### Post by saltydog on 2005-05-01
I have now added capability to manage also scripts in rcS.d directory.
New version 1.2.5 is online:

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)

---

### Post by aledie on 2005-07-14
[QUOTE=saltydog]I have now added capability to manage also scripts in rcS.d directory.
New version 1.2.5 is online:

[http://www.marzocca.net/linux/ubm.html](http://www.marzocca.net/linux/ubm.html)[/QUOTE]


There is a new version of the software, 1.3.5. Also the name changed to BUM. You can find at: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

It was also mentioned in Unofficial Ubuntu 5.04 Starter Guide, 
Q: How to install Boot-Up Manager (BUM)?

But the link is to old to an older version. To install the version mentioned above:

wget [http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb](http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb)
sudo dpkg -i bum_1.3.1-1_all.deb

---

### Post by Hamman on 2005-07-22
[QUOTE=aledie]There is a new version of the software, 1.3.5. Also the name changed to BUM. You can find at: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

It was also mentioned in Unofficial Ubuntu 5.04 Starter Guide, 
Q: How to install Boot-Up Manager (BUM)?

But the link is to old to an older version. To install the version mentioned above:

wget [http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb](http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb)
sudo dpkg -i bum_1.3.1-1_all.deb[/QUOTE]

Very nice program, using the latest version right now, and it's about 100 times better than services.msc in Windows :). 
I might as well sneak in a question: If I don't have any RAID-devices, is it safe to disable the mdadm service? What about lvm, evms and pppd-dns under "Startup Scripts"?

---

### Post by doc_holiday on 2005-07-29
[QUOTE=aledie]There is a new version of the software, 1.3.5. Also the name changed to BUM. You can find at: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

It was also mentioned in Unofficial Ubuntu 5.04 Starter Guide, 
Q: How to install Boot-Up Manager (BUM)?

But the link is to old to an older version. To install the version mentioned above:

wget [http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb](http://www.marzocca.net/linux/downloads/bum_1.3.1-1_all.deb)
sudo dpkg -i bum_1.3.1-1_all.deb[/QUOTE]
very nice programm 
tnx

---

### Post by ACK!! on 2005-07-29
The Ubuntu Boot Manager is very nice. 


It is unfortunate that services tool in GST has a bug because I love the idea of having as many of these tools that are distro independant (not just good for us but also Slack and Gentoo and others).  One of the greatest problems for linux is that so many admin tools are very distro specific.  

Kudos to the community and especially the author of this tool.

---

### Post by Jade Robbins on 2005-07-29
[QUOTE=anando]Hi 

I just installed Ubuntu 5.4 - it looks grea so far (apart from the RealPlayer issue, I have not had any serious problems). However, now I would like to look at the services that are running on my computer and enable/disable them ... is there a tool for doing this on Ubuntu ?

On Fedora 3 (my previous bloated distro). I could go to menu->system->services (or something like that) and browse through all the services. 

Any help will be greatly appreciated. I am not an expert - so if you explain in detail :) it will be very nice.

Thanks,
Anand.[/QUOTE]
 Anando if you read the forum rules you are not supposed to ask questions here. Please ask them in the appropriate forum.

---

### Post by poofyhairguy on 2005-07-29
This thread was very sneaky.

Come on people- please don't answer questions in the how to section. Lets not reward people for breaking the rules.

---

