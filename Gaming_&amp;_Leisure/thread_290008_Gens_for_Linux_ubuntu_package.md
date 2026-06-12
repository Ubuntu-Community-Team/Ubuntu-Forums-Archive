---
title: "Gens for Linux ubuntu package"
date: 2006-10-31
forum: Gaming &amp; Leisure
---

### Post by megamaced on 2006-10-31
[COLOR="Red"]**Gens is a Sega Megadrive (Genesis), 32x and MegaCD emulator**[/COLOR].

[SIZE="6"][COLOR="Red"]Information in this post is out of date and links probably don't work. Please use Gens/GS[/COLOR]

[http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)[/SIZE]





--------------------------------------------------------------------------------------------------------------------
[SIZE="5"]**Packages:**[/SIZE]
--------------------------------------------------------------------------------------------------------------------

[SIZE="4"]Gens/GS 2.15.5 M5[/SIZE]

*Gens/GS is a version of Gens for Linux maintained by GerbilSoft. The main goal of Gens/GS is to clean up the source code and combine features from various forks of Gens. *

**For Hardy Heron (Intrepid)**
[http://info.sonicretro.org/images/a/a9/Gens-2.15.5-gs-m5-1_i386.deb](http://info.sonicretro.org/images/a/a9/Gens-2.15.5-gs-m5-1_i386.deb)
**For Suse, Fedora, Mandriva**
[http://www.zshare.net/download/50439696022b92a5/](http://www.zshare.net/download/50439696022b92a5/)
**Source**
[http://info.sonicretro.org/images/6/6c/Gens-2.15.5-gs-m5.tar.gz](http://info.sonicretro.org/images/6/6c/Gens-2.15.5-gs-m5.tar.gz)
**Website**
[http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)
**Forum Thread**
[http://ubuntuforums.org/showthread.php?t=959074](http://ubuntuforums.org/showthread.php?t=959074)

[SIZE="4"]Gens 2.15.5[/SIZE]

*Built from the offical Gens for Linux CVS tree. Features include integrated GTK interface & openGL support. Use this package if you want to run the "official" Gens.*

**For Hardy Heron (Intrepid)**
[http://www.zshare.net/download/20011849e53d2280/](http://www.zshare.net/download/20011849e53d2280/)
**For Dapper Drake (Edgy, Feisty, Gutsy)**
[http://www.zshare.net/download/20011749ecd028fe/](http://www.zshare.net/download/20011749ecd028fe/)
**For Suse, Fedora, Mandriva**
[http://www.zshare.net/download/2001200202565a76/](http://www.zshare.net/download/2001200202565a76/)
**Source**
[http://www.zshare.net/download/20011662a458fbbf/](http://www.zshare.net/download/20011662a458fbbf/)

--------------------------------------------------------------------------------------------------------------------
**[SIZE="5"]How to install:[/SIZE]**
--------------------------------------------------------------------------------------------------------------------

1) Download the Gens package

2) Double click the file and choose "Install Package"

or

Open a terminal and type

```
sudo dpkg -i gens_*.deb
```

To uninstall, type:

```
sudo aptitude remove gens
```

--------------------------------------------------------------------------------------------------------------------
[SIZE="5"]**News:**[/SIZE]
--------------------------------------------------------------------------------------------------------------------

[SIZE="3"]**UPDATE: 05/10/08**[/SIZE]

Gens 2.15.5 released!

A bug fix release, fixing various issues with the GUI enabling / disabling options. The new feature for this release is internal save state for SCD games. Thanks to ilguido for the patch.

[SIZE="3"]**UPDATE: 01/09/08**[/SIZE]

Gens 2.15.4 released!

This is a good release for ATi users. You can now enjoy openGL support!

[ 1488458 ] opengl: optimization for ati card

[SIZE="3"]**UPDATE: 24/08/08**[/SIZE]

Gens 2.15.3 released!

[ 1923815 ] Fix startup crash

[SIZE="3"]**UPDATE: 20/06/08**[/SIZE]

Gens 2.15.2 released!

The Gens available here is no longer a fork. Thats the big news for this release. I have merged all the patches that are used in Gens 2.15.2 upstream to CVS.

Big thanks to ilGuido for adding an option to choose your CD-ROM drive (Options > Current CD Drive). Thats the big feature for this release.

If anyone wants to submit a patch, you can use the Gens sourceforge page at [http://sourceforge.net/projects/gens/](http://sourceforge.net/projects/gens/)

As always, keep hacking!

[SIZE="3"]**UPDATE: 09/06/08**[/SIZE]

No the new package does not offer anything thats already currently available. Its simply a version bump to stop confusion with other packages labelled version 2.14

[SIZE="3"]**UPDATE: 07/06/08**[/SIZE]

New package uploaded! The big news is that Gens now supports real MegaCD / SegaCD CD-ROMs. Gens assumes that your CD-ROM is mapped to dev/hdc, but you could create a symlink if its not. Thanks to ilGuido for the patch

[SIZE="3"]**UPDATE: 19/05/08**[/SIZE]

I've uploaded a new version of Gens for you all, albeit unofficial in that it strays from CVS. The changelog is at the bottom of this post

[SIZE="3"]**UPDATE: 26/04/08**[/SIZE]

The Hardy Heron package is here but unfortunately Gens CVS just segfaults for me. Even the Gutsy package segfaults with Hardy. This could be a major incompatibility issue between Gens and the Hardy libraries should this issue not just be isolated to me.. At this point I suppose we should all be crying out to programmers to kick-start the Gens development again!

PS. The Gens stable package is OK with Hardy

[SIZE="3"]**UPDATE: 08/03/08**[/SIZE]

Unfortunately Wryun, our Gens guru, is currently unable to devote much time to coding these days. Rather then let Gens go unmaintained again, I am calling out for developers to pick up where Wryun left off. For those who want to code, the priorities to fix are:

- add the ATI patch in

- clean up joystick support
- work out what's going on with the GUI updates, and put the OpenGL option into the Glade files
- fall back properly to no OpenGL when OpenGL fails
- rework the config files parsing (it's kinda ugly, and more significantly relies on unique chars which potentially conflict with things in filenames. I changed from [] to *? for this reason).
- work out why it loses the plot sometimes on fullscreen/window switch

Enhancements:
- XVideo support for those whose OpenGL isn't working - see the latest generator source
- J-Cart support - one of the recent console emulator releases has it, can't remember which (PSP?)
- run all the files through a code beautifier so the indentation/style gets half-way consistent (didn't do it myself because it would make the repository a mess of changes; wanted to wait until the basic patches were in and 2.13 was something stable)
- rewrite the terrifying joystick code

[SIZE="3"]**UPDATE: 08/11/07**[/SIZE]

Finally got around to compiling Gens CVS 20070625 with the Gutsy libraries. You can find the Gutsy package in the downloads section of this post. As for an altogether new CVS package, well you will have to harass Wryun for that!

[SIZE="3"]**UPDATE: 29/06/07**[/SIZE]

Several users have been reporting crashes in the new Gens CVS package (cvs20070625). The package was built in an Dapper Drake environment and this might be causing problems for Feisty Fawn users. I have now re-packaged Gens in an Feisty environment and maybe this will solve the problems. You can find the updated packages in the "Packages" section of this thread

Note that you need openGL support to run Gens CVS.

[SIZE="3"]**UPDATE: 25/06/07**[/SIZE]

Gens-2.13-cvs20070625 released!

Okay people, time to get excited! The first glimpse of Wryun's work is upon us!! I have made a package of the latest snapshot in CVS. Be aware that it may contain bugs and should be considered unstable until Wryun releases the final product.

[SIZE="3"]**UPDATE: 14/06/07**[/SIZE]

Great news! Gens is being actively maintained again and we can expect a new version in the coming weeks! An alpha build will be released soon, followed by a stable 2.13. Ubuntuforums member wryun is responsible for the new work being carried out, and we thank him for his contributions! I'll be packaging the new version(s) so be sure to check back here!

[SIZE="3"]**UPDATE: 16/05/07**[/SIZE]

Gens-2.12b released!

--------------------------------------------------------------------------------------------------------------------
[SIZE="5"]**Changelog:**[/SIZE]
--------------------------------------------------------------------------------------------------------------------

## gens-2.15.5
- [ 2138114 ] fix the bugs of the gui (by ilguido)

## gens-2.15.4
- [ 1488458 ] opengl: optimization for ati card (by nbondoux)

## gens-2.15.3
- [ 1923815 ] Fix startup crash (by Mark Schreiber)

## gens-2.15.2
- New CD-ROM drive chooser (by ilGuido)

## gens-2.15.1
- Version bump to stop confusion with the Gens 2.14 linux package
- No other changes

## gens-patched20080606 changes
- CD-ROM support (assumes /dev/hdc). (by ilGuido)

## gens-patched20080519 changes
- Fixed segfault on startup. (by MonkeeSage)
- Set OpenGL mode default to off, since it's crashprone if you don't have
  the proper bpp selected (and sometimes even if you do). (by garron)
- The Pause button on the keyboard pauses emulation. Same as Escape, but
  Escape also quits the game when gens is started with --quickexit.Ideally
  these should all be remappable, but that has to wait for another day.(by garron)
- Add a listing for --quickexit to gens --help. (by garron)

## gens-cvs20070625 changes
- ROM window now integrates with main interface
- Full command line options now implemented
- OpenGL turned on by default
- Better joypad support
- Tons of other undocumented improvements!

## gens-2.12b changes
- Open ROM dialog box remembers last used directory
- Source code now compiles using gcc4

## gens-2-12a changes
- Rebuilt using proper Debian way; no more checkinstall :)

- Changed package naming scheme
- Dependency list now included

---

### Post by anti-trend on 2006-11-01
**Disclaimer:** I am *not* an Ubuntu user; I'm running Debian 'Etch'.

But this package worked perfectly for me, both installing and removing with apt, along with the k-menu entry. If nothing else, this proves baseline Debian compatibility.

Good job dude,
-AT

---

### Post by zcal on 2006-11-04
I'm using Dapper and the package installed perfectly, though it would not open with the GUI installer when I tried.  Haven't tried uninstalling it yet as I'm still trying to work out my issues with the emulator, [which you can look at here]("http://www.ubuntuforums.org/showthread.php?p=1713241#post1713241").

---

### Post by profshiny on 2006-11-04
Thank you *very* much for this.  I'm on 6.06, and it works for me.  I've only tried Shining Force so far, but I'll test some others and get back to you.

Few minutes later, I've tried a few more games.  This runs smoother than Gens on my XP install.  The 32x games run perfectly as well(but are, unfortunately, still 32x games,) and hopefully I'll find some of my old Sega CDs soon to try that out.  The only hitch I've found so far is that, when I tried 48khz sound, the emu spat out a godawful noise, but 22khz (default) and 44khz (what I generally use anyway) work fine.

Okay, last edit, I promise.  It won't let me select or configure a CD rive, so it won't try to play CDs.  I don't have any .isos around, so I can't test those.  If anyone sees a reason why, I'd sure appreciate the feedback.

I lied, it plays CDs, you just have to hit ctrl+b.  Durr.

---

### Post by Sethiano on 2006-11-06
This worked like a charm!

Many thanks! I have struggled to get Gens to work for a long time now.

---

### Post by megamaced on 2006-11-08
Good to hear it's working for most people.

I find it strange that the ubuntu repositories have Zsnes and vbaexpress, but don't have a Sega emulator as well. Okay, well they have DGen, but that sucks :D

---

### Post by jm2003uk on 2006-11-08
Just installed it and is working brilliantly. Tried DGen a while ago but wasn't impressed. Glad to have stumbled across this.

---

### Post by hikaricore on 2006-11-08
Oh gawd now I have to dig toejam and earl out of my backup archives on the external hard drive.  hehe

Thanks for sharing.  :)

---

### Post by Chrono86 on 2006-11-12
That package worked great!

Now for one minor problem...whenever I try to change the resolution Gens just quits...here's what bash says:

> The program 'gens' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContextTag'.
  (Details: serial 1990 error_code 158 request_code 148 minor_code 144)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


But if I run it with the --sync flag it doesn't tell me any more...anybody else having this problem?

---

### Post by Frem on 2006-11-12
Very, very nice. 
There was an occasional half second pause when switching between levels in Sonic 3 & Knuckles, but nothing that interfered with gameplay. Also, the colors seemed slightly flat when running in windowed mode. But fullscreen is Where It's At anyway, so I'm not complaining.

---

### Post by megamaced on 2006-11-15
It's possible to get Gens running on very old hardware with a bit of tweaking. I've got it running perfect full screen on an old P2 laptop with no direct rendering. For older hardware it's best to disable OpenGL in Gens and change the frame skip from 'auto' to '3' or '4'.

---

### Post by narceron on 2006-11-16
NEWBIE ALERT

Where should I extract it to?

---

### Post by megamaced on 2006-11-16
You can extract the zip archive wherever you want to. The Gens installer is in the zip archive.

---

### Post by TheRingmaster on 2006-11-23
could you make a .deb for the xe-emulator?
 
[http://www.xe-emulator.com/](http://www.xe-emulator.com/)

---

### Post by TheRingmaster on 2006-11-23
I get this error

> petey@Data:~$ sudo -i
root@Data:~# dpkg -i gensforlinux_3.5rc-1_i386.deb
dpkg: error processing gensforlinux_3.5rc-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gensforlinux_3.5rc-1_i386.deb
root@Data:~# 




---

### Post by NESFreak on 2006-11-24
> **TheRingmaster said:**
> I get this error

my system denies it's existence to

NESFreak

---

### Post by bebop_tango on 2006-11-26
It seems the package is corrupted...

---

### Post by LinuxSince92 on 2006-11-26
It installs fine but I can't use the emu because of a missing lib.  If anyone out there knows where to find libpangocairo-1.0.so.0 please let me know where to find it.  I've been looking for it for a little while.  :confused: ](*,)

---

### Post by megamaced on 2006-11-26
Try:

```
sudo apt-get install libpango1.0-0
```

---

### Post by megamaced on 2006-11-26
> **TheRingmaster said:**
> I get this error

> **NESFreak said:**
> my system denies it's existence to

NESFreak

> **bebop_tango said:**
> It seems the package is corrupted...

I downloaded the package myself and got the 'No such file or directory' error. Strange because the version I have stored on my hard drive doesn't do that. It seems as if the package became corrupt on the Ubuntu servers somehow. Anyway I have removed it and uploaded it again. Should be OK now, let me know.

---

### Post by Mike'sHardLinux on 2006-11-26
Works for me in Edgy. Thanks!

---

### Post by bebop_tango on 2006-11-27
The zip archive is fine, but I still cannot open the .deb package.

:-k

---

### Post by IronMan7491 on 2006-11-27
Works great. Thank you very much!

---

### Post by NESFreak on 2006-11-28
> **megamaced said:**
> I downloaded the package myself and got the 'No such file or directory' error. Strange because the version I have stored on my hard drive doesn't do that. It seems as if the package became corrupt on the Ubuntu servers somehow. Anyway I have removed it and uploaded it again. Should be OK now, let me know.

alternative server?

NESFreak

---

### Post by d3x7r0 on 2006-11-29
The emulator looks fine but the sound keeps slowing down like the computer can't handle it :? I have an Audigy 4 on a Pentium 4 3.06GHz so I don't think the computer is to blame... And I really wanted to play those good ol' sonic games... :(

---

### Post by sharperguy on 2006-12-01
Works perfectly w/o beryl, but no netplay :( - grayed out

---

### Post by cookfromfrozen on 2006-12-02
Either the zip or deb is corrupted at the mo, not working here.

---

### Post by sharperguy on 2006-12-02
install it with "dpkg -i" instead of gdebi graphical installer and it should work

---

### Post by bebop_tango on 2006-12-04
It finally worked!

:D 

Well, I tried to install it with "dpkg -i" before and it didn't work... this time it did.

I was using an old rpm package converted with alien. The sound was buggy - it couldn't run full speed at 60fps.

But now with opengl support it runs wonderful!

:D

---

### Post by megamaced on 2006-12-05
I've removed the Gens package from the Ubuntu forums and uploaded it to ZShare instead. The link to the package is in the first post and [here as well]("http://www.zshare.net/download/gensforlinux_3-5rc-1_i386-deb.html"). Hopefully this will bring an end to the corrupt package problems that some users have been experiencing. :)

---

### Post by leech on 2006-12-05
What would be nice is if we could get the package in Universe or Multiverse.  Just an apt-get install gens away.

Leech

---

### Post by NESFreak on 2006-12-08
> **megamaced said:**
> I've removed the Gens package from the Ubuntu forums and uploaded it to ZShare instead. The link to the package is in the first post and [here as well]("http://www.zshare.net/download/gensforlinux_3-5rc-1_i386-deb.html"). Hopefully this will bring an end to the corrupt package problems that some users have been experiencing. :)

tnx now it works.
btw added the package to MOTU/Packages/Candidates as a request

NESFreak

---

### Post by megamaced on 2006-12-11
> **NESFreak said:**
> btw added the package to MOTU/Packages/Candidates as a request

The package isn't finished yet! I need to configure the dependencies first :p

---

### Post by cborga1985 on 2006-12-11
It even works on amd64. Just do 
```
sudo dpkg -i --force-architecture gensforlinux_3.5rc-1_i386.deb
```
**Reminder** Doing this often can be dangerous but I think it's safe to do with this.

---

### Post by psyke83 on 2006-12-13
> **TheRingmaster said:**
> could you make a .deb for the xe-emulator?
 
[http://www.xe-emulator.com/](http://www.xe-emulator.com/)

Here you go:
[http://www.zshare.net/download/xe_06-11-01-1_i386-deb.html]("http://www.zshare.net/download/xe_06-11-01-1_i386-deb.html")

Nice emulator, but desperately needs opengl or xv support :)

---

### Post by TheRingmaster on 2006-12-14
> **psyke83 said:**
> Here you go:
[http://www.zshare.net/download/xe_06-11-01-1_i386-deb.html]("http://www.zshare.net/download/xe_06-11-01-1_i386-deb.html")

Nice emulator, but desperately needs opengl or xv support :)
thanks again for this

---

### Post by psyke83 on 2006-12-19
Hi,

I've updated the gensforlinux 3.5rc package, adding a fix that allows the File Open dialog to remember the last visited directory (instead of defaulting to ~/.gens every time). I have also attached the newer "rc4" from cvs, but on my system I have noted stuttering sound despite the same video fps as the older version.

Version 4rc: [http://www.zshare.net/download/gensforlinux_4rc_cvs-1_i386-deb.html](http://www.zshare.net/download/gensforlinux_4rc_cvs-1_i386-deb.html)
Version 3.5rc_fix: [http://www.zshare.net/download/gensforlinux_3-5rc_fix-1_i386-deb.html](http://www.zshare.net/download/gensforlinux_3-5rc_fix-1_i386-deb.html)

Enjoy!

---

### Post by Charlie51 on 2006-12-26
Can anyone get their joypad to work with this?

I can redefine the keys but they don't work?

---

### Post by Valinski on 2007-01-01
Works great! Thx for the package. I was having trouble with the source code stuff but that was quick and easy. cheers

---

### Post by rolando2424 on 2007-01-01
SWEET MOTHER ALL THAT IS WORTH EXISTING...

THIS ROCKS!

Edgy install, and it's working perfectly :D

---

### Post by megamaced on 2007-01-04
> **psyke83 said:**
> I have also attached the newer "rc4" from cvs, but on my system I have noted stuttering sound despite the same video fps as the older version.

Can you tell me where you found the 'RC4' source code? I was under the impression that 'RC3.5' is an unofficial build and is the latest release so far? Does RC4 include OpenGL?

Thanks

---

### Post by psyke83 on 2007-01-06
> **megamaced said:**
> Can you tell me where you found the 'RC4' source code? I was under the impression that 'RC3.5' is an unofficial build and is the latest release so far? Does RC4 include OpenGL?

I got it from here: [http://aur.archlinux.org/packages/gens-cvs/](http://aur.archlinux.org/packages/gens-cvs/)
Also, I believe this is the same (webcvs): [http://gens.cvs.sourceforge.net/gens/Gens-MultiPlatform/linux/](http://gens.cvs.sourceforge.net/gens/Gens-MultiPlatform/linux/)

The "Open Rom" dialog fix is from member KingFisher's post on Gentoo Forums here: [http://forums.gentoo.org/viewtopic-t-204287-postdays-0-postorder-asc-start-75.html](http://forums.gentoo.org/viewtopic-t-204287-postdays-0-postorder-asc-start-75.html)

I haven't compared the code of RC3.5 to RC4 in depth, but to my recollection it appeared that RC4 is based on RC3.5, and OpenGL support is included.

Regards,
psyke83

---

### Post by sub7 on 2007-01-06
Will this ever be available in amd64?

---

### Post by wryun on 2007-01-10
I think the reason why some people are getting stuttering (at least on auto frame skip) is that the Linux Gens version has no auto frame-skip implemented if sound is enabled. That means setting frame skip to Auto is basically like setting it to 0. So, if ever your computer can't handle a frame in the audio time, it's all over (crackle).

Having said that, I'm surprised that so many people have this issue, but it's certainly a problem on my Celeron 300 (overclocked to 450!) ;)

Anyway, I hacked together a few lines to 'fix' it as long as the required frameskip is less than 2, at the cost of the audio being very slightly out of sync (I don't care about it, you can't tell - purists can hate me now). I'm feeling lazy, though, so someone will have to want it for me to post it.

PS For Debian users like me - that package won't work on anything except experimental at the moment, since it requires GLIB_2.4.

---

### Post by jon_benge on 2007-01-24
This is geat! Thanks

---

### Post by disturbedite on 2007-02-09
i don't mean to revive an old thread but...
i've gotten permission (and encouragement) from the maintainer/author of gens32 (for windows) to port it to linux.  imho, at least on windows, gens32 is *the best* genesis/md/32x emulator there is.  (unfortunately, neither gens or gens32 run with wine).  he gave me the source code, the only problem is, i have no experience compiling assembly.

i have nasm installed.  (feel free to recommend any other asm compiler).  could someone here who has experience compiling asm provide a tutorial for compiling gens?

or if that would be too tedious/difficult, i could send someone the source and they could upload the deb package for the rest of us to try out.  (i'd also prefer a tar package for a general linux binary/executable, so the author can post it on his site obviously).

thanks

EDIT:  nvm, i found [this]("http://www.ubuntuforums.org/showthread.php?t=166980").

---

### Post by ViperKnight on 2007-02-11
I'm on an AMD64 system and this deb isn't working for me:( 

It installs fine but when I try to run it I get this in the terminal:
```
gens: error while loading shared libraries: libSDL-1.2.so.0: wrong ELF class: ELFCLASS64

```

I have libSDL and all other dependencies installed.....but I think it has something more to do with using a 64bit version instead of the 32bit files.  Any ideas?

---

### Post by dannyboy2k on 2007-03-04
When I do this:

```
 dpkg -i gensforlinux_3.5rc-1_i386.deb

```

I get this message:

```
dpkg: error processing gensforlinux_3.5rc-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gensforlinux_3.5rc-1_i386.deb

```

When I do this:

```
gdebi gensforlinux_3.5rc-1_i386.deb
```

I get this:

```
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
gdebi error, file not found: gensforlinux_3.5rc-1_i386.deb

```

What?

I'm a bit of a newbie. Running Edgy.

Can anybody help me?

---

### Post by megamaced on 2007-03-08
I've rebuilt the package. Download and install the new version instead :)

---

### Post by disturbedite on 2007-03-14
thanks so much for the release megamaced!  i checked the about dialog, and even tho you said its based on 2.12a it still says 2.12-rc3, is that the same release, or has it just not been updated in the dialog box?

isn't gens as an organized project dead?  it is afaict.  i've checked the gens site, forums, and sourceforge site and can't find anything more than a couple years old.  anyone feel free to correct me if i'm wrong, but it appears that gens as an organized project is dead and only survives through random ppl making patches....  at least its  not entirely dead in that manner.

(gens _and_ gens32 don't run under wine, they throw a directx error:  Oops...  Error with lpDD_Back->SetSurfaceDesc).

i am an acquaintance of the developer of [gens32]("http://gens32.emubase.de/"), which is a HUGE improvement over gens, but unfortunately, its only for windows.  i contacted him over im to inquire about creating a linux port, and he encouraged me and sent me the source.  i then noticed it didn't contain any make files or config files and he doesn't have any linux experience so...
i finally made a little headway in getting some info out of him about it recently...
he told me that gens32 is currently being developed with msvc2005.  that made my stomach turn.  so this brings me to my question.
is there a way to port it to linux being that its a vc2005 project?  my guess is no.
but...i did strike up the subject of how we (him & i) could go about creating a linux port and he said we'd basically have to recreate the project (obviously based on the win port/version) for use with other compilers.  thats about the current state of affairs as far as gens32 is concerned.

anyone that would be willing to help please contact me or him via the gens32 forum or email him.

---

### Post by megamaced on 2007-03-15
As far as I am aware, the Linux port for Gens hasn't been maintained in a long time. They may be waiting for a new release of Gens for Windows, which if I understand correctly, is undergoing a complete re-write. On the other hand, perhaps they got bored and left it for dead

The version of Gens I've packaged is an unofficial build that contains OpenGL support. Basically it's just a patched version of the official build. I think it was only ever a 'one-off' though as the author has also dispanded this project (from what I can tell).

To be perfectly honest with you, somebody should fork this OpenGL version of Gens for Linux and build a new community around it. It would be much easier using it as the building blocks for a new Gens, rather then starting from scratch with Gens32. I don't have programming experience so I don't know for sure.
If you can get a team around you then I'll be more then happy to contribute! Like I said, I don't have programming skills but I know how to build a decent Debian / Ubuntu package :)

Let me know

---

### Post by disturbedite on 2007-03-15
thanks for the response.  i think you're prolly right that forking this version with opengl support would be easier than basically recreating gens32.  i don't have programming experience either, but i can/could take care of much of the rest.  the only experience i have creating deb packages is with checkinstall, i've done that a lot, but understand that it isn't the preferable way of creating/maintaining a debian package.  so if you have experience creating them the proper way, your skills woud be valuable.

i'm not sure about how to generate interest in a new gens-based project.  i guess i'll post a new thread about it.

---

### Post by D-- on 2007-03-23
> **psyke83 said:**
> Hi,

I've updated the gensforlinux 3.5rc package, adding a fix that allows the File Open dialog to remember the last visited directory (instead of defaulting to ~/.gens every time). I have also attached the newer "rc4" from cvs, but on my system I have noted stuttering sound despite the same video fps as the older version.

Version 4rc: [http://www.zshare.net/download/gensforlinux_4rc_cvs-1_i386-deb.html](http://www.zshare.net/download/gensforlinux_4rc_cvs-1_i386-deb.html)
Version 3.5rc_fix: [http://www.zshare.net/download/gensforlinux_3-5rc_fix-1_i386-deb.html](http://www.zshare.net/download/gensforlinux_3-5rc_fix-1_i386-deb.html)

Enjoy!

Does anyone have these files? ZSHARE is dead right now (10:35 AM China time, March 24). I had someone in the USA try too, just in case it was the Great Firewall blocking me. It's not.

---

### Post by megamaced on 2007-03-24
They appear to be working now

---

### Post by Benshiro on 2007-03-25
For anyone on AMD64 getting libSDL error messages:
Despite installing all the compatibility libraries and updating libSDL, I found I had to manually retrieve the 32 bit version of libSDL-1.2.so.0 in order to get gens to work on my AMD64. Simply unpack the rpm from here [http://rpm2html.osmirror.nl/libSDL-1.2.so.0.html](http://rpm2html.osmirror.nl/libSDL-1.2.so.0.html) and copy libSDL-1.2.so.0 to /usr/lib32/. Other than --force-architecture for the install this is all I had to do to get it running.
I'm pretty clueless as to how this stuff works, just thought I'd put this out there in case anyone has had a similar problem.
Finally I can play Bare Knuckle again!

---

### Post by D-- on 2007-03-26
Thanks, I got it when it came back up.

WOW! What a difference.

The one in the Ubuntu sources was running with skipping at a solid 2GHz on my PC. What a brutal beating :( This one runs beautifully even at 800MHz.

---

### Post by megamaced on 2007-03-27
> **D-- said:**
> The one in the Ubuntu sources was running with skipping at a solid 2GHz on my PC. What a brutal beating :(

Are you refering to DGen? That emulator hasn't been updated in years. In fact, I think it's totally abandoned now. I never got it to work properly anyway

---

### Post by HeXy on 2007-03-28
thanks very much for this :D

---

### Post by D-- on 2007-03-30
> **megamaced said:**
> Are you refering to DGen? That emulator hasn't been updated in years. In fact, I think it's totally abandoned now. I never got it to work properly anyway

No. There was an old old old Gens version in the Ubuntu repositories. Not sure if it was Multiverse or Universe or what. I had to remove it with Synaptic before installing yours.

Again, kickass job.

---

### Post by bhuthogg on 2007-04-22
hi there this works for me but when i shift between full and windowd mode it freezes my ubuntu (had to power down) is there a 2.14 ver ?

---

### Post by megamaced on 2007-04-23
As far as I know, Gens 2.12a is the latest version for Linux. I don't think anyone is maintaining the project anymore.

I can't replicate your full screen issues. I've tested Gens on Dapper, Edgy and Feisty and I've not experienced any problems. Maybe you are running Compiz / Beryl or have altered something with your system?

---

### Post by bhuthogg on 2007-04-23
> **megamaced said:**
> As far as I know, Gens 2.12a is the latest version for Linux. I don't think anyone is maintaining the project anymore.

I can't replicate your full screen issues. I've tested Gens on Dapper, Edgy and Feisty and I've not experienced any problems. Maybe you are running Compiz / Beryl or have altered something with your system?

thanks for your reply,

to be honest i have just started playing with ubuntu. but haven't altered anything to my knowledge, bit of a bummer that its freezin up on me on feisty i have lotsa old roms id like to play too :(

maby its cos im on the 7.04 beta? ive dun all the updates.

thanks

Bri

---

### Post by megamaced on 2007-04-23
Maybe try toggling OpenGL on and off. Or try changing the OpenGL or SDL screen resolutions.

---

### Post by megamaced on 2007-04-27
**[SIZE="4"]Compile Gens for 64-BIT users (Please test!)[/SIZE]**

Below are instuctions for compiling my Gens source package against an x64 system. Now I don't have a 64-BIT installation, so I am assuming the compiling process is no different from x86 systems.

Anyhow, please test and see if you can produce a Gens 64-BIT package from these instructions. If you suceed, please post the package in this thread. Thank you!

Firstly, you must install the tools needed to compile source and built Debian packages:

```
sudo aptitude install build-essential fakeroot dh-make
```

Now you must install the build dependencies for the Gens compile

```
sudo aptitude install debhelper autotools-dev gcc-3.4 nasm libgtk2.0-dev libsdl1.2-dev
```

Download the gens_2.12a_src.zip package from [here]("http://www.zshare.net/download/gens_2-12a_src-zip.html") and extract it. Then extract the gens_2.12a.tar.gz archive. You should now have a new gens-2.12a folder. Enter the new folder:

```
cd ~/gens-2.12a
```

Then run:

```
fakeroot debian/rules clean
```

Then build the package with:

```
fakeroot debian/rules binary
```

Finally, run:

```
debuild -us -uc
```

That should be all you need. The new package will be waiting for you in the Gens folder. If not, it will be in your home folder.

---

### Post by Blairboy on 2007-04-28
The program works beautifully, but I can only play roms.  If I try to use a sega cd, the option to boot from cd is always greyed out.  I've tried using both of my cd drives, one of which I know worked under windows with gens.  Anybody got any ideas?

---

### Post by megamaced on 2007-04-28
> **Blairboy said:**
> The program works beautifully, but I can only play roms.  If I try to use a sega cd, the option to boot from cd is always greyed out.  I've tried using both of my cd drives, one of which I know worked under windows with gens.  Anybody got any ideas?

You need to download the Sega CD BIOS. Sorry, no links because that's illegal :)

Also, you might try making an ISO file. But only if you own the actual CD.

---

### Post by Blairboy on 2007-04-28
Wow, did you even read my post?  I can play sega cd games.  I have the proper files to do so.  Gens just doesn't give me the option to play it from a cd drive.  It makes me use a rom/iso.

---

### Post by megamaced on 2007-04-28
Okay, no reason to patronise! Allow me to have a few beers and get it wrong!

I see what you mean though. I hadn't even noticed it because all of my Sega CD games are on ISO. However, I am not a programmer so I don't know exactly what's wrong. I only package the program!

Anyhow, glad you enjoy the program :) Long live Sega!

---

### Post by Blairboy on 2007-04-29
So nobody but me is having this problem?  Everyone else can boot from a cd in gens?

---

### Post by megamaced on 2007-04-29
I can't use CDs either. Like you said, the option is grayed out.

---

### Post by Blairboy on 2007-04-29
I did a little digging and it turns out you need ASPI installed for it to recognize the cd drive.  The only cute little problem with that is I can't seem to find any information on how to install ASPI in linux.

---

### Post by mrazster on 2007-04-29
I don't know if it's me or something went wrong...but I can't find any roms installed anywhere.

It installed fine but no roms....do I have to download them somewhere....did I missunderstand something..?

---

### Post by disturbedite on 2007-04-29
yes, you misunderstood everything about emulation.  there is no such thing as an emulator that includes roms.

---

### Post by mrazster on 2007-04-29
> **disturbedite said:**
> yes, you misunderstood everything about emulation.  there is no such thing as an emulator that includes roms.

Ahh yeah...got it....figured it out now...thnx for the pointer. :)

Everything works prefectly fine...

---

### Post by adam0509 on 2007-05-05
Can't get my joystick/gamepad to WORK FFS §§§ The directions aren't reconized


I try all I can do, and I try about 3 or 4 different package...


I read this HOW-TO but it don't work :

> 
If you must edit gens.cfg by hand to configure your joystick :

Down  : 4096 + 256*which + 1
Up    : 4096 + 256*which + 2
Left  : 4096 + 256*which + 3
Right : 4096 + 256*which + 4

Buttons : 4112 + 256*which + x


where which = 0 for first joystick,
            = 1 for second joystick,
      x     = the number of the button
         
Here how a typical gens.cfg with joystick would look like (modify for your own needs)

P1.Up=4097
P1.Down=4099
P1.Left=4100
P1.Right=4098
P1.Start=4112


That's weird cause I got exactly these values under Windows, but it WORKS on Windows...

I use a Sidewinder game pad (NOT analog) correctly configured/calibrated...



Linux will still suxx about games, as far as a 3D virtual machine will be available on Linux...

---

### Post by DoktorSeven on 2007-05-05
> **Blairboy said:**
> The program works beautifully, but I can only play roms.  If I try to use a sega cd, the option to boot from cd is always greyed out.  I've tried using both of my cd drives, one of which I know worked under windows with gens.  Anybody got any ideas?

Booting from CD via the menu is apparently not supported.  However, since in Linux the CD device is represented as a file, can you point it to /dev/cdrom and get it to run? (Edit: CD audio probably won't work, though.)

---

### Post by megamaced on 2007-05-11
@ adam0509

Does your joypad work in other Linux games?

---

### Post by wryun on 2007-05-18
My (4!) USB joypads work just fine under gens configuring them through the menu system. But be careful if you have more than two installed - you'll need to fix the source up to support that.

---

### Post by wryun on 2007-05-18
Hmm... or alternatively, there are really lots of patches out there:
[http://mythtv.wbond.net/gens_for_linux_mythgame_edition/](http://mythtv.wbond.net/gens_for_linux_mythgame_edition/)
[http://sourceforge.net/tracker/?group_id=73619&atid=538344](http://sourceforge.net/tracker/?group_id=73619&atid=538344)

(and note that the version in CVS on the sourceforge site is slightly newer than the rc3.5 build that people here are using)

---

### Post by megamaced on 2007-05-21
[quote=wryun]Hmm... or alternatively, there are really lots of patches out there:
[http://mythtv.wbond.net/gens_for_linux_mythgame_edition/](http://mythtv.wbond.net/gens_for_linux_mythgame_edition/)
[http://sourceforge.net/tracker/?group_id=73619&atid=538344](http://sourceforge.net/tracker/?group_id=73619&atid=538344) [/quote]

Thanks for these links. I will apply those patches to my build soon and create a new debian package.

[quote=wryun](and note that the version in CVS on the sourceforge site is slightly newer than the rc3.5 build that people here are using)[/QUOTE]

I don't think it's part of the opengl branch though

---

### Post by megamaced on 2007-05-22
Gens-2.12b released. I added the Open ROM and GCC patches :)

@ wryun

I couldn't find the code for the joypads. I could only find the gens source code with the patch already applied. Where did you find the patch?

---

### Post by sl1pkn07 on 2007-05-27
sl1pkn07@SpinFlo:~/aplicaciones/gens_2.12b_src/gens-2.12b$ fakeroot debian/rules binary
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b'
/usr/bin/make  all-recursive
make[2]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b'
Making all in src
make[3]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src'
Making all in starscream
make[4]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream'
Making all in main68k
make[5]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/main68k'
/usr/bin/make  all-am
make[6]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/main68k'
make[6]: No se hace nada para `all-am'.
make[6]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/main68k'
make[5]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/main68k'
Making all in sub68k
make[5]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/sub68k'
/usr/bin/make  all-am
make[6]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/sub68k'
make[6]: No se hace nada para `all-am'.
make[6]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/sub68k'
make[5]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream/sub68k'
make[5]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream'
make[5]: No se hace nada para `all-am'.
make[5]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream'
make[4]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/starscream'
Making all in gens
make[4]: se ingresa al directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/bash ../../depcomp \
        x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/glade -I.   -DDATADIR=\"/usr/share/gens\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -Wall -g -O2 -Wl,-z,defs -Wall -g -O2 -Wl,-z,defs -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: error: el elemento inicializador no es constante
gens_core/cpu/68k/cpu_68k.c:27: error: (cerca de la inicialización de ‘M68K_Fetch[1].offset’)
gens_core/cpu/68k/cpu_68k.c:28: error: el elemento inicializador no es constante
gens_core/cpu/68k/cpu_68k.c:28: error: (cerca de la inicialización de ‘M68K_Fetch[2].offset’)
gens_core/cpu/68k/cpu_68k.c:29: error: el elemento inicializador no es constante
gens_core/cpu/68k/cpu_68k.c:29: error: (cerca de la inicialización de ‘M68K_Fetch[3].offset’)
gens_core/cpu/68k/cpu_68k.c:63: error: el elemento inicializador no es constante
gens_core/cpu/68k/cpu_68k.c:63: error: (cerca de la inicialización de ‘S68K_Fetch[0].offset’)
gens_core/cpu/68k/cpu_68k.c: En la función ‘M68K_Set_32X_Rom_Bank’:
gens_core/cpu/68k/cpu_68k.c:365: aviso: conversión de puntero a entero de tamaño diferente
gens_core/cpu/68k/cpu_68k.c: En la función ‘M68K_Set_Prg_Ram’:
gens_core/cpu/68k/cpu_68k.c:390: aviso: conversión de puntero a entero de tamaño diferente
make[4]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[4]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src/gens'
make[3]: *** [all-recursive] Error 1
make[3]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b/src'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b'
make[1]: *** [all] Error 2
make[1]: se sale del directorio `/home/sl1pkn07/aplicaciones/gens_2.12b_src/gens-2.12b'
make: *** [build-stamp] Error 2
sl1pkn07@SpinFlo:~/aplicaciones/gens_2.12b_src/gens-2.12b$

any ideas?

kubuntu 7.04feisty on amd64 bits

---

### Post by wryun on 2007-05-27
The patch is towards the end of the page - it's a bundle patch with the others you've already applied. However, I'd strongly suggest you make further builds off the CVS version: it is based on rc3.5 (the OpenGL version), and since I now have dev access (thanks Stéphane) I've been rolling some patches in. See: [http://gens.cvs.sourceforge.net/gens/Gens-MultiPlatform/linux/](http://gens.cvs.sourceforge.net/gens/Gens-MultiPlatform/linux/)

(the GensForLinux directory is the old one; this is the OpenGL one)

Hopefully I'll make a tar ball for release in a week or so, after a bit more testing and the rest of the sf.net patches are in, so you may want to hold off till then. Tell me if you want CVS access too.

EDIT: Hmm, there are also some patches in NetBSD ports. So many people fiddling, so little coordination :-)

---

### Post by Kumeelyun on 2007-05-29
Re-sizes work well, sound is good, Tried it out with Gunstar Heroes and it plays beautifully. Thanks for the package. Quite excellent!

---

### Post by megamaced on 2007-05-29
> **wryun said:**
> Hopefully I'll make a tar ball for release in a week or so, after a bit more testing and the rest of the sf.net patches are in, so you may want to hold off till then. 

Thats excellent! I have been hoping *someone* was still maintaining Gens! Please contact me as soon as you've built the tarball!

> **wryun]Tell me if you want CVS access too. [/quote]

Thanks  said:**
> So many people fiddling, so little coordination :-)

Couldn't agree more :D

---

### Post by VFiend on 2007-06-09
What's the status on this tarball, wryun?

---

### Post by megamaced on 2007-06-12
Added an RPM package for any SUSE or Fedora user that might be passing through. It's built using Alien, so I cannot predict the quality of the package. Seems OK on SUSE though.

Get it here:

[http://www.zshare.net/download/2249004789d17b/](http://www.zshare.net/download/2249004789d17b/)

---

### Post by VFiend on 2007-06-12
Seems to work perfectly on Fedora 7, thanks

---

### Post by wryun on 2007-06-13
> **VFiend said:**
> What's the status on this tarball, wryun?

I've finished with the most interesting patches - including embedding the graphics display in the window - but still have a few minor things to work through before I release a source tarball. It's all on CVS however - feel free to grab it and compile from there.

Note that if people are having performance problems with ATI cards, there's a patch on sourceforge to deal with that (not sure if this is relevant for the latest drivers, as I have an NVIDIA myself).

---

### Post by VFiend on 2007-06-13
> **wryun said:**
> I've finished with the most interesting patches - including embedding the graphics display in the window - but still have a few minor things to work through before I release a source tarball. It's all on CVS however - feel free to grab it and compile from there.

Ah, great, thanks for your work!

---

### Post by BigSilly on 2007-06-13
Installed this great and everything runs really lovely, except I can't get the joypad to work properly. It calibrates in the options perfectly, but when you go to play a game it doesn't work correctly. The buttons are OK, but the directions are broken.

Has anyone else had this problem and been able to fix it? Your help much appreciated.

---

### Post by megamaced on 2007-06-13
> **wryun said:**
> I've finished with the most interesting patches - including embedding the graphics display in the window - but still have a few minor things to work through before I release a source tarball. It's all on CVS however - feel free to grab it and compile from there.

That's great mate. Can't wait for your tarball. Please let us know when it's ready so I can package it ASAP!

So I guess you are the only current maintainer for Gens at the moment? Or are you going to create your own branch and fork it? Let me know what version number you want the new package to have! :)

EDIT: I might make pre-release packages from your CVS if people are interested. As I mentioned, just let me know how you want the packages to be numbered

---

### Post by wryun on 2007-06-13
> **megamaced said:**
> So I guess you are the only current maintainer for Gens at the moment? Or are you going to create your own branch and fork it? Let me know what version number you want the new package to have! :)

I wouldn't go as far as to call me a maintainer - I'm just trying to get the latest fixes into the main repository. No forking for me (gens has already been forked way too many times) ;)

I'll probably call the tarball 2.13alpha and hopefully get some feedback on how it's working, then release a Linux 2.13.

---

### Post by megamaced on 2007-06-13
Okay, so looking at the Gens CVS, I need to download and compile /Gens-MultiPlatform/linux/ right?

---

### Post by wryun on 2007-06-13
> **megamaced said:**
> Okay, so looking at the Gens CVS, I need to download and compile /Gens-MultiPlatform/linux/ right?

Yes, just that directory, and you'll need to mess around with aclocal, autoconf and automake then run ./configure and make. You may want to pass 'CFLAGS=-O3 -march=i686' or similar to configure.

EDIT: By the way, if people use this, they'll need to get rid of their old ~/.gens/gens.cfg file.

---

### Post by jemy_x on 2007-06-14
Hello there

I get this message when trying to install your latest package as instructed:

$ sudo dpkg -i gens_2.12b_i386.deb
dpkg: error processing gens_2.12b_i386.deb (--install): package architecture (i386) does not match system (amd64)
Errors were encountered while processing: gens_2.12b_i386.deb

Yes indeed, it's the 'ol "thought-I'd-be-smart-and-try-64bit" trap. Any ideas how I might fix/overcome this? Aside from running back to my 32bit happy-place...

Cheers!

---

### Post by leech on 2007-06-14
You have to use --force-architecture.  Like this ```
sudo dpkg -i --force-architecture gens_2.12b_i386.deb
```

As a side note, this is truly fantastic that gens is finally getting some love.

There are so many emulators for Linux out there that have just kind of floundered on the wayside.

It'd be cool if we could get a list of them (in a new thread obviously) and get some programmers to show them some love.  I know virtual jaguar is one that I'd like to see completed, but it's been in a sort of limbo for years.

I'll start that thread now.... :D

Leech

---

### Post by BigSilly on 2007-06-14
Can no-one help with the joypad configuration? As I say above, all seems OK when you configure it, but when you try to play it it doesn't work. Up and down on the analogue works for left and right for some reason, but the digital pad doesn't work at all.  I'm using a dual analogue Speedling 2 pad, so if anyone can help it'd most appreciated. I'd love to play some old Megadrive faves in Linux.

---

### Post by megamaced on 2007-06-14
> **wryun said:**
> Yes, just that directory, and you'll need to mess around with aclocal, autoconf and automake then run ./configure and make. You may want to pass 'CFLAGS=-O3 -march=i686' or similar to configure.

I ran:

```
cvs -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens login
```

And pressed enter for the password but nothing happened! What am I doing wrong?

---

### Post by eadmaster on 2007-06-14
> **BigSilly said:**
> Can no-one help with the joypad configuration? As I say above, all seems OK when you configure it, but when you try to play it it doesn't work. Up and down on the analogue works for left and right for some reason, but the digital pad doesn't work at all.  I'm using a dual analogue Speedling 2 pad, so if anyone can help it'd most appreciated. I'd love to play some old Megadrive faves in Linux.

I suggest you to try with some joypad 2 keyboard converter like QJoyPad.

---

### Post by eadmaster on 2007-06-14
> **wryun said:**
> I wouldn't go as far as to call me a maintainer - I'm just trying to get the latest fixes into the main repository. No forking for me (gens has already been forked way too many times) ;)

I'll probably call the tarball 2.13alpha and hopefully get some feedback on how it's working, then release a Linux 2.13.

Can you please apply the patch described [here]("http://brian.gentoo-clan.org/2006/08/30/gens-command-line-parameters/").

Currently it seems that command line options are not processed so Gens cannot be associated with any file type.

---

### Post by Jimbob17 on 2007-06-14
Yeah, it works fine for me also. Brings back memories of playing NHLPA 93 non stop ....

---

### Post by disturbedite on 2007-06-14
its really great that its being maintained in a somewhat orderly fashion by wyrun.

thanks all.

p.s.  i don't know how many of you are familiar with gens32 (on windows) but it'd be great to get some of the options gens32 has in gens (for linux).  in particular the sound options, rom explorer (for archived/compressed files), & the improved game genie ui...

---

### Post by wryun on 2007-06-15
> **megamaced said:**
> I ran:

```
cvs -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens login
```

And pressed enter for the password but nothing happened! What am I doing wrong?

You shouldn't see anything much happen after that. You need the next line then (look at the directions on the sf project site):

cvs -z3 -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens co Gens-MultiPlatform/linux

---

To the person who mentioned command line arguments: are you using the CVS version? If you are, it should work (although in a slightly different fashion to that described by the patch). See --help.

---

### Post by wryun on 2007-06-15
> **BigSilly said:**
> Can no-one help with the joypad configuration? As I say above, all seems OK when you configure it, but when you try to play it it doesn't work. Up and down on the analogue works for left and right for some reason, but the digital pad doesn't work at all.  I'm using a dual analogue Speedling 2 pad, so if anyone can help it'd most appreciated. I'd love to play some old Megadrive faves in Linux.

Hard to say. The joystick code's a bit of a mess; it's probably a simple fix, but without knowing what numbers your joystick is generating I wouldn't know what to change. Does it work ok in other apps?

---

### Post by BigSilly on 2007-06-16
Pretty much. I'm also using ZSNES 1.51 with no pad or control problems, and also Mupen64 works great with my joypad. I managed to configure Secret Maryo Chronicles to work with it as well, and FakeNES works as it should also. There's only GridWars I can't get to work at all, and this version of Gens with broken controls, which is a real bummer! It's a great emulator, though, and I'd love to see further updates to it. 

Thanks for your replies.

---

### Post by Tommerz on 2007-06-16
Hey, just want to say thanks for the package, it's running really well on my gibbon install.

One problem I'm having though, is save states won't load. :(

---

### Post by wryun on 2007-06-16
> **Tommerz said:**
> Hey, just want to say thanks for the package, it's running really well on my gibbon install.

One problem I'm having though, is save states won't load. :(

There's an issue with save states in the non-CVS version. It should work if you use the 'preset' quicksaves in the menu.

---

### Post by megamaced on 2007-06-19
> **wryun said:**
> You shouldn't see anything much happen after that. You need the next line then (look at the directions on the sf project site):

cvs -z3 -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens co Gens-MultiPlatform/linux


Thanks for that. I will play around with it when I get home and build a pre-alpha package - unless your tarball is almost done ;)

---

### Post by D-- on 2007-06-22
Hey, is anyone else having a speed issue? The games are running unplayable fast for me even though I have Perfect Syncro checked and Frameskip set to auto.

---

### Post by wingnux on 2007-06-22
Same problem here, even with vsync on all games run at 100+ fps =/

Btw, nice job with the emu, I was really missing a genesis emulator on ubuntu ::D

---

### Post by wryun on 2007-06-24
> **wingnux said:**
> Same problem here, even with vsync on all games run at 100+ fps =/

Have you got the sound enabled? It should run at the correct speed then...

---

### Post by adam0509 on 2007-06-25
There is an 2.14 version there :

[http://www.getdeb.net/app.php?name=Gens](http://www.getdeb.net/app.php?name=Gens)

Where does it come from ??

---

### Post by megamaced on 2007-06-25
> **adam0509 said:**
> There is an 2.14 version there :

[http://www.getdeb.net/app.php?name=Gens](http://www.getdeb.net/app.php?name=Gens)

Where does it come from ??

I don't know. I will install it later to find out. Wryun do you know about this package?

---

### Post by megamaced on 2007-06-25
I am now even more confused having installed the package! There is no opengl support, no logos in the 'start menu' or gens menus and the 'about' box still shows 2.12r3!

I wonder if this version might be an old CVS version and the package has been incorrectly named?

---

### Post by megamaced on 2007-06-25
Okay people, time to get excited! The first glimpse of Wryun's work is upon us!! I have made a package of the latest snapshot in CVS. Be aware that it may contain bugs and should be considered unstable until Wryun releases the final product. If you want to use the current stable instead, please download gens-2.12b in the first post

Please enjoy and report bugs!

deb (dapper, edgy, feisty, gutsy)
[http://www.zshare.net/download/242791807a267a/](http://www.zshare.net/download/242791807a267a/)

rpm (suse, fedora, mandriva)
[http://www.zshare.net/download/2428380177a720/](http://www.zshare.net/download/2428380177a720/)

Wryun, I love the embedded ROM window! I haven't used it much yet but will let you know more soon :D

---

### Post by BigSilly on 2007-06-25
My sincerest and most heartfelt thanks for this incredible update! All seems to be working really well. I downloaded and installed as soon as I saw your file (removed older Gens first) and have been playing around with it since. Joypad works beautifully after calibration, and when stretched to full screen with scale 2x I swear it adds an extra generation to the old Mega Drive!

Perhaps the only thing I've noticed is a really really tiny delay on the sound effects. It's barely perceptible, and I suspect it may be some setting I haven't checked yet (or just me!) rather than a problem with the program. Honestly you can hardly notice it. 

I've sent this off to a mate of mine who is a big Mega Drive fan and Linux user. He'll be thrilled as I am. Many many thanks again. 

/plays Streets of Rage :)

---

### Post by wingnux on 2007-06-25
This build crashed here while the 2.14 one worked fine and fixed the vsync problem :O

---

### Post by BigSilly on 2007-06-26
Ah, I knew it was a setting I hadn't looked at with regards the sound. I changed the rate from 22050 to 48000 and it's absolutely perfect. This is now my favourite MegaDrive emulator. One thing though, is it supposed to support 32X games, or is that something you'll be adding at a later date? None of mine seem to work.

---

### Post by megamaced on 2007-06-26
> **wingnux said:**
> This build crashed here while the 2.14 one worked fine and fixed the vsync problem :O

You could make yourself useful by telling us what you were doing when it crashed ;)

> **BigSilly said:**
> One thing though, is it supposed to support 32X games, or is that something you'll be adding at a later date? None of mine seem to work.

Yes it plays some 32x games but it's not as compatible. It can play rougly 50-60% of all 32x games produced (which wasn't many of course). Do you have the 32x bios files and paths configured in Gens?

---

### Post by BigSilly on 2007-06-26
Ah I see, no I don't think I even have them. My rom collection is just one I dragged over from my Kega Fusion on Windows. All my 32X roms work fine on that without bios files etc. I didn't even know you needed them. I'll certainly grab hold of some now. 

Sorry for any confusion.

---

### Post by MetalMusicAddict on 2007-06-26
Can someone host the Ubuntu package someplace that doesn't require acceptance of 100 cookies or pop-up ads?

If someone can get it to me I can also mirror.

Also is someone working to get this into Gutsy? I can help with this as well.

---

### Post by BigSilly on 2007-06-26
OK, got hold of the bios files needed to run 32X games, and configured the path in the settings. Unfortunately it doesn't seem to be working for me at all. I've tried to run a few games now with no luck. Tried Afterburner, Virtua Racing, Knuckles Chaotix, Darxide and Space Harrier and all that happens is that Gens shuts down. I'll keep trying though, in case I missed something. 

Still, the Megadrive stuff looks and plays wonderfully. Kega Fusion only manages a windowed screen even when I select stretch in the options, but not so here. It's a proper full screen beauty!

This really should be in the official repositories. If you intend to continue developing it, you should find the biggest audience possible. :)

EDIT: Got Brutal Unleashed 32X to work, but unfortunately the other games I have don't work at all.

---

### Post by megamaced on 2007-06-26
Knuckles Chaotix, Darxide and Space Harrier all work on my Gens so I am assuming you might have the wrong files. For reference:

Gens > Options > Bios / Misc files

BIOS name         [COLOR="#ff0000"]File name[/COLOR]
M68000               [COLOR="Red"]32X_G_BIOS.BIN[/COLOR]
Master SH2        [COLOR="#ff0000"]32X_M_BIOS.BIN[/COLOR]
Slave SH2           [COLOR="#ff0000"]32X_S_BIOS.BIN[/COLOR]

And for Sega CD BIOS files:

USA            [COLOR="#ff0000"]us_scd2_9306.bin[/COLOR]
Europe      [COLOR="#ff0000"]eu_mcd2_9306.bin[/COLOR]
Japan          [COLOR="#ff0000"]jp_mcd1_9112.bin[/COLOR]

---

### Post by BigSilly on 2007-06-26
Yeah, my bios files are set up exactly how you describe, but no joy with my roms apart from Brutal Unleashed. I'll certainly go on the hunt for other downloads of Darxide, Knuckles and the others, but they do all work fine in Kega Fusion on XP so it strikes me as odd that they don't work here. Could it be anything else?

---

### Post by megamaced on 2007-06-26
I can think of several things:

1. the BIOS are incorrect, fake
2. the ROMs are broken somehow
3. Try different regions of games, might be that an eu works over an us
4. the gens configuration is wrong somewhere.

As I said, all games you've mentioned work on the Gens CVS. BTW, I should probably mention that you need to own the games and the system to legally hold the BIOS. Don't want to get the tread locked :)

---

### Post by BigSilly on 2007-06-26
I'll try all the things you mention just to make sure. It's certainly worth it for me, since this is an excellent emu. :)

I'll post back when I've had a good tinker. I'm afraid it'll probably be tomorrow afternoon before I get the chance to play around again, but I'll certainly report any developments. Thanks for your patience.

---

### Post by wryun on 2007-06-26
> **megamaced said:**
> I don't know. I will install it later to find out. Wryun do you know about this package?

If he's built it from what he says (the 2.14 win32 bundle), it's an old version (that '2.14' didn't contain any linux updates). In other words, it is 2.12rc3 as the about box reports.

Sorry for not getting any more updates happening; I've been relatively busy lately (and will be for a couple of weeks). I'll let you know here if I find time to make any interesting changes.

And yes, whoever it crashed for, please say if you have any further details :)

---

### Post by BigSilly on 2007-06-27
OK, downloaded new bios files from another site I know. Tried a couple of different versions of Afterburner 32X but to no avail I'm afraid. It just shuts Gens down as soon as I try to play it. However, got hold of alternative version of Space Harrier 32X (JU! rather than E!) and that runs great. 

I'll keep tinkering with it and try to get more alternative downloads, so if I can help in any way I'll report back.

---

### Post by meschaffe on 2007-06-28
Thanks, I've been looking for a decent Genesis emulator for weeks now - even tried running Gens32 via Wine. For some odd reason, sound is screwy in windowed mode, but near perfect in fullscreen, no matter what my frequency is. Not much of a problem since I don't play in windowed mode, though. Aside from that, it's just as good to me as the windows version was before I converted. Many thanks to everyone involved.

---

### Post by Frem on 2007-06-28
I get a crash also. I used "sudo apt-get remove gens" to get rid of stable, then I used dpkg to install the new CVS version. A roughly 640x480 window appeared, with the menubar at the top. I tried to click on the menus, but they didn't open; the whole interface was frozen up. About five seconds later, it closed.
Tried running it again, and it closed almost instantly.

I get the same console output every time.

/home/james/.themes/Clearlooks-Boring/gtk-2.0/gtkrc:46: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/james/.themes/Clearlooks-Boring/gtk-2.0/gtkrc:47: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/james/.themes/Clearlooks-Boring/gtk-2.0/gtkrc:48: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Segmentation fault (core dumped)

I'm pretty sure the stuff about my Clearlooks theme is irrelavent because I switched to Crux & reran, and the only thing that showed up was "Segmentation fault (core dumped)"

---

### Post by wingnux on 2007-06-28
That's what happens to me: "Segmentation fault (core dumped)"

---

### Post by megamaced on 2007-06-29
To all the people that Gens CVS crashes on, can you confirm the following:

[LIST]
[*]That you have Direct Rendering, OpenGL support enabled
[*]The graphics card you are using
[*]The version of (K/X) ubuntu you are using
[/LIST]

OpenGL is enabled by default in Gens CVS so it will crash if you don't have DRI.

---

### Post by Frem on 2007-06-29
Wait, I thought DRI was bad because it allowed things to access the video card directly? That was why running StarCraft in wine in non-OpenGL mode was slower than on Windows, because they had to emulate it because DRI was a security hazzard? 
Or am I thinking of something else?

In any case, I've got the official ATi drivers installed, and glxinfo confirms that I do have direct rendering.

edit: actually, thinking about it, even the old stable version would go slow and crash when I tried to enable OpenGL mode. I know OpenGL works, but this card has an absolutely horrid implementation of it; it's very slow. Interesting...

glxinfo output:
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig, GLX_MESA_copy_sub_buffer
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8)
OpenGL extensions:
    GL_ARB_multitexture, GL_EXT_texture_env_add, GL_EXT_compiled_vertex_array, 
    GL_S3_s3tc, GL_ARB_depth_texture, GL_ARB_fragment_program, 
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader, 
    GL_ARB_multisample, GL_ARB_occlusion_query, GL_ARB_point_parameters, 
    GL_ARB_point_sprite, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_shadow, GL_ARB_shadow_ambient, GL_ARB_texture_border_clamp, 
    GL_ARB_texture_compression, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_crossbar, GL_ARB_texture_env_dot3, 
    GL_ARB_texture_float, GL_ARB_texture_mirrored_repeat, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, GL_ARB_vertex_blend, 
    GL_ARB_vertex_buffer_object, GL_ARB_pixel_buffer_object, 
    GL_ARB_vertex_program, GL_ARB_vertex_shader, GL_ARB_window_pos, 
    GL_ARB_draw_buffers, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_separate_stencil, 
    GL_ATI_texture_env_combine3, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_ATI_vertex_streams, 
    GL_ATIX_texture_env_combine3, GL_ATIX_texture_env_route, 
    GL_ATIX_vertex_shader_output_point_size, GL_EXT_abgr, GL_EXT_bgra, 
    GL_EXT_blend_color, GL_EXT_blend_func_separate, GL_EXT_blend_minmax, 
    GL_EXT_blend_subtract, GL_EXT_clip_volume_hint, 
    GL_EXT_draw_range_elements, GL_EXT_fog_coord, GL_EXT_framebuffer_object, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_pixels, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, GL_EXT_stencil_wrap, 
    GL_EXT_texgen_reflection, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_rectangle, GL_EXT_vertex_array, 
    GL_EXT_vertex_shader, GL_HP_occlusion_test, GL_NV_blend_square, 
    GL_NV_occlusion_query, GL_NV_texgen_reflection, GL_SGI_color_matrix, 
    GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp, 
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x28 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x29 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x30 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x31 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x34 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x35 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x36 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x37 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x39 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x3b 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3c 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x3d 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3e 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x3f 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x41 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x43 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x44 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x45 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x46 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x47 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x48 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x49 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x51 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x52 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x59 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5a 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5c 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8 16 16 16 16  0 0 None
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5e 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0 16 16 16 16  0 0 None
0x5f 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x60 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x61 24 dc  0 32  0 r  y  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
0x62 24 dc  0 32  0 r  .  .  8  8  8  8  0 24  0  0  0  0  0  0 0 None
```

---

### Post by megamaced on 2007-06-29
The crashes may be due to the ATi cards but I can't confirm this. I am using an nVidia Geforce FX 5200 on Kubuntu 6.06 and Gens CVS runs perfectly.

The Gens CVS package was built in an Dapper environment and this might be causing problems for Feisty Fawn users. I have now re-packaged Gens in an Feisty environment and maybe this will solve the problems.

Gens CVS for Dapper Drake
[http://www.zshare.net/download/248242463f1bee/](http://www.zshare.net/download/248242463f1bee/)

Gens CVS for Feisty Fawn
[http://www.zshare.net/download/2482436eb33dc0/](http://www.zshare.net/download/2482436eb33dc0/)

---

### Post by leech on 2007-06-29
It isn't very fond of Compiz, that's for sure.  After I disabled the desktop effects in Gutsy, both packages would work fine.  Before I disabled it, I would get similar results on my 6800GT that were reported by Frem, though mine wouldn't segfault, I would have to kill it.  It wouldn't even die on it's own or pop up the Force Quit / Wait dialog, instead I had to close the terminal that I had started it from.

But it seems to be working fine without Compiz.

Leech

---

### Post by Nythain on 2007-06-29
yay, a working gen emulator that does everythign i want it to for linux... time to bust out those classics... Dark Force, its time to meet your maker

---

### Post by disturbedite on 2007-06-29
well, i get a different crash than the other ones reported here.  but its kinda ok, since it doesn't affect anything (that i'm aware of).  its that gens triggers a core dump when exiting.  the config is saved tho, so its fine i guess. 
i'm on kubuntu gutsy i386 with an integrated intel i845g with dri enabled.  i am using the gens_2.13-cvs200706257.04_i386.deb package with opengl enabled. here is the info:

```
*** glibc detected *** gens: free(): invalid pointer: 0xb0a24020 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75b5f7d]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75b95c0]
/usr/lib/dri/i915_dri.so(_tnl_free_vertices+0x27)[0xb49107b7]
/usr/lib/dri/i915_dri.so(intelDestroyContext+0x2e)[0xb48615ae]
/usr/lib/dri/i915_dri.so[0xb48486f5]
/usr/lib/libGL.so.1[0xb7f0e3d5]
/usr/lib/libSDL-1.2.so.0[0xb7e5c086]
/usr/lib/libSDL-1.2.so.0[0xb7e60907]
/usr/lib/libSDL-1.2.so.0[0xb7e60b15]
/usr/lib/libSDL-1.2.so.0(SDL_VideoQuit+0x50)[0xb7e4dc90]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x65)[0xb7e22025]
gens[0x806b6e0]
gens[0x807d418]
gens[0x807e749]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7563ebc]
gens[0x804d3e1]
======= Memory map: ========
08048000-081f7000 r-xp 00000000 08:01 8208736    /usr/bin/gens
081f7000-08225000 rwxp 001ae000 08:01 8208736    /usr/bin/gens
08225000-099c9000 rwxp 08225000 00:00 0          [heap]
afea9000-aff09000 rwxs 00000000 00:09 414810117  /SYSV00000000 (deleted)
aff09000-aff7c000 r-xp 00000000 08:01 8438033    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-BoldOblique.ttf
aff7c000-afffb000 r-xp 00000000 08:01 8438036    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
afffb000-b09fb000 rwxp afffb000 00:00 0
b0a24000-b0cee000 rwxp b0a24000 00:00 0
b0cee000-b2cee000 rwxs f3800000 00:0e 26204      /dev/dri/card0
b2cee000-b33ae000 rwxs f3000000 00:0e 26204      /dev/dri/card0
b33ae000-b3a6e000 rwxs f2800000 00:0e 26204      /dev/dri/card0
b3a6e000-b412e000 rwxs 2e01c000 00:0e 26204      /dev/dri/card0
b412e000-b47ee000 rwxs f00e0000 00:0e 26204      /dev/dri/card0
b47ee000-b4a1d000 r-xp 00000000 08:01 8225244    /usr/lib/dri/i915_dri.so
b4a1d000-b4a2c000 rwxp 0022e000 08:01 8225244    /usr/lib/dri/i915_dri.so
b4a2c000-b4a37000 rwxp b4a2c000 00:00 0
b4a37000-b4a38000 ---p b4a37000 00:00 0
b4a38000-b5238000 rwxp b4a38000 00:00 0
b5238000-b5298000 rwxs 00000000 00:09 414515204  /SYSV00000000 (deleted)
b5298000-b5317000 r-xp 00000000 08:01 8438036    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5317000-b5341000 r-xp 00000000 08:01 8210149    /usr/lib/libkdefx.so.4.2.0
b5341000-b5342000 rwxp 0002a000 08:01 8210149    /usr/lib/libkdefx.so.4.2.0
b5342000-b5371000 r-xp 00000000 08:01 8210103    /usr/lib/libidn.so.11.5.19
b5371000-b5372000 rwxp 0002f000 08:01 8210103    /usr/lib/libidn.so.11.5.19
b5372000-b5387000 r-xp 00000000 08:01 8210796    /usr/lib/libart_lgpl_2.so.2.3.19
b5387000-b5388000 rwxp 00014000 08:01 8210796    /usr/lib/libart_lgpl_2.so.2.3.19
b5388000-b538a000 r-xp 00000000 08:01 9144579    /lib/tls/i686/cmov/libutil-2.5.so
b538a000-b538c000 rwxp 00001000 08:01 9144579    /lib/tls/i686/cmov/libutil-2.5.so
b538c000-b539b000 r-xp 00000000 08:01 9144575    /lib/tls/i686/cmov/libresolv-2.5.so
b539b000-b539d000 rwxp 0000f000 08:01 9144575    /lib/tls/i686/cmov/libresolv-2.5.so
b539d000-b539f000 rwxp b539d000 00:00 0
b539f000-b53d0000 r-xp 00000000 08:01 8210124    /usr/lib/libDCOP.so.4.2.0
b53d0000-b53d1000 rwxp 00031000 08:01 8210124    /usr/lib/libDCOP.so.4.2.0
b53d1000-b53d3000 rwxp b53d1000 00:00 0
b53d3000-b5609000 r-xp 00000000 08:01 8210147    /usr/lib/libkdecore.so.4.2.0
b5609000-b5619000 rwxp 00236000 08:01 8210147    /usr/lib/libkdecore.so.4.2.0
b5619000-b561c000 rwxp b5619000 00:00 0
b561c000-b561f000 r-xp 00000000 08:01 9109535    /lib/libattr.so.1.1.0
b561f000-b5620000 rwxp 00002000 08:01 9109535    /lib/libattr.so.1.1.0
b5620000-b5626000 r-xp 00000000 08:01 9109531    /lib/libacl.so.1.1.0
b5626000-b5627000 rwxp 00005000 08:01 9109531    /lib/libacl.so.1.1.0
b5634000-b5636000 r-xp 00000000 08:01 8323275    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5636000-b5637000 rwxp 00001000 08:01 8323275    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5637000-b563b000 r-xp 00000000 08:01 8257705    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b563b000-b563c000 rwxp 00003000 08:01 8257705    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b563c000-b563f000 r-xp 0000Aborted (core dumped)
```also, gens freezes when i try to set the bit depth to 32bit.  the only output from konsole is this:
*** glibc detected *** gens: free(): invalid pointer: 0xb0a4f020 ***.

other than that, it works fine.  thanks for all the hard work keeping this great emulator alive!

if you guys have the source debianized, would you be willing to post it so i could make a gutsy package?

---

### Post by megamaced on 2007-06-29
> **disturbedite said:**
> if you guys have the source debianized, would you be willing to post it so i could make a gutsy package?

Sure:
[http://www.zshare.net/download/248946971f0557/](http://www.zshare.net/download/248946971f0557/)

I have been reluctant to build a Gutsy package because it's still a moving circus and not stable yet. Let us know if your Gutsy build works any better for you :)

---

### Post by disturbedite on 2007-06-30
it (the gutsy package [i386]) doesn't really run any differently, except it doesn't do the core dump any more on exit....

---

### Post by wingnux on 2007-06-30
No luck with this new build either =/ I have DRI enabled and I'm using ATI's official drivers (Radeon 9600 Pro) on Ubuntu Feisty. All OGL games run with no problem at all (even zsnes with ogl support).

---

### Post by K-Starz on 2007-06-30
Awesome, I'm thrilled  find these packages!

I used to use Gens+ in Wine, but that stopped working, I couldn't get the Linux ones working. 

Thanks!

---

### Post by disturbedite on 2007-06-30
btw, i've got a question.

gens 2.14 was released for windows right?  the source for this says its "gens 2.13cvs"...i assume this (2.13) cvs version *IS* actually newer than the 2.14 release right?

also, why wasn't the 2.14 source used as the basis for this linux port?  was it cuz the 2.14 release was only for windows/windows related?

---

### Post by Devezu on 2007-07-03
NOOB ALERT!

Gens works perfectly for me, but i cant select a cd drive or anything (basically run any sega cd games!) help me... Sonic CD is calling for me...

---

### Post by disturbedite on 2007-07-03
noob alert for sure.

if you looked around the options a bit or read the gens website, you'd know why...
you need bios files for 32x & cd.  i can't tell you how to get them tho cuz you're supposed own them yourself.

---

### Post by bluemech on 2007-07-05
Alright, now anybody have any luck getting this compiled/installed on a 64-bit system? I tried **megamaced's** instructions [here](http://ubuntuforums.org/showpost.php?p=2547879&postcount=64) on three separate source packages already: 2.12a, 2.12b, and the presently-unstable CVS. No luck.

This is what I get (note that this is from trying to compile 2.12b, but I get similar errors with the other two):

```
mix@desktop:~/Desktop/gens-2.12b$ fakeroot debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp 
# Add here commands to clean up after the build process.
/usr/bin/make distclean
make[1]: Entering directory `/home/mix/Desktop/gens-2.12b'
make[1]: *** No rule to make target `distclean'.  Stop.
make[1]: Leaving directory `/home/mix/Desktop/gens-2.12b'
make: [clean] Error 2 (ignored)
cp -f /usr/share/misc/config.sub config.sub
cp -f /usr/share/misc/config.guess config.guess
dh_clean 
mix@desktop:~/Desktop/gens-2.12b$ fakeroot debian/rules binary
dh_testdir
# Add here commands to configure the package.
CFLAGS="-Wall -g -O2 -Wl,-z,defs" ./configure --host=x86_64-linux-gnu --build=x86_64-linux-gnu --prefix=/usr --mandir=\${prefix}/share/man --infodir=\${prefix}/share/info
checking build system type... x86_64-pc-linux-gnu
checking host system type... x86_64-pc-linux-gnu
checking target system type... x86_64-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for x86_64-linux-gnu-gcc... x86_64-linux-gnu-gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether x86_64-linux-gnu-gcc accepts -g... yes
checking for x86_64-linux-gnu-gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of x86_64-linux-gnu-gcc... gcc3
checking whether x86_64-linux-gnu-gcc and cc understand -c and -o together... yes
checking for strerror in -lcposix... no
checking how to run the C preprocessor... x86_64-linux-gnu-gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for pkg-config... /usr/bin/pkg-config
checking for GTK+ - version >= 2.4.0... yes (version 2.10.11)
checking for sdl-config... /usr/bin/sdl-config
checking for SDL - version >= 1.1.3... yes
checking for nasm... /usr/bin/nasm
checking for OpenGL support... yes
checking for clock_gettime in -lrt... yes
checking for getopt in -lc... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating pixmaps/Makefile
config.status: creating src/Makefile
config.status: creating src/gens/Makefile
config.status: creating src/starscream/Makefile
config.status: creating src/starscream/main68k/Makefile
config.status: creating src/starscream/sub68k/Makefile
config.status: creating config.h
config.status: executing default-1 commands
dh_testdir
# Add here commands to compile the package.
/usr/bin/make
make[1]: Entering directory `/home/mix/Desktop/gens-2.12b'
cd . \
          && CONFIG_FILES= CONFIG_HEADERS=config.h \
             /bin/bash ./config.status
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing default-1 commands
/usr/bin/make  all-recursive
make[2]: Entering directory `/home/mix/Desktop/gens-2.12b'
Making all in src
make[3]: Entering directory `/home/mix/Desktop/gens-2.12b/src'
Making all in starscream
make[4]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream'
Making all in main68k
make[5]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream/main68k'
source='star.c' object='star.o' libtool=no \
        depfile='.deps/star.Po' tmpdepfile='.deps/star.TPo' \
        depmode=gcc3 /bin/bash ../../../depcomp \
        x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -I. -I../../..     -Wall -g -O2 -Wl,-z,defs -c `test -f star.c || echo './'`star.c
star.c:497: warning: &#8216;force_trickybit_process&#8217; defined but not used
x86_64-linux-gnu-gcc: -z: linker input file unused because linking not done
x86_64-linux-gnu-gcc: defs: linker input file unused because linking not done
x86_64-linux-gnu-gcc  -Wall -g -O2 -Wl,-z,defs  -lGL -o star  star.o  -lc -lrt 
./star main68k.asm -hog -name main68k_
STARSCREAM version M0.26d
Generating "main68k.asm" with the following options:
 *  CPU type: 68000 (24-bit addresses)
 *  Identifiers begin with "main68k_"
 *  Stack calling conventions
 *  Hog mode: On
Decoding instructions: 0123456789ABCDEF done
Building table: done
routine_counter = 7244
/usr/bin/make  all-am
make[6]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream/main68k'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream/main68k'
make[5]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream/main68k'
Making all in sub68k
make[5]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream/sub68k'
source='star.c' object='star.o' libtool=no \
        depfile='.deps/star.Po' tmpdepfile='.deps/star.TPo' \
        depmode=gcc3 /bin/bash ../../../depcomp \
        x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -I. -I../../..     -Wall -g -O2 -Wl,-z,defs -c `test -f star.c || echo './'`star.c
x86_64-linux-gnu-gcc: -z: linker input file unused because linking not done
x86_64-linux-gnu-gcc: defs: linker input file unused because linking not done
x86_64-linux-gnu-gcc  -Wall -g -O2 -Wl,-z,defs  -lGL -o star  star.o  -lc -lrt 
./star sub68k.asm -hog -name sub68k_
STARSCREAM version S0.26d
Generating "sub68k.asm" with the following options:
 *  CPU type: 68000 (24-bit addresses)
 *  Identifiers begin with "sub68k_"
 *  Stack calling conventions
 *  Hog mode: On
Decoding instructions: 0123456789ABCDEF done
Building table: done
routine_counter = 7244
/usr/bin/make  all-am
make[6]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream/sub68k'
make[6]: Nothing to be done for `all-am'.
make[6]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream/sub68k'
make[5]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream/sub68k'
make[5]: Entering directory `/home/mix/Desktop/gens-2.12b/src/starscream'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream'
make[4]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/starscream'
Making all in gens
make[4]: Entering directory `/home/mix/Desktop/gens-2.12b/src/gens'
source='gens_core/cpu/68k/cpu_68k.c' object='gens_core/cpu/68k/gens-cpu_68k.o' libtool=no \
        depfile='.deps/gens_core/cpu/68k/gens-cpu_68k.Po' tmpdepfile='.deps/gens_core/cpu/68k/gens-cpu_68k.TPo' \
        depmode=gcc3 /bin/bash ../../depcomp \
        x86_64-linux-gnu-gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I./gens_core/cpu/68k -I./gens_core/cpu/sh2 -I./gens_core/cpu/z80 -I./gens_core/sound -I./gens_core/mem -I./gens_core/misc -I./gens_core/gfx -I./gens_core/io -I./gens_core/vdp -I./segacd -I./mp3_dec -I./sdllayer -I./util -I./port -I./emulator -I./debug -I./netplay -I./gtkui -I./gtkui/glade -I.   -DDATADIR=\"/usr/share/gens\" -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -DPNG_NO_MMX_CODE -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -Wall -g -O2 -Wl,-z,defs -Wall -g -O2 -Wl,-z,defs -c -o gens_core/cpu/68k/gens-cpu_68k.o `test -f gens_core/cpu/68k/cpu_68k.c || echo './'`gens_core/cpu/68k/cpu_68k.c
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for &#8216;M68K_Fetch[1].offset&#8217;)
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for &#8216;M68K_Fetch[2].offset&#8217;)
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for &#8216;M68K_Fetch[3].offset&#8217;)
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for &#8216;S68K_Fetch[0].offset&#8217;)
gens_core/cpu/68k/cpu_68k.c: In function &#8216;M68K_Set_32X_Rom_Bank&#8217;:
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function &#8216;M68K_Set_Prg_Ram&#8217;:
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[4]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[4]: Leaving directory `/home/mix/Desktop/gens-2.12b/src/gens'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mix/Desktop/gens-2.12b/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mix/Desktop/gens-2.12b'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/mix/Desktop/gens-2.12b'
make: *** [build-stamp] Error 2
```

I'm running Feisty, on 64-bit like I said.

---

### Post by Devezu on 2007-07-05
i DID provide the bioses (DUH! (plus, its ok - i have a sega cd)) but i still cant select the  option to boot a cd, disturbedite  disturbedite is offline
Way Too Much Ubuntu

---

### Post by disturbedite on 2007-07-06
@bluemech
i would try just downloading one of the 32bit packages & force the architechure while installing and see if that works.

@Devezu
do you have the disc in the drive?  or are you trying to play an image?

---

### Post by Bablefish on 2007-07-06
It works for me at least as far as the Genesis roms, it does not work on the 32X roms.

If anyone wants to know of an excellent vurus free rom site that has these 16 bit and earlier titles PM me and I'll send you the link

---

### Post by disturbedite on 2007-07-06
even that might earn a ban, i'd be careful babelfish.

---

### Post by EvilMarshmallow on 2007-07-06
Hey all,

I've got a weird issue... not sure if it's Gens-related or because of my game pad.

I use a Playstation2-style controller that plugs in via USB.  When I calibrate everything's ok... then I go to map the buttons in Gens and it won't allow me to select the d-pad or the analog sticks for my directions!

All the other buttons on the device work fine... but the dpad and analogs (which show up as axes, maybe that's why?) won't allow themselves to be mapped to the UDLR controls in Gens.

---

### Post by bluemech on 2007-07-07
> **disturbedite said:**
> @bluemech
i would try just downloading one of the 32bit packages & force the architechure while installing and see if that works.
That's what I did next actually. Got the 2.12b deb and forced it. It runs, but not very well. For one, it generates theme errors, making the interface messy. Not a big deal, but then again there's the controller issues of 2.12b, not to mention that sometimes it just decides to break down and seg fault on me. Not really nice when you're knee deep in Shinobi bosses. :P

So again, I'll repeat my question: anyone out there who has managed to compile a 64-bit version from the source package? Mind sharing?

---

### Post by disturbedite on 2007-07-07
@bluemech
why the heck would you use an older version?  i meant the newest packages.

---

### Post by verb3k on 2007-07-07
Thanks man , works perfectly :)
great packaging 
Thanks ;)

---

### Post by Devezu on 2007-07-07
No desturbedite, i put a cd in the drive (a copy), but no option.... (then again, i have two drives and only tried one..)

---

### Post by disturbedite on 2007-07-07
its possible that it won't recognize more than one drive.  or maybe looks for a specific device name (i.e. cdrom or cdrom0).
the first thing i would have tried (before posting) would have been to stick the disc in the other drive...

---

### Post by Epilonsama on 2007-07-07
Hi I tested it and it work at some extent but whne I activate OpenGL, cuz SDL runs slow on anything expect normal size, the screen went blank and it soon crashed, any help on this?

---

### Post by bluemech on 2007-07-08
> **disturbedite said:**
> @bluemech
why the heck would you use an older version?  i meant the newest packages.
I already did that before I looked for help here. CVS version seg faults immediately. It just doesn't work. At least with 2.12b I got as far as actually playing the game even though I got a ton of GTK errors:

```
Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap"
```

And yeah, I've already installed gtk2-engines-pixbuf, and even gtk-engines-pixmap. No go (well actually, it's a go, but like I said in my previous post, there are some problems with it.)

---

### Post by acoustibop on 2007-07-08
> **Devezu said:**
> No desturbedite, i put a cd in the drive (a copy), but no option.... (then again, i have two drives and only tried one..)

FWIW Devezu, I've had success with other emulators starting games from CDs with /dev/hda, /dev/hdb, /dev/hdc or /dev/hdd, depending on which IDE channel the drive is - hda = channel 1 master, hdb = channel 1 slave, hdc = channel 2 master, hdd = channel 2 slave.

The advantage of this is that you know what drive you're pointing at.  Not only do you not know which drive cdrom, cdrom0 or cdrom1 is without checking, I've known it to change sometimes.  Apparently those labels only point to hda, -b, -c or -d anyway.

---

### Post by Carbon Tiger on 2007-07-10
> **Devezu said:**
> No desturbedite, i put a cd in the drive (a copy), but no option.... (then again, i have two drives and only tried one..)

I fixed this on my end the first time by going to files on Gens and having it open:

/dev/disk/by-id/ NAME OF CD DRIVE (name as in the company who made it)

Also make sure Gens is set to all files in the file choice drop down menu so it will list what you need to open.

Or as acoustibop noted you can use: /dev/_____ In my case it was /dev/cdrom but your set up may be different. As for the grayed out CD button on the emulator itself I have no idea how to fix that. Also you can run isos which is a lot faster in many cases but a bit of a hassle. 

The same Cd path fix has also worked in Hu-Go (PC Engine/TG 16) emulator to run its CD games.

---

### Post by F-3582 on 2007-07-31
I'm not sure if this has been said, already... Didn't want to go through the entire thread and the CVS version crashes constantly. Anyway, the GUI sinda keeps forgetting some of the options I set. This involves the sound stuff (improved engines) and the SegaCD Perfect Synchro option in Gens up to 2.12b:

Sometimes some of those options appear turned on although they are off, sometimes it's the other way round. The only way to make sure is watching the GUI messages.

Anyway, the packages work splendidly.

EDIT: Well, looks like there are still issues. Silpheed locks up sometimes even though Perfect Synchro is activated. This didn't happen with 2.12rc3.

---

### Post by Vince4Amy on 2007-08-02
On the CVS Version I get:

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)
```

On the normal one everything is fine.

---

### Post by BigSilly on 2007-08-02
> **F-3582 said:**
> I'm not sure if this has been said, already... Didn't want to go through the entire thread and the CVS version crashes constantly. Anyway, the GUI sinda keeps forgetting some of the options I set. This involves the sound stuff (improved engines) and the SegaCD Perfect Synchro option in Gens up to 2.12b:

Sometimes some of those options appear turned on although they are off, sometimes it's the other way round. The only way to make sure is watching the GUI messages.

Anyway, the packages work splendidly.

EDIT: Well, looks like there are still issues. Silpheed locks up sometimes even though Perfect Synchro is activated. This didn't happen with 2.12rc3.

I'm finding it forgets settings too. Usually I set it to full screen and perfect synch etc, and as soon as I select another game it seems to revert back to defaults, though the tick boxes remain checked.

Other than that, I'm finding it excellent as a Megadrive emulator, and I'm thrilled that someone is maintaining it and showing the Linux emu scene some love!

---

### Post by F-3582 on 2007-08-02
> **BigSilly said:**
> I'm finding it forgets settings too. Usually I set it to full screen and perfect synch etc, and as soon as I select another game it seems to revert back to defaults, though the tick boxes remain checked.

Other than that, I'm finding it excellent as a Megadrive emulator, and I'm thrilled that someone is maintaining it and showing the Linux emu scene some love!
Exactly. I don't know which one to trust - the GUI or the emu OSD messages telling me that I just activated Perfect Synchro although I just unchecked that box ;) Which one is right? Apparently the GUI doesn't check back the gens.cfg which is used by the emulator.

---

### Post by Dirkomatic on 2007-08-06
I appreciate the work in getting this package together!

I've encountered a small snag, though...

I use wah!cade as my front end.  When I use gens with wah!cade, Alt+F4 registers as two different keystrokes and I can't exit.

Is there a way to configure gens to exit with another key-stroke?  Any other ideas?

---

### Post by Dirkomatic on 2007-08-07
In case anyone else is interested, I found some "undocumented" command line options, one of which makes gens behave like I'm used to with other emulators.  Here's a link: [http://brian.gentoo-clan.org/2006/08/30/gens-command-line-parameters/]("http://brian.gentoo-clan.org/2006/08/30/gens-command-line-parameters/")

Basically, use the --quickexit option to make the Esc key exit gens.

---

### Post by EnemyUnknown on 2007-09-08
it works nice on my amd64 
nice work dude

---

### Post by i23098 on 2007-09-17
Any amd64 packages readly available for download?

---

### Post by BigSilly on 2007-09-17
Still using this and it's a great Megadrive emu. My thanks to all involved!

There's only a couple of nitpicky problems with this Gens now (such as the aforementioned GUI probs). Is this emu still being worked on, or is Gens for Linux now considered a finished product?

Cheers.

---

### Post by DancemasterGlenn on 2007-09-19
Hi everyone, this is my first post on these forums. I wanted to say that I was thrilled to find that Gens is starting to be worked on again! I've been keeping an eye on this thread for a few months now, and it has been great seeing all the work that has been done. I'm chiming in now, first of all, to say I'm loving the program, and I hope the inactivity of the board does not signify that the work on this project has once again subsided. You've taken a great emulator and made it even better!

That said, I would also point out that I have also experienced some minor problems with configuration not necessarily reflecting what I've checked in the GUI (like some other people, it seems). Another personal woe I was hoping could be taken care of... I recently purchased a widescreen monitor, which is great for movies and new games, but when it comes to emulation I much prefer that the normal aspect ratio be kept (or at least, to simply stretch the video to my vertical max, rather than this large horizontal max). Any chance a "maintain aspect ratio" option could be included in the GUI? It would be much appreciated.

Sorry about the long post, and I'm really looking forward to this project getting even better. Thanks!

---

### Post by Faris on 2007-09-19
i know this will  sound silly but
how to make it run in the fullscreen mode and then get back to the normal window size
alt+enter is not working 
i have to restart my pc
(because i don't know how to end any application that runs in a fullscreen mode ) ===>:confused:

---

### Post by acoustibop on 2007-09-20
Most likely reason is there's a problem with your videocard driver, Faris.

Try pressing Control+c - this should stop emulation - before toggling back to windowed view.

---

### Post by dahlek on 2007-09-21
Gens seems great, but I'm wondering why Generator isn't in the repos? Dgen is included but it's really not a good emu - even the guy who made it agrees :)

Here is the page for the updated generator: 

[http://www.ghostwhitecrab.com/generator/](http://www.ghostwhitecrab.com/generator/)

It doesn't support SegaCD or 32X, but it is a very good Genesis emu and is still maintained and updated (unlike Dgen). It's fast too, even on *ancient* hardware, and has more modern features such as XV support (hardware 2D acel), the ability to play compressed ROMs,  a GUI (simple, but functional), and so on.

Perhaps the Ubuntu team can *remove* and put Dgen to rest and *add* Generator? Most Genesis games, probably by a factor of 100 to one, are Genesis games, not 32X or SegaCD games in any case. It would be handy for noobs if they could fire up Adept or Synaptic, install Generator, and start playing their games.

Surely something with such bland/common dependencies, gtk and sdl, could easily and quickly be added to the official repos? Compiling it is probably out of reach of most noobs and even annoys me a little :)

---

### Post by disturbedite on 2007-09-22
i didn't know much of anything about generator other than it exists.  but it looks pretty good/promising.  too bad it doesn't support 7-zipped roms yet tho....

---

### Post by megamaced on 2007-09-22
> **dahlek said:**
> Gens seems great, but I'm wondering why Generator isn't in the repos? 

Generator isn't too bad and I have made a Ubuntu package of it here:

[http://ubuntuforums.org/showthread.php?t=451647](http://ubuntuforums.org/showthread.php?t=451647)

However I do prefer Gens because of the added functionality and GTK+2 support

---

### Post by disturbedite on 2007-09-22
> **megamaced said:**
> However I do prefer Gens because of the added functionality and GTK+2 support
heh, and i'm on kubuntu/kde...

---

### Post by dahlek on 2007-09-23
Thanks for the package, megamaced. That will save some time for my next install or PC. Any chance that Ubuntu can put one of these nice working emus into the official repos?

Seems Ubuntu ought to have at least one good emu for each major console. Dgen really doesn't cut it.

---

### Post by SaLv1a on 2007-09-24
I've been using Gens on Windows for a long time and I'm glad its on Ubuntu now since I just made the switch. 

This version runs great without slowing down or anything but I can't seem to find where to change the resolution.

On Windows I would max it out so that it would be nice and sharp. Over here it looks horrible. Is there a command for this?

---

### Post by disturbedite on 2007-09-25
> **SaLv1a said:**
> This version runs great without slowing down or anything but I can't seem to find where to change the resolution.
its right there under Graphic --> OpenGL Resolution.

oh and turn on stretch in the graphic menu too.

---

### Post by SaLv1a on 2007-09-26
Mine doesn't have OpenGL Resolution. 

The only options I have in Graphic are...'

Fullscreen
Vsync
Stretch
Color Adjust
Render (no rez option)
Sprite Limit
Frame Skip
Screenshot


I'm running 2.12 rc3

---

### Post by disturbedite on 2007-09-26
then i don't think you're using the latest build.  i wouldn't rely so much on the version number given in the about dialog, it seems to go backward and forward with different builds.  ;)  i'm sure mine is the latest & it says 2.13 alpha, but as i said, i take that with a grain of salt...

---

### Post by BigSilly on 2007-09-27
Yep, that's not the one we're using. I've attached the best version of Gens, but it's available at the beginning of this thread.

---

### Post by disturbedite on 2007-09-27
this is the one i'm using, its updated for feisty even tho i'm on gutsy:

---

### Post by Extreme Coder on 2007-10-02
Even though I moved to Mandriva, I still lurk here sometimes :P

Anyway, I tried the Mandriva package you have on the first page, and it's working great. Thanks a lot!

---

### Post by cfehunter on 2007-10-08
I have to say that it works great.

Only bug i can find is that if i hit alt + enter and go to full screen, the program freezes and dosnt do anything until i go back to a window. Other than that thanks for making it and getting rid of one of my reasons to keep windows installed :)

---

### Post by BigSilly on 2007-10-08
I agree, it's an excellent emulator, and certainly the best Megadrive Emu on Linux imo. Can't wait for a new release!

---

### Post by elpresidente on 2007-10-08
Thanks for packaging this. Everything looks good so far. I have just one little problem. I use a Logitech usb gamepad and the only button that works in-game is the start button. Gens allows me to configure the joypad (It detects UP, DOWN, etc) but when I get in game, only the Start button works. Very strange. The gamepad works fine in FCEU. Now I have tried to use Joy2key to work around this problem but Joy2key complains that a joypad is not connected. Very strange. Any suggestions?

---

### Post by acoustibop on 2007-10-09
A number of programs have this problem with controllers: it's because they look for the controller in /dev rather than /dev/input.  Sometimes it's possible to change this in the program's configuration, but the easiest solution is just to put a symlink to your controller in /dev.

What Logitech controller are you using?  The only problem I have with my Rumblepad 2 is that each directional control configures as one of two controls rather than one of four; the best way to get round this seems to be to edit the configuration file manually: note the number for Up and increment it by 1 for each successive directional control.  That is, Up is 4097, so Down becomes 4098, Left 4099 and Right 4100 for my controller.

---

### Post by F-3582 on 2007-10-09
> **disturbedite said:**
> this is the one i'm using, its updated for feisty even tho i'm on gutsy:
This one keeps crashing for me everytime I try to change some OpenGL-related things, like resolution, color depth or full-screen mode...

---

### Post by cfehunter on 2007-10-10
i fixed my problem with fullscreen now. it was just that i had enter set to start, and it paused it when i went to full screen and that caused it to crash for some strange reason.

Does anybody know how to make the emulator use 2XSAI in full screen mode? I've been trying to get it to work but without a floating menu in fullscreen it's proving to be a problem.

---

### Post by s_spiff on 2007-10-10
**Disclamer** : Newb to emulators and the such.

Anyone has a x64 deb for this? and also, how do i go about using this? where can I get the games?

---

### Post by disturbedite on 2007-10-10
*don't* ask where to get the games.

---

### Post by i23098 on 2007-10-10
> **disturbedite said:**
> *don't* ask where to get the games.

where to get the x64 deb? ;)

---

### Post by disturbedite on 2007-10-11
if there isn't a link to a 64bit deb package in this thread then maybe one doesn't exist.  i'd google it.

---

### Post by macness on 2007-10-12
Can you use version 2.14 source to build a deb package?  I'm really wanting to test this out!

Oh and I'm running Gutsy Beta.

---

### Post by mthei on 2007-10-12
Version 2.14 is available on GetDeb.net. It works well, but there are no icons in the program's menus, and it feels very sluggish, so I'm sticking with the ones up here for now. Still, it feels as if Gens has come a long way since I used it on Windows before I switched to Kega Fusion. These are excellent emulators, thanks for these.

---

### Post by BigSilly on 2007-10-12
I tried that version, but it wasn't half as good as the one from this very forum.

---

### Post by hernyman on 2007-10-13
Just tried it in Gutsy RC, works fine.

---

### Post by wryun on 2007-10-15
I'm still planning on spending some time on this to reduce the crashes and add a couple more features, just been busy/lazy. Crashes are due to only having one window now vs. previous builds with separate menu, because I bodged it in without properly understanding the code :)

Joystick problems - noted, I'll have a look. I think this section needs a complete rewrite.

GUI sync problems - yes, noticed them myself, haven't tracked them down yet.

If you are having crashes after upgrading, please remove your .gens directory and try again (the config files changed in a dodgy way to avoid a particular problem - again, this will hopefully be rewritten).

2.14 version - this doesn't exist. Some versions are mistakenly labelled 2.14 because they're taken from a 2.14 source dump which included all the cross-platform versions, but the only changes between 2.12 and 2.14 were to the Windows version and don't seem at all useful for Linux. I'll probably bump the CVS up to 2.15alpha or something to avoid confusion though. Or is there a better suggestion?

---

### Post by hagiviz on 2007-10-15
sir good day...i'm new in this ubunto thing... iwant to learn more about it...... i wonder how do you do the installation thing? how do i open to acces the term called "terminal" to put the text command line for installation... i downlaoaded the packages but when i install it it wont work..... plz help.

---

### Post by DancemasterGlenn on 2007-10-15
Good to hear an update, wryun. Any thoughts on adding the "maintain aspect ratio" option? A separate resolution for windowed and fullscreen would also be welcomed, unless it's there and I'm just not seeing it...

---

### Post by disturbedite on 2007-10-15
> **hagiviz said:**
> sir good day...i'm new in this ubunto thing... iwant to learn more about it...... i wonder how do you do the installation thing? how do i open to acces the term called "terminal" to put the text command line for installation... i downlaoaded the packages but when i install it it wont work..... plz help.
it would have been better to ask that in the "Absolute Beginner Talk" section.

---

### Post by wryun on 2007-10-15
> **DancemasterGlenn said:**
> Good to hear an update, wryun. Any thoughts on adding the "maintain aspect ratio" option?

The aspect ratio thing is something you should be able to control in your drivers - there should be some way to tell your monitor/video card not to stretch the output to widescreen for 4:3 resolutions. Don't have one of these myself, unfortunately, so I couldn't say how.

---

### Post by DancemasterGlenn on 2007-10-16
Hm. Psx (the emulator) and ZSNES both have options to correct aspect ratio, so I've never needed to dig through my drivers to accomplish this. That's the only reason I mentioned it, but I don't know how either emulator accomplishes this. But yes, if you don't have a widescreen monitor yourself, I suppose a feature like that will probably not be very high on your list.

The separate resolutions for windowed/fullscreen would still be most welcome, if that is on your to-do list. Thanks again, I'm really enjoying this emulator.

---

### Post by megamaced on 2007-10-17
> **wryun said:**
> I'll probably bump the CVS up to 2.15alpha or something to avoid confusion though. Or is there a better suggestion?

I agree with the version bump as that would solve all the confusion :cool:

I'll keep an eye on the CVS tree and make new packages as and when needed. I plan to build a Gutsy package for the current CVS build quite soon.

---

### Post by disturbedite on 2007-10-17
> **megamaced said:**
> I agree with the version bump as that would solve all the confusion :cool:

I'll keep an eye on the CVS tree and make new packages as and when needed. I plan to build a Gutsy package for the current CVS build quite soon.
i agree too with the version bump, perfect way to differentiate it.

thanks megamaced!

---

### Post by revolve on 2007-10-20
i'm having a problem with this. The package installed fine and the program starts, but whenever I try to do anything(Start a game, change resolution, etc) it crashes. I've deleted the .gens folder and still it crashes on me.

Here's what it says if I try to start it with terminal:

The program 'gens' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadRenderRequest'.
  (Details: serial 23 error_code 160 request_code 149 minor_code 1)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Segmentation fault (core dumped)

---

### Post by Dirkomatic on 2007-10-22
I love gens, but I've run across a problem and I can't seem to figure out the answer.  I'm trying to map the space bar to my C button...  when I do that it doesn't work and I just get a -1 in the gens.cfg if I try to save it.

Any suggestions?

---

### Post by Super Jamie on 2007-10-28
Hi, thanks for making this package. Works great for me!

Gutsy installed since Beta, nvidia-new driver in Twinview mode, using windowed OpenGL mode, SB Live 24-bit using ALSA.
I have a usb gamepad (acutally a USB-to-PS2 converter) which is regognised by jscalibrate, which is also working fine.
Haven't found any problems at all.

---

### Post by Frak on 2007-10-28
Have you uploaded this to the REVU? The MOTU would be very happy to have a community uploader. You could also create a launchpad personal repository.

---

### Post by DoktorSeven on 2007-10-28
Still freezes in the middle of games for me, no errors or any messages from console when frozen.  Has to be killed with kill -9.  This is on Gutsy (but happened when I had it installed on previous versions) under fluxbox with nvidia card (properly configured).

No other games have issues, and a compiled gens-rc3.5 (from an old thread on the Gentoo forum) works just fine.

---

### Post by BigSilly on 2007-10-28
Any chance of packaging this for Gutsy? I can't be doing without me Gens! :)

I tried this current version, but it causes problems on Gutsy, with the mouse pointer slowing down and the dialogue boxes not responding. I thought I'd try it since the package manager said all dependencies were satisfied, but it's not working like it did on Feisty.

Thanks in advance.

---

### Post by chronusdark on 2007-10-28
i too would like to figure out how to get this to run in gutsy
when i launch i get no errors in the terminal but if i open a rom i get "Error Opening Rom" message and if i run with compiz on it locks my machine up

---

### Post by DancemasterGlenn on 2007-10-28
Really? I just upgraded to gusty (kept my old packages) and Gens is still running fine for me...

---

### Post by acoustibop on 2007-10-29
@BigSilly & chronusdark: like DoktorSeven, try some of the earlier packages (there may be some floating around in this thread): I could never get the latest one to run on Feisty, either.  Haven't had time to check it out on Gutsy yet, but when I do, if the newest doesn't work, I'll try older ones.

---

### Post by megamaced on 2007-10-29
> **BigSilly said:**
> Any chance of packaging this for Gutsy? I can't be doing without me Gens! :)


You bet! I'll get a package done in the next few days

---

### Post by BigSilly on 2007-10-29
> **megamaced said:**
> You bet! I'll get a package done in the next few days

That's brilliant! Thanks very much. I'll keep an eye on this forum.

Cheers for your hard work.  8-)

---

### Post by chronusdark on 2007-10-29
a little off topic but does anyone know of an genesis emu that has been updated within the last 2 years

---

### Post by F-3582 on 2007-10-29
Technically yes. It's called Kega Fusion and has been updated 21 months ago which is technically within the past two years ;) Unfortunately this one is not for Linux.

Oh, and there's HazeMD which is a derivative off MAME. It's been updated quite frequently for a while aiming to bring near-perfect Genesis emulation. However, it likes its ROMs stored the MAME way which might mean some work on your side, I suppose. Unless you get ClrMAMEPro to do the dirty job of renaming and byte-swapping for you. And running on Linux, of course ;)

---

### Post by chronusdark on 2007-10-30
> **F-3582 said:**
> Oh, and there's HazeMD which is a derivative off MAME. It's been updated quite frequently for a while aiming to bring near-perfect Genesis emulation. However, it likes its ROMs stored the MAME way which might mean some work on your side, I suppose. Unless you get ClrMAMEPro to do the dirty job of renaming and byte-swapping for you. And running on Linux, of course ;)

ick i hate renaming roms I just finished sorting and renaming i dont think my wife could take a round 2 (it drives her nuts when i organize mp3/roms)

---

### Post by F-3582 on 2007-10-31
As I said, just run ClrMamePro through WINE and let it do it for you.

---

### Post by BigSilly on 2007-11-05
Just wanted to post up again to say thanks to all those involved in bringing this emulator to Linux. I've now got the current packages working just fine on both Gutsy and Mandriva 2008. Like a plonker I'd just not disabled the 3D desktop effects. Now I've done that, all works wonderfully on both Linux's.

Top emu, and thanks for all your hard work.

---

### Post by adam0509 on 2007-11-07
It's ABSOLUTELY NECESSARY to get a STABLE package for Hardy Heron !!!


Please !!!

---

### Post by Frak on 2007-11-07
> **adam0509 said:**
> It's ABSOLUTELY NECESSARY to get a STABLE package for Hardy Heron !!!


Please !!!
I don't see the need. There isn't enough people using Hardy, it would be a waste of time and effort. Plus, the Gutsy Package should run FINE under Hardy.

---

### Post by DancemasterGlenn on 2007-11-07
> **Frak said:**
> I don't see the need. There isn't enough people using Hardy, it would be a waste of time and effort. Plus, the Gutsy Package should run FINE under Hardy.

What Gutsy package?

---

### Post by Rafadagaffer on 2007-11-08
Ill download and test this later on. got a bunch of Sonic roms I can play :)

---

### Post by megamaced on 2007-11-08
Finally got around to compiling Gens CVS 20070625 with the Gutsy libraries. As for an altogether new CVS package, well you will have to harass Wryun for that!

[http://www.zshare.net/download/477181507f7e3b/](http://www.zshare.net/download/477181507f7e3b/)

---

### Post by DancemasterGlenn on 2007-11-09
New package works great, my old one worked fine when I upgraded from Dapper, but I figured I might as well use this one.

Wryun, consider yourself harassed!

---

### Post by BigSilly on 2007-11-09
Thanks for this megamaced. Excellent stuff, and have installed it immediately. Performs better than the Feisty version did on Gutsy for me, so well worth an install.

Now we really must petition Wryun....

---

### Post by Mellowdrone on 2007-11-09
I'll grant I haven't read the entire thread, so no worries, but upon reading the initial question I thought I'd throw in my two cents. The emulator works well - tried it with Sonic 1, 2, and 3, and each game works as expected. In windowed mode, like some of the others have posted, the colors do come off flat interestingly, but windowed mode is about all I ever play due to personal preference.

 My controller does have some issues - the Xbox 360 Wired Controller - as pressing one button in the joypad configuration results in two or three button presses. Other programs using the joypad work fine. I can play with the keyboard, though! So that works, too.

Anyway, thought I'd add what I could.

---

### Post by disturbedite on 2007-11-09
> **Mellowdrone said:**
> My controller does have some issues - the Xbox 360 Wired Controller - as pressing one button in the joypad configuration results in two or three button presses.
same here with my original xbox controller s (wired).  i could be wrong, but i believe the reason for this is cuz the controller is too sensitive.  i wouldn't know how to adjust its sensitivity tho if it is even possible...

---

### Post by matemargo on 2007-11-13
> **megamaced said:**
> Finally got around to compiling Gens CVS 20070625 with the Gutsy libraries. As for an altogether new CVS package, well you will have to harass Wryun for that!

[http://www.zshare.net/download/477181507f7e3b/](http://www.zshare.net/download/477181507f7e3b/)

After installing the package I get this error:

```

Segmentation fault (core dumped)

```

Any ideas?

---

### Post by ooshlablu on 2007-11-19
> **d3x7r0 said:**
> The emulator looks fine but the sound keeps slowing down like the computer can't handle it :? I have an Audigy 4 on a Pentium 4 3.06GHz so I don't think the computer is to blame... And I really wanted to play those good ol' sonic games... :(

hey, i had the same problem for a while, but it seems that enabling opengl does the trick.
if u don't have opengl desktop enabled or opengl period, make sure the option is disabled

---

### Post by ooshlablu on 2007-11-19
> **disturbedite said:**
> same here with my original xbox controller s (wired).  i could be wrong, but i believe the reason for this is cuz the controller is too sensitive.  i wouldn't know how to adjust its sensitivity tho if it is even possible...

i use the xbox360 controller and had the same problem with sensitivity

the old version (gens 2.12b/a) has not that great controller support. compiling the new cvs version will solve ur problem

---

### Post by darqfiber on 2007-11-23
gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for ‘M68K_Fetch[1].offset’)
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for ‘M68K_Fetch[2].offset’)
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for ‘M68K_Fetch[3].offset’)
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for ‘S68K_Fetch[0].offset’)
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_32X_Rom_Bank’:
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_Prg_Ram’:
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[4]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[4]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b/src/gens'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1247:
debian/rules build failed
@raven:~/Desktop/gens_2.12b_src/gens-2.12b$ 

Anyone know how to build either version of the source on amd64 gutsy ? I tried the instructions in this thread but I get coming out with some error. Maybe some nice person on here has x64 debs they could send to me?

Thanks

-DF

---

### Post by Frak on 2007-11-23
> **darqfiber said:**
> gens_core/cpu/68k/cpu_68k.c:27: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:27: error: (near initialization for ‘M68K_Fetch[1].offset’)
gens_core/cpu/68k/cpu_68k.c:28: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:28: error: (near initialization for ‘M68K_Fetch[2].offset’)
gens_core/cpu/68k/cpu_68k.c:29: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:29: error: (near initialization for ‘M68K_Fetch[3].offset’)
gens_core/cpu/68k/cpu_68k.c:63: error: initializer element is not constant
gens_core/cpu/68k/cpu_68k.c:63: error: (near initialization for ‘S68K_Fetch[0].offset’)
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_32X_Rom_Bank’:
gens_core/cpu/68k/cpu_68k.c:365: warning: cast from pointer to integer of different size
gens_core/cpu/68k/cpu_68k.c: In function ‘M68K_Set_Prg_Ram’:
gens_core/cpu/68k/cpu_68k.c:390: warning: cast from pointer to integer of different size
make[4]: *** [gens_core/cpu/68k/gens-cpu_68k.o] Error 1
make[4]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b/src/gens'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/Desktop/gens_2.12b_src/gens-2.12b'
make: *** [build-stamp] Error 2
debuild: fatal error at line 1247:
debian/rules build failed
@raven:~/Desktop/gens_2.12b_src/gens-2.12b$ 

Anyone know how to build either version of the source on amd64 gutsy ? I tried the instructions in this thread but I get coming out with some error. Maybe some nice person on here has x64 debs they could send to me?

Thanks

-DF
That is code for the Motorola 68k chipset. I wonder why it is trying to build that?

---

### Post by Jengu on 2007-11-23
I'm also getting the core dump error, any ideas? I tried disabling compiz because I guess that was the problem, but it didn't help. I also tried with and without my joypad plugged in.

---

### Post by Hatta0 on 2007-11-25
I've compiled the source on debian sid, it built and installed fine.  But when I try to run it flashes the gui for a second then seg faults. It's not an opengl problem on my part, everything else opengl runs flawlessly.  None of the .debs work either.

I don't even get any helpful error messages:

hatta@iblis:/usr/src/gens-2.13-cvs20070625$ gens
Segmentation fault
hatta@iblis:/usr/src/gens-2.13-cvs20070625$

---

### Post by acoustibop on 2007-11-25
Try the 2.12b .deb - it's linked in this thread somewhere, Hatta0.

The 2.13 ones did the same for me in Feisty and Gutsy.

---

### Post by KnuX on 2007-12-04
It would be great if someone can tell us how to compile the CVS version on x64 system... I'm using Debian Sid x64 and I have exactly the same error as above :(

---

### Post by Felarin on 2007-12-08
Has anyone compiled a package with netplay so far or has the source file for the netplay plugin so that i can create a package and release it?

---

### Post by scunc_dvl on 2007-12-15
Before I try a forced-install on my amd64 system, does anyone know the dependancies? (i.e. packages I need to install).

In getting some 32-bit stuff running, I've had to manually install 32-bit libs in the past.. But somehow I don't think this is necessary, if someone else just "did" it. :P (I'm currently using Gutsy)

---

### Post by megamaced on 2007-12-16
The dependencies for Gens on Gutsy are:

```
libatk1.0-0 (>= 1.13.2), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libgl1-mesa-glx | libgl1, libglib2.0-0 (>=
         2.14.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.18.2),
         libsdl1.2debian (>= 1.2.10-1), libx11-6, libxcomposite1 (>= 1:0.3-1),
         libxcursor1 (> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>=
         1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1,
         zlib1g (>= 1:1.2.3.3.dfsg-1)
```

Most of the packages should be installed by default in Ubuntu.

As for Gens on x64, I really don't know. I don't run a x64 OS so I've never really looked into compiling and installing Gens on that platform.

---

### Post by Frak on 2007-12-16
> **megamaced said:**
> The dependencies for Gens on Gutsy are:

```
libatk1.0-0 (>= 1.13.2), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0),
         libfontconfig1 (>= 2.4.0), libgl1-mesa-glx | libgl1, libglib2.0-0 (>=
         2.14.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.18.2),
         libsdl1.2debian (>= 1.2.10-1), libx11-6, libxcomposite1 (>= 1:0.3-1),
         libxcursor1 (> 1.1.2), libxdamage1 (>= 1:1.1), libxext6, libxfixes3 (>=
         1:4.0.1), libxi6, libxinerama1, libxrandr2 (>= 2:1.2.0), libxrender1,
         zlib1g (>= 1:1.2.3.3.dfsg-1)
```

Most of the packages should be installed by default in Ubuntu.

As for Gens on x64, I really don't know. I don't run a x64 OS so I've never really looked into compiling and installing Gens on that platform.
All you need to do is provide the source debian packages and people can build the .deb themselves.

---

### Post by megamaced on 2007-12-16
> **Frak said:**
> All you need to do is provide the source debian packages and people can build the .deb themselves.

I do! Check the first post in this thread for the links! :)

---

### Post by Frak on 2007-12-16
> **megamaced said:**
> I do! Check the first post in this thread for the links! :)
Then all you need to do is describe how to install build-depends for apt, then run dpkg-buildpackage in the  directory.

---

### Post by megamaced on 2007-12-16
I think the problem is that Gens won't compile on x64. I am not a programmer so I don't know why this is!

---

### Post by Frak on 2007-12-16
> **megamaced said:**
> I think the problem is that Gens won't compile on x64. I am not a programmer so I don't know why this is!
Since it is an emulator, I could possibly see why this is. It most likely needs to be ported, since 64-bit instruction sets are different from 32-bit. (x86_64 bit processors don't run the SSE1 instruction set in 64-bit mode)

---

### Post by disturbedite on 2007-12-16
> **Frak said:**
> That is code for the Motorola 68k chipset. I wonder why it is trying to build that?
cuz the MD/Genesis [used a motorola 68k]("http://en.wikipedia.org/wiki/Motorola_68k#Main_uses").

---

### Post by el_itur on 2007-12-23
The gutsy version segfaults here, sorry if they reported it already, I can't read the whole thread
[edit]
I was talking about the unstable

the stable version works but won't load anything i throw at it :(

---

### Post by wingnux on 2007-12-23
> **el_itur said:**
> The gutsy version segfaults here, sorry if they reported it already, I can't read the whole thread
[edit]
I was talking about the unstable

the stable version works but won't load anything i throw at it :(

Same here!

---

### Post by roachk71 on 2007-12-26
Yes and No:

Yes: The stable 2.12 version starts, but I haven't tested it with a ROM yet...

No: The CVS version crashes with a segmentation fault.

My computer is a dual-core AMD64 machine. Guess we'll see how it goes...:)

For the life of me, I can't seem to get Flash working in 6.06 AMD64. Due to this fact, web browsing has just become quite mundane; so I'd really like to start using my Gen/32X ROMs playing again. Oh, the nostalgia... \\:D/

Update:
It works!! The sound is a bit out of sync, but the games I have play well, and the audio's almost perfect!

Many thanks for those links!

---

### Post by adam0509 on 2008-01-06
got sound issue : when sound is activated, gens gets slowwwwww

I've tryed everything I could (closing all program, redefining quality etc...), but nothing works !!!


EDIT :

Strange, works fine in antoher -clean- session...

...**** gnome seriously !!!


EDIT 2 :

In fact, didn't found any valuable solution... if you get one, please post !

---

### Post by james_mcl on 2008-01-08
Just wanted to thank you, megamaced! I had actually ruled out installing gens due to it's notoriously difficult compilation until I discovered you'd provided a deb package, and I now have an absolutely brilliant MD/MCD emulator running without any problems.

---

### Post by jetfire4 on 2008-01-09
Has anyone got this working on a fedora 7 powerpc64 build?   I tried compiling from source and during the make procedure I got a "expected identifier before numeric constant" and the "all-recursive" error.  Then when I tried to install the .deb it said i didn't have the "dpkg" command file.  Is there any way to install a debian package on fedora?

---

### Post by roachk71 on 2008-01-09
I doubt there is a way to install a Debian package on Fedora, unless the Red Hat repositories offer dpkg and apt.

Although Ubuntu is a Debian-based distribution, the repos also include a tool for Red Hat packages to be converted into Debian packages (alien). I don't believe there's an easy way to do the reverse from Red Hat-based distributions, unfortunately.

However, if you manage to get your hands on the two packages mentioned above, you could download one of the 32-bit packages like I did (my machine is a dual-core AMD64-based one), and force its installation with:
```
dpkg --force-architecture -i *package_name*.deb
```Just make sure you have all of the 32-bit libraries needed by Gens installed first.

Uh, Oh: I just re-read that post, and it (as yet) has not been built for a PowerPC machine, so this could be dangerous to install on your hardware, or simply not work at all (without x86 emulation, that is.)

---

### Post by F-3582 on 2008-01-10
Alien can convert packages from .rpm to .deb and vice versa.

---

### Post by jetfire4 on 2008-01-10
Update:  It looks like the alien and dpkg i found requires the mandiva "perl-base" version as a dependency and if i try to install that it says it conflicts with the perl-base I already have installed, so I'm not gonna mess with that.  I thought about installing ubuntu but I put so much time and effort into fedora and I like the theme.  Then i found out sdlmess will play genesis games but the latest version i downloaded apparently has a "keyboard crash" that can only be fixed with "sdl 1.2.13" which there is no rpm out for ppc yet, only the source i installed per directions yet package manager still says i have 1.2.12.  So i'll just have to wait until that ppc rpm package comes out for sdl.

---

### Post by jetfire4 on 2008-01-10
Now I'm thinking of changing to a i586 system.  PPC rpms are such a pain in the *** to find.  The only reason i got PPC is I saw some guy bragging about it in a forum and it seems like PPC takes up more memory, crashes more, and hard to find RPMs for.   While I'm at it i'll probably go to Debian so I'll go with ubuntu.  Just so it lets me install SDLMame, FakeNes and a few other game programs which is all i wanted it for on my Playstation.

---

### Post by jetfire4 on 2008-01-10
The plot just thickened, koji.fedoraproject.org just released the ppc rpm for sdl-1.2.13 which is supposed to fix a whole bunch of other bugs besides the keyboard crash like pulse audio.   I wont be able to install it for a while, but it looks like i may keep powerpc after all if this just installs sdlmess and who knows maybe it will get the old dgen working right.

---

### Post by jetfire4 on 2008-01-11
I found out mess was just crashing because i didn't set up a output directory, did that and it works now except I have to find a way to configure the controller buttons because they're all out of whack.  I even set up a way to start games from file manager with the command line "'/usr/bin/mess' genesis -cart sonic.smd".  It has support for nintendo64 too so that should be good.  It seems ok after i changed opengl to soft in video and enabled 0 to 1 for multithreading.  Sound isn't working on some games.  I would still prefer to have gens too.

---

### Post by jetfire4 on 2008-01-13
Is anyone here familiar with dosbox?  I have it with the autoconfig so it mounts a C: drive at startup with one of my directories.  What would be the smallest OS i could install on that to use gens?  Would the joystick work?  I tried to run gens on it and it said "illegal command"

---

### Post by wryun on 2008-01-14
> **BigSilly said:**
> Now we really must petition Wryun....

Sorry about the lack of action on this guys... unfortunately, it's been one of those things I think I 'ought to do', and that usually pushes things down my list of priorities ;) Even worse news is that I had to put my Linux box in storage last month due to moving house, and I've started a new job, so I'm afraid that I'm unlikely to do anything more on gens for ages. This, of course, is not stopping anyone else from grabbing the latest CVS and fixing stuff :)

For those who want to code, priorities to fix from what I remember:
  - add the ATI patch in
  - clean up joystick support
  - work out what's going on with the GUI updates, and put the OpenGL option into the Glade files
  - fall back properly to no OpenGL when OpenGL fails
  - rework the config files parsing (it's kinda ugly, and more significantly relies on unique chars which potentially conflict with things in filenames. I changed from [] to *? for this reason).
  - work out why it loses the plot sometimes on fullscreen/window switch

Enhancements:
 - XVideo support for those whose OpenGL isn't working - see the latest generator source
 - J-Cart support - one of the recent console emulator releases has it, can't remember which (PSP?)
 - run all the files through a code beautifier so the indentation/style gets half-way consistent (didn't do it myself because it would make the repository a mess of changes; wanted to wait until the basic patches were in and 2.13 was something stable)
 - rewrite the terrifying joystick code

---

### Post by wryun on 2008-01-14
> **jetfire4 said:**
> Is anyone here familiar with dosbox?  I have it with the autoconfig so it mounts a C: drive at startup with one of my directories.  What would be the smallest OS i could install on that to use gens?  Would the joystick work?  I tried to run gens on it and it said "illegal command"

There is no port of Gens to DOS, so... get the Linux version working? Try running the windows version under Wine?

---

### Post by jetfire4 on 2008-01-15
Problem solved for my search for a genesis emulator in powerpc.   The Xe multi system emulator I found on planetemu.net.  It installed like a breeze and the gui is smooth as snes9x-gtk.  all the genesis games are working now with easy joystick mapping.

---

### Post by tghe-retford on 2008-01-18
> **F-3582 said:**
> Technically yes. It's called Kega Fusion and has been updated 21 months ago which is technically within the past two years ;) Unfortunately this one is not for Linux.
Kega Fusion running using Wine did get a major step closer lately as the problem with the program not running under X's 24-bit colour mode has been fixed for Fusion and a few other programs. The problem now is that the DirectX window where the games graphics should be have been shifted down and to the right, leaving a black border in the top and left of the window. Moving the window only makes things worse.

I tried to send a test result report to Wine's AppDB, but something went wrong.

You can run Fusion perfectly if you set your X windows environment to 16-bit colour mode, but I find it is too much hassle.

If only Kega Fusion could be ported to Linux... sigh!

More information: [http://www.eidolons-inn.net/tiki-view_forum_thread.php?comments_parentId=4261&forumId=10](http://www.eidolons-inn.net/tiki-view_forum_thread.php?comments_parentId=4261&forumId=10)

Anyway, it is a step in the right direction and once this bug is fixed, I will move from using Gens to Kega Fusion, as I have found Kega Fusion to be more compatible and have better sound compatibility.

---

### Post by DancemasterGlenn on 2008-01-19
I'm disappointed to hear that we won't be seeing any more work on Gens for quite a while (I know someone else could pick it up, but who knows when that will happen?), but life obviously comes first, and I hope thins work out at your new job and home. It's mostly disappointing that this may turn into a thread where people start posting about alternatives they'll be using instead of Gens, when you did so much amazing work on this port for us. I just wanted to say thank you for your work, wryun. I'm gonna see if I can find someone who would be interested in picking up this project from where you've left off. I don't want Gens to die!

EDIT: I posted on the zsnes forum in the hopes that one of the coders who frequent it may take up the cause. Here's hoping!

---

### Post by disturbedite on 2008-01-19
> **tghe-retford said:**
> ...
Anyway, it is a step in the right direction and once this bug is fixed, I will move from using Gens to Kega Fusion, as I have found Kega Fusion to be more compatible and have better sound compatibility.
fwiu the opposite is the case.

---

### Post by F-3582 on 2008-01-19
What do you mean by that? Fusion is a lot better than Gens in many aspects - mostly the sound emulation. Compare them running Comix Zone and you'll hear what I mean. Only MAME/HazeMD seems to come close to Kega, at the moment.

---

### Post by leech on 2008-02-03
> **DancemasterGlenn said:**
> I'm disappointed to hear that we won't be seeing any more work on Gens for quite a while (I know someone else could pick it up, but who knows when that will happen?), but life obviously comes first, and I hope thins work out at your new job and home. It's mostly disappointing that this may turn into a thread where people start posting about alternatives they'll be using instead of Gens, when you did so much amazing work on this port for us. I just wanted to say thank you for your work, wryun. I'm gonna see if I can find someone who would be interested in picking up this project from where you've left off. I don't want Gens to die!

EDIT: I posted on the zsnes forum in the hopes that one of the coders who frequent it may take up the cause. Here's hoping!

Why don't we post it over on [http://www.happypenguin.org](http://www.happypenguin.org) ? They have a Game of the Month feature, where they pick a game and get all the developers on there that want a project to work on to polish it up.  Gens counts as a game to me...  

Leech

---

### Post by DancemasterGlenn on 2008-02-03
Gah! I knew I forgot something. I posted on the ZSNES forums, and while I didn't get a huge response (one post!), Byuu of bsnes had this to say:

> Sadly, I barely have time to maintain my own apps. Which really sucks, so many people help me out yet I can rarely return the favor. So no help from me to fix those issues in Gens. However, if anyone wants to, you can use the XVideo code in bsnes, as public domain, to add to Gens.

So that would be a potential source of XVideo code, if someone would like to implement it. I'm almost conveniently inept with code, but I thought I would throw this into the ring and see if anyone would like to add this code to wryun's work. Does anyone have the know-how to do this?

You can find Byuu's bsnes source at [http://byuu.cinnamonpirate.com/](http://byuu.cinnamonpirate.com/)

EDIT: Also, Leech, I definitely think you should shoot those guys an email or something... it couldn't hurt, as long as wryun doesn't mind (since he seems to be the person to ask, if he's still at least looking at the forums).

---

### Post by disturbedite on 2008-02-03
yeah, that sounds like a good idea to me.  i hope the gens builds don't die here...

---

### Post by baroughter on 2008-02-14
I compiled from the CVS source you uploaded, and Gens runs great on my Gentoo box.  Except it's a little slow at times.  Is it normal that it uses 70% cpu?  I'm using it on an old Pentium 4, so I guess I can't expect much.  Also OpenGL makes it run much slower, though I've got a Geforce 4 in there.  I can't really see a performance increase when changing rendering modes.

---

### Post by basfo on 2008-02-28
Great work. I was struggling with dgen, i was making a little script with zenity so it was a little easier to execute a game. The compatibility problems and ugly joystick support (i couldn't make it work with other than the old 3 button pad) were making me go grazy, but then you apperead, and all my work for the last couple of days become useless. Great work, this package should be on the official repositories.
:mrgreen:\\:D/
Thanks
Basfo

---

### Post by CaptainCabinet on 2008-02-28
Just downloaded and worked perfect for me. :)

---

### Post by wah_wah_69 on 2008-02-28
¡Hi everyone!

It was me who added opengl to gens long time ago.
[http://forums.gentoo.org/viewtopic-t-204287-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-204287-postdays-0-postorder-asc-start-0.html)

I know the joystick code is ugly it's something I've always wanted to rewrite I have a cvs co from some time ago (I think there are no recent submissions,checked the sf page a while back),in fact I do not use gens now because my joystick which is a xbox1 pad with usb cord ,constantly gives axis movement events (bad calibration I think) and when configuring all the buttons events are detcted as axis 1 up.

I can't edit the config file by hand because the dpad of the joystick I want to use is not being considered in the joysick code (It reads the first 3 or 4 axis but the dpad is axis 5 or so).

But prior to that I'd like to write a custom gui a la Zsnes for gens It's something I really like to do, as ugly and difficult to maintain as custom gui's are,I don't care if it's not added to the main gens source,I'll do it anyway.

I have 2 years old code, for a very basic menu and file navigation,never have the time (or will) to finish it's something I really like to do but is always "on hold".

I think is because I started writing code instead of designing everything first.

It's written in plain good old c,my main concern was to use less libraries as possible and to be as portable as possible.

I've also thought about making a gui with opengl,but that's another story.

Here's a screenshot:

[http://omploader.org/vNWV2/CustomGuiGens.PNG](http://omploader.org/vNWV2/CustomGuiGens.PNG)

---

### Post by megamaced on 2008-02-29
Hey wah_wah_69

It is your code from the Gentoo forums, plus a few extra patches I found around the internet that make up my Gens 2.12b package! Great work on the openGL code by the way.

Have you checked out the latest CVS build? The Gens GUI no longer operates in two windows anymore (ie one for the game and one for the menu). Everything has been integrated.

It would be great if you could start hacking away at the CVS code base. Wryan was doing a lot of work on it but has been a bit too busy of late. I think he pointed out some stuff that needs to be done on Gens earlier in this thread.

I'd love to fix all the bugs myself but I am not a programmer. I can make debian packages but that's my lot :)

---

### Post by wah_wah_69 on 2008-03-01
I've been toying with the latest cvs checkout (Although I had a checkout from some months ago and there's no write activity since june last year).

I've gotten my Xbox  pad (The first revision of the pad the one for yeti sized hands) to work correctly,the analog stick no longer is configured as every button.

It turns out the sleep function is not sleeping at all,there was a warning, but I didn't noticed until y run it through gdb,replaced the sleep calls with SDL_Delay calls.

Then I hardcoded the usage of the dpad (axis 6 and 7 which were not being taken into account by the input code).

By hardcoding I mean to simply write the code for it to work,it's not clean,it's not configurable it's only useful for people with a xbox pad or people with a joystick which dpad is assigned axis 6  and 7.

I'd like to rewrite the input code which is a tad messy,but I should first look at the problem carefully and design a proper solution with full configurability.

---

### Post by DancemasterGlenn on 2008-03-01
megamaced, perhaps you should update the first post regarding wryun's current inability to work on the project, and also his list of things that still need to be worked on (from that post he made). Hopefully wah_wah_69 and others who would like to pick up from where he left off can look through that list for starting points on further work.

---

### Post by disturbedite on 2008-03-01
well i have an xbox s controller (newer non-yeti sized ;)) that i use for all my games & emulators.  (that it works with, which almost everything).
i'd love to be able to use it with gens.

---

### Post by chips24 on 2008-03-03
i really want to play my sonic  games. i cant find the file when im done downloading it.

---

### Post by GSZX1337 on 2008-03-03
Hit Ctrl-Y to open your Downloads and hit open.

---

### Post by BigSilly on 2008-03-08
Can I respectfully ask that Megamaced package this up again for us all for use in Hardy when it comes out? I for one would be very grateful indeed, since this is one of my favourite emulators on Ubuntu, and I'd hate to lose it after an upgrade to Hardy. Also, if there's a chance could you do the same for Mandriva 2008 too? I know it's cheeky to ask, but it would be fantastic! :D  I've installed the Mandriva package you have on page one of this thread, and it's excellent for the most part, but for some reason I'm not getting any audio when playing Mega CD games. It's fine on Gutsy.

Let me know. Sorry to be really cheeky. :redface:

---

### Post by megamaced on 2008-03-08
[quote=DancemasterGlenn]megamaced, perhaps you should update the first post regarding wryun's current inability to work on the project, and also his list of things that still need to be worked on (from that post he made). Hopefully wah_wah_69 and others who would like to pick up from where he left off can look through that list for starting points on further work. [/quote]

Done

wah_wah_69 we are calling out for you! :)

[quote=BigSilly]Can I respectfully ask that Megamaced package this up again for us all for use in Hardy when it comes out? I for one would be very grateful indeed, since this is one of my favourite emulators on Ubuntu, and I'd hate to lose it after an upgrade to Hardy. Also, if there's a chance could you do the same for Mandriva 2008 too? I know it's cheeky to ask, but it would be fantastic!  I've installed the Mandriva package you have on page one of this thread, and it's excellent for the most part, but for some reason I'm not getting any audio when playing Mega CD games. It's fine on Gutsy. [/quote]

I will package Gens for Hardy Heron upon general release. I don't want to package it now because Hardy is still evolving.

I don't actually run any RPM based distros so it's difficult to package Gens in that format. My Gens RPM package was created using Alien, which basically converts DEB to RPM with varying degrees of success. I don't know enough about the RPM format to make a proper package I am afraid.
You could try running Alien against the latest Gutsy package. I think my Gens RPM package was run against the Dapper package.

---

### Post by BigSilly on 2008-03-09
Excellent! As long as it's running sweetly in Hardy I'm happy. Thanks for your work Megamaced. I'd love to have it on Mandriva too, but I understand your limitations. I have to tell you though; even though you don't run an RPM distro, your current Gens package runs great on Mandriva 2008. If I could just figure out why I'm getting no sound on Mega CD games...

Still, thanks again! :)

---

### Post by francois12 on 2008-03-13
gens 2.12b crashs X server when opengl is activated
VSync option doesn't help

I'm running ubuntu gusty up to date and compiz fusion is activated.

Thanks for your help
and sorry for my poor english

---

### Post by acoustibop on 2008-03-13
Try disabling Compiz, francois12.

---

### Post by francois12 on 2008-03-14
> **acoustibop said:**
> Try disabling Compiz, francois12.

I'd like to find the way without disabling it
thanks

---

### Post by BigSilly on 2008-03-14
> **francois12 said:**
> I'd like to find the way without disabling it
thanks

And it's a fair point really. Is it likely that the 3D desktop will be much more stable in Hardy? I have to disable it completely even now if I want to play a game, or watch a DVD, or countless other things. I know it's not really a discussion for the games forums, and I also realise that Compiz wasn't stable when it was included with Gutsy. But I'm really hoping it's better integrated with Hardy. Is there any news on it?

---

### Post by acoustibop on 2008-03-14
> **francois12 said:**
> I'd like to find the way without disabling it
thanks

Of course you would, francois12, but the fact is that at present, having it enabled usually causes these sorts of problems.  As BigSilly says, this may be fixed in Hardy - you could try the current beta.

---

### Post by mastrboy on 2008-03-14
hi, this also works under Debian Lenny :) Thanks..

but why do you not use the latest source? 2.14?
[http://www.gens.ws/download/gens-win32-src-2.14.zip](http://www.gens.ws/download/gens-win32-src-2.14.zip) (even if it says win32 in the name, the linux source is also in that zip file)

---

### Post by rossjman1 on 2008-03-14
How would I run a ROM in full screen from the command line?

---

### Post by acoustibop on 2008-03-15
Do gens --help for a list of command line switches, rossjman1.

---

### Post by rossjman1 on 2008-03-15
None of em work. I can run the GUI though, but I'm trying to launch the ROMS from MythTV.

---

### Post by acoustibop on 2008-03-15
> None of em work
I can only see one switch for full screen, rossjman1, --fs-mode.

Try it from a terminal - then you'll know if the problem is with running GENS from the command line, or running it from MythTV.

---

### Post by rossjman1 on 2008-03-16
The gui pops up along with a windowed screen with the ROM running.

---

### Post by mdkaneda55 on 2008-03-17
awesome! works great!! i'm running Gutsy 32bit and i attempted to install the unstable / cvs deb 1st, and that crashed on me.. so i uninstalled and tried the stable and it's running like a champ! One thing to note, most Sega CD games require "perfect syncro" to be checked to play right, otherwise it freezes at the sega cd boot up, now that i figured that out, all my games work. woo hoo!

---

### Post by acoustibop on 2008-03-17
> **rossjman1 said:**
> The gui pops up along with a windowed screen with the ROM running.

I tried it too - looks like some switches, at least, must be busted in Linux. :(

---

### Post by prurigro on 2008-03-19
> but why do you not use the latest source? 2.14?
[http://www.gens.ws/download/gens-win32-src-2.14.zip](http://www.gens.ws/download/gens-win32-src-2.14.zip) (even if it says win32 in the name, the linux source is also in that zip file)

It took a bit of hacking at the code and converting all the files to unix txt from dos to get it to compile, but it does work. However, it seems that the linux code in this is rather ancient, even compared to 2.12b; theres no opengl support and the gui is still not attached to the graphics. Not sure why newer linux versions are still getting older version numbers but you can rest assured that the packages on this site are more current than that.

---

### Post by rossjman1 on 2008-03-21
So, I take it that running a ROM in fullscreen from the command line is currently impossible?

---

### Post by acoustibop on 2008-03-21
Looks like it, rossjman1. :(

---

### Post by sl1pkn07 on 2008-04-05
[http://www.aep-emu.de/PNphpBB2-file-viewtopic-t-8698.html](http://www.aep-emu.de/PNphpBB2-file-viewtopic-t-8698.html) 

This version is based on Gens-rc3.5-opengl with an added support for real CDs.

;)

but no added support to 64 bits :(

---

### Post by BigSilly on 2008-04-05
> **sl1pkn07 said:**
> [http://www.aep-emu.de/PNphpBB2-file-viewtopic-t-8698.html](http://www.aep-emu.de/PNphpBB2-file-viewtopic-t-8698.html) 

This version is based on Gens-rc3.5-opengl with an added support for real CDs.

;)

but no added support to 64 bits :(

Cool find, and it compiled just fine for me on my Mandriva install, but sadly it's not as good as the original package in this very thread. It didn't recognise my joypad (well it let me configure it, but the direction pad didn't work whatever I did), it forgets the render you selected when you go full screen, and it crashed on me a couple of times with segmentation fault.

One to keep an eye on I reckon though, especially if development is continuing.

---

### Post by BigSilly on 2008-04-05
Actually can anyone help me with the original Gens package? I mentioned earlier that I installed it (from the first page of this thread) on Mandriva, but I get no sound with Mega CD games. I've noticed that I do get some sound, but only in game effects. It's the game music I'm not getting, though I do in the Ubuntu version. 

Having a look in the CD files it looks like the music files are MP3's. My install can play these just fine, but as I say here in Gens it won't play them. Is there anything I can do to get them to play? I don't get why Mandriva Gens won't play the music in CD games...

Thanks all. :)

---

### Post by murasame on 2008-04-16
> **BigSilly said:**
> Actually can anyone help me with the original Gens package? I mentioned earlier that I installed it (from the first page of this thread) on Mandriva, but I get no sound with Mega CD games. I've noticed that I do get some sound, but only in game effects. It's the game music I'm not getting, though I do in the Ubuntu version. 

Having a look in the CD files it looks like the music files are MP3's. My install can play these just fine, but as I say here in Gens it won't play them. Is there anything I can do to get them to play? I don't get why Mandriva Gens won't play the music in CD games...

Thanks all. :)

It's probably a matter of converting these files back to wav format and issue a proper toc/cue file. Google toc / cuemaker / mega cd for relevant info on this in your language. Sorry, I can't remember of a link but I had the same issue a couple of years ago using gens on windws... Basically, it might be related to the fact your audio files are in mp3 format...

Actually, if you have like an iso, mp3 and a cue file, you should enquire on how to make/burn a PROPER cd (or cd image) to be able to use it in both gens or even in the real thing. Most stuff that can be downloaded everywhere on the web usually WON'T be working on a real system without rebuilding a proper ISO, meaning it won't work under gens... provided linux gens does have built-in mp3 support (not sure about that though). In any case, gens WILL work with a REAL megacd game... ifif you buy the original game (which btw you should own if you use an emulator.... not to mention the system) the game will work.

---

### Post by megamaced on 2008-04-16
Gens for Linux does have mp3 support. I have several MegaCD games with audio ripped to mp3 and have no issues whatsoever. BigSilly, maybe you are missing some kind of audio package in Mandriva?

---

### Post by BigSilly on 2008-04-16
Thanks for your replies guys. I thought that too Megamaced, but so far I've been unable to pinpoint just what it could be if I am missing a package. MP3 plays back just fine on my Mandriva install under normal circumstances, so I cannot understand why it shouldn't in Gens.

Thanks again. :)

---

### Post by bornagainpenguin on 2008-04-26
/BUMP for Hardy release...

--bornagainpenguin

---

### Post by megamaced on 2008-04-26
UPDATE: 26/04/08

The Hardy Heron package is here but unfortunately Gens CVS just segfaults for me. Even the Gutsy package segfaults with Hardy. This could be a major incompatibility issue between Gens and the Hardy libraries should this issue not just be isolated to me.. At this point I suppose we should all be crying out to programmers to kick-start the Gens development again!

PS. The Gens stable package is OK with Hardy

---

### Post by BigSilly on 2008-04-27
Odd. I installed the Gens unstable package for Gutsy in Hardy before you put the new package up, and it's been fine. I'll let you know if there are any issues in the future, but so far so good. Your RPM is good in the new Mandriva too! ;)

---

### Post by begemot. on 2008-05-06
Greetings, gentlemans.

Gens "stable" works enough for me in Gutsy and Hardy, but "unstable" didn't. However, i have marked that "Netplay" option is still inactive even in "unstable" versions for both GG && HH.
I've searched this thread and didn't find any words about configuring "Netplay" option.

So, can anyone tell me what's the problem with network in this gens packages? Maybe, there is a way to include "Netplay" in Linux by compiling something?
I'm so interested in it, cuz network gaming is critically important for me and my friends, we playing in (by our opinion) best multiuser-games for "Sega Mega Drive 2" - "MK3-Ultimate" and "Super Star Soccer", even organizing tournaments, so we have to use weendows to play it for now.

Many thanks for advices.

**ADD:**
And one more thing: weendows gens version has very useful volume-chooser (25%, 50%, etc) why it's unavailable in this deb's?
I have to turn off game volume for my background mp3-music listerning, because games in gens is too loud. :dezol:

---

### Post by disturbedite on 2008-05-08
just thought i'd let all of you know (for future reference) that the hardy package works fine on kubuntu intrepid KDE4 x86.

---

### Post by MonkeeSage on 2008-05-14
> **megamaced said:**
> . . .
The Hardy Heron package is here but unfortunately Gens CVS just segfaults for me. Even the Gutsy package segfaults with Hardy. This could be a major incompatibility issue between Gens and the Hardy libraries should this issue not just be isolated to me.. At this point I suppose we should all be crying out to programmers to kick-start the Gens development again!
. . .


I also get the segfault on Hardy LTS.

After looking (briefly) at the gens CVS source and inserting some printfs, it looks like it is dieing on the call to Flip() in the last else block of the while (is_gens_running ()) block in the main() function of src/gens/emulator/g_main.c. I'm not sure why.

A bit later I'll try to see if I can  figure out the problem in Flip, but don't hold your breath (I'm not overly proficient in C, plus I have no knowledge of SDL / OpenGL programming--but hey, if it's a simple off-by-one error or something, maybe I'll catch it).

---

### Post by MonkeeSage on 2008-05-14
OK, I traced the problem back to Clear_Screen() in src/gens/sdllayer/g_sdldraw.c (specifically a memset in the if(Opengl) clause; see patch). I'm not sure what the problem is (maybe that the drawing surface is not 640*480 any more, since it is contained within the emulator window? Just a guess...). I just used the commented memset, and it seems to work.

As I said previously, I know virtually nothing about OpenGL programming, so maybe this will explode and spew brain-eating slugs into your ear canal--I'm not responsible for anything bad that happens if you use this patch. Patch is public domain.

---

### Post by disturbedite on 2008-05-15
@ MonkeeSage
now i'm even more curious why gens doesn't segfault on intrepid...

---

### Post by Firestone on 2008-05-15
I seem to have trouble using the gamestates. It worked back in Feisty and long before that in Windows, but ever since Gutsy it stopped working. I dunno if it's Gens fault or my Ubuntu install, because I did a clean install for both Gutsy n Hardy including the newest Gens(stable) I could find.
I can switch slots, but QuickLoad/Save+hotkeys don't work or give an on screen message. I can semi-load a state with 'File - load state', and althought the filename is listed in the load history afterwards, it doesn't really load anything. 

Anyone got an idea?

---

### Post by disturbedite on 2008-05-15
are you sure the savestates are actually there?  maybe there are permission issues where you told gens to save savestates.  maybe gens "acts" as if it saves, but it actually isn't cuz of permission issues.

---

### Post by MonkeeSage on 2008-05-15
> **disturbedite said:**
> @ MonkeeSage
now i'm even more curious why gens doesn't segfault on intrepid...

Yeah, that's definitely strange. You are talking about the [CVS deb](http://www.zshare.net/download/11145762daafa769/), right? I wouldn't think it to be an OpenGL bug, since other apps that use SDL + OpenGL (e.g., mednafen) work correctly. Maybe it's something to do with the ATI fglrx driver or something (I have a raedon 9550). . .hmm.

---

### Post by disturbedite on 2008-05-16
i already mentioned which package i was using:  gens_2.13-cvs200706258.04_i386

i have an onboard intel i845g graphics chip though, not a "true" video card...

---

### Post by SZF2001 on 2008-05-17
Hi, sorry for asking a stupid question that has probably been covered but I can't bother looking back page after page, so excuse me for doing so. I like playing my games in fullscreen but sometimes I need to switch out to answer an IM or check on a program or... whatever. I press ESC and Gens just goes gray, like it would on Windows, but I click and press buttons but no menu or anything comes up. I thought maybe CTRL-F would work or something but apparently not. The only way I could find my way out of fullscreen was to press CTRL-ALT-BACKSPACE...

Another question - before I used dgen, but I didn't like not having a GUI and what have you. So I found Gens, but here's the thing; in Thunar, if I go to a ROM and press the right mouse button to pull up options on what to do with that file, I get dgen twice because one time I ran it just as dgen and another as dgen -f -otherstuff... So I'm just trying to make it so those two options will go away and, if I can, have them open Gens by default.

Running Xubuntu Hardy with stable package. Thanks in advance!

---

### Post by acoustibop on 2008-05-17
The fullscreen toggle is Alt+Enter, SZF2001.

---

### Post by MonkeeSage on 2008-05-17
> **SZF2001 said:**
> Hi, sorry for asking a stupid question that has probably been covered but I can't bother looking back page after page, so excuse me for doing so. I like playing my games in fullscreen but sometimes I need to switch out to answer an IM or check on a program or... whatever. I press ESC and Gens just goes gray, like it would on Windows, but I click and press buttons but no menu or anything comes up. I thought maybe CTRL-F would work or something but apparently not. The only way I could find my way out of fullscreen was to press CTRL-ALT-BACKSPACE...

As another user said, alt+return toggles fullscreen. Most of the accelerators are marked next to the menu item for the option. E.g., in the File menu, F5 is shown next to Quicksave, thus the F5 key triggers the same feature the menu item does. Even though there is no menu item (there really should e in the CVS version, since the emulator window is contained within the frontend now), pressing ESC (un-)pauses the emulator.

> **SZF2001 said:**
> Another question - before I used dgen, but I didn't like not having a GUI and what have you. So I found Gens, but here's the thing; in Thunar, if I go to a ROM and press the right mouse button to pull up options on what to do with that file, I get dgen twice because one time I ran it just as dgen and another as dgen -f -otherstuff... So I'm just trying to make it so those two options will go away and, if I can, have them open Gens by default.

Running Xubuntu Hardy with stable package. Thanks in advance!

No problem. :)

Open Thunar, right-click the rom, choose "Properties", and in the middle you should see an "Open With" dropdown where you can choose the default application used to open the file.

Or did you want to know how to delete an item in the "Open With" right-click menu? If so, right-click the file, choose "Open With Other Application...", then right-click the item and select "Remove Launcher". This is covered in more detail in the [Thunar FAQ](http://thunar.xfce.org/documentation/C/working-with-files-and-folders.html).

If that doesn't work (thunar is sometimes fidgety with this), you can do it manually, by checking the mime-type (by hovering the mouse over the "Kind" item in the properties dialog), then editing ~/.local/share/applications/defaults.list. You should see an entry for the mime-type that looks something like (e.g., for JPEG files):

```
image/jpeg=eog.desktop;ristretto.desktop
```


You can delete the whole line for that mime-type, or just the application you don't want. The first application listed is the default. So if I wanted to remove eog from the "Open With" list, I'd change the above line to:

```
image/jpeg=ristretto.desktop
```


Or, if I wanted to use ristretto as the default, but keep eog in the list, I'd do:

```
image/jpeg=ristretto.desktop;eog.desktop
```


Also, if you remove "*-usercreated.desktop" from any lines in ~/.local/share/applications/defaults.list (like your custom dgen commands for example), you can also remove the actual desktop file as well. E.g.:

```
rm ~/.local/share/applications/blah-usercreated.desktop
```


HTH! :)

---

### Post by Firestone on 2008-05-17
> **Firestone said:**
> I seem to have trouble using the gamestates. It worked back in Feisty and long before that in Windows, but ever since Gutsy it stopped working. I dunno if it's Gens fault or my Ubuntu install, because I did a clean install for both Gutsy n Hardy including the newest Gens(stable) I could find.
I can switch slots, but QuickLoad/Save+hotkeys don't work or give an on screen message. I can semi-load a state with 'File - load state', and althought the filename is listed in the load history afterwards, it doesn't really load anything. 

Anyone got an idea?

To answer myself... I managed to discover that the savestate dir was changed to './filename.gsx', where filename was the savestate of my game, and was listed as many times after each other as I loaded the savestate. I never changed it though, and after I fixed it this morning it was back at './filename.gsx' after a shakedown cruise. Both times it was the same name, and although I haven't been able to reproduce it, I think it is related to the '&' character in the gamename since that is the only difference with the other games I tried. 
I'll try to backtrace my steps next time it happiness to see if it's a bug, but until then I'm happy I can save again.

---

### Post by OLIAX on 2008-05-18
> **leech said:**
> You have to use --force-architecture.  Like this ```
sudo dpkg -i --force-architecture gens_2.12b_i386.deb
```


I just tried that and I got cannot access archive: no such file or directory

```
oliax@BLACKKKNIGHT:~$ sudo dpkg -i --force-architecture gens_2.12b_i386.deb
dpkg: error processing gens_2.12b_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gens_2.12b_i386.deb

```

I have it saved on my desktop so any help much appreciated

---

### Post by acoustibop on 2008-05-18
Are you sure 'gens_2.12b_i386.deb' is the correct name for the package you have, OLIAX?  Might sound silly, but... ;)

**Edit:** if your file is saved to your desktop, you need to do 'cd Desktop' first - looks like you haven't done this.  Had you been in your Desktop folder, the line would have read like this: ```
oliax@BLACKKKNIGHT:~/Desktop$ sudo dpkg -i --force-architecture gens_2.12b_i386.deb
```

---

### Post by disturbedite on 2008-05-18
> **acoustibop said:**
> Are you sure 'gens_2.12b_i386.deb' is the correct name for the package you have, OLIAX?  Might sound silly, but... ;)

**Edit:** if your file is saved to your desktop, you need to do 'cd Desktop' first - looks like you haven't done this.  Had you been in your Desktop folder, the line would have read like this: ```
oliax@BLACKKKNIGHT:~/Desktop$ sudo dpkg -i --force-architecture gens_2.12b_i386.deb
```
that, or type the full path:
```
sudo dpkg -i --force-architecture ~/Desktop/gens_2.12b_i386.deb
```

---

### Post by megamaced on 2008-05-19
> **MonkeeSage said:**
> OK, I traced the problem back to Clear_Screen() in src/gens/sdllayer/g_sdldraw.c (specifically a memset in the if(Opengl) clause; see patch). I'm not sure what the problem is (maybe that the drawing surface is not 640*480 any more, since it is contained within the emulator window? Just a guess...). I just used the commented memset, and it seems to work.

As I said previously, I know virtually nothing about OpenGL programming, so maybe this will explode and spew brain-eating slugs into your ear canal--I'm not responsible for anything bad that happens if you use this patch. Patch is public domain.

Thank you for your patch, MonkeeSage. I will test it later tonight and if successful I will re-package Gens CVS to include it.

FYI: I am using an nVidia Geforce 8400 GS. Looks like the segfault affects users of all types of graphics card

---

### Post by GSZX1337 on 2008-05-19
> **megamaced said:**
> **[SIZE="4"]Compile Gens for 64-BIT users (Please test!)[/SIZE]**

Below are instuctions for compiling my Gens source package against an x64 system. Now I don't have a 64-BIT installation, so I am assuming the compiling process is no different from x86 systems.

Anyhow, please test and see if you can produce a Gens 64-BIT package from these instructions. If you suceed, please post the package in this thread. Thank you!

Firstly, you must install the tools needed to compile source and built Debian packages:

```
sudo aptitude install build-essential fakeroot dh-make
```

Now you must install the build dependencies for the Gens compile

```
sudo aptitude install debhelper autotools-dev gcc-3.4 nasm libgtk2.0-dev libsdl1.2-dev
```

Download the gens_2.12a_src.zip package from [here]("http://www.zshare.net/download/gens_2-12a_src-zip.html") and extract it. Then extract the gens_2.12a.tar.gz archive. You should now have a new gens-2.12a folder. Enter the new folder:

```
cd ~/gens-2.12a
```

Then run:

```
fakeroot debian/rules clean
```

Then build the package with:

```
fakeroot debian/rules binary
```

Finally, run:

```
debuild -us -uc
```

That should be all you need. The new package will be waiting for you in the Gens folder. If not, it will be in your home folder.

Did anyone try this?

---

### Post by megamaced on 2008-05-19
I have patched Gens CVS and uploaded a package for Hardy Heron (others versions to follow soon)

## gens-patched20080519 changes
- Fixed segfault on startup. (by MonkeeSage)
- Set OpenGL mode default to off, since it's crashprone if you don't have
the proper bpp selected (and sometimes even if you do). (by garron)
- The Pause button on the keyboard pauses emulation. Same as Escape, but
Escape also quits the game when gens is started with --quickexit.Ideally
these should all be remappable, but that has to wait for another day.(by garron)
- Add a listing for --quickexit to gens --help. (by garron)

Get it here
[http://www.zshare.net/download/1227521502fbf4d1/](http://www.zshare.net/download/1227521502fbf4d1/)

---

### Post by ilGuido on 2008-05-22
I made my own version of Gens (mentioned in post #302) to add support for real CDs to Gens and someone recently suggested me to sync it with the official(cvs) version. Well, it's based on gens-rc3.5-opengl with some code from gens 2.14, so I guess it's a bit different from the current cvs version (though I have not tried it yet).

For the curious ones: sourcecode can be found on [http://wido.freehostia.com/sgeng/]("http://wido.freehostia.com/sgeng/")

Sorry if my english is not that good...#-o

---

### Post by megamaced on 2008-05-22
> **ilGuido said:**
> I made my own version of Gens (mentioned in post #302) to add support for real CDs to Gens and someone recently suggested me to sync it with the official(cvs) version. Well, it's based on gens-rc3.5-opengl with some code from gens 2.14, so I guess it's a bit different from the current cvs version (though I have not tried it yet).

For the curious ones: sourcecode can be found on [http://wido.freehostia.com/sgeng/]("http://wido.freehostia.com/sgeng/")

Sorry if my english is not that good...#-o

Gens 2.14 is actually the Gens 2.12 build without openGL. Nobody uses that version of Gens anymore. The 2.12b package on this thread is based on Wah Wah Wah's gens-rc3.5-opengl build, with some other patches. The current version of Gens is 2.13 CVS. A lot has changed since Gens 2.12, including the integration of the ROM and menu windows. It would be great if you could supply a patch for CD-ROM support for the latest CVS build.

We are crying out for good programmers here! :)

---

### Post by ilGuido on 2008-05-22
> We are crying out for good programmers here!
not sure of being a good programmer:p

> Gens 2.14 is actually the Gens 2.12 build without openGL.
Gens for Windows 2.14(souvenir) has support for segacd save state and some minor stuff that's not present in the 2.12 branch.:)

> It would be great if you could supply a patch for CD-ROM support for the latest CVS build.
I'll post some code as soon as I gather all the changes that I made to the CD interface.;)

---

### Post by disturbedite on 2008-05-22
> **megamaced said:**
> ...The current version of Gens is 2.13 CVS. A lot has changed since Gens 2.12, including the integration of the ROM and menu windows. It would be great if you could supply a patch for CD-ROM support for the latest CVS build.
exactly.

> **ilGuido said:**
> Gens for Windows 2.14(souvenir) has support for segacd save state and some minor stuff that's not present in the 2.12 branch.:)
how/why does the 2.12 branch has features that the 2.14 branch does not?

---

### Post by megamaced on 2008-05-22
There is no such thing as an 2.14 branch for Linux. The Windows sourceball for 2.14 claims to contain both Windows and Linux versions, but the Linux version bundled is actually 2.12 without openGL

To be honest, I think the CVS version should bump to 2.15 to end confusion

---

### Post by disturbedite on 2008-05-23
> **megamaced said:**
> There is no such thing as an 2.14 branch for Linux. The Windows sourceball for 2.14 claims to contain both Windows and Linux versions, but the Linux version bundled is actually 2.12 without openGL

To be honest, I think the CVS version should bump to 2.15 to end confusion
thanks for clearing that up.

i think bumping the version to 2.15 is a good idea too, for the same reason you stated.

---

### Post by ilGuido on 2008-05-24
> **disturbedite said:**
> how/why does the 2.12 branch has features that the 2.14 branch does not?

Because the linux versions are developed from the last official linux version: 2.12. So version after version new features were added to 2.12/2.13. However version 2.14(for Windows) has some features that nobody cared to import into the linux version.

e.g. function *Env_Substain_Next* from the file ym2612.c :

>  in gens for linux 2.12a/b rc3 rc3.5 2.13 etc etc:

  901 void
  902 Env_Substain_Next (slot_ * SL)
  903 {
  904   if (SL->SEG & 8 )		// SSG envelope type
  905     {
  906       if (SL->SEG & 1)
  907 	{
  908 	  SL->Ecnt = ENV_END;
  909 	  SL->Einc = 0;
  910 	  SL->Ecmp = ENV_END + 1;
  911 	}
  912       else
  

> gens 2.14 for windows, gens32 all versions and my gens:

void
Env_Substain_Next (slot_ * SL)
{
  if(YM2612_Enable_SSGEG)
  {
    if (SL->SEG & 8 )		// SSG envelope type
      {
        if (SL->SEG & 1)
	  {
	    SL->Ecnt = ENV_END;
	    SL->Einc = 0;
	    SL->Ecmp = ENV_END + 1;
	  }
        else


Sorry for the long post, but I hope to have better explained this point.:-D

---

### Post by MonkeeSage on 2008-05-26
> **ilGuido said:**
> . . .
Sorry for the long post, but I hope to have better explained this point.:-D

No problem. :)

What does this mean for the average person? Are these just bug fixes, or do they alter basic functionality? You said something about better CD emulation I think? I'm just curious what the differences are from a user perspective.

---

### Post by ilGuido on 2008-05-26
@MonkeeSage
> **Gens 2.14 (souvenir) - 21 May, 2006** (announcement from gens.consolemul.com)
No, you're not dreaming, a new version of Gens is out.
But to be honest don't expect many changes from the last (and old) version. See it as a bugfix version.
Gens 2.12b accidently added "fake" support of sega CD save state. I just forgot to desactivate support (which was very partially implemented) before releasing the version.
With Gens 2.14 (you can get it in the download section), we now have much better support of Sega CD save state (thanks to Upthorn, he did the job here), but it's still not really safe to use it as i doesn't work every time.
SGG ENV support was desactived from the YM2612 since it brings severals bugs in the core unfortunatly.
Some others minors stuff were modified, consult the history file to know more about them.
This version is provided by DarkDancer (Thanks ;))[...]


These are mainly bugfixes. However the problem of SSG is interesting, because the SSG envelope is disabled by default in Gens 2.14 and in all versions of Gens32, while it is always enabled in older versions of Gens. Moreover it seems that the chip YM2612 has the SSG function disabled in the MAME emulator (cf. *fm.c* from the MAME source code). This [document]("http://www.smspower.org/maxim/docs/ym2612/")(smspower.org) is a bit ambiguous, but it seems to state that the SSG is desactivated.

---

### Post by disturbedite on 2008-05-26
maybe someone should just write a new G/MD emulator for linux based on the mame/mess G/MD implementations.

---

### Post by FranMichaels on 2008-05-28
Oh it does work. 

:guitar:

Great job patching and packaging... Hopefully Ubuntu will add the package to repos in the next release...

---

### Post by disturbedite on 2008-05-30
> **FranMichaels said:**
> Oh it does work. 

:guitar:

Great job patching and packaging... Hopefully Ubuntu will add the package to repos in the next release...
bug was reported over a year ago:
[https://bugs.launchpad.net/ubuntu/+bug/107927](https://bugs.launchpad.net/ubuntu/+bug/107927)

---

### Post by Itzi on 2008-05-30
Installed it last night wish i had more time to play around with it.  But that what weekends are for =).  Thank you very much love it.  O and btw Earthworm Jim Ftw

-Itzi

---

### Post by SaxIndustries on 2008-05-30
I have a feature request!

Would it be possible to make it so the user can optionally map a joypad key to quit the emulator?  It would be very handy for those of us looking to integrate this into our MythTV systems (I use a gamepad exclusively, no remote), being able to quickly exit an emu with a simple button press would be fantastic.

Thanks!

---

### Post by denham2010 on 2008-05-30
>  Re: Gens for Linux ubuntu package
I have patched Gens CVS and uploaded a package for Hardy Heron (others versions to follow soon)

## gens-patched20080519 changes
- Fixed segfault on startup. (by MonkeeSage)
- Set OpenGL mode default to off, since it's crashprone if you don't have
the proper bpp selected (and sometimes even if you do). (by garron)
- The Pause button on the keyboard pauses emulation. Same as Escape, but
Escape also quits the game when gens is started with --quickexit.Ideally
these should all be remappable, but that has to wait for another day.(by garron)
- Add a listing for --quickexit to gens --help. (by garron)

Get it here
[http://www.zshare.net/download/1227521502fbf4d1/](http://www.zshare.net/download/1227521502fbf4d1/)

Unfortunately I can not get gens to run. The window opens up on the screen and then the whole program just locks up and requires me to force quit. Running in the terminal generates no errors.

I can only think something strange may have happened to my Xubuntu install, as exactly the same thing happens with dgen (that just opens a black window and completely locks up - no errors or messages in the terminal either).

I can only assume it has something to do with an update received over the last few weeks, as I am certain both dgen and gens worked with my Hardy install previously.

If anyone can shed some light on this, or maybe offer suggestions as to how I can figure out what is going on, it would be appreciated!

Thanks.

---

### Post by hessiess on 2008-05-31
is there a 64 bit version of this?

---

### Post by wah_wah_69 on 2008-05-31
> **disturbedite said:**
> maybe someone should just write a new G/MD emulator for linux based on the mame/mess G/MD implementations.

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

I wish I had time for gens, maybe by the end of june when I finish my exams.

---

### Post by disturbedite on 2008-05-31
> **wah_wah_69 said:**
> [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

I wish I had time for gens, maybe by the end of june when I finish my exams.
what about r belmont?  i know him from the emuversal board, what does he have to do with this discussion?

---

### Post by mthei on 2008-05-31
It's funny, I've only recently considered enabling OpenGL after using these builds since 2006 when I began using Ubuntu, which immediately took care of the high CPU usage in Gens.
Anyway, I'd like to comment on how well the RPMs for 2.12 work on Fedora 8, as I didn't see it mentioned, and that with Fedora 9, enabling OpenGL really starts to slow everything down. However, with just the default graphic engine, it was nice to have a working version of this in Fedora, and would recommend any Fedora users who visit these forums to use this version instead of the one provided by Dribble, which is no longer maintained and buggy.

Edit: and also how well the recent patched version runs on Hardy, which I had recently switched back to. Thank you for continuing to update this package for so long.

---

### Post by wah_wah_69 on 2008-05-31
> **disturbedite said:**
> what about r belmont?  i know him from the emuversal board, what does he have to do with this discussion?

Scroll down a little bit until you see:

SDLHazeMD
The latest version is 0.12a.

That's a megadrive emulator that uses the mame core.

---

### Post by disturbedite on 2008-06-01
> **wah_wah_69 said:**
> Scroll down a little bit until you see:

SDLHazeMD
The latest version is 0.12a.

That's a megadrive emulator that uses the mame core.
ohhhhhhh, ok.  i didn't know that.  i will definitely check that out.  thanks!

---

### Post by GSZX1337 on 2008-06-01
> **GSZX1337 said:**
> Did anyone try this?

I tried it recently, it didn't work. Is there any way to have Gens on 64-bit versions of Ubuntu besides forcing the architecture?

---

### Post by disturbedite on 2008-06-02
> **GSZX1337 said:**
> I tried it recently, it didn't work. Is there any way to have Gens on 64-bit versions of Ubuntu besides forcing the architecture?
you could compile the source yourself.  but i don't think the gens source accommodates 64bit though, otherwise, there would prolly be 64bit packages posted in this thread already.

---

### Post by GSZX1337 on 2008-06-02
> **disturbedite said:**
> you could compile the source yourself.  but i don't think the gens source accommodates 64bit though, otherwise, there would prolly be 64bit packages posted in this thread already.
I tried this:
> **megamaced said:**
> **[SIZE="4"]Compile Gens for 64-BIT users (Please test!)[/SIZE]**

Below are instuctions for compiling my Gens source package against an x64 system. Now I don't have a 64-BIT installation, so I am assuming the compiling process is no different from x86 systems.

Anyhow, please test and see if you can produce a Gens 64-BIT package from these instructions. If you suceed, please post the package in this thread. Thank you!

Firstly, you must install the tools needed to compile source and built Debian packages:

```
sudo aptitude install build-essential fakeroot dh-make
```

Now you must install the build dependencies for the Gens compile

```
sudo aptitude install debhelper autotools-dev gcc-3.4 nasm libgtk2.0-dev libsdl1.2-dev
```

Download the gens_2.12a_src.zip package from [here]("http://www.zshare.net/download/gens_2-12a_src-zip.html") and extract it. Then extract the gens_2.12a.tar.gz archive. You should now have a new gens-2.12a folder. Enter the new folder:

```
cd ~/gens-2.12a
```

Then run:

```
fakeroot debian/rules clean
```

Then build the package with:

```
fakeroot debian/rules binary
```

Finally, run:

```
debuild -us -uc
```

That should be all you need. The new package will be waiting for you in the Gens folder. If not, it will be in your home folder. Didn't work. Any 64-bit Genesis emulators out there?

---

### Post by disturbedite on 2008-06-04
> **GSZX1337 said:**
> I tried this:
 Didn't work. Any 64-bit Genesis emulators out there?
if you had my discussion a little earlier on in thread you would have seen:
[SDLhazeMD]("http://rbelmont.mameworld.info/?p=159")
i don't know if it supports 64bit though...

---

### Post by slave-zeo on 2008-06-04
I didn't see if anyone asked this or not, BUT does Sega CD emulation work in the latest 32-bit release ? It seems to be ghosted in the file menu.

I am running 8.04 on a Dell xps 410, Nvidia 7900gs gfx card. Latest updates to hardy.

FIGURED IT OUT: i figured it out... go to FILE > OPEN ROM > and switch the rom type at the bottom of the windows to SEGACD IMAGE then you can load up your iso/mp3s. Sweet.

---

### Post by acoustibop on 2008-06-04
I think the default setting is "Sega CD/32X/Genesis roms," which should work with all ROM/image types the emulator plays, slave-zeo - so much so that, in several installations of several versions of this emulator, I've never changed it to anything else. ;)

**Edit:** in fact, on checking it out, GENS actually reverts to this setting every time I do File -> Open ROM...

---

### Post by slave-zeo on 2008-06-04
> **acoustibop said:**
> I think the default setting is "Sega CD/32X/Genesis roms," which should work with all ROM/image types the emulator plays, slave-zeo - so much so that, in several installations of several versions of this emulator, I've never changed it to anything else. ;)

**Edit:** in fact, on checking it out, GENS actually reverts to this setting every time I do File -> Open ROM...\

Yup, you are correct. Further inspection led me to find this out too. What about Real CDs though. any idea on that?

---

### Post by MonkeeSage on 2008-06-05
[Papa G]("http://www.google.com/search?q=sega%20cd%20copy%20protection") says Sega CD had no copy protection, and there is a "Boot CD" menu option (at least in the deb from this thread), so I would guess real CDs work.

---

### Post by slave-zeo on 2008-06-05
> **MonkeeSage said:**
> [Papa G]("http://www.google.com/search?q=sega%20cd%20copy%20protection") says Sega CD had no copy protection, and there is a "Boot CD" menu option (at least in the deb from this thread), so I would guess real CDs work.

the "Boot CD" is ghosted though, you cant select it. strange.

---

### Post by ilGuido on 2008-06-06
This patch should add real cd emulation to gens cvs. It assumes that your cd device is /dev/hdc. Please test it...:roll:

---

### Post by megamaced on 2008-06-06
> **ilGuido said:**
> This patch should add real cd emulation to gens cvs. It assumes that your cd device is /dev/hdc. Please test it...:roll:

Unfortunately that causes a problem for me as my two cd-rom devices are /dev/scd0 & dev/scd1 :) Even the CD-drive in my ancient laptop, running Xubuntu 8.04, is marked as /dev/scd0!

That being said, for those who do have an CD-ROM labelled as device /dev/hdc, I have made an debian package, built on Hardy, for testing. Please let ilGuido know if it works!

[http://www.zshare.net/download/1322277304b7d1c2/](http://www.zshare.net/download/1322277304b7d1c2/)

---

### Post by megamaced on 2008-06-06
> **denham2010 said:**
> Unfortunately I can not get gens to run. I can only think something strange may have happened to my Xubuntu install, as exactly the same thing happens with dgen 

What's strange is that in my Xubuntu 8.04 installation, I can't run Gens by clicking the icon in the games menu. Gens will appear for a brief second and then disappear. However if I type "gens" into the terminal, Gens works fine! Very strange

---

### Post by slave-zeo on 2008-06-06
Testing the new package now. And for what it's worth, my menu icon works fine for gens. As does starting it from the terminal.

btw, thanks a lot for making this emulator happen. i love me some genesis.

---

### Post by MonkeeSage on 2008-06-07
> **ilGuido said:**
> This patch should add real cd emulation to gens cvs. It assumes that your cd device is /dev/hdc. Please test it...:roll:

Wow! I had just assumed that the menu entry was disabled because I had no CD in the drive. Oops. I'll try this out tomorrow and let you know how it goes. Thanks for your work! :)

Ps. It might be worth-while to check what "cdrecord -scanbus" does, so you can set CDROM_DEV to the first cdrom drive, dynamically, instead of relying on "/dev/hdc" as the first device. I'm sure you can use the HAL interface to do it, but cdrecord already implements whatever is needed, so it might be the easiest way. Just a thought.

---

### Post by acoustibop on 2008-06-07
> **megamaced said:**
> ... That being said, for those who do have an CD-ROM labelled as device /dev/hdc... 

Easy enough to put a symlink to your CD device in /dev and call it hdc. ;)

---

### Post by megamaced on 2008-06-07
The new package is now on the front page. I've also created an Dapper Drake package and an RPM package (although I am not sure if there is demand for one?)

And a question for all the hackers out there, where in the Gens source code can I change the Gens version number in the Help > About menu? I want to bump the next version of Gens to 2.15, to avoid confusion with other Gens packages not using the latest CVS.

---

### Post by ilGuido on 2008-06-07
> **megamaced said:**
> And a question for all the hackers out there, where in the Gens source code can I change the Gens version number in the Help > About menu? I want to bump the next version of Gens to 2.15, to avoid confusion with other Gens packages not using the latest CVS.

Look in the file src/gens/gtkui/glade/interface.c

BTW, I'm going to post a patch which adds a dialog for choosing the path of the cdrom device.

---

### Post by DancemasterGlenn on 2008-06-07
Thanks for doing some work on gens, ilguido! We all really appreciate your work.

Also, I agree that the version bump will help alleviate confusion, so good luck with that.

---

### Post by MonkeeSage on 2008-06-07
What is the difference between the source packages on your site:

gens-2.14-rc1.tar.gz
gens-rc3.5.Mk6.tar.gz 

?

---

### Post by docPhunk on 2008-06-10
im having trouble setting up my controller in gens, seems when i set the keys it sets the button when i press and when i release(i.e. push up for up and down gets assigned up too) i tried setting it to the analog stick but its super sensitive and fires through the key as soon as i touch the stick. is there a way to set the key in the config file or something? is anyone else having this problem?

---

### Post by disturbedite on 2008-06-10
> **megamaced said:**
> The new package is now on the front page. I've also created an Dapper Drake package and an RPM package (although I am not sure if there is demand for one?).
i am on opensuse 11 now, so an rpm package is certainly appreciated! please don't stop packaging rpms of gens!

just a suggestion though, the rpm package prolly shouldn't have "dapper" in it's title.

---

### Post by megamaced on 2008-06-10
Wah Wah Wah, Wryun, ilGuido & MonkeeSage have all been great, contributing patches and keeping Gens alive. But what features or bugs do we want fixed in Gens looking to the future? We can certainly look forward to ilGuido's CD-ROM drive chooser dialog box for Sega CD. But I suppose for me, the ultimate feature would be Netplay support. There is an option for Netplay in the menu, but there isn't actually any code behind it. I am not a programmer, but maybe it would be possible to implement the netplay code of Snes9x or Zsnes? The netplay code in both emulators seems quite stable and would be a good addition to Gens.

---

### Post by MonkeeSage on 2008-06-10
> **megamaced said:**
> Wah Wah Wah, Wryun, ilGuido & MonkeeSage have all been great, contributing patches and keeping Gens alive. But what features or bugs do we want fixed in Gens looking to the future? We can certainly look forward to ilGuido's CD-ROM drive chooser dialog box for Sega CD. But I suppose for me, the ultimate feature would be Netplay support. There is an option for Netplay in the menu, but there isn't actually any code behind it. I am not a programmer, but maybe it would be possible to implement the netplay code of Snes9x or Zsnes? The netplay code in both emulators seems quite stable and would be a good addition to Gens.

I'd like to see a project page up for the fork (or have it re-merged with the official upstream). Then we could report bugs or contribute more easily. For example, I get Xlib errors sometimes about "Bad Drawable", and OpenGL doesn't work with the fglrx drivers on my radeon9550 (but did work on the open ati driver when I tried the "opengl-3.5" branch like a year ago, IIRC, though I think I was also on Gentoo at the time).

I haven't said anything because 1.) I know next to nothing about graphics programming, and only a little bit of xlib / xcb, so I didn't want to sound like I was crying about it instead of doing something to fix it; and 2.) I didn't want to undermine all the *awsome* work everyone has done in hacking and packing this version of gens for us!

Having a centralized project page / bug tracker would alleviate the second of those two concerns. (It would also get the word out for more developers  like ilGuido to contribute). My 2 pennies.

---

### Post by disturbedite on 2008-06-11
> **megamaced said:**
> Wah Wah Wah, Wryun, ilGuido & MonkeeSage have all been great, contributing patches and keeping Gens alive. But what features or bugs do we want fixed in Gens looking to the future? We can certainly look forward to ilGuido's CD-ROM drive chooser dialog box for Sega CD. But I suppose for me, the ultimate feature would be Netplay support. There is an option for Netplay in the menu, but there isn't actually any code behind it. I am not a programmer, but maybe it would be possible to implement the netplay code of Snes9x or Zsnes? The netplay code in both emulators seems quite stable and would be a good addition to Gens.
i would like to see all the audio options in gens32 implemented in this gens project (fork)?

i agree with MonkeeSage, i think a new page for it would be great. that way we could visit the site for software/news updates. it'd be a good way to follow progress.

---

### Post by slave-zeo on 2008-06-12
> **disturbedite said:**
> i would like to see all the audio options in gens32 implemented in this gens project (fork)?

i agree with MonkeeSage, i think a new page for it would be great. that way we could visit the site for software/news updates. it'd be a good way to follow progress.

If you want to set up a nice website for the Gens for linux project, I can donate some webspace and subdomain off my alphaboxmedia.net domain. It could be something like gens.alphaboxmedia.net.

just an offer.

---

### Post by megamaced on 2008-06-12
I suppose my preferred option would be to upload all the patches that make up Gens 2.15.1 to the official CVS repository. I don't see the point of forking Gens, especially considering there are already too many versions of it laying around the internet.
I don't know whether any of the Gens Sourceforge Admins are still alive, but I may contact them to see whether we can get write access to the repo.

So the above would provide us with a repository and a place where people can submit patches. Although it does not provide us with a dedicated Gens for Linux website. I have never put a website together and my design skills are shockingly awful, so I'll leave it you guys to come up with a solution!

---

### Post by disturbedite on 2008-06-12
> **slave-zeo said:**
> If you want to set up a nice website for the Gens for linux project, I can donate some webspace and subdomain off my alphaboxmedia.net domain. It could be something like gens.alphaboxmedia.net.

just an offer.
that is a very generous offer, but as far as i'm concerned, i'm not experienced with web design & whatnot. i was just agreeing that it is a good idea imo. hopefully someone else will take up your offer though! :)

---

### Post by megamaced on 2008-06-16
Some news:

Soon I will be able to apply patches to the official Gens CVS tree, meaning that the packages in this thread will follow the official Gens development ie. no more forking.

More news to follow.

---

### Post by slave-zeo on 2008-06-16
Who's the main person around here for the gens on linux project?

---

### Post by disturbedite on 2008-06-16
> **megamaced said:**
> Some news:

Soon I will be able to apply patches to the official Gens CVS tree, meaning that the packages in this thread will follow the official Gens development ie. no more forking.

More news to follow.
its great news that you've been approved for cvs access!

@ slave-zeo
he just posted, its megamaced.

---

### Post by slave-zeo on 2008-06-16
> **disturbedite said:**
> 
@ slave-zeo
he just posted, its megamaced.

lol. I was just making sure. I hate directing something at the wrong person and looking like a dumb butt.

---

### Post by DancemasterGlenn on 2008-06-17
That's wonderful news, congrats! This is a definite step forward.

---

### Post by hardyjuejue on 2008-06-18
First of all, great work on gens CVS and the nice package, it really "revives" gens ! Yet, I have an ati X700 mobility and using fglrx (since the open drivers are still so-so for this model) and OpenGL doesn't work. I've seen a patch for ATI on the gens sourceforge page; is there any chance to see this patch added in the next coming packages ?
Besides, I've noticed that there are strange noises (clicks) when using a SegaCD iso/mp3 (doesn't do it when using a real CD, though), this strange bug has been going on since the very first releases of gens for linux (and I'm pretty sure it's not hardware related, since I've tried it on several different machines and distros), but somehow noone ever talks about it... so, I was wondering if this was a well known issue ?
And last, but not least, there is still this strange bug resulting in options being selected or unselected randomly (notably, SegaCD perfect sync.) when switching to full screen or simply opeing a new file.
Strangely enough, I haven't seen much posts about these bugs, and yet I believe they are annoying enough to be noticed...

---

### Post by ilGuido on 2008-06-18
> **hardyjuejue said:**
> And last, but not least, there is still this strange bug resulting in options being selected or unselected randomly (notably, SegaCD perfect sync.) when switching to full screen or simply opeing a new file.

It's a bug of gens cvs. This problem is due to some missing resyncs between the graphical interface and the values of variables.

[QUOTE=MonkeeSage]What is the difference between the source packages on your site:

gens-2.14-rc1.tar.gz
gens-rc3.5.Mk6.tar.gz ?[/QUOTE]

2.14-rc1 has a modified gui (still in development).

[QUOTE=megamaced]But I suppose for me, the ultimate feature would be Netplay support. There is an option for Netplay in the menu, but there isn't actually any code behind it. I am not a programmer, but maybe it would be possible to implement the netplay code of Snes9x or Zsnes?[/QUOTE]

The windows version of gens uses a Kaillera client. Kaillera clients are windows only and unluckily enough are closed-source and proprietary.

This patch adds the cd-drive chooser dialog:

---

### Post by megamaced on 2008-06-18
Thank you ilGuido for your patch. I will test it out later and release Gens 2.15.2.

The menu options bug is certainly annoying and should be a priority fix. What Gens needs is some good PR to attract more developers! Hopefully the upcoming website will give Gens for Linux more of a face (thanks slave-zeo).

So expect in the coming days to see CVS up to date, and the website too. Finding time is a bit difficult right now so things are moving slower then I'd like.

---

### Post by megamaced on 2008-06-18
> **ilGuido said:**
> This patch adds the cd-drive chooser dialog:

I have applied your patch to my local CVS build (your previous CD-ROM patch has not been applied - do I need to apply that first?) and there was a failure!

```
patch -p0 < gens-cd_ui2.diff
patching file Gens-MultiPlatform/linux/src/gens/emulator/g_main.c
Hunk #1 succeeded at 767 (offset 13 lines).
patching file Gens-MultiPlatform/linux/src/gens/gtkui/glade/callbacks.c
patching file Gens-MultiPlatform/linux/src/gens/gtkui/glade/callbacks.h
patching file Gens-MultiPlatform/linux/src/gens/gtkui/glade/interface.c
patching file Gens-MultiPlatform/linux/src/gens/gtkui/glade/interface.h
patching file Gens-MultiPlatform/linux/src/gens/gtkui/support.c
patching file Gens-MultiPlatform/linux/src/gens/gtkui/support.h
patching file Gens-MultiPlatform/linux/src/gens/Makefile.in
patching file Gens-MultiPlatform/linux/src/gens/sdllayer/g_sdldraw.c
patching file Gens-MultiPlatform/linux/src/gens/segacd/cd_aspi.c
Hunk #1 FAILED at 18.
1 out of 1 hunk FAILED -- saving rejects to file Gens-MultiPlatform/linux/src/gens/segacd/cd_aspi.c.rej
patching file Gens-MultiPlatform/linux/src/gens/segacd/cd_aspi.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #1 succeeded at 527 with fuzz 2 (offset 450 lines).
patching file Gens-MultiPlatform/linux/src/gens/util/file/rom.c
patching file Gens-MultiPlatform/linux/src/gens/util/file/rom.h
patching file Gens-MultiPlatform/linux/src/gens/util/file/save.c
patching file src/Makefile.in
patching file src/starscream/main68k/Makefile.in
patching file src/starscream/Makefile.in
patching file src/starscream/sub68k/Makefile.in

```

You may want to check out the current live CVS tree at:
```

cvs -z3 -d:pserver:anonymous@gens.cvs.sourceforge.net:/cvsroot/gens co -P Gens-MultiPlatform/linux
```

---

### Post by ilGuido on 2008-06-19
I forget to say it isn't a cumulative patch. You need to apply the old one first.

---

### Post by disturbedite on 2008-06-19
@ megamaced
you asked before if anyone had any feature requests. i mentioned that i'd like to see the sound options in gens32 implemented in gens. have you considered that at all?
i'm not asking this cuz i think they should be implemented simply cuz i want them to be, i'm just curious if you've thought about it.

---

### Post by megamaced on 2008-06-19
> **ilGuido said:**
> I forget to say it isn't a cumulative patch. You need to apply the old one first.

I applied the first patch, then the second patch successfully. But when I click "boot cd", nothing happens!

Below you will find a download link to my build environment so you can see for yourself. Its straight from CVS, with your two patches applied.

[http://www.zshare.net/download/13879816a46ccca7/](http://www.zshare.net/download/13879816a46ccca7/)

---

### Post by ilGuido on 2008-06-19
Delete your old gens.cfg. Launch gens and configure it (bios, dirs, cdrom device). Quit gens and then launch gens again. If, after this procedure, "boot cd" doesn't work, the problem is either a raw read/write permission for the device or a problem with SCSI CD devices. Or both.
However since gens has problems with saving/loading the configuration file, I think the matter is with the gens.cfg file.

---

### Post by nerdy_girlscout on 2008-06-19
Oh, oh, feature requests?! :D Well, I would like the GUI to work just as well as it does in the Windows version. The recent improvements have made it much better than before, but I still see some oddities, and most importantly, options are still a little inconsistent. Right now Vsync is disabled in the menu, but it is enabled in the emulator settings. If I click enable, it will get disabled. Maybe this is just considered bugfixes rather than adding features, but still.

This might be too much for you though, but if it's feasible:

Ditch SDL for video and audio, and use portaudio or just simply OSS for audio, and use Xv and OpenGL for video, please. :D

When being in fullscreen, I would also like to have just a menu bar (like in gambatte, or VisualBoyAdvance for Windows.), wich you can make appear/disappear with a press of a button.

---

### Post by megamaced on 2008-06-19
> **ilGuido said:**
> Delete your old gens.cfg. Launch gens and configure it (bios, dirs, cdrom device). Quit gens and then launch gens again. If, after this procedure, "boot cd" doesn't work, the problem is either a raw read/write permission for the device or a problem with SCSI CD devices. Or both.
However since gens has problems with saving/loading the configuration file, I think the matter is with the gens.cfg file.

Doh! I didn't notice the "Current CD Drive" option under "Options"! For some reason I assumed that when I clicked "Boot CD", a pop up box would come up asking me which CD drive to use! :) Cool good work man!

---

### Post by megamaced on 2008-06-19
Gens 2.15.2 released!

The Gens available here is no longer a fork. Thats the big news for this release. I have merged all the patches that are used in Gens 2.15.2 upstream to CVS.

Big thanks to ilGuido for adding an option to choose your CD-ROM drive (Options > Current CD Drive). Thats the big feature for this release.

If anyone wants to submit a patch, you can use the Gens sourceforge page at [http://sourceforge.net/projects/gens/](http://sourceforge.net/projects/gens/)

As always, keep hacking!

---

### Post by FranMichaels on 2008-06-19
Ah I'm so pleased. :KS Love it when an emulator gets "updated/resurrected" same goes for projects like pcsx-df.

So requests... How about you guys/gals put your names in the About box, under credits. You deserve it!

A built in cheat system ala zsnes or mednafen would be nice. One that lets you search memory for value changes, then replace it with your own values, that type of thing ;) 

My other request, not really about gens itself, but the official website should get a tiny update and show off this Linux download.

Anyone in touch with the maintainer? The fact the home page says it's optimized for IE6 and 16-bit color depth worries me somehow. 
I'm used to the nostalgia and fact that many of the games I play emulated are well over 20 years old, but that little notice on a website freaks me out. :lolflag:

Again, Great job!

---

### Post by Zeotronic on 2008-06-20
Ok, I admit I'm not sure if this is the place for it, but I have a few suggestions/requests... also, the 2.12b and 2.15 thing is weirding me out... which one am I supposed to use? They both look to be pretty well the same expect the one comes in two windows, while the other comes in one. I'm going to opt for the single windowed one, I don't know about you...

First off, when running without a ROM, it hogs all of my processing power... there is no reason for this... I think its bad enough when you get programs that do that to dynamically get every possible frame they can out of your system, but this isn't getting anything out of it! So if that could be fixed without too much hassle...

Secondly, and I'm going to cite experience with VBA under Windows for this one (haven't played with it much since my switch a year ago), but OpenGL mode in anything beyond 320x240 is kind of blurry... I suppose I don't know how Gens uses OpenGL, but in VBA I could have it set to be sharp, and I rather liked that. In some of the games you'd see the pixels in the sprite rotating in their square formations, where-as in a normal resolution you'd just see this jumble of pixels trying to navigate in a way that looks like a rotation. So if its at all possible to give us the option of sharp rendering in OpenGL mode? As I've stated, I don't understand the rendering systems of the emulator (or any systems of any emulator)... I may just be overlooking something.

Finally, if there could be an option to render text menus, or icon menus (as well as the current text & icon menus) that would be great... Personally I would like to just have text menus, but that should be an option up to the user, I think. Of course this is very minor in comparison to the first thing I stated which I think despritely needs fixed.

---

### Post by mister_k81 on 2008-06-20
> **Zeotronic said:**
> 

First off, when running without a ROM, it hogs all of my processing power... there is no reason for this... I think its bad enough when you get programs that do that to dynamically get every possible frame they can out of your system, but this isn't getting anything out of it! So if that could be fixed without too much hassle...


I noticed that oddity too. But it also happens when you press the Esc key to pause. I dunno, but the Windows version has a "static-animation" effect at start up, that seems to be missing here. Could the high CPU usage be from the Linux build trying to render this missing effect? Just a thought. 

Also, another minor issue I have Is that there is some jerkiness when the screen scrolls in OpenGL mode. This isn't a major problem, but it is noticeable in faster scrolling games, like Sonic. Disabling OpenGL seems to fix the problem, though.   

But even with these issues, it's nice to see someone continue on with this project. :)

---

### Post by Zeotronic on 2008-06-20
> Also, another minor issue I have Is that there is some jerkiness when the screen scrolls in OpenGL mode. This isn't a major problem, but it is noticeable in faster scrolling games, like Sonic. Disabling OpenGL seems to fix the problem, though.
Have you tried using VSync? It sounds like you could use some VSync, but I could be wrong.

As for the massive CPU use, like I've said, I have no experience on the internals of an Emulator, but I suspect that no-one has applied a frame-cap to it drawing that blank screen... so it just piles out as many frames as it can... and since their all the same thing, its pretty pointless... but anyone in a position to fix it would know why, I suspect.

Finally, I've noticed that if I have it set to render in OpenGL when I close it, when I open it up again it crashes... so I have to go and delete the configuration files in order to open it up again. I haven't touched OpenGL in half a year, and was only an novice then, so I'm hard pressed to offer any useful ideas as to why... but obviously it would be somewhere in the declarations... it may be trying to declare OpenGL before SDL is sufficiently prepared or something.

---

### Post by disturbedite on 2008-06-20
yes, vsync is intended for tearing of this kind. there is a catch though, vsync almost always decreases performance.

---

### Post by wingnux on 2008-06-21
Gens 2.15.2 was released!

[http://sourceforge.net/project/showfiles.php?group_id=73619](http://sourceforge.net/project/showfiles.php?group_id=73619)

---

### Post by DrMelon on 2008-06-21
For some reason sound does not work for me; disabling and enabling the sound has no effect whatsoever. Sound works for almost everything else, it just seems to be Flash and Gens that have no sound.

I'm running Hardy 8.04, just so you know.

---

### Post by ilGuido on 2008-06-21
> **wingnux said:**
> Gens 2.15.2 was released!


I think that it should be marked as unstable or testing (because it has a lot of bugs).

---

### Post by mister_k81 on 2008-06-21
> **Zeotronic said:**
> Have you tried using VSync? It sounds like you could use some VSync, but I could be wrong.


I tried VSync and it does fix screen tearing, but it still didn't fix the issue that I'm having. I think I found the culprit though, when I turned on the frames per second counter, I noticed that I'm getting a really inconsistent framerate. It seems to jump between 57fps to 75fps in OpenGL mode, which causes the stuttery looking scrolling. In Software mode it's a lot more consistent and hovers around 60-62fps, even though I am using a lot more CPU power.

I also noticed that pressing Alt-Enter seems to toggle off and on the VSync when jumping in and out of fullscreen mode. 

The emulator is still playable enough, regardless. But I would like to see the high CPU usage bug fixed when there is no ROM in the emulator at the very least.

---

### Post by disturbedite on 2008-06-22
@ mister_k81
if you go back and read my comments (made recently) about vsync you will see that i mentioned that vsync can fix tearing, but usually at a performance cost.
also, about vsync in windowed & fullscreen mode, that is a known bug.

---

### Post by MonkeeSage on 2008-06-22
> **ilGuido said:**
> However since gens has problems with saving/loading the configuration file, I think the matter is with the gens.cfg file.

I've noticed that gens seems to write the config file on exit, rather than after each configuration change (which is normally fine), and this causes a problem when it segfauls or has an Xlib error or whatever, because the config never gets written (also causes a problem with save states being committed sometimes?). I usually save the config manually after every change just to be sure.

---

### Post by MonkeeSage on 2008-06-22
> **nerdy_girlscout said:**
> Ditch SDL for video and audio, and use portaudio or just simply OSS for audio, and use Xv and OpenGL for video, please. :D

Since the SDL audio driver can use OSS (or Pulse or Alsa, or DSound or whatever), audio output seems like a moot point. And OpenGL support is implemented through SDL's OpenGL extension, so there seems to be no reason to try and export it to overlay or directly using OpenGL, imho--I don't think it would give any benefit, and it would exclude people who can only use SDL (but I'm not a graphics developer, so maybe I'm wrong).

---

### Post by nerdy_girlscout on 2008-06-23
I hope that the bad sound gets fixed in a better way then, and the display stops tearing, and that the display is fully integrated in the GUI. (It seems to get by with some kind of hack now, but if you mess with it a little you'll get some bad effects. Try maximizing the window for example.)

I don't think there's anyone who can only use SDL. If you're using a driver without 3d, you might need to use Xv instead of OpenGL, but I don't think there's anyone stuck with just SDL.

---

### Post by MonkeeSage on 2008-06-23
> **nerdy_girlscout said:**
> I hope that the bad sound gets fixed in a better way then. . .

You can (somewhat) fix this by adjusting the buffer size of your sound driver; larger buffer equals less popping and crackling.[1]

> **nerdy_girlscout said:**
> I don't think there's anyone who can only use SDL. If you're using a driver without 3d, you might need to use Xv instead of OpenGL, but I don't think there's anyone stuck with just SDL.

Suprisingly, there are such people. Myself included. If I use the proprietary ATI drivers for my card (fglrx), I can't use OpenGl (another user mentioned the same problem, so I'm not alone). Now granted, this is probably a bug in the OpenGl driver, but in any case some of us *do* need the SDL interface.

[1] "Level of latencies [depend on] buffer size." [http://4front-tech.com/hannublog/?p=5#comment-422](http://4front-tech.com/hannublog/?p=5#comment-422)

---

### Post by acoustibop on 2008-06-23
Myself as well; I find myself in the same boat as you over ATI, the fglrx driver and OpenGL/SDL, MonkeeSage! :(

But, it works.

---

### Post by megamaced on 2008-06-24
> **ilGuido said:**
> I think that it should be marked as unstable or testing (because it has a lot of bugs).

There hasn't been a Gens for Linux release on the sourceforge page for years. People who visited that page and did not know about this thread would have assumed that the project is well and truly dead.

I thought about releasing the 2.15.2 package as "alpha" or "beta" but then wondered is it really less stable then the 2.12 packages or anything else that has been released before? The answer is no, not really. Although some bugs can be described as annoying, I would not consider any of them to be critical, like the segfault crash that affected earlier releases.

I suppose I could compare this Gens release to the release of KDE 4.0. Everyone knew it was unstable and buggy as hell, but the KDE developers released it regardless because they knew more people would likely be using it, thus there would be more bug hunting and patches submitted. Given that the only *active* developers for Gens are youself, MonkeeSage and... well.. I think the more developers we can attract the better.

Moving off topic, some people have mentioned openGL support using the ATi driver. There is a patch for this on the Gens sourceforge site but it doesn't appear to patch the current Gens CVS source properly. Has anyone tried to apply this patch or modified this patch to work, or know of another solution / workaround?

The ATi patch can be found here: [http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344](http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344)

---

### Post by MonkeeSage on 2008-06-25
> **megamaced said:**
> Moving off topic, some people have mentioned openGL support using the ATi driver. There is a patch for this on the Gens sourceforge site but it doesn't appear to patch the current Gens CVS source properly. Has anyone tried to apply this patch or modified this patch to work, or know of another solution / workaround?

The ATi patch can be found here: [http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344](http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344)

I'll see about trying to apply it later tonight or tomorrow, but don't hold your breath (I'm not a graphics programmer).

Ps. I agree that gens for linux needs some good PR, and more real devs like ilGuido are needed.

---

### Post by nerdy_girlscout on 2008-06-25
> **MonkeeSage said:**
> You can (somewhat) fix this by adjusting the buffer size of your sound driver; larger buffer equals less popping and crackling.[1]



Suprisingly, there are such people. Myself included. If I use the proprietary ATI drivers for my card (fglrx), I can't use OpenGl (another user mentioned the same problem, so I'm not alone). Now granted, this is probably a bug in the OpenGl driver, but in any case some of us *do* need the SDL interface.

[1] "Level of latencies [depend on] buffer size." [http://4front-tech.com/hannublog/?p=5#comment-422](http://4front-tech.com/hannublog/?p=5#comment-422)

I am not talking about crackliness; the sound doesn't seem to scratch or lag. What I mean with bad sound is: The sound (atleast the music) seems to have a different tone than it should. Also, the volume seems to be all messed up; Some things are louder than they should, while some things have a lower volume than they should have. I just tested the Windows version though, and it seems the same, so the problem is probably with something else than SDL.

ATI cards seemed to have quite good support these days, I am surprised you cannot use anything but SDL. Maybe it's still needed then.

---

### Post by spyder0080 on 2008-06-25
Gens installed correctly, but when I run the program, it crashes and closes right after it opens. Any ideas of what would be wrong?

---

### Post by disturbedite on 2008-06-25
> **spyder0080 said:**
> Gens installed correctly, but when I run the program, it crashes and closes right after it opens. Any ideas of what would be wrong?
i'm not mad at you, but i've prolly said this a hundred times on this forum:
in situations like this, you need to try to launch the program from command line and post the output here.

---

### Post by acoustibop on 2008-06-25
And say which version you've installed...

---

### Post by spyder0080 on 2008-06-25
> **disturbedite said:**
> i'm not mad at you, but i've prolly said this a hundred times on this forum:
in situations like this, you need to try to launch the program from command line and post the output here.

sorry, I jumped to the end of the thread...
The version I am running is 2.15.2 (Hardy). When I run it from the command line, I get a segmentation fault.

---

### Post by megamaced on 2008-06-26
> **spyder0080 said:**
> sorry, I jumped to the end of the thread...
The version I am running is 2.15.2 (Hardy). When I run it from the command line, I get a segmentation fault.

Whoa! I thought we'd seen the last of those...

Looks like you will have to use Gens 2.12b instead.

---

### Post by spyder0080 on 2008-06-26
> **megamaced said:**
> Whoa! I thought we'd seen the last of those...

Looks like you will have to use Gens 2.12b instead.

Gens 2.12b runs perfectly! Thanks a lot!

---

### Post by rmx687 on 2008-06-28
Hey all, I'm running 7.04 Feisty Fawn on a Playstation 3.  I try compiling both the packages on the front page from source and on the "make" step I keep running into an error about the sega cd:

segacd/cd_aspi.c: In function &#8216;Wait_Read_Complete&#8217;:
segacd/cd_aspi.c:668: warning: unused variable &#8216;i&#8217;
make[3]: *** [segacd/gens-cd_aspi.o] Error 1
make[3]: Leaving directory `/home/mike/Desktop/gens-2.15.2/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/gens-2.15.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/gens-2.15.2'
make: *** [all] Error 2

I apologize if this has already been handled, I don't have time to sift through the 41 pages of this thread to see if it has.  Running Genesis games on my PS3 has been something I've been trying to do for a long time, so any help would be greatly appreciated.

---

### Post by MonkeeSage on 2008-06-28
> **rmx687 said:**
> Hey all, I'm running 7.04 Feisty Fawn on a Playstation 3.  I try compiling both the packages on the front page from source and on the "make" step I keep running into an error about the sega cd:

segacd/cd_aspi.c: In function ‘Wait_Read_Complete’:
segacd/cd_aspi.c:668: warning: unused variable ‘i’
make[3]: *** [segacd/gens-cd_aspi.o] Error 1
make[3]: Leaving directory `/home/mike/Desktop/gens-2.15.2/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mike/Desktop/gens-2.15.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mike/Desktop/gens-2.15.2'
make: *** [all] Error 2

I apologize if this has already been handled, I don't have time to sift through the 41 pages of this thread to see if it has.  Running Genesis games on my PS3 has been something I've been trying to do for a long time, so any help would be greatly appreciated.

Hmm, unless gcc is called with -Werror, the warning you list is not the cause of the error. There is probably something further up the screen that is the actual error.

---

### Post by MonkeeSage on 2008-06-28
> **MonkeeSage said:**
> I'll see about trying to apply it later tonight or tomorrow, but don't hold your breath (I'm not a graphics programmer).

Been busy with another project the past few days, but I'll definitely see if I can get the patch working this weekend. (But again, don't hold your breath.)

---

### Post by MonkeeSage on 2008-06-28
> **nerdy_girlscout said:**
> I am not talking about crackliness; the sound doesn't seem to scratch or lag. What I mean with bad sound is: The sound (atleast the music) seems to have a different tone than it should. Also, the volume seems to be all messed up; Some things are louder than they should, while some things have a lower volume than they should have. I just tested the Windows version though, and it seems the same, so the problem is probably with something else than SDL.

From the other board, I take it you are using oss4? Maybe try installing the libsdl1.2debian-oss package and see if that helps?

---

### Post by ilGuido on 2008-06-29
> **rmx687 said:**
> Hey all, I'm running 7.04 Feisty Fawn on a Playstation 3.  I try compiling both the packages on the front page from source and on the "make" step I keep running into an error about the sega cd:

I'm pretty sure that gens can't work on a ps3, because some parts of it are written in x86 assembly language. PS3 is based on the powerpc architecture.
On a ps3 should work: snes9x, mednafen, (sdl)mame and xe (which runs genesis games and much more, however it's closed source).

---

### Post by AamirM on 2008-07-04
Hi,

[Regen]("http://board.zsnes.com/phpBB2/viewtopic.php?t=11109"), another megadrive/genesis emulator ported to linux recently.

stay safe,

AamirM

---

### Post by nerdy_girlscout on 2008-07-04
> **MonkeeSage said:**
> From the other board, I take it you are using oss4? Maybe try installing the libsdl1.2debian-oss package and see if that helps?

Yes that's correct, OSS4. About libsdl1.2debian-oss, that's what I'm using.

Regen? It's closed source as far as I know. Technically quite impressive though.

---

### Post by DancemasterGlenn on 2008-07-04
He would know, he wrote it :P

Regen is impressive, but it will take some time for it to be on par with its windows counterpart. It's still gui-less, and joystick control is being worked on. Besides that, it's very feature rich, and Aamir works quite hard on it. Definitely keep an eye on the site he linked for more updates, and definitely give it a go if you can.

---

### Post by AamirM on 2008-07-06
Hi,

Does the author of this GTK port comes here? I want to ask a few question from him.

stay safe,

AamirM

---

### Post by disturbedite on 2008-07-06
> **AamirM said:**
> Hi,

Does the author of this GTK port comes here? I want to ask a few question from him.

stay safe,

AamirM
gens gui/frontend for linux has always been coded in gtk. gens isn't a port to gtk, simply a port to linux.

and yes the (current) maintainer/author does come here, he started this thread. he is megamaced.

---

### Post by megamaced on 2008-07-07
> **disturbedite said:**
> and yes the (current) maintainer/author does come here, he started this thread. he is megamaced.

I am only the guy who applies other people's patches and creates packages! The real developers are on the sourceforge page :)

---

### Post by denham2010 on 2008-07-07
Hi,

Recently I have been having problems with gens (dgen does exactly the same for extra info)

Previously both gens and dgen worked flawlessly for me.

Then I had an update (has been so many over the past few months I am unable to pinpoint exactly after which update I got the problem) and both gens and dgen stopped working. They would both get to the point of opening up the window and then just freezing (no errors in the terminal at all, just locked up and I actually had to kill the terminal to kill the gens/dgen process).

Then, I had a kernal update come through, and suddenly, both gens and dgen worked flawlessly again.......now, after yet more updates again (and I believe a kernel update or 2) both are back to freezing upon the window opening.

I have tried and tried to find out why it is happening, but just can't seem to make any headway.

Currently using Xubuntu 8.04 (with both kde and gnome installed as I use quite an extensive mix of all three desktops...hehehe) running kernel 2.6.24-19-generic.

Can anyone shed some light on what might be happening, or at least where I can start to find out? (I know this is a gens thread, not dgen, but just wanted to mention dgen as both are having exactly the same issue...)

As I have not been able to find anyone else with the same issue, I can only assume it must be something peculiar to my setup causing the problem....

Looking forward to any help!

Cheers.

[SOLVED]

Hi, thought I'd mention I have solved the issue I was having...and others may find it useful, along with the developers of Gens:

It appears Gens (and dgen) do not play nicely with pulseaudio. After certain updates, my pulseaudio daemon has been killed, and consquently, Gens would work again. After a reboot, with pulseaudio again running, Gens would lock up again.

As I use .desktop launchers for my Gens roms, I have just added the commands to kill pulseaudio and run the game, and when the game is exited, restarting the pulseaudio daemon.

---

### Post by disturbedite on 2008-07-07
> **megamaced said:**
> I am only the guy who applies other people's patches and creates packages! The real developers are on the sourceforge page :)
well, i know that, but i think he was referring specifically to this thread.

---

### Post by DancemasterGlenn on 2008-07-07
He was not. I'm assuming he'd like to pick the brain of whoever coded the GTK gui, since he's working on his own frontend. Who submitted the patch to put everything in Gens in one window, again? Was that you, megamaced? I can't even remember anymore...

---

### Post by MonkeeSage on 2008-07-08
> **DancemasterGlenn said:**
> He was not. I'm assuming he'd like to pick the brain of whoever coded the GTK gui, since he's working on his own frontend. Who submitted the patch to put everything in Gens in one window, again? Was that you, megamaced? I can't even remember anymore...

> **megamaced said:**
> Ubuntuforums member wryun is responsible for the new work being carried out...

^ From first page.

---

### Post by DancemasterGlenn on 2008-07-08
Yeah, wryun hasn't been around for a while now... you might try PMing him anyway, though.

---

### Post by clarkec321 on 2008-07-29
I'm lucky enough to have everything working fine on my laptop, but I can't get my ps3 joypad to work over usb (i don't have bluetooth)

Can anyone point me in the right direction

---

### Post by tjwoosta on 2008-07-29
>  	
I'm lucky enough to have everything working fine on my laptop, but I can't get my ps3 joypad to work over usb (i don't have bluetooth)

Can anyone point me in the right direction 


does it work with any other programs?

in ubuntu usually you can just plug in the joypad and it works without any  setup

---

### Post by clarkec321 on 2008-07-31
When i plug it in via the usb cable, the led charging lights flash
I've also gone to the System Log, and it does show as an event that the ps3 joypad has been plugged in

But nothing happens after that an wWhen i go to map the buttons in Gens, nothing happens

---

### Post by clarkec321 on 2008-07-31
When i plug it in via the usb cable, the led charging lights flash
I've also gone to the System Log, and it does show as an event that the ps3 joypad has been plugged in

But nothing happens after that and When i go to map the buttons in Gens, nothing happens

---

### Post by ddryden on 2008-08-06
The ps3 pad works even though the lights are flashing. On my system i have the following dmesg:
```

[  316.151768] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  316.477869] usb 2-1: configuration #1 chosen from 1 choice
[  316.698403] usbcore: registered new interface driver hiddev
[  316.786859] input: Sony PLAYSTATION(R)3 Controller as /devices/pci0000:00/0000:00:1d.1/usb2/2-1/2-1:1.0/input/input10
[  316.822619] input,hidraw0: USB HID v1.11 Joystick [Sony PLAYSTATION(R)3 Controller] on usb-0000:00:1d.1-1
[  316.822657] usbcore: registered new interface driver usbhid
[  316.822662] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver

```

For me it was then maped to /dev/input/js0 you can check its working by running:
```

jstest --event /dev/input/js0

```
If you dont use the --event option you'll get far too much information for one console line and its a pain to see whats going on.

The SIXAXIS stuff isnt registering but all the buttons are triggering events.

---

### Post by You Are Not Pro on 2008-08-11
I downloaded it and it worked for a Sega Genesis game I downloaded.

However when I downloaded Lunar for the Sega CD and try to start it...it doesn't want to play the game

How do you get the Sega CD games to work?  or maybe I have a bad iso?

---

### Post by F-3582 on 2008-08-11
Did you get the BIOS images as well?

---

### Post by You Are Not Pro on 2008-08-11
Okay, okay.  I figured it out.

I only downloaded the MP3's and ISO file.

This is what I had to do to make it work:
1. I had to go to: [http://www.fantasyanime.com/emuhelp/emuhelp_gens.htm#segacdbios](http://www.fantasyanime.com/emuhelp/emuhelp_gens.htm#segacdbios)
.2 Then I had to do this: [http://www.fantasyanime.com/emuhelp/emuhelp_gens.htm#segacdbios-setup](http://www.fantasyanime.com/emuhelp/emuhelp_gens.htm#segacdbios-setup)

Other than that.  Everything was fine.  Now I just need to mess with the options to make the resolution look better since using OpenGL makes Gens freeze up Ubuntu and I have to Ctrl+Alt+Backspace so log back in.

Thanks for all the help!

---

### Post by Saoshyant on 2008-08-17
I reckon there's some kind of regression in Gens.

Last time I tried Gens from a package on this thread (gens-2-12a) it worked like a charm, but since I wanted to play some old Mega CD games I had lying around I needed the CD support so I came here and got an updated package.  Now both versions present 2.12b and 2.15 are segfaulting on me.  I don't reckon anyone's going to try to fix the issue, but anyway here's a backtrace just in case:

```

*** glibc detected *** gens: free(): invalid pointer: 0x093e26b8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb75c47cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb75c7e30]
/usr/lib/libSDL-1.2.so.0(SDL_AudioQuit+0x65)[0xb7dabad5]
/usr/lib/libSDL-1.2.so.0(SDL_QuitSubSystem+0x7c)[0xb7daafec]
gens[0x806d957]
gens[0x807b7da]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb77519d9]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb774462b]
/usr/lib/libgobject-2.0.so.0[0xb7755103]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb7756627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb77567e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_item_activate+0x53)[0xb7b84bd3]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bb38b2]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x49)[0xb77519d9]
/usr/lib/libgobject-2.0.so.0[0xb7742e49]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x12b)[0xb774462b]
/usr/lib/libgobject-2.0.so.0[0xb775559a]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c7)[0xb7756627]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb77567e9]
/usr/lib/libgtk-x11-2.0.so.0(gtk_menu_item_activate+0x53)[0xb7b84bd3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_check_menu_item_set_active+0x54)[0xb7abfd84]
gens[0x80aa9a4]
gens[0x807d8a9]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7572ebc]
gens[0x804d0a1]
======= Memory map: ========
08048000-081f4000 r-xp 00000000 08:05 195661     /usr/bin/gens
081f4000-08222000 rwxp 001ac000 08:05 195661     /usr/bin/gens
08222000-0943b000 rwxp 08222000 00:00 0          [heap]
b3efa000-b3f91000 rwxp b3efa000 00:00 0
b3f91000-b40bd000 rwxs 00000000 00:08 286916678  /SYSV00000000 (deleted)
b40bd000-b40be000 ---p b40bd000 00:00 0
b40be000-b48be000 rwxp b40be000 00:00 0
b48be000-b48bf000 ---p b48be000 00:00 0
b48bf000-b50bf000 rwxp b48bf000 00:00 0
b50bf000-b511f000 rwxs 00000000 00:08 286883909  /SYSV00000000 (deleted)
b511f000-b57b8000 r-xp 00000000 08:05 1045007    /usr/share/icons/hicolor/icon-theme.cache
b57b8000-b5e61000 r-xp 00000000 08:05 1066480    /usr/share/icons/gnome/icon-theme.cache
b5e61000-b5ebf000 r-xp 00000000 08:05 1112126    /usr/local/share/fonts/tahoma.ttf
b5ebf000-b5ec1000 r-xp 00000000 08:05 1027474    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5ec1000-b5ec2000 rwxp 00001000 08:05 1027474    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5ec2000-b5eec000 r-xp 00000000 08:05 283912     /usr/lib/libkdefx.so.4.2.0
b5eec000-b5eed000 rwxp 0002a000 08:05 283912     /usr/lib/libkdefx.so.4.2.0
b5efc000-b5f00000 r-xp 00000000 08:05 1027679    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5f00000-b5f01000 rwxp 00003000 08:05 1027679    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5f01000-b5f04000 r-xp 00000000 08:05 1027682    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b5f04000-b5f05000 rwxp 00002000 08:05 1027682    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-ico.so
b5f06000-b5f25000 r-xp 00000000 08:05 114378     /usr/lib/kde3/plugins/styles/plastik.so
b5f25000-b5f26000 rwxp 0001e000 08:05 114378     /usr/lib/kde3/plugins/styles/plastik.so
b5f26000-b5f29000 r-xs 00000000 08:05 153855     /var/cache/fontconfig/5e10083637a12ecd1bff191eb66bfa2f-x86.cache-2
b5f29000-b5f2f000 r-xs 00000000 08:05 153631     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5f2f000-b5f34000 r-xs 00000000 08:05 153853     /var/cache/fontconfig/bddabcf04192498a6a74911686fc6962-x86.cache-2
b5f34000-b5f37000 r-xs 00000000 08:05 153852     /var/cache/fontconfig/a46337af8a0b4c9b317ad981ec3bdf87-x86.cache-2
b5f37000-b5f38000 r-xs 00000000 08:05 153851     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b5f38000-b5f3b000 r-xs 00000000 08:05 153850     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b5f3b000-b5f3c000 r-xs 00000000 08:05 153849     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b5f3c000-b5f3d000 r-xs 00000000 08:05 153848     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b5f3d000-b5f41000 r-xs 00000000 08:05 153624     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b5f41000-b5f44000 r-xs 00000000 08:05 153846     /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b5f44000-b5f45000 r-xs 00000000 08:05 153845     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5f45000-b5f47000 r-xs 00000000 08:05 153844     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b5f47000-b5f49000 r-xs 00000000 08:05 153843     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b5f49000-b5f4a000 r-xs 00000000 08:05 153842     /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b5f4a000-b5f4c000 r-xs 00000000 08:05 153841     /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b5f4c000-b5f52000 r-xs 00000000 08:05 153840     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5f52000-b5f54000 r-xs 00000000 08:05 153839     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5f54000-b5f56000 r-xs 00000000 08:05 153838     /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b5f56000-b5f5e000 r-xs 00000000 08:05 153837     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5f5e000-b5f64000 r-xs 00000000 08:05 153836     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5f64000-b5f65000 r-xs 00000000 08:05 153835     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5f65000-b5f7c000 r-xs 00000000 08:05 153834     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5f7c000-b5f7e000 r-xs 00000000 08:05 153833     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5f7e000-b5f84000 r-xs 00000000 08:05 153832     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b5f84000-b5f87000 r-xs 00000000 08:05 153831     /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b5f87000-b5f8b000 r-xs 00000000 08:05 148594     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b5f8b000-b5f8d000 r-xs 00000000 08:05 148484     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b5f8d000-b5f8e000 r-xs 00000000 08:05 153883     /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b5f8e000-b5f8f000 r-xs 00000000 08:05 153882     /var/cache/fontconfig/e9e44584608a73233979f764b5f9ddAborted


