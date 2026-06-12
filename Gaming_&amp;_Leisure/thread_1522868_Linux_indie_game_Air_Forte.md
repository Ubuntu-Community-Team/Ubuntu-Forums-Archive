---
title: "Linux indie game: Air Forte"
date: 2010-07-02
forum: Gaming &amp; Leisure
---

### Post by Brendon Chung on 2010-07-02
Hi all,

I'm developing my first Linux game, "Air Forte". I have the game running on my local machine, but would love to get some real-world stress testing on my latest build. Any tips or suggestions are welcome!

[img]http://www.blendogames.com/airforte/images/screenshot1a.jpg[/img] [img]http://www.blendogames.com/airforte/images/screenshot2a.jpg[/img]  [img]http://www.blendogames.com/airforte/images/screenshot4a.jpg[/img]

Link to the game: [http://www.blendogames.com/dev/airfortedemo_v2.tar.gz](http://www.blendogames.com/dev/airfortedemo_v2.tar.gz)

Thanks!

---

### Post by su-37 on 2010-07-02
Nice Game. Little tricky with it not being full screen though.

---

### Post by Brendon Chung on 2010-07-02
Good point - I'll change it to start the game in fullscreen by default.

In the meantime, there should currently be a Fullscreen option in the video settings menu.

---

### Post by Yneth on 2010-07-03
I downloaded the game and when i do try to run it, it doesn't go beyond the 'Loading' screen, it freezes there and i am compelled to terminate it, or am i not doing it the right way??

---

### Post by Brendon Chung on 2010-07-03
@Yneth - The game shouldn't require any special setup, it should just work out of the box.

Are you running on a 64-bit system?  I made the game with 32-bit binaries and libraries; I assumed this was compatible with 64-bit systems.

Would you mind executing the game from the Terminal and copy/pasting me the output? There should be good debug info in there.

---

### Post by Yarui on 2010-07-03
Doesn't run on my system.  I'm currently on a non-ubuntu machine, so if you have only tested it on ubuntu so far that could be something to keep in mind.

EDIT:  From your previous comment it could be because the OS I'm running at the moment is 64 bit.

---

### Post by Yneth on 2010-07-03
My apologies for my previous post, the game does run post the loading screen, i just had to wait for sometime. It was a lil jerky initially but then when i restarted the game, it was alright, nonetheless it was fun playing, i also noticed that when i change the resolution to full screen, and as i exit the game, my whole screen goes blank, or its just a white screen, and i am forced to reboot manually, this happened a couple of times and the third time i got a  msg stating " Ubuntu is running on low graphics" and i had the following options 
-continue running on low graphics,
- configure graphics manually,
- restart X.
and restarting X failed and the machine rebooted automatically.

This does not happen while on the windowed mode.

---

### Post by Yneth on 2010-07-03
And i also wish there would be an option to save the game between levels, strictly in my opinion :)

---

### Post by Yarui on 2010-07-03
> **Yneth said:**
> And i also wish there would be an option to save the game between levels, strictly in my opinion :)
I get the idea this game is still in development.  Save games seem like the kind of feature that is added toward the end of development.

---

### Post by renkinjutsu on 2010-07-03
Question: Are you going to release your game with static libraries? You'll have a bigger download, but it should save a bunch of compatibility issues right?

---

### Post by Yarui on 2010-07-03
> **renkinjutsu said:**
> Question: Are you going to release your game with static libraries? You'll have a bigger download, but it should save a bunch of compatibility issues right?
Perhaps, it's quite possible the reason I'm not able to run it is because I don't have some dependency installed.

---

### Post by Brendon Chung on 2010-07-03
@Yarui - Can you run the game from the Terminal and copy/paste me the output?  Hopefully the debug will give a hint to why it's not running on your system. Also, you're right - I only tested it on Ubuntu; what are you using?

@Yneth - the game should automatically save whenever you complete a level. The next time you start the game, it should start off at whatever level you were at. Is that broken?

@renkinjutsu - I'm trying to avoid static libraries for license reasons.

Also, a general question - are special steps needed to make this work on 64-bit sytems? I was under the impression that keeping all the binaries/libraries 32-bit would make the game compatible for either system.

