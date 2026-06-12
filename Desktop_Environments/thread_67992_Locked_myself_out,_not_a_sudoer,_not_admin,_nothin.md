---
title: "Locked myself out, not a sudoer, not admin, nothing, help!"
date: 2005-09-21
forum: Desktop Environments
---

### Post by Steve Smith on 2005-09-21
I've somehow removed myself from all groups, except the group that is my username.  I'm not on the sudoers list.  I don't have a second user account on the system.  I can't sudo, can't get in as root, is there anything I can do?!

---

### Post by macgyver2 on 2005-09-21
[QUOTE=happysteve]I've somehow removed myself from all groups, except the group that is my username.  I'm not on the sudoers list.  I don't have a second user account on the system.  I can't sudo, can't get in as root, is there anything I can do?![/QUOTE]
 If you have a LiveCD (any LiveCD...doesn't have to be Ubuntu) you can boot the LiveCD, mount your root partition somewhere temporary...like under /mnt, say) then edit the group file from your real system to add your username back into the groups it's supposed to be in.  When you're done editing, unmount and boot like normal.

---

### Post by karuptdata on 2005-09-21
try this in terminal type sudo root psswd and it will ask you to change pass for root. Enter a new password then inside term again type sudo gdmsetup under the security tab there should be a spot that says allow root to login at gdm select that option. Then you will be able to at least log into root from gdm at least to set permissions for user..I DONT RECOMMEND USING ROOT FOR ANY OTHER PURPOSE!!!!! I FOUND OUT THE HARD WAY:)

---

### Post by macgyver2 on 2005-09-21
[QUOTE=karuptdata]try this in terminal type sudo root psswd...[/QUOTE]
Hmm...issue there is that he can't sudo.

---

### Post by karuptdata on 2005-09-21
crap thats right sorry......dont mind me live cd would be the way to go..

---

### Post by varunus on 2005-09-21
You could try booting up in rescue mode and editing the group settings there...  This puts you automatically as root, but in the console.  Post here if you need more help...

---

### Post by az on 2005-09-21
[QUOTE=varunus]You could try booting up in rescue mode and editing the group settings there...  This puts you automatically as root, but in the console.  Post here if you need more help...[/QUOTE]
If you gave your root acount a password, then booting into recovery mode will ask you for it and you will still be screwed.  If you hadn't, this is the way to go.

You can use the installer instead of downloading the live cd (or using another live cd)  Just boot it and let it go to the partitionner.  Then do CTRL-ALT-F2 and do

mount /dev/hda5 /mnt #(I assume that your partition is hda5, here.  Put in the correct device!)
thendo
chroot /mnt


Now, instead of editing the group settings, use adduser.  It creates a home directory and everything...

adduser (whatever)
and it will prompt you for a password.

Reboot and you are done.

---

### Post by macgyver2 on 2005-09-21
[QUOTE=azz]If you gave your root acount a password, then booting into recovery mode will ask you for it and you will still be screwed.  If you hadn't, this is the way to go.[/QUOTE]
I always forget about recovery mode!

[QUOTE=azz]Now, instead of editing the group settings, use adduser.  It creates a home directory and everything...

adduser (whatever)
and it will prompt you for a password.

Reboot and you are done.[/QUOTE]
I'm not 100% sure about this, but I don't think adduser lets you add a user that already exists...

---

### Post by Steve Smith on 2005-09-21
[QUOTE=macgyver2]I always forget about recovery mode!


I'm not 100% sure about this, but I don't think adduser lets you add a user that already exists...[/QUOTE]
 wow, thanks for the major discussion about me, that was quick!  About 10 minutes after I posted, tho, I had a long-shot idea, and it worked.  Though I'd call it a serious security loophole.  If anyone knows how to plug it, please let me know!

I rebooted into recovery mode, it came up as root.  sudo visudo, stuck my own username on the list, rebooted, logged on as normal and I was away!  Reset my permissions in Users and Groups, the did visudo again to take out what I put in.  And eureka!

---

### Post by cwaldbieser on 2005-09-21
[QUOTE=happysteve]wow, thanks for the major discussion about me, that was quick!  About 10 minutes after I posted, tho, I had a long-shot idea, and it worked.  Though I'd call it a serious security loophole.  If anyone knows how to plug it, please let me know!

I rebooted into recovery mode, it came up as root.  sudo visudo, stuck my own username on the list, rebooted, logged on as normal and I was away!  Reset my permissions in Users and Groups, the did visudo again to take out what I put in.  And eureka![/QUOTE]
This is not a security hole.  You can do the same thing on most personal workstations, regardless of the OS.  Basically, once you allow someone to have physical access to the machine, it is pretty much impossible to protect your machine via the OS, because an attacker can bypass the OS.

Also, as a practical matter, many people lock themselves out of the machine at one point or another.  If you really need to protect sensitive materials, you can consider encryption, which prevents an intruder from discovering what the data means, irrespective of the OS.

---

### Post by Steve Smith on 2005-09-22
Ah, that makes sense!  I don't actually need to protect my data, just curious.  And seeing I make a bit of a  habit of locking myself out at the moment, probably a good idea if I leave things as they are... thanks :)

---

### Post by fordfan753 on 2005-09-22
If you don't like the idea of this backdoor, you can always delete the recovery mode entry from the /boot/grub/menu.lst

Alternatively you can set a root password, which will, I think, only let you log into the recovery console if you have this password. To set a root password just use
```
sudo passwd root
```

---

### Post by Steve Smith on 2005-09-22
[QUOTE=fordfan753]If you don't like the idea of this backdoor, you can always delete the recovery mode entry from the /boot/grub/menu.lst

Alternatively you can set a root password, which will, I think, only let you log into the recovery console if you have this password. To set a root password just use
```
sudo passwd root
```[/QUOTE]
 Thanks, I'll bear that in mind when I'm a bit more competent and not likely to need to let myself back in!

---

