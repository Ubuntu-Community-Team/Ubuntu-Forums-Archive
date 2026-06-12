---
title: "Command-line partition reboot selection"
date: 2009-02-26
forum: General Help
---

### Post by cosmocrazy on 2009-02-26
I know that executing [FONT="Courier New"][COLOR="DarkRed"]shutdown -r now[/COLOR][/FONT] from the terminal will restart the computer. I don't know how to restart into a specific partition. This would be useful for say, rebooting into a non-default OS without having to be in front of the computer. 

In OS X, you can use the "bless" command to reboot into a specific partition:

```
/usr/sbin/bless --device /dev/<devNode> --setBoot --legacy --nextonly
```

Is this possible to achieve in Ubuntu and Windows? (I have Cygwin on Windows, but would prefer a native Windows command-line solution if possible)

---

### Post by Yellow Pasque on 2009-02-26
My hunch is that this is not possible due to fundamental differences between Apple's EFI and the venerable PC BIOS. For your sake, I hope to be proven wrong. :P

---

### Post by dcstar on 2009-02-27
> **cosmocrazy said:**
> I know that executing [FONT="Courier New"][COLOR="DarkRed"]shutdown -r now[/COLOR][/FONT] from the terminal will restart the computer. I don't know how to restart into a specific partition. This would be useful for say, rebooting into a non-default OS without having to be in front of the computer. 
........
Is this possible to achieve in Ubuntu and Windows? (I have Cygwin on Windows, but would prefer a native Windows command-line solution if possible)

In Ubuntu you simply have various /etc/boot/menu.lst templates set up to boot in whatever partition you have, and a script that replaces your existing menu.lst with the one you want before rebooting.

For Windows, who cares.......    ;-)

---

### Post by cosmocrazy on 2009-02-28
Man....I was hoping there was a better way. I guess I won't be able to control it unless I overwrite the MBR with GRUB and install some ext3 reader on Windows.

---

