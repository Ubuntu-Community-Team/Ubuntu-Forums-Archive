---
title: "How to fix pam.d??"
date: 2009-03-08
forum: General Help
---

### Post by humphreybc on 2009-03-08
Hi,

I was fiddling around with the common-auth file under pam.d trying to get my fingerprint reader to work, following [these instructions.]("http://knowledge76.com/index.php/Fingerprint_Reader_Usage")

Because

auth	 requisite	 pam_unix.so nullok_secure
auth	 optional	 pam_smbpass.so migrate missingok

Wasn't there in the first place, I added in what you're meant to change it to. I saved it and then went to start up package manager sometime later and found that after entering my password it wouldn't start. Then I tried starting up root terminal, entered my password and again wouldn't work. I went to take out what I put in but I think I took out too much and now every time I enter my password it says invalid password even though it's correct!!!

Is there a way to "restore" this PAM thing back to default? Thankyou

---

### Post by humphreybc on 2009-03-08
Well I found the original common-auth file on the internet, and I have seen the missing line that I need to add that I deleted by accident - but when I add it in and click save it tells me I don't have permission to save this file!!

My current common-auth:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

and then what it SHOULD be:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth	optional	pam_ecryptfs.so unwrap
# end of pam-auth-update config
```

Note that the line that is missing is:

```
auth	optional	pam_ecryptfs.so unwrap
```

But when I try to add that missing line it and save the document, I get:

> Could not save the file /etc/pam.d/common-auth.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

I have tried logging in as root following [these instructions]("http://www.sizlopedia.com/2008/04/16/how-to-login-to-ubuntu-as-root-user/") but it gives me a wrong password error when it asks for the password for my account.

It's a vicious cycle, The file I need to edit to fix the problem is preventing me from fixing the problem!

---

### Post by lindsay7 on 2009-03-08
Have you tried sudu su to add the line

---

### Post by lindsay7 on 2009-03-08
I found this on another post, there is something her about making a change to set up a password free setup. See the MAN page for help.



Re: How to remove PAM, pam.d and all this CANCER? 
Hi there,

This thread doesn't seem to have anything to do with accessibility.  Your posts may be answered more quickly if you put them in the right place.

I don't want to get tangled up in a religious war, so I'll pass discreetly over your issues with PAM, resolvconf, etc. (although I am curious about what you would put in avahi's place). I suspect though that, compared to Gentoo, a great many Ubuntu users simply won't care enough to feel particularly motivated about the PAM debate.

Incidentally, running sudo passwordlessly is a matter of adding a single line to /etc/sudoers. The man page for sudoers will help you there.

---

### Post by humphreybc on 2009-03-08
How do I use "sudo su" ? I have used sudo and it prompts me for my password but then it just says "sorry, try again"

It's almost impossible to do ANYTHING when it locks you out of your own user password.

And also, I had a look at the etc/sudoers file and I cannot access it because it locks me out of it.

I was thinking of restarting the computer and going into recovery mode to reset my user password, but I'm not sure that will do anything because it will still not fix the missing line in the common-auth text file. There must be some command to save a text file with brute force or something.

---

### Post by heindsight on 2009-03-08
Perhaps you should try rebooting into recovery mode, which should give you a root shell without needing a password and then edit the file. 

Alternatively, you could boot from a live CD, mount your root partition somewhere, and edit the file.

For example, in a live CD session, open a terminal and do something like:
```
sudo mount /dev/sdXX /mnt
gksudo gedit /mnt/etc/pam.d/common-auth
```
You'll have to replace /dev/sdXX with the correct device for your root partition.

---

### Post by humphreybc on 2009-03-08
I tried rebooting into recovery mode and then selected "normal boot" but it didn't log me in as root... I typed in my regular password and it let me in, but then when I tested it by trying to open package manager and typing in my password it said 'wrong password.'

So then I rebooted back into recovery mode and dropped down to shell level prompt where I reset my password, and tried again, to no avail. How do you boot into the GUI as a root user?

I then tried the live CD method, i'm typing this from the live CD session at the moment. I've tried mounting the ubuntu install, which is on my second HDD, so /dev/sdb and it didn't work. It has however mounted that hard drive because partition manager tells me it is mounted, and when I go to /mnt I can see my things. So I thought i'd navigate to /etc/pam.d/common-auth and saw that it was actually still missing that one line. I tried editing it, but it said I didn't have permission, so I went into root terminal and used:

```
gksudo gedit /etc/pam.d/common-auth
```

And then I added in the one line and saved it. Now i'm not too sure whether to reboot it and see if it works, because it takes about 15mins to boot up into Live CD so I thought i'd ask you guys if there is anything else I can do to ensure it will work while i'm here.

Thanks!

---

### Post by lindsay7 on 2009-03-08
This is from the Ubuntu pocket Guide
[http://www.ubuntupocketguide.com/download2.html](http://www.ubuntupocketguide.com/download2.html)


Working with root powers
It&#8217;s generally discouraged under Ubuntu to log in as the root user.
Therefore, administrative tasks are carried out by ordinary users who
&#8220;borrow&#8221; the root user&#8217;s powers.
Using sudo
At the command-line, you can force a command to run with root powers
by preceding it with sudo (short for super-user do). For example, to
install software using the dpkg command (discussed in Chapter 6), root
powers are needed, so to use dpkg you would type something similar to
the following:
&#61607; sudo dpkg &#8208;i package.deb 
You&#8217;ll be prompted for your password. Once this is entered, the
command will complete.
If you run a graphical application from the command-line it&#8217;s necessary
to precede it with gksu instead of sudo. To most intents and purposes,
gksu is identical to sudo. For example, to start the Synaptic software
installation application, you would type gksu synaptic.
     NOTE    If  you&#8217;re  using  Kubuntu,  the  kdesu  command  is  used 
     instead  of  gksu.  It&#8217;s  identical  in  function  to  gksu.  Under  Xubuntu 
     the gksu command is used, as with the main Ubuntu release.  
Temporarily switching to root
Despite the desire of Ubuntu&#8217;s developers to stop you logging in as root,
it&#8217;s possible to temporarily switch to the root user account. This is
useful if you have a lot of administrative work to do, where typing sudo
before each command can become annoying.
To switch to the root user temporarily, type the following:
&#61607; sudo su 
After typing your password, you&#8217;ll see that the command-prompt
changes to a hash symbol, to indicate that you have root powers.
When you&#8217;ve finished your work and want to return to your ordinary
user account, just type exit, or hit Ctrl+D.
Enabling root login
It&#8217;s also possible to enable the root login account. This will make
Ubuntu just like most other versions of Linux and Unix. The main
                                               Hands&#8208;on at the Command&#8208;Line :  77 
benefit of this is that it will let you directly login as root at a virtual
console&#8212;just type root as the username.
To enable the root login, type the following; this will assign the root
user a password and thereby allow login:
&#61607; sudo passwd root 
After typing your own password to authorize, you&#8217;ll be prompted to
create a new password for root, so do so.
Following this, in addition to logging in as root at a virtual console, you
can switch to the root user in a terminal window by typing su  &#8208;, and
entering the new root password when prompted. Once the admin work
is done, type exit to logout (or hit Ctrl+D).
     NOTE      Enabling  the  root  account  login  makes  no  difference  to 
     borrowing  root  powers  using  sudo  or  gksu&#8212;you&#8217;ll  still  have  to 
     enter  your  login  password.  The  only  time  you&#8217;ll  need  to  type  the 
     root password is when logging in as the root user.  
It&#8217;s even possible to login to a Gnome desktop session as root. Because
of the real potential for a misclick disaster, this is considered insanely
reckless and isn&#8217;t permitted by default. However, for some major
administrative operations, access to a root-enabled GUI can be useful.
To allow GUI login as root, click System &#61537; Administration &#61537; Login
Window. Select the Security tab and put a check in the box marked
Allow Local System Administrator Login. Then logout and back in.
Give it a try&#8212;type root as the username at the login screen.
     TIP   When logged in as an ordinary user you can start a Nautilus 
     file  browsing  window  with  root  powers  by  opening  a  terminal 
     window  and  typing  gksu  nautilus.  However,  close  the  window 
     straight after you&#8217;ve finished with it, because that Nautilus window 
     will be able to delete any file, anywhere on the system!

---

### Post by humphreybc on 2009-03-08
@Lindsay7

I know how to use the sudo command, but the point is, when I go to enter my user password to enable sudo, it says "sorry try again" because I have accidentally removed a line in common-auth that gives regular users admin privilages.. but to add that line back in again I need admin privilages, which I can't get because the line isn't there!! It's a catch-22 situation.

> &#61607; sudo dpkg &#8208;i package.deb
You&#8217;ll be prompted for your password. Once this is entered, the
command will complete.

I enter in my password and then it says "wrong password!"

---

### Post by heindsight on 2009-03-08
> **humphreybc said:**
> I tried rebooting into recovery mode and then selected "normal boot" but it didn't log me in as root... I typed in my regular password and it let me in, but then when I tested it by trying to open package manager and typing in my password it said 'wrong password.'

So then I rebooted back into recovery mode and dropped down to shell level prompt where I reset my password, and tried again, to no avail. How do you boot into the GUI as a root user?

You don't need to log in to the GUI as root, in fact it would be a very bad idea to do so. I meant that in recovery mode you could have chosen to get a root shell from where you could have edited your /etc/pam.d/common-auth file using an editor like nano or vim.

> **humphreybc said:**
> 
I then tried the live CD method, i'm typing this from the live CD session at the moment. I've tried mounting the ubuntu install, which is on my second HDD, so /dev/sdb and it didn't work. It has however mounted that hard drive because partition manager tells me it is mounted, and when I go to /mnt I can see my things. So I thought i'd navigate to /etc/pam.d/common-auth and saw that it was actually still missing that one line. I tried editing it, but it said I didn't have permission, so I went into root terminal and used:

```
gksudo gedit /etc/pam.d/common-auth
```

And then I added in the one line and saved it. Now i'm not too sure whether to reboot it and see if it works, because it takes about 15mins to boot up into Live CD so I thought i'd ask you guys if there is anything else I can do to ensure it will work while i'm here.

Thanks!
Make sure you edited the right file -- the one on your hard drive, not the one from the live CD session (the command you say you used would have edited the live CD pam.d file not the one on your hard drive). Other than that I think you should be fine.

---

### Post by humphreybc on 2009-03-08
Okay so under the root shell, what would be the correct code to mount my hard drive? This is my layout:

160GB HDD (/C) Local Disk with Windows
160GB HDD (/D) Media Disk with Ubuntu installed using Wubi installer

So to mount my Ubuntu system files, I'd be looking at a /dev/sdb or a /dev/sdb1 command? Or neither? Also when I tried /dev/sdb on its own, it asked me to specify the type, which I said ntfs-3g and then it gave me some other error...

Or can I just go into recovery mode without mounting anything and run gksudo gedit /etc/pam.d/common-auth?

> Make sure you edited the right file -- the one on your hard drive, not the one from the live CD session (the command you say you used would have edited the live CD pam.d file not the one on your hard drive). Other than that I think you should be fine.

I would say that I have edited the file on the CD, unless Ubuntu has mounted my system files from the HDD in the exact same place even though i'm in a live session. Running the command gksudo gedit /mnt/etc/pam.d/common-auth gave me an error that said no file existed there. Which means that it wasn't mounted properly, which takes me back up to the first paragraph!

This is what happens 

```

