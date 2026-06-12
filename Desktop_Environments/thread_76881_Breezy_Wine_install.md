---
title: "Breezy Wine install"
date: 2005-10-15
forum: Desktop Environments
---

### Post by usbsnowcrash on 2005-10-15
Here is my sources.list
[PHP]
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

deb http://us.archive.ubuntu.com/ubuntu/ breezy universe main restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ breezy-security universe main restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

#not ready
#deb http://us.archive.ubuntu.com/ubuntu breezy-backports main universe multiverse restricted

#wine
deb http://wine.sourceforge.net/apt/ binary/

[/PHP]

So I installed wine libwine and xwine but I can't get wine to start.  When I try to run winecfg I get the following error:
[PHP]
jeff@ubuntu:~$ winecfg
wine: creating configuration directory '/home/jeff/.wine'...
err:module:load_builtin_dll failed to load .so lib for builtin L"gdi32.dll": libstdc++.so.5: cannot open shared object file: No such file or directory
err:module:import_dll Loading library gdi32.dll (which is needed by L"c:\\windows\\system\\user32.dll") failed (error c000007a).
err:module:import_dll Library user32.dll (which is needed by L"C:\\windows\\rundll32.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\rundll32.exe" failed, status c0000135
wine: wineprefixcreate failed while creating '/home/jeff/.wine'.
[/PHP]

---

### Post by The Headhunter on 2005-10-15
I'm having the same problem.  I'm assuming that it's because wine hasn't been updated for breezy but...

---

### Post by medisyn on 2005-10-15
I am having the same error, I dont know what to do :???:

---

### Post by ryke on 2005-10-16
Hi,

i've installed wine from ubuntu repos (not for the wine one), and it works ok.

here you are my sources.list:

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
#deb-src [http://es.archive.ubuntu.com/ubuntu](http://es.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) breezy-extras main restricted universe multiverse
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) breezy-backports-staging main restricted universe multiverse

## Security
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe

---

### Post by manicka on 2005-10-16
[QUOTE=usbsnowcrash]
So I installed wine libwine and xwine but I can't get wine to start.  When I try to run winecfg I get the following error:
[[/QUOTE]
you don't need the libwine package, it mat be causing the conflict although it's just a  dummy transitional package, so I'm not usre.

Try a complete removal of libwine and xwine with synaptic, then reinstall just the wine package and see how that goes.

I to have used the version avaliable in the breezy repos with success. It's the same version that you'll get at winehq anyway.

---

### Post by MikeyXX on 2005-10-16
When I installed the winesetuptk through apt it actually says that it needs to uninstall wine. So I say yes and I get the winesetup but nothing to actually set up because it removed wine. Anyone come across that?

---

### Post by ryke on 2005-10-16
hi,

in my case, I've just installed wine (from ubuntu's repo) and that's all. Afterthat, you can run winecfg from the Console if you need to setup wine.

regards

---

### Post by Sh|fty on 2005-10-27
every time i try to set a drive in winecfg it says 

```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\shifty\\Desktop"'.

```

my fake windows it, /home/shifty/fakewindows

and every time i get to to do an auto detect it says,

```

err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/me dia/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/me dia/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/me dia/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/me dia/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/ho me/shifty'

```

---