```

Edit: I'm also considering it may be that my libSDL and libc are not up to date and thus causing the crash.  Unfortunately I cannot upgrade them at the moment, so I won't be able to confirm it myself.  Oh well.

---

### Post by FranMichaels on 2008-08-17
Saoshyant, does
```
ldd /usr/bin/gens
``` (or whatever "whereis gens" returns...)
List anything as not found? If so, try

```
sudo ldconfig
```

Just a guess though :KS

---

### Post by maybeway36 on 2008-08-18
Thanks so much for this package! I was looking for a good Genesis emulator to try out Sonic Megamix and this fit the bill. It ran just fine on Debian lenny.

---

### Post by megamaced on 2008-08-24
Gens 2.15.3 released!

[ 1923815 ] Fix startup crash

This should help prevent the segfaults...

---

### Post by jake74 on 2008-08-24
Many thanks!

Running this on my Asus EEE 701, with Sega Saturn USB pad. It's brilliant!

I have one question, which I can't seem to find an answer for, what file format does Gens consider to be a MD file? All my MD games are .zip format, so when they're decompressed, as .md files, I still have to choose "Show all files" to select a game.

---

### Post by mthei on 2008-08-24
Thanks. I know I probably shouldn't be mixing packages, but this runs great on Debian Lenny.

---

### Post by Glucklich on 2008-08-24
Oh, I can't believe it! Thaaaaaank youuu! Finally I can play Streets of Rage again. I love it.

---

### Post by hardyjuejue on 2008-08-25
Still no support for OpenGL with ati binary driver fglrx ?
I went to the sourceforge page of Gens, found a recent (august 2008 ) patch for it, but it won't work => [http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344](http://sourceforge.net/tracker/index.php?func=detail&aid=1488458&group_id=73619&atid=538344) (tried with different sources and CVS, but it gives me segfault as soon as I switch to OpenGL).
I hope someone will have some interest in including this patch to Gens; having to revert to xorg ati open driver in order to use gens is really bothersome...

---

### Post by megamaced on 2008-08-25
> **hardyjuejue said:**
> Still no support for OpenGL with ati binary driver fglrx ?

I will attempt to incorporate that patch into Gens. But I don't use any ATi cards so I can't test it. I'll upload a package in the next couple of days.

---

### Post by DancemasterGlenn on 2008-08-25
I have a bit of a request. When the "stretch" option is off, can the gtk window resize to fit what's being emulated? Right now when I have stretch off, the window is a bit taller than it needs to be (black bars above and below).

The other request (almost certain I already asked this), is it possible to make fullscreen more widescreen-friendly (in other words, not over-stretch the image horizontally)? I believe there was some issue with doing this, but it would be a great option to have, if possible. Thanks so much, megamaced.

---

### Post by hardyjuejue on 2008-08-26
> **megamaced said:**
> I will attempt to incorporate that patch into Gens. But I don't use any ATi cards so I can't test it. I'll upload a package in the next couple of days.

Well, I do :-)
I'd be more than happy to test and feedback. Can't wait to see it !
btw, when I try to apply the patch to the source, I get the following errors: 

patching file src/gens/emulator/g_main.c
patching file src/gens/gens_core/gfx/blit2.c
patching file src/gens/gens_core/gfx/blit.h
patching file src/gens/gtkui/glade/callbacks.c
patching file src/gens/sdllayer/g_sdldraw.c
Hunk #1 succeeded at 59 (offset 1 line).
Hunk #2 succeeded at 70 (offset 1 line).
Hunk #3 succeeded at 122 (offset 1 line).
Hunk #4 FAILED at 140.
Hunk #5 succeeded at 296 (offset 1 line).
Hunk #6 FAILED at 329.
Hunk #7 succeeded at 350 (offset 2 lines).
Hunk #8 succeeded at 922 (offset 2 lines).
Hunk #9 succeeded at 974 (offset 2 lines).
2 out of 9 hunks FAILED -- saving rejects to file src/gens/sdllayer/g_sdldraw.c.rej
patching file src/gens/sdllayer/g_sdlsound.c

Hope this helps...

---

### Post by ezekiel000 on 2008-08-28
Would it be possible to add support for ogg music files instead of mp3 with mega cd games?

---

### Post by megamaced on 2008-08-28
> **hardyjuejue said:**
> Well, I do :-)
I'd be more than happy to test and feedback. Can't wait to see it !
btw, when I try to apply the patch to the source, I get the following errors: 

patching file src/gens/emulator/g_main.c
patching file src/gens/gens_core/gfx/blit2.c
patching file src/gens/gens_core/gfx/blit.h
patching file src/gens/gtkui/glade/callbacks.c
patching file src/gens/sdllayer/g_sdldraw.c
Hunk #1 succeeded at 59 (offset 1 line).
Hunk #2 succeeded at 70 (offset 1 line).
Hunk #3 succeeded at 122 (offset 1 line).
Hunk #4 FAILED at 140.
Hunk #5 succeeded at 296 (offset 1 line).
Hunk #6 FAILED at 329.
Hunk #7 succeeded at 350 (offset 2 lines).
Hunk #8 succeeded at 922 (offset 2 lines).
Hunk #9 succeeded at 974 (offset 2 lines).
2 out of 9 hunks FAILED -- saving rejects to file src/gens/sdllayer/g_sdldraw.c.rej
patching file src/gens/sdllayer/g_sdlsound.c

Hope this helps...

Same here.

I have emailed the author of the patch. Hopefully he'll have time to resolve it.

---

### Post by megamaced on 2008-08-28
[SIZE="6"]For ATi users - PLEASE TEST!![/SIZE]

nbondoux, the author of the ATi patch, has re-released his patch and you'll find it now compiles against Gens 2.15.3. I have built a new package including his patch, and want testers to OK it before I release it on Sourceforge and the 1st page of this tread. The objective is simply that openGL work properly with ATi cards.

I also want confirmed that users of Intel & nVidia cards are NOT affected by the changes..

The package is below (Ubuntu 8.04 package only for this testing phase, sorry):

[http://www.zshare.net/download/178009043573563c/](http://www.zshare.net/download/178009043573563c/)

---

### Post by quanumphaze on 2008-08-29
This is odd. The program runs fine except that the mouse cursor is still displayed, stuck in the middle when I run it full screen.

This always happens when I go in and out of full screen twice.

I don't notice this behavior in other apps. Any clues?

---

### Post by megamaced on 2008-08-29
> **quanumphaze said:**
> This is odd. The program runs fine except that the mouse cursor is still displayed, stuck in the middle when I run it full screen.

This always happens when I go in and out of full screen twice.

I don't notice this behavior in other apps. Any clues?

Are you referring to Gens 2.15.3 or 2.15.4 with the ATi patch? If the latter, did this happen in 2.15.3?

---

### Post by quanumphaze on 2008-08-29
2.15.3 on an Intel 945GM

I just upgraded from 2.12.?rc3 in the hope that this would be fixed.

A similar problem happens in Quake 1 (QuDos/Qrack port specifically) but the cursor remains where I left (I aim for the corner) it instead of the dead center. Quake 2 is fine though. So this may not be entirely the fault of Gens and due to some Intel/Xorg problem maybe.

goodnight

---

### Post by megamaced on 2008-08-29
> **quanumphaze said:**
> 2.15.3 on an Intel 945GM

I just upgraded from 2.12.?rc3 in the hope that this would be fixed.

A similar problem happens in Quake 1 (QuDos/Qrack port specifically) but the cursor remains where I left (I aim for the corner) it instead of the dead center. Quake 2 is fine though. So this may not be entirely the fault of Gens and due to some Intel/Xorg problem maybe.

goodnight

Please try 2.15.4

---

### Post by quanumphaze on 2008-08-30
> **megamaced said:**
> Please try 2.15.4

Sorry, 2.15.4 didn't fix the problem.

Turns out the problem is not the fault of Gens, I just tried to see if it effected any other games. I found Frozen Bubble and Starfighter have the exact same problem when toggling fullscreen.

A bit hard to describe it's exact behaviour as it's is a bit random. I alt+return to get into fullscreen and there is no mouse cursor. I drop in and out of fullscreen about 2 more times and then the cursor is suddenly there and will always be there in fullscreen until I close the program.

Upon opening again to check the consistency I get the same behavour the second time I run Gens, but the third time the cursor is there first time.

I can work around it by quickly running the mouse to the lower right before the cursor gets locked in place to limited degrees of success.

Sorry for the false alarm

---

### Post by jake74 on 2008-08-30
Sorry to repeat myself, but what file compression formats does Gens support, if any?

If no compression is support, what extension should my files have, as .md isn't recognised straight off.

---

### Post by megamaced on 2008-08-30
> **jake74 said:**
> Sorry to repeat myself, but what file compression formats does Gens support, if any?

If no compression is support, what extension should my files have, as .md isn't recognised straight off.

.smd or .bin

---

### Post by jake74 on 2008-08-30
> **megamaced said:**
> .smd or .bin

Thanks!

---

### Post by ezekiel000 on 2008-08-30
I thought I'd ask again as I think my question got lost in the ATI patch fixing but would it be possible to add support to be able to use Vorbis Ogg files instead of MP3 for Mega CD games?

---

### Post by hardyjuejue on 2008-08-31
> **megamaced said:**
> [SIZE="6"]For ATi users - PLEASE TEST!![/SIZE]

nbondoux, the author of the ATi patch, has re-released his patch and you'll find it now compiles against Gens 2.15.3. I have built a new package including his patch, and want testers to OK it before I release it on Sourceforge and the 1st page of this tread. The objective is simply that openGL work properly with ATi cards.

Ok, just tested. As far as it went, no problems: runs fine without speed problems. Only thing is: no more bilinear filtering. Indeed, when I used 2.15.3 with ati xorg drivers, I had a nice smooth bilinear filtering when using "Normal" render, but it seems to have disappeared with fglrx + gens 2.15.4. Is it normal ?

PS: Btw, I am using a widescreen LCD (16:10), hence fullscreen stretches way too much the display. Some emus do have correct aspect ratio for non 4:3 screen (esp. sdlmame and snes9x-gtk), any chances to see that in Gens ?

---

### Post by FranMichaels on 2008-08-31
Odd, it works properly for me (I'm on 1920 x 1200 and games have two vertical black bars full screen so to speak, so it is keeping the 4:3 ratio), you don't have Stretch ticked in the Graphics menu, do you? That would distort it full screen...

What I'd like to know is why the gens for linux on sourceforge lacks configure...?

---

### Post by megamaced on 2008-09-01
So can I assume that openGL support works now (in some shape or form) with the binary ATi driver?

---

### Post by hardyjuejue on 2008-09-01
> **megamaced said:**
> So can I assume that openGL support works now (in some shape or form) with the binary ATi driver?

Yes ;) Sorry if I wasn't clear, but OpenGL *does* work. Just bilinear filtering missing or something.

---

### Post by hardyjuejue on 2008-09-01
> **FranMichaels said:**
> Odd, it works properly for me (I'm on 1920 x 1200 and games have two vertical black bars full screen so to speak, so it is keeping the 4:3 ratio), you don't have Stretch ticked in the Graphics menu, do you? That would distort it full screen...

What I'd like to know is why the gens for linux on sourceforge lacks configure...?

No, if I untick Stretch, I just get black lines on top and bottom but the display is still overstretched on the left and right sides. I assume this is also driver related, since Nvidia binary drivers offer Aspect Ratio correction, while Ati's don't (display is either letterboxed or stretched).
Hence, if Aspect Ratio isn't achieved through soft methods, you get overstreched display, which doesn't happen with NVidia's bin drivers (and I imagine that other chips/drivers have this feature as well).

Btw, I don't know why gens CVS doesn't include configure (maybe to make it more OS independent ?) but I believe you can have it with autoconf, automake and some other stuff (I used to know how to do it, google for it).

---

### Post by nerdy_girlscout on 2008-09-08
> **ezekiel000 said:**
> I thought I'd ask again as I think my question got lost in the ATI patch fixing but would it be possible to add support to be able to use Vorbis Ogg files instead of MP3 for Mega CD games?

It seems they missed it again. I too hope to have OGG support, because MP3 is a patent-encumbered format and also has worse quality than OGG. FLAC support would be good too, since it's also free, and because it's lossless.

---

### Post by roachk71 on 2008-09-08
Gens (both versions) initially worked fine for me, until the latest library updates. Now, neither version works, even after a source build (the window simply hangs there, eating up CPU cycles, and can't be killed.)

Update (2008-09-08 18:37 AKDT): I have since reverted to Gutsy. In addition to the Gens issues, I kept having problems with random DNS lookup failures and network disconnects, which I never had in prior versions...Those are showstoppers.

EDIT: It would appear that the network driver in Hardy wasn't to blame for the modem problems. When Dad and I replaced the lighting in my room, its unusual wiring shorted out a few times and sent surges into my network. So I went over my checklist and discovered that both my cable modem and network interface are losing it. Thus, I'm using the modem's USB network bridge instead now (which only works somewhat better.)

---

### Post by begemot. on 2008-09-16
I'm running Ubuntu 8.04, got deb-pack from here
[http://www.zshare.net/download/18030216b0a87254/](http://www.zshare.net/download/18030216b0a87254/)
and it's not installing because of unsatisfied dependency - libpango 1.0-0.
Can this problem be fixed? Or i should take deb-pack for 7.10?


Thank you.

---

### Post by murak on 2008-09-17
Thank you for this, megamaced!

---

### Post by jon555 on 2008-09-22
Error
It worked good, i played some roms, but then I switched to fullscreen, it frose and became black. I only saw and could change framerite.  I could only minimise it for 5 secons or so pressing F12. I closed it by force. When I started it up next time it already started up frosen and with fullscreen.    But when it worked it was superb.

---

### Post by tjwoosta on 2008-09-22
> Error
It worked good, i played some roms, but then I switched to fullscreen, it frose and became black. I only saw and could change framerite. I could only minimise it for 5 secons or so pressing F12. I closed it by force. When I started it up next time it already started up frosen and with fullscreen. But when it worked it was superb.

if you delete the configuration file (gens.cfg) and start the emulator again, it will work

all your settings will go back to default

---

### Post by megamaced on 2008-10-05
UPDATE: 05/10/08

Gens 2.15.5 released!

A bug fix release, fixing various issues with the GUI enabling / disabling options. 
The new feature for this release is internal save state for SCD games. Thanks to ilguido for the patch.

See the first post for download links

---

### Post by disturbedite on 2008-10-05
i've got a feature request...
how about the option to disable menu icons in the gui?

---

### Post by mateamargo on 2008-10-05
I can't download it, I got this message:

```

