---
title: "My complete guide to Cisco VPN in Ubuntu 5.10 (it works and I am a n00b)"
date: 2005-10-23
forum: Desktop Environments
---

### Post by repawn on 2005-10-23
Using a variety of methods picked up from numerous posts plus abit of jst paling trial and error - I managed to get my Cisco VPN Client to connect to my workplace.

Surprisingly - even though it took me three days - it is easy if you know the steps.  I will try to break it down into a few separate steps.

First - Install Ubuntu!  Ok - done - your internet connection is ok?  Then we can move on.  We are going to start by opening the synaptic package manager - once there you should do a search for "build-essential"  Select and install this - it gives you everything you need to "make: plus the linux headers and kernel.  That is a whole lot easier than my original attempt.  Now you are going to want to hop over to /usr/src
there you should see:  
/usr/src$ ls
linux          linux-headers-2.6.12-9      linux-source-2.6.12
linux-headers  linux-headers-2.6.12-9-386  

Ok - you will not see "linux" or "linux-headers" thos are links - go ahead and make them "linux" is linked to 'linux-source-2.6.12' and "linux-headers" is linked to 'linux-headers-2.6.12-9-386'  (you will have to do a 'sudo -s' to make the links (to be honest I am pretty bad at command line so I enable root to login and changed the root password just so I could do this via the file manager) 

Now - extract your cisco vpn client (mine was "vpnclient-linux-4.0.4.B-k9.tar.gz.tar") I just extracted it to my home directory) You should now have a vpnclient folder with a bunch of files in it.  Do not do the install yet.

Next the infamous patch:
-----------------------------------------------------------------------
Copy/paste this patch:

code:
[I]--- interceptor.c.orig  2005-01-04 14:55:44.246848280 -0500
+++ interceptor.c       2005-01-04 14:56:15.955027904 -0500
@@ -236,6 +236,24 @@
     dev_kfree_skb(skb);
     return 0;
 }
+
+static int
+inline supported_device(struct net_device* dev)
+{
+    int rc=0;
+
+    if(dev->type == ARPHRD_ETHER)
+    {
+        rc=1;
+    }
+    else if(dev->type == ARPHRD_PPP)
+    {
+        rc=1;
+    }
+
+    return rc;
+}
+
 static int
 add_netdev(struct net_device *dev)
 {
@@ -476,23 +494,6 @@
     s->rc = 0;
 }

-static int
-inline supported_device(struct net_device* dev)
-{
-    int rc=0;
-
-    if(dev->type == ARPHRD_ETHER)
-    {
-        rc=1;
-    }
-    else if(dev->type == ARPHRD_PPP)
-    {
-        rc=1;
-    }
-
-    return rc;
-}
-

 static BINDING *
 getbindingbydev(struct net_device *dev)[/I]

and apply it with 'patch -p0 < patch.txt' when you are in the vpnclient directory. All that is being done is modifying interceptor.c by moving the supported_device() function definition before the add_netdev() call.
---------------------------------------------------------------------

Now you should be ready to do the install

open a terminal and

sudo -s
Enter password

./vpn_install
you should be able to accept all of the defaults

if you make it to the end you will have to initialize the server (the install should tell you that - but here it is anyway)

/etc/init.d/vpnclient_init start

should just post Done.

Now you will have to take your .pcf file and make sure you have a copy of it in the following folder: /etc/CiscoSystemsVPNClient/Profiles

You will know that it is the correct folder because there should be a sample.pcf in there.

Now all you have to do is open a terminal and enter: vpnclient connect "profile name without the .pcf - sample instead of sample.pcf)

Should get a screen that looks like this:

--------------------------------------------------
XXXXXX@XXXXXXX:~$ vpnclient connect abc

Cisco Systems VPN Client Version 4.0.4 (B)
Copyright (C) 1998-2003 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686

Initializing the VPN connection.
Contacting the gateway at 123.4456.789.1
User Authentication for abc...

Enter Username and Password.

Username [XXXXXXX]:
Password []:
Authenticating user.
Negotiating security policies.
Securing communication channel.
You are connected to ABC VPN access.
Unauthorized use is prohibited.
Do you wish to continue? (y/n): y

