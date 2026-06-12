---
title: "Installing hardware drivers from the command line?"
date: 2009-02-18
forum: General Help
---

### Post by rodney cross on 2009-02-18
Hello,

I didn't know which forum to post in, because I'm not sure of the nature of my problem, so please excuse me if this is missplaced.

This morning I turned on my laptop (Fujitsu-Siemens Amilo) and booted up Kubuntu (running Hardy).  I logged in to find that it would hang every time I asked it to do anything; e.g. I could open a terminal window, but the response to 'ls' might be anything up to 30 seconds.  It will open Firefox, but randomly hang.

Instead of the continual chuntering of a healthy thinking machine, I hear two very short period bursts of processing when I ask it to do anything.  Booting up in safe mode worked fine, and I managed to create backups of my files.  Booting up to my windows partition works as well as it ever did, so I guess the hardware's still ok.

I have no error messages, so it's difficult to search for help.  The only two clues I can offer to help your diagnoses are that

1) An icon I've never seen before popped up this morning telling me there were new hardware drivers to install.  It wanted me to run jockey-kde, but it crashes whenever I try to. I can't run 'jockey-kde' from the command line in recovery mode.

2) Yesterday I updated some package with HAL in the title using adept updater, which google informs me might be relevant.

As you can probably tell I'm no Linux expert.  I guess I need to find out what these updated drivers are and how to install them from the command line, but I don't know how to go about doing that.

Many thanks,

Rodney

---

### Post by rodney cross on 2009-02-18
OK, my first post was a bit lacking in details.  Trouble is I'm not sure what I should be telling you.  Here's more info on point 2:

Re: 2)  According to /var/log/dpkg.log adept installed the following packages yesterday:

hal-info 20081124-0ubuntu1~hardy
libpq5 8.3.6-0ubuntu8.04
libc6 2.7-10ubuntu4

I'm running:

Ubuntu 8.04.02 kernel 2.6.24-23-generic

according to /boot/grub/menu.lst.  Someone told me I should expect the suffix '2.7-10ubuntu3' in the libc6 package.  Could this be the source of my problems?

Many thanks,

Rodney

---

### Post by rodney cross on 2009-02-18
Aha!  Problem solved.  I'll recount my steps here so that (a) any one with the same problem might find the solution and (b) so that you can suggest how I might have better asked the initial question.

Following some advice from another forum I tried to update my system with:

sudo apt-get update

which produced the following errors:

Reading package lists... Error!
E: Read error - read (5 Input/output error)
E: The package lists or status file could not be parsed or opened.

As it suggests here [(link)]("http://ubuntuforums.org/archive/index.php/t-197407.html") I ran

sudo dpkg --configure -a

which produced the message:

dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error

Then these guys [(link)]("http://www.linuxquestions.org/questions/debian-26/aptdpkg-errors-varlibdpkgstatus-155478/") explain that the file /var/lib/dpkg/status might be corrupted (it wouldn't open with emacs for example) and should be replaced by /var/lib/dpkg/status-old.  Then I ran

sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get install
sudo apt-get autoremove

following this [(link)]("http://kubuntuforums.net/forums/index.php?topic=3098388.0") advice) and rebooted.  I don't know if all of the previous steps are necessary but they seemed to have alleviated my problems.

Comments are welcomed.  In particular, why does adept throwing a paddy make my entire system break?

CDR

---