Fatal error: Cannot instantiate non-existent class: memcache in /home/zshare/www/include/site/functions.php on line 5

```

---

### Post by BigSilly on 2008-10-06
> **megamaced said:**
> UPDATE: 05/10/08

Gens 2.15.5 released!

A bug fix release, fixing various issues with the GUI enabling / disabling options. 
The new feature for this release is internal save state for SCD games. Thanks to ilguido for the patch.

See the first post for download links

Thanks very much for this. It's fantastic to see work still going on with this marvellous emulator. Works just great here on my Hardy.

Excellent! :biggrin:

---

### Post by ilGuido on 2008-10-06
> **mateamargo said:**
> I can't download it, I got this message:

```

Fatal error: Cannot instantiate non-existent class: memcache in /home/zshare/www/include/site/functions.php on line 5

```

That's a temporary problem of zshare. Try to download it again.

---

### Post by megamaced on 2008-10-06
You can also download from [Sourceforge ]("http://sourceforge.net/projects/gens/")too. I'll probably stop using zshare for the next release and just use Sourceforge. Makes more sense.

---

### Post by matemargo on 2008-10-06
> **ilGuido said:**
> That's a temporary problem of zshare. Try to download it again.

Yes, I could download it :)

But I had to install a new libpango version for Hardy.

Works really fine. Thanks a lot!

---

### Post by FranMichaels on 2008-10-06
I'm pleased as punch, as the Zero Wing (european release) works in this one!

Built off of the sourceforge package, kudos for that.

One thing, not sure if it counts as a bug, but I'll mention it. In the load rom dialog, the open and cancel buttons are in the reverse order (as opposed to all other gnome apps...)

EDIT: I should mention I'm using the Intrepid Ibex beta, and gens built without a hitch with the new gcc 4.3...)

---

### Post by disturbedite on 2008-10-11
> **FranMichaels said:**
> ...One thing, not sure if it counts as a bug, but I'll mention it. In the load rom dialog, the open and cancel buttons are in the reverse order (as opposed to all other gnome apps...)
that might be because gens might not comply with the HIG. i know nestopia for linux doesn't. (i'm not complaining about, just stating a fact).

---

### Post by BigSilly on 2008-10-12
Is it just me or is this release actually performing better graphically than the last one? Has any work been done to improve it's performance with this new release? It's probably the best I've seen Gens looking on Linux. There seems to be no tearing to me, and Sonic the Hedgehog at full tilt looks fantastic!

Maybe it's just me, but either way well done all involved. 

:guitar:

---

### Post by RobLoach on 2008-10-14
How can we add Gens to the Ubuntu repositories?  Now that the .deb files are shipped on SourceForge, I assume this makes it a bit easier?

---

### Post by DjFIL on 2008-10-17
is there an i686 .deb installer available?  it won't let me install the i386 one available at the sourceforge page, and i don't know how to compile it on my own.  thank you.

---

### Post by matemargo on 2008-10-17
> **DjFIL said:**
> is there an i686 .deb installer available?  it won't let me install the i386 one available at the sourceforge page, and i don't know how to compile it on my own.  thank you.

Try to use
```

