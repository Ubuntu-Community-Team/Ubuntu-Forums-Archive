---
title: "Kontact and Kopete have suddenly started to eat my memory :-("
date: 2008-05-05
forum: Desktop Environments
---

### Post by Marshlurker on 2008-05-05
Hi fellow Kubuntu Users,


as of today some of my KDE application, for example Kontact and Kopete, don't start normally anymore. They don't show anything on the screen, but start eating away at my memory until the system is completely clogged by heavy swapping and the application finally crashes.
Kmail is an exception insofar as showing the normal window; but  it starts eating all my memory like the others when i click on one of my mail folders.
I have tried the following:
```

apt-get check <- no problems found there
apt-get autoremove <- no packages to be removed
```
Since the problems occurs when invoking different programs i think the real problem might be in one of the libraries used by all of these programs. But sadly i dont know how to find that one...

The system is a Kubuntu 7.10 updated to 8.04, which i have been running for some days now without the abovementioned problems.
The versions of the installed software packages are:
```

Qt: 3.3.8b
KDE: 3.5.9
Kontact: 1.2.9
Kopete: 0.12.7
KMail: 1.9.9
KAddressBook: 3.5.9
KOrganizer: 3.5.9
```

My sources.lst contains (cleaned of comments):
```

deb http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy main restricted
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-security main restricted
deb http://de.archive.ubuntu.com/ubuntu/ hardy-security universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-security universe
deb http://de.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-updates multiverse universe
deb-src http://de.archive.ubuntu.com/ubuntu/ hardy-security multiverse
deb http://de.archive.ubuntu.com/ubuntu/ hardy-proposed restricted main multiverse universe
```

So i hope that somebody shares with me (and people who might have the same problem) the wisdom what causes the problem, and the means to get rid of it. If i can assist by supplying addition information i will of course gladly do so.


Thanks in advance to all the people who will help me on this!



PS: It might be completely unrelated, but when i press the buttons of my keyboard that i linked to amarok / speedcalc the kded-daemon crashes (SIGSEV).

---

### Post by Xiong Chiamiov on 2008-05-05
Does the problem persist after reboots, and is it only sometimes, or always?  Do you notice anything unusual if you run them from Konsole?

---

### Post by Marshlurker on 2008-05-06
> **Xiong Chiamiov said:**
> Does the problem persist after reboots, and is it only sometimes, or always?  Do you notice anything unusual if you run them from Konsole?

The problem persists and it occurs always. When running from konsole, only kmail gives me some output:
```
WeaverThreadLogger: thread (ID: 1) suspended.
WeaverThreadLogger: thread (ID: 2) suspended.
WeaverThreadLogger: thread (ID: 3) suspended.
WeaverThreadLogger: thread (ID: 4) suspended.
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "move_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "copy_message_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "jump_to_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "cancel"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "inc_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "dec_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "select_current_folder"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "inc_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "dec_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "select_current_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "edit"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "delete"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "post_message"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "use_template"
kdecore (KAction): WARNING: KAction::plugAccel(): call to deprecated action.
kdecore (KAction): WARNING: KAction::plugAccel( kacc = 0x81ea630 ): KAccel object already contains an action name "display_message"
%USERNAME@desktop:~$ Sorry, couldn't chdir to /home/$USERNAME/.crm114

crm: *UNTRAPPABLE ERROR*
 Couldn't open the file:  mailreaver.crm
Sorry, but I can't recover from that.
This happened at line 0 of file mailreaver.crm

```

---

### Post by Marshlurker on 2008-05-06
I have tested some more.
```

strace kopete
strace korganizer

```
indicate that the error happens when reading from the file "/etc/ld.so.cache".

I tried
```
sudo ldconfig
```
but it didnt help.

Any ideas what i could check next?

---

### Post by Xiong Chiamiov on 2008-05-06
Not that I think it would work, but have you tried renaming the cache file?  It should (I think) be recreated on reboot, but, hey, try the easy things first...

---

### Post by Marshlurker on 2008-05-07
> **Xiong Chiamiov said:**
> Not that I think it would work, but have you tried renaming the cache file?  It should (I think) be recreated on reboot, but, hey, try the easy things first...

I renamed the cache file but the problem persists. The Programs 
BUT: I have a new set of straces to play around with. ;-)
AND: I noticed that i should consider the "close(5)" syscalls in the straces in finding out wich file causes the problem... ^^

---