---

### Post by Yneth on 2010-07-03
> @Yneth - the game should automatically save whenever you complete a level. The next time you start the game, it should start off at whatever level you were at. Is that broken?

No, That works fine, also could you please tell me if the problem with the full-screen is only with my computer or does it occur to others as well?

---

### Post by Yneth on 2010-07-03
> @Yneth - the game should automatically save whenever you complete a level. The next time you start the game, it should start off at whatever level you were at. Is that broken?
No, That works fine, also could you please tell me if the problem with the full-screen is only with my computer or does it occur to others as well?

---

### Post by Yarui on 2010-07-03
> **Brendon Chung said:**
> @Yarui - Can you run the game from the Terminal and copy/paste me the output?  Hopefully the debug will give a hint to why it's not running on your system. Also, you're right - I only tested it on Ubuntu; what are you using?
I'm using Arch right now, and since it's a very minimal OS it's likely I don't have some dependency installed.  If I run the program from nautilus nothing happens at all, when I run it from the terminal I get this output:
```
$ ./AirForte

Mono-INFO: Assembly Loader probing location: './mscorlib.dll'.
Mono-INFO: Image addref mscorlib 0x96aaa60 -> /home/owner/Desktop/AirForteDemo/data/mscorlib.dll 0x96a9f68: 2

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/mscorlib.dll.so: /home/owner/Desktop/AirForteDemo/data/mscorlib.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: './mscorlib.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/mscorlib.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/mscorlib/mscorlib.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/mscorlib/mscorlib.config'.
Mono-INFO: Assembly mscorlib 0x96aaa60 added to domain release.exe, ref_count=1

Mono-INFO: Config attempting to parse: '/etc/mono/config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/config'.
Mono-INFO: Assembly Loader probing location: 'release.exe'.
Mono-INFO: Unloading image release.exe [0x96e4908].
Mono-INFO: Image addref release 0x96e4838 -> release.exe 0x96a8e98: 4

Mono-INFO: Assembly release 0x96e4838 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module release.exe.so: release.exe.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: 'release.exe'.
Mono-INFO: Config attempting to parse: 'release.exe.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/release/release.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/release/release.config'.
Mono-INFO: Assembly Loader probing location: 'release.exe'.
Mono-INFO: Unloading image release.exe [0x96e4bf0].
Mono-INFO: AOT failed to load AOT module release.exe.so: release.exe.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Ref addref release 0x96e4838 -> mscorlib 0x96aaa60: 2

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll'.
Mono-INFO: Image addref System.Windows.Forms 0x96f2dd0 -> /home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll 0x96c1190: 2

Mono-INFO: Assembly System.Windows.Forms 0x96f2dd0 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll.so: /home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/System.Windows.Forms.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/System.Windows.Forms/System.Windows.Forms.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/System.Windows.Forms/System.Windows.Forms.config'.
Mono-INFO: Assembly Ref addref release 0x96e4838 -> System.Windows.Forms 0x96f2dd0: 2

Mono-INFO: Assembly Ref addref System.Windows.Forms 0x96f2dd0 -> mscorlib 0x96aaa60: 3

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/System.dll'.
Mono-INFO: Image addref System 0x96f9e70 -> /home/owner/Desktop/AirForteDemo/data/System.dll 0x96f94a0: 2

Mono-INFO: Assembly System 0x96f9e70 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/System.dll.so: /home/owner/Desktop/AirForteDemo/data/System.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/System.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/System.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/System/System.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/System/System.config'.
Mono-INFO: Assembly Ref addref System.Windows.Forms 0x96f2dd0 -> System 0x96f9e70: 2

Mono-INFO: Assembly Ref addref System 0x96f9e70 -> mscorlib 0x96aaa60: 4

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/System.Drawing.dll'.
Mono-INFO: Image addref System.Drawing 0x9706500 -> /home/owner/Desktop/AirForteDemo/data/System.Drawing.dll 0x9705d98: 2

Mono-INFO: Assembly System.Drawing 0x9706500 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/System.Drawing.dll.so: /home/owner/Desktop/AirForteDemo/data/System.Drawing.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/System.Drawing.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/System.Drawing.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/System.Drawing/System.Drawing.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/System.Drawing/System.Drawing.config'.
Mono-INFO: Assembly Ref addref System.Windows.Forms 0x96f2dd0 -> System.Drawing 0x9706500: 2

Mono-INFO: Assembly Ref addref System.Drawing 0x9706500 -> mscorlib 0x96aaa60: 5

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/Accessibility.dll'.
Mono-INFO: Image addref Accessibility 0x9708038 -> /home/owner/Desktop/AirForteDemo/data/Accessibility.dll 0x970b128: 2

Mono-INFO: Assembly Accessibility 0x9708038 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/Accessibility.dll.so: /home/owner/Desktop/AirForteDemo/data/Accessibility.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/Accessibility.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/Accessibility.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/Accessibility/Accessibility.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/Accessibility/Accessibility.config'.
Mono-INFO: Assembly Ref addref System.Windows.Forms 0x96f2dd0 -> Accessibility 0x9708038: 2

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll'.
Mono-INFO: Image addref sfmlnet-audio 0x970ba78 -> /home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll 0x9719f08: 2

Mono-INFO: Assembly sfmlnet-audio 0x970ba78 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll.so: /home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-audio.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/sfmlnet-audio/sfmlnet-audio.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/sfmlnet-audio/sfmlnet-audio.config'.
Mono-INFO: Assembly Ref addref release 0x96e4838 -> sfmlnet-audio 0x970ba78: 2

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll'.
Mono-INFO: Image addref sfmlnet-window 0x971a790 -> /home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll 0x971ac30: 2

Mono-INFO: Assembly sfmlnet-window 0x971a790 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll.so: /home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-window.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/sfmlnet-window/sfmlnet-window.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/sfmlnet-window/sfmlnet-window.config'.
Mono-INFO: Assembly Ref addref sfmlnet-audio 0x970ba78 -> sfmlnet-window 0x971a790: 2

Mono-INFO: Assembly Ref addref sfmlnet-window 0x971a790 -> mscorlib 0x96aaa60: 6

Mono-INFO: Assembly Loader probing location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll'.
Mono-INFO: Image addref sfmlnet-graphics 0x971b410 -> /home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll 0x971b9f8: 2

Mono-INFO: Assembly sfmlnet-graphics 0x971b410 added to domain release.exe, ref_count=1

Mono-INFO: AOT failed to load AOT module /home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll.so: /home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll.so: cannot open shared object file: No such file or directory

Mono-INFO: Assembly Loader loaded assembly from location: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll'.
Mono-INFO: Config attempting to parse: '/home/owner/Desktop/AirForteDemo/data/sfmlnet-graphics.dll.config'.
Mono-INFO: Config attempting to parse: '/etc/mono/assemblies/sfmlnet-graphics/sfmlnet-graphics.config'.
Mono-INFO: Config attempting to parse: '/home/owner/.mono/assemblies/sfmlnet-graphics/sfmlnet-graphics.config'.
Mono-INFO: Assembly Ref addref release 0x96e4838 -> sfmlnet-graphics 0x971b410: 2

Mono-INFO: Assembly Ref addref sfmlnet-graphics 0x971b410 -> sfmlnet-window 0x971a790: 3

Mono-INFO: Assembly Ref addref release 0x96e4838 -> System 0x96f9e70: 3

Mono-INFO: Assembly Ref addref sfmlnet-graphics 0x971b410 -> mscorlib 0x96aaa60: 7

Mono-INFO: DllImport attempting to load: 'csfml-graphics'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'csfml-graphics'.
Mono-INFO: DllImport error loading library 'csfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'libcsfml-graphics'.
Mono-INFO: DllImport error loading library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport attempting to load: 'csfml-graphics'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'csfml-graphics'.
Mono-INFO: DllImport error loading library 'csfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'libcsfml-graphics'.
Mono-INFO: DllImport error loading library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: Assembly Ref addref release 0x96e4838 -> sfmlnet-window 0x971a790: 4

Mono-INFO: DllImport attempting to load: 'csfml-graphics'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'csfml-graphics'.
Mono-INFO: DllImport error loading library 'csfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'libcsfml-graphics'.
Mono-INFO: DllImport error loading library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport attempting to load: 'csfml-graphics'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'csfml-graphics'.
Mono-INFO: DllImport error loading library 'csfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library: 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libcsfml-graphics.so'.
Mono-INFO: DllImport error loading library 'libGL.so.1: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading: 'libcsfml-graphics'.
Mono-INFO: DllImport error loading library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libcsfml-graphics: cannot open shared object file: No such file or directory'.
Mono-INFO: Assembly Ref addref System.Drawing 0x9706500 -> System 0x96f9e70: 4

Mono-INFO: Assembly Loader probing location: '/usr/lib/mono/gac/UIAutomationWinforms/1.0.0.0__f4ceacb585d99812/UIAutomationWinforms.dll'.
Mono-INFO: Assembly Loader probing location: '/usr/lib/UIAutomationWinforms.dll'.
Mono-INFO: Assembly Loader probing location: '/usr/lib/mono/gac/UIAutomationWinforms/1.0.0.0__f4ceacb585d99812/UIAutomationWinforms.exe'.
Mono-INFO: Assembly Loader probing location: '/usr/lib/UIAutomationWinforms.exe'.
Mono-INFO: Assembly Loader probing location: 'content/libraries/UIAutomationWinforms.dll'.
Mono-INFO: DllImport attempting to load: 'libc.so.6'.
Mono-INFO: DllImport loading location: 'libc.so.6.so'.
Mono-INFO: DllImport error loading library: 'libc.so.6.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libc.so.6.so'.
Mono-INFO: DllImport error loading library './libc.so.6.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libc.so.6'.
Mono-INFO: Searching for 'uname'.
Mono-INFO: Probing 'uname'.
Mono-INFO: Found as 'uname'.
Mono-INFO: DllImport attempting to load: 'gdiplus.dll'.
Mono-INFO: DllImport loading location: 'libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library: 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'gdiplus.dll'.
Mono-INFO: DllImport error loading library 'gdiplus.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libgdiplus.so'.
Mono-INFO: DllImport error loading library: 'libgdiplus.so: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libgdiplus.so'.
Mono-INFO: DllImport error loading library './libgdiplus.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'gdiplus'.
Mono-INFO: DllImport error loading library 'gdiplus: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library: 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libgdiplus.dll'.
Mono-INFO: DllImport error loading library 'libgdiplus.dll: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libgdiplus.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport attempting to load: 'gdiplus.dll'.
Mono-INFO: DllImport loading location: 'libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library: 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'gdiplus.dll'.
Mono-INFO: DllImport error loading library 'gdiplus.dll: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libgdiplus.so'.
Mono-INFO: DllImport error loading library: 'libgdiplus.so: wrong ELF class: ELFCLASS64'.
Mono-INFO: DllImport loading library: './libgdiplus.so'.
Mono-INFO: DllImport error loading library './libgdiplus.so: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'gdiplus'.
Mono-INFO: DllImport error loading library 'gdiplus: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading location: 'libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library: 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading library: './libgdiplus.dll.so'.
Mono-INFO: DllImport error loading library 'libtiff.so.4: cannot open shared object file: No such file or directory'.
Mono-INFO: DllImport loading: 'libgdiplus.dll'.
Mono-INFO: DllImport error loading library 'libgdiplus.dll: cannot open shared object file: No such file or directory'.

(release.exe:6799): Mono-WARNING **: DllImport unable to load library 'libgdiplus.dll: cannot open shared object file: No such file or directory'.

Unhandled Exception: System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.WindowsFormsSynchronizationContext ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.ThemeEngine ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.Windows.Forms.ThemeWin32Classic ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.Drawing.KnownColors ---> System.TypeInitializationException: An exception was thrown by the type initializer for System.Drawing.GDIPlus ---> System.DllNotFoundException: gdiplus.dll
  at (wrapper managed-to-native) System.Drawing.GDIPlus:GdiplusStartup (ulong&,System.Drawing.GdiplusStartupInput&,System.Drawing.GdiplusStartupOutput&)
  at System.Drawing.GDIPlus..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Drawing.KnownColors..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Drawing.Color.get_Black () [0x00000] 
  at System.Windows.Forms.ThemeWin32Classic..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.ThemeEngine..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.SystemInformation.get_MenuAccessKeysUnderlined () [0x00000] 
  at System.Windows.Forms.Control..ctor () [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.Control:.ctor ()
  at System.Windows.Forms.WindowsFormsSynchronizationContext..cctor () [0x00000] 
  --- End of inner exception stack trace ---
  at System.Windows.Forms.Control..ctor () [0x00000] 
  at System.Windows.Forms.ScrollableControl..ctor () [0x00000] 
  at System.Windows.Forms.ContainerControl..ctor () [0x00000] 
  at System.Windows.Forms.Form..ctor () [0x00000] 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon, Boolean displayHelpButton) [0x00000] 
  at System.Windows.Forms.MessageBox+MessageBoxForm..ctor (IWin32Window owner, System.String text, System.String caption, MessageBoxButtons buttons, MessageBoxIcon icon) [0x00000] 
  at (wrapper remoting-invoke-with-check) System.Windows.Forms.MessageBox/MessageBoxForm:.ctor (System.Windows.Forms.IWin32Window,string,string,System.Windows.Forms.MessageBoxButtons,System.Windows.Forms.MessageBoxIcon)
  at System.Windows.Forms.MessageBox.Show (System.String text, System.String caption, MessageBoxButtons buttons) [0x00000] 
  at BlendoEngine.Game1.Initialize () [0x00000] 
  at BlendoEngine.Game0.Main () [0x00000] 
./airfortelinux: line 8:  6799 Killed                  MONO_LOG_LEVEL="debug" ./airfortelinux.exe "$@"
```

