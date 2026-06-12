---
title: "WIndows XP BSoD after grub update"
date: 2010-11-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by saxuntu on 2010-11-22
My wife is using a Dell 10 with a dual boot Windows XP and Ubuntu 10.04.  I have no idea about the grub update making XP through a fit, probably coincidence,  but i'm getting a "STOP 0x000000ED UNMOUNTABLE_BOOT_VOLUME" Error Message "STOP 0x000000ED UNMOUNTABLE_BOOT_VOLUME" Error Message BSoD.  I hoping some might be able to answer 2 things.

1) If it is a coincidence

2) How the heck do you access the Dell Diagnostic partition.  I get the boot menu open and hit enter on the Diagnostic option and it just boots to the grub menu.

Thanks for any help.

p.s. Mods - if this should be somewhere else sorry.  I haven't been to the forums in a while and couldn't find the Windows section (guess it got thrown in the fridge).

---

### Post by oldfred on 2010-11-22
So we can see what is where:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

If you are getting to windows errors, I would think grub is working ok. If it is just windows corruption, you may be better in a windows forum. 

Have you tried running windows chkdsk?

---

### Post by saxuntu on 2010-11-23
I can't even access windows for anything.

On the booting diagnostic bit.  Its not listed in grub, but it is available within nautilus.  Should I add it to grub to see if that will work?  Why am I asking?  I'm going to try that.  

Will try this and other advise after holiday weekend.  Thanks for the help, we both appreciate it.

---

### Post by oldfred on 2010-11-23
XP CHKDSK
chkdsk drive /p /r
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information. Run chkdsk several times, until no more errors are detected.
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

