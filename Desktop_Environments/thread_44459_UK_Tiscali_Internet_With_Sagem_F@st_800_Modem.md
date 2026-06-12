---
title: "UK Tiscali Internet With Sagem F@st 800 Modem"
date: 2005-06-26
forum: Desktop Environments
---

### Post by podrik0 on 2005-06-26
My last request for a while then I can format my whole disk of this Microsoft crap.

If I can get this internet working then I can have just this distro on their and can build my knowledge onwards from their.

First I have an Tiscali internet connection 512K Broadband.

It uses an Sagem F@st 800 modem to connect

I went to the kppp but said a file was missing or damaged? Log on to root to create a new one or something

I ignore and carry on and TRY to set up my connection, my connection doesn't have a phone number as it's broadband?

The User & Pass sections are greyed out as well

Please anyone help me get this working, then I will leave you all alone  :grin:

---

### Post by podrik0 on 2005-06-26
I think the linux drivers and setup is on the CD as I found this on there:

[IMG]http://img79.echo.cx/img79/2002/linux6zx.jpg[/IMG] 

Could anyone tell me how to install it?

I have no experience of installing packagaes

Thanks

---

### Post by podrik0 on 2005-06-26
I have found a site where it explains how to install but I still don't understand
I have downloaded the latest Eagle 2.30 drivers, but still it seem confusing!

Any one care to translate for me  :neutral: >?
Do I need to burn this onto CD? Should I keep it on the root?

```
To connect a Suse 9.1 (Kernel 2.6) machine via a Sagem Fast800? E2T to a UK-ADSL network with Tiscali as provider.

See the detailed instructions below.

Especially note steps 4 and 8 which were unexpected. They are no longer needed since eagle-usb-2.0.0. Use latest Dev:EagleUsb230 (interwiki)


0. Install development packages (via Yast)

    * kernel-source
    * gcc (C-Compiler)
    * cpp
    * libgcc (C-Bibliotheken)
    * eazy (SUSE Compatibilty Links)
    * lsb (Standard Base Tools)
    * bison (C Parser Generator)
    * libusb (USB-Bibliotheken)
    * usbutils
    * make
    * ncurses
    * ncurses - devel (kernel-menuconfig)



1. Start a root console

2. Preparing the kernel-sources: The sources must belong to the installed kernel.
cd /usr/src/linux
Save an old config if exists:
mv .config .config.old
Type "uname -r" to find out the version of the installed kernel and copy the respective file from "/boot/config*" to "/usr/src/linux/.config".
cp /boot/config-`uname -r` /usr/src/linux/.config
Run
make menuconfig
and exit with saving.

3. Prepare the eagle-usb-driver
Download: eagle-usb-1.9.8.tar.bz2 from SourceForge download area (you may take latest version and adapt)
Unpack it somewhere: e.g. into /opt
cd /opt
tar xvfj eagle-usb-1.9.8.tar.bz2
cd /opt/eagle-usb-1.9.8
If no configure-file exists run
./autogen.sh
Then a configure-file should exist. Run
./configure --prefix=/usr

4. Normally you would proceed with "make" etc. but I had the problem that after completing the installation my modem seemed to be too new:
The modem wouldn't become operational, after waiting and when typing "eaglectrl -p" something like this would appear:
Post-firmware device on USB bus 4 (type=POTS)

The solution for this was to use the original *.bnm-files from the Tiscali-Windows-Installation-CD instead of the *.bnm-files in the eagle-usb-1.9.8-package:
The directory /media/cdrecorder/ASSETS/Sagem/L1/IDMA contains the files:
RTBLDEP0.BNM, RTBLDEP1.BNM, RTBLDEP2.BNM, RTBLDEP3.BNM, RTBLDEP4.BNM

Copy them to /opt/eagle-usb-1.9.8/driver/firmware/sagem/pots and /opt/eagle-usb-1.9.8/driver/firmware/usr/pots and also rename them from uppercase to lowercase letters e.g.:
cp /media/cdrecorder/ASSETS/Sagem/L1/IDMA/RTBLDEP0.BNM /opt/eagle-usb-1.9.8/driver/firmware/sagem/pots/rtbldep0.bnm
etc. (for files 0...4)

Note you may use this alternate method :
dowload latest windows drivers from sagem http://www.sagem.com/web-modems/download/modems/w.2.0.31_fr.zip
cd /opt/eagle-usb-1.9.8/
unzip $(DIR_DL)/eagle-w.2.0.31_fr.zip # where DIR_DL is the directory where you downloaded
cp W.2.0.31_fr/L1/IDMA/rtbldep*.bnm driver/firmware/sagem/pots
cp W.2.0.31_fr/L1/IDMA/rtbldei*.bnm driver/firmware/sagem/isdn

Those .bnm work with E2L modem and work with Fast 800 WA (wanadoo origin) and Fast 908
I don't know the difference from E2T to E2L but I suspect T mind Tiscaly, for L, I don't know.

Do you know if those bnm work with E2T modems?

5. Now it's finally time for make:
make
make install

6. Configuring the ADSL-connection:
eagleconfig
Some questions about country, username, password and when to launch the ADSL-connection will be asked now.

When everything works then text similar to this will appear:
Loading DSP & options... [ OK ]
Waiting for modem to be operational... [ OK ]
Configuration successful.
You can now type "startadsl" to launch the connection.

7. Now run "startadsl" and try to access the internet via konqueror or similar.

8. After restarting the computer neither eagleconfig nor startdsl worked anymore. The problem seemed to be that the DSP-code wasn't reinitialised.
My solution was to change line 59 in /usr/sbin/eagleconfig to
SEND_DSP_NEEDED=1
which forces the DSP-reinitialisation with every launch of eagleconfig.
Then "startadsl" works again.

9. The connection can finally be terminated with "stopadsl".
```

