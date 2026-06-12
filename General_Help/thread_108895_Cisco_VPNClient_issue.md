---
title: "Cisco VPNClient issue"
date: 2005-12-27
forum: General Help
---

### Post by cadumg on 2005-12-27
I am trying to install the Cisco VPNClient on my Ubuntu breeze but I am having some issues.... I did it 2 weeks ago on the version 5.04 and was fine, but in the 5.10 version it doesn't work.

-----

root@Rome:/home/cadumg/Desktop/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.7.00 (0640) Linux Installer
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.12-9-386/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.12-9-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.12-9-386/build" will be used to build the module.

Is the above correct [y]

Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/cadumg/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/cadumg/Desktop/vpnclient/linuxcniapi.o
  CC [M]  /home/cadumg/Desktop/vpnclient/frag.o
  CC [M]  /home/cadumg/Desktop/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/cadumg/Desktop/vpnclient/interceptor.o
  CC [M]  /home/cadumg/Desktop/vpnclient/linuxkernelapi.o
  LD [M]  /home/cadumg/Desktop/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST
[COLOR="Red"]Warning: could not find /home/cadumg/Desktop/vpnclient/.libdriver.so.cmd for /home/cadumg/Desktop/vpnclient/libdriver.so[/COLOR]
  CC      /home/cadumg/Desktop/vpnclient/cisco_ipsec.mod.o
  LD [M]  /home/cadumg/Desktop/vpnclient/cisco_ipsec.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
Copying module to directory "/lib/modules/2.6.12-9-386/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* Replaced Profiles: sample

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
    /opt/cisco-vpnclient/bin/ipseclog
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (permissions not changed)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.
[COLOR="Red"]root@Rome:/home/cadumg/Desktop/vpnclient# ./vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)[/COLOR]


-----

What should I do to install it ?

Thanks

---

### Post by cadumg on 2005-12-27
[COLOR="Red"][SIZE="4"]SOLVED!!![/SIZE][/COLOR]

