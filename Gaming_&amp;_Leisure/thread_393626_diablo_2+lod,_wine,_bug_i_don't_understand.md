---
title: "diablo 2+lod, wine, bug i don't understand"
date: 2007-03-25
forum: Gaming &amp; Leisure
---

### Post by lunaz on 2007-03-25
i'm starting to follow a guide to install d2 & lod, so i installed wine  & typed winecfg in the command line & it worked ok i guess, till i clicked on the audio tab. the windows looking thing crashed & the terminal thew up on me. :) note that i haven't installed d2 yet, just sudo aptitude update & install wine, then winecfg:

```

gail@gail-badassness:~$ winecfg
wine: creating configuration directory '/home/gail/.wine'...
Failed to open the service control manager.
fixme:ole:ITypeInfo_fnRelease destroy child objects
wine: '/home/gail/.wine' created successfully.
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** winecfg.exe: free(): invalid pointer: 0x7c2d27a8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7da58bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7da5a44]
/usr/bin/../lib/libstdc++.so.6(_ZdlPv+0x21)[0x7e8cefc1]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts11readTypeSeqINS_12InterfaceDefEEEvRNS_6BufferERSt6vectorIT_SaIS5_EE+0x18e)[0x73baa71e]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts9ModuleDef8readTypeERNS_6BufferE+0x56)[0x73b7bf66]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts9ModuleDefC1ERNS_6BufferE+0xa4)[0x73b7c1be]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts10IDLFileReg7startupEv+0xb5)[0x73b7c279]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts14StartupManager7startupEv+0x3e)[0x73b5f742]
/usr/bin/../lib/libmcop.so.1(_ZN4Arts10DispatcherC1EPNS_9IOManagerENS0_11StartServerE+0x80a)[0x73b9200c]
/usr/lib/libartscbackend.so.0(arts_backend_init+0x8d)[0x73e86e6f]
/usr/bin/../lib/libartsc.so.0(arts_init+0x231)[0x7c45f76c]
/usr/bin/../lib/wine/winearts.drv.so(ARTS_WaveInit+0x72)[0x7bfe7652]
/usr/bin/../lib/wine/winearts.drv.so(ARTS_DriverProc+0x96)[0x7bfe31e6]
/usr/bin/../lib/wine/winmm.dll.so[0x7e63351a]
/usr/bin/../lib/wine/winmm.dll.so(DRIVER_TryOpenDriver32+0xe9)[0x7e633889]
/usr/bin/../lib/wine/winmm.dll.so(OpenDriver+0x1cf)[0x7e633c3f]
/usr/bin/../lib/wine/winmm.dll.so(OpenDriverA+0x45)[0x7e633d05]
/usr/bin/../lib/wine/winecfg.exe.so[0x7edb4e38]
/usr/bin/../lib/wine/winecfg.exe.so(AudioDlgProc+0x2cf)[0x7edb6a6f]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6fb4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea719f8]
/usr/bin/../lib/wine/user32.dll.so(WINPROC_CallDlgProcW+0x5a)[0x7ea7523a]
/usr/bin/../lib/wine/user32.dll.so(DefDlgProcW+0x8a)[0x7ea0745a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6fb4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea7027e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea75333]
/usr/bin/../lib/wine/user32.dll.so[0x7ea3e458]
/usr/bin/../lib/wine/user32.dll.so(SendMessageTimeoutW+0x1a0)[0x7ea42bc0]
/usr/bin/../lib/wine/user32.dll.so(SendMessageW+0x50)[0x7ea42c30]
/usr/bin/../lib/wine/user32.dll.so[0x7ea0c841]
/usr/bin/../lib/wine/user32.dll.so(CreateDialogIndirectParamAorW+0x36)[0x7ea0d8d6]
/usr/bin/../lib/wine/user32.dll.so(CreateDialogIndirectParamW+0x41)[0x7ea0d921]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e71ea42]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e71f46f]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e72141f]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6fb4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea719f8]
/usr/bin/../lib/wine/user32.dll.so(WINPROC_CallDlgProcW+0x5a)[0x7ea7523a]
/usr/bin/../lib/wine/user32.dll.so(DefDlgProcW+0x8a)[0x7ea0745a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6fb4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea7027e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea75333]
/usr/bin/../lib/wine/user32.dll.so[0x7ea3e458]
/usr/bin/../lib/wine/user32.dll.so(SendMessageTimeoutW+0x1a0)[0x7ea42bc0]
/usr/bin/../lib/wine/user32.dll.so(SendMessageW+0x50)[0x7ea42c30]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e735d4a]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e73a9dc]
/usr/bin/../lib/wine/user32.dll.so[0x7ea6fb4a]
/usr/bin/../lib/wine/user32.dll.so[0x7ea7027e]
/usr/bin/../lib/wine/user32.dll.so(CallWindowProcW+0x53)[0x7ea75333]
/usr/bin/../lib/wine/user32.dll.so(DispatchMessageW+0x153)[0x7ea3e953]
/usr/bin/../lib/wine/user32.dll.so(IsDialogMessageW+0xfb)[0x7ea0de3b]
/usr/bin/../lib/wine/comctl32.dll.so[0x7e71c2f0]
/usr/bin/../lib/wine/comctl32.dll.so(PropertySheetW+0x25d)[0x7e7229fd]
/usr/bin/../lib/wine/winecfg.exe.so(WinMain+0x364)[0x7edbcd34]
/usr/bin/../lib/wine/winecfg.exe.so(main+0xa3)[0x7edc1f43]
/usr/bin/../lib/wine/winecfg.exe.so[0x7edc1e6b]
/usr/bin/../lib/wine/kernel32.dll.so[0x7ee99ede]
/usr/bin/../lib/libwine.so.1[0xb7e9a567]
======= Memory map: ========
00000000-00110000 ---p 00000000 00:00 0 
00110000-00190000 rw-p 00110000 00:00 0 
00190000-00220000 ---p 00190000 00:00 0 
00220000-00221000 rw-p 00220000 00:00 0 
00221000-00230000 ---p 00221000 00:00 0 
00230000-00231000 ---p 00230000 00:00 0 
00231000-00340000 rw-p 00231000 00:00 0 
00340000-00348000 ---p 00340000 00:00 0 
00348000-00350000 ---p 00348000 00:00 0 
00350000-00370000 ---p 00350000 00:00 0 
00370000-00380000 rw-p 00370000 00:00 0 
00380000-60000000 ---p 00380000 00:00 0 
739bf000-739f2000 r-xp 00000000 08:01 7196327    /usr/lib/libkmedia2_idl.so.1.0.0
739f2000-73a00000 rw-p 00033000 08:01 7196327    /usr/lib/libkmedia2_idl.so.1.0.0
73a00000-73a19000 r-xp 00000000 08:01 7194781    /usr/lib/libvorbis.so.0.3.1
73a19000-73a27000 rw-p 00019000 08:01 7194781    /usr/lib/libvorbis.so.0.3.1
73a27000-73a32000 r-xp 00000000 08:01 7194783    /usr/lib/libvorbisenc.so.2.0.2
73a32000-73b21000 rw-p 0000a000 08:01 7194783    /usr/lib/libvorbisenc.so.2.0.2
73b21000-73b23000 rw-p 73b21000 00:00 0 
73b23000-73bb9000 r-xp 00000000 08:01 7196328    /usr/lib/libmcop.so.1.0.0
73bb9000-73bc7000 rw-p 00096000 08:01 7196328    /usr/lib/libmcop.so.1.0.0
73bc7000-73c11000 r-xp 00000000 08:01 7194113    /usr/lib/libXt.so.6.0.0
73c11000-73c15000 rw-p 00049000 08:01 7194113    /usr/lib/libXt.so.6.0.0
73c15000-73c2a000 r-xp 00000000 08:01 7194150    /usr/lib/libaudio.so.2.4
73c2a000-73c2b000 rw-p 00014000 08:01 7194150    /usr/lib/libaudio.so.2.4
73c2b000-73c49000 r-xp 00000000 08:01 7194152    /usr/lib/libaudiofile.so.0.0.2
73c49000-73c4b000 rw-p 0001e000 08:01 7194152    /usr/lib/libaudiofile.so.0.0.2
73c4b000-73cd3000 r-xp 00000000 08:01 7196319    /usr/lib/libartsflow_idl.so.1.0.0
73cd3000-73cfb000 rw-p 00087000 08:01 7196319    /usr/lib/libartsflow_idl.so.1.0.0
73cfb000-73d45000 r-xp 00000000 08:01 7196331    /usr/lib/libsoundserver_idl.so.1.0.0
73d45000-73d5c000 rw-p 00049000 08:01 7196331    /usr/lib/libsoundserver_idl.so.1.0.0
73d5c000-73e5b000 r-xp 00000000 08:01 7196318    /usr/lib/libartsflow.so.1.0.0
73e5b000-73e79000 rw-p 000fe000 08:01 7196318    /usr/lib/libartsflow.so.1.0.0
73e79000-73e7e000 rw-p 73e79000 00:00 0 
73e7e000-73e8b000 r-xp 00000000 08:01 7196315    /usr/lib/libartscbackend.so.0.0.0
73e8b000-73e8e000 rw-p 0000d000 08:01 7196315    /usr/lib/libartscbackend.so.0.0.0
73e8e000-73f1f000 r-xp 00000000 08:01 7194375    /usr/lib/libglib-2.0.so.0.1200.4
73f1f000-73f20000 rw-p 00091000 08:01 7194375    /usr/lib/libglib-2.0.so.0.1200.4
73f20000-7bf00000 rw-s 00003000 00:0d 9274       /dev/dri/card0
7bf00000-7bf02000 r-xp 00000000 08:01 3686415    /usr/bin/wine-pthread
7bf02000-7bf03000 rw-p 00001000 08:01 3686415    /usrwine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...
Killed
gail@gail-badassness:~$ 

```

