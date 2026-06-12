---
title: "Ubuntu Server with KDE -- stop loading kdm at start!!!!!!"
date: 2011-10-31
forum: Desktop Environments
---

### Post by cpsusie on 2011-10-31
Alright,
  
   I just downloaded and installed ubuntu server 11.10 64-bit on a virtual machine because I wanted to test setting it up in a vm before I go screwing up my current real installation.  My goals are:

    1) I want to have the KDE desktop environment installed with ONLY those applications and utilities I specifically install.

   2) I do NOT want it to load kdm UNLESS AND UNTIL I LOG IN TO TTY AND type "sudo service kdm start"

 Sorry about the shouting but this is really driving me crazy.  I installed ubuntu server.  Then I installed dkms, g++ and synaptic in that order.

  Then I installed kdm and kde-workspace and seemed to get the no-stuff installed experience I desire.  However, upon reboot I find that it starts kdm by default.  Now I have used linux for a while, but am not super dooper familiar with all the startup scripts and stuff.  Can someone please tell me how I make it stop loading kdm before instructed?

Thanks!
Chris

---

### Post by cpsusie on 2011-10-31
Bump!  Come on, somebody please help me.  In 10.10 it was easy as editing /etc/default/grub replacing "quiet splash" with "quiet splash text" in the following line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" but that didn't seem to help.  I've spent many hours trying to do something that should be very simple with no success and am very frustrated.  Any help would by much appreciated.

---

### Post by collisionystm on 2011-10-31
[http://ubuntuforums.org/showthread.php?t=1873016](http://ubuntuforums.org/showthread.php?t=1873016)

---

### Post by cpsusie on 2011-10-31
Sadly, that does not work.  That was one of the many things I tried last night.  Thanks for your help anyway.

---

### Post by azmyth on 2011-10-31
#update-rc.d -f gdm remove
or
$sudo update-rc.d -f gdm remove

Reboot and you should be taken to the command prompt without kdm, gdm, etc starting.

---

### Post by cpsusie on 2011-10-31
> **azmyth said:**
> #update-rc.d -f gdm remove
or
$sudo update-rc.d -f gdm remove

Reboot and you should be taken to the command prompt without kdm, gdm, etc starting.

Sadly, this does not work either.  That is why I am getting so po'ed.  There is absolutely no reason it should be this difficult.

---

### Post by haqking on 2011-10-31
things have changed in 11.10.  You need to use a .override file

see here from sisco [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

tailor to suit kde

---

### Post by cpsusie on 2011-10-31
> **haqking said:**
> things have changed in 11.10.  You need to use a .override file

see here from sisco [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

tailor to suit kde

OMG man, THANK YOU! THANK YOU! THANK YOU!

---

### Post by haqking on 2011-11-01
> **cpsusie said:**
> OMG man, THANK YOU! THANK YOU! THANK YOU!

no problem.  You are welcome.

Cheers

---

### Post by cpsusie on 2011-11-02
Just thought I'd post a little bit of follow up in case anyone else might be in my situation and need help.

When I added the kdm.override file with "manual" (no quotes) as its contents, the system did indeed boot into text mode and, if I wanted, could start kde with "sudo service kdm start".

This solution, however, had an unfortunate side effect: it prevented me from logging in remotely via xrdp, a facility I find most valuable (because it lets me log in without complications from windows and because rdp is much faster than vnc).  

I wasn't sure if this side effect was worth it especially since the kdm greeter offers an option to drop to console mode and you can just stop it with a "sudo service kdm stop" after logging in to the tty.  However, I found the following post:

> **sisco311 said:**
> Well, not a *real* kernel option, because it wasn't interpreted by the kernel. 

It was a *dirty hack* used by GDM's Upstart job to prevent GDM from running if the **text** parameter is present. Here is the relevant part of the code:
```

cat /etc/init/gdm.conf

# gdm - GNOME Display Manager
...
    # Check kernel command-line for inhibitors
     for ARG in $(cat /proc/cmdline)
     do
         case "${ARG}" in
             **text**|-s|s|S|single)
                 **exit 0**
                 ;;
         esac
     done
...

```
( find at: [http://ubuntuforums.org/showpost.php?p=11415280&postcount=17](http://ubuntuforums.org/showpost.php?p=11415280&postcount=17) )

Well, that old "dirty hack" is something beautiful.  I just pasted it into the kdm.conf file, edited grub to have "text" in it (just like in 10.10), got rid of kdm.override, uninstalled and reinstalled (with purging) vnc4server and xrdp, and voila -- everything works just the way I want it to.

(You might wonder why I wanted the command line by default since you can get all the command line goodness by a terminal along with GUI convenience in KDM -- primarily it is because in my experience text-mode linux almost never crashes.  If I leave KDE or gnome running for two weeks or so, invariably problems arise necessitating a restart.  So I'd rather just use the GUI when I want to.)

Hope this helps someone.  

Long live that dirty hack!!!!!! :)

---

