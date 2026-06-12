---
title: "sudo not working in ubuntu 5.10"
date: 2005-10-13
forum: Desktop Environments
---

### Post by Jim Stewart on 2005-10-13
Hi.  I'm new to Ubuntu.  I just downloaded the 5.10 "Breezy" CD yesterday (although it seems like it wasn't officially released til today, that's what I got when I downloaded the CD image yesterday).

The initial install went very well, and the machine booted up to a working X desktop.  I logged in using the regular user account I'd created during installation, and there was a desktop notification telling me that 188 updates were available.  I clicked to install the updates, and was prompted for my password.  I entered my password, and nothing happened.

I poked around a bunch, and found this logged in /var/log/auth.log:

Oct 13 11:45:21 localhost sudo: stewartj : command not allowed ; TTY=pts/1 ; PWD=/home/stewartj ; USER=root ; COMMAND=validate

I narrowed the problem down to "sudo" not working.  If I did "sudo ls", for example, I'd get prompted for my password, and the command would do nothing.  No output whatsoever, no errors, no file listing, just another command prompt.

I put an entry into /etc/sudoers (via visudo), allowing "stewartj" to run all command, and now I can run the update tool, and command-line sudo works as you'd expect.  This isn't very secure, and I don't want to leave such a wide-open entry in sudoers.

Did I miss something during setup?  Was I supposed to authorize my non-root login to run certain administrative tools?

My initial impression of Ubuntu from the installation process was very good, but this issue would have been a big deal if I didn't have some systems administration background.  I can probably figure out a more secure sudoers configuration, but I'm sure there's a "real" solution to this that fits with Ubuntu's security and administration model, and I'd like to fix it properly so I don't have to worry about other problems down the road.

Thanks,
Jim

---

### Post by aysiu on 2005-10-13
In answer to your question about what should be done during setup: there is no explicit time to set up a sudoers file--you're just prompted for a regular user password, which should be put in sudoers.

Did you do an expert or server install?

---

### Post by taurus on 2005-10-13
Why don't you use apt-get to upgrade your system like

sudo apt-get update
sudo apt-get upgrade

---

### Post by Jim Stewart on 2005-10-13
[QUOTE=aysiu]In answer to your question about what should be done during setup: there is no explicit time to set up a sudoers file--you're just prompted for a regular user password, which should be put in sudoers.

Did you do an expert or server install?[/QUOTE]

I did an expert install.  I still expected to be able to use things like the menu-driven update system, however.  It seems like it was intended to be used.  It did start automatically and there was a menu/taskbar item informing me that new updates were available to install.  I'm just wondering if I missed something important that will prevent other administrative tools from being available.  I'm not allowed to start an X session as "root" (by default), and I prefer a system where I'm only prompted for an admin password (or a sudo password) when needed.

Is it normal that you have to manually configure sudoers before these administrative tools work under a normal X user session?

---

### Post by Jim Stewart on 2005-10-13
[QUOTE=taurus]Why don't you use apt-get to upgrade your system like

sudo apt-get update
sudo apt-get upgrade[/QUOTE]

I could do that, sure.  But one of the reasons I installed Ubuntu is because I wanted some of the bells and whistles that a regular Debian installation doesn't get you.  I can live without a package management GUI if I need to, but if it's there, it should work, and it should work in an intuitive manner.  If I login, and I'm told there are packages to install, and I tell the installer to proceed, and it asks me for a password..it should do something.  It should not fail silently.  At the very least, it should tell me that I'm not authorized to run the utility, and point me to the proper method for getting authorization.

As I said, I have a systems administration background.  I did get it working.  I'm sure I can manually tweak it to work and be secure.  However, I was driven to Ubuntu because I'm tired of doing everything by hand and I'm looking for a Linux dist that's more user-friendly.

This is mainly a usability complaint.

---

### Post by withoutclass on 2005-10-13
system->administration->users and groups
 then click the checkbox for show all users/groups

root should show up as the first option

click on it and go to properties, and then change the password manually to whatever you want

---

### Post by aysiu on 2005-10-13
I'm confused. You chose the expert install, but you expect things to just work, and you're complaining about usability? I don't mean to be cheeky, but if you want things to just work, try the normal install--expert install, by definition, is for experts.

