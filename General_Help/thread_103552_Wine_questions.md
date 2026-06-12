---
title: "Wine questions"
date: 2005-12-14
forum: General Help
---

### Post by Ruskie on 2005-12-14
Hello everybody,

I'd like to be able to part from from Windows, and I know that Wine could be a way to make Linux run the few applications I can't substitute in the Linux world...
But there are things that still aren't clear to me so I'd like to ask...

1) After installing Wine, do I have to setup (or does it setup for me) some kind of a virtual Win box? That is, am I gonna fake a C:\Windows\ structure somewhere, with actual files and all to make new apps run, or is it all included in one executable?

2) If I have a NTFS partition where I had windows installed, will I be able to run program that are there, or will I be forced to install such programs again in a fake windows machine on Linux?

3) Console / Dos programs. I have VGA Planets, and old game made for Dos. I know that in Windows it runs in a Dosbox, with no actual installation (I make it run from my pendrive where I copied all relevant files). How can I make it run with Wine? I have a .bat file which makes some unzipping (unzip enclosed on disk) and then launch a dos command, but I have not been able to make it work when I tried wineconsole in a previous quick installation of Wine.... Do you know if it is possible? In other words, is there a cmd.exe executable for Wine?

Many thanks for your answers!
Marco

---

### Post by Zaventh on 2005-12-14
After installing wine from the repository, run "wine" as a user. It will automatically setup the structure under ~/.wine.

You'll need to be able to read the NTFS partition in linux first. (get libntfs5). Once mounted, you can "wine /mnt/windows/program.exe" for example straight from the drive.

As for DOS applications, take a look at dosemu.

---

### Post by ninocass on 2005-12-14
also if your running apps from the NTFS drive i found i was getting errors if the program wrote data to config files etc whilst running, i set up a shared FAT32 and copied the programs into there and it ran no problems

Nino

---

### Post by Ruskie on 2005-12-15
[QUOTE=Zaventh]After installing wine from the repository, run "wine" as a user. It will automatically setup the structure under ~/.wine.

You'll need to be able to read the NTFS partition in linux first. (get libntfs5). Once mounted, you can "wine /mnt/windows/program.exe" for example straight from the drive.

As for DOS applications, take a look at dosemu.[/QUOTE]

Ok, thanks.
As for DOS applications, I couldn't make dosemu work properly. I set it up via package, downloaded freedos-dosemu package, tried a little bit of modifications to the .rc file, but it always crashed. Isn't any chance to make dos-apps work with Wine?

thank you
Marco

---

