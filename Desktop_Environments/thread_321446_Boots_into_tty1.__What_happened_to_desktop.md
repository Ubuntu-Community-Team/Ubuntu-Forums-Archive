---
title: "Boots into tty1.  What happened to desktop?"
date: 2006-12-18
forum: Desktop Environments
---

### Post by Gen2ly on 2006-12-18
This one is interesting.  I was working on my labtob in the morning, booted later that day and half way through Gnome booting it changes to the shell tty1.  Yes, it's easy to cntl-alt-F7 and get back there, but what the...?  Anyone know how to fix it and what may have caused it?  Other ppl use this computer besides me that won't know what to do.

---

### Post by Gen2ly on 2006-12-19
No one knows how this came about?  I think it might have to do with GDM?  I checked xorg.conf and don't see any reference.  I even built xorg.conf again to see it that did anything.  X11 got updated a couple days ago?  hmm.

I've found similar problems in these threads:

[Starting on tty1 instead of tty7]("http://ubuntuforums.org/showthread.php?t=88490&highlight=tty1")

[Dapper + LTSP: Boot into console login (tty1) instead of gui]("http://ubuntuforums.org/showthread.php?t=167364&highlight=tty1")

The second one is caught my attention because it points to a developer-bug thats similiar to mine, but in Dapper.  A problem with the LTSP program caused a boot into tty1.

[No ldm login on the thinclient]("https://launchpad.net/distros/ubuntu/+source/ltsp/+bug/39294")

This provoked a little interest so I did:
> $ locate ltsp
/etc/foomatic/defaultspooler
/usr/share/locale-langpack/en_GB/LC_MESSAGES/ltsp.mo
/usr/lib/localization-config/woody/ltsp-xfree86-kbd
/usr/lib/localization-config/sarge/ltsp-xfree86-kbd
/usr/lib/localization-config/ltsp.postinst
/mnt/Macintosh_HD/Reconstructor_Directory/remaster/pool/main/l/ltsp
/mnt/Macintosh_HD/Reconstructor_Directory/remaster/pool/main/l/ltsp/ldm_0.124_all.deb
/mnt/Macintosh_HD/Reconstructor_Directory/remaster/pool/main/l/ltsp/ltsp-client_0.124_powerpc.deb
/mnt/Macintosh_HD/Reconstructor_Directory/remaster/pool/main/l/ltsp/ltsp-server-standalone_0.124_all.deb
/mnt/Macintosh_HD/Reconstructor_Directory/remaster/pool/main/l/ltsp/ltsp-server_0.124_all.deb


I think my the fears I had have come true!  I was trying a program called Reconstructor that was to use the Ubuntu Live CD to make a bootable Ubuntu CD.  I did some experimental things like using my Macintosh_HD for additional storage and I think Reconstuctor did something to my / partition.

---