By the way, the term "user-friendly," if meant to be totally GUI for configuration and installation, does not yet apply to Ubuntu. I'd actually say that Ubuntu is a really good *second* distro. It's not an advanced one, but I wouldn't recommend it as the first distro someone fresh from Windows should install and configure (*use* is a different story if someone else sets it up for you). If you want a GUI installer and GUI configuration, I'd recommend Mepis or Blag.

---

### Post by agger on 2005-10-13
[QUOTE=aysiu]I'm confused. You chose the expert install, but you expect things to just work, and you're complaining about usability? I don't mean to be cheeky, but if you want things to just work, try the normal install--expert install, by definition, is for experts.
[/QUOTE]

You're right, but Mr. Stewart does have a valid point, OTOH:
> 
If I login, and I'm told there are packages to install, and I tell the installer to proceed, and it asks me for a password..it should do something. It should not fail silently. At the very least, it should tell me that I'm not authorized to run the utility, and point me to the proper method for getting authorization.

If Synaptic or the update manager program (probably also synaptic with  a slightly different use case) fails because the user is not a sudoer, it should display an error message stating as much - it should not fail silently.

I think the right thing to do here is to file a bug suggesting this be changed, and then the developers can consider this in due time?

---

### Post by withoutclass on 2005-10-13
[QUOTE=agger]You're right, but Mr. Stewart does have a valid point, OTOH:

If Synaptic or the update manager program (probably also synaptic with  a slightly different use case) fails because the user is not a sudoer, it should display an error message stating as much - it should not fail silently.

I think the right thing to do here is to file a bug suggesting this be changed, and then the developers can consider this in due time?[/QUOTE]

I agree with this

---

### Post by mrmcctt on 2005-10-13
[QUOTE=aysiu]I'm confused. You chose the expert install, but you expect things to just work, and you're complaining about usability? I don't mean to be cheeky, but if you want things to just work, try the normal install--expert install, by definition, is for experts.

By the way, the term "user-friendly," if meant to be totally GUI for configuration and installation, does not yet apply to Ubuntu. I'd actually say that Ubuntu is a really good *second* distro. It's not an advanced one, but I wouldn't recommend it as the first distro someone fresh from Windows should install and configure (*use* is a different story if someone else sets it up for you). If you want a GUI installer and GUI configuration, I'd recommend Mepis or Blag.[/QUOTE]

I agree with this except for one detail.  This is the one distro that I *would* advise new users to try (LiveCD first).  This has got to be the most user-friendly version that I have ever installed. 

I realize you're an expert and I'm a n00b but this is just my opinion.  I have had no problems with this installation, setup and use of this particular distro.

---

### Post by aysiu on 2005-10-13
[QUOTE=mrmcctt]I agree with this except for one detail.  This is the one distro that I *would* advise new users to try (LiveCD first).  This has got to be the most user-friendly version that I have ever installed. 

I realize you're an expert and I'm a n00b but this is just my opinion.  I have had no problems with this installation, setup and use of this particular distro.[/QUOTE] I, too, have had no problems, but my experience is not everyone's experience, and I can copy and paste terminal commands to get my partitions mounted, for example. In Mepis, you don't have to copy and paste commands to get things set up (extra repositories, mounted partitions, installing .deb files). I said Ubuntu is a good *second* distro. It isn't an expert distro like Slackware or Linux from Scratch, but for absolute beginners (little computer experience, only Windows, all GUI), I'd recommend something other than Ubuntu for installing.

---

### Post by ElVirolo on 2005-10-13
I have *exactly* the same problem as jim has.

---

### Post by preater on 2005-10-13
[QUOTE=aysiu]I'm confused. You chose the expert install, but you expect things to just work, and you're complaining about usability? I don't mean to be cheeky, but if you want things to just work, try the normal install--expert install, by definition, is for experts.[/QUOTE]
I had the same problem as Jim did, half and hour ago.  After the graphical update tool (and apt-get update) failed silently, I went straight to visudo and found my normal user wasn't set as a sudoer.

I was more bothered by root's editor being set to GNU Nano by default.  Or rather, $EDITOR was not set, and Ubuntu was defaulting to Nano rather than vi.  Not very 'expert'. ;)

Andrew

---

### Post by SilentCacophony on 2005-10-13
I found something interesting that may be the cause of sudo not working for some of the people who have problems with it.

 I had to backstep in my installation of Breezy today, because of a cd error. From then on, It seems that I was in expert mode, and had to advance through the steps manually.

