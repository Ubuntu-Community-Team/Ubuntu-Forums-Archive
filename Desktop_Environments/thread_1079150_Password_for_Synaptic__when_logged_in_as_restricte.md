---
title: "Password for Synaptic  when logged in as restricted user"
date: 2009-02-24
forum: Desktop Environments
---

### Post by npaisnel on 2009-02-24
First off, I could just do a complete re-install of the machine in question but that is defeatist, for my own learning I would like to know what is going on here.

Quick background:

I have two public access machines Ubuntu 7.?? that I set up from old hardware at a local club, maybe 12 -18 months ago. This was the last time I did any linux/command line work
A few (6?) months ago, one of the committee members decide it should be done 'in house'.....both systems re installed with 6.06.  Since then one machine 'broke' and Committee have done nothing, and club users have been on at me to 'fix' them, as only one machine was working and that poorly...Committee as usual have lost interest and can't be bothered.

One machine I bumped up RAM and re-installed XUBUNTU 8.10..all fine. The other ..just needed a few OS/software tweaks.

Are you still with me?

  
Now to the point.

Other machine OK, but need a few apps/flash player etc installed.
I could only boot in to the restricted Club user (..as set up previously by the 'committee expert').
This meant I could not run Synaptic or other package manager.


So I booted as far as GRUB, booted to single user,
and (I am writing this from recall from memory, while sitting in airport terminal... ) used I think:

sudo passwd

to reset password.
The command prompt showed *#root@JAC2:* or what ever the correct format is...but any way I was logged in as root

then created new user (myself)(UUID 1002)and set myself to the group: admin.

Re booted as normal and successfully logged in under my newly created username.  It would seem I had full admin privileges.

Under Users, there were three users (UUID 1000, 1001 and 1002)
From the users screen, I could successfully change passwords, of the original admin user(1000) and the restricted club users.

So, as far as I was concerned...mission accomplished ..I had full control of my machine back again  

BUT NO

I then logged out and back in again as the restricted club user.
Tried to run Synaptic...it asks for a password...ah no problem I thought, but none of my newly reset passwords worked.
I get an error something like  user/synaptic  incorrect password 

Yes I can do the upgrades while logged in under my own name, but not from the restricted user.  

What am I missing here?

Thanks

Neil

---

### Post by mikewhatever on 2009-02-24
You aren't missing anything. Restricted users can neither update nor upgrade, nor use synaptic. Isn't it why they are restricted? Obviously, resetting the password for such a user would not elevate permissions.

---

### Post by npaisnel on 2009-02-25
Yes, I see what you are saying, but the password I was entering when asked for one was not the restricted user pwd, but the admin pwd.

I was assuming the GUI worked in a smilar fashion to doing something from the terminal.  You cant do major stuff from term without sudo.  I iamagined asking for the pwd was similar to using sudo in term and entering the root/admin pwd.


If logged in as a restricted user, and I opened term, I would have imagined I could do sudo apt-get and would be asked for a password.  The password the machine would be expecting would be the root/admin password.  

Is this not the same via the GUI....and similar in Windows, I can log in as a restricted user in Windows, but use Run As xxx User to elevate priviliges to do admin tasks.  
I can't go and try this out, as I am away from home base now for 4 weeks, although I do have a Xubuntu live Cd with me...maybe it wil run on this laptop.

---

### Post by mikewhatever on 2009-02-25
A user must belong to the admin group to be able to peform admin tasks, and that's regardless of what the password is. If you want a certain restricted user to perform admin tasks, that user's restrictions must be changed, and not the password.

---

### Post by npaisnel on 2009-02-25
So is that the same even if I go into terminal while logged in as restricted user; I will not be able to use sudo?

I do not want the user to have these priviliges, just hoped I could do the admin tasks while logged in as Res User, by using the admin/root pwd.

No big deal to log out and back in again....just another step I thought I could avoid

Thanks

Neil

---

### Post by mikewhatever on 2009-02-25
I think that's correct. Restricted users aren't allowed to use sudo. Only those in the admin group can elevate their privileges with sudo.

---

### Post by evas80 on 2009-02-25
If you are comfortable with command line, You can use su command to login as Admin/root user (any user for that matter) and manage tasks thru command line.

While you have logged in as restricted user, in the terminal use the command "su *username*". For example to login as root in terminal "su root" then provide root password and manage the tasks.

---

### Post by npaisnel on 2009-02-25
Mike, evas80, thanks for that

I cant get access to the machine in question for another couple of weeks, as I am away from home so have d/loaded a copy of xubuntu.  Will burn and try and run as live CD on this laptop and have a play with the su username options from the cmd line

Thanks for clearing this all up

Neil

---

### Post by Yashiro on 2009-02-25
The admin group in ubuntu grants you use of sudo. 
This is because %admin is defined with full rights in the sudoers file.

Only root and people defined in the sudoers file can run administrative tasks. Normal users cannot, this is correct.

If you want to allow a restricted user to be able to nuke the machine then either just make them a member of the admin group or add them to the sudoers file using visudo. 

If you're using ubuntu and want to somewhat replicate traditional su then create a user with admin rights and tell everyone who needs to know the name and password. They can then use 'su accountname' from any account.

---

### Post by npaisnel on 2009-02-26
Thanks
There is no need for that, this is basically a Internet Cafe type machine, in a private club room of the local aeroclub.

What I was hoping for was a locked down machine thta I could do admin type tasks just be typing a password...without having to log out and back in as admin.

There are no other users, just myself, and all club members with very basic priviliges...internet access and that is it.

I would like to lock it down even further, remove a lot of icons in the Applications menu, lock the menu bars, and Desktop icons, and just allow internet access, printer, and basic text, doc, spreadsheet viewing options.

Think I will start another thread for that question though.

---

