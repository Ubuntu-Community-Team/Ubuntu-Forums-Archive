---
title: "Some questions from a Xandros user"
date: 2005-11-30
forum: Desktop Environments
---

### Post by php4us on 2005-11-30
Hi everyone,

I'm a Xandros OS user for about a year now. I've been wanting to explore Kubuntu and finally installed Breezy today.

Coming from Xandros, I'd like to ask some questions:

1. Being a minimalist that I am, I like to see some of my menu fonts smaller. With Xandros, I can manipulate gnome applications from "gnome-control-center". I think Ubuntu does not have that. Is there another application that corresponds to this?

2.  I notice that there is no way to automatically mount a samba partition, or is there? I might be missing it.  Can you please walk me thru doing that?

3. I also noticed that I can't access my windows partition.  When I click System > Storage Media, I see hda1. But I can't access it.  Any clue?

4. This is not Xandros specific, but is there a way to make web cams work with Ubuntu? 

5. Also, is there a program that I can "view the desktop" so i can place it as a link?

6. When installing a network printer from a windows machine, Utilities > Printing Manager > Add Printer wizzard > SMB printer > then I selected the machine that has the printer.  I got this error : NT_STATUS_ACCESS_DENIED. Any clue how to fix this? I'm sure this is not about that machine.

More later.  Kubuntu is real cool. I hope to stay long :D

---

### Post by otake-tux on 2005-11-30
> 3. I also noticed that I can't access my windows partition. When I click System > Storage Media, I see hda1. But I can't access it. Any clue?
Try mounting it first. type
mount "path to hda1" and then cd into it. should work.
example
mount /dev/hda1
I dont know where hda1 is cause I'm on a windows machine but what you type should look like that.

---

### Post by Mobus on 2005-11-30
the reason you can't access your windows partition is because you are not root.  so you need to re-mount it with you as the user.  Provided that your windows partition is the first partition on your first HD, it should be called hda1.  if it is the first partition on the second hard drive, it will be hdb1. if it is the second partition on the first HD, the it is hda2, and so on and so forth.  from there, you should type 

sudo umount /media/hda1

with hda1 being your windows partition, change the name to suit.  Then, remount it

sudo mkdir /mnt/windows
sudo chmod 777 /mnt/windows 
sudo mount -o uid=whateveryournameis /dev/hda1 /mnt/windows

and your windows partition should be working fine.  As for mounting your samba partition automatically, edit you fstab in the etc folder (I beleive its in /etc, someone correct me if I'm wrong)  basically you'd be adding the last line in my example above and putting it in that text file, and whatever mount options are in that file should be automatically mounted.  in fact, you can mount the windows partition in fstab also.

Webcams usually don't work for linux if you are able to run them on windows.  Webcams are little pricks that think that they're so cool that they're going to try to force you on windows.  Its possible to make them work, but unless you think you can't live without the webcam, I would not reccomend bothering.

I also was coming from Xandros when I went to Ubuntu, although, I like the GNOME version better.   Quite honestly, I don't like KDE, but I must admit it has its ups.  Good Ubuntuing!

---

### Post by php4us on 2005-11-30
Hi,

Thanks for the responses. Here's an update:

[QUOTE=php4us]
1. Being a minimalist that I am, I like to see some of my menu fonts smaller. With Xandros, I can manipulate gnome applications from "gnome-control-center". I think Ubuntu does not have that. Is there another application that corresponds to this?
[/quote]
This one's really needed. Any comments?

> 
[COLOR="Silver"]2.  I notice that there is no way to automatically mount a samba partition, or is there? I might be missing it.  Can you please walk me thru doing that?
[/COLOR]
Per comments above, this has been answered.

> 
[COLOR="Silver"]3. I also noticed that I can't access my windows partition.  When I click System > Storage Media, I see hda1. But I can't access it.  Any clue?[/COLOR]

This, too.

> 
4. This is not Xandros specific, but is there a way to make web cams work with Ubuntu? 

I have a client that is contemplating on hopping to Linux. I'm looking closely at Ubuntu right now (not Xandros for some licensing problem).  But web cam over Yahoo IM is an integal part of their operation -- that is, webcam conferencing with foreign counter parts. Any possible solutions?

> 
5. Also, is there a program that I can "view the desktop" so i can place it as a link?

Pending question.

> 
[COLOR="Silver"]6. When installing a network printer from a windows machine, Utilities > Printing Manager > Add Printer wizzard > SMB printer > then I selected the machine that has the printer.  I got this error : NT_STATUS_ACCESS_DENIED. Any clue how to fix this? I'm sure this is not about that machine.[/COLOR]

I solved this trying around.

***
Thanks guys.  Hope to hear from you more.

---

### Post by php4us on 2005-11-30
Here's another one -- very important.

In Xandros, the root is separate from the user. Meaning, the ordinary user cannot install new software or even accidentally delete some system files if they don't have the root password.  This is very important in the case of an office setting where there is a system admin that manages all the PCs and not allowing the users to install new apps.  

I noticed that Ubuntu has a different way of doing this.  One can change virtually everything by using sudo.  Is there a way we can separate root from the user?

---

### Post by php4us on 2005-12-01
bump.

New problem. I inserted my usb drive, konqueror goes up, but unfortunately, there's an error:

An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

I investigate to see if sdb1 is mounted, it is. Any comments?

---

### Post by GeneralZod on 2005-12-01
[QUOTE=php4us]Here's another one -- very important.

In Xandros, the root is separate from the user. Meaning, the ordinary user cannot install new software or even accidentally delete some system files if they don't have the root password.  This is very important in the case of an office setting where there is a system admin that manages all the PCs and not allowing the users to install new apps.  

I noticed that Ubuntu has a different way of doing this.  One can change virtually everything by using sudo.  Is there a way we can separate root from the user?[/QUOTE]

In a word - yes :)

