---
title: "Wine fubard, won't create a drive c"
date: 2006-08-16
forum: Desktop Environments
---

### Post by BongoBob on 2006-08-16
Hello everyone.

I recently went to install my copy of Return to Castle Wolfenstein on my ubuntu box. I got the latest linux install, and ran it, and then realized I deleted the files from my windows box. No biggie, I'll just install it in wine to get the pk3 files. I opened winecfg and added my cdrom drive. Apparently, that caused it to lose my c drive. It is still on my hard drive, but it isn't reading it. I've tried to manually add it, and it still didn't work. I tried uninstalling and reinstalling wine, and that didn't work either.

What can I do to fix this mess :(

EDIT: Forgot to include the errors it gives me. This is written in the terminal when I open winecfg

```
bongobob@RaptorBandito:/cdrom$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
```

When I click the drives tab it says "You don't have a C drive. This is not so great. Remember to click "Add" in the Drives tab to create one!"

When I click add it makes a C: drive and under drive mapping it says ../drive_c, but the Apply button stays gray. When I click browse it says this in the terminal:

```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\bongobob\\Desktop"'.
```

And when I click ok nothing changes. It still doesn't see the C: drive.

---

### Post by Ziox on 2006-08-16
> **BongoBob said:**
> Hello everyone.

I recently went to install my copy of Return to Castle Wolfenstein on my ubuntu box. I got the latest linux install, and ran it, and then realized I deleted the files from my windows box. No biggie, I'll just install it in wine to get the pk3 files. I opened winecfg and added my cdrom drive. Apparently, that caused it to lose my c drive. It is still on my hard drive, but it isn't reading it. I've tried to manually add it, and it still didn't work. I tried uninstalling and reinstalling wine, and that didn't work either.

What can I do to fix this mess :(

EDIT: Forgot to include the errors it gives me. This is written in the terminal when I open winecfg

```
bongobob@RaptorBandito:/cdrom$ winecfg
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
```

When I click the drives tab it says "You don't have a C drive. This is not so great. Remember to click "Add" in the Drives tab to create one!"

When I click add it makes a C: drive and under drive mapping it says ../drive_c, but the Apply button stays gray. When I click browse it says this in the terminal:

```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\bongobob\\Desktop"'.
```

And when I click ok nothing changes. It still doesn't see the C: drive.

Have you tried clicking on the AutoDetect button?

---

### Post by eeefresh on 2008-03-21
Did you ever find a fix for this?  I am having the exact same problem!

---

### Post by anatolica on 2008-04-25
Me too, I am having the same problem and used autodetect too; but it does not create a c driv, giving the same reply. Is there any way to fix this???

---

