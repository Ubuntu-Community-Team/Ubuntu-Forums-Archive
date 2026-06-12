---
title: "gpg blues"
date: 2009-01-04
forum: General Help
---

### Post by TDFlanders on 2009-01-04
Hi there,

I finally am getting the confirmation emails fromthe launchpad server. Unfortunately I cannot decrypt them. But firegpg and the gnome-terminal refer me to a key that I do not know about:

thomas@thomas-laptop:~$ gpg
gpg: Go ahead and type your message ...
^Z
[1]+  Stopped                 gpg
thomas@thomas-laptop:~$ gpg -d ~/Desktop/gpg
gpg: no valid OpenPGP data found.
gpg: decrypt_message failed: eof
thomas@thomas-laptop:~$ gpg -d ~/Desktop/gpg
gpg: encrypted with ELG-E key, ID D43D9A79
gpg: decryption failed: secret key not available
thomas@thomas-laptop:~$ gpg --fingerprint
/home/thomas/.gnupg/pubring.gpg
-------------------------------
pub   1024D/C605E80D 2007-03-29
      Key fingerprint = D298 466F B439 5436 D16E  FB8D 258C C5DA C605 E80D
uid                  Landscape Development Team <landscape-devel@lists.canonical.com>
sub   2048g/A37FF5CD 2007-03-29

pub   1024D/9081B35A 2008-11-12
      Key fingerprint = 7EE5 00D5 1F9D 6A25 386A  73AD 593C 218B 9081 B35A
uid                  Thomas Delbeke <thomasdelbeke@yahoo.com>
sub   4096g/7EDED57E 2008-11-12

pub   1024D/C8B84D32 2008-11-26
      Key fingerprint = 6DF1 C26F CE3A 5913 D2EB  52B8 7CAE BF74 C8B8 4D32
uid                  Thomas Delbeke (test3) <thomasdelbeke@gmail.com>
uid                  Thomas Delbeke (test 2) <thomasdelbeke@yahoo.com>
uid                  Thomas Delbeke (test) <thomasdelbeke@yahoo.com>
uid                  Thomas Delbeke <toom2079@gmail.com>
sub   4096g/4CE6B329 2008-11-26

pub   1024D/EA5BBD71 2005-11-24
      Key fingerprint = DBBF 2EEB F925 FAAD CF1F  3FFF D986 6941 EA5B BD71
uid                  Barry A. Warsaw <barry@warsaw.us>
uid                  Barry A. Warsaw <barry@wooz.org>
uid                  Barry A. Warsaw <barry@python.org>
uid                  Barry A. Warsaw <barry@canonical.com>
uid                  Barry Warsaw (GNU Mailman) <barry@list.org>
uid                  Barry A. Warsaw <barry.warsaw@canonical.com>
sub   2048g/D792C43B 2005-11-24

pub   1024D/428D7C01 2008-09-02
      Key fingerprint = 2512 191F EF87 29D6 E5AF  414D ECDC AD72 428D 7C01
uid                  Ubuntu Debug Symbol Archive Automatic Signing Key <ubuntu-archive@lists.ubuntu.com>
sub   2048g/A2C2A7A5 2008-09-02

thomas@thomas-laptop:~$ 
thomas@thomas-laptop:~$ 

What is:

ELG-E key, ID D43D9A79

??

Thanks for the help!

Thomas

---

