---
title: "usb modem blues"
date: 2009-03-02
forum: Desktop Environments
---

### Post by reid8.1 on 2009-03-02
ha all, new to linux (ubuntu 8.10) and attempting to connect to internet via usb with a dial up to earthlink. I guess I can connect, but the system than disconnects automatically after 45 seconds(I have checked the connection with my phone/landline and it is connecting with isp). the modem than reconnects, on disconnection I get an exit code = 8. var/log/messages shows chat pppd 2.4.4 started (as root or user no diff.), abort on busy...bla...bla, send (ATZ^M), expect (OK), alarm, Failed, Exit.
also, can only connect from term. window (gnome ppp will not connect). any suggestions? thx

---

### Post by ddrichardson on 2009-03-03
Your init string looks wrong, how are you connecting - through which program?

---

### Post by reid8.1 on 2009-03-05
the program I am using wvdial, wvdial.conf is as follows: Init1 = ATZ, Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0, Modem type = USB Modem, ISDN = 0, New PPPD = yes, Phone = xxxxxxx, (have received advice that because I am using a conexant series 1063, model 3095, 08-15356 USB that the 'phone' should be either Phone = /dev/modem or /dev/ttySHF0tried no diff. also that modem port (ttyACM0) is unix comm. tried ln -s /etc/dev/ttyACM0 /dev/modem without change). Modem = /dev/ttyACM0, Username ELN/meee@earthlink.net, Password = secret, Baud = 115200. linuxant says that the driver appears ok, probably in config somewhere. I seem to connect but than are disconnected after 45 sec. gnome ppp seems a duplicate of .conf file but will not connect via gui. any and all ideas are welcome, thx Reid.

---

### Post by ddrichardson on 2009-03-05
Have you tried increasing pppd time out? Maybe you're not getting a response quick enough.

---

### Post by GeorgeVita on 2009-03-05
Hi **reid8.1**,

it would be helpful to copy/paste all your **/etc/wvdial.conf** file to see the full syntax (do not edit anything except your username & password).

With your modem attached to the USB port (powered on) copy/paste the output of:
**lsusb**
**ls /dev/ttyU* /dev/ttyA***

Also copy/paste all the output of the command: **sudo wvdial** (to show all messages from connection till the disconnection).

Regards,
George

---

### Post by reid8.1 on 2009-03-06
Outputs requested (hope most translated from openoffice to ms word, looks like it) note* below. investigated man pages, did /var/log/messages and /var/log/auth.log as well. can send if it would help. 

/etc/wvdial.conf
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = USB Modem
ISDN = 0
New PPPD = yes
Phone = xxxxxxx
Modem = /dev/ttyACM0
Username = ELN/meeee@earthlink.net
Password = secret
Baud = 460800

wvdial
sudo wvdial 
--> WvDial: Internet dialer version 1.60 
--> Cannot get information for serial port. 
--> Initializing modem. 
--> Sending: ATZ 
OK 
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 
OK 
--> Modem initialized. 
--> Sending: ATDTxxxxxxx 
--> Waiting for carrier. 
ATDTxxxxxxx 
CONNECT 9600 
--> Carrier detected.  
Waiting for prompt. 
Level 3 Comm nas61.det1 UQKT2 
Username:/login:/Login: 
--> Looks like a login prompt. 
--> Sending: ELN/meeee@earthlink.net 
ELN/meeee@earthlink.net 
Password:  
--> Looks like a password prompt. 
--> Sending: (password)     
Entering PPP Session.     
IP address is 4.229.180.144     
MTU is 1524. 
--> Looks like a welcome message. 
--> Starting pppd at Fri Mar  6 09:44:51 2009 
--> Pid of pppd: 6394 
--> pppd: &#65533;'&#65533;[08]&#65533;%&#65533;[08] *(squares are question mark in diamond)
--> Disconnecting at Fri Mar  6 09:45:37 2009 
--> The PPP daemon has died: Connect script failed (exit code = 8) 
--> man pppd explains pppd error codes in more detail. 
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information. 
--> Auto Reconnect will be attempted in 5 seconds 
lsusb
Bus 001 Device 006: ID 0803:3095 Zoom Telephonics, Inc.  
Bus 001 Device 005: ID 051d:0002 American Power Conversion Uninterruptible Power Supply 
Bus 001 Device 004: ID 0781:9595 SanDisk Corp. ImageMate xD-SM 
Bus 001 Device 003: ID 05fe:0011 Chic Technology Corp. Browser Mouse 
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
ls /dev/ttyU* /dev/ttyA*
ls: cannot access /dev/ttyU*: No such file or directory /dev/ttyACM0 
I really appreciate all the help, Reid.

---

### Post by reid8.1 on 2009-03-06
thanx ddrichardson,
pppd time out? is that in options? sorry trying to keep things in order and reply to several good people who are trying to help. sooner or later something will work, Reid.

---

### Post by ddrichardson on 2009-03-06
Its not the timeout, what does /var/log/messages say?

---

### Post by reid8.1 on 2009-03-11
dd,
following is what I think applies to connection. not sure what to look for, the whole doc is several pages. also have /var/log/auth.log if helpful, it is also lengthy. thanx reid
/var/log/messages (user)
meee-desktop kernel:[ 329.655953] PPP generic driver version 2.4.2
meee-desktop pppd[6429]: pppd 2.4.4 started by meee, uid 1000
meee-desktop chat[6436]: abort on (BUSY)
meee-desktop chat[6436]: abort on (VOICE)
meee-desktop chat[6436]: abort on (NO CARRIER)
meee-desktop chat[6436]: abort on (NO DIALTONE)
meee-desktop chat[6436]: abort on (NO DIAL TONE)
meee-desktop chat[6436]: send (ATZ^M)
meee-desktop chat[6436]: expect (OK)
meee-desktop chat[6436]: alarm
meee-desktop chat[6436]: Failed
meee-desktop pppd[6429]: Exit