### Post by lilricky on 2005-11-09
I get the same error, even tried sudo winecfg :(  anyone got around this?

---

### Post by Sh|fty on 2005-11-10
I still havnt found a wave around it :(

---

### Post by manicka on 2005-11-10
[QUOTE=Sh|fty]every time i try to set a drive in winecfg it says 

```
err:shell:SHGetFolderPathW Failed to create directory 'L"c:\\windows\\profiles\\shifty\\Desktop"'.

```

my fake windows it, /home/shifty/fakewindows

and every time i get to to do an auto detect it says,

```

err:winecfg:apply_drive_changes   unable to define devicename of 'C:', targetpath of '/'
err:winecfg:apply_drive_changes   unable to define devicename of 'D:', targetpath of '/me dia/cdrom0'
err:winecfg:apply_drive_changes   unable to define devicename of 'E:', targetpath of '/me dia/cdrom1'
err:winecfg:apply_drive_changes   unable to define devicename of 'F:', targetpath of '/me dia/floppy0'
err:winecfg:apply_drive_changes   unable to define devicename of 'G:', targetpath of '/me dia/windows'
err:winecfg:apply_drive_changes   unable to define devicename of 'H:', targetpath of '/ho me/shifty'

```[/QUOTE]


Delete the fakewindows directory and start again by running the winecfg command. I'd suggest just sticking with the ~/.wine directory that winecfg makes rather than using the fakewindows directory you are currently using.(Delete this as well '~/wine' before running wincfg again if it exists)

---

### Post by mrgnash on 2005-11-10
I updated my apt/sources list as per ryke's example, then performed an apt-get update which went fine, but I still can't find wine from a search under 'add applications.' :confused:

---

### Post by dott.malcom on 2005-11-10
for me when i run wine or wine cfg it freezes.
If i delete .wine and then rune winecfg i get:
> malcom@cryptomys:~/temp/tps suite$ wine tpsdig2w32.exe
wine: creating configuration directory '/home/malcom/.wine'...
fixme:shell:_SHGetDefaultValue (2,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (6,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (2,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (6,L""), LoadString failed, missing translation?
fixme:shell:_SHGetDefaultValue (23,L""), LoadString failed, missing translation?fixme:shell:_SHGetDefaultValue (31,L""), LoadString failed, missing translation?wine: '/home/malcom/.wine' created successfully.

but then freezes

---

### Post by manicka on 2005-11-10
[QUOTE=mrgnash]I updated my apt/sources list as per ryke's example, then performed an apt-get update which went fine, but I still can't find wine from a search under 'add applications.' :confused:[/QUOTE]

You don't actually use wine as a program from the menus. It's a program used to install and run other programs and as such has no gui except for the winecfg panel which can be launched by typing pressing 'alt-f2' and running the command 'winecfg'

---

### Post by manicka on 2005-11-10
[QUOTE=dott.malcom]for me when i run wine or wine cfg it freezes.
If i delete .wine and then rune winecfg i get:

but then freezes[/QUOTE]

Maybe it's a kde issue with the winehq version of wine. I'm not sure :confused:

---

### Post by dott.malcom on 2005-11-10
i'm under GNOME, not kde

---

### Post by ryke on 2005-11-10
hi,

doing the installation that i've explained before,

and assuming that I wish run the program called "echoview.exe", that is located in: my home directory/vgap/Echov/echoview

in console, I type:
wine vgap/Echov/echoview

and that's all

---

### Post by dott.malcom on 2005-11-10
yes, right, i already work with it in Hoary and didn't give me problems.
It's under Breeze that gives problem

---

### Post by ryke on 2005-11-10
well, i'm using and doing that in Breezy... in case of wine (not for other programs ;-) , no problems for me in both

---

### Post by legout on 2005-11-11
At first i wanna say hello to all (K)ubuntu users. This my first post here in the forum.

For me wine works fine. I´ve installed it yesterday and i´ve play cs 1.6 the whole night ;-).

I´ve did it this way:

Add wine-repos to ur source.list (I know you did but i wanna show MY way)

```

#wine packages
deb-src http://wine.sourceforge.net/apt/ source/ 
deb http://wine.sourceforge.net/apt/ binary/ 

```

Next i install ONLY wine.
```

sudo apt-get update
sudo apt-get install wine
```

So i´ve u have installed other packeges like *libwine* or *xwine* too, i would try to uninstall all this packages. And than reinstall only *wine*.

I´ve deleted an old *.wine* folder. Than i only ran 
```

#wine

```

This will creat a new *.wine* folder. After that i ran 
```
#winecfg
```
to configure my new wine.

That´s all and this worked god for me. So if u wanna try this, unistall all wine-related packages, remove ur *wine* folder and do all that i´ve done.

Legout

---

### Post by jeffreyvergara.NET on 2005-11-12
Hello, I want to compile my own WINE (something I must do... lol) do I only need "build-essentials"? or other things?

---

### Post by DarkTrancer on 2006-02-12
Try typing:  
```
wineprefixcreate
```

Worked for me after spending days trying,so simple :(

Heres a link you can read about it:
[http://72.14.207.104/search?q=cache:jHaEyAOQxLkJ:www.irclogs.ws/freenode/winehq/13Nov2005/2.html+err:winecfg:apply_drive_changes+++unable+to+define+devicename+of+%27C:%27,+targetpath+&hl=en&gl=uk&ct=clnk&cd=4]("http://72.14.207.104/search?q=cache:jHaEyAOQxLkJ:www.irclogs.ws/freenode/winehq/13Nov2005/2.html+err:winecfg:apply_drive_changes+++unable+to+define+devicename+of+%27C:%27,+targetpath+&hl=en&gl=uk&ct=clnk&cd=4")

---

### Post by elamericano on 2006-03-29
I didn't need to do that. Like Mikey I had tried to install winesetuptk with wine. I didn't notice 'til later that wine wasn't installed (thanks synaptic). I went back and installed wine, which removed setup - that's ok, it wasn't needed. Following legout's example...

I had to:
rm -r ~/.wine

then:
wine

then:
winecfg

Unfortunately, when I finally ran:
wine e:\\apps\\perforce

it failed ](*,)  I needed to detach the graphics from the window manager. Now it perforce wants some IE5 dlls. Well, I'm not finished, but it's installed damnit! :cool: 

Good luck to the rest of you - BTW just the sources I had from Automatix were all I needed (0.9.10~winehq1.-2)

---

