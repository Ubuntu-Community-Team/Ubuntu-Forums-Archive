---
title: "Paths?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Guns90 on 2006-08-24
I have PC programs I want to use on my (now) ubuntu pc.  I have installed wine using [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine), but I don't understand what to use for the Path to Program at the 'Adding applications to the menu' section.  Their example (eg.  wine "C:\Program Files\World of Warcraft\WoW.exe" ).  I have loaded my cd into cdrom1 and a 'Math Review PC' icon appears on my desktop, so I assume that it is loading there by default.  When I click on the icon the cdrom-1 file browser window shows three folders (data, install, and Mind Power Math Review) and four icons (Autorun.inf, Play exe. RevRefs, and SetUp.exe).  When I access the terminal, the prompt is gary@my-desktop:~$.  I have tried several paths such as wine :C:\gary\my-desktop\Math Review PC\setup.exe and wine :C:\desktop\Math Review PC\Autorun.inf. Can someone tell me what I am doing wrong, please?

---

### Post by sbassett on 2006-08-24
> **Guns90 said:**
> I have PC programs I want to use on my (now) ubuntu pc.  I have installed wine using [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine), but I don't understand what to use for the Path to Program at the 'Adding applications to the menu' section.  Their example (eg.  wine "C:\Program Files\World of Warcraft\WoW.exe" ).  I have loaded my cd into cdrom1 and a 'Math Review PC' icon appears on my desktop, so I assume that it is loading there by default.  When I click on the icon the cdrom-1 file browser window shows three folders (data, install, and Mind Power Math Review) and four icons (Autorun.inf, Play exe. RevRefs, and SetUp.exe).  When I access the terminal, the prompt is gary@my-desktop:~$.  I have tried several paths such as wine :C:\gary\my-desktop\Math Review PC\setup.exe and wine :C:\desktop\Math Review PC\Autorun.inf. Can someone tell me what I am doing wrong, please?

First, run winecfg. If this has been done, then open the "Math Review PC" icon and right-click setup.exe and select open with wine. If you need to perform this from the terminal try this

```
wine /media/cdrom1/Setup.exe
```

please note, the above needs to match case exactly.
If this does not work, try /media/cdrom0 or /media/cdrom.
This will (hopefully) install this on your pc. If you need to access these installed programs, they will be contiained within:

```
~/.wine/drive_c/
```

From this point forward, this rest of this will look just like a Windows system, containing Windows, Program Files, etc.

---

### Post by Guns90 on 2006-08-24
I apologize for taking so long to get back to you.  I tried right-clicking on the Setup.exe. icon and then 'Open with another application'.  Wine is not one listed.  How do I check to see if wine has in fact been installed, then get it to list in the applications list?

I also tried the terminal commands you listed.   I got...

gary@my-desktop:~$ wine /media/cdrom1/Setup.exe
wine: cannot find '/media/cdrom1/Setup.exe'
gary@my-desktop:~$ wine \media\cdrom1\Setup.exe
wine: could not load L"c:\\windows\\system32\\mediacdrom1Setup.exe": Module not found
gary@my-desktop:~$

---

### Post by sbassett on 2006-08-25
I would suggest, then, copying these files to a folder within your /home/username directory.

---