Your VPN connection is secure.

VPN tunnel information.
Client address: 123.456.789.1
Server address: 098.765.432.1
Encryption: 168-bit 3-DES
Authentication: HMAC-MD5
IP Compression: None
NAT passthrough is inactive
Local LAN Access is disabled
----------------------------------------

If it didn't work - let me know - it is late and I may have forgotten a step or two.  

On a side note I use tsclient to remote desktop to my office PC (running win XP pro)  Very cool - additionally - with vpn connected I am able to connect to my Edxchange servers global address list with Evolution (with Evolution everything is pretty much web based - just not the public folders and global addresses)!

Chris

---

### Post by djjazzy on 2005-10-25
Great post, filled in a lot of the blanks for this noob. I'm having trouble though making the symbolic links. Can you give me the exact commands you used. I'm just seeing directories in /usr/src. Thanks man.........Jeff

---

### Post by djjazzy on 2005-10-25
Sorry, I was being stupid :confused: I was able to make the symlinks. Still having a problems tho running the interceptor script. I copied and pasted the code into patch.txt in the vpnclient install driectory. When I run

patch -p0 < patch.txt

I get this output

woodman@payback:~/Download/linux$ patch -p0 < patch.txt
can't find file to patch at input line 3
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|--- interceptor.c.orig 2005-01-04 14:55:44.246848280 -0500
|+++ interceptor.c 2005-01-04 14:56:15.955027904 -0500
--------------------------
File to patch:

I've never patched before so maybe this is normal and I just don't know it? Any help would be appreciated.

---

### Post by djjazzy on 2005-10-25
oops, another bad mistake by me. I got the patch to run when I did it correctly....

---

### Post by djjazzy on 2005-10-25
I've completed the install successfully but when I try to start the vpn service, I get the following (which I know I have seen before)

woodman@payback:~$ sudo /etc/init.d/vpnclient_init start
Password:
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Can anybody help me out? Thanks in advance.......Jeff

---

### Post by shadow07 on 2005-10-25
With the official release of Breezy, I was able to successfully install the Cisco VPN client without any patch or hack.  What version are you trying to install?  I have 4.6.03.0190-k9 installed.

I also have GVPNDialer installed and it works perfectly.

---

### Post by djjazzy on 2005-10-25
Hey Shadow, I'm using this:

vpnclient-linux-4.7.00.0640-k9.tar.gz

I did get it installed, just when I try to start the ipsec service I get the above gag. I've been digging and most stuff I've seen says to run the interceptor.c patch which I did according to this post. Still having the same insmod error tho......

---

### Post by shadow07 on 2005-10-25
Try installing/compiling it WITHOUT the patch.  I did not apply the patch, as it was only needed to build the module.  Like I said, it compiled and loaded just fine with my install.  I am running an older version than you.  But, yours should work just fine.

---

### Post by djjazzy on 2005-10-25
I unpacked the original tarfile and re-ran the install successfully. I'm still getting the same insmod error when I run the init script:

root@payback:/home/woodman# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Dmesg shows the following:

[4303525.996000] cisco_ipsec: disagrees about version of symbol struct_module

I originally tried to run the install on a fresh installation of breezy but had build problems which following the steps in this thread solved for me. At this point, I'm knackered and don't know what to do. I think I'm in over my head. I need this thing to run so I can throw away winblows for good :razz:  Any help greatly appreciated. BTW, other than this and a weird Evolution/Exchange issue, breexy has been GREAT! I've had none of the problems I've read about in other posts. I also did an apt-get dist-upgrade on my other notebook running hoary, no problems there either.

---

### Post by evisboy on 2005-10-25
ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC. 

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example: 

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0
 

You will see a bunch of information.  Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold): 

IPSec gateway **10.10.222.215**
IPSec ID **mygroup**
IPSec secret **ClearTextPassword**
Xauth username **UserName**

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!! 

To disconnect, use:    vpnc-disconnect 

My suggestion is don't waste your time w/ the cisco client.

---

### Post by shadow07 on 2005-10-25
PM me if you would like to get the version of the Cisco client I have.

---

