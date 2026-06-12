---
title: "Login/Username"
date: 2009-03-31
forum: General Help
---

### Post by netside on 2009-03-31
I was never prompted to enter a password or login when installing Ubunto.  It boots to the login (GUI) screen fine (where I can enter my login and password), but I have no idea what the username is.  I already changed the password to "Root" using the sudo method... but I have no idea how to obtain or change the login/username.  I'm really new to linux, so I have no idea what to do.  Can somebody please assist me with changing or locating the username so that I can login, preferebly *step-by-step*?  Any help would be greatly appreciated, thanks.  I'm really looking forward to Ubuntu... but I guess I've run into some obstacles.  Is there anyways to just disable login security altogether?  Thanks again.   

PS - I already tried default usernames on the web that I thought might work such as "oem" "ubuntu" and "user" as login/usernames... but without any luck.  Please help! :)

---

### Post by kanikilu on 2009-03-31
Seems to be a lot of this going around lately...not sure how since of the dozen or so installations I've done, I've never *not* been able to install without setting up an initial username and password.

Anyways...check out this guide to reset it:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by coffeecat on 2009-03-31
If you used the live CD to install, you would have seen this page:

[IMG]http://news.softpedia.com/images/extra/LINUX/large/ubuntu804installationguide-large_008.png[/IMG]

Like kanikulu I've done dozens of Ubuntu installs and I know no way of skipping this page. If you saw this, this is where you entered your username and password. If you didn't, I really don't know what's going on.

**Edit:** in case you need to reinstall, [here's the softpedia howto](http://news.softpedia.com/news/Installing-Ubuntu-8-04-LTS-84314.shtml) for installing 8.04 from which that image came. The 8.10 installer is similar, with a nicer-looking partitioner.

---

### Post by kanikilu on 2009-03-31
To think of it, no only have I done numerous installs, but I've done it pretty much every way you can - from the Live CD, from the alternate CD, server CD, and Wubi. All require an initial username/password...

---

### Post by SikEnCide on 2009-03-31
> **kanikilu said:**
> Seems to be a lot of this going around lately...not sure how since of the dozen or so installations I've done, I've never *not* been able to install without setting up an initial username and password.

Anyways...check out this guide to reset it:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

The directions written above are the way to correct the issue.

It does however show an inherent flaw with ubuntu and that is the fact that it never has you create a root password. Meaning that anyone could login to your system in recovery mode. Drop to root and create a username with admin privileges or change you password.

Also as mentioned before I have never seen an install where it does not ask for this info even using an alternate iso it still prompts for this.

---

### Post by coffeecat on 2009-03-31
> **SikEnCide said:**
> It does however show an inherent flaw with ubuntu and that is the fact that it never has you create a root password. Meaning that anyone could login to your system in recovery mode. Drop to root and create a username with admin privileges or change you password.

Sorry I just have to pick you up on this. This 'flaw' as you call it is nothing to do with Ubuntu's root policy. (Which, incidentally, [makes a lot of sense]("https://help.ubuntu.com/community/RootSudo").) This 'flaw' is true of any operating system, Linux or otherwise. Boot up in single/recovery mode in Fedora, or Suse or whichever distro you choose, and you can do whatever damage you want.

There is an old adage in the computer security world. If there is physical access to your machine, there is no security at all.

---

### Post by kanikilu on 2009-03-31
Indeed. Also, kind of off-topic, but with the right tools and enough time, Windows is not immune, check out the Ophcrack live cd. If you have a weak password, the job is made especially easy ;)

---

### Post by netside on 2009-04-01
I never even saw that message... the install seemed to automatically go on it's own without asking me for anything.

---

### Post by netside on 2009-04-01
The problem now that I'm having is, it won't let me drop to the root shell prompt without a password.  And, the one I changed it to (root), doesn't work.  I have no idea what to do... I'm pretty much locked out of the operating system altogether.   It's getting *uber* frustrating.  Any other ideas? :(

---

### Post by mcduck on 2009-04-01
> **netside said:**
> I never even saw that message... the install seemed to automatically go on it's own without asking me for anything.

Are you sure you didn't use the "Install in OEM mode" option? (it's available on the Alternate-CD at least, might be on the normal install CD as well these days..)

If you did that, then your installation isn't finished yet. The OEM install is for companies and computer shops who wish to sell computers with Ubuntu pre-installed. It's not something a normal user would ever need.

If you did do OEM install, the user name is "oem" and if I remember right the password it either "oem" or empty. Use those to log in, open a terminal and run "sudo oem-config-prepare" to finish the installation. Then boot the machine, and it will ask you to create the actual user for the machine and set the time zones  etc. options (this is what a person who bought the machine with Ubuntu pre-installed would see the first time he starts the system).

edit: A bit old walkthrough for OEM install on Ubuntu 6.06: [https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview]("https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview")

---

### Post by coffeecat on 2009-04-01
> **netside said:**
>   Any other ideas? :(

Yes. Reinstall. An installation takes about 20-30 minutes. You have a system which has never worked and you've probably spent more than an hour on it.

But this time, use the live desktop CD, **not** the alternate CD (if that's what you used), and as the last poster points out, don't use the OEM mode (if indeed it's available on the live CD). If you use the live CD, you **will** see the password screen that I posted earlier.

Promise. :p

---

### Post by bodhi.zazen on 2009-04-01
> **netside said:**
> The problem now that I'm having is, it won't let me drop to the root shell prompt without a password.  And, the one I changed it to (root), doesn't work.  I have no idea what to do... I'm pretty much locked out of the operating system altogether.   It's getting *uber* frustrating.  Any other ideas? :(

Well it sounds as if some of this is a combination of your own doing and/or forgetting passwords.

Yes, boot a live CD

Mount your Ubuntu root partition to /mnt

```
sudo chroot /mnt

# obtain your user name if needed
ls /home

# set password
passwd <insert_user_name_here>

#lock root account 
usermod --lock root
```While you are at it, I suggest you disable the root account as I outlined.

---

