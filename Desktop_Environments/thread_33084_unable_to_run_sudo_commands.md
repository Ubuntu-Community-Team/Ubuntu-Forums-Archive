---
title: "unable to run sudo commands"
date: 2005-05-09
forum: Desktop Environments
---

### Post by SilvioTO on 2005-05-09
I add a user in addition to me and after few days I delete it. Now I don't be able to enter as root in applications!  :? 

for example: when I try to launch Synaptic, a password request appear; I type, then return and:

"Failed to run user-admin: child terminated with 1 status".

From console:

"silvio is not in the sudoers file. This incident will be reported.


help me please. thanks.

---

### Post by Professor X on 2005-05-09
My suggestion is to enable root access (sudo passwd), then switch to the root user and use visudo to edit the sudoers file.  Make sure your username is listed in that file and looks like this:

```
silvio ALL=(ALL) ALL
```

 If for some reason you can't enable root access using sudo, then use the installation CD (or Knoppix) to gain root access.

---

### Post by az on 2005-05-09
[QUOTE=Professor X]My suggestion is to enable root access (sudo passwd), then switch to the root user and use visudo to edit the sudoers file.  Make sure your username is listed in that file and looks like this:

```
silvio ALL=(ALL) ALL
```

 If for some reason you can't enable root access using sudo, then use the installation CD (or Knoppix) to gain root access.[/QUOTE]

You only need to boot into recovery mode to become root and edit your sudoers file.  You do not need to use a live cd.

---

### Post by SilvioTO on 2005-05-09
problem fixed, thanks.
I'm only added using Damn Small Linux and Beaver editor this line in sudoers file:

silvio ALL=(ALL) ALL


 :smile:  :smile:  :smile:  :smile: Thanks again...

---

### Post by jones_jj on 2005-07-25
On a similar note to SilvioTO's question.  I did an expert install of Ubuntu which prompted me for a root password, and then a first user username and password.  I did this.  I login as the first user <username> which as I understand has some Admin rights?  

My problem is the time was wrong and I wanted to change it, so I right click on the clock and and go to adjust time and date.  It prompts me for a password for time-admin password.  I thought this would be my root password so I entered it and it gave me an error:  "Failed to run time-admin: child terminated with 1 status".  So then I decided I would use my first user account and the same error came up.  This pretty much happens with any app that I try to run through the Administration menu.  Does this have something to do with running the install as an expert?  Or is there some other issue going on?  

Thanks for the help.

---

### Post by majikstreet on 2005-07-25
I'm not sure about the above problem but I wanted to share something I found:
Instead of editing your sudoers file, you can add the new user account to the group wheel if you want to account to have sudo privledges. If you want the user to have full privledges like the original account, you can add them to the group admin.

