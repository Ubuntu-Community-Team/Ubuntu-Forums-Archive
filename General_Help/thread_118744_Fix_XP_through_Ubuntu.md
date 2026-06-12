---
title: "Fix XP through Ubuntu?"
date: 2006-01-17
forum: General Help
---

### Post by angeleyes on 2006-01-17
I somehow lost a boot file(<Windows root>/system32/hal.dll.)for my XP so it wont boot up.It is in my GRUB menu.
I am wondering if there is any way I can find and reinstall the boot file for XP through Ubuntu?
I like Ubuntu,but my husand and kids like the XP,so Im trying to find a way to fix xit so I can run it.

---

### Post by o_fortuna on 2006-01-17
[QUOTE=angeleyes]I somehow lost a boot file(<Windows root>/system32/hal.dll.)for my XP so it wont boot up.It is in my GRUB menu.
I am wondering if there is any way I can find and reinstall the boot file for XP through Ubuntu?
I like Ubuntu,but my husand and kids like the XP,so Im trying to find a way to fix xit so I can run it.[/QUOTE]
In order to fix boot files for XP, you need the XP install disk. Without it, it may be extremely difficult to fix the file because Ubuntu can't support writing to NTFS (the Windows XP file system). If you have the install disk, simply insert it into the computer, restart, and there should be an option to fix the operating system, or maybe transfer files to it.

Come to think of it, there is a way to write to Windows using [Captive]("http://www.jankratochvil.net/project/captive/"). Look on the link to see how to use it. This will let you write to Windows, so all you'd need are those files. Try a [Google Search]("http://www.google.com/search?q=hal.dll&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official") for the files. Or you could look in the Windows CD or the "Recovery" CD you probably got with the computer.

I've never used Captive, so I can't account for its stability. One thing you can do is use normal Ubuntu support to read NTFS and backup your needed files, then reinstall the whole Windows XP operating system. If you choose to reinstall windows, though, you have to go through some additional procedures to be able to use Ubuntu again (something with the install disk, but I don't know what it is, sorry :( ).

---

### Post by lamego on 2006-01-17
[QUOTE=angeleyes]I somehow lost a boot file(<Windows root>/system32/hal.dll.)for my XP so it wont boot up.It is in my GRUB menu.
I am wondering if there is any way I can find and reinstall the boot file for XP through Ubuntu?
I like Ubuntu,but my husand and kids like the XP,so Im trying to find a way to fix xit so I can run it.[/QUOTE]
Is it a NTFS partitition ? If yes you can't mount it read-write (required for the fix), on your case i think using the windows recovery console is a better option.
(OOops, forgot about captive as stated on the previous post)

---

### Post by soulestream on 2006-01-17
just use the windows XP disk to fix it. No need to reinvent the wheel. Just boot up the XP install disk go ro recovery console and copy the file from the disk back over

soule

---