dunno what it is or even if it means anything, but if i have any more issues i'll post it.
edit: k i clicked install.exe & it dont know what to do, so i tried to find wine in that program list, nope.

next i tried opening up winecfg again & adding install.exe or setup.exe then opening in 'winxp', still nothing somes up other than this during 1 try.

```

gail@gail-badassness:~$ winecfg
fixme:shell:ShellView_OnNotify LVN_KEYDOWN key=0x00000090
fixme:shell:ShellView_OnNotify LVN_KEYDOWN key=0x00000011
gail@gail-badassness:~$ winecfg

```

---

### Post by hikaricore on 2007-03-26
What version of wine are you using?

```
wine --version
```

The most recent version can always be found here:

[http://wine.budgetdedicated.com/](http://wine.budgetdedicated.com/)


Just a note, I've had issue with the audio tab on almost every system I've installed Wine on.
This doesn't mean that it won't work, but it could cause issues if you have sound problems
and need to change the driver.

To install you'll need to goto the directory of the mounted CD Example:

```

cd /media/cdrom
wine install.exe

```

The cd/dvd mount point will vary from system to system, so make sure you're in the right path.

And I know you won't want to do everything in linux from command line, but trust me here.
When first installing anything with wine, you'll probably want to do so from the command line
so you can see what's happening incase of errors.

You can find more about installing diablo 2 in the [wine application database]("http://appdb.winehq.org"), and by searching
this forum.  I know there's atleast a couple nice walk-thrus around here.

---

### Post by lunaz on 2007-03-26
well i was following [http://ubuntuforums.org/showthread.php?t=362457](http://ubuntuforums.org/showthread.php?t=362457)

thanks to ur post i finally got it to start the install process using command line but now it dont work cuz i cant eject the cdrom, typing wine eject dont help, i still cant dbl click on the install.exe & still cant choose wine from a program list; i can only seem to run it from the command line. i have the latest from that site u gave me. i verified by doing wine --version.

is there a walk thru that actually explains all this? and gets all the steps? :P

---

### Post by hikaricore on 2007-03-26
It's normal to run wine from the command line or launchers. It's isn't a gui based application.

You may want to try copying the contents of all of the diablo 2 cds to a temporary folder on your desktop, this avoids having to swap cds, as they won't always eject properly.

Once you understand more clearly how wine works you'll be able to install and run applications directly, but for now I still suggest command line.

---

### Post by lunaz on 2007-03-27
thx to somebody in #winehq i got d2 & xpac installed & patched by using

cd ~ && wine "d:\install.exe"

but now i can't get d2loader working ;( it says something about mpq files & i copied the d2xmusic,sound,video,speech etc type files to wine's program files/diablo ii directory.

---

### Post by lunaz on 2007-03-29
well, i got it installed, and it starts up w/o a cd. for me that's progress. :)

only issue is i get this error. (attach2) i tried to go to a console to quit the program cuz i couldnt see a mouse but when i press ctrl alt f1 it throws up on me (attach2)... i think its got to do w/ envy but i thot i got rid of that.

next post is my crash log for today :P i dunno what it means but its got something to do with fog.dll will mess more after dinner. that screen thing in attach1 has me worried....do i have to reinstall?

edit: ok i cant get my crash log in here cuz its the size of a novel.. if anyone wants it let me know.

---

### Post by Albi on 2007-03-29
Um, does it work if you DON'T use d2loader?

---

### Post by lunaz on 2007-03-29
ya, i can play single player. i was able to get to uswest a couple days ago but now i see an error: can't identify app version.

---

### Post by Dr Gryme on 2007-06-01
i have a problem very similar to this, if not the same. If there was a solution to this problem, and it was not posted, please send it to me. If there isn't a solution yet, then i am giving you a big frown. ...:( PLease PM me the solution when it comes up! thanks guys!

---

### Post by lunaz on 2007-06-03
going off memory:

it ended up i didn't have my ati x800 card installed right, once i got that fixed, i was able to play w/o the major graphic lag. to get d2 loader working i ran the cd key refiller. i don't know where to get it anymore but i can attach it here. that program has made it thru 3 computers :P

let me know if u need more instructions then that, i'll hopefully remember more when i'm awake. :P

---