### Post by repawn on 2005-10-27
[QUOTE=evisboy]ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC. 

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example: 

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0
 

You will see a bunch of information.  Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold): 

IPSec gateway **10.10.222.215**
IPSec ID **mygroup**
IPSec secret **ClearTextPassword**
Xauth username **UserName**

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!! 

To disconnect, use:    vpnc-disconnect 

My suggestion is don't waste your time w/ the cisco client.[/QUOTE]


Thanks for this - I have done a reinstall of Ubuntu after I had gotten Cisco to run - on the reinstall I didn't want to mess with it.  I ran my IPSec Secret through the program and it came out clean!  I can now use vpnc (so much easier!)  I highly recommedn this method if your workplace/school will accept it.

---

### Post by Plagued on 2005-11-06
This is a pretty good how-to. I just installed vpnclient-linux-x86_64-4.7.00.0640-k9 without any patching or anything. The only problem I am having is that the vpn service doesn't start when I boot. When I run `/etc/init.d/vpnclient_init start` everything runs fine, it just won't start as part of the default runlevel. 

The symlinks are in place under the appropriate runlevels, it just won't start.

If anyone has any thoughts on this, I would be very happy to hear them.

Also, to add, for the detractors out there who would start saying that I am wasting my time with the cisco vpn client, I would like to add that I would prefer to use vpnc, but our current vpn solution is not using username and password, simply the group name and group password: a setup which vpnc does not support.

---

### Post by shadow07 on 2005-11-07
Actually, vnpc does support vpn group authentication.  In my case, I support numerous clients out there, and not all are willing to give me the vpn group's password.

I too have the very same thing you are experiencing.  The service does not start upon reboot.

The fix I'm thinking about is adding the service to sudoers, and then add the service to my desktop session.  I haven't tested this, yet, as I have been a bit lazy the past few days.

---