dpkg -i --force-architecture thepackage.deb

```

---

### Post by DjFIL on 2008-10-17
wow, that was easy.  big thanks to you.  yay genesis on my dell mini 9!

---

### Post by RobLoach on 2008-10-17
Added a Ubuntu Brainstorm idea for adding Gens to the Ubuntu repositories:
[http://brainstorm.ubuntu.com/idea/14511/](http://brainstorm.ubuntu.com/idea/14511/)

---

### Post by Epilonsama on 2008-10-17
Im having a dependency problem, when i tried to install gens 2.15.5 it asked me for libcairo2 but the thing is that I already installed it, what could be the problem.

---

### Post by matemargo on 2008-10-17
I've had a similar problem, and I've installed the libcaro from getdeb.net

---

### Post by DjFIL on 2008-10-18
ok... so i got the emulator it self working just fine.  but there's some weird things going on.  first it keeps forcing some hidden /.gens folder to be used, can't i use my own folder?  also whenever i try to configure any settings (video, default folders, control inputs, etc), it never saves the settings i configure.  i even tried to save a settings file, it doesn't save the file properly, nor does it automatically load the settings file like i'd expect it to.  really happy to have a genesis emulator that works really well... but i'd love to get these little issues out of the way.

---

### Post by megamaced on 2008-10-18
Those people with libcairo2 issues:

What version of Ubuntu are you running?
What version of Gens are you trying to install - and for what version of Ubuntu?
What version of libcairo2 do you have installed?

Gens for Dapper requires libcairo2 version 1.0.2-2
Gens for Hardy requires libcairo2 version 1.6.0

Libcairo2 in hardy is version 1.6.0

---

### Post by maybeway36 on 2008-10-19
> **DjFIL said:**
> ok... so i got the emulator it self working just fine.  but there's some weird things going on.  first it keeps forcing some hidden /.gens folder to be used, can't i use my own folder?  also whenever i try to configure any settings (video, default folders, control inputs, etc), it never saves the settings i configure.  i even tried to save a settings file, it doesn't save the file properly, nor does it automatically load the settings file like i'd expect it to.  really happy to have a genesis emulator that works really well... but i'd love to get these little issues out of the way.

What I do is to symlink my ~/.gens to whatever folder I want to use, for example:
```
ln -s ~/.gens ~/Desktop/gens-folder
```

---

### Post by gneville on 2008-10-19
Hi,

Is there LIRC support for this yet? If so, I can't seem to get it working. All i need is some sort of Back/Exit function so I can return to mythtv easily.

Thanks

---

### Post by DjFIL on 2008-10-19
for some reason today it started to save the config file properly, and loads it automatically.  so it's ok now, not really sure why it wasn't taking before.

---

### Post by MaxTeel on 2008-10-23
I can't download this from zshare. Can you host the .deb in another place?
Thanks in advance

---

### Post by seb0 on 2008-10-23
Yes, it seems that "gens_2.15.5_hardy_i386.deb" does not exist anymore on the website.

---

### Post by alex-weej on 2008-10-23
Please, for the love of all...! Maintain this package properly in Universe.

[https://launchpad.net/bugs/107927](https://launchpad.net/bugs/107927)

That way, people can just "apt-get install gens".

Please!

---

### Post by r2rX on 2008-10-24
Hey guys.

Gens doesn't seem to work for some reason.

This is what I get when trying to install/extract the file:

```

