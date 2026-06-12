---
title: "Gnome Power Manager configuration settings not installed correctly"
date: 2011-03-08
forum: Desktop Environments
---

### Post by luciferactual on 2011-03-08
Edit:* I would just like to say I never repaired this issue, rather I backed up my data via command line and reformatted, going with 10.10. I still would like to know why my hard drive appeared to be filled to capacity, but I'll leave this post up in case some one else has the same issue and resolves it. *

Ubuntu 10.4 x64
Heres the deal: Hard Drives is a 255gig, seems full even though I only had 50 gigs of data. I can not access the gui, it says on the log in page.. 
"***gnome power manager configuration settings are installed incorrectly***"
And it just brings back to the login page when I attempt to log in.

However, I do have command line access. I'm the admin and I can not repair this issue as of today. What I have tried is host of suggestion (summarized below ) from forums;

.apt-get --reinstall install gnome power-manager
.sudo apt-get clean, autoclean, upgrade, 
.sudo apt-get --reinstall install ubuntu-desktop
.chmod /tmp to 0777 
.sudo dpkg --configure -a
.mkdir /var/lib/gconf.defualt
.mv .gconfd/saved_state saved_state.old
.sudo dkpg-reconfigure gnome-power-manager
.sudo apt-get remove/install  powermgmt-base 

None of these worked.

My users accounts are encrypted so I can not livecd the data out. I can't seem to mount an external hard drive in command line properly - the external drive does not report in fstab so I have no destination for the cp -r command. I'm at my wits end and I need to recover this data and find out why my 255gig hard drive filled up almost over night with out me knowing.

Also, I *du -h* on the user accounts and the data was no more than 50 gigs total.

Any help would be appreciated

---

### Post by jon47 on 2011-12-05
This is a belated answer, but I'm posting it just in case anyone finds this unanswered question via Google like I did.

The cause is most likely that your root filesystem is full, resulting in something in Gnome failing to create a test file in /tmp, resulting in this unhelpful error message.

(a) check that /tmp has the right permissions, just in case something's broken it - it should be rwxrwxrwxt - if it's not, then do
  sudo chmod a+rwxt /tmp
(b) check whether your root filesystem has any space left
  df -h /
you're looking for some reasonable space free under "Avail".  If it's not, then the obvious places to look for garbage are in /tmp and /var/tmp - after that it's hard to point you in the right places.  du -sh * will give you a disk usage summary (s) in human-readable form (h) of all the files in the current directory.

Hope this helps someone in the future...

Cheers
Jon

---

### Post by frilgtate on 2013-04-27
So, Jon, how does one recognise which items may be "garbage", and then how can they be deleted from there?
Before I started having this problem I was getting warnings about filesystem root getting full, but I couldn't figure out how to find filesystem root, or I think I did manage to find it once and couldn't figure out what would be safe to delete from there vs. what would be essential.

---

### Post by oldos2er on 2013-04-27
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

