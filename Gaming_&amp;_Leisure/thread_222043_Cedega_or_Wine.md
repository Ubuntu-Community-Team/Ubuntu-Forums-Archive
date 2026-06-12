---
title: "Cedega or Wine?"
date: 2006-07-24
forum: Gaming &amp; Leisure
---

### Post by mcvos on 2006-07-24
The main reason I was still using Windows was for playing games, but recently my Windows went belly-up, and a friend told me that Wine is now very good at running even very recent games, so I finally decided to install linux again. My eye fell on Ubuntu, and now I'm here, checking out the game forum.

First thing that surprised my is that the stickies don't seem to be mentioning Wine at all. There is a link to a site that mentions Cedega, which I'd never heard of, but which does seem to support most of my favourite games.

So what's the consensus here? Use Wine or Cedega? Or are some games better with Wine, and others with Cedega?

Note that I'm a complete newbie with regards to gaming on Wine. (And I haven't gotten Ubuntu to treat my nvidia card properly yet, but that's a totally different issue for a different forum.)

---

### Post by Paerez on 2006-07-24
I don't have much experience with the two, but here is my knowledge on the subject:

wine: free and handles lots of windows apps and older games

cedega: special version of wine with lots of directX support and plays more versions of games, but costs $5 a month.

So basically, try wine, but if its a new game it probably won't work, so then google to see if it works in wine. If it doesn't you'd have to use cedega.

---

### Post by Carrots171 on 2006-07-24
You can also get a free version of Cedega called cvscedega. Unfortunately, it's unsupported and harder to install. There is, however, [a script that can help you install cvscedega]("http://www.ubuntuforums.org/showthread.php?t=193814"). 

The Wine and Cedega websites both have sections telling you what's compatible and what's not.

[The Wine Application Database]("http://appdb.winehq.org/")
[The Cedega Games Database]("http://transgaming.org/gamesdb/")

---

### Post by Paerez on 2006-07-24
am I correct in saying that cvscedega does not come with point2play? And also, does cvscedega run all the same games as cedega?

---

