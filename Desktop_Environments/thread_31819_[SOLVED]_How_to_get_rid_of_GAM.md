---
title: "[SOLVED] How to get rid of GAM?"
date: 2005-05-04
forum: Desktop Environments
---

### Post by poptones on 2005-05-04
It seems to tie up resources often running up to 100% CPU time and it locks me into my user mountable partitions soon as they are mounted, preventing them from being unmounted. Killing the process just results in it instantly being respawned, thus requiring a reboot just to unmount user mounted drives!

And why can I not post this in the ohter forum? When trying pto post this to the mailing list forum it says I can't access that page. Why have I apparently been banned?

---

### Post by Marble2 on 2005-05-04
sudo dpkg -r gaim

---

### Post by rwabel on 2005-05-05
[QUOTE=Marble2]sudo dpkg -r gaim[/QUOTE]

He was talking about gam and not gaim.
Isn't gam part of gamin? I don't think you should and can remove that package.

---

### Post by poptones on 2005-05-05
I don't care about "removing" gamin so much as getting it to step out of the way when it's not supposed to be occupying resources. This is almost exactly the same problem that plagued gnome like a YEAR ago before the problems with fam were fixed, now it's the same nonsense all over again because they had to "improve" something that FINALLY actually worked.

According to this ug report

[http://bugzilla.gnome.org/show_bug.cgi?id=169027](http://bugzilla.gnome.org/show_bug.cgi?id=169027)

The problem was fixed in .25, but hoary tells me it's using .26 and the problem sure ain't fixed. I have encrcypted partitions with user mount permissions and they simply refuse to umount when ordered and it IS because gam server is tying them up. I have set the gaminrc file to poll these drives instead of using the kernel monitorin and it does no good, once a drive is opened with gnome it simply cannot be unounted without a reboot. It doesn't cause this trouble with DVDs or CDs but I suspect it would with a USB drive as well and I am certain it's causing trouble with the crypto mapped devices.

---

### Post by rwabel on 2005-05-05
I've no problem with GAM. I can plug my mp3 player and it mounts it automatically (well takes a bit longer than under windows, don't know why) and it opens a nautilus window. I even tried via the ICON and I've no problem unmounting it.

I've also .26 version of Gamin.

sorry but I've no idea what is making your gam to use that much of ressource. does the unmounting not work for u?

---

### Post by poptones on 2005-05-06
OK, let's try this again. I've checked the gamin mailing list, everyone there says the problem has sort of been fixed, but it seems kinda iffy. And through google I found a message from just a couple months back, right before hoary was released officially, and the dev then said they knew there were problems but ther's no time to fix it before hoary is due.

So I ask again: WHAT majikk do I need to cast to get gam server to release my encrypted mapper devices? These should be treated just like any ohter removable devices, if they are not being treated that way it's a bug and if changing the usage in the gaminrc is supposed to actually work then it would seem that's  bug too, or I just don't know the majikk words.

And still no one has explained why I can't post this to the mailing list.

---

### Post by poptones on 2005-06-20
Been I dunno... a month? Still hoping for an answer to this problem... anybody?

---

### Post by skoal on 2005-06-20
[QUOTE=poptones]Been I dunno... a month? Still hoping for an answer to this problem... anybody?[/QUOTE]
Yes, I know.  I gave up on trying to remove the 'gam' server some time ago.  I'll definitely watch this thread for a sol'n.  Post back if you find one, and I will as well.  Teh current sol'n of removing 'gamin' pretty much leaves you with a vintage 1993 Linux distro - aka, the console.

\\//_

---

### Post by poptones on 2005-06-21
I do not know why this did not work the first time I tried it, but here is a "solution" i tried yesterday and it now seems to be working. I have reinstalled ubuntu since the first time I tried it and so cannot explain why it did not work the first time, but perhaps it will work for you.

Create a file in your home directory called .gaminrc (dont forget the leading dot to make it hidden). Gamin recognizes only two commands here so far as I can tell, notify and poll. Notify is what is used by default and the kernel as it is now uses a version that leaves open files and thus locks the directory.

Poll will cause gamin to poll the tree itself and, hoefully, won't leave open files. 

So, for example, if you have a partition mounted as "/foo" you would include this line in your .gaminrc

poll /foo*

Any more partitions you want polled rather than monitored by the kernel you can include on that line, each separated by a space:

poll /foo* /bar* /mnt*

That will cause it to poll any folder on drives /foo, /bar, and anything mounted under /mnt (like USB drives, USB keys, cameras, etc)

Like I said: I don't know why this did not work for me the first time I tried it, so take this entire "resolution" with a big ol' rock of salt. But (this time) it worked for me and I can now use the handy disk mounter panel tool to unmount my user mountable encrypted partitions when they are not in use.

---

### Post by neovatar on 2005-06-27
I have the similar problems, after mounting remote shares via shfsmount or SMB/CIFS in my home (e.g. /home/username/mnt/smb). When browsing this directories with Konqueror (I use KDE), gam_server starts monitoring them for ever, so that an umount is not possible.

Putting 
poll /home/username/smb*

in /home/username/.gaimrc, fixes the issue.

Is there a possibility to configure gamin system wide? Or just via /home/user/.gaminrc ?

---

### Post by poptones on 2005-07-02
I am not one of the developers, but I am pretty sure gamin runs at the user level, and on a per user basis. This could be a problem if you have several user accounts on the same machine I suppose, but in the example I am using here (encrypted partitions) one would assume even if there are multiple accounts on the machine only a few would be allowed access to any given encrypted partition.

I think there should be some sort of "system wide" fix regarding encrypted fileshares, since encrypted partitions are not secure at all if they cannot be unmounted once mounted. So what other conditions should this be required that are not already addressed?

The next release will probably bring with it a whole assortment of NEW issues just like this, since it will have beagle built in by default. Doesn't beagle also use its own filesystem notifier?

---