---

### Post by podrik0 on 2005-06-26
HELP!!!

I have burnt it onto CD so far and have no way of knowing where to start!!

---

### Post by coolclassic on 2005-06-26
I installed the correct drivers on the kubuntu cd using kynaptic (search for the two files with eagle in it).

Unfotunatly I can't remember how I actually got it working but it was one of two things.
1) use sudo eaglectrl -w in your shell
    Then sudo startadsl

2) Run a config file which I can't remember it could be "dpkgconfig" or similiar. To further aid you the command actually updates your system as kynaptic fails to do so.
Then use the commands in 1 above.

Sorry this will confuse you but the files supplied do work. I hope I've given enough info for someone to give further help.

Good luck

---

### Post by podrik0 on 2005-06-26
THANK YOU & everyone else who helped!! 
Finally online posting off linux my first!  :)

---

### Post by davie on 2005-07-13
Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie

---

### Post by avantgardaclue on 2005-07-20
[QUOTE=davie]Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. 
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie[/QUOTE]

Hmmmm, when i got to "System>Administration>Networking" the only option displayed in front of me is a greyed out modem option ](*,)  Nearly there, can anyone advise if i've done anything stupid here? do i have to be logged on as "root" or something like that??

Simon

---

### Post by Trops on 2005-08-04
I have sagem modem but not with tiscali can you tell me how to configure manually for my ISP?

---

### Post by Hg80 on 2005-08-05
[QUOTE=davie]Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie[/QUOTE]


Done as you have Davie, but i get the following:

