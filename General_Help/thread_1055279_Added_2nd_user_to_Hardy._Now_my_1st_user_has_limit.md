---
title: "Added 2nd user to Hardy. Now my 1st user has limited rights."
date: 2009-01-30
forum: General Help
---

### Post by Roasted on 2009-01-30
Wow. Just wow.

I have a hardy box here at work to help me with certain utilities. I have two accounts. "clonezilla" which was the first one, and I just added "admin." 

clonezilla was set up to be a clone server. But I use Ubuntu for more stuff, so I decided to keep things separate. I figure clonezilla account for cloning and admin account for other stuff.

I added the admin account. Logged out, logged in as admin... hmm... no synaptic. Log out, back in as clonezilla... hmm... no synaptic...

Now both of my accounts seem restricted. In each account I logged in to admin-users and groups and tried to unlock the security so I can make sure both accounts are administrators of the system... but it doesn't let me. It's like the button itself is dead.

What can I do? GAHHHHHHHH

---

### Post by geirha on 2009-01-30
When you create a user, a group with the same name is also created. Secondly, the group that controls sudo privileges is named "admin". When creating the user named admin, something must've happened with the admin group. Could you post the output of the following command run in a terminal?
```
getent group admin
```

---

### Post by Yellow Pasque on 2009-01-30
If your /etc/group file has two lines starting with 'admin', then this could create issues.

You shouldn't have named the account 'admin' (in fact, I can't believe it let you do that ](*,) ). My theory is that your /etc/group file is probably screwed up with two groups named 'admin', and this will, in turn, deny sudo/root permissions (by default, /etc/sudoers is set to grant sudo permissions to the root account and anyone in the 'admin' group).

If this is the case, I would boot a LiveCD, and edit the /media/<disk-#>/etc/sudoers file (disk-# will be the directory in /media where the CD mounts your hard disk root partition), adding a line:
```
clonezilla  ALL=(ALL) ALL
```
This will explicitly give your clonezilla account the ability to use sudo regardless of whether it is a member of the admin group. Now you can boot your HD, log in as clonezilla, backup any important info in admin's home dir, and delete the admin account.
Next, create your second account and a pick a **unique** name that doesn't already have a group in /etc/group
After you do that, look at /etc/group and make sure there is one line that looks like:
```
admin:x:117:clonezilla,<name of your second account>
```

---

### Post by Roasted on 2009-01-30
admin:x:1001:

So basically, I have user "clonezilla" with admin rights (synaptic, etc).

I added "jason"

Now "clonezilla" is a limited account.
"jason" is also a limited account.

So I have root account disabled due to the nature of Ubuntu and two limited accounts that won't let me change user settings.

Talk about a bunch of sh...

edit - I think I'll just do a fresh install. I was planning on it anyway so I can install Edubuntu and demo it to my boss to see if he wants to deploy that in our school district. I just wanted to hear if there WAS a possible solution.

Makes sense about adding the admin account, though. That's just what I'm used to with using windows machines... It just came to mind. I guess I suck? Haaa. Lesson learned!

---

### Post by Yellow Pasque on 2009-01-30
There is a fix, see my post above.

---

### Post by geirha on 2009-01-30
> **Roasted said:**
> 
Makes sense about adding the admin account, though. That's just what I'm used to with using windows machines... It just came to mind. I guess I suck? Haaa. Lesson learned!

You do NOT suck! This is Ubuntu's fault. It is perfectly legal to have a user named admin, the problem is just that the Users and Groups interface also creates a group by the same name by default, so it is the Users and Groups interface's fault for neither denying you to do it nor warning you about the consequences it may have. This should be reported as a bug.

Anyway, there's no irreparable damage done. Temüjin has posted the necessary steps to get your system back to normal.

---

### Post by Roasted on 2009-01-30
I did what you said with the LiveCD. It still doesn't work. I need to get to work asap and my data is backed up on all accounts, so I'm reinstalling.

How do I file this as a bug report? This is absolutely laughable to see that something like this wasn't picked up on at an earlier time.

---

### Post by Yellow Pasque on 2009-01-30
You did edit /media/<disk->/etc/sudoers and not just /etc/sudoers, right?

I'm about to boot up a spare Intrepid install and see if the error exists there. I will report the Launchpad bug if it still exists there.

---

### Post by geirha on 2009-01-30
The proper place to report bugs in the Users and Groups interface is: [https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools)

Odd that Temüjin's instructions didn't work. We probably would've fixed it eventually, but since you're in a hurry and you've been smart and kept backups, reinstalling sounds like the better choice.

---

### Post by Yellow Pasque on 2009-01-30
This bug was already reported, so don't feel bad about naming your user 'admin' as a bunch of others have done it:
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/236305)

Yes, the bug still occurs in Intrepid (probably Jaunty too).

---

### Post by Roasted on 2009-01-30
> **Temüjin said:**
> You did edit /media/<disk->/etc/sudoers and not just /etc/sudoers, right?

I'm about to boot up a spare Intrepid install and see if the error exists there. I will report the Launchpad bug if it still exists there.

Yeah, I did do that with /media/disk/etc/sudoers.

I just ended up doing a fresh install. I have my home directory on another partition so it's not like I was losing anything.

---

### Post by Yellow Pasque on 2009-01-30
Yeah, I made an admin user on a fresh install of Intrepid to test it out. I then edited /etc/sudoers and added my first user. I then rebooted.

Strangely, my first user still was locked out of 'Users and Groups' (the app wouldn't even start) and even using 'gksudo users-admin' would only allow partial access. I had to use the sudo adduser command to put my first user back in the admin group, and I'm not sure if that will fix it or not.

I'll experiment with this some more (at another time) because I think I don't have a full understanding of how GNOME determines permissions (doesn't seem to be with /etc/sudoers).

---

