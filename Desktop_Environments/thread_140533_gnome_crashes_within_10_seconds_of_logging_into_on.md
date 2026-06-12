---
title: "gnome crashes within 10 seconds of logging into one of my accounts"
date: 2006-03-06
forum: Desktop Environments
---

### Post by s|k on 2006-03-06
I get this error:

```
    GNU nano 1.3.8                         File: .xsession-errors

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xse$/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ip70-171-219-145:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ip70-171-219-145:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/ip70-171-219-145:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:18261): WARNING **: Unable to read ICE authority file: /home/bjorn/.ICEauthority
 
```

I tried deleting all the .gnome files, but that didn't work.

Thanks.

---

### Post by Ramses de Norre on 2006-03-06
At the login prompt do ctrl+alt+F1
Then ```
mv /home/bjorn/.ICEauthority /home/bjorn/.ICEauthority.bak
```

And try to login again.

If it works you can delete the renamed file.

---

### Post by ComplexNumber on 2006-03-06
what do you do immediately before it started giving you the error?

---

### Post by Ramses de Norre on 2006-03-06
This is probably the known issue caused by some kde apps. 
Just renaming/removing the ICEauthority file should be enough and you don't loose all your settings then.

EDIT: Hey you changed your whole post!:)

---

### Post by ComplexNumber on 2006-03-06
>  EDIT: Hey you changed your whole post i guess you're talking to me :D. yeah, i considered that he could delete(after making a backup) the .gconf files because they contain the system settings. then i changed my mind - i decided it was perhaps a bit drastic if a simpler solution exists.

---

### Post by s|k on 2006-03-06
[QUOTE=ComplexNumber]what do you do immediately before it started giving you the error?[/QUOTE]
I installed ET, I posted about this in the gaming forum but didn't get an answer. There I said: > I installed ET correctly (I think) I got it to run, managed to get the sound to work, but a funny thing happened: after closing ET my screen resolution wouldn't return to normal. I was fixing the sound, turning it on and off, and each time I quit I had to fix the screen resolution. The last time, before I managed to fix the resolution I scrolled a bit vertically and the part in the top panel that said 'Applications Places System' moved toward the right to flank the volume control and date box.


I'll try Ramses de Norre's suggestion. Be right back.

---

### Post by evilgold on 2006-03-06
you will probably need to use sudo when running

```
mv /home/bjorn/.ICEauthority /home/bjorn/.ICEauthority.bak
```

reason for this error, is usally iceauthority's ownership became root instead of the users.

---

### Post by s|k on 2006-03-06
[QUOTE=Ramses de Norre]At the login prompt do ctrl+alt+F1
Then ```
mv /home/bjorn/.ICEauthority /home/bjorn/.ICEauthority.bak
```

And try to login again.

If it works you can delete the renamed file.[/QUOTE]
This worked! What does that file do? And how do I prevent the game from doing this in the future?

evilgold I was in the other account under su, so I didn't need to use sudo. :)

Thank you.

---

### Post by Ramses de Norre on 2006-03-06
I think that isn't necessary inside your own home directory.

---

### Post by Ramses de Norre on 2006-03-06
The file holds some information used by kde.
I don't think it's harmful to delete it.
However maybe it's also possible to sudo chmod 777 it.
You can try it if you've still got your back up.

---

### Post by engla on 2006-03-06
If this file has information relevant to KDE, how come it's always recreated if I move or delete it? I've seen this login failure some times before and I'm beginning to sour on that file...

---

### Post by openmind on 2006-04-02
[quote=s|k]This worked! What does that file do? And how do I prevent the game from doing this in the future?

evilgold I was in the other account under su, so I didn't need to use sudo. :)

Thank you.[/quote]

The most common reason for this to occur is opening a KDE Application as root. This gives .ICEauthority root ownership for some reason, and will not boot you into your user account after rebooting.

You can revert to shell at the prompt screen, and delete .ICEauthority, as it will "Remake" it on boot. Reboot and There you go!

PS. Don't open KDE Apps as root!

---

### Post by slgriner on 2006-04-03
My gnome is also crashing 10 seconds after login with the following error:

(gnome-session:8312): libgnomevfs-WARNING **: Unable to create ~/.gnome2 directory: Permission denied
Could not create per-user gnome configuration directory '/home/stephen/.gnome2/' : Permission denied

I have not been able to login to the gnome at all on this install.  From a command line with the root user I can not add a new user either using adduser.  Maybe these are related.

Any thoughts???

---

