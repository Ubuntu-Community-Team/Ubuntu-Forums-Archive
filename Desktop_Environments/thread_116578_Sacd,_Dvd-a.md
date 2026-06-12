---
title: "Sacd, Dvd-a"
date: 2006-01-13
forum: Desktop Environments
---

### Post by gray380 on 2006-01-13
Hello all!

Is there any possibility to play Super Audio CD (or DVD-A) in Ubuntu?

brg,
Serhiy.

---

### Post by Turin Turambar on 2006-01-26
Please install a libdvdcss2 (search these forums in order to see how!). This helped me to play my Depeche Mode Playing the Angel SACD in Totem!

---

### Post by gray380 on 2006-01-27
[QUOTE=Turin Turambar]Please install a libdvdcss2 (search these forums in order to see how!). This helped me to play my Depeche Mode Playing the Angel SACD in Totem![/QUOTE]

Improbable concurrence. I also have bought this disk. "libdvdcss2" is already installed (v 1.2.8-1), but my totem does not play it.
When I try to open it in/var/log/messages there are following messages:

Jan 27 14:38:05 localhost kernel: [4494114.983000] hdc: media error (bad sector): status=0x51 { DriveReady SeekComplete Error }
Jan 27 14:38:05 localhost kernel: [4494114.983000] hdc: media error (bad sector): error=0x30 { LastFailedSense=0x03 }
Jan 27 14:38:05 localhost kernel: [4494114.983000] ide: failed opcode was: unknown
Jan 27 14:38:05 localhost kernel: [4494114.983000] end_request: I/O error, dev hdc, sector 136

Under WinOS I can play this CD ;(

brg,
Serhiy.

PS additional information:

~$ dpkg -l libdvd*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
un  libdvdcss                  <none>                     (no description available)
un  libdvdcss0.0.1             <none>                     (no description available)
un  libdvdcss0.0.2             <none>                     (no description available)
ii  libdvdcss2                 1.2.8-1                    portable abstraction library for DVD decryption
ii  libdvdnav4                 0.1.9-3                    The DVD navigation library
un  libdvdread1                <none>                     (no description available)
ii  libdvdread3                0.9.4-5                    Simple foundation for reading DVDs

---

### Post by Turin Turambar on 2006-01-27
Have you tried Xine-ui or VLC?
Totem requires a little bit of tweaking in order to play DVDs, yet VLC or XINE should work out of the box.

Still, your .log message is kinda strange...

Also, there's a new version of libdvdcss2. Mine is 1.2.9

---