### Post by mcvos on 2006-07-24
Hm... according to [http://appdb.winehq.org/appbrowse.php?iCatId=55]("http://appdb.winehq.org/appbrowse.php?iCatId=55") wine even supports Oblivion, which is supposed to be the most graphically demanding game on the market. If it can handle that, I'd expect it to handle anything. Unfortunately PGIIISE is not on the list of supported games, despite being much older.

Edit: Turns out Wine+Oblivion is rated "garbage". So being listed doesn't mean much. Cedega rates it 2/5 for playability, for that matter. So just being listed doesn't mean much.

---

### Post by Paerez on 2006-07-24
no it doesn't. It's on the list because someone mentioned it. The official play status is "Garbage"
[http://appdb.winehq.org/appview.php?iVersionId=4596](http://appdb.winehq.org/appview.php?iVersionId=4596)

EDIT: My bad that was for the newest version, an older version of wine gets a "Bronze", which is ok.

---

### Post by abowman on 2006-07-24
What games are you looking to play?

---

### Post by vem0m on 2006-07-24
some work better in wine for some people and some work better for other people in cedega it varies per person/per computer not per app between ppl as it might run better on cedega for one person and better in wine for another for the same game all i can conclude with is that it depends.

---

### Post by handy on 2006-07-24
> **mcvos said:**
> The main reason I was still using Windows was for playing games, but recently my Windows went belly-up, and a friend told me that Wine is now very good at running even very recent games, so I finally decided to install linux again. My eye fell on Ubuntu, and now I'm here, checking out the game forum.

First thing that surprised my is that the stickies don't seem to be mentioning Wine at all. There is a link to a site that mentions Cedega, which I'd never heard of, but which does seem to support most of my favourite games.

So what's the consensus here? Use Wine or Cedega? Or are some games better with Wine, and others with Cedega?

Note that I'm a complete newbie with regards to gaming on Wine. (And I haven't gotten Ubuntu to treat my nvidia card properly yet, but that's a totally different issue for a different forum.)

You can get [Automatix]("http://www.ubuntuforums.org/showthread.php?t=177646") & use it to install whatever takes your fancy from the 48 options.  One of which sets up your nVidia card.  Automatix is great for new & old hands alike, reliable fast & simple.

You can get the [Cedega_demo]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Simulation/Cedega-9843.shtml") here.  It is not the latest version, by the way.

Cedega costs a minimum subscription of $15.50 US. for 3 months.  You can cancel & continue using any of the versions that you have installed.  If you download the Cedega.deb(s) & the engine.deb You can reinstall without having to resubscribe.

CVSCedega, is not the same as the commercial version of Cedega. There is NO copy protection support in the CVS version. Nor is there the sweet GUI: Point2Play, which by the way is becoming a lot more powerful & friendly as Cedega develops.  CVScedega is not for beginners & is quite limited in what it can run.

Don't get me wrong, I only use Cedega because I can not play Guild Wars on linux any other way. As soon as I can play GW on Wine I will dump Cedega as quick as a flash!

I do agree with those that consider Cedega extortionware, due to the Transgaming marketing strategy, which = you keep on paying, every month, forever...

Wine is usually not as easy as Cedega to set up & get a game working on.  Some games like Guild Wars are still not playable under Wine.  

As far as consensus is concerned, there are extreme veiws on each side & everything in the middle! :KS

Use whatever works for you to play the games that you want to play.  Search the forums for particular game titles to see how they run on Wine or Cedega.

If you haven't looked [here]("http://ubuntuforums.org/showthread.php?t=85573") yet, there is lots more info' on specific games.

Also, the Quake/Doom engines have multiple games that run natively on Linux, as do the Unreal based games.

Have fun & welcome... :KS

---

### Post by mcvos on 2006-07-25
Thanks for all the great feedback. I'll check out both wine and cedega.

The kind of games I like to play are mostly turn-based strategy (Panzer General and 4X games), and CRPG (usually turn-based). And I tend to play older games mostly. For example, the moment Oblivion was in the shops, I started playing Morrowind. So with a bit of luck, wine will usually be good enough for me. But I'll definitely have a look at Cedega.

---

### Post by Perfect Storm on 2006-07-25
There's a wine loki installer for Morrowind: [http://liflg.org/?catid=7&gameid=38](http://liflg.org/?catid=7&gameid=38)

Save it to your Desktop, then to the terminal;

```
cd Desktop
sudo sh morrowind_1.2.0722-english.run
```

Make sure your graphic card is set up for 3D acc.

The intro might be choppy, but the game works great.

---

### Post by mcvos on 2006-07-30
Do I understand correctly that this installs or copies Morrowind to my linux partition? Is it possible to keep Morrowind in my old Windows partition and run it from there?

Hm... I've installed it, and when I try to run, I get a "Unable to find a CD-ROM/DVD drive on this computer" error, which is kind of weird, considering the game has just been installed from cdrom.

Which reminds me, will the no-cd patch work?

---

### Post by mcvos on 2006-07-30
nocd patch seems to work fine. No complaints about the CD anymore. Instead, I get this error:

```

Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7e54da0 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
11804: old priority 0, new priority 5
mcv@rhovanion:~$ Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7e54da0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:b7e54da0 ESP:7fb9f200 EBP:7fb9f204 EFLAGS:00010206(   - 00      - RIP1)
 EAX:7fd79378 EBX:7eb48af4 ECX:7fd79377 EDX:00000000
 ESI:7fd79378 EDI:7fd79350
Stack dump:
0x7fb9f200:  00000000 7fb9f444 7eaf4bce 7fd79378
0x7fb9f210:  00000000 00000148 7ff999d7 7fb9f294
0x7fb9f220:  7fcf0000 7fcf0000 7ff8df80 7f953920
0x7fb9f230:  00090000 7fd79240 7ff8d95d 7fd790d8
0x7fb9f240:  7ffd51fc 7fb9f2a4 7ff9b836 7fcf0020
0x7fb9f250:  0000ffff 7fb9f294 7fc946dc 7f953920
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0xb7e54da0 strcpy+0x20 in libc.so.6 (0xb7e54da0)
  2 0x7eaf4bce in wined3d (+0x24bce) (0x7eaf4bce)
  3 0x7eaf8917 IWineD3DImpl_GetAdapterIdentifier+0x1f2 in wined3d (0x7eaf8917)
  4 0x7f53d46e IDirect3D8Impl_GetAdapterIdentifier+0x7d in d3d8 (0x7f53d46e)
  5 0x0069ce27 in morrowind (+0x29ce27) (0x0069ce27)
  6 0x00000001 (0x00000001)
  7 0x7f53d8e8 IDirect3D8Impl_AddRef in d3d8 (0x7f53d8e8)
0xb7e54da0 strcpy+0x20 in libc.so.6: movzbl     0x0(%edx),%eax
Modules:
Module  Address                 Debug info      Name (85 modules)
PE      0x00400000-007d4000     Export          morrowind
PE      0x30000000-3006e000     Deferred        binkw32
PE      0x780c0000-78121000     Deferred        msvcp60
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e4ef000-7e520000     Deferred        uxtheme<elf>
  \-PE  0x7e500000-7e520000     \               uxtheme
ELF     0x7e63b000-7e650000     Deferred        midimap<elf>
  \-PE  0x7e640000-7e650000     \               midimap
ELF     0x7e766000-7e78c000     Deferred        msacm32<elf>
  \-PE  0x7e770000-7e78c000     \               msacm32
ELF     0x7e78c000-7e7a4000     Deferred        msacm<elf>
  \-PE  0x7e790000-7e7a4000     \               msacm
ELF     0x7e7a4000-7e7e8000     Deferred        wineoss<elf>
  \-PE  0x7e7b0000-7e7e8000     \               wineoss
ELF     0x7e806000-7e80f000     Deferred        libxcursor.so.1
ELF     0x7e80f000-7e82b000     Deferred        imm32<elf>
  \-PE  0x7e820000-7e82b000     \               imm32
ELF     0x7e82b000-7e833000     Deferred        libxrender.so.1
ELF     0x7e833000-7e8b6000     Deferred        winex11<elf>
  \-PE  0x7e840000-7e8b6000     \               winex11
ELF     0x7e8b6000-7e8d5000     Deferred        libexpat.so.1
ELF     0x7e8d5000-7e903000     Deferred        libfontconfig.so.1
ELF     0x7e903000-7e917000     Deferred        libz.so.1
ELF     0x7e917000-7e980000     Deferred        libfreetype.so.6
ELF     0x7e980000-7ea40000     Deferred        comctl32<elf>
  \-PE  0x7e990000-7ea40000     \               comctl32
ELF     0x7ea56000-7eab7000     Deferred        msvcrt<elf>
  \-PE  0x7ea70000-7eab7000     \               msvcrt
ELF     0x7eab7000-7eb4a000     Export          wined3d<elf>
  \-PE  0x7ead0000-7eb4a000     \               wined3d
ELF     0x7ebe2000-7f333000     Deferred        libglcore.so.1
ELF     0x7f333000-7f3a9000     Deferred        libglu.so.1
ELF     0x7f3a9000-7f421000     Deferred        libgl.so.1
ELF     0x7f421000-7f507000     Deferred        libx11.so.6
ELF     0x7f507000-7f51f000     Deferred        libice.so.6
ELF     0x7f51f000-7f549000     Export          d3d8<elf>
  \-PE  0x7f530000-7f549000     \               d3d8
ELF     0x7f549000-7f59b000     Deferred        dsound<elf>
  \-PE  0x7f560000-7f59b000     \               dsound
ELF     0x7f59b000-7f5dc000     Deferred        dinput<elf>
  \-PE  0x7f5b0000-7f5dc000     \               dinput
ELF     0x7f5dc000-7f5f0000     Deferred        dinput8<elf>
  \-PE  0x7f5e0000-7f5f0000     \               dinput8
ELF     0x7f5f0000-7f604000     Deferred        lz32<elf>
  \-PE  0x7f600000-7f604000     \               lz32
ELF     0x7f604000-7f61d000     Deferred        version<elf>
  \-PE  0x7f610000-7f61d000     \               version
ELF     0x7f61d000-7f6a5000     Deferred        winmm<elf>
  \-PE  0x7f630000-7f6a5000     \               winmm
ELF     0x7f6a5000-7f6c4000     Deferred        iphlpapi<elf>
  \-PE  0x7f6b0000-7f6c4000     \               iphlpapi
ELF     0x7f6c4000-7f70d000     Deferred        rpcrt4<elf>
  \-PE  0x7f6d0000-7f70d000     \               rpcrt4
ELF     0x7f70d000-7f79e000     Deferred        ole32<elf>
  \-PE  0x7f720000-7f79e000     \               ole32
ELF     0x7f79e000-7f7de000     Deferred        advapi32<elf>
  \-PE  0x7f7b0000-7f7de000     \               advapi32
ELF     0x7f8b3000-7f964000     Deferred        gdi32<elf>
  \-PE  0x7f8d0000-7f964000     \               gdi32
ELF     0x7f964000-7fa90000     Deferred        user32<elf>
  \-PE  0x7f980000-7fa90000     \               user32
ELF     0x7fba3000-7fbb0000     Deferred        libxext.so.6
ELF     0x7fbb1000-7fbb6000     Deferred        libxxf86vm.so.1
ELF     0x7fbb6000-7fbbb000     Deferred        libxxf86dga.so.1
ELF     0x7fbee000-7fcf0000     Deferred        kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe04000     Deferred        libxfixes.so.3
ELF     0x7fe04000-7fe0e000     Deferred        libgcc_s.so.1
ELF     0x7fe0e000-7fe18000     Deferred        libnss_files.so.2
ELF     0x7fe18000-7fe21000     Deferred        libnss_nis.so.2
ELF     0x7fe21000-7fe36000     Deferred        libnsl.so.1
ELF     0x7fe36000-7fe3f000     Deferred        libnss_compat.so.2
ELF     0x7fe3f000-7fe42000     Deferred        libxrandr.so.2
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Deferred        ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7de0000-b7de2000     Deferred        libnvidia-tls.so.1
ELF     0xb7de8000-b7deb000     Deferred        libdl.so.2
ELF     0xb7deb000-b7f1a000     Export          libc.so.6
ELF     0xb7f1a000-b7f2c000     Deferred        libpthread.so.0
ELF     0xb7f2c000-b7f2f000     Deferred        libxau.so.6
ELF     0xb7f37000-b7f51000     Deferred        libwine.so.1
ELF     0xb7f54000-b7f6a000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) Z:\usr\local\games\morrowind\Morrowind.exe
        00000009    0 <==

```

I've seen a similar error before, and someone suggested that Xlib:  'extension "GLX" missing on display ":0.0"' means that something is wrong with my graphics driver, I've followed all the (extremely detailed and complex) instructions on [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")
(including the special case for the GeForce4 MX 440),
and I thought everything worked fine. But not for wine, it appears.

Is this still the right place to look for a solution?

---

### Post by ZylGadis on 2006-07-31
Morrowind does not work with vanilla wine, period. It produces the infamous "Unknown stencil" message.
Judging by comments on winehq, it is possible that it works with a newly compiled cvswine after a certain patch is applied.

---