### Post by Marshlurker on 2008-05-07
As i mentioned in my earlier Post i made an Error in checking my straces for hints. I missed that the number 5 was assigned to new targets some times in the strace. So here is a snippet of a new strace, notice the last line, it is the last thing that is printed on the screen prior to memory use going through the roof:
```
socket(PF_FILE, SOCK_STREAM, 0)         = 5
uname({sys="Linux", node="desktop", ...}) = 0
connect(5, {sa_family=AF_FILE, path="/tmp/.ICE-unix/dcop10994-1210184009"}, 38) = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
write(5, "\0\1\0\0\0\0\0\0", 8)         = 8
read(5, "\0\1\0\0\0\0\0\0", 8)          = 8
access("/home/$USERNAME/.ICEauthority", R_OK) = 0
open("/home/$USERNAME/.ICEauthority", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0600, st_size=386, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f60000
read(6, "\0\3ICE\0\0\0001local/desktop:/tmp/.ICE"..., 4096) = 386
read(6, "", 4096)                       = 0
close(6)                                = 0
munmap(0xb7f60000, 4096)                = 0
write(5, "\0\2\1\1\6\0\0\0\0\0\0\0\0\0\0\0\3\0MIT\0\0\0\3\0001.0"..., 56) = 56
read(5, "\0\3\0\0\1\0\0\0", 8)          = 8
read(5, "\0\0\0\0\0\0\0\0", 8)          = 8
access("/home/$USERNAME/.ICEauthority", R_OK) = 0
open("/home/$USERNAME/.ICEauthority", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0600, st_size=386, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f60000
read(6, "\0\3ICE\0\0\0001local/desktop:/tmp/.ICE"..., 4096) = 386
close(6)                                = 0
munmap(0xb7f60000, 4096)                = 0
write(5, "\0\4\1\1\3\0\0\0\20\0\0\0\0\0\0\0\325zi\315M\277L6\26\3"..., 32) = 32
read(5, "\0\6\0\0\2\0\0\0", 8)          = 8
read(5, "\3\0MIT\0\0\0\3\0001.0\0\0\0", 16) = 16
fcntl64(5, F_SETFL, O_WRONLY)           = 0
access("/home/$USERNAME/.ICEauthority", R_OK) = 0
open("/home/$USERNAME/.ICEauthority", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0600, st_size=386, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f60000
read(6, "\0\3ICE\0\0\0001local/desktop:/tmp/.ICE"..., 4096) = 386
read(6, "", 4096)                       = 0
close(6)                                = 0
munmap(0xb7f60000, 4096)                = 0
write(5, "\0\7\1\0\7\0\0\0\1\1\0\0\0\0\0\0\4\0DCOPL6\3\0KDE)\254"..., 64) = 64
read(5, "\0\3\0\0\1\0\0\0", 8)          = 8
read(5, "\0\0MIT\0\0\0", 8)             = 8
access("/home/$USERNAME/.ICEauthority", R_OK) = 0
open("/home/$USERNAME/.ICEauthority", O_RDONLY) = 6
fstat64(6, {st_mode=S_IFREG|0600, st_size=386, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f60000
read(6, "\0\3ICE\0\0\0001local/desktop:/tmp/.ICE"..., 4096) = 386
close(6)                                = 0
munmap(0xb7f60000, 4096)                = 0
write(5, "\0\4\1\0\3\0\0\0\20\0\0\0\0\0\0\0\325zi\315M\277L6\26\3"..., 32) = 32
read(5, "\0\10\0\2\2\0\0\0", 8)         = 8
read(5, "\3\0KDE\0\0\0\3\0002.0\0\0\0", 16) = 16
getsockopt(5, SOL_SOCKET, SO_PEERCRED, "\362*\0\0\350\3\0\0\350\3\0\0", [12]) = 0
getuid32()                              = 1000
write(5, "\1\2\1\0I\0\0\0\0\0\0\0", 12) = 12
write(5, "\0\0\0\0\0\0\0\vDCOPServer\0\0\0\0\1\0\0\0\0\25regi"..., 53) = 53
write(5, "\0\0\0\20anonymous-11597\0", 20) = 20
read(5, "\2\3\0\0028\0\0\0", 8)         = 8
read(5, "\214\0\0\0", 4)                = 4
read(5, "\0\0\0\vDCOPServer\0\0\0\0\0\0\0\0\tQCString\0"..., 56) = 56
write(5, "\1\2\1\0]\0\0\0\214\0\0\0", 12) = 12
write(5, "\0\0\0\20anonymous-11597\0\0\0\0\vDCOPServ"..., 82) = 82
write(5, "\0\0\0\7kopete\0", 11)        = 11
read(5, "\2\3\0\0024\0\0\0", 8)         = 8
read(5, "\214\0\0\0", 4)                = 4
read(5, "\0\0\0\vDCOPServer\0\0\0\0\20anonymous-115"..., 52) = 52
write(5, "\1\2\1\0e\0\0\0\2\0\0\0", 12) = 12
write(5, "\0\0\0\20anonymous-11597\0\0\0\0\7kopete\0\0"..., 64) = 64
write(5, "\0\0\0\r/home/$USERNAME\0\0\0\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 37) = 37
read(5, "\2\5\0\2#\0\0\0", 8)           = 8
read(5, "\2\0\0\0", 4)                  = 4
read(5, "\0\0\0\7kopete\0\0\0\0\20anonymous-11597\0\0"..., 35) = 35
read(5, 
```
I checked with "strace korganizer" and "strace kaddressbook", wich also stop output when reading from
```
connect(5, {sa_family=AF_FILE, path="/tmp/.ICE-unix/dcop10994-1210184009"}, 38) = 0
```
So if i read that right, my problem should have to do with DCOP, doesnt it?
Any hints are welcome... ;-)

---

### Post by Marshlurker on 2008-05-09
I found the source of the problem. I can't explain how it happened, i can't explain how it affected korganizer, but the fact remains:
My problem occured because
~/.kde/share/apps/kabc/std.vcf
was corrupted. When i opened it in kwrite i noticed that it contained about 200MB of crap where a german Umlaut schould have been. So i deleted this "Information" and that solved the problem.
Everything runs smoothly again.

---

### Post by Marshlurker on 2008-05-09
Thanks to you Xiong Chiamiov for making me try more, without answers i might as well have reinstalled the system. Which would have been futile... ;-)

---

### Post by Xiong Chiamiov on 2008-05-09
Eh, hey, I just don't believe in reinstalls unless you have a *very* good reason.  I'm glad that you figured it out, and of course, that I was able to help in a very indirect way.

EDIT: right after, my roommate linked me [this]("http://tech.slashdot.org/tech/08/05/09/1258229.shtml").  Heh.

---

