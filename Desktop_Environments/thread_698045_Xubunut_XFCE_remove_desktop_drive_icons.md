---
title: "Xubunut XFCE remove desktop drive icons"
date: 2008-02-15
forum: Desktop Environments
---

### Post by gjhicks on 2008-02-15
Hi,

Am using Xubuntu 7.10, with the XFCE desktop manager.

My machine has lots of partitions and all are displayed as icons on the desktop.

I can figure out how to remove all of them (XFCE Desktop Settings) but is there a way to remove just some of them?

Thanks,

Geoff

---

### Post by mojoman on 2008-02-29
I think you can do this by changing the mount points in /etc/fstab. If I remember correctly the options in the xfce settings (display removable media, other drives/partitions and whatnot) are sorted by their mount points (whether mounted under /mnt or /media or whatever). I tinkered with this myself when I used xfce and managed to get it to display some partitions  by doing this but I don't remember exactly how I did it. Check where the stuff that shows up is mounted, change one and see if it still shows up. Trial and error...

/mojoman

---

### Post by gjhicks on 2008-03-01
Thanks for the suggestions.

Unfortunately, the partitions are shown on the desktop whether or not they are mounted.

It must be part of the startup routine, to scan the hard disk(s) and generate a desktop with icons for evey partition.

So presence or abscence in /etc/fstab (or /etc/mtab) makes no difference to the desktop display.

Do you know if there is a start-up script that generates the desktop?  Maybe I could tinker with such a script?

Thanks again,

---

### Post by mali2297 on 2008-03-01
> **gjhicks said:**
> Thanks for the suggestions.

Unfortunately, the partitions are shown on the desktop whether or not they are mounted.

It must be part of the startup routine, to scan the hard disk(s) and generate a desktop with icons for evey partition.


It might also be that the desktop shortcuts are saved somewhere and not recreated on each startup. Try to reset the relevant xfce settings, look in the folders ~/Desktop, ~/.cache and ~/.config.

---

### Post by kerry_s on 2008-03-01
The file icon view by default shows 'special' icons for the root of your
filesystem, your home directory, and the trash.  Removable volumes (such as
USB flash drives) are also shown when they are plugged in.  If you'd like to
configure which of these are shown, edit (or create) the file
~/.config/xfce4/desktop/xfdesktoprc to look something like this:

[file-icons]
show-filesystem=true
show-home=true
show-trash=true
show-removable=true

The defaults are all 'true', but you can set ones you want hidden to 'false'.
If an entry is omitted, it defaults to 'true'.  You will need to restart
xfdesktop to make the settings take effect.

if that don't work, the old way i did it back when i used xfce4, was to move the mount point to /mnt. you'll have to edit fstab and change the ones you want to move /media/hd? to /mnt/hd?, so you will also need to create the new folders in /mnt. after all that just reboot and it should all mount in /mnt and not show up on your desktop.

ps: since your changing the mount point you might want to use custom folders.
example:
fstab entry->
/dev/sda1        /mnt/picture's   auto user,noatime,noauto     0       0

then in /mnt, make a folder with that name "picture's".

hope that's understandable.

---

### Post by mojoman on 2008-03-01
> **kerry_s said:**
> the old way i did it back when i used xfce4, was to move the mount point to /mnt. you'll have to edit fstab and change the ones you want to move /media/hd? to /mnt/hd?, so you will also need to create the new folders in /mnt. after all that just reboot and it should all mount in /mnt and not show up on your desktop.

Yes, that's the way I did it. I even think I got the advice from kerry_s :)

---

### Post by kerry_s on 2008-03-01
> **mojoman said:**
> Yes, that's the way I did it. I even think I got the advice from kerry_s :)

:lolflag:
it gets kind of hard to remember, i only use jwm now. pic's->

---

### Post by mojoman on 2008-03-02
> **kerry_s said:**
> :lolflag:
it gets kind of hard to remember, i only use jwm now. pic's->

Nice. I use fluxbox running on Lenny. (Sorry for going OT...)

---

### Post by kerry_s on 2008-03-02
> **mojoman said:**
> Nice. I use fluxbox running on Lenny. (Sorry for going OT...)

sweet, i'm using the etch kernel and lenny for everything else, the lenny kernel gives me bad behavior.

hey are you fully up to date? if so i was wondering if these updates->
libwxbase2.6-0 (2.6.3.2.2-1) to 2.6.3.2.2-2
libwxgtk2.6-0 (2.6.3.2.2-1) to 2.6.3.2.2-2

screwed up your x applications, like xcalc, xedit, xmessage,etc... the rarely used stuff that comes with x, for example, my xcalc was just the outline, in other words it was showing white on white, i fixed it already, but just wondered what happened.

my x stuff looks like this->

---

### Post by mojoman on 2008-03-02
> **kerry_s said:**
> sweet, i'm using the etch kernel and lenny for everything else, the lenny kernel gives me bad behavior.

hey are you fully up to date? if so i was wondering if these updates->
libwxbase2.6-0 (2.6.3.2.2-1) to 2.6.3.2.2-2
libwxgtk2.6-0 (2.6.3.2.2-1) to 2.6.3.2.2-2

screwed up your x applications, like xcalc, xedit, xmessage,etc... the rarely used stuff that comes with x, for example, my xcalc was just the outline, in other words it was showing white on white, i fixed it already, but just wondered what happened.