root@ubuntu:/home/ubuntu# mount /dev/sdb1 /mnt
fuse: mount failed: Device or resource busy
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# mount /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt

```

---

### Post by lindsay7 on 2009-03-08
So I guess you could not get permission with sudo su or set it up to log in the permission, I do not know if this will help, but it is another idea

In Unix, what are the sudo and su commands?

The Unix commands sudo and su allow access to other commands as a different user.
The sudo command

The sudo command stands for "superuser do". It prompts you for your personal password and confirms your request to execute a command by checking a file, called sudoers, which the system administrator configures. Using the sudoers file, system administrators can give certain users or groups access to some or all commands without those users having to know the root password. It also logs all commands and arguments so there is a record of who used it for what, and when.

To use the sudo command, at the command prompt, enter:
  sudo command

Replace command with the command for which you want to use sudo.

The sudo command also makes it easier to practice the principle of least privilege (PoLP), which is a computer security concept that helps control system access and potential system exploits and compromises. For more information about the sudo command, visit A. P. Lawrence's Using sudo page.
The su command

The su command stands for "switch user", and allows you to become another user. To use the su command on a per-command basis, enter:
  su user -c command

Replace user with the name of the account which you'd like to run the command as, and command with the command you need to run as another user. To switch users before running many commands, enter:
  su user

Replace user with the name of the account which you'd like to run the commands as.

The user feature is optional; if you don't provide a user, the su command defaults to the root account, which in Unix is the system administrator account. In either case, you'll be prompted for the password associated with the account for which you're trying to run the command. If you supply a user, you will be logged in as that account until you exit it. To do so, press Ctrl-d or type exit at the command prompt.

Using su creates security hazards, is potentially dangerous, and requires more administrative maintenance. It's not good practice to have numerous people knowing and using the root password because when logged in as root, you can do anything to the system. This could provide too much power for inexperienced users, who could unintentionally damage the system. Additionally, each time a user should no longer use the root account (e.g., an employee leaves), the system administrator will have to change the root password.

---

### Post by humphreybc on 2009-03-08
Yeah but that still doesn't work because it requires my password to grant access to sudo commands, and because the files that grant access are corrupted, my password is about as useful as a one-legged butt kicking monkey.

---

### Post by heindsight on 2009-03-08
> **humphreybc said:**
> Okay so under the root shell, what would be the correct code to mount my hard drive? This is my layout:

160GB HDD (/C) Local Disk with Windows
160GB HDD (/D) Media Disk with Ubuntu installed using Wubi installer

So to mount my Ubuntu system files, I'd be looking at a /dev/sdb or a /dev/sdb1 command? Or neither? Also when I tried /dev/sdb on its own, it asked me to specify the type, which I said ntfs-3g and then it gave me some other error...

Or can I just go into recovery mode without mounting anything and run gksudo gedit /etc/pam.d/common-auth?



I would say that I have edited the file on the CD, unless Ubuntu has mounted my system files from the HDD in the exact same place even though i'm in a live session. Running the command gksudo gedit /mnt/etc/pam.d/common-auth gave me an error that said no file existed there. Which means that it wasn't mounted properly, which takes me back up to the first paragraph!

This is what happens 

```

