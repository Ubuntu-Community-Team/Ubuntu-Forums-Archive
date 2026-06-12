---
title: "problems with kubuntu install"
date: 2008-01-30
forum: Desktop Environments
---

### Post by sleeper414 on 2008-01-30
hi, im relatively new to ubuntu, but recently installed xubuntu,sharing the environment with ubuntu.
so, feelling adventorus, i decided to install kubuntu as well. in order to learn how they all work.

it failed to install, and now my hard drive is full...ok thats a whole other issue.

the main issue im concerned with right now is that when i go to synaptic package manager,to uninstall xubuntu, and kubuntu.

i get this error message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


?????

like i said, im relatively new, i understand everything but the terminal scares me.

help. thanks

---

### Post by DMK62 on 2008-01-30
The terminal can be a bit scary at first. Make sure that Synaptic is closed and open Terminal and enter

sudo dpkg --configure -a 

It may take a while to finish, be patient. After that enter the following commands.

sudo apt-get update

sudo apt-get upgrade

sudo apt-get clean

After a while you will become more comfortable with the terminal. If you have any questions about its use or the command then just post here on the forums for help.

Dale

---

### Post by sleeper414 on 2008-01-30
thank you dale, that seems easy enough.
but, remember in the post where  i said my ubuntu hard drive was outta space?
i dont get it..it says its only 6.5 gigs...its bigger than that!

so, if i were to goto terminal and get these items...where would they go if there is no room?

---

### Post by sleeper414 on 2008-01-30
ok i tired going into terminal, and typing in sodu dpkg--configure-a

it says command not found.

i really REALLY dont want to reinstall ubuntu. there has got to be a way to fix this

---

### Post by DMK62 on 2008-01-30
Sorry but from other posts I was not able to determine exactly how your system partitions are configured.

Is that 6.5 gigs of total space or 6.5 gigs of free space ? Installing additional DE's like Kubuntu can eat up hard drive space fast, Kubuntu-desktop uses up over 700 megs. I don't have access to Ubuntu right now but try checking Applications>Accessories>Disk Usage Analyzer . It has a gui and lets you view information about the partitions on your computer. 

Running the commands given will place the updated files onto the partition that is used for Ubuntu. 

Dale

The command has to be exact , sudo dpkg --configure -a and not sodu dpkg--configure-a

---

### Post by sleeper414 on 2008-01-30
dave thanks. somtimes i tend to get so worked up that i should walk away for a few minutes...it seems to be working now.
the hard drive is 6.5 gigs total, i ran apt-get-clean and it freed up about 300 mgs of space.

if this works, i will simply remove all other desktop environments other than gnome.

thanks again.

---

### Post by sleeper414 on 2008-01-30
well looks like this solved the problem...im going to go snooping for terminal commands.
it seems pretty straight foward..its more about the basic understanding of the terms used.


thanks alot [solved]

---