> Also, a general question - are special steps needed to make this work on 64-bit sytems? I was under the impression that keeping all the binaries/libraries 32-bit would make the game compatible for either system.
I think this really just depends on the specific program and what libraries it uses.  I have never dealt with anything like this so I can't give you any expert advice, but I know there have been cases where I had to install extra 32 bit libraries to run some 32 bit programs.  It could be that I just don't have the proper 32 bit libraries installed right now.

---

### Post by pieman711 on 2010-07-03
pieman@pieman-desktop:~/Documents/Gmaes/AirForteDemo$ ./AirForte 
./airfortelinux.exe: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.11' not found (required by ./airfortelinux.exe)

I got this output from terminal.
I am using an old version of Ubuntu, will upgrade any day now! I had a quick look in synaptic and add/remove programs but couldn't find GLIBC_2.11

---

### Post by Brendon Chung on 2010-07-03
@Yneth - I'm running on Ubuntu 10.04, and I haven't run across that issue yet.

@pieman711 - What version of Ubuntu are you running on?

@Yarui - Ok, the "wrong ELF class: ELFCLASS64" seems to indicate the game is searching for 32-bit dependencies, but is only finding 64-bit dependencies. Looks like I'll need to include more dependencies in the package.

A general question - what are the most common Linux distros I should test? I'm new to Linux development and still learning the ropes  :- )

---

### Post by Yarui on 2010-07-03
You won't necessarily need to include them in the package, I would just recommend writing a readme or something that lists off all the necessary dependencies.

---

### Post by Perfect Storm on 2010-07-03
> **Brendon Chung said:**
> 
A general question - what are the most common Linux distros I should test? I'm new to Linux development and still learning the ropes  :- )

Properly: 
Ubuntu
Debian
OpenSuse
Fedora

should cover your bases.

---

### Post by silentrock on 2010-07-03
Its a really cool game with awsome and intersting GFX, you should add a Wolf to the animals ;) 

Its really good keep the good work!

---

### Post by pieman711 on 2010-07-04
I'm still on 8.10. I'm planning on upgrading after my exams (next weekend) I don't want to do it now and risk loosing  all of my revision material/computer to revise on!

---

### Post by =CrAzYG33K= on 2010-07-04
Played the demo and just loved it. :KS

Though didn't try the full-screen, but didn't find any bugs as of yet.
Os : Ubuntu 10.04 (32-bit)

---