To solve it I installed GCC 3.4 and all other components (Download binary packages on [http://packages.debian.org/unstable/devel/gcc-3.4](http://packages.debian.org/unstable/devel/gcc-3.4) and using "dpkg -i <package name>").

It seems that it doesn't work with GCC 4.0!

---

### Post by varunus on 2005-12-27
Yeah, Ubuntu breezy is compiled with GCC4.0, but the kernel is still compiled with 3.4 (as it wont compile with 4.0). So to make kernel modules, you need 3.4.

---

### Post by nhisyam on 2006-01-03
hisyam@onix-06:~/Desktop/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.12-10-386/build]
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.12-10-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.12-10-386/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/hisyam/Desktop/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-386'
  CC [M]  /home/hisyam/Desktop/vpnclient/interceptor.o
/home/hisyam/Desktop/vpnclient/interceptor.c: In function `add_netdev':
/home/hisyam/Desktop/vpnclient/interceptor.c:59: sorry, unimplemented: inlining failed in call to 'supported_device': function body not available
/home/hisyam/Desktop/vpnclient/interceptor.c:245: sorry, unimplemented: called from here
/home/hisyam/Desktop/vpnclient/interceptor.c: In function `recv_ip_packet_handler':
/home/hisyam/Desktop/vpnclient/interceptor.c:607: warning: passing arg 1 of `skb_checksum_help' from incompatible pointer type
/home/hisyam/Desktop/vpnclient/interceptor.c: In function `do_cni_send':
/home/hisyam/Desktop/vpnclient/interceptor.c:732: warning: passing arg 1 of `skb_checksum_help' from incompatible pointer type
make[2]: *** [/home/hisyam/Desktop/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/hisyam/Desktop/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

gcc 3.4 installed.. but still receiving this error. any idea what i should do?
thanks in advance

---

### Post by cadumg on 2006-01-03
Did you try the lastest version ? It is the 4.7. 

Check if you are not trying also the 64 bit version (or the 32 if you are running in a 64 bit machine).

If you do not find the lastest version to download, ask me and I'll put in some website like rapidshare so you can download it.

---

### Post by nhisyam on 2006-01-04
hmm my campus only provides me the 4.6 version... yeah i'm on 32 bit machine. i would like to try 4.7 if possible.

---

### Post by cadumg on 2006-01-04
Try this link: 
[http://www.fc.up.pt/cca/servicos/acesso/vpn/software/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz?popup](http://www.fc.up.pt/cca/servicos/acesso/vpn/software/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz?popup)

Or: [http://www.cs.uu.nl/technical/services/vpn/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz](http://www.cs.uu.nl/technical/services/vpn/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz)

Or: [http://vpn.doit.wisc.edu/download/test/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz](http://vpn.doit.wisc.edu/download/test/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz)

Let me know how does it work.

---

### Post by Rud on 2006-01-04
[QUOTE=nhisyam]
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

gcc 3.4 installed.. but still receiving this error. any idea what i should do?
thanks in advance[/QUOTE]

I had a similar issue. Did you install the linux-headers for your kernel? I installed package linux-headers-2.6.12-10-386 (which also installed linux-headers-2.6.12-10), and that fixed it.

Good luck.

---

### Post by neoflight on 2006-01-04
>  
Failed to make module "cisco_ipsec.ko".

gcc 3.4 installed.. but still receiving this error. any idea what i should do?
thanks in advance

sudo apt-get install build-essential % see its *not* essential_s_

and the run ./vpn_install

check that you have installed the kernel headers and source . it should be in 
/usr/src/ 
try ls and if there is nothing use synaptic to get both of them. you will get a zip file for source. unzip it in the same folder. 
during the make process the system will look into this folder. you dont have to manually put in the directory. just accept the default ans while u install.

i hope this helps... i have had the same problem and solved it...

if it still doesnt work try installing gcc 3.4 using synaptic AFTER you run the command buld-essential (here again gcc 4 will be installed. so)...and try vpn-install. 

let me know fellas...
later

---

### Post by nhisyam on 2006-01-04
hmm thanks for the file links.. i successfully installed cisco vpn client 4.7.. unfortunately now my profiles from the cisco installer provided by my campus (4.6 ) aren't usable in cisco vpn client 4.7..whenever i run the profile.. the whole ubuntu system will hang..any ideas?

thanks in advance..

---

### Post by cadumg on 2006-01-05
Maybe you can explode Cisco.... I can't understand how a profile from a 4.6 version could not be read in a 4.7 version.... If it was the oposite it would be bad, but acceptable, but this case is impossible.

What happen when you try to open de profile ?

I don't know your knowledge, so I will detail what you should do, to be sure that it is a major problem.

After the installation you should type

[COLOR="Red"]./vpnclient_init start[/COLOR]

and then you should get a message like:

[COLOR="Green"]Starting /opt/cisco-vpnclient/bin/vpnclient: Done[/COLOR]

So, now that the VPN is loaded, you need to load the profile, put the profile file in the VPN folder (like /etc/opt/cisco-vpnclient/Profiles) and type in the command line:

[COLOR="Red"]vpnclient connect *[/COLOR]

Where * is the name of the profile, like NAME.pcf (watch out, it is case sensitive), but you just type NAME, excluding the .pcf.  And then it should ask your username and password. 

If it doesn't work, I suggest you trying another VPN Client. One friend told me about kvpnc: [http://home.gna.org/kvpnc/](http://home.gna.org/kvpnc/)

You can get this debian package: [http://download.gna.org/kvpnc/kvpnc_0.8.2_unstable_kde35_i386.deb](http://download.gna.org/kvpnc/kvpnc_0.8.2_unstable_kde35_i386.deb)

And install it by typing in the folder I've downloaded it:

sudo dpkg -i kvpnc_0.8.2_unstable_kde35_i386.deb

I hope it will work!

---

### Post by Rud on 2006-01-05
Here is my profile with the sensitive stuff removed and replaced with X's. It's working fine for me:

```

[main]
Description=
Host=XXXXX
AuthType=1
GroupName=XXXX
GroupPwd=
enc_GroupPwd=XXXX
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=XXXX
SaveUserPassword=0
EnableBackup=0
BackupServer=
EnableNat=1
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
DHGroup=2
ForceKeepAlives=0
UserPassword=
enc_UserPassword=
ISPPhonebook=
NTDomain=
EnableMSLogon=1
MSLogonType=0
TunnelingMode=0
TcpTunnelingPort=XXXX
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0

```

---

### Post by nhisyam on 2006-01-05
i tried kvpn like u suggested.. and for some reason.. after importing the cisco .pnf file and when i tried to connect, my whole system hang..there must be something wrong with the profiles.. or something else which i don't know..

i'll try to ask people around about this problem when the school starts...right now it's the winter break and not many people around..thanks for all the suggestion and help..

---

### Post by Zyzzyva100 on 2006-01-15
Yea, actually I am having the same problem.  Using the new client (4.7) and my old profile, the system hangs and I have to hard reboot.

God I hate cisco.  Vpnc worked for me for awhile, but now they won't allow me to connect with it anymore.

---

### Post by nhisyam on 2006-01-17
well this is what i'm getting so far.. my vpn still not working...
this is the error message.


hisyam@onix-06:~$ sudo /etc/init.d/vpnclient_init restart
Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Starting /opt/cisco-vpnclient/bin/vpnclient: Done
hisyam@onix-06:~$ sudo /etc/init.d/vpnclient_init stat
Usage: /etc/init.d/vpnclient_init {start|stop|restart|reload|status}
hisyam@onix-06:~$ sudo /etc/init.d/vpnclient_init status
Module                  Size  Used by
cisco_ipsec           393196  0

cipsec0   Link encap:Ethernet  HWaddr 00:00:00:00:00:00
          BROADCAST MULTICAST  MTU:1400  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

hisyam@onix-06:~$ sudo vpnclient connect ~/vpnclient/RPI_External_VPN.pcf
Cisco Systems VPN Client Version 4.6.00 (0045)
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.12-10-686 #1 Thu Dec 22 11:55:07 UTC 2005 i686
Config file directory: /etc/opt/cisco-vpnclient

The profile specified could not be read.
hisyam@onix-06:~$

any idea? thanks in advance..

---

### Post by Miguel on 2006-01-17
Just a quick note:

From your terminal output, the VPN service isn't running after boot... unless you have already stopped. If it was running while you stopped, you would get:
```
miguel@lcpybm:~$ sudo /etc/init.d/hplip stop
password:
 * Stopping HP Linux Printing and Imaging System                                       [ ok ]
miguel@lcpybm:~$ 

```

Where, of course, you use your cisco thing instead of hplip. 

The second point, is that if you want to start a service, you use "start", not "stat". It's a small typo, but can make a whole lot of a difference.

Lastly, the client doesn't seem to be looking on eht0 or eth1, as the mac address is all zeros.

---

### Post by nhisyam on 2006-01-17
finally ... SUCCESS...

i should have read better...:oops:

the command should be

vpnclient connect RPI_Wireless 
intead of
vpnclient connect RPI_Wireless.pcf

it works now...   :razz:  YAY...

---

### Post by sambitnayak on 2006-01-20
Hi folks,

I have 64-bit kernel installed, and the Cisco vpnclient I am using is 4.6
I have installed the appropriate kernel source headers (based on output of `uname -r`)
I have made /usr/bin/gcc point to /usr/bin/gcc-3.4; and this is the gcc being used during compilation.



But I get the following errors :


* Binaries will be installed in "/home/sambit/VPN".
* Modules will be installed in "/lib/modules/2.6.12-10-amd64-generic/CiscoVPN".
* The VPN service will *NOT* be started automatically at boot time.
* Kernel source from "/lib/modules/2.6.12-10-amd64-generic/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.12-10-amd64-generic/build SUBDIRS=/home/sambit/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
  CC [M]  /home/sambit/vpnclient/linuxcniapi.o
In file included from /home/sambit/vpnclient/Cniapi.h:15,
                 from /home/sambit/vpnclient/linuxcniapi.c:34:
/home/sambit/vpnclient/GenDefs.h:101:2: warning: #warning 64 bit
In file included from /home/sambit/vpnclient/Cniapi.h:15,
                 from /home/sambit/vpnclient/linuxcniapi.c:34:
/home/sambit/vpnclient/GenDefs.h:102: error: parse error before "intptr_t"
/home/sambit/vpnclient/GenDefs.h:102: warning: type defaults to `int' in declaration of `intptr_t'
/home/sambit/vpnclient/GenDefs.h:102: warning: data definition has no type or storage class
/home/sambit/vpnclient/GenDefs.h:111:2: warning: #warning 64 bit
make[2]: *** [/home/sambit/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/sambit/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".






Could anyone suggest something please?

Thanks & Regards,
Sambit

---

### Post by cadumg on 2006-01-20
Do you know if your cisco version is compatible with 64 bits ?

---

### Post by sambitnayak on 2006-01-21
[QUOTE=cadumg]Do you know if your cisco version is compatible with 64 bits ?[/QUOTE]
Hi cadumg,

I ain't sure about that. Will try to find out.
Thanks for your reply.

Regards,
Sambit

---

### Post by cadumg on 2006-01-21
Try this one: [http://www.cs.uu.nl/technical/services/vpn/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz](http://www.cs.uu.nl/technical/services/vpn/vpnclient-linux-x86_64-4.7.00.0640-k9.tar.gz)

Or find the version that best fits your case:
[http://www.cs.uu.nl/technical/services/vpn/](http://www.cs.uu.nl/technical/services/vpn/)

---

### Post by Tichondrius on 2006-01-21
> **sambitnayak]Hi folks,

I have 64-bit kernel installed, and the Cisco vpnclient I am using is 4.6
I have installed the appropriate kernel source headers (based on output of `uname -r`)
I have made /usr/bin/gcc point to /usr/bin/gcc-3.4 said:**
> 

Making module
make -C /lib/modules/2.6.12-10-amd64-generic/build SUBDIRS=/home/sambit/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
  CC [M]  /home/sambit/vpnclient/linuxcniapi.o
In file included from /home/sambit/vpnclient/Cniapi.h:15,
                 from /home/sambit/vpnclient/linuxcniapi.c:34:
/home/sambit/vpnclient/GenDefs.h:101:2: warning: #warning 64 bit
In file included from /home/sambit/vpnclient/Cniapi.h:15,
                 from /home/sambit/vpnclient/linuxcniapi.c:34:
/home/sambit/vpnclient/GenDefs.h:102: error: parse error before "intptr_t"
/home/sambit/vpnclient/GenDefs.h:102: warning: type defaults to `int' in declaration of `intptr_t'
/home/sambit/vpnclient/GenDefs.h:102: warning: data definition has no type or storage class
/home/sambit/vpnclient/GenDefs.h:111:2: warning: #warning 64 bit
make[2]: *** [/home/sambit/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/sambit/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-amd64-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".






Could anyone suggest something please?

Thanks & Regards,
Sambit

yeah, I had the exact same problem, and you can easily fix it by editing the file interceptor.c to move the function "supported_device" from its current location somewhere in the middle of the file to the beginning of the file where its prototype is (replacing the one line prototype of the function with its full defintion that you moved from the middle of the file).

---

### Post by limaunion on 2006-01-21
Hi! I'm this problem while trying to install the Cisco VPN client (4.6/4.7), any ideas ? Thanks!

Making module
make -C /usr/src/linux SUBDIRS=/home/user1/My.Programs/vpnclient modules
make[1]: Entering directory `/usr/src/linux-2.6.15'
  CC [M]  /home/user1/My.Programs/vpnclient/linuxcniapi.o
/home/user1/My.Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/user1/My.Programs/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/user1/My.Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/user1/My.Programs/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/user1/My.Programs/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/user1/My.Programs/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

---

### Post by aysiu on 2006-02-18
First of all, I want to say I've been struggling to get VPN working on my Ubuntu for a *long* time. My workplace doesn't exactly offer much support on the Linux version of Cisco's VPN client.

I've poked around the forums quite a bit for this, and [this post](http://ubuntuforums.org/showpost.php?p=148190&postcount=21) was by far the most helpful in getting me set up.

Basically, after extracting the .tar ball, I did ```
sudo apt-get install build-essential gcc-3.4 linux-headers-2.6.12-10-k7
``` I use the k7 kernel because I have an AMD processor, but you pick the header for the appropriate kernel, of course.

Then in the extracted directory: ```
sudo ./vpn_install
``` I didn't answer to start it up automatically, but all the rest of the defaults worked for me.

Since I didn't start it automatically, I run this command every time: ```
sudo /etc/init.d/vpnclient_init start
```

However, copying my profile to /etc/opt/cisco-vpnclient/Profiles didn't work. When I did that (copying it from my Windows partition to my Linux one), I got something about "bad parameter." What worked was copying the sample profile (/etc/opt/cisco-vpnclient/Profiles/sample.pcf) and then changing the values to the appropriate ones.

Finally, I ran it as ```
sudo vpnclient connect *profilename*
``` and it has to be *profilename* and **not** *profilename.pcf*.

Then, once connected, and I know this is a separate issue, but for me I VPN to work so I can VNC.

So I did ```
sudo apt-get install xtightvncviewer
``` and then the command I use to run TightVNC is ```
vncviewer -compresslevel 9 -quality 0 -bgr233
``` I created a launcher for it. It's a good way to get the remote desktop working with minimal bandwidth use. After that, I'm prompted for the IP address and password, and that's it.

Oh, and to send a Control-Alt-Delete (to lock the computer when I'm done using it), I have to press F8.

I don't know if that helps anyone, but that's what finally got it working for me. Absolutely **no** reason for me to dual boot any more now!

---

### Post by gatorbait on 2006-02-24
Thanks guys.

Add to the record I was able to connect with version 4.6.2.30 using the 686 headers.

---

### Post by anil_robo on 2006-03-04
[quote=limaunion]Hi! I'm this problem while trying to install the Cisco VPN client (4.6/4.7), any ideas ? Thanks!

Making module
make -C /usr/src/linux SUBDIRS=/home/user1/My.Programs/vpnclient modules
make[1]: Entering directory `/usr/src/linux-2.6.15'
  CC [M]  /home/user1/My.Programs/vpnclient/linuxcniapi.o
/home/user1/My.Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/user1/My.Programs/vpnclient/linuxcniapi.c:292: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/user1/My.Programs/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/user1/My.Programs/vpnclient/linuxcniapi.c:432: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/user1/My.Programs/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/user1/My.Programs/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.15'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".[/quote] 
I have exactly the same error! Cant' be coincidence - has to be a reason behind it!!!

I was trying to install "vpnclient-linux-4.0.4.A-k9" with all the prerequisites already installed (gcc3.4 and 4.0, build-essential). The university provides me with version 4.04 only. I need to be 8000 miles away from work for two months... and even a noob can tell that I need VPN BADLY!!!

How can I make this vpn thing work? PLEASE HELP ME!!! :-(

---

### Post by x3non on 2006-05-03
anil_robo & limaunion:

Comment out these lines:

/* move the data into the packet */                                                             
/* do_gettimeofday(&skb->stamp); */

and

/* put the mac header on */
/* do_gettimeofday(&skb->stamp); */

in linuxcniapi.c

It worked for me.

Bye!

---

### Post by anil_robo on 2006-05-04
[quote=x3non]anil_robo & limaunion:

Comment out these lines:

/* move the data into the packet */                                                             
/* do_gettimeofday(&skb->stamp); */

and

/* put the mac header on */
/* do_gettimeofday(&skb->stamp); */

in linuxcniapi.c

It worked for me.

Bye![/quote]

I did exactly as you said. However, I get the same error: cisco_ipsec.ko
:confused:

---

### Post by WhimpyPeon on 2006-05-05
I used to work with the Cisco client and finally gave up because it was such a pain to get working in the first place and there were problems with all kernel upgrades.  I switched to vpnc and life has been good ever since.

I highly recommend you look into vpnc.  I just set up the configuration file (which wasn't hard at all) and have not touched a thing since.

[http://packages.ubuntu.com/breezy/net/vpnc]("http://packages.ubuntu.com/breezy/net/vpnc")

---

