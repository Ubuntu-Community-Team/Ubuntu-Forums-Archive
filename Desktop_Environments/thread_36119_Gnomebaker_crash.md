---
title: "Gnomebaker crash"
date: 2005-05-21
forum: Desktop Environments
---

### Post by ions on 2005-05-21
Yeah, if you search my posts I've had to ask this before unfortunately.  Anyway, this time when I open it it crashes immediately.  I tried uninstalling it and then reinstalling it.  No difference.  Here's what I get from runnong gnomebaker for a terminal:

```
$ gnomebaker
** Message: splashdlg_set_text - Loading preferences...
** Message: creating [/tmp/GnomeBaker/chris]
** Message: splashdlg_set_text - Detecting devices...
** Message: looking for device [1]
** Message: devices_add_ide_device - probing [hdc]
** Message: node [proc] mount [/proc]
** Message: node [/dev/hda1] mount [/]
** Message: node [/dev/hda5] mount [none]
** Message: node [/dev/hdc] mount [/media/cdrom0]
** Message: devices_write_device_to_gconf - Added [LITE-ON LTR-52327S] [/dev/hdc] [/dev/hdc] [/media/cdrom0]
** Message: ---- key [drive name:], value [hdc]
** Message: ---- key [Can close tray:], value [1]
** Message: ---- key [Can read DVD:], value [0]
** Message: ---- key [Can change speed:], value [1]
** Message: ---- key [Can read multisession:], value [1]
** Message: ---- key [Can play audio:], value [1]
** Message: ---- key [drive speed:], value [12]
** Message: ---- key [drive # of slots:], value [1]
** Message: ---- key [Reports media changed:], value [1]
** Message: ---- key [Can read MRW:], value [1]
** Message: ---- key [Can write MRW:], value [1]
** Message: ---- key [Can write RAM:], value [1]
** Message: ---- key [Can select disk:], value [0]
** Message: ---- key [Can write CD-R:], value [1]
** Message: ---- key [Can lock tray:], value [1]
** Message: ---- key [Can read MCN:], value [1]
** Message: ---- key [Can write DVD-RAM:], value [0]
** Message: ---- key [Can open tray:], value [1]
** Message: ---- key [Can write CD-RW:], value [1]
** Message: ---- key [Can write DVD-R:], value [0]
** Message: looking for device [2]
** Message: Requested device index [2] is out of bounds.  All devices have been read.
** Message: splashdlg_set_text - Loading GUI...

```

I used it just last week just fine.  I guess something that was installed via backports has caused this?

---

### Post by Reb on 2005-05-30
It crashes for me on startup. I'm using Hoary, and I don't have anything from backports. As far as I know, it's the same version that didn't crash on startup three days ago (0.3). I don't know what else changed in the meantime. It fails with the same error you get (device out of bounds) - if that an error.

---

### Post by leoandru on 2005-08-16
I had the same problem this morning and I tried starting from the console using sudo. And it worked.

---

### Post by nhannebicque on 2005-08-26
I have this problem too, under my user profile only. 

Sudoing works ; gnomebaker also works under other user profiles.

Does anybody have a solution to this problem ? Or any idea on how to solve the problem ?

Nicolas

---

### Post by PhilOSparta on 2005-09-15
I also have this problem.

Immediate crash from GUI and terminal, but sudo works.

It would be great to get this working.

Phil

---

### Post by nhannebicque on 2005-09-15
I don't know what did this, but my problem solved itself. Maybe an update replaced something.

Sorry for my very vague answer.

 ](*,)

---