/usr/sbin/eagleconfig: line 110: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 117: /etc/eagle-usb/eagle-usb.conf: Permission denied
/usr/sbin/eagleconfig: line 141: /etc/ppp/peers/adsl: Permission denied
touch: cannot touch `/etc/ppp/peers/mire': Permission denied
/usr/sbin/eagleconfig: line 146: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 147: /etc/ppp/peers/adsl: Permission denied
grep: /etc/ppp/peers/adsl: No such file or directory
/usr/sbin/eagleconfig: line 151: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 153: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 159: /etc/eagle-usb/tmp: Permission denied
cat: /etc/ppp/peers/adsl: No such file or directory
/usr/sbin/eagleconfig: line 160: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 161: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 164: /etc/ppp/peers/mire: Permission denied
/usr/sbin/eagleconfig: line 165: /etc/ppp/peers/mire: Permission denied
/usr/sbin/eagleconfig: line 166: /etc/ppp/peers/mire: Permission denied
touch: cannot touch `/etc/ppp/secret9127.temp': Permission denied
/usr/sbin/eagleconfig: line 187: /etc/ppp/secret9127.temp: Permission denied
/usr/sbin/eagleconfig: line 191: /etc/ppp/chap-secrets: Permission denied
/usr/sbin/eagleconfig: line 213: /etc/ppp/secret9127.temp: Permission denied
/usr/sbin/eagleconfig: line 214: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 215: /etc/ppp/pap-secrets: Permission denied
grep: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 220: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 234: /etc/resolv.conf.old: Permission denied
ln: cannot remove `/etc/resolv.conf': Permission denied
touch: cannot touch `/etc/resolv.conf': Permission denied
chmod: changing permissions of `/etc/resolv.conf': Operation not permitted
ERROR: Removing 'eagle_usb': Operation not permitted

Loading DSP & options...

---

### Post by coolclassic on 2005-08-05
To start adsl connection

sudo eaglectrl -w
*password*
sudo startadsl

---

### Post by dave111 on 2005-08-24
Followed these instructions and managed to get online.
(using a sagem F@st800 on virgin BB.
Restarted the computer and cannot get online :-k 

Please help
what do should i do.
thank you....

[QUOTE=davie]Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie[/QUOTE]

---

### Post by lerrup on 2005-08-24
As poofyhairguy might say;  save yourself a lot of grief and buy something like this:
[http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=48448](http://www.ebuyer.com/customer/products/index.html?action=c2hvd19wcm9kdWN0X292ZXJ2aWV3&product_uid=48448)

---

### Post by dave111 on 2005-08-24
i never quit

---

### Post by davie on 2005-10-05
[QUOTE=dave111]Followed these instructions and managed to get online.
(using a sagem F@st800 on virgin BB.
Restarted the computer and cannot get online :-k 
Please help
what do should i do.
thank you....[/QUOTE]

Dave - when you restart start a terminal in root. Then put in 'eaglectrl -d' and hit return. Wait a wee while and then put in 'startadsl'. If it comes back saying 'modem not operational' just wait a wee while longer and then put 'startadsl' in again. Seems to work for me. 

All the best,

Davie

---

### Post by emo on 2005-10-06
If I understood you want to install ubuntu or kubuntu rigth but you connection doesn't help at all yeah so it is your problem I can burn and send one cd for you.when you got you cd is easy  go to your bios change the boot sequence after that just reboot your system and follow the instructions.

---

### Post by Bueno on 2005-11-17
[QUOTE=davie]Thanks very much to everyone for that. It gave me enough info to get my adsl up and running on Ubuntu. Here's what I did, starting off with my modem unplugged from the USB:

1. System>Administration>Synaptic Packet Manager
2. Scroll down left hand menu. Click on Networking.
3. In right hand box, mark 'eagle-usb-data' and 'eagle-usb-utils' for installation.
4. Stick the Ubuntu installation CD in the drive.
5. Click Apply
6. The system should then install these two packages from the CD.
6.5 Plug in your modem.
7. Go to Applications>System Tools>Root Terminal. (Don't do what I did the first four times I tried this and go to Applications>System Tools>Terminal. You need to be in root to make it work.)
8. At the prompt type in 'eagleconfig'. This will give you a list of options for different ISPs. You'll see Tiscali at the bottom as 'UK01'
9. Type in 'UK01'
10. At the prompt, type in your ISP username
11. At the prompt, type in your ISP password
12. At the prompt about encryption, say 'no'
13. At the prompt about startup on boot, say 'no'
14. You should then get a message saying that configuration was successful.
15. Type 'startadsl'
16. Go to System>Administration>Networking
17. Double click on 'Ethernet connection eth01'
18. Tick the 'This device is configured' box'
19. Change the Connection Settings Configuration drop down from 'Static IP Address' to 'DHCP'
20. Click 'OK'
21. This takes you back to the first dialogue box. 
22. Make sure that 'Ethernet connection eth01' is highlighted and then click on 'Activate' 

And that should be it. Hope it helps someone. 

All the best,

Davie[/QUOTE]
Hi, I've been following Davie's instructions above and have got to point 14 and not got the "config successful" I then typed "eaglestat" and got the following

Enter your password (given by your ISP):

Does your ISP support password encryption? [y]/nn

Do you want the connection to automaticaly be started at boot? y/[n]n
/usr/sbin/eagleconfig: line 45: strings: command not found


Loading module...                      [ OK ]

Loading DSP & options...               [ Error ]
root@ubuntu:/home/rob# startadsl


Modem is not operational!
Check eaglestat result to know its state!

root@ubuntu:/home/rob# eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 001    USB Device : 005        Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:47:59
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

root@ubuntu:/home/rob#

Can anyone help?

I'm actually using v5.10 not Hoary! My provider is tiscali through a Sagem 800 modem

Cheers
Bueno

---

### Post by dgtester on 2005-12-11
I have the same problem as Bueno:

Loading DSP & options... [ Error ]

Anyone else? (I'm also using 5.10.)

---

### Post by Geoneil on 2006-01-01
Seems Breezy has a problem with Sagem modems that Hoary didn't, I'm using Kubuntu (so getting the files with Adpet rather than Synaptic) and have having the exact same bother.

---

### Post by ragnar_ok on 2006-01-02
same distro, same modem, same problem;) ...and so far no solution?

---

### Post by coolclassic on 2006-01-02
Have a look at this thread it provides the correct drivers and the correct installation process:

[http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)

---

### Post by ace2005 on 2006-01-28
There is no problem in breezy, is there? because i compiled it fine in Kubuntu 5.10 and its worked fine (until i went to dapper, added debian repos and completely screewed everything up, switched to debian stable to etch to sid, screwed that up, went to kanotix (which has eagle-usb on the install CD) and upgraded everything to sid)

Just install build essential, and kernel headers and the eagle-usb version 2.3.2 drivers compiled fine.

---

### Post by ace2005 on 2006-01-28
[QUOTE=coolclassic]Have a look at this thread it provides the correct drivers and the correct installation process:

[http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)[/QUOTE]

Is there a memory leak in the sagem driver?

I've read that in so many places that i never tried installing those

---

### Post by christhemonkey on 2006-01-31
This worked fine for me!
On tinternet and everything...!

---

### Post by nmsmith on 2006-01-31
I followed the instructions linked above ([http://ubuntuforums.org/showthread.php?t=45974]("http://ubuntuforums.org/showthread.php?t=45974") about manually compiling the drivers) but since this is my first experience of make, I'm not sure I did things right.

```
make
```

The output is:

```
make -C driver && \
make -C pppoa && \
make -C utils/scripts && \
make -C utils/eagleconnect && \
make -C doc
make[1]: Entering directory `/home/nick/eagle-usb/eagle-usb-src/driver'
make  -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/nick/eagle-usb/eagle-usb-src/driver modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/nick/eagle-usb/eagle-usb-src/driver/eu_main.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/nick/eagle-usb/eagle-usb-src/driver/eu_main.o] Error 127
make[2]: *** [_module_/home/nick/eagle-usb/eagle-usb-src/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [eagle-usb.ko] Error 2
make[1]: Leaving directory `/home/nick/eagle-usb/eagle-usb-src/driver'
make: *** [build] Error 2
```

Now synaptic tells me that gcc-4.0 is installed, but there is no mention of 3.4. Is my installation (5.10) able to compile this driver from the source files or not?

Any advice appreciated.

---

### Post by coolclassic on 2006-01-31
Try the version available here:
[http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb211](http://dev.eagle-usb.org/wakka.php?wiki=EagleUsb211)

---

### Post by nmsmith on 2006-02-01
Well thanks for the suggestion coolclassic, but I get a similar problem:

```
root@thrymr:/home/nick/eagle-usb-2.1.1# make
make -C driver
make[1]: Entering directory `/home/nick/eagle-usb-2.1.1/driver'
USE_CMVS=0 make  -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/nick/eagle-usb-2.1.1/driver modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/nick/eagle-usb-2.1.1/driver/eu_main.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/nick/eagle-usb-2.1.1/driver/eu_main.o] Error 127
make[2]: *** [_module_/home/nick/eagle-usb-2.1.1/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [eagle-usb.ko] Error 2
make[1]: Leaving directory `/home/nick/eagle-usb-2.1.1/driver'
make: *** [build] Error 2
root@thrymr:/home/nick/eagle-usb-2.1.1#

