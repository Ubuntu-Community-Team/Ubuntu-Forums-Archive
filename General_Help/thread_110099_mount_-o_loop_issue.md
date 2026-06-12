---
title: "mount -o loop issue"
date: 2005-12-30
forum: General Help
---

### Post by Nikusan on 2005-12-30
When I try to mount an .iso (eg: sudo mount -o loop ta.iso /home/dan/ta) I get the error "mount: could not find any free loop device".
Can anyone tell me what I'm doing wrong?

---

### Post by psyguy92 on 2005-12-30
[QUOTE=Nikusan]When I try to mount an .iso (eg: sudo mount -o loop ta.iso /home/dan/ta) I get the error "mount: could not find any free loop device".
Can anyone tell me what I'm doing wrong?[/QUOTE]

If you have several (> 8 I think) iso images mounted, it may fail.

sudo modprobe loop
Does it show that it recognizes 'loop' ?

maybe specifying the vfstype and read only options (default i believe is read+write). 

sudo mount -t iso9660 -o ro,loop /path/to/file/ta.iso /home/dan/ta 


hope it works :)

---

### Post by Nikusan on 2005-12-30
There's aren't any iso's mounted yet.
sudo modprobe loop doesn't do anything. What should it do?
I had previously tried specifing iso9660 and read only, neither helps :(

---

### Post by psyguy92 on 2005-12-30
if the modprobe command isn't giving errors, the loop should be fine.

i am not sure what the problem is. 

Oh Gurus? *calling all gurus*

Sorry that didn't get it.

: /

---

### Post by Nikusan on 2005-12-30
That's a shame..

Appreciate the help though :)

---

### Post by deNoobius on 2005-12-30
OK, I'm new here as my name implies, but I just successfully mounted an ISO and I have a question--did you make the mount point first?  For example, mkdir /media/ta?  

If this is off-base, ignore, but this is what worked for me.  Hope it helps, sorry if it doesn't.

---

### Post by Nikusan on 2005-12-31
The mount point definately exists. Thanks though...

---

### Post by deNoobius on 2006-01-03
[QUOTE=Nikusan]The mount point definately exists. Thanks though...[/QUOTE]

Hmmm....I wonder if it would make a difference if you made the mount point in /media/nameofmountpoint.  Maybe the controller for the loop devices only looks in /media?

---

### Post by BobSongs on 2006-01-10
I was told mounting an .iso was as easy as using the **mount** command. However, it appears to be a bit more difficult than that.

The .iso file I'm using is for a DVD. Here's the command:
```
[COLOR="black"][COLOR="Black"][FONT="Lucida Console"]sudo mount -t iso9660 -o ro,loop /dvd.iso /media/iso[/FONT][/COLOR][/COLOR]
```Here's the output.> mount: wrong fs type, bad option, bad superblock on /dev/loop0,
[INDENT]missing codepage or other error
In some cases useful info is found in syslog - try
dmesg | tail  or so[/INDENT]

So I did what **mount** suggested. Here's the output:
> [4304290.199000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304290.199000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304290.342000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304290.342000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304290.592000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304290.592000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304353.000000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4304353.000000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4304353.182000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4304353.182000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.The current file system is ReiserFS.

**sudo modprobe loop** returns a blank line. So all is well there.
Mount point **/media/iso** is created by root and has the same properties as other folders located here.
I tested this command with a CD ISO and all works fine. Just wondering if the DVD ISO is a different number than iso9660. Thanks.

---

