---
title: "Sound went dead suddenly and a reboot doesn't help at all!"
date: 2006-09-21
forum: Desktop Environments
---

### Post by motin on 2006-09-21
Hmmm. My sound just ran away somewhere in a Skype-session a few hours ago... And it didn't come back after reboot!

Basically I installed a few audio-relevant (?) packages (in case it matters...):
ardour-i686
ardour-gtk
arson
autotrace

Then went on doing stuff as usual (listening to Amarok, wasting time everywhere except for on school and work). 

I wanted to call me friend on Skype so I played stop in Amarok (apparently necessary...) and called'im up. In the middle of a skype-call the sound went dead, Skype bitched around said there was a problem with MY sound device... so rude. [-X 

Amarok didn't play any more as well (xine complained), and after a reboot everything was just the same! No amarok, no skype. 

I got this error when trying aplay:
```
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
aplay: main:544: audio open error: No such file or directory

```

So I checked the /dev/dsp - it was gone, but there was a new /dev/dsp1 instead, so I made a symlink in between to patch it up. And then Skype worked again!

But not Amarok... and aplay is still showing that message!

What can I do?

Btw, here is an strace:
```
motin@laptop:~$ LANGUAGE=C strace aplay
execve("/usr/bin/aplay", ["aplay"], [/* 28 vars */]) = 0
uname({sys="Linux", node="laptop", ...}) = 0
brk(0)                                  = 0x8054000
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f89000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
old_mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f87000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=100764, ...}) = 0
old_mmap(NULL, 100764, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f6e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libasound.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\362\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=737088, ...}) = 0
old_mmap(NULL, 740164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eb9000
old_mmap(0xb7f69000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaf000) = 0xb7f69000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@3\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=136368, ...}) = 0
old_mmap(NULL, 138800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e97000
old_mmap(0xb7eb8000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20000) = 0xb7eb8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=8204, ...}) = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7e96000
old_mmap(NULL, 11016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e93000
old_mmap(0xb7e95000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7e95000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=86580, ...}) = 0
old_mmap(NULL, 71064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e81000
old_mmap(0xb7e90000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0xb7e90000
old_mmap(0xb7e91000, 5528, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e91000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220O\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1232784, ...}) = 0
old_mmap(NULL, 1238972, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d52000
old_mmap(0xb7e77000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x125000) = 0xb7e77000
old_mmap(0xb7e7e000, 10172, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e7e000
close(3)                                = 0
old_mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d51000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7d518e0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
munmap(0xb7f6e000, 100764)              = 0
set_tid_address(0xb7d51928)             = 15313
rt_sigaction(SIGRTMIN, {0xb7e853b0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7e85430, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
_sysctl({{CTL_KERN, KERN_VERSION, 0, 20d91, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0}, 2, 0xbfa9c1cc, 43, (nil), 0}) = 0
brk(0)                                  = 0x8054000
brk(0x8075000)                          = 0x8075000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f86000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2586
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f86000, 4096)                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_IDENTIFICATION", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_IDENTIFICATION", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=345, ...}) = 0
mmap2(NULL, 345, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f86000
close(3)                                = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/gconv/gconv-modules", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=45568, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f85000
read(3, "# GNU libc iconv configuration.\n"..., 4096) = 4096
read(3, "lias\tJS//\t\t\tJUS_I.B1.002//\nalias"..., 4096) = 4096
read(3, "ule\tINTERNAL\t\tISO-8859-3//\t\tISO8"..., 4096) = 4096
read(3, "lias\tISO-IR-199//\t\tISO-8859-14//"..., 4096) = 4096
read(3, "\t\tto\t\t\tmodule\t\tcost\nalias\tCSEBCD"..., 4096) = 4096
read(3, "ule\t\tcost\nalias\tCP284//\t\t\tIBM284"..., 4096) = 4096
read(3, "lias\tCP864//\t\t\tIBM864//\nalias\t86"..., 4096) = 4096
read(3, "module\tIBM937//\t\tINTERNAL\t\tIBM93"..., 4096) = 4096
read(3, "\tEUC-JP//\nalias\tUJIS//\t\t\tEUC-JP/"..., 4096) = 4096
read(3, "module\t\tcost\nalias\tISO-IR-143//\t"..., 4096) = 4096
read(3, "-BOX//\nmodule\tISO_10367-BOX//\t\tI"..., 4096) = 4096
read(3, "module\tINTERNAL\t\tEUC-JISX0213//\t"..., 4096) = 512
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f85000, 4096)                = 0
futex(0xb7e7dc4c, FUTEX_WAKE, 2147483647) = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_MEASUREMENT", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_MEASUREMENT", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=23, ...}) = 0
mmap2(NULL, 23, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f85000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_TELEPHONE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_TELEPHONE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=57, ...}) = 0
mmap2(NULL, 57, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f84000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_ADDRESS", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_ADDRESS", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=127, ...}) = 0
mmap2(NULL, 127, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f83000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_NAME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_NAME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=62, ...}) = 0
mmap2(NULL, 62, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f82000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_PAPER", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_PAPER", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=34, ...}) = 0
mmap2(NULL, 34, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f81000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_MESSAGES", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
close(3)                                = 0
open("/usr/lib/locale/sv_SE.utf8/LC_MESSAGES/SYS_LC_MESSAGES", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f80000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_MONETARY", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_MONETARY", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=290, ...}) = 0
mmap2(NULL, 290, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f7f000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_COLLATE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_COLLATE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=880098, ...}) = 0
mmap2(NULL, 880098, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c7a000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_TIME", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_TIME", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2391, ...}) = 0
mmap2(NULL, 2391, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f7e000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_NUMERIC", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=54, ...}) = 0
mmap2(NULL, 54, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f7d000
close(3)                                = 0
open("/usr/lib/locale/sv_SE.UTF-8/LC_CTYPE", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/sv_SE.utf8/LC_CTYPE", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=208464, ...}) = 0
mmap2(NULL, 208464, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7c47000
close(3)                                = 0
stat64("/usr/share/alsa/alsa.conf", {st_mode=S_IFREG|0644, st_size=7501, ...}) = 0
open("/usr/share/alsa/alsa.conf", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=7501, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c46000
read(3, "#\n#  ALSA library configuration "..., 4096) = 4096
read(3, "if cards.pcm.iec958\npcm.modem ca"..., 4096) = 3405
brk(0x8096000)                          = 0x8096000
read(3, "", 4096)                       = 0
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7c46000, 4096)                = 0
futex(0xb7e95b04, FUTEX_WAKE, 2147483647) = 0
access("/etc/asound.conf", R_OK)        = 0
open("/etc/asound.conf", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=219, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c46000
read(3, "pcm.card0 {\ntype hw\ncard 0\n}\n\npc"..., 4096) = 219
read(3, "", 4096)                       = 0
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7c46000, 4096)                = 0
access("/home/motin/.asoundrc", R_OK)   = -1 ENOENT (No such file or directory)
semget(1025, 1, IPC_CREAT|0600)         = 851971
semop(851971, 0xbfa9bee2, 2)            = 0
shmget(1025, 384, IPC_CREAT|0600)       = 4948002
shmat(4948002, 0, 0)                    = 0xb7c46000
mlock(0xb7c46000, 384)                  = 0
shmctl(4948002, IPC_64|IPC_STAT, 0xbfa9bd38) = 0
open("/dev/snd/controlC0", O_RDONLY)    = 3
close(3)                                = 0
open("/dev/snd/controlC0", O_RDWR)      = 3
ioctl(3, USBDEVFS_CONTROL, 0xbfa9ba38)  = 0
ioctl(3, 0x40045532, 0xbfa9ba34)        = 0
open("/dev/snd/pcmC0D0p", O_RDWR|O_NONBLOCK) = -1 ENOENT (No such file or directory)
close(3)                                = 0
write(2, "ALSA lib pcm_dmix.c:819:(snd_pcm"..., 44ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) ) = 44
write(2, "unable to open slave", 20unable to open slave)    = 20
write(2, "\n", 1
)                       = 1
shmdt(0)                                = -1 EINVAL (Invalid argument)
shmdt(0xb7c46000)                       = 0
shmctl(4948002, IPC_64|IPC_STAT, 0xbfa9bd3c) = 0
shmctl(4948002, IPC_64|IPC_RMID, 0)     = 0
semctl(851971, 0, IPC_64|IPC_RMID, 0xbfa9bd84) = 0
write(2, "aplay: main:544: ", 17aplay: main:544: )       = 17
write(2, "audio open error: No such file o"..., 43audio open error: No such file or directory) = 43
write(2, "\n", 1
)                       = 1
exit_group(1)                           = ?

```

