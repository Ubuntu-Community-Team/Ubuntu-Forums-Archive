---
title: "Initrd.img hangs at boot up after updating 8.10"
date: 2009-01-26
forum: General Help
---

### Post by John Wiersba on 2009-01-26
(See [http://ubuntuforums.org/showthread.php?p=6617822]("http://ubuntuforums.org/showthread.php?p=6617822") for the solution.)

I just installed quite a number of new packages on a completely up-to-date Intrepid 8.10, using synaptic. Installation went without problems. When I reboot, I see:
[INDENT]Boot from (hd0,0) ext3 ...<UUID>...
Starting up ...
Loading, please wait ...
<CLEAR SCREEN>
usb 2-1: device not accepting address 2, error -71
usb 2-0:1.0: unable to enumerate USB device on port 1
[/INDENT]
After rebooting from a rescue environment, I checked /boot and saw that initrd.img-2.6.27-9-generic had been changed by synaptic. Luckily, I had backed up the previous version of initrd.img-2.6.27-9-generic, so I renamed the bad one and was able to boot from the previous version.

This error is completely repeatable. However, my hard disk is luks-encrypted, so no logs are saved in /var/log. I do see other copies of these same error messages in /var/log/syslog (from a successful boot into my luks-envryped LVM root disk).

So, my questions:
[LIST=1]
[*]   What caused this error?
[*]   How can I help debug this error?
[*]   How can I fix it other than by using a previous version of initrd.img?
[*]   How can I tell which changes were made to initrd.img-2.6.27-9-generic that caused it to fail to be able to boot? I presume the changes were made because of newly loaded modules, but maybe it's something else. Is there something I can diff between the two versions of initrd.img?
[/LIST]

Thanks in advance!

---

### Post by jaygo on 2009-02-02
subscribing

---

### Post by John Wiersba on 2009-02-02
jaygo, see [http://ubuntuforums.org/showthread.php?p=6617822](http://ubuntuforums.org/showthread.php?p=6617822) for the solution.

---

### Post by jaygo on 2009-02-10
thx for the tips and the bug-reporting, John.

I was trying to repair a broken LILO and rescue my system (also using full disk encryption). I could update LILO and copy over the kernels & initrd.img stuff from a working install but I couldn't update the init-related files inside the broken installation, even with all the partitions mounted & unencrypted. Eventually, I had to reinstall from scratch, then copy over my data + settings. 30+ hours troubleshooting and then the reinstall only took about 5 hours to get everything as it was. I'm hoping this stuff will get simpler down the road.

---