my x stuff looks like this->

My system is up-to-date as of today and I haven't had these problems. I usually do both an upgrade and dist-upgrade every week or so, so I might have 'missed' that bug. Lenny kernel doesn't do it for my either so I'm using a Sid kernel. Pulled VLC from Sid too but everything else is Lenny. :)

EDIT: BTW, what do you mean "rarely used stuff"? I use xcalc all the time. :)

---

### Post by kerry_s on 2008-03-02
:lolflag:
i use xcalc all the time too, my math sucks. most people i know prefer galcultor, the gtk2 version. anyways i was doing my bills this mourning and that's when i first noticed it, luckly i had 1 in my backup .Xdefaults already done with colors matching a real calculator i have. all the colors are gone from all my x app's, even xedit witch i use for its split feature, so i can work on 2 files at the same time or compare, copy move different parts around, etc...
i haven't got around to putting color back in that yet.

---

### Post by gjhicks on 2008-03-03
Thanks for the reply.

[COLOR="Blue"]The file icon view by default shows 'special' icons for the root of your
filesystem, your home directory, and the trash. Removable volumes (such as
USB flash drives) are also shown when they are plugged in. If you'd like to
configure which of these are shown, edit (or create) the file
~/.config/xfce4/desktop/xfdesktoprc to look something like this:

[file-icons]
show-filesystem=true
show-home=true
show-trash=true
show-removable=true

The defaults are all 'true', but you can set ones you want hidden to 'false'.
If an entry is omitted, it defaults to 'true'. You will need to restart
xfdesktop to make the settings take effect.
[/COLOR]

I have tried the editing of xfdesktoprc approach but this only affects the file-system, home. trash and removable storage icons.  As you can see from the attached screen shot, I have several other partitions displayed on the desktop.

[COLOR="Blue"]if that don't work, the old way i did it back when i used xfce4, was to move the mount point to /mnt. you'll have to edit fstab and change the ones you want to move /media/hd? to /mnt/hd?, so you will also need to create the new folders in /mnt. after all that just reboot and it should all mount in /mnt and not show up on your desktop.
[/COLOR]

Tried adding a mount point to the /mnt/ folder and editing the /etc/fstab file to suit.  However, the /etc/fstab appears to be re-created at each boot, so such changes are lost.

So, these "extra" desktop icons refer to partitions not mentioned in /etc/fstab.

They do not have corresponding mount points in /media/ (or /mnt/) - such mount points are created when the desktop icon is double clicked and the partition is mounted.

They do not have any corresponding files in Desktop (which only contains "Examples").

I reckon that there mus be a start-up script that scans the disk(s) at boot and creates these icons, along with the "code" of what to do if they are double-clicked.

If anyone knows about this script, I would be happy to hear about same.

---

### Post by kerry_s on 2008-03-03
> Tried adding a mount point to the /mnt/ folder and editing the /etc/fstab file to suit. However, the /etc/fstab appears to be re-created at each boot, so such changes are lost.


it shouldn't be recreated each time it's a static file, ubuntu might still be using that 2 section thing, so there would be a static section in fstab.

> So, these "extra" desktop icons refer to partitions not mentioned in /etc/fstab.

They do not have corresponding mount points in /media/ (or /mnt/) - such mount points are created when the desktop icon is double clicked and the partition is mounted.

okay, you lost me here. if you create the folders, they will be there, they don't get deleted.
yes they are mounted when clicked if your using "noauto" in fstab. but if you don't have "noauto" specified it is mounted at boot.

here's what i have for my usb, which is not always plugged in.

---

### Post by gjhicks on 2008-03-03
Thanks for your continued assistance.

Have attached a screen shot, showing the /etc/fstab and contents of /media/:
1) initially
2) after mounting one of the partitions via one of the pesky desktop icons
3) after unmounting that partition.

The /etc/fstab always lookslike this after booting, no matter what editing I do in the previous session.

Also, you will see that the mount point gets created as the partition is mounted and then deleted after it is unmounted.

If I create a 'special' mount point in /mnt/ and add such info to the /etc/fstab:
1) even if that partition is mounted via the /mnt/ mount point, the automatic desktop icon will still mount it as above.
2) the edited fstab is not preserved through the next boot.

Am still puzzled.

---

### Post by kerry_s on 2008-03-03
can you show me your real /etc/fstab not the terminal, i need to see how it's laid out in the file.

press alt+f2
type> mousepad /etc/fstab

take that screen shot.

---

### Post by gjhicks on 2008-03-05
As requested, attached is a screenshot of the /etc/fstab file, opened in mousepad.

Doesn't look any different than the 'cat /etc/fstab' in the terminal screenshot.

Any idea of a startup script that might be creating these desktop icons?

---

### Post by kerry_s on 2008-03-05
whooo, that don't look right. maybe ubuntu is going another way i don't know about.

i'm going to leave you to people actually using ubuntu, as i've never seen the fstab look like that.

good luck to you.

---

### Post by cammin on 2008-03-05
Are you running off the LiveCD? It sure looks like it.
It would explain why your /etc/fstab file doesn't save after a reboot.

It explains the entries in fstab
It also explains the Install icon on your desktop.

---

