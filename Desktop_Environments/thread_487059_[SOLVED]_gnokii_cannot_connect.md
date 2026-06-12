---
title: "[SOLVED] gnokii cannot connect"
date: 2007-06-28
forum: Desktop Environments
---

### Post by rampitec on 2007-06-28
Hi!

I'm using Ubuntu 7.04 Festy:

uname -a
Linux nemezida 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

I could connect to the Nokia 6131 phone via Bluetooth well from nautilus, sending files. My phone is connectible and paired. Now I'm trying to setup gnokii, as described in the following article:

[https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing?highlight=%28bluetooth%29](https://help.ubuntu.com/community/NokiaEvolutionBluetoothSyncing?highlight=%28bluetooth%29)

The problem is gnokii cannot connect:

gnokii --identify
GNOKII Version 0.6.17
LOG: debug mask is 0x1
Config read from file /home/stas/.gnokiirc.
phone instance config:
model: 6510
port_device: 00:18:8d:25:98:ec
connection_type: 5
init_length: 0
serial_baudrate: 115200
serial_write_usleep: -1
hardware_handshake: 0
require_dcd: 0
smsc_timeout: 100
connect_script: 
disconnect_script: 
rfcomm_cn: 1
sm_retry: off
Connecting
Serial device: opening device 00:18:8d:25:98:ec
Can't connect: Connection refused
Couldn't open PHONET device: Connection refused
Error in link initialisation: 1
Telephone interface init failed: Command failed.
Quitting.
Cannot unlock device.
Command failed.
Serial device: closing device

I was trying 0.6.14 from Ubuntu repositories with the same effect, this one is the recent from gnokii web site.

The config files I have:

/etc/bluetooth/hcid.conf

options {
        autoinit yes;
        security auto;
        pairing multi;
        passkey "XXXX";
        pin_helper /home/stas/bin/btpiwrapper
}

device {
        name "%h-%d";
        class 0x3e0100;
        iscan enable; pscan enable;
        discovto 0;
        lm accept;
        lp rswitch,hold,sniff,park;
}

.gnokiirc

[global]
port=00:18:8d:25:98:ec
model = 6510
initlength = default
connection = bluetooth
use_locking = no
serial_baudrate = 115200
smsc_timeout = 10

[gnokiid]
bindir = /usr/local/sbin/

[connect_script]
[disconnect_script]
[logging]
debug = on
rlpdebug = on
xdebug = on


The prefix /usr/local here is correct. Phone can be found:

hcitool scan
Scanning ...
        00:18:8D:25:98:EC       Stas's mobile

Running `sudo gnokii --identify` has the same effect.

The relevant strace output is:

write(2, "Serial device: opening device 00"..., 48Serial device: opening device 00:18:8d:25:98:ec
) = 48
socket(PF_BLUETOOTH, SOCK_STREAM, 3)    = 5
connect(5, {sa_family=AF_BLUETOOTH, sa_data="\354\230%\215\30\0\16\0\354\230%\215\30\0"}, 10) = -1 ECONNREFUSED (Connection refused)


Does anyone know what to do now? ;)

---

### Post by oled on 2007-06-30
Got the exact same error on my 6131, using the same guide. 

Only difference that I noticed was in .gnokiirc where I think model should be 6110

---

### Post by rampitec on 2007-07-01
OK, I've solved the problem. Removing pairing on device and repairing helped. Now BT is working and gnokii can retrieve data from the cell phone.

---

### Post by rampitec on 2007-07-01
Wow! If worked :) The key is not to install the latest things from sources, but instead download and instal .debs from [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/feisty.php](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/feisty.php)

You-ho!

---

### Post by labreche on 2007-07-25
Hy guys, 

i'm trying to connect a nokia 6110 navigator, running symbian os v9.1. 
i have installed gnokii suite using [http://www.in.fh-merseburg.de/~jahn/opensync-0.21/](http://www.in.fh-merseburg.de/~jahn/opensync-0.21/) 
i can connect and do bluetooth file transfert, but when trying a gnokii --identify i get a connection refused. 
 I 've tried to use gnapplet.sys, downloaded from gnokii.org/download, but my cellphone does'nt want to setup this sis file. 
 So now, i'm facing two problems and, at least, 2 solutions:
1)managing to connect using gnokii command line, but without gnapplet running on my cellphone
2)setting up gnapplet.sis on my nokia,  configure gnokiirc whith rfcomm=14 and model=serie60

Well all i want to do is to impress my gf with sending sms via my fesiti fawn powered  inspiron 640m. So if anyone has encountered, tried to solve this problems, or get the solution, i'm ready to share.

Cio

---

### Post by clint1010 on 2008-05-31
I to am trying to sync my Nokia 6110 via bluetooth to a toshiba laptop running Hardy

Have a Bluetooth dongle, and can connect and transfer files from phone to laptop (not the other way round yet, get an error) but no success yet with sync, I will watch this thread for info. Please post up if you have had any success doing this

Thanks

---