```

Maybe I was not destined to use this modem.

Nick

---

### Post by coolclassic on 2006-02-01
It's all down to the version of the driver you are using an older version will work with the version of gcc you have. You can install gcc 3.4 along side other versions by using synaptic.

---

### Post by ace2005 on 2006-02-04
[QUOTE=nmsmith]I followed the instructions linked above ([http://ubuntuforums.org/showthread.php?t=45974]("http://ubuntuforums.org/showthread.php?t=45974") about manually compiling the drivers) but since this is my first experience of make, I'm not sure I did things right.
[/QUOTE]

Try it this way

[http://ubuntuforums.org/showpost.php?p=704112&postcount=13](http://ubuntuforums.org/showpost.php?p=704112&postcount=13)

---

### Post by Deklan on 2006-02-05
Hello, I'm a  first time linux user, obviously i use Ubuntu. I have installed it, got the correct drivers, followed davies instructions and i get the same error as the other guy, see below:

/usr/sbin/eagleconfig: line 110: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 117: /etc/eagle-usb/eagle-usb.conf: Permission denied
/usr/sbin/eagleconfig: line 141: /etc/ppp/peers/adsl: Permission denied
touch: cannot touch `/etc/ppp/peers/mire': Permission denied
/usr/sbin/eagleconfig: line 146: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 147: /etc/ppp/peers/adsl: Permission denied
grep: /etc/ppp/peers/adsl: No such file or directory
/usr/sbin/eagleconfig: line 151: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 153: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 159: /etc/eagle-usb/tmp: Permission denied
cat: /etc/ppp/peers/adsl: No such file or directory
/usr/sbin/eagleconfig: line 160: /etc/eagle-usb/tmp: Permission denied
/usr/sbin/eagleconfig: line 161: /etc/ppp/peers/adsl: Permission denied
/usr/sbin/eagleconfig: line 164: /etc/ppp/peers/mire: Permission denied
/usr/sbin/eagleconfig: line 165: /etc/ppp/peers/mire: Permission denied
/usr/sbin/eagleconfig: line 166: /etc/ppp/peers/mire: Permission denied
touch: cannot touch `/etc/ppp/secret9127.temp': Permission denied
/usr/sbin/eagleconfig: line 187: /etc/ppp/secret9127.temp: Permission denied
/usr/sbin/eagleconfig: line 191: /etc/ppp/chap-secrets: Permission denied
/usr/sbin/eagleconfig: line 213: /etc/ppp/secret9127.temp: Permission denied
/usr/sbin/eagleconfig: line 214: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 215: /etc/ppp/pap-secrets: Permission denied
grep: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 220: /etc/ppp/pap-secrets: Permission denied
/usr/sbin/eagleconfig: line 234: /etc/resolv.conf.old: Permission denied
ln: cannot remove `/etc/resolv.conf': Permission denied
touch: cannot touch `/etc/resolv.conf': Permission denied
chmod: changing permissions of `/etc/resolv.conf': Operation not permitted
ERROR: Removing 'eagle_usb': Operation not permitted