r2rxsu@r2rx:~/Desktop$ sudo dpkg -i gens-2.15.5-1.i386.deb
[sudo] password for r2rxsu: 
dpkg: error processing gens-2.15.5-1.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 gens-2.15.5-1.i386.deb
```

Any ideas why it's happening? I'll appreciate the assistance. :)

r2rX  :)

---

### Post by megamaced on 2008-10-24
Zshare seems to be OK now

Also bare in mind that you can download the same packages on the Gens sourceforge website...

---

### Post by wryun on 2008-10-24
> **RobLoach said:**
> Added a Ubuntu Brainstorm idea for adding Gens to the Ubuntu repositories:
[http://brainstorm.ubuntu.com/idea/14511/](http://brainstorm.ubuntu.com/idea/14511/)

There's a good reason it's not already in there:

[http://www.mail-archive.com/debian-legal@lists.debian.org/msg24871.html](http://www.mail-archive.com/debian-legal@lists.debian.org/msg24871.html)

(which fails to identify the MAME-derived YM2612 code as problematic, which it is...)

---

### Post by megamaced on 2008-10-26
Official Gens is on hiatus for the time being. I'd recommend downloading Gens/GS until we can get these changes uploaded back to official Gens.

[SIZE="4"]Gens/GS 2.15.5 M5[/SIZE]

*Gens/GS is a version of Gens for Linux maintained by GerbilSoft. The main goal of Gens/GS is to clean up the source code and combine features from various forks of Gens. *

Website: [http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)
Forum Thread: [http://ubuntuforums.org/showthread.php?t=959074](http://ubuntuforums.org/showthread.php?t=959074)

I've removed Gens 2.12b from this thread. Its not maintained anymore and getting very long in the tooth. Besides why would you want to run it anyway? ;)

---

### Post by buckeyered80 on 2008-10-28
Hey, sorry if I missed this somewhere in this thread, but did anyone ever get fullscreen aspect ratio working to fit to the screen?  I love the GFCEU emulator, it seems to be the most stable on linux.  But, I am kind of OCD about little issues like not being able to stretch the image to fit the screen.  Anyone got that working yet?
**Edit
Sorry, I just realized I posted this in the wrong thread!

---

### Post by Calculon64 on 2008-11-08
Any chance of an Ubuntu 8.10 64-bit version?

---

### Post by unebaguettesvp on 2008-11-09
> **Calculon64 said:**
> Any chance of an Ubuntu 8.10 64-bit version?

Calculon64:

```
sudo dpkg -i --force-architecture Gens-2.15.5-gs-m5-1_i386.deb
```

hope that helps!

---

### Post by BigSilly on 2008-11-09
Can we still hope for updates for this? I've moved back to this version at the moment since I get a better experience with it. Gens/GS is a bit laggy and slow for me.

Cheers. :)

---

### Post by meoblast001 on 2008-11-16
Any chance of netplay ever being added? I want to play Sonic with people.

---

### Post by ColeJayStooks on 2008-11-29
Hey man, doesn't look like that z share website is working out for Intrepid. For some reason when I use the Gens package at sourceforge I can't open Gens without the terminal... So I figured I'd give this page a try. They aren't the exact same packages, right?

---

### Post by ColeJayStooks on 2008-11-29
Hey guys, a little bump and what my problem seems to be.

```
cole@coledesktop:~$ gens
The program 'gens' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 57 error_code 3 request_code 3 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