root@ubuntu:/home/ubuntu# mount /dev/sdb1 /mnt
fuse: mount failed: Device or resource busy
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# mount /dev/sdb /mnt
mount: /dev/sdb already mounted or /mnt busy
mount: according to mtab, /dev/sdb1 is already mounted on /mnt

```

Oh dear. I'm afraid I have no idea how wubi works, so I'm not sure how you'd go about mounting your root partition.

However, if you get a root shell in recovery mode, then everything will be mounted as it normally is, so you can just do:
```
nano /etc/pam.d/common-auth
```
In nano, edit the file as you need to, then press Ctrl+O to save the file and Ctrl+X to exit.

After that,
```
exit
```and then boot normally.

---

### Post by lindsay7 on 2009-03-08
This looks interestion, hope it helps

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by humphreybc on 2009-03-08
Okay well I just went into recovery and used nano to fix the file and save it, then booted up and checked the file and sure enough the new line is there... but guess what, it still doesn't work. I tried starting up synaptics and it prompted me for my password, entered it in and then told me it was the wrong password.

What now?!

---

### Post by lindsay7 on 2009-03-08
That like I sent you should set up a new admin user to the list and hopfully you can setup a new password for that user.

---

### Post by humphreybc on 2009-03-08
Okay i'm gonna give that one a shot, be back in ten minutes or so!

---

### Post by humphreybc on 2009-03-08
Okay so I went into recovery mode and backed up the two files. I checked the /etc/sudoers file, and found that this section was missing:

```
# Defaults

