---
title: "[SOLVED] Can't log in with main user account."
date: 2008-09-11
forum: Desktop Environments
---

### Post by Maheriano on 2008-09-11
I went into the administrator settings and enabled my user to be able to administrate the system. Then I added the user to the root group, all in an attempt to try and add a file to the /etc/ directory. Eventually I wasn't able to open applications anymore, it was just hang. So I rebooted and when I tried to log in with that user again I get an error message:
> User's 4HOME/.dmrc file is being ignored. This prevents the default session and laguage from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users.
Then I click OK and get another error:
> Your session only lasted less than 10 seconds. If you have not logged out yoruself, this could mean that there is some installation problem or that you may be out of diskpace. Try logging in with one of the failsafe sessions to see if you can fix this problem.
And it gives me the option to View details (~/.xsession-errors file)

But I can log in with another user I created called admin and I can su to root once in there. Can I fix it somehow?

---

### Post by Pro-reason on 2008-09-12
Simply log on as &#8220;admin&#8221; and undo what you did to your main account (take it out of the root group).

---

### Post by Maheriano on 2008-09-12
I tried that (maybe I was doing it wrong) but when I load the Users And Groups application and click UNLOCK to edit the accounts, nothing happens. I click UNLOCK, it waits about 10-15 seconds, then a box tells me I don't have permissions. So I click Properties, go to the second tab and the only box that's not checked for my ADMIN (just a name) account is the ability to modify users/groups. Am I close?

---

### Post by Maheriano on 2008-09-12
Wait, would it being in the root group even cause this? Also, I guess I could sudo the group change from root on the command line right? Would that work?

---

### Post by Pro-reason on 2008-09-12
> **Maheriano said:**
> Wait, would it being in the root group even cause this? Also, I guess I could sudo the group change from root on the command line right? Would that work?

Well, yes, it should work, but to use “sudo” you need the ability to administrate the system, and the failure to “unlock” that thing to edit the accounts indicates to me that your “admin” account is not in fact set up to administrate the system.

Are you able to log on to a non-graphical terminal (press Ctrl-Alt-F1) with your original account?  From there you should be able to sudo your problems away.  In fact, you should be able to select your original account from the drop-down list in the user-management window.

---

### Post by Maheriano on 2008-09-13
Admin is just a regular user, I tried to say in my last post that admin is just a name, it's not actually an administrator. Sorry about that. I can su to root though and make any changes I want that way, I just don't know how to make it so that my main user (deemar) can once again log into Gnome. Can I drop that user and create a new one that can control everything? Or is there a way to reset the permissions for deemar?

To answer your second question, I can log in as deemar when using Ctrl+Alt+F1 just fine but don't know what to do once I'm there. It's just a command prompt so there's no drop down box, just text. Sorry, been researching this all day and managed to make a pile of new users but either they can't administrate the system or they can't log in at all.

---

### Post by Maheriano on 2008-09-13
Actually, after I did that I restarted the machine and was able to log into Gnome with deemar just fine. WTF? Is there something I should check while I'm logged into it now or should I just assume I'll be able to log in always now?

---

### Post by Pro-reason on 2008-09-13
> **Maheriano said:**
> Actually, after I did that I restarted the machine and was able to log into Gnome with deemar just fine. WTF? Is there something I should check while I'm logged into it now or should I just assume I'll be able to log in always now?

I really don't know what you have done in all your playing around!   LOL

Delete the other accounts, and their home directories.  Make sure that deemar is set to administrate the system (in other words, be able to &#8220;sudo&#8221;).

To do admin stuff, don't use &#8220;su&#8221; to log on as root.  Just out &#8220;sudo&#8221; in front of command-line programs, and &#8220;gksu&#8221; in front of the commands to start up graphical apps.

You said you wanted to add a file to the /etc directory.  What exactly were you trying to do?  If, for example, you had a file called &#8220;myfile&#8221; on your desktop, and you wanted to put it in the /etc directory, you would use the following command:

```

sudo mv ~/Desktop/myfile  /etc

```

If you wanted to edit a file in that directory, you would use the following:

```

gksu gedit /etc/*myfile*

```

(replacing *myfile* with the name of the file in question).

---

### Post by Maheriano on 2008-09-13
Ha, no idea! So I can log out and log into Gnome just fine now but this happens when I try to sudo. How do I fix this?

```
deemar@chugger:/etc$ sudo mf asdf
[sudo] password for deemar: 
deemar is not in the sudoers file.  This incident will be reported.

```

My machine is named Chugger! I can hear it chugging when it works.

---

### Post by Pro-reason on 2008-09-13
> **Maheriano said:**
> 
deemar is not in the sudoers file.  This incident will be reported.


We need an account that is in the sudoers file.  The first account that you created on the machine during installation should be a sudoer, but it seems that you might have removed those privileges.

We can't do any system administration unless you have the password to an account with sudo (administrative) rights.  Unless you know the password to the root account (which by default has no password on Ubuntu).

---

### Post by aysiu on 2008-09-13
This will help you:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

After you fix it, read this:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by Maheriano on 2008-09-15
Thanks, I'll read those tonight.

And to answer the previous post, I did assign a password to root before any of this happened. So I can su to root on the command line and do any sudo work from there.

---

### Post by Maheriano on 2008-09-17
Thanks, I fixed it! When I looked at the link Aysiu posted and read how my sudoer file should look, I realized it's likely that the file didn't change, I'm just not in the admin group anymore. So I ran
> usermod -aG admin deemar
and all was well with the world again! Rejoice!

---