---

### Post by dlehman on 2006-09-21
that strace means nothing to me I'm not sure that this will help but, 

go to System>Preferences>Sound and make sure you have the right sound device selected at the bottom 
also open your mixer I right click on the icon in my task bar to get to it there is probably another menu option, anyway make sure you are not muted and the volume is at an appropriate level, I keep it at about 80% 

I hope it is as easy as this but it may be something deeper and you will have to call in an expert.

---

### Post by motin on 2006-09-22
> **dlehman said:**
> that strace means nothing to me I'm not sure that this will help but, 

go to System>Preferences>Sound and make sure you have the right sound device selected at the bottom 
also open your mixer I right click on the icon in my task bar to get to it there is probably another menu option, anyway make sure you are not muted and the volume is at an appropriate level, I keep it at about 80% 

I hope it is as easy as this but it may be something deeper and you will have to call in an expert.

Actually it helped a lot! But far from solved it I am afraid. The thing is: My USB keyboard was selected as the preferred sound device! I switched back to Intel HCI6 and tried again - no change. I went back and found the USB keyboard back as the preferred sound device so I plugged the keyboard out and tried again, and now I get another response (still sound doesn't work though...):

```
motin@laptop:~$ LANGUAGE=C aplay test.wav
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
aplay: main:544: audio open error: No such device

```

I guess this has to do with me booting with my USB keyboard plugged in (never done that before). I'll try rebooting without it...

---

### Post by motin on 2006-09-22
Look at that... A reboot without the USB Keyboard (a M-AUDIO Keystation 49e) solved it. 

Strange it started out like this in the middle of a Skype call as well. 

It sure as hell is a bug somewhere. I'll check if I can repeat it again and if it still is the same in Edgy, and then report it. 

Thanks man :) Often it doesn't take an expert... Just some nifty thinking.

---

### Post by crazedgremlin on 2006-11-26
I'm in a similar situation... My sound isn't working and I just put my fancy new wireless keyboard in yesterday.  I'll try a reboot without my keyboard in. :)

---

### Post by crazedgremlin on 2006-11-26
Yess!!  You guys are geniuses!!!
I wonder if there is a way we can report this bug? :-k 

it's a wee bit strange though..  Why are usb keyboards interfering with sound cards

---

