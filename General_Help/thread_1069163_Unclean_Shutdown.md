---
title: "Unclean Shutdown"
date: 2009-02-13
forum: General Help
---

### Post by ShadowCloven on 2009-02-13
I'm new to the whole fixing computers thing, so bare with me here. I run windows on my computer, so I don;t know much about Ubuntu.

My parent's computer wouldn't work a few weeks ago, and when I got back from visiting my aunt and taking care of the horses there, they asked me to fix their computer as it wouldn't boot or start up. At first when I took it apart (The computer) I thought the power brick was the problem. It turned out to be the processor, after I cleaned it the computer turned on and ran smoothly, however, about 25% the way through starting Ubuntu, It says under th bar, "Un-Clean Shutdown, checking drives..."
and then I get the black screen saying the "fsck died with exit status 4"

"[COLOR="Red"]*[/COLOR]An automatic file system chack (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root file system mounted in read-only mode. 
[COLOR="DarkOrange"]* [/COLOR]The root file system is currently in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell" 

I've no idea what that means or what to do, It's never happened to me before but I guess when  the processor went, the computer shut down without shutting down the OS first.

---

### Post by jdong on 2009-02-13
Exit 4 of fsck is
```

            4    - File system errors left uncorrected

```

which means there are errors found on the disk that are unexpected and can be considered risky to fix (i.e. it could delete otherwise recoverable files, leave a bigger mess, etc etc).

95% of the time, a root fsck will fix this problem:
```

fsck -fy /dev/sda1

```

where sda1 is the root filesystem. Issue the "mount" command with no arguments to see what is mounted at "/"

**WITH THAT SAID** there is that ~5% chance that fsck will go nuts and completely trash the filesystem beyond recovery if the damage is bad enough! If you've got the spare disk space, I strongly recommend pulling off as much valuable data as you can from the drive by booting onto a LiveCD and attaching an external hard drive. If you need help with this procedure let us know.

---

### Post by ShadowCloven on 2009-02-21
> **jdong said:**
> Exit 4 of fsck is
```

            4    - File system errors left uncorrected

```

which means there are errors found on the disk that are unexpected and can be considered risky to fix (i.e. it could delete otherwise recoverable files, leave a bigger mess, etc etc).

95% of the time, a root fsck will fix this problem:
```

fsck -fy /dev/sda1

```

where sda1 is the root filesystem. Issue the "mount" command with no arguments to see what is mounted at "/"

**WITH THAT SAID** there is that ~5% chance that fsck will go nuts and completely trash the filesystem beyond recovery if the damage is bad enough! If you've got the spare disk space, I strongly recommend pulling off as much valuable data as you can from the drive by booting onto a LiveCD and attaching an external hard drive. If you need help with this procedure let us know.

It stops at "Force rewrite? yes

_ "

I've seen that before while it was running, but it seems to e stuck there now.

---

### Post by ShadowCloven on 2009-02-21
My apologizes for the double post, but I think it finished as it said to reboot Linux, which I did, and the ubuntu screen came up and loaded all the way; now I have a black screen doing absolutely nothing... Help?

---

### Post by jdong on 2009-02-21
Most likely the repair was unable to recover some of the files required to boot Ubuntu; Once you've pulled all the data off I'd recommend an "overwrite reinstall" (uncheck Format in the livecd installer and the installer will just replace the system files leaving configuration and home directories unharmed). If that doesn't work, then do a full reinstall.

---

