---
title: "Script for easy wine &amp; steam setup."
date: 2006-04-26
forum: Gaming &amp; Leisure
---

### Post by Johme on 2006-04-26
[http://home.comcast.net/~websysdesign/wine-setup.sh]("http://home.comcast.net/~websysdesign/wine-setup.sh")

This script will take a basic installation and install wine, Microsoft Core fonts, MSI installer, ActiveX Controls, DirectShow Filters, and Steam.

Type 'sudo sh /path/to/download/wine-setup.sh'.

Changing which is installed is modifiable by editing the top of the file.

Requirements: 
Having additional repositories enabled in your /etc/apt/sources.list file.
Running it under 'sudo' (NOT 'su')

Updates:
Added chown -R so that user can execute the wine data...
Hopefully fixed the apt-get errors.... At least for x86, which is all i can test.


Comments/Suggestions?

---

### Post by hollywoodb on 2006-04-26
ran this in a 32-Bit chroot (amd64 system), already had wine installed, here's what I've got so far:

```

Reading package lists... Done
Building dependency tree... Done
wine is already the newest version.
wget is already the newest version.
cabextract is already the newest version.
gzip is already the newest version.
tar is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Conflicts: wine-doc but 0.0.20050524-2 is to be installed
E: Broken packages

```
(no big deal, wine-doc isn't necessary anyways)

```

wine-setup.sh: line 27: rpm: command not found
wine-setup.sh: line 28: cd: /usr/src/rpm/RPMS/noarch/: No such file or directorywine-setup.sh: line 29: alien: command not found

```
perhaps add these to the inital apt-get install command since they aren't necessarily widely used on a debian-based system... or perhaps just start with a deb... msttcorefonts-1.2 is available for ubuntu

```

+ /usr/bin/ttmkfdir
/var/tmp/rpm-tmp.11011: line 40: /usr/bin/ttmkfdir: No such file or directory
error: Bad exit status from /var/tmp/rpm-tmp.11011 (%build)


RPM build errors:
    Bad exit status from /var/tmp/rpm-tmp.11011 (%build)
File "msttcorefonts-1.3-4.noarch.rpm" not found.

```
I didn't have ttmkfdir installed either... at this point I also realized that the script had to redownload all the font .exe files, perhaps have it save them until the script has completed and then clean up

Other than that it works well, nice work :D

EDIT: found a MAJOR showstopper... since wine is called by root (sudo to run script), Steam is installed as root, and everything it installs is owned by root.  User won't be able to run steam.exe (access denied errors).  I fixed this by 'sudo chown -R $USER:$USER /home/$USER/.wine'

---

### Post by adamkane on 2006-04-26
AMD64 is always an exception. If you make any discoveries regarding AMD64, then post your findings in the AMD64 forums, otherwise no one will know about it.

Thanks for the new script!

---

### Post by Johme on 2006-04-26
hollywoodb:
It apears the reason the rpm and ttmkfnt errors happened was because alien and ttmkfnt didn't download with apt-get.
Maybe your version of Ubuntu (unstable?) doesn't have it, or the extra repositories aren't enabled.. Alien should download rpm as a dependency.

I will add the chown part tommorow, I need some sleep <_<...

---

### Post by hollywoodb on 2006-04-27
actually, since apt-get works sequentially, the missing wine-doc package aborted the rest of the apt-get command at the beginning... I had missed that part.

---

### Post by tburns on 2006-04-27
Steam sucks. And it would be nicer to have a native version of HalfLife 2. How is the performance with an emulator?

---

### Post by Zeroedout on 2006-04-28
[quote=tburns]Steam sucks. And it would be nicer to have a native version of HalfLife 2. How is the performance with an emulator?[/quote]

Yes, native versions of any game would be much nicer (personally, i will refuse to use wine, unless absolutly neccessary eg. streaming gamecube games with the loader that supports 100 Mb), but getting source codes for games and porting is an expensive and time consuming process. When WINE is an option, it is a good option, and Wine Is Not an Emulator (WINE). I refer you to debunking WINE myths [http://www.winehq.org/site/myths](http://www.winehq.org/site/myths) . Myth 1 covers the emulator and slowdown myth. Read the entire page though, very informative.

---

### Post by Johme on 2006-04-28
[QUOTE=tburns]Steam sucks. And it would be nicer to have a native version of HalfLife 2. How is the performance with an emulator?[/QUOTE]

Yes, Steam isn't my favorite platform either, but it's the only way to play HL2 & Mods....  Native version isn't likely, unless steam gets ported soon. Valve won't want to lose control of distribution.

Important: **W**ine **I**s **N**ot an **E**mulator.
It's a compatibility layer.

Meaning: If the reqired part of the API is implemented, the program can still make system calls and other hardware specific things that an emulator can't, giving Wine comparable (or even better) speeds versus the native OS.

---

### Post by abyssspecter on 2006-05-06
okay, heres my problem. Steam doesntturn out to be a actual excecutable file. its a .lnk file. what should i do to be able to run this?

---

### Post by ZylGadis on 2006-05-07
As far as I know, .lnk files are windows shortcuts - the functional equivalent of a symbolic link. Are you sure you have the right thing?

---

### Post by rickc on 2006-05-14
Great script... I'm glade I found it... thanks guys/gals

---

### Post by anxie on 2006-05-19
Where does this install steam. I'm not real great at finding installed programs :(

---

### Post by Johme on 2006-05-21
[QUOTE=anxie]Where does this install steam. I'm not real great at finding installed programs :([/QUOTE]
It installs it (with default configs) at: 

$YOUR-HOME-DIR$/.wine/drive_c/Program\ Files/Steam/Steam.exe

---