That's with the Gens deb package from Sourceforge.

I figured I would try and compile by source after this, so I purged it, got the source package, and ran 'make'. Then an error came up so I ended up fixing it by installing:

```
sudo aptitude install libglade2-0 libglade2-dev
```

Finished installation, and didn't really work. Purged that, ran the deb again, and it worked one time when I went Applications -> Games -> Gens. Played for a while, then decided to see if it would still open. Tried again, GUI came up then closed, ran it through the terminal, and got that same first error from the first time around. It's a vicious cycle apparently.

---

### Post by megamaced on 2008-11-29
> **ColeJayStooks said:**
> Hey man, doesn't look like that z share website is working out for Intrepid. For some reason when I use the Gens package at sourceforge I can't open Gens without the terminal... So I figured I'd give this page a try. They aren't the exact same packages, right?

Use Gens/GS. Official Gens is dead again

---

### Post by bolingw on 2008-12-15
Hi guys.

I've just installed the "Gens_2.15.5-gs-m6-1_i386" package and have been trying the emulator out. For some reason, the bottom part of my screen is cut off (i have a 1280*800 laptop screen) when I go into full screen mode. I've tried the stretching but all its options seem to have no effect on the mode and I could not find other options solving the problem. There must be mechanics within the program for twisting screen ratio, so I've wondering what I'm missing out here.