Loading DSP & options... [ERROR]

Also when i type "startadsl" or whatever it was, i get Modem is non Operational.

I just get Operation not Permitted or Permission Denied, i use Sagem F@ST 800 E2T, Tiscali 1MBPS broadband. I really want to start using linux asap as my windows is completely fludged. So if i could get any help, anything at all i would be so greatful.

Thanks again guys,
Declan.

---

### Post by Deklan on 2006-02-05
Heres some of the notes i have written down, just incase thats any help...

2.6.12-9-386
cd ~/eagle*
sudo make install
sudo dpkg -i *deb
sudo apt-get -f install

Thats the stuff i have tried.

---

### Post by coolclassic on 2006-02-05
Deklan you have a permission problem. All you need to do is change the permissions of the files concerned.

Also have a look here for other changes you will need for 'pap-secrets' and 'chap-secrets' :
[http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)

---

### Post by Deklan on 2006-02-05
[QUOTE=coolclassic]Deklan you have a permission problem. All you need to do is change the permissions of the files concerned.

Also have a look here for other changes you will need for 'pap-secrets' and 'chap-secrets' :
[http://ubuntuforums.org/showthread.php?t=45974](http://ubuntuforums.org/showthread.php?t=45974)[/QUOTE]

I just tried that, it says the directory or file dosnt exist when it does because its there, but it has a little black x ina red box in the top right hand corner of the icon of pap-secrets and chap-secrets. It says im not the owner but im the only user on the pc so i must be the owner, what else can i do?

---

### Post by coolclassic on 2006-02-05
All changes must be done as root.

---

### Post by coolclassic on 2006-02-05
Sorry when starting your connection use sudo:

sudo startadsl
sudo stopadsl

---

### Post by Deklan on 2006-02-05
[QUOTE=coolclassic]All changes must be done as root.[/QUOTE]
Sorry to sound dumb but what does that mean? Today is my first day using linux so i still have to learn it.

---

### Post by coolclassic on 2006-02-06
When you install most linux distro's you install with two users. One is yourself and the other is root. When using root you can do anything to your setup even mess it up and if your on the internet it is open to attack. Thus for every day use you use your own user account.

In ubuntu to do system management and alterations you would use sudo, this allows temporary access to the root account. As you have allready installed the eagel software you have allready used sudo without realising.

---

### Post by charbel on 2006-05-07
removed

---

### Post by charbel on 2006-05-07
[QUOTE=Bueno]Hi, I've been following Davie's instructions above and have got to point 14 and not got the "config successful" I then typed "eaglestat" and got the following

Enter your password (given by your ISP):

Does your ISP support password encryption? [y]/nn

Do you want the connection to automaticaly be started at boot? y/[n]n
/usr/sbin/eagleconfig: line 45: strings: command not found


Loading module...                      [ OK ]

Loading DSP & options...               [ Error ]
root@ubuntu:/home/rob# startadsl


Modem is not operational!
Check eaglestat result to know its state!

root@ubuntu:/home/rob# eaglestat
eagle-usb status display
-------------------------------------------------------------
Driver version 2.3.2     Chipset: Eagle0
Vendor ID : 0x1110     Product ID : 0x9031   Rev: 0x200b
USB Bus : 001    USB Device : 005        Dbg mask: 0x0
Ethernet Interface : none
MAC: 00:60:4c:71:47:59
Tx Rate           0  Rx Rate           0
FEC               0  Margin            0  Atten             0 dB
VID-CPE           0  VID-CO            0  HEC               0
VPI               0  VCI               0  Delin          GOOD
Cells Tx          0  Cells Rx          0
Pkts Tx           0  Pkts Rx           0
OAM               0  Bad VPI           0  Bad CRC           0
Oversiz.          0

Modem waiting for driver response.
Please send DSP (eaglectrl -d)

root@ubuntu:/home/rob#

Can anyone help?

I'm actually using v5.10 not Hoary! My provider is tiscali through a Sagem 800 modem

Cheers
Bueno[/QUOTE]


Same for me, exactly same thing (on ubuntu 5.10):


This is what I get when using the synaptic package manager, I get:

Preconfiguring packages ...
Selecting previously deselected package eagle-usb-data.
(Reading database ... 73168 files and directories currently installed.)
Unpacking eagle-usb-data (from .../eagle-usb-data_2.1.1-2_all.deb) ...
Selecting previously deselected package eagle-usb-utils.
Unpacking eagle-usb-utils (from .../eagle-usb-utils_2.1.1-2_i386.deb) ...
Setting up eagle-usb-data (2.1.1-2) ...
Setting up eagle-usb-utils (2.1.1-2) ...


Loading module... [ OK ]

Loading DSP & options... [ Error ]


this is what I get if I try eagleconfig


charbel@dracula:~$ sudo su
root@dracula:~# eagleconfig


================================================== ============================
============================= ADSL Configuration =============================
================================================== ============================
Your modem has to be plugged before proceeding.
You can stop this script anytime with [Ctrl][c]

Choose a network configuration :
__________________________________________________ _____________________
. . . Country. . . Network. . . . . . . . . VPI VCI ENC
-----------------------------------------------------------------------
DZ01 : Algeria Wanadoo 0 23 1 PPPoE LLC
AR01 : Argentina Speedy 1 23 1 PPPoE LLC
.....
.....
UK02 : United King British Telecom 0 26 6 PPPoA VC
UK01 : United King Tiscali UK 0 26 6 PPPoA VC
-----------------------------------------------------------------------
?UK01

Enter your login for connecting to the ISP (given by your ISP):
sgereige

Enter your password (given by your ISP):

Does your ISP support password encryption? [y]/nno

Do you want the connection to automaticaly be started at boot? [y]/nno


Loading module... [ OK ]

Loading DSP & options... [ Error ]

---