### Post by UphillSkier on 2005-11-17
[QUOTE=
The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!! 

To disconnect, use:    vpnc-disconnect 

My suggestion is don't waste your time w/ the cisco client.[/QUOTE]

I wish it was that easy for me.  Everything works until this last step, when I get
```
andy@grumpy:~$ sudo vpnc /etc/vpnc/McMasterVPNC.conf
Enter password for mullera@macvpn.mcmaster.ca:
vpnc: hash comparison failed: AUTHENTICATION_FAILED
check group password!
```

I gathered from what I read on the Cisco site that they had blocked this method of breaking the hashed password.

---

### Post by Plagued on 2005-11-25
[QUOTE=shadow07]Actually, vnpc does support vpn group authentication.  In my case, I support numerous clients out there, and not all are willing to give me the vpn group's password.

I too have the very same thing you are experiencing.  The service does not start upon reboot.

The fix I'm thinking about is adding the service to sudoers, and then add the service to my desktop session.  I haven't tested this, yet, as I have been a bit lazy the past few days.[/QUOTE]


How do you get vpnc working without a username and password? I tried messing for the thing for months in Gentoo using only our group name and group password (no username / userpass) and I could never get it to work. 

Any help you can offer will be greatly appreciated since I would much rather use F/OSS any day.

---

### Post by shadow07 on 2005-11-25
It depends on the version of PIXOS that is running.  With ver 7.0, you can no longer use vpnc at all.  If your firewall is running PIXOS ver 6.2(x), you can use vpnc.  If it is running ver 6.3(x), you cannot use vpnc with group password.

I ask again:  why can you not use the 4.7 VPN client with GVPNDialer????  This works perfectly well on my machine, and you do NOT need to know the group name and password.

And, adding 'sudo /etc/init.d/vpnclient_init start' to the Sessions -> Startup Programs list works perfectly fine for me.  Oh, and you will need to add the path to the startup script to sudoers so you are not prompted for your password.

---

### Post by Nyala on 2005-11-28
[QUOTE=shadow07]It depends on the version of PIXOS that is running.  With ver 7.0, you can no longer use vpnc at all.  If your firewall is running PIXOS ver 6.2(x), you can use vpnc.  If it is running ver 6.3(x), you cannot use vpnc with group password.

I ask again:  why can you not use the 4.7 VPN client with GVPNDialer????  This works perfectly well on my machine, and you do NOT need to know the group name and password.

And, adding 'sudo /etc/init.d/vpnclient_init start' to the Sessions -> Startup Programs list works perfectly fine for me.  Oh, and you will need to add the path to the startup script to sudoers so you are not prompted for your password.[/QUOTE]
It's said that version 4.7 should work with no modification, but I'm having trouble. I'm new to Ubuntu, though I've futzed with Linux and Solaris in the past. I'm trying to install v4.7 of the Cisco VPN client on Ubuntu 5.10. I've tried several things listed in this thread and in others on ubuntu forums, but I still have problems when I run the vpn_install script. I get the following error:

> /.../vpnclient/interceptor.c:468: error: redefinition of 'supported_device'
/.../vpnclient/interceptor.c:215: error: previous definition of 'supported_device' was here
make[2]: *** [/.../vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/.../vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2


Using Google, the only reference I can find to the "redefinition of supported device" is on a German version of the Ubuntu forums, and I can't seem to parse the solution that may (or may not) be provided there.

BTW, I've already tried vpnc, it didn't seem to work for me. Besides, the big corporate monolith I work for would much prefer I stick with the "approved" solution.

Anyone have any ideas? Any help would be greatly appreciated.

---

### Post by Nyala on 2005-11-28
Nevermind - I got it working. I wish I knew exactly what I did -- I'd post a nice tutorial. But I tried so many different things, I'm not sure what worked.

The last thing I did was run the vpn_uninstall script, then deleted the vpnclient directory and re-extracted it, then re-ran the vpn_install script. It worked! 

I suspect the installation of the "build-essential" package was the necessary step, and the install script just had something stuck in it's craw. But I don't really know for sure.

The moral of the story: if you try several different things to make this work, be sure to use the vpn_uninstall script before you try building the client again. I'm very happy to have VPN working.

---

### Post by shadow07 on 2005-11-29
[QUOTE=Nyala]Nevermind - I got it working. I wish I knew exactly what I did -- I'd post a nice tutorial. But I tried so many different things, I'm not sure what worked.

The last thing I did was run the vpn_uninstall script, then deleted the vpnclient directory and re-extracted it, then re-ran the vpn_install script. It worked! 

I suspect the installation of the "build-essential" package was the necessary step, and the install script just had something stuck in it's craw. But I don't really know for sure.

The moral of the story: if you try several different things to make this work, be sure to use the vpn_uninstall script before you try building the client again. I'm very happy to have VPN working.[/QUOTE]


If you don't have the build-essential, linux-kernel-headers, and the correct versio nof g++ (3.4, not 4.0), the module should build properly and the install should complete successfully.  And, I am using version 4.7 as well.

Glad to see you got it working.

---

### Post by murkin on 2005-12-01
[QUOTE=shadow07]It depends on the version of PIXOS that is running.  With ver 7.0, you can no longer use vpnc at all.  If your firewall is running PIXOS ver 6.2(x), you can use vpnc.  If it is running ver 6.3(x), you cannot use vpnc with group password.

I ask again:  why can you not use the 4.7 VPN client with GVPNDialer????  This works perfectly well on my machine, and you do NOT need to know the group name and password.

And, adding 'sudo /etc/init.d/vpnclient_init start' to the Sessions -> Startup Programs list works perfectly fine for me.  Oh, and you will need to add the path to the startup script to sudoers so you are not prompted for your password.[/QUOTE]

how did you get gvpn installed?? i keep getting an error message which states "cannot find pcre.h." and then asks that i install libpcre. i have all libpcre libraries found within synaptic. i also downloaded the latest pcre tar from their site (version 6.4). any ideas?
thanks!

---

### Post by diffuser78 on 2005-12-01
[QUOTE=evisboy]ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC. 

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example: 

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0
 

You will see a bunch of information.  Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold): 

IPSec gateway **10.10.222.215**
IPSec ID **mygroup**
IPSec secret **ClearTextPassword**
Xauth username **UserName**

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!! 

To disconnect, use:    vpnc-disconnect 

My suggestion is don't waste your time w/ the cisco client.[/QUOTE]


Thanks a lot...worked like a charm!!!!

---

### Post by rjacksix on 2005-12-07
I would really like to use vpnc but the authenticating server does not resolve to a name as a result I get the following message:

response from unknown host xx.xx.xx.xx:xxxxx where xx.xx.xx.xx is the IP address and :xxxxx is the port.

an examination of ethereal shows that the vpn is trying to assign a IP address and the message is correct...ideas?????

---

### Post by chibo on 2005-12-07
[QUOTE=djjazzy]I unpacked the original tarfile and re-ran the install successfully. I'm still getting the same insmod error when I run the init script:

root@payback:/home/woodman# /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)[/QUOTE]

Have you (or anyone else) figured out any solution for this problem? I'm getting the same errors and I think I've done everything I can...
 
I can't even download vpnc from synaptic to give it a try, because I need the vpn-client to connect internet (stupid campus networks :???: ). I'm able to use Cisco's vpn client from Windows and I downloaded vpnc for Debian but I get a bunch of errors when trying to compile it:
```
henri@ubuntu:~/vpnc-0.3.3$ sudo make
make: libgcrypt-config: Command not found
gcc -W -Wall -O -g '-DVERSION="0.3.3"'    -c -o vpnc.o vpnc.c
vpnc.c:40:20: error: gcrypt.h: No such file or directory
vpnc.c:102: error: &#226;&#8364;&#732;GCRY_MD_MD5&#226;&#8364;&#8482; undeclared here (not in a function)
vpnc.c:103: error: &#226;&#8364;&#732;GCRY_MD_SHA1&#226;&#8364;&#8482; undeclared here (not in a function)
...
```

I'd be glad if there's someone who could help me. It's so fustrating to switch between Ubuntu and Windows all the time.

---

### Post by rjacksix on 2005-12-08
Here are the essentials!

Install linux-headers (you do not need full source).

unpack your vpnclient software into a directory where you want to work

replace the interceptor.c file with this one (this obviates the patch that you 
may see referenced in some articles) [http://www.ces.clemson.edu/linux/interceptor.c](http://www.ces.clemson.edu/linux/interceptor.c)

go into super user mode (su -)

change into the directory that you unpacked the vpnclient into

run ./vpn_install

use the default for installation location

answer whether you want it to start automatically

when it asks where the source code is specify:

/usr/src/linux-headers-2.6.12-9-386

IMPORTANT: Symbols may not match...to overcome this do not use insmod as it does not give you a force option....if you try to use insmod you will more than likely get a symbol not found error.  Instead simply do a modprobe -r cisco_ipsec.

Create a pcf file or copy an existing pcf file into the /etc/Ciscovpnclient/profiles/ directory

issue the command vpnclient connect connection_pcf_file_name

Note: you do not need to specify .pcf

follow the prompts

you should be connected.

As an aside, I am very impressed with krdc and am able to connect to my win2K and win2003 servers rdp with ease.

Have fun! :p

---

### Post by chibo on 2005-12-08
Thanks for the advise, but it didn't work... I've tried it once before to replace interceptor.c with the new one, but it won't even compile. I get the following errors when running vpn_install:
```
Making module
make -C /usr/src/linux-headers-2.6.12-9-386 SUBDIRS=/home/henri/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/henri/vpnclient/linuxcniapi.o
  CC [M]  /home/henri/vpnclient/frag.o
  CC [M]  /home/henri/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/henri/vpnclient/interceptor.o
/home/henri/vpnclient/interceptor.c: In function 'recv_ip_packet_handler':
/home/henri/vpnclient/interceptor.c:640: error: 'struct <anonymous>' has no member named 'real_hh_len'
/home/henri/vpnclient/interceptor.c: In function 'do_cni_send':
/home/henri/vpnclient/interceptor.c:752: error: 'struct <anonymous>' has no member named 'real_hh_len'
make[2]: *** [/home/henri/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/henri/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```
I tried to look at the code of interceptor.c but I did'n figure out the problem... Could these errors be because of me using gcc-4.0? I've created a link /usr/bin/gcc-3.4 -> gcc-4.0. One problem is that I can't download anything from synaptic 'cause I need the VPN connection to work before connecting to internet. Is there any more good advice to make this up and running? Or even for the vpnc?

---

### Post by chibo on 2005-12-09
Now I got the Cisco VPN client to work. It was all because of gcc-3.4. I managed to install it from Kubuntu DVD and after that it started working.

---

### Post by CTD on 2006-03-08
Hello all, I just wanted to chime in to say that I succesfully got a cisco vpn client working after following directions at the following link:  

[http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm#install](http://www.mcmaster.ca/uts/network/vpn/vpnclient_linux.htm#install)

They even provide you with the client!

Quickly, here's the steps I took to get it working

prerequisites - install the following packages from snaptic
build-essential
gcc-3.4
linux-source-(your kernel version)
linux-headers-(your kernel version)

in my case it was linux-source-2.6.12-10 and linux-headers-2.6.12-10-386

create symbolic links to linux-source and linux-headers directories

```
$ cd /usr/src
$ ln -s linux linux-source-2.6.12-10
$ ln -s linux-headers linux-headers-2.6.12-10-386
```

download and unpack vpn client from aformentioned link

run vpn_install from vpnclient directory, using default options.

One thing to note, when I rebooted, the vpn service did not automatically start like it was supposed to.  I had to turn it on manually
```
$ /etc/init.d/vpnclient_init start
```

---

### Post by jerinjoy on 2006-03-09
I've installed my vpn client but I'm getting the following error related to invalid module format.

jerinjoy@jj-ubuntu-sys:~$ sudo /etc/init.d/vpnclient_init start
Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.12-9-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Does anyone know what is wrong and how I can solve it. I'm new to Ubuntu.

Jerin

---

### Post by adamkane on 2006-03-09
This is over my head, but .ko errors, may mean you have an Athlon (K7) system, and do not have the appriate headers installed. Search for the following in Synaptic and install

```

sudo apt-get install linux-headers-k7 linux-image-k7 linux-k7  linux-restricted-modules-k7

``` 

If your installation script requires linux-*-686 headers, then the script may need to be altered for k7.

It isn't necessary to remove the linux-*-386 and linux-*-686 packages. If you decide to remove them, do it only after you've rebooted.

---

### Post by jerinjoy on 2006-03-10
i'm running ubuntu on my centrino laptop. i didn't compile the source. The vpn client installation asked me for my source directory when I installed and I pointed it to the headers directory in /usr/src/

---

### Post by jerinjoy on 2006-03-10
OK. I downloaded the source - it was necessary. in addition it needed gcc-3.4. now it finds the compile script. But i'm seening a WHOLE lot of errors

Makefile:485: .config: No such file or directory

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/jerinjoy/My_Setups/vpnclient/linuxcniapi.o
In file included from /home/jerinjoy/My_Setups/vpnclient/linuxcniapi.c:12:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
/home/jerinjoy/My_Setups/vpnclient/linuxcniapi.c:13:27: linux/version.h: No such file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:13,
                 from include/linux/if.h:22,
                 from include/linux/netdevice.h:28,
                 from /home/jerinjoy/My_Setups/vpnclient/linuxcniapi.c:14:
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/asm/posix_types.h:13:22: features.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/3.4.5/include/asm/posix_types.h:14:35: no include path in which to search for asm/posix_types.h
In file included from include/linux/if.h:22,
                 from include/linux/netdevice.h:28,
                 from /home/jerinjoy/My_Setups/vpnclient/linuxcniapi.c:14:

The list goes on...

---

### Post by adamkane on 2006-03-10
This sort of error is common. When it says you're missing .h or .c files, then you probably need to install some development packages. Development packages look like this:

beep-media-player-dev
libssl-dev
qt3-apps-dev
x-dev

I've gotten into the bad habit of installing any -dev packages that I think may be necessary to compile a piece of software. There are almost always clues about which -dev packages you need to install, if you look at the relevant installation guides. You can usually find installation guides on the software maker's website or inside the software archive. 

It gets hairy if the -dev packages you need are not available/compatible with Ubuntu. There are usually ways to deal with it, but there's no simple HOWTO that I've found to deal with this.

---

### Post by FantasySportsMan on 2006-03-17
[QUOTE=evisboy]ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC. 

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example: 

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0
 

You will see a bunch of information.  Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold): 

IPSec gateway **10.10.222.215**
IPSec ID **mygroup**
IPSec secret **ClearTextPassword**
Xauth username **UserName**

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!! 

To disconnect, use:    vpnc-disconnect 

My suggestion is don't waste your time w/ the cisco client.[/QUOTE]
I followed these instructions, but I'm getting a 
"vpnc: binding to port 500: Permission denied" error 
when I run "vpnc /etc/vpnc/VPN.conf"

Is this something to do with our server?  I noticed some replies later in this thread that indicated vpnc couldn't be used for the lastest verison of the CISCO fw....

any ideas?  I'm going to try the cisco client install now

---

### Post by FantasySportsMan on 2006-03-17
nevermind, I ran it as sudo and it worked

---

### Post by blx_286 on 2006-03-18
I am a serious noob and I am having trouble getting my head around this vpn setup. I have tried several things in the various vpn threads, but I am still stuck. These last setup I tried was using the instructions provided by that McMasters University. Everthing looked ok, but when trying to initialize it, I got that Insmod error. So, I thought I would start over and this is where I am at:

root@blackhole:/usr/src# sudo apt-get install build-essential gcc-3.4 linux-image-2.6.12-10-386 linux-headers-2.6.12-10-386
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
linux-image-2.6.12-10-386 is already the newest version.
The following extra packages will be installed:
  cpp-3.4 gcc-3.4-base linux-headers-2.6.12-10
Suggested packages:
  gcc-3.4-doc libc6-dev-amd64
The following NEW packages will be installed:
  cpp-3.4 gcc-3.4 gcc-3.4-base linux-headers-2.6.12-10
  linux-headers-2.6.12-10-386
0 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 9116kB of archives.
After unpacking 79.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gcc-3.4-base 3.4.4-6ubuntu8.1 [163kB]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main cpp-3.4 3.4.4-6ubuntu8.1 [1707kB]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main gcc-3.4 3.4.4-6ubuntu8.1 [517kB]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10 2.6.12-10.30 [5927kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main linux-headers-2.6.12-10-386 2.6.12-10.30 [802kB]
Fetched 9116kB in 47s (191kB/s)

Preconfiguring packages ...
Selecting previously deselected package gcc-3.4-base.
(Reading database ... 72413 files and directories currently installed.)
Unpacking gcc-3.4-base (from .../gcc-3.4-base_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package cpp-3.4.
Unpacking cpp-3.4 (from .../cpp-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package gcc-3.4.
Unpacking gcc-3.4 (from .../gcc-3.4_3.4.4-6ubuntu8.1_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-10.
Unpacking linux-headers-2.6.12-10 (from .../linux-headers-2.6.12-10_2.6.12-10.30_i386.deb) ...
Selecting previously deselected package linux-headers-2.6.12-10-386.
Unpacking linux-headers-2.6.12-10-386 (from .../linux-headers-2.6.12-10-386_2.6.12-10.30_i386.deb) ...
Setting up gcc-3.4-base (3.4.4-6ubuntu8.1) ...
Setting up cpp-3.4 (3.4.4-6ubuntu8.1) ...
Setting up gcc-3.4 (3.4.4-6ubuntu8.1) ...
Setting up linux-headers-2.6.12-10 (2.6.12-10.30) ...

Setting up linux-headers-2.6.12-10-386 (2.6.12-10.30) ...
root@blackhole:/usr/src# ls
linux-headers-2.6.12-10  linux-headers-2.6.12-10-386
root@blackhole:/usr/src# rm -r linux-headers-2.6.12-10-386
root@blackhole:/usr/src# ln -s linux linux-source-2.6.12-10
root@blackhole:/usr/src# ln -s linux-headers linux-headers-2.6.12-10

I don't know what I did wrong, but /usr/src showed two different headers, so I deleted one. And the linux-source is showing as a broken link.

Sorry for the long post, but if someone could point me in the right direction I would appreciate it.

Thanks,
Tim

---

