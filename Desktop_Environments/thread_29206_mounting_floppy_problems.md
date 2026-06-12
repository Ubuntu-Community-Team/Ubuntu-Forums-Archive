---
title: "mounting floppy problems"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Rodrigo on 2005-04-23
I made a link to a device (floppy drive) and setup it properly (/dev/fd0, and /media/floppy0), but when I click it, it says mount: can't determinate the system file type and none has been especified (or something like that: I have my kde in spanish)...what can I do, what's the problem?

---

### Post by localzuk on 2005-04-23
How are you trying to mount it? Straight from the command line? If so try

sudo mount -t vfat /dev/fd0 /media/floppy0

This should mount it using the filesystem type fat32 (or is it fat - I can't remember)

---

### Post by Rodrigo on 2005-04-23
[QUOTE=localzuk]How are you trying to mount it? Straight from the command line? If so try

sudo mount -t vfat /dev/fd0 /media/floppy0

This should mount it using the filesystem type fat32 (or is it fat - I can't remember)[/QUOTE]

nop, I just make a link to the device... right click on Desktop --> Create new --> Link to device --> Floppy bla bla

I know how to mount it from the command line, but Im not the only one who uses the pc (I own a ciber cafe), and I want to make the life easy for my costumers.

---

### Post by daller on 2005-08-04
Well, I am having the same problem... Or something similar...

I have added the "Storagemedia" to the panel (Or whatever it is named - I use a Danish language-pack)

Clicking on the floppy-drive, gives me these options:

**Floppy drive**
----------------------------------------
- Open in a new window
- Copy
- Paste
- Append to kaffeine playlist
- Unmount
----------------------------------------
- Properties

Clicking on "Open in a new window" apparently mounts the floppy, and opens /media/fd0 (shouldn't that be /media/floppy0 ???)

So far so good, the first time doing this (In the KDE session), it mount the floppy-disc, and shows the content.

Now I would like to use another floppy-disc. I Click on the floppy-drive in the panel, and clicks "Unmount"... Then this message pops up: 

umount: /media/floppy0 is not mounted (according to mtab)
Please check that the floppydisc is inserted correctly.

There we have the problem all over again - /media/floppy0, instead of /media/fd0

---

