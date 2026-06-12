---
title: "Samba shares don't stay mounted - why?"
date: 2006-08-17
forum: Desktop Environments
---

### Post by BlueNoteMKVI on 2006-08-17
In my office we have a half dozen or so computers, some running Windows XP and some running k/ubuntu.  One of the XP boxes is our collective file server using Samba.  I have the shared directory automatically mounted using the following fstab entry:

//gershwin/SharedDocs   /home/chris/networkshares/gershwin_shared     smbfs   auto,users,rw,uid=chris,gid=users,credentials=/home/chris/.smbpasswd    0       0

This works beautifully, the share is mounted at boot, everybody is happy.  The trouble is that after a while the connection is lost with the server and then I have problems getting it to work.  I can't say an event that triggers it to disconnect, but frequently I go to access the shared documents and they're gone.  I have to open a console and use:
sudo umount /home/chris/networkshares/gershwin_shared
sudo mount /home/chris/networkshares/gershwin_shared

Occasionally I'll get messages about the device being busy and I have to umount -f or -l to make it work.  I'm about to put those commands into a cron script that runs every hour as a workaround hack, but I'm sure there's a better solution out there.

So, any ideas of what's causing this or how to fix it?  I've looked through the logs but I don't see any messages about it.  The network here is all wired so it's not flaky wifi connections.  Even with all of those computers there are generally only 2-3 people working at any given moment and we don't make heavy use of the shared files.

Any help would be appreciated.

---

### Post by Dennis Laumen on 2006-08-17
I have the exact same problem.

I use Samba mainly for playing music. I have a share which hosts all my Flac's and use Rhythmbox or Banshee for playing them. The problem I am having (since approximately a week or so I think) is that under load (e.g. playing a couple of Flac's) causes the share to freeze or something.

The solution as the topic starter suggested is umount-ing the share with the -f or -l directive. For me personally it makes this setup completely unusable as I can't play two or three songs without it crapping out on me.

I have tested this problem on two different Ubuntu installs and a Windows XP install. The results are the same. The share which "freezes" needs remounting. All the other shares keep working however.

My testing (as stated above) tells me it's a server problem. My server's running Ubuntu 6.06 with Samba apt-getted from the repositories.

Any help would be greatly appreciated.

---

### Post by bazz on 2006-08-17
I had something like that. I needed to make the machines static, and that fixed it for the most part.

---

### Post by BlueNoteMKVI on 2006-08-17
Everything in the office is on a static IP except the laptops that are in and out on a regular basis.  I don't know that my laptop has ever been on the network here long enough to see that problem.  When I bring my laptop in, I generally just sync it with the desktop box and then shut it down.  Nobody else has complained about it with laptops but most of them don't have the share automatically mounted.  My business partner has a Linux box with the same kind of automount setup and he sees the problem occasionally, but he frequently reboots from windows to linux and back so probably isn't connected long enough for it to be an issue.

As a test, I'm playing MP3s from the network share this morning.  So far it's been going for several hours without interruption.

---

### Post by Dennis Laumen on 2006-08-17
I just tried mounting the shares with CIFS instead of SMBFS.

An example from my /etc/fstab :

//10.10.10.50/Muziek     /home/dennis/Muziek     cifs     username=dennis,password=topsecret,uid=1000,iocharset=utf8,codepage=unicode,unicode     0     0

Using CIFS seemed to work longer/better than using SMBFS. Apparently CIFS is the replacement for SMBFS so if you are still using SMBFS you could try it out.

Still not working though. Help!

---

### Post by Dennis Laumen on 2006-08-17
I must correct myself. This might be a solution after all. I thought it didn't work because Rhythmbox crashed on me (which usually means samba is misbehaving).

I will stress test it by shuffling through a couple of thousand Flac's :D. I suggest the topic starter tries the CIFS approach if he is still experiencing problems. If all is still well tomorrow I will post another reply.

---

### Post by BlueNoteMKVI on 2006-08-18
For what it's worth, I walked in this morning and the music was STILL playing - so that samba share has been steadily connected for nearly 24 hours.  Since I was previously remounting the share at least once (and often 2-3 times) each day, this is a huge improvement.  Maybe Samba got bored with nothing flowing over the connection?

I'll try the CIFS setup also and report back.

---

### Post by Dennis Laumen on 2006-08-19
Everything seems to be fixed by the CIFS solution.

---

