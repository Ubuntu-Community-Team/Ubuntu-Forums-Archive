---
title: "Sync Evolution between two computers (no phone/PDA)"
date: 2007-11-13
forum: Desktop Environments
---

### Post by bogoliubov on 2007-11-13
Hello. I want to sync Evolution between two co mputers, both running Ubuntu.   The mail-part of Evolution I don't need to sync, since I use IMAP, but the calendar, tasks and addressbook I need to sync.

Anyone has any idea? It seems to be that there should be such a feature in Evolution!

If possible, I'd like to be able to do it over ssh and through a script!


If the above isn't possible, I at least would like to be able to update Evolution from one computer to the other. In this case, I have to keep track of which computer I used last, and update from that one. I tried to do this by syncing the files in .evolution and the .gconf/apps/evolution/, but it doesn't work...

---

### Post by bogoliubov on 2007-11-14
No one? I can't be the only one with this problem!?

---

### Post by storri on 2007-11-15
No you are not alone. I synced only the .evolution directory and got my messages but the contacts, memos and tasks do not sync properly. I was using the program 'unison' to sync the two via SSH. Unison works great but I am at a loss to where data is located in evolution.

---

### Post by bogoliubov on 2007-11-15
The data is stored in .evolution, but the names of the folders depend on the computer name, etc...
I've been thinking about creating links within the .evolution folder, but it seems a bit tricky. Also, I would have to keep track of which computer I was using...

---

### Post by bogoliubov on 2007-11-16
I've solved it using OpenSync and Unison together. It's not very elegant, but so far it seems to work. I can sync calendar, addressbook and tasks! 

In essence, this is what to do:
0 Kill evolution on both machines (use the command 'evolution --force-shutdown')
1. Run opensync (Evolution - File) on both machines. 
The files are stored in some folder.
2. Sync these folders using unison.
3. Run opensync on both machines again.

The only problem I have left is to fix a script that doesn't require me to write my login password (for ssh) a million times. Any ideas on this? I'm not too keen on using ssh certificates...

---

### Post by betes on 2007-11-24
So if you named both machines the same name would unison sync all Evolution data without trouble?

---

### Post by bogoliubov on 2007-11-26
> **betes said:**
> So if you named both machines the same name would unison sync all Evolution data without trouble?

Hmm, now I'm not sure what you mean..., No I don't have the same names on both machines, but it's working anyway...

---

### Post by betes on 2007-11-26
Sorry, I realized I was refering to a post you made in another thread (both of those threads came up in my search for info on this).
In another thread you said:

> Hmm, it seems that Unison is not enough to sync Evolution between two machines. It might work if the machines have identical names, but mine can't have that...

And above you said:
> 
The data is stored in .evolution, but the names of the folders depend on the computer name, etc...

So i was wondering if you were to give two computers in a LAN the same name if unison would be able to synch all evolution data without opensync.  Is my question clear?  

Thanks,
Ben

---

### Post by bogoliubov on 2007-11-26
Well, I'm not sure if it will work or not. You can try of course. Probably you should start by setting up Evolution on one computer, than use the backup utility in Evolution to make a backup. This can then be opened when you setup Evolution on the second machine. 

Note that there may be a difference between getting syncing to work between calendars that already exist, and the making of new calendars!

Also, with your version, I don't think you can make changes to both computers at a time, and then sync the changes. You'll have to keep track on which computer you used last.

Let me know if it works!

---

### Post by Maddy on 2007-12-13
> **bogoliubov said:**
> Well, I'm not sure if it will work or not. You can try of course. Probably you should start by setting up Evolution on one computer, than use the backup utility in Evolution to make a backup. This can then be opened when you setup Evolution on the second machine. 

Note that there may be a difference between getting syncing to work between calendars that already exist, and the making of new calendars!

Also, with your version, I don't think you can make changes to both computers at a time, and then sync the changes. You'll have to keep track on which computer you used last.

Let me know if it works!

This just simply backups everything in evolution, my backup for example is over 2.2 gigabyte, if  I have to do this every night over the wireless network then I would spend a lot of time 'syncing'.

No this is not the right solution, it should be possible from witin evolution just to sync the adressbook or the calendar to other computers over ssh. and with syncing I mean sending only the differences!!

Dirk

---