Defaults !lecture,tty_tickets,!fqdn
```

So I added that in and saved it.

Then I went to the group file and went down to this part here:

```
admin:x:106:benjamin
```

BUT instead of saying that, it had this:

```
fuse:x:106:
```

So I changed it to ```
admin:x:106:benjamin
``` and saved it then rebooted and... guess what?

It still doesn't work.

I also tried the command ```
adduser benjamin admin
``` and it politely told me that benjamin was already in the admin group.

What's the next step? Do I have to create a new user and delete benjamin? If so how do I go about doing that?

---

### Post by lindsay7 on 2009-03-08
wow, about the last thing that I would try would be to add a new user name and see if you can log in go get sudo rights with that. Other then that I would try a new post with some details on the problem i.e. admin password lockout or something similar.

---

### Post by heindsight on 2009-03-08
> **humphreybc said:**
> Okay so I went into recovery mode and backed up the two files. I checked the /etc/sudoers file, and found that this section was missing:

```
# Defaults

Defaults !lecture,tty_tickets,!fqdn
```

So I added that in and saved it.

That probably would not make much difference to your particular problem

> **humphreybc said:**
> 
Then I went to the group file and went down to this part here:

```
admin:x:106:benjamin
```

BUT instead of saying that, it had this:

```
fuse:x:106:
```

So I changed it to ```
admin:x:106:benjamin
``` and saved it then rebooted and... guess what?

I suggest you change that back to the way it was, otherwise you can expect more things to break.

Have a look at /etc/group again and see if there isn't already an entry for admin with a different number, and make sure you're a member of that group. If there really is no admin group, you can add one with yourself as member by adding a line like:
```
admin:x:115:benjamin
``` to the group file.

**IMPROTANT:**, 115 is the GID for the admin group on my 8.04 install, I'm not sure it really matters what number you choose (though it will probably be a good idea to choose something close to 100 and not greater than 999). You must however be very certain that no other group already has the same GID number.

---

### Post by humphreybc on 2009-03-08
Okay so I think I just screwed it up even more... I went back into recovery and ran file check, then clean, then fix X server and then booted normally and it wouldn't boot at all, just hung on a black screen with a little blinking white cursor up in the top left corner. I turned off the computer and tried again and same thing happened... so now i'm in windows! I thought it's a bit odd that running "fix" operations in the "recovery" console actually does more damage to the OS so it can't boot!?!

I presume to restore the original files that I backed up I just go into recovery mode and type ```
cp /etc/group.old /etc/group
``` and then for the other one, ```
cp /etc/sudoers.old /etc/sudoers
``` right?

> Have a look at /etc/group again and see if there isn't already an entry for admin with a different number, and make sure you're a member of that group. If there really is no admin group, you can add one with yourself as member by adding a line like:

I didn't have an "admin" entry per se, other than the fuse one. The only admin thing I had was an entry for ```
lpadmin:x:104:benjamin
``` (That's from memory, I'm not sure whether the number was actually 104)

When ubuntu was working before I ran those checks and couldn't boot I went into Administration > Users and Groups and then to my account and properties, then permissions and saw that there were actually TWO entries for "administration rights" checked.

I'm thinking there must be a way to restore the sudoers and group files back to default, or perhaps erase my admin account "benjamin" and then recreate a new one? If I have to re-install Ubuntu, how can I save my settings and programs?

---

### Post by heindsight on 2009-03-08
> **humphreybc said:**
> 
I presume to restore the original files that I backed up I just go into recovery mode and type ```
cp /etc/group.old /etc/group
``` and then for the other one, ```
cp /etc/sudoers.old /etc/sudoers
``` right?

Yes, that should do it. Hopefully that should get you booting again.


> **humphreybc said:**
> 
I didn't have an "admin" entry per se, other than the fuse one. The only admin thing I had was an entry for ```
lpadmin:x:104:benjamin
``` (That's from memory, I'm not sure whether the number was actually 104)

When ubuntu was working before I ran those checks and couldn't boot I went into Administration > Users and Groups and then to my account and properties, then permissions and saw that there were actually TWO entries for "administration rights" checked.

I'm thinking there must be a way to restore the sudoers and group files back to default, or perhaps erase my admin account "benjamin" and then recreate a new one? If I have to re-install Ubuntu, how can I save my settings and programs?

If there really is no admin group in /etc/group, then add one as I described earlier. That should hopefully get everything working properly again. You shouldn't need to delete your admin account or re-install.

---

### Post by humphreybc on 2009-03-08
Okay so I replaced the files with the original ones I backed up and then went sudo visudo to check and sure enough they were the original ones.

Then I went into /etc/groups and had a closer look, and further down on another page there was indeed an entry for admin:

```
admin:x:123:benjamin
```

So I exited it and booted to see if I could get in, and it still wouldn't boot. This time it froze on a black screen with a colourful bar across the top of red/blue/green lines about 40 pixels high... basically it looked like some sort of resolution problem because you could faintly make out the word ubuntu spanning the width about five times. I would say that was the splash screen or the login screen but it isn't working.

---

### Post by humphreybc on 2009-03-08
I just tried to boot into Ubuntu by choosing a different linux kernel. I tried:

Ubuntu 8.10 kernel 2.6.27-11 generic

and it gave me this error message in a window:

> Could not start the X server (your graphical environment) due to some internal error. Please contact your system administrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected.

In other words, Ubuntu is ******.

---

### Post by humphreybc on 2009-03-09
Well I ended up reinstalling Ubuntu entirely from scratch using Wubi again. It has only taken me about 2 hours to get back to where I was in terms of settings and programs, and this time round it's easier cos I know what i'm doing.

---