You'll need to create a separate "root" account, and mess around with the /etc/sudoers file.

Note that any new additional new users created after the initial, default user can *not* use sudo unless someone with root access explicitly enables it for them (again, using /etc/sudoers).

[QUOTE=php4us]bump.

New problem. I inserted my usb drive, konqueror goes up, but unfortunately, there's an error:

An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

I investigate to see if sdb1 is mounted, it is. Any comments?[/QUOTE]

Make sure KDE is 100% up-to-date - this was a huge bug in the initial release of Kubuntu 5.10 which (for me at least) was fixed by the latest updates.  You'll have to restart KDE before the fix takes effect.

---

### Post by adriantry on 2005-12-01
Hi

I started my Linux life with Xandros, too, which was a very helpful introduction. Now I feel very at home with Kubuntu.

[QUOTE=php4us]1. Being a minimalist that I am, I like to see some of my menu fonts smaller. With Xandros, I can manipulate gnome applications from "gnome-control-center". I think Ubuntu does not have that. Is there another application that corresponds to this?[/QUOTE]

Try System Settings / Appearance / GTK styles and fonts. It works perfectly for me.

Adrian

---

### Post by adriantry on 2005-12-01
[QUOTE=php4us]4. This is not Xandros specific, but is there a way to make web cams work with Ubuntu?[/QUOTE]

There is a java instant messenger called Mercury that can apparently do web cams. In the future (KDE 4), Kopete will support web cams.

[QUOTE=php4us]5. Also, is there a program that I can "view the desktop" so i can place it as a link?[/QUOTE]

Right click the panel, select Add to Panel, then Special Button, then Desktop Access. This will give you a "view the desktop" type of button on your panel.

Adrian

---

### Post by php4us on 2005-12-01
Whew! Thanks guys.  You've been helpful so far. I realized that this thread is worth bookmarking for any [k]ubuntu newbie.  I'll keep asking whenever I encounter problems and I hope you'll have patience even with dumb questions ;)

One thing that seem to have remained in my series of questions is that of the windows partition mounting.  There is that "shell" way of mounting it. But, is there a "Xandros" type where it is automatically mounted at boot time?  XFM is so cool that it even shows the Windows drive as "Drive C".  I hope there's a Kubuntu workaround.

Also, former Xandros folks, can you confirm if my observation is correct?  Xandros also uses KDE. But after installing Kubuntu on the same machine, I noticed that Kubuntu runs and loads the programs faster.  Is this your experience too? Or am I just excited with Kubuntu that my perception isn't balance? I'm asking this because I'm researching/testing on what Linux distro to install in our company network-wide.

Thanks.

---

### Post by php4us on 2005-12-03
Just wanted to *bump* this thread.  

I'm really interested in honest comments and observation from former Xandros users.  Is my observation correct that Kubuntu loads programs faster than Xandros? If so, what may be the reason for this?

---

### Post by dw5437 on 2005-12-03
I have used Xandros for years and I love it. I have used Ubuntu and Kubuntu for about a year and love these also. The only difference I have noticed is Xandros boots slower. I have noticed no difference in running or installing programs. I still use Xandros/Kubuntu/Windows XP Pro and Frugalware. They are all equally as good. Well equally as far as Linux goes but I would gladly dump the Windows if I could get my games to run in Linux.

Cheers

---

