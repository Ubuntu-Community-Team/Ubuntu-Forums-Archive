---
title: "[SOLVED] Xilinx ISE WebPACK 10.1 : Can't access /dev/parport0"
date: 2008-12-11
forum: General Help
---

### Post by jdb2 on 2008-12-11
I just finished going through hoops while trying to get Xilinx' ISE WebPACK 10.1 to run under Kubuntu 8.04 . Here's the thread on the Xilinx Forums : 

[URL="http://forums.xilinx.com/xlnx/board/message?board.id=DEENBD&thread.id=26"]
http://forums.xilinx.com/xlnx/board/message?board.id=DEENBD&thread.id=26[/URL]


Basically, I followed the instructions in the ["Gentoo Xilinx HOWTO"]("http://da.gentoo-wiki.com/HOWTO_Xilinx") by proxy via the instructions presented at [this]("http://vkataev.googlepages.com/xilinxiseandlinuxgnushellscriptsandmakef") site.

After installing openmotif, libstdc++5, and portmap, I compiled and installed libusb-driver.so as per the instructions given [here]("http://rmdir.de/~michael/xilinx/"). I had to do this as Xilinx' JTAG parallel port drivers are binary-only and compiled against a specific version of RHEL -- libusb-driver emulates the Xilinx drivers at the user level.

So, when I launched Xilinx iMPACT in order to program the serial PROM on my dev board via the parallel port, I got the following error messages :

```
// *** BATCH CMD : setMode -bs
// *** BATCH CMD : setMode -bs
GUI --- Auto connect to cable...
// *** BATCH CMD : setCable -port auto
AutoDetecting cable. Please wait.
PROGRESS_START - Starting Operation.
Reusing 7803C001 key.
Reusing FC03C001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport0).
 libusb-driver.so version: 2008-11-27 08:11:07.
 parport0: baseAddress=0x0, ecpAddress=0x400
 LPT base address = 0000h.
 ECP base address = 0400h.
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed.
Reusing 7903C001 key.
Reusing FD03C001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport1).
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing 7A03C001 key.
Reusing FE03C001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport2).
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing 7B03C001 key.
Reusing FF03C001 key.
 OS platform = i686.
Connecting to cable (Parallel Port - parport3).
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing A003C001 key.
Reusing 2403C001 key.
 OS platform = i686.
Connecting to cable (Usb Port - USB21).
Checking cable driver.
File version of /opt/Xilinx/10.1/ISE/bin/lin/xusbdfwu.hex = 1030.
File version of /usr/share/xusbdfwu.hex = 1030.
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing A103C001 key.
Reusing 2503C001 key.
 OS platform = i686.
Connecting to cable (Usb Port - USB22).
Checking cable driver.
File version of /opt/Xilinx/10.1/ISE/bin/lin/xusbdfwu.hex = 1030.
File version of /usr/share/xusbdfwu.hex = 1030.
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing A203C001 key.
Reusing 2603C001 key.
 OS platform = i686.
Connecting to cable (Usb Port - USB23).
Checking cable driver.
File version of /opt/Xilinx/10.1/ISE/bin/lin/xusbdfwu.hex = 1030.
File version of /usr/share/xusbdfwu.hex = 1030.
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
Reusing A303C001 key.
Reusing 2703C001 key.
 OS platform = i686.
Connecting to cable (Usb Port - USB24).
Checking cable driver.
File version of /opt/Xilinx/10.1/ISE/bin/lin/xusbdfwu.hex = 1030.
File version of /usr/share/xusbdfwu.hex = 1030.
 libusb-driver.so version: 2008-11-27 08:11:07.
Cable connection failed.
PROGRESS_END - End Operation.
Elapsed time =      8 sec.
Cable autodetection failed.
WARNING:iMPACT:923 - Can not find cable, check cable setup !

```

as well as a message to STDERR in the console :

"Can't open /dev/parport0: Permission denied"

After doing an "ls -al /dev/parport0" : 

"crw-rw---- 1 lp scanner 99, 0 2008-12-11 07:23 /dev/parport0"


i tried changing the group of iMPACTS' executables to "scanner" but this resulted in the same error messages.

Failing this, I checked if the parport, parport_pc, and ppdev kernel modules were loaded : 

"parport_pc             36260  1
 parport                37832  3 ppdev,lp,parport_pc"

which, as you can see, they appeared to be.

Then I noticed I had overlooked one of the iMPACT error messsages : 

"LPT port is already in use."

HA! Well, if it's in use, I don't know by what, or why.

If anyone could shed some light on this conundrum I'd be extremely grateful.

Thank you,

jdb2

---

### Post by jdb2 on 2008-12-11
I ended up having to change the permissions of /dev/parport0 from
"crw-rw----" to "crw-rw-rw-" which is the inelegant "solution" I wanted to avoid. ( my system crashed just after doing this, and upon a reboot the permissions were reset. Don't know if the above had anything to do with that )

If there is another way, I'd appreciate it if someone could offer an explanation.

jdb2

---

### Post by leospart on 2008-12-17
Add yourself to the group 'lp', then log out & in again:

sudo usermod -a -G lp $USER

That will give you permission to access the parallel port.

Have fun!  Now I just need to get my board working ...

---

### Post by jdb2 on 2008-12-17
Tried that. Didn't work for some reason. I'll try it again.

Thanks for the advice.


Regards,


jdb2

---

### Post by jdb2 on 2008-12-17
Oops. I just remembered that I changed the group of "/usr/local/bin/startise" to "lp" and then to "scanner" -- I did not add myself to any groups. 

Unfortunately, adding myself, and root, to lp and scanner still results in a ```
LPT port is already in use. rc = FFFFFFFFh
Cable connection failed

``` error, along with a "Can't open /dev/parport0: Permission denied" to STDERR. 

:confused:

jdb2

---

### Post by jdb2 on 2008-12-18
HA! Brain segfault. I forgot to re-login. :biggrin: Works perfectly now!!! ( I can verify that my design was implemented on the FPGA )

Thanks a lot leospart!

Regards,

jdb2

---