/var/log/messages (root)
meee-desktop kernel:[ 207.773873] PPP generic driver version 2.4.2
meee-desktop pppd[6237]: pppd 2.4.4 started by root, uid 0
meee-desktop chat[6245]: abort on (BUSY)
meee-desktop chat[6245]: abort on (VOICE)
meee-desktop chat[6245]: abort on (NO CARRIER)
meee-desktop chat[6245]: abort on (NO DIALTONE)
meee-desktop chat[6245]: abort on (NO DIAL TONE)
meee-desktop chat[6245]: send (ATZ^M)
meee-desktop chat[6245]: expect (OK)
meee-desktop chat[6245]: alarm
meee-desktop chat[6245]: Failed
meee-desktop pppd[6237]: Exit

---

### Post by reid8.1 on 2009-03-11
dd, some more from var/log/messages if it helps, thank you much Reid.

Mar 11 09:40:14 meee-desktop kernel: [  136.501828] PPP generic driver version 2.4.2
Mar 11 09:40:14 meee-desktop kernel: [  136.686140] NET: Registered protocol family 10
Mar 11 09:40:14 meee-desktop kernel: [  136.691540] lo: Disabled Privacy Extensions
Mar 11 09:40:14 meee-desktop kernel: [  136.695653] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 11 09:40:14 meee-desktop pppd[6209]: pppd 2.4.4 started by meee, uid 1000
Mar 11 09:40:14 meee-desktop chat[6223]: abort on (BUSY)
Mar 11 09:40:14 meee-desktop chat[6223]: abort on (VOICE)
Mar 11 09:40:14 meee-desktop chat[6223]: abort on (NO CARRIER)
Mar 11 09:40:14 meee-desktop chat[6223]: abort on (NO DIALTONE)
Mar 11 09:40:14 meee-desktop chat[6223]: abort on (NO DIAL TONE)
Mar 11 09:40:14 meee-desktop chat[6223]: send (ATZ^M)
Mar 11 09:40:14 meee-desktop chat[6223]: expect (OK)
Mar 11 09:40:39 meee-desktop pppd[6209]: Exit.
Mar 11 09:40:43 meee-desktop kernel: [  166.303578] type=1503 audit(1236778843.918:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6258/net/" pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.310181] type=1503 audit(1236778843.926:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.315529] type=1503 audit(1236778843.930:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.321006] type=1503 audit(1236778843.938:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326254] type=1503 audit(1236778843.942:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326289] type=1503 audit(1236778843.942:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326311] type=1503 audit(1236778843.942:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326333] type=1503 audit(1236778843.942:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326355] type=1503 audit(1236778843.942:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6258 profile="/usr/sbin/cupsd"
Mar 11 09:40:43 meee-desktop kernel: [  166.326508] type=1503 audit(1236778843.942:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6258/net/dev" pid=6258 profile="/usr/sbin/cupsd"

---

### Post by ddrichardson on 2009-03-11
Nothing leaps out, have a look at this [guide]("https://help.ubuntu.com/community/DialupModemHowto") and see if there are any steps missing.

---

### Post by reid8.1 on 2009-03-12
thanx dd,
I am going to, for kicks, paste in /var/log/auth.log and let me know if this tells you anything. tried the link below [www.gnome](www.gnome)... but no longer exists I geuss. I have looked at that guide before but will look again. as always, thanx for any help Reid.
/var/log/auth.log
Mar  6 09:39:48 meee-desktop gdm[5695]: pam_unix(gdm:session): session opened for user meee by (uid=0) 
Mar  6 09:39:48 meee -desktop gdm[5695]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0 
Mar  6 09:39:48 meee -desktop gdm[5695]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified 
Mar  6 09:39:49 meee -desktop gdm[5695]: Autolaunch error: X11 initialization failed. Mar  6 09:39:49 meee -desktop gdm[5695]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified 
Mar  6 09:39:49 meee -desktop gdm[5695]: Autolaunch error: X11 initialization failed. 
Mar  6 09:39:49 meee -desktop gdm[5695]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified 
Mar  6 09:39:49 meee -desktop gdm[5695]: Autolaunch error: X11 initialization failed. 
Mar  6 09:39:49 meee -desktop gdm[5695]: ) 
Mar  6 09:41:17 meee -desktop sudo:    meee : TTY=pts/0 ; PWD=/home/ meee ; USER=root ; COMMAND=/usr/bin/gedit 
Mar  6 09:44:29 meee -desktop sudo:    meee : TTY=pts/0 ; PWD=/home/ meee ; USER=root ; COMMAND=/usr/bin/wvdial 
Mar  6 09:45:40 meee -desktop sudo:     root : TTY=unknown ; PWD=/ ; USER= meee ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy 
Mar  6 09:45:41 meee -desktop sudo:     root : TTY=unknown ; PWD=/ ; USER= meee ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/host Mar  6 09:45:42 meee -desktop sudo:     root : TTY=unknown ; PWD=/ ; USER= meee ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/port Mar  6 09:54:09 meee -desktop polkit-grant-helper[6732]: granted authorization for org.freedesktop.hal.storage.mount-fixed to pid 6722 [uid=1000] [auth= meee] 
Mar  6 09:56:42 meee -desktop gdm[5695]: pam_unix(gdm:session): session closed for user meee

---