ty.

---

### Post by Disreali on 2008-12-15
> **bolingw said:**
> Hi guys.

I've just installed the "Gens_2.15.5-gs-m6-1_i386" package and have been trying the emulator out. For some reason, the bottom part of my screen is cut off (i have a 1280*800 laptop screen) when I go into full screen mode. I've tried the stretching but all its options seem to have no effect on the mode and I could not find other options solving the problem. There must be mechanics within the program for twisting screen ratio, so I've wondering what I'm missing out here.

ty.

Try asking on the Gens/GS thread [http://ubuntuforums.org/showthread.php?t=959074](http://ubuntuforums.org/showthread.php?t=959074)

---

### Post by murasame on 2009-02-21
Hello to everyone, I have a strange issue with both the official and unofficial gens packages. Here it is, I configure keyboard and it works fine in windowed mode but whenever I switch to fullscreen mode, only arrows work and 'start' work.

I configured my keyboard like this:

A=Z
B=X
C=C

START=enter
RIGHT SHIFT= mode key

X=S
Y=D
Z=F

Of course, I tried to change layout and try other keys with no succes.

My keyboard has an American/Russian layout and works fine with any other apps without any specific configuration (out of the box) except for the 'compose' key which I reconfigured.

I also tried to launch it via the command line with no success neither.

Other thing is I seem to be unable to enable FX in fullscreen mode via the gui. FX only work by command line by typing 

```
gens --fs --rendermode 10 path_to_my_rom
```

Which is fine as I love my lauchers anyway and don't need a gui that much...

My issue really is about the keys and I found no solution (nothing !!!) after googling a couple of hours.

Any idea here ? Anyone with the same issue ?

Edit: I just tried win32 Gens/GS milestone 6 on wine and keyboard works fine... I really don't have a clue why it doesn't work in Fullscreen mode natively... Odd...

---

### Post by white_eagle-mk on 2009-03-11
It works! How awesome indeed!

Now I can play my beloved Shining Force 1/2 w/o having to run some stupid emulators via wine.

Emulation^2 FTW! :D

---

### Post by anjilslaire on 2009-03-11
Shining Force FTW!

---

### Post by Mr. Hibba on 2009-04-19
Hi all,

  The link to sonicretro wasn't working for me, so I went to the site and found the link there, but it still didn't work.

  The link for the source code worked, though, so I downloaded that and tried to compile it. I ran ./configure and I got the following error message:

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK+ version 2.4.0 or later not found!

I think I got Gens/GS version from the site, if that helps.

I'm not a very advanced user, so I would appreciate it if someone could walk me through, please.

Mr. Hibba

---

### Post by GerbilSoft on 2009-04-20
> **Mr. Hibba said:**
> Hi all,

  The link to sonicretro wasn't working for me, so I went to the site and found the link there, but it still didn't work.

  The link for the source code worked, though, so I downloaded that and tried to compile it. I ran ./configure and I got the following error message:

*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK+ version 2.4.0 or later not found!

I think I got Gens/GS version from the site, if that helps.

I'm not a very advanced user, so I would appreciate it if someone could walk me through, please.

Mr. Hibba
You need to install the GTK+ development packages.

Packages required to build Gens/GS:
autotools-dev pkg-config nasm libsdl1.2-dev libglib2.0-dev libgtk2.0-dev mesa-common-dev libgl1-mesa-dev zlib1g-dev libpng12-dev

---

### Post by Mr. Hibba on 2009-04-20
> **GerbilSoft said:**
> You need to install the GTK+ development packages.

Packages required to build Gens/GS:
autotools-dev pkg-config nasm libsdl1.2-dev libglib2.0-dev libgtk2.0-dev mesa-common-dev libgl1-mesa-dev zlib1g-dev libpng12-dev

Thanks! I installed/made sure I had those packages again and it completed the configure. When I tried "make", it came up with some errors. At the end, it said:

make[3]: *** [plugins/render/hq2x/mdp_render_hq2x_16_x86.o] Error 1
make[3]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6'
make: *** [all] Error 2

What should I do?

---

### Post by Grishka on 2009-04-20
> **Mr. Hibba said:**
> Thanks! I installed/made sure I had those packages again and it completed the configure. When I tried "make", it came up with some errors. At the end, it said:

make[3]: *** [plugins/render/hq2x/mdp_render_hq2x_16_x86.o] Error 1
make[3]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6'
make: *** [all] Error 2

What should I do?

you on 64-bit? use the .deb from the homepage. right click and save, for some reason it opens the file in my browser, maybe you have the same issue. if you insist on compiling, you'll have to use "-m32" compiler flag. if you're on 32-bit, idk. you'll have to post a few more lines of your make log.

---

### Post by GerbilSoft on 2009-04-20
> **Mr. Hibba said:**
> Thanks! I installed/made sure I had those packages again and it completed the configure. When I tried "make", it came up with some errors. At the end, it said:

make[3]: *** [plugins/render/hq2x/mdp_render_hq2x_16_x86.o] Error 1
make[3]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src/gens'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/munch/Desktop/gens-2.15.5-gs-m6'
make: *** [all] Error 2

What should I do?
That backtrace doesn't really help, but I'm guessing that you have an older (<2.05.01) version of nasm installed. Older versions of nasm can get tripped up quite easily with the hq?x code.

Try installing a later version of nasm. You should be able to use the packages from Intrepid or Jaunty even if you're using an older version of Ubuntu.

Also, the next release (r7) supports building with yasm instead of nasm. yasm doesn't have as many issues with this sort of thing.

---

### Post by Mr. Hibba on 2009-04-20
> **Grishka said:**
> you on 64-bit? use the .deb from the homepage. right click and save, for some reason it opens the file in my browser, maybe you have the same issue. if you insist on compiling, you'll have to use "-m32" compiler flag. if you're on 32-bit, idk. you'll have to post a few more lines of your make log.

I'm not sure if I'm 32 or 64 bit. How can I check?

And my browser does appear to be trying to open it in the window. I'll try right-clicking the link...

---

### Post by Mr. Hibba on 2009-04-20
Right-clicking the link helped, I could save it to my desktop, and got it running. 

Thank you all for helping me with my questions.

Mr. Hibba

---

### Post by Gannin on 2009-05-02
I'm not sure if this has been reported yet, but on my system the sound seems to lag a bit.  When you do something, it takes about a second for the sound to play, almost like the sound buffer is too large.

---

### Post by firehawk_thexder on 2009-05-07
I've noticed that since I updated to Ubuntu 9.04 from 8.10, Gens runs very slowly with any Render filter enabled, and only runs at speed when 'Graphic' -> 'Render' is set to Normal.  (as opposed to my prefence of say, Hq2x).  
 
This is running on an Asus EEE PC 1000HA -

---

### Post by tjwoosta on 2009-05-07
> **firehawk_thexder said:**
> I've noticed that since I updated to Ubuntu 9.04 from 8.10, Gens runs very slowly with any Render filter enabled, and only runs at speed when 'Graphic' -> 'Render' is set to Normal.  (as opposed to my prefence of say, Hq2x).  
 
This is running on an Asus EEE PC 1000HA -

that sounds like a graphics driver issue to me

---

### Post by CharmyBee on 2009-05-07
Yep, the EEE PC uses Intel graphics which Jaunty has poor support for.

---

### Post by cdwillis on 2009-05-08
It may be a driver issue. I have the 1000HE, but I don't have any genesis roms to test out right now. You may want to look at this thread: [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582) which should help with video performance for you. My wireless randomly cuts out after a few hours with the updated kernel for some reason, but the video performance is better.

---

### Post by BeBoBli on 2009-05-11
Great emulator as always. Unlike others I'm running it perfectly on my EeePC (900A). I've got one problem though software wise. The gamepad config will not detect my dpad buttons when I press them. I have deducted that other emulators like mednafen, Psx and zsnes do not have trouble detecting the dpad. All of the other buttons work including analogue sticks.

I do not know how to troubleshoot this, unfortunately. Would opening js0 in some manner help? If so, how?

---

### Post by Gannin on 2009-05-11
There's a program called jstest you might want to try out.  I haven't tried it myself so I don't know exactly how it works, but I know it's supposed to help you test out your joystick.

---

### Post by BigSilly on 2009-05-12
If you have a dual analogue PC pad, I generally find with Gens that you have to disable the analogues on the pad. There should be a small button in the centre of your controller that controls this. Worth a shot anyway.

---

### Post by BeBoBli on 2009-05-13
> **BigSilly said:**
> If you have a dual analogue PC pad, I generally find with Gens that you have to disable the analogues on the pad. There should be a small button in the centre of your controller that controls this. Worth a shot anyway.

It is an original PSX dualshock. This particular converter I have on hand doesn't allow you to disable the analogue. The directional pad works fine in other emulators though so while it might have been a solution I'd prefer filing a detailed bug report. I'm not concerned with playing my games rather than informing the authors of the problem anyways.

---

### Post by MaindotC on 2009-06-06
Thank you for the package and it works perfectly for me on 64-bit with the --force-architecture option.  I wish the "thank you" thing was working :(

---

### Post by wingnux on 2009-06-07
I can't get any filter to work on fullscreen mode, only on windowed mode, any help? I'm running Ubuntu Jaunty 32bit with the latest nvidia beta drivers and the opengl box checked on gens' config.

EDIT: Oh, and most of the time I can't save/load a savestate when in fullscreen =/

---

### Post by wingnux on 2009-06-08
Bump.

---

### Post by unebaguettesvp on 2009-08-05
hi-

i'm trying to get this package working on a fresh install of jaunty 64-bit. everything works except for the sound. any ideas?

---

### Post by unebaguettesvp on 2009-08-05
solved this problem by uninstalling pulseaudio. this actually solved ALL of my sound problems! i have had to uninstall pulseaudio for hardy and intrepid too. pa is bad news.

---

### Post by juliobahar on 2009-09-28
This Gens 2.15.5 Version worked like a charm on my Desktop Ubuntu Jaunty x86. With built in intel video card and audio. Yet some video issue. I used Sega SMD files that came with a version of MS windoes fusion emulator.

Thanks all for the package.

---

### Post by murasame on 2009-10-30
> **wingnux said:**
> I can't get any filter to work on fullscreen mode, only on windowed mode, any help? I'm running Ubuntu Jaunty 32bit with the latest nvidia beta drivers and the opengl box checked on gens' config.

EDIT: Oh, and most of the time I can't save/load a savestate when in fullscreen =/

You must edit the configuration manually to achieve this:

[LIST]
[*]Edit gens.cfg in ~/.gens
[*]Look for the line with filter settings in fullscreen mode
[*]Done !
[/LIST]

About the saves, I don't know. I never had such an issue and I can't reproduce that behaviour.

---

### Post by joshuajon on 2009-11-15
Just wanted to mention the hardy/intrepid .deb seems to work great in karmic.  Yay :)

---

### Post by lichuan on 2010-01-05
Works great for Ubuntu 9.10 Karmic! :KS

---

### Post by Musilitar on 2010-01-24
Hello,
I'm very interested to use this package for emulation, but I have a problem: I'd like to do this on my PS3, which currently runs Ubuntu 9.10. I've been looking for days for a good Genesis emulator, but haven't found a thing that would work or install. I know that the PS3 has a PPC-architecture and that there is no package for that, but would it be possible to make that? I've read nothing but good things about this emulator and I'm wondering if it would be possible to get it running on PS3 Linux. If it would be, I'd finally have a working emulator for most of the systems.

I'm not sure if this thread is still checked, but it would be great to get an answer.
Thanks in advance,
Musilitar

---

### Post by MaindotC on 2010-01-24
Did you try installing it from source?  Can you not install build-essential on your psp?  What happens when you try installing it from source?

---

### Post by Musilitar on 2010-01-24
When I download the source package, cd to where I unpacked it and then run ./configure (as mentioned in the install file) I get this error:

configure: error: Unsupported operating system: powerpc64-unknown-linux-gnu

So I guess it just isn't possible then? I was really hoping it was...

---

### Post by MaindotC on 2010-01-24
They handle requests for specially built packages on their support site [http://sourceforge.net/projects/gens/support](http://sourceforge.net/projects/gens/support) why don't you see if you can get a special build?

---

### Post by afkun on 2010-03-05
I have x64 Karmic, I ran

```
sudo dpkg -i --force-architecture Gens-2.15.5-gs-m5-1_i386.deb
```

and it works perfectly. At first when I would configure the joystick, it would freeze, but I think I was just being impatient. Thank you for this!

---

### Post by cor2y on 2010-03-09
I tried that method and while it did install i got this message
```
~/Desktop/Downloads$ gens
terminate called after throwing an instance of 'std::out_of_range'
  what():  basic_string::substr
Aborted
```
any help would be appreciated

---

### Post by yaztromo on 2010-03-20
The zshare link for the latest hardy version doesn't work when the timer gets to zero. Anyone still have the file can re-upload it?

Edit: NVM I got the GS package and it works good in Karmic.

---

### Post by Gannin on 2010-03-20
You should just try Gens/GS.  It's a new project based on Gens that's actually still being actively developed.

---

### Post by brantpadams on 2010-03-26
Hi. New member of the forum and I'm having quite a bit of trouble trying to get Gens installed. I've been using ubuntu a little over a year now, but I would definitely still consider myself a newb.

Basically, every package that I've tried to download either won't install or won't open once I've downloaded it. I'm running 9.10 Karmic on a Dell Inspiron 1525. I'm not sure how to tell whether or not it's a 32-bit or a 64-bit. 

The .deb files won't open for me, neither will the ones ending in i386. I'm sorry if I'm being too vague in my description, but that's the best I can do. Any ideas? I really appreciate the help.

---

### Post by bb93 on 2010-04-02
Hi Guys. My system is Ubuntu 9.10 64 bits and it works :)

Steps:

1.Download Gens/GS 2.15.5 M5 .deb in the fisrt page

2.Install ia32-libs if you haven't already:

```
sudo apt-get update
sudo apt-get install ia32-libs
```

3. sudo dpkg --force-architecture -i Gens-2.15.5-gs-m5-1_i386.deb

And it'll works perfectly :D;)

---

### Post by megamaced on 2010-04-03
Yes I now run Gens/GS on 64-BIT myself using the --force-architecture option and it works fine.. Maybe if we ask nicely Gerbilsoft might release a 64-bit version.. but probably not! ;)