### Post by bogoliubov on 2007-12-14
Hello. I agree with you that Evolution should have this feature. But with the solution I found, I only move the differences! Note that I don't sync the mail part, since I use IMAP. But anyhow, you shouldn't have to move large parts of data! 
Look, this is the way it's done:
1. On machine 1, do evolution -> sync with folder (msync/opensync)
2. On machine 2, do evolution -> sync with folder (msync/opensync)
3. Sync the folders on the two machines (with unison) (msync/opensync)
4. On machine 1, do evolution -> sync with folder (msync/opensync)
5. On machine 2, do evolution -> sync with folder (msync/opensync)

Does this make it easier?

---

### Post by Maddy on 2007-12-24
> **bogoliubov said:**
> Hello. I agree with you that Evolution should have this feature. But with the solution I found, I only move the differences! Note that I don't sync the mail part, since I use IMAP. But anyhow, you shouldn't have to move large parts of data! 
Look, this is the way it's done:
1. On machine 1, do evolution -> sync with folder (msync/opensync)
2. On machine 2, do evolution -> sync with folder (msync/opensync)
3. Sync the folders on the two machines (with unison) (msync/opensync)
4. On machine 1, do evolution -> sync with folder (msync/opensync)
5. On machine 2, do evolution -> sync with folder (msync/opensync)

Does this make it easier?

Ok, this works now, however if you are like me (and I can't imagine that there aren't any other persons who do it this way) and you make for every type of appointment a calendar then there are a lot of calendars and so you have a lot of work to making the groups in multisync, I have for example 13 calendars so that makes 13 groups in Multisync.  But well this works and I can keep my notebook and desktop computer synced now, I hope someone writes a plugin for evolution itself to make it easier.

Thank you for your help!!

Regards.

---

### Post by cdub772 on 2008-02-18
Would someone elaborate on the solution in this post?  I've read it about 20 times, and poked around my systems but haven't had much luck.

Specifically, does one sync evolution to a folder through the evolution application, or is there a way to do this with multisync?  I've installed the last two verisons of multisync and related plug-ins as well as unison on both my regular laptop and my eeePC.  

I've got ssh working, and can wireless sync directories on the two machines with unison....

Any elaboration on this would be appreciated.

---

### Post by reidi on 2008-03-29
I use ScheduleWorld to sync my home and work computers running Windows, Outlook, Thunderbird, Ubuntu 7.10, Evolution.  ScheduleWorld pretty much syncs anything, computers, phones, PDAs. The service is free, fast and well supported.  You could easily set it up to sync 2 computers running Ubuntu - you will need to install and configure Syncevolution if you use Evolution.  If you use Thunderbird it is almost effortless.  See the ScheduleWorld site.
[http://www.scheduleworld.com](http://www.scheduleworld.com)

---

### Post by betes on 2008-04-02
> **reidi said:**
> I use ScheduleWorld to sync my home and work computers running Windows, Outlook, Thunderbird, Ubuntu 7.10, Evolution.  ScheduleWorld pretty much syncs anything, computers, phones, PDAs. The service is free, fast and well supported.  You could easily set it up to sync 2 computers running Ubuntu - you will need to install and configure Syncevolution if you use Evolution.  If you use Thunderbird it is almost effortless.  See the ScheduleWorld site.
[http://www.scheduleworld.com](http://www.scheduleworld.com)

Thanks reidi,  This is exactly what i've been looking for for a long time.  Only problem is that using scheduleworld with syncevolution made a lot of duplicate entries of my contacts on each machine.  However, thats better than missing info on each machine.  Has anyone else had this problem?

---

### Post by bogoliubov on 2008-04-30
> **cdub772 said:**
> Would someone elaborate on the solution in this post?  I've read it about 20 times, and poked around my systems but haven't had much luck.

Specifically, does one sync evolution to a folder through the evolution application, or is there a way to do this with multisync?  I've installed the last two verisons of multisync and related plug-ins as well as unison on both my regular laptop and my eeePC.  

I've got ssh working, and can wireless sync directories on the two machines with unison....

Any elaboration on this would be appreciated.

Sorry for the late reply; I haven't checked this thread in a long time.

The syncing between evolution and a folder is done by multisync/opensync.
You set it up so it syncs to some folder of your choice ( I keep it hidden so it doesn't get in the way). 
This is done on both machines. Obviously, the folders on the two machines doesn't have to have the same names, or locations. 

Then you sync the folders on the two machines using Unison. This can be done over ssh. 

When this is done, once again sync the folders on both machines with Evolution, using multisync/opensync.

---

