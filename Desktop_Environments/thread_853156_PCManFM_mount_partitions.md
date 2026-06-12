---
title: "PCManFM mount partitions"
date: 2008-07-08
forum: Desktop Environments
---

### Post by kagashe on 2008-07-08
I am using light weight WMs with pcmanfm on Ubuntu Hardy command line install.

pcmanfm is supposed to mount partitions (though hal) when you click on them. When I try this as normal user it gives errors.

If I open pcamnfm through sudo it works and the partition gets mounted on /media/disk

It appears to be some kind of permission problem.

To check the errors I opened pcmanfm through terminal and the error I get is:
> (pcmanfm:5444): Gtk-WARNING **: Failed to set text from markup due to error parsing markup: Error on line 1 char 73: '-' is not a valid character following a '<' character; it may not begin an element name

which does not appear to be relevant.

kagashe

---

### Post by richtl on 2008-07-08
I'm having exactly the same problem. I've switched back to nautilus for the moment, but would prefer the lighter pcmanfm.

---

### Post by firmit on 2008-07-09
First - if you absolutely want to use Ubuntu CLI - use Feisty. Hardy Heron is not mature yet - or more correctly - LXDE has some issues with it. My advice - use Debian Lenny. LXDE rep is slowly being migrated into Debian rep's - currently in Sid (experimental), and will soon be in Lenny (testing). This means that it may be included into the next Ubuntu release.
----
Okei - to cover the basics (as far as I know) - you obviously have udev and hal installed, and of course you are a member of the group plugdev?

How do you start LXDE? Is gdm the DM? Or do you issue startlxde, startx with .xinitrx {exec startlxde}?

---

### Post by kagashe on 2008-07-09
> **firmit said:**
> First - if you absolutely want to use Ubuntu CLI - use Feisty. Hardy Heron is not mature yet - or more correctly - LXDE has some issues with it. My advice - use Debian Lenny. LXDE rep is slowly being migrated into Debian rep's - currently in Sid (experimental), and will soon be in Lenny (testing). This means that it may be included into the next Ubuntu release.
----
Okei - to cover the basics (as far as I know) - you obviously have udev and hal installed, and of course you are a member of the group plugdev?

How do you start LXDE? Is gdm the DM? Or do you issue startlxde, startx with .xinitrx {exec startlxde}?I am not going back to Gutsy or Feisty because the immature Hardy is working well on my hardware. This question is not related to lxde because pcmanfm could be used even with IceWM.

Yes. I have hal and udev installed. As I have written in the initial post the partition gets mounted when I open pcmanfm as sudo and there is a problem only for the normal user. When I give following command:
> sudo adduser username plugdev
output is:
> The user `username' is already a member of `plugdev'.

I have slim login manager to login to LXDE, openbox, IceWM, Fluxbox, JWM etc.

kagashe

---

### Post by firmit on 2008-07-09
Add yourself to the group:
> sudo usermod -a -G plugdev yourusername
The -a is for adding the 'yourusername' to the group (-G) plugdev. Somebody told me this was the command to use...

You can view your groupmemberships with:
> id
and 
> groups

I myself use GDM - not the slim'est of the DM's, but it does the trick. Also it is easy to set autologin via GUI. 

I did experience some mounting issues when I did not have a DM - I ran **startx**. Maybe it is related? I don't know - maybe someone with skills may help better than me. :) I will try out SLIM.

Added:
You say mounting is no issue when sudo. You mean PCManfm as root I guess? Have you tried mounting via CLI with sudo?

---

### Post by kagashe on 2008-07-09
> **firmit said:**
> I did experience some mounting issues when I did not have a DM - I ran **startx**. Maybe it is related? I don't know - maybe someone with skills may help better than me. :) I will try out SLIM.I was also using startx initially but added slim after installing all lightweight WMs.

I tried the command suggested by you. Does not work.

As you say Ubuntu Hardy may not be mature but I have found the solution to this problem by removing Gnome from full Hardy install as described [on this post]("http://ubuntuforums.org/showpost.php?p=5349611&postcount=145") and I am happy.

kagashe

---

### Post by johnraff on 2008-07-11
Now you've fixed it anyway I guess it doesn't matter, but it might have needed a line in /etc/fstab to get that partition to mount.

I've got a command-line Gutsy install running Openbox and pcmanfm, so quite similar to lxde, and a Windows partition mounts fine. The line in fstab is:```
/dev/sda1	/mnt/win	vfat	noauto,rw,user,umask=077,codepage=932,iocharset=utf8	0	0
```
(With ```
mount /mnt/win
``` in my ~/.profile file it automounts on bootup, with full permissions for me.)
I still havent't figured out how to get Japanese file names displaying on the terminal (they're OK in the file manager), but that's a separate issue...

[Ubuntu Wiki on fstab](https://help.ubuntu.com/community/Fstab) or ```
man mount
```for some help.

**edit:** Sorry I should have made clear the "codepage=932,iocharset=utf8" bits were for my Japanese issue, and irrelevant to the mounting problem...

---

### Post by PCMan on 2008-07-13
> **kagashe said:**
> I am using light weight WMs with pcmanfm on Ubuntu Hardy command line install.

pcmanfm is supposed to mount partitions (though hal) when you click on them. When I try this as normal user it gives errors.

If I open pcamnfm through sudo it works and the partition gets mounted on /media/disk

It appears to be some kind of permission problem.

To check the errors I opened pcmanfm through terminal and the error I get is:


which does not appear to be relevant.

kagashe
As the warning suggests, there should be a meaningful error message in a message dialog, but that message contains <-, which is not allowed in gtk+'s pango markup syntax. So, you see no error message.
However, there shouldn't be any '<-' in the error messages generated by mount. There must be something wrong with your system.

HAL, claimed to be the cure, is actually in a mess and frequently break things. I believed that there's something wrong with HAL on your system, but we need more details.

---

### Post by kagashe on 2009-06-02
Although, this is an old thread I would like to say that this problem was related to PolicyKit and I found the solution on [ArchWki]("http://wiki.archlinux.org/index.php/HAL#Permission_Denied").

I could not mark this thread SOLVED through Thread Tools ??

kagashe

---

