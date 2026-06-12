---
title: "Doom 3?"
date: 2007-11-01
forum: Gaming &amp; Leisure
---

### Post by eheyl on 2007-11-01
Hey all I downloaded what looks like the doom3 demo.run file from the ftp server and tried running it using the docs found here. Is that the right file? There doesn't seem to be one for the full game?? When I run the install and try to install to the default /usr it says I've got no permission to do that? How do I change the permissions? SHEESH. Linux for games...right....Need a bit of help here if possible. I've the sneaky suspicion the demo file isn't the right file....I'm still a newbie when it comes to linux and games....

---

### Post by eheyl on 2007-11-01
Now its telling me that root can't login from the login screen?? help?!

---

### Post by Sockerdrickan on 2007-11-01
sudo sh thefile
[http://zerowing.idsoftware.com:6969/stats.html?info_hash=b221a4dee26cf007dd33cfc7871aa70f6899a213](http://zerowing.idsoftware.com:6969/stats.html?info_hash=b221a4dee26cf007dd33cfc7871aa70f6899a213)

---

### Post by weblordpepe on 2007-11-01
The install file needs to be run as root. Personally I think they should distribute doom 3 / quake as an rpm or .deb.

Anyway. You need to use the **sudo** command in the terminal to run the file. It will prompt you for the root password, and then execute file.
eg:
**sudo sh /doom3demothingiefile.run**

---

### Post by eheyl on 2007-11-01
Thanks. Hey Tux0r is that the right file? only 20MB?

---

### Post by cogadh on 2007-11-01
The 20 MB file is the binary for the full game, which requires you to already have the data files from the retail game. The demo should be about 460 MB and comes with the necessary data files.

---

### Post by eheyl on 2007-11-01
ah ok then. I've got the full game

---

### Post by Sockerdrickan on 2007-11-01
Have you gotten it to work?

---

### Post by eheyl on 2007-11-01
yes but now it says when I try to copy one of the files from the cd to the /base directory that I don't have permission....now what? isn't there a way I can set the permission without terminal and if not, whats the command....a bit frustrating

---

### Post by cogadh on 2007-11-01
```
sudo cp /media/cdrom/<source file> /usr/games/<destination directory>/
```
Just adjust the paths in the command to compensate for the correct CD-ROM and game paths.

---

### Post by eheyl on 2007-11-01
gave it a shot via terminal but the linux book I have isn't the best on details....could really use the help...

---

### Post by eheyl on 2007-11-01
what does cp do?

---

### Post by eheyl on 2007-11-01
Here's what I did:

sudo cp /media/cdrom/Setup/Data/base/pak002.pk4  usr/local/games/doom3/base

The output I get: cp: cannot create regular file `usr/local/games/doom3/base': No such file or directory

---

### Post by cogadh on 2007-11-01
"cp" is copy.

Try this:
```
sudo cp /media/cdrom/Setup/Data/base/pak002.pk4 /usr/local/games/doom3/base/
```
The extra "/" on the beginning and end makes a difference. If the "base" directory doesn't actuially exist, then you need to create it:
```
sudo mkdir /usr/local/games/doom3/base
```

---

### Post by eheyl on 2007-11-01
ah ringadingding. I GET IT! I have to first cd to the top level directory

---

### Post by hikaricore on 2007-11-01
Before typing random commands in that you haven't even looked into yet, might I suggest learning a little bit about the terminal and what certain commands actually do?

Found this with a quick google search: [http://jucato.wordpress.com/2006/08/22/ubuntu-classroom-command-line-basics/](http://jucato.wordpress.com/2006/08/22/ubuntu-classroom-command-line-basics/)

I know better intros to the Linux/Ubuntu command line exist, I just didn't search extensively.

---

### Post by eheyl on 2007-11-01
takes a while though

---

### Post by cogadh on 2007-11-01
But it is worth it in the end, you will be able to do a lot more once you learn a little on how to use the terminal.

---

### Post by eheyl on 2007-11-01
Almost done copying things over, thanks for that link hikaricore

---

### Post by philven on 2007-11-01
I got Doom 3 to run fine except it won't save the  game.  The last save was an autosave when I entered the Mars City Underground, but when I hit F5 to save, it won't and I have to start each time at the Mars City Underground.

I tried using the chown command to change the permissions for the directory the saved games are in, but i did no good, still can't save a game.  Anyone else having this problem?

---

### Post by weblordpepe on 2007-11-02
yeah i did. i had to chown the /usr/local/games/whatever/doom3 folder and then use nautilus to actually set the permissions.

eep!!

---

### Post by pmj on 2007-11-02
Why not just install the game to your home directory? No sudo or permissions problems can happen that way and you don't have to do anything from a terminal; it's the safest and best method unless you have multiple users on the system that needs to run the game.

Uninstalling also becomes really easy when you do that, as all you have to do is delete the game directory.

---

### Post by Tom Mann on 2007-11-02
I'd use:

```
sudo chown -hR $USERNAME:users /usr/local/games/doom3
```

to get it working.

(the h means it sets any symlinks to the user/group specified - but not the file it links to, the R means recursive, $USER would be seen by the shell as your username.)

Also, do not substitute USERNAME for your username. The shell will do that itself :)

---

### Post by philven on 2007-11-02
I tired chown on the /usr/local/games/doom3 directory.  Still can't save.  I think I'll delete it and install it into the the /home/ directory and see what happens.

---

### Post by philven on 2007-11-02
It works now.  Thanks for all your tips.

---

### Post by Sockerdrickan on 2007-11-02
Glad I could help :D

---

### Post by weblordpepe on 2007-11-03
Personally I don't think you should install software to your home directory. It's a naughty place because all of a sudden your home directory is gigabytes in size and contains binaries & symlinks which branch out of the system.

---

### Post by FG123 on 2007-11-03
> **weblordpepe said:**
> Personally I don't think you should install software to your home directory. It's a naughty place because all of a sudden your home directory is gigabytes in size and contains binaries & symlinks which branch out of the system.
That's certainly true, but for someone just starting with Linux it's probably the easier place to dump software to begin with since they have full write access, until they learn about permissions.

---

### Post by cogadh on 2007-11-03
> **FG123 said:**
> That's certainly true, but for someone just starting with Linux it's probably the easier place to dump software to begin with since they have full write access, until they learn about permissions.
By that logic, wouldn't installing a game properly be the perfect opportunity to learn about permissions? I'd rather make my permission mistakes on that, instead of something important, like a driver install or kernel upgrade, but maybe that's just me.

---

### Post by FG123 on 2007-11-03
> **cogadh said:**
> By that logic, wouldn't installing a game properly be the perfect opportunity to learn about permissions? I'd rather make my permission mistakes on that, instead of something important, like a driver install or kernel upgrade, but maybe that's just me.
It's just you. :)

I used to be a fairly active gamer, trying Linux occasionally. If it was too much work to get the same game I played in Windows to run in Linux - I'd give up. So, if you're a gamer coming from Windows, the less work required to get a game up and running in Linux, the better the first impression, even if you had to cut a few corners. Games can be rather important to people, so avoiding extra frustration for a newbie is a good thing. They can learn permissions later, they just want to play!

---

### Post by weblordpepe on 2007-11-03
**Which is why games need to be released as a .deb or put in repositories, and not just distributed as a .run file**
Grr!!! :P

Installing software in Ubuntu is like 1000 times easier than in Windows. Its just the pure linux stuff which is annoying thanks to permissions.

---

### Post by cogadh on 2007-11-04
Distributing it as a .run file ensures that an application will be compatible with any Linux distribution and is not dependent on any particular package management system. Releasing a .deb would mean that an app would only work on Debian based systems, like Ubuntu, and would leave users of distros that use other package managers, like Fedora or Suse, out in the cold. If they were to produce packages for all package managers, then that would mean maintaining multiple copies of the install, plus a .run package for distros that don't rely on RPM, DEB or other package managers. The generic .run package is just easier to deal with in the long run.

What really needs to happen is developers who release .run files for Linux need to stop assuming that Linux users are very knowledgeable about the proper uses of their system and provide "idiot-proof" instructions for installing applications like they already do for Windows.

---

### Post by weblordpepe on 2007-11-04
All that they need to create is:
.run file (a script installer for any linux OS)
.deb
.rpm

If they create a deb or rpm, then it is like 2 seconds to create another package from it using alien. It is not a bourdon to create multiple package formats. Many many software vendors do, even vendors which release software on a monthly cycle (e.g. Wine).

Game developers release something - what - every 3 years? It is not a problem for game developers to release multiple package formats.

They need to provide a .deb or .rpm.

---

### Post by FG123 on 2007-11-04
I think it's a question of

(a) Bandwidth for the providers
(b) Simplicity for everyone

Having multiple versions of the same game installer tends to confuse people, plus it's extra bandwidth/storage required for whoever has to host them.

---

### Post by weblordpepe on 2007-11-04
> **FG123 said:**
> I think it's a question of

(a) Bandwidth for the providers
(b) Simplicity for everyone

Having multiple versions of the same game installer tends to confuse people, plus it's extra bandwidth/storage required for whoever has to host them.nope nope nope nope.

Bandwidth = solved already through mirrors, torrents, and various other means. 
Simplicity = SOLVED with multiple formats available. It does not make things confusing having more than one option to download, when it is easily labeled. Take Firefox for example. The website automatically selects which operating system you are using and provides the right download file.

Firefox even exists in repositories. Firefox is released more often than iD Software releases titles. 

I am all for having few package formats in existence. However, the deb, rpm, and .run (or even tarballs) cover 99.9% of all distros that are worth caring about.

---

### Post by cogadh on 2007-11-04
Wine and Firefox are bad examples for developer package maintenance. They actually don't create any distro specific packages, they have community members maintain the different packages. In fact, in both cases, the devs only provide a source or binary package in tar ball form, not a package manager form. The community maintainers take those tar balls and create distro specific packages from them.

You are looking at this from the perspective of the user, not the developer. In their mind, the greatest possible result from a minimal amount of effort is the desirable solution. In the case of providing a native linux installer for games, that means a .run file only. If game companies would allow community maintainers like Wine and Firefox, that would change everything.

---

### Post by weblordpepe on 2007-11-05
Well, is someone gonna make a .deb of doom3? i dont know how.

---

### Post by weblordpepe on 2007-11-05
Well, is someone gonna make a .deb of doom3? i dont know how.

---

### Post by FG123 on 2007-11-06
> **weblordpepe said:**
> Well, is someone gonna make a .deb of doom3? i dont know how.
I'm not sure how the licensing stuff works with closed-source applications, but I'm guessing you'd have to get permission from iD before you'd be allowed to repackage their binaries in a .deb. They generally prefer people use their .run files, at least officially.

You can take a regular open-source app and repackage it, but I've never seen anyone try that with a closed-source, commercial app, unless they were granted permission.

---

### Post by weblordpepe on 2007-11-06
Oh yeah now that's a good point. I didn't think of the shareware motto of not modifying the content when redistributing it.

Although yeah I can see where the difference between unofficial and official comes into it. iD should be good sports and make some debs and rpms.

---

### Post by SpaceFarm on 2007-11-10
-> Linux noob here.

I'm tried reading this thread and a number of other instructions but I can't seem to get this working properly. I'm very new to linux but have a basic understanding of what's going on haha... 

I've managed to get the doom3 shell script file into /usr/local/games. I can run the installer and after I go through the prompts, right at the end I get errors:

"Can't create, can't write etc...to usr/local/games/doom3...etc"

Even though it says installation complete! 

Obviously this is just a permission thing for the usr/local/games/doom3 folder but I tried the 

```
sudo chown -hR $USERNAME:users /usr/local/games/doom3
```

but that doesn't seem to be doing anything. What am I doing wrong? Hehe, thanks.

---

### Post by SpaceFarm on 2007-11-10
It's okay, solved it. Turns out the doom3 file/script was preventing the creation of the doom3 folder.

---

### Post by weblordpepe on 2007-11-10
These are the kinds of silly linux problems that are solved by using package managers, debs and rpms.

We really need a relaxed licencing model which lets us repackage doom3 & commercial titles as debs.

---

### Post by SpaceFarm on 2007-11-11
Hahaha. I got Doom 3 working 100% though. I'm really impressed with Linux...I think I'll try Prey or Quake 4 next!

But I do agree weblordpepe, It'd be much easier if games were to be installed that way.

---

### Post by carlosjuero on 2007-11-11
> **weblordpepe said:**
> These are the kinds of silly linux problems that are solved by using package managers, debs and rpms.

We really need a relaxed licencing model which lets us repackage doom3 & commercial titles as debs.

Ya gotta take that up with id software - they are quite adamant about the repackaging of their installers being a 'no no'.

> **SpaceFarm said:**
> Hahaha. I got Doom 3 working 100% though. I'm really impressed with Linux...I think I'll try Prey or Quake 4 next!

But I do agree weblordpepe, It'd be much easier if games were to be installed that way.

Quake 4 runs great on my Linux system :D, the installation routine is a tad annoying (bloody Rocky Ridge or whatever CD protection) but once installed it is smooth as butter.

---

### Post by citybird on 2007-11-20
ok for all the absolute newbs out there (like me) that need step by step hand holding (like me) do this...

download doom3-linux-1.3.1.1304.x86.run from the official website or torrent.
open a terminal window
sudo sh ./doom3-linux-1.3.1.1304.x86.run 

sudo cp /media/cdrom0/Setup/Data/base/*.pk4 /usr/local/games/doom3/base/.
(note your cdrom dir may differ from mine "cdrom0")

now after this i get the message"wrong game DLL API version"

whut up?

---

### Post by citybird on 2007-11-20
> **weblordpepe said:**
> All that they need to create is:
.run file (a script installer for any linux OS)
.deb
.rpm

If they create a deb or rpm, then it is like 2 seconds to create another package from it using alien. It is not a bourdon to create multiple package formats. Many many software vendors do, even vendors which release software on a monthly cycle (e.g. Wine).

Game developers release something - what - every 3 years? It is not a problem for game developers to release multiple package formats.

They need to provide a .deb or .rpm.

i agree

---

### Post by Sockerdrickan on 2007-11-20
> **citybird said:**
> ok for all the absolute newbs out there (like me) that need step by step hand holding (like me) do this...

download doom3-linux-1.3.1.1304.x86.run from the official website or torrent.
open a terminal window
sudo sh ./doom3-linux-1.3.1.1304.x86.run 

sudo cp /media/cdrom0/Setup/Data/base/*.pk4 /usr/local/games/doom3/base/.
(note your cdrom dir may differ from mine "cdrom0")

now after this i get the message"wrong game DLL API version"

whut up?
or even easier don't use the ./ after sh :)

---

### Post by Morton's Red Stapler on 2007-11-20
ok, i got the game installed and all the fils copied over, but when i hit alt-f2 and try to run the game, it opens, then closes right away. i used synaptic to get all the libs etc that i need to run the game, but to no avail. i tried to open it in console and got this ```
jd@jd-laptop:~$ sudo doom3
DOOM 1.3.1.1304 linux-x86 Jan 16 2007 21:58:02
found interface lo - loopback
found interface eth1 - 
------ Initializing File System ------
Loaded pk4 /usr/local/games/doom3/base/game00.pk4 with checksum 0xf07eb555
Loaded pk4 /usr/local/games/doom3/base/game01.pk4 with checksum 0x51c6981f
Loaded pk4 /usr/local/games/doom3/base/game02.pk4 with checksum 0xf3ec6f7
Loaded pk4 /usr/local/games/doom3/base/game03.pk4 with checksum 0x5d4230ea
Loaded pk4 /usr/local/games/doom3/base/pak000.pk4 with checksum 0x28d208f1
Loaded pk4 /usr/local/games/doom3/base/pak001.pk4 with checksum 0x40244be0
Loaded pk4 /usr/local/games/doom3/base/pak002.pk4 with checksum 0xc51ecdcd
Loaded pk4 /usr/local/games/doom3/base/pak003.pk4 with checksum 0xcd79d028
Loaded pk4 /usr/local/games/doom3/base/pak004.pk4 with checksum 0x765e4f8b
Loaded pk4 /usr/local/games/doom3/base/pak005.pk4 with checksum 0x8ffc3621
Loaded pk4 /usr/local/games/doom3/base/pak006.pk4 with checksum 0x95b65ab
Loaded pk4 /usr/local/games/doom3/base/pak007.pk4 with checksum 0x666bdb3c
Loaded pk4 /usr/local/games/doom3/base/pak008.pk4 with checksum 0x23ae5993
Current search path:
/home/jd/.doom3/base
/usr/local/games/doom3/base
/usr/local/games/doom3/base/pak008.pk4 (3 files)
/usr/local/games/doom3/base/pak007.pk4 (38 files)
/usr/local/games/doom3/base/pak006.pk4 (48 files)
/usr/local/games/doom3/base/pak005.pk4 (63 files)
/usr/local/games/doom3/base/pak004.pk4 (5137 files)
/usr/local/games/doom3/base/pak003.pk4 (4676 files)
/usr/local/games/doom3/base/pak002.pk4 (6120 files)
/usr/local/games/doom3/base/pak001.pk4 (8972 files)
/usr/local/games/doom3/base/pak000.pk4 (2698 files)
/usr/local/games/doom3/base/game03.pk4 (2 files)
/usr/local/games/doom3/base/game02.pk4 (2 files)
/usr/local/games/doom3/base/game01.pk4 (2 files)
/usr/local/games/doom3/base/game00.pk4 (2 files)
game DLL: 0x0 in pak: 0x0
Addon pk4s:
file system initialized.
--------------------------------------
----- Initializing Decls -----
------------------------------
------- Initializing renderSystem --------
using ARB renderSystem
renderSystem initialized.
--------------------------------------
5206 strings read from strings/english.lang
Couldn't open journal files
execing editor.cfg
execing default.cfg
couldn't exec DoomConfig.cfg
couldn't exec autoexec.cfg
5206 strings read from strings/english.lang
----- Initializing Sound System ------
sound system initialized.
--------------------------------------
----- R_InitOpenGL -----
Setup X display connection
dlopen(libGL.so.1)
Initializing OpenGL display
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
XFree86-VidModeExtension not available
Xlib:  extension "XFree86-DGA" missing on display ":1.0".
Failed to detect DGA DirectVideo Mouse
Using 8/8/8 Color bits, 8 Alpha bits, 24 depth, 8 stencil display.
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
GL_RENDERER: ATI MOBILITY RADEON X700
GL_EXTENSIONS: GL_ARB_multitexture GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_transpose_matrix GL_EXT_abgr GL_EXT_blend_color GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod_bias 

------- Input Initialization -------
XKB extension: compile time 0x1:0x0, runtime 0x1:0x0: OK
XKB extension present on server ( 0x1:0x0 )
------------------------------------
dlopen(libasound.so.2)
asoundlib version: 1.0.14a
Alsa is available
------ Alsa Sound Initialization -----
opened Alsa PCM device default for playback
device buffer size: 5644 frames ( 22576 bytes )
allocated a mix buffer of 16384 bytes
--------------------------------------
...using GL_ARB_multitexture
...using GL_ARB_texture_env_combine
...using GL_ARB_texture_cube_map
...using GL_ARB_texture_env_dot3
...using GL_ARB_texture_env_add
X..GL_ARB_texture_non_power_of_two not found
X..GL_ARB_texture_compression not found
X..GL_EXT_texture_filter_anisotropic not found
...using GL_EXT_texture_lod
...using GL_1.4_texture_lod_bias
X..GL_EXT_shared_texture_palette not found
X..GL_EXT_texture3D not found
X..GL_EXT_stencil_wrap not found
X..GL_NV_register_combiners not found
X..GL_EXT_stencil_two_side not found
X..GL_ATI_separate_stencil not found
X..GL_ATI_fragment_shader not found
X..GL_ATI_text_fragment_shader not found
X..GL_ARB_vertex_buffer_object not found
X..GL_ARB_vertex_program not found
X..GL_ARB_fragment_program not found
X..EXT_depth_bounds_test not found
---------- R_NV20_Init ----------
Not available.
----------- R200_Init -----------
Not available.
---------- R_ARB2_Init ----------
Not available.
----- R_ReloadARBPrograms -----
glprogs/test.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/test.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/interaction.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/bumpyEnvironment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/ambientLight.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/shadow.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/R200_interaction.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_bumpAndLight.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_specularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/nv20_diffuseAndSpecularColor.vp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_VERTEX_PROGRAM_ARB not available
glprogs/environment.vfp: GL_FRAGMENT_PROGRAM_ARB not available
glprogs/arbVP_glasswarp.txt: File not found
glprogs/arbFP_glasswarp.txt: File not found
-------------------------------
WARNING: vertex array range in virtual memory (SLOW)
signal caught: Segmentation fault
si_code 1
Trying to exit gracefully..
Shutting down sound hardware
----------- Alsa Shutdown ------------
close pcm
dlclose
--------------------------------------
idRenderSystem::Shutdown()
jd@jd-laptop:~$ 
jd@jd-laptop:~$ 

```
any help here would be really appreciated 
my system specs are:
Acer laptop w/
2gig pentiumM
1 gig ram
ati x700mobility 128m
running ubuntu 7.10

---

### Post by happysmileman on 2007-11-20
I'm thinking of getting Doom3 and am wondering whether I can expect it to go fast on Linux, since it was developed for Windows and then just ported.

I have 512MB RAM and a 64MB graphics card, and a 2.6Ghz processor so that's enough to run it, but when I tried it on Windows I had to turn down a lot of the graphics to get it working smoothly, would it be as fast on Linux as Windows?

I'm asking because I assume people here have tried it on both

---

### Post by Sockerdrickan on 2007-11-21
Might be -5fps

---

### Post by weblordpepe on 2007-11-23
> **happysmileman said:**
> I'm thinking of getting Doom3 and am wondering whether I can expect it to go fast on Linux, since it was developed for Windows and then just ported.

It was actually developed to be cross-platform. There's a video from 2001 showing it running on OSX. We always knew Doom 3 would be coming out for linux. If you're using an ATi graphics card then you'll need to be running the proprietary drivers.

Otherwise it should be normal.

---