When it got to the user/password setup, it asked for the root password, which it doesn't do in the normal install, and then asked if I wanted any other users, which it also doesn't do normally. I set a root password, and made my user with the same password.

Having set it up that way, **sudo **did not work, but **su **did (or logging in as root.) So, it seems to me that installing in expert mode bypasses the whole sudo idea, and just uses the old root + users formula. I reinstalled normally, and the problem was gone.

---

### Post by linusgl on 2005-10-13
[QUOTE=SilentCacophony]Having set it up that way, **sudo **did not work, but **su **did (or logging in as root.) So, it seems to me that installing in expert mode bypasses the whole sudo idea, and just uses the old root + users formula. I reinstalled normally, and the problem was gone.[/QUOTE]

So there we have it. An expert is, by Ubuntu, expected to be setting up more of a regular Linux system, where you have a root user. In a normal install, Ubuntu defaults to having no root login, but instead putting everyone in the admin group in sudoers, and adding the first user account to the admin group (or at least that's the way things were set up for me in the Hoary install). Seems pretty good to me.

---

### Post by fimbulvetr on 2005-10-13
The default /etc/sudoers should look like this:

<code>
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL
</code>

I'm not sure how yours is different, but here it says anyone in the admin group is allowed to run any command on any machine as any user. 
My question is, how the heck did you visudo if you can't use sudo:) I assume you used root, but if you didn't, perhaps sudo isn't running because your /etc/sudoers permissions are messed up. sudo won't run unless /etc/sudoers is only readable/writable by root, noone else. sudo also won't run if /etc/sudoers is a symlink. 

If you think your sudo is really broken, you can test by running sudo commands as root (yeah, it sounds silly, but it's a good test). 

I wonder if the snapshot/rc you downloaded was buggy, because every install I've done has always worked correctly with sudo.

---

### Post by GlennB on 2005-10-24
Hi,

sudo is borked on my fresh 5.10 install also. This is a clean, default install, and running any command after sudo normally results in no response, though on one occasion trying to view the logs in /var/log/samba gave me an error like:

"glenn is not in sudoers file. This incident will be reported".

At the time I was logged in as the first user created during the install.

Since I don't have an active root account, and I can't sudo, I'm not sure how to get around this. I'm guessing that booting to single user mode then editing the sudoers file is the best option? Any suggestions?

The weird thing here is that sudo must have been working directly after installation, since I configured samba the same night I did the install (which requires root privs, I think). I definitely haven't changed the sudoers file myself, so I guess I must have done something wacky without realising it. Unfortunately, I've played with three or more Ubuntu systems in the last few days, so I can't remember what might have kicked this off.

Regards,

Glenn.

---

### Post by Bill Statler on 2005-10-24
Check this thread for an answer:

[http://www.ubuntuforums.org/showthread.php?t=77614]("http://www.ubuntuforums.org/showthread.php?t=77614")

---

### Post by rady on 2005-10-25
[QUOTE=withoutclass]system->administration->users and groups
 then click the checkbox for show all users/groups

root should show up as the first option

click on it and go to properties, and then change the password manually to whatever you want[/QUOTE]
You can do follow this recommendation. YOU HAVE TO INPUT YOUR PASSWORD MANUALLY INSTEAD ******* ALREADY SHOWED AS DEFAULT.

---

### Post by SavvyPlayer on 2005-11-22
When using the expert option during install, the "admin" group is not created. This is why sudo fails -- it is configured only to allow members of the admin group to execute any commands. Create an admin group and add yourself, then log out and back in for gnome to pickup your new group membership.

---

### Post by pppoe_dude on 2005-11-30
Hi... k, if you want the expert install, root account enabled, etc. sudo will obviously not work by default. I think this is a bug because the original ubuntu is based on sudo and not root. One was to solve this (brute-force) is to replace all the commands the system tries to run from the menu by "gksu <command>", this will prompt for the *root* password. For example, the network settings menu button can be removed, and another one added to run "gksu network-admin". 

If you don't want to use sudo, this is the only way i can think of, as the menu buttons are made this way. For the update manager, you'll probably have to edit some files.

gksu just runs a command as root, like sudo but actually changes the user to the root user by default.

---