If you can't get into the account you can do this:
When you boot up and see "Grub loading", press either f1 or f2 (I can't remember which one now...) and you'll get a menu. Select the one with the word "recover" in it and press enter. You have full admin privledges now. You can change the password of your account by typing "passwd username" replacing username with your username and entering your password when it prompts you.

---

### Post by jones_jj on 2005-07-25
Do you need to install the "recover" install?  Or does it get installed automatically when do an expert install?

---

### Post by az on 2005-07-25
The "expert" install is just a regular install with the user being prompted about things before they get done automagicaly.  Ther eis no reason to use the expert install unless there is a bug in the installer which prvents the thing from booting or installing.

That being said, yes, the recovery mode option in grub if present in a basic Ubuntu install.  You even get it with the "server" install.

---

### Post by jones_jj on 2005-07-25
If the expert mode installation is the same as the "just hit enter" installation mode, why does the expert mode ask you to add a root password where as the "just hit enter" mode does not ask you to add a password to root?

I'm just trying to understand more of what Ubuntu is all about.  Thanks

---

### Post by Takis on 2005-07-25
Hmm, can someone straighten this out for me: if you reboot your Ubuntu box and select the Recovery Mode boot option, you get root priviledges without having to put any special password in or anything? So any Bob off the street who knows how Ubuntu works can do that?


Did I miss something? That seems like a backdoor.

---

### Post by jones_jj on 2005-07-25
No, I believe when you reboot into recovery you should be prompted to put your username and password, which seems to enable sudo/su - root access.  So no I don't think any ole Bob off the street could come in and take over your Ubuntu box, they would have to know your username and password.

---

### Post by az on 2005-07-25
Regardless of the OS, anyone with physical access to your computer can own it.  This is nothing new.

---

### Post by az on 2005-07-25
[QUOTE=jones_jj]No, I believe when you reboot into recovery you should be prompted to put your username and password, which seems to enable sudo/su - root access.  So no I don't think any ole Bob off the street could come in and take over your Ubuntu box, they would have to know your username and password.[/QUOTE]
No.  There is no password prompt.  The same goes for any other linux distro.  If you pass a boot argument like "init=/bin/bash", or "single" you are root.

---

### Post by Takis on 2005-07-25
[QUOTE=azz]Regardless of the OS, anyone with physical access to your computer can own it.  This is nothing new.[/QUOTE]
Obviously, but that's not the question. I'm still trying to get my head around this. If I created a guest account, who's a member of the standard media (floppy, cdrom, etc) groups but not the admin group, could they log in through recovery mode?

---

### Post by Xian on 2005-07-25
[QUOTE=azz]No.  There is no password prompt.  The same goes for any other linux distro.  If you pass a boot argument like "init=/bin/bash", or "single" you are root.[/QUOTE]
When I run 'single' in the kernel line I get dropped to a shell with this:

```
Type root password for maintenance
(Or type Control-D to continue)
```

---

### Post by Xian on 2005-07-25
[QUOTE=Takis]If I created a guest account, who's a member of the standard media (floppy, cdrom, etc) groups but not the admin group, could they log in through recovery mode?[/QUOTE]
According to my results the answer would be no.
It clearly asks for a root password.

---

### Post by jones_jj on 2005-07-25
[QUOTE=Xian]When I run 'single' in the kernel line I get dropped to a shell with this:

```
Type root password for maintenance
(Or type Control-D to continue)
```[/QUOTE]


I actually get the same prompt/posting that Xian has when booting into the recovery mode.  I'm not sure what other people are seeing.

---

### Post by Xian on 2005-07-25
[QUOTE=jones_jj]I actually get the same prompt/posting that Xian has when booting into the recovery mode.  I'm not sure what other people are seeing.[/QUOTE]
Yeah, nothing new here. 
That's what I've always gotten for an output.

For those that get no password-required access, what are you doing?

---

### Post by Takis on 2005-07-25
[QUOTE=Xian]When I run 'single' in the kernel line I get dropped to a shell with this:

```
Type root password for maintenance
(Or type Control-D to continue)
```[/QUOTE]
Now see that's what I get to, but because it disagrees with what other people have said I just thought I'd broken something again.
So what's the solution when you haven't set a root password?

---

### Post by Xian on 2005-07-25
[QUOTE=Takis]Now see that's what I get to, but because it disagrees with what other people have said I just thought I'd broken something again.
So what's the solution when you haven't set a root password?[/QUOTE]
For me it would be to just access Ubuntu as root from another Linux partition.
The same could be done via a LiveCD.

---

### Post by Takis on 2005-07-25
Okay cool. I have plans of setting up an Ubuntu box in a reasonably public place in the future, and just wanted to be sure this wasn't a gaping open hole. By putting a password on the BIOS (so you can't change the boot order) it's easy enough to lock that part down.

---

### Post by az on 2005-07-25
Ah.  

If you run a default ubuntu install, there is no root password and you do not get a prompt for a password.  You just get logged in as root.

It comes to the same thing.  You can run a live cd and chroot (as root) into your ubuntu filesystem.

Or you can take a screwdriver and make off with the drive.

---

### Post by az on 2005-07-25
[QUOTE=Takis]Okay cool. I have plans of setting up an Ubuntu box in a reasonably public place in the future, and just wanted to be sure this wasn't a gaping open hole. By putting a password on the BIOS (so you can't change the boot order) it's easy enough to lock that part down.[/QUOTE]

Lock the case so that they cannot open it and reset your bios to default (no password)

Also, remove the 'show menu' grub option.

---

### Post by Xian on 2005-07-25
[QUOTE=azz]If you run a default ubuntu install, there is no root password and you do not get a prompt for a password.  You just get logged in as root.[/QUOTE]
The sudo idea exists to shore up security but it doesn't help much here. :)
Mike of the street could login as root to your box.

'Course anyone with access to the box is in anyway....

---

### Post by az on 2005-07-25
That has been my point.  Ubuntu is a desktop system.  Sudo is a convenience afforded to desktop users. 

If you want to run a server or any other kind of system, you have to turn on security.  One of the basic tenets of security is that anyone with physical access to your box can be root.  Nothing new here.

The fact that Ubuntu does not do much to fight that battle is irrelevant.  If any linux distribution claims to offer protection against a guy with a screwdriver, they are lying.

---

### Post by gmcle454 on 2006-05-14
The single-user login can be thwarted. Although it would only buy you time and force the hacker to use better methods, it is better than nothing if your box is in an unsecure environment (IE a college dormitory).

[http://www.antionline.com/showthread.php?threadid=269805]("http://www.antionline.com/showthread.php?threadid=269805")

For what it's worth, if you want to harden linux, [Bastille Linux]("http://www.bastille-linux.org/") is a great tool for hardening a Linux OS if you don't know anything about it.

---