---

### Post by bb93 on 2010-04-03
> **megamaced said:**
> Yes I now run Gens/GS on 64-BIT myself using the --force-architecture option and it works fine.. Maybe if we ask nicely Gerbilsoft might release a 64-bit version


That would be great jeje!

---

### Post by brantpadams on 2010-04-04
> **bb93 said:**
> Hi Guys. My system is Ubuntu 9.10 64 bits and it works :)

Steps:

1.Download Gens/GS 2.15.5 M5 .deb in the fisrt page

2.Install ia32-libs if you haven't already:

```
sudo apt-get update
sudo apt-get install ia32-libs
```

3. sudo dpkg --force-architecture -i Gens-2.15.5-gs-m5-1_i386.deb

And it'll works perfectly :D;)
I'm sure this will work for me, but I don't know which one to download from the first page. The only .deb file that I've downloaded won't extract. Is there a specific one that I need to get?

---

### Post by bb93 on 2010-04-05
> **brantpadams said:**
> I'm sure this will work for me, but I don't know which one to download from the first page. The only .deb file that I've downloaded won't extract. Is there a specific one that I need to get?


Hi brantpadams. I have install Gens/GS Release 7, exactly this one...and it works ;)

You can download from [here]("http://segaretro.org/Gens/GS?rdfrom=http%3A%2F%2Finfo.sonicretro.org%2Findex.php%3Ftitle%3DGens%2FGS%26redirect%3Dno#Download")

---

### Post by BigSilly on 2010-04-05
Is Gens/GS dead then? This release is quite old now, and I've not seen any activity for a while. I hope it's still going anyway. :)

---

### Post by brantpadams on 2010-04-05
> **bb93 said:**
> Hi brantpadams. I have install Gens/GS Release 7, exactly this one...and it works ;)

You can download from [here]("http://segaretro.org/Gens/GS?rdfrom=http%3A%2F%2Finfo.sonicretro.org%2Findex.php%3Ftitle%3DGens%2FGS%26redirect%3Dno#Download")
Still having problems.

I downloaded each individual file from the source you suggested to see if they would work. There doesn't seem to be any working application in the tar.gz file and the .deb file still won't extract. After I downloaded the .deb I ran the script and here's what came up:

brant@brant-laptop:~$ sudo apt-get update
[sudo] password for brant: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release.gpg                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic Release                                   
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Translation-en_US       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Translation-en_US 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release                               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/main Sources                              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Sources                        
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Packages                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [908B]
Fetched 3,637B in 2min 0s (30B/s)
Reading package lists... Done
brant@brant-laptop:~$ sudo apt-get install ia32-libs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
The following packages were automatically installed and are no longer required:
  lsb-desktop m4 libqt4-gui lsb pax libqt3-mt lsb-graphics lsb-core
  ncurses-term lsb-cxx
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
brant@brant-laptop:~$ sudo dpkg --force-architecture -i Gens-2.15.5-gs-m5-1_i386.deb
dpkg: error processing Gens-2.15.5-gs-m5-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 Gens-2.15.5-gs-m5-1_i386.deb

I'm guessing it's saying "No such file or directory" because nothing has been extracted. I'm not sure why I can't extract the file, but that seems to be the main problem. Thanks for all your help guys, sorry I'm such a newb.

---

### Post by Grishka on 2010-04-05
> **brantpadams said:**
> Still having problems.

I downloaded each individual file from the source you suggested to see if they would work. There doesn't seem to be any working application in the tar.gz file and the .deb file still won't extract. After I downloaded the .deb I ran the script and here's what came up:

[SNIP]
brant@brant-laptop:~$ sudo dpkg --force-architecture -i Gens-2.15.5-gs-m5-1_i386.deb
dpkg: error processing Gens-2.15.5-gs-m5-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 Gens-2.15.5-gs-m5-1_i386.deb

I'm guessing it's saying "No such file or directory" because nothing has been extracted. I'm not sure why I can't extract the file, but that seems to be the main problem. Thanks for all your help guys, sorry I'm such a newb.

there's no need to extract anything. from the looks of it, you've missed the './' before the filename. so, once again, here's how to install it on a 64-bit system:
download [the deb file](http://segaretro.org/images/7/75/Gens_2.16.7_i386.deb) into your home directory, then run the terminal and
```
sudo dpkg -i --force-architecture ./Gens_2.16.7_i386.deb
```

---

### Post by brantpadams on 2010-04-05
> **Grishka said:**
> there's no need to extract anything. from the looks of it, you've missed the './' before the filename. so, once again, here's how to install it on a 64-bit system:
download [the deb file](http://segaretro.org/images/7/75/Gens_2.16.7_i386.deb) into your home directory, then run the terminal and
```
sudo dpkg -i --force-architecture ./Gens_2.16.7_i386.deb
```
Awesome! The problem was I was sending it to my download folder and not my home directory. Now it's running like a charm. Thanks for all your help everyone!

---

### Post by brantpadams on 2010-04-05
The only other problem I seem to be having is getting out of fullscreen. It simply doesn't happen. Anybody else have this problem?

---

### Post by Grishka on 2010-04-05
> **brantpadams said:**
> The only other problem I seem to be having is getting out of fullscreen. It simply doesn't happen. Anybody else have this problem?

alt+enter doesn't work for you?

---

### Post by bb93 on 2010-04-05
> **brantpadams said:**
> Awesome! The problem was I was sending it to my download folder and not my home directory. Now it's running like a charm. Thanks for all your help everyone!

Yeah :guitar: It was a little personal error :)

> **brantpadams said:**
> The only other problem I seem to be having is getting out of fullscreen. It simply doesn't happen. Anybody else have this problem?

Alt+ENTER on your keyborad ;)

---

### Post by brantpadams on 2010-04-05
> **Grishka said:**
> alt+enter doesn't work for you?
Kinda weird. Wasn't working at first, but it is after a restart. 
Gens/GS for life!

---

### Post by bb93 on 2010-04-07
Hi guys! How can i play network via in Gens?

Because option is disabled when it put's a game. I know in Windows is too easy, but in GNU......

[[IMG]http://img532.imageshack.us/img532/3541/capturadepantallagensgs.th.png[/IMG]](http://img532.imageshack.us/i/capturadepantallagensgs.png/)

---

### Post by disturbedite on 2010-04-08
> **bb93 said:**
> Hi guys! How can i play network via in Gens?

Because option is disabled when it put's a game. I know in Windows is too easy, but in GNU......

i don't believe gens for linux has network play capability. there isn't a sufficient library/software analogous to Kaillera (which is what gens on windows utilizes for network play, iirc).

---

### Post by bb93 on 2010-05-08
I downloaded last stable version Gens/GS .deb, it's 2.16.7, and Gens starts, but roms doesn't work; it doesn't see anything.

My computer is an Ubuntu 10.04 x64.

Yes, I install ia32-libs.

Any people with problems?

Thanks!

[EDIT] Sorry, it works in my Ubuntu 10.04 x64. I should to choose an rom with a bug ;)

---

### Post by brantpadams on 2010-09-02
Haven't been here in a while!

So I'm having some trouble trying to load SegaCD games. I was assured that I had downloaded the correct package for my particular game (iso file) but when I try to load it I get the message "Your Sega CD BIOS files aren't configured correctly.
Go to menu 'Options -> BIOS/Misc Files' to set them up."

I have absolutely no clue what to do when I get to this menu. What exactly is it asking me to set up and how do I do it? 

Running 10.04.

---

### Post by -15F on 2010-10-07
Can anybody say how can I adjust volume in Gens/GS v2.16.7 ?

---

### Post by mister_playboy on 2010-10-07
> **brantpadams said:**
> I get the message "Your Sega CD BIOS files aren't configured correctly.
Go to menu 'Options -> BIOS/Misc Files' to set them up."

I have absolutely no clue what to do when I get to this menu. What exactly is it asking me to set up and how do I do it?

You'll need to get the BIOS file for the SegaCD and put them in the directory so Gens can see them.  You have to do the same thing for any of the disc-based systems... Playstation, Saturn, etc.

We can't discuss getting the BIOS files on this forum, you'll have to ask Google instead.

---

### Post by inukaze on 2011-01-17
Packages for AMD64

[http://www.megaupload.com/?d=RFY8BCCP](http://www.megaupload.com/?d=RFY8BCCP)

Its Version of 32 Bits , you must need installed ia32 , or something like that , depend of your distro

For the guy , and the netplay , you can try with the emulator called "regen"

[http://aamirm.hacking-cult.org/www/regen.html](http://aamirm.hacking-cult.org/www/regen.html)

---

### Post by mama21mama on 2011-06-16
Netplay desactivado
como lo activo?

---

