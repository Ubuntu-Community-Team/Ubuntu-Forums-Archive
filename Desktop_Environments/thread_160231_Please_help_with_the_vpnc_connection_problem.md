---
title: "Please help with the vpnc connection problem"
date: 2006-04-14
forum: Desktop Environments
---

### Post by jameszhu on 2006-04-14
I'm able to install Cisco VPN client on my Ubuntu and connect to my corporation successfully. Now I would like to try vpnc for simplicity's sake, but the problem is, I'm getting ISAKMP_N_INVALID_EXCHANGE_TYPE(7).  This is what I did:

$ sudo vpnc-connect
Enter IPSec ID for 10.10.10.xxx: cliffz
Enter IPSec secret for [email]cliffz@10.10.10.xxx[/email]:  <-- input clear text password here and enter
vpnc-connect: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

Do I need to supply Xauth username in the configuration file? If so, my question is, how do I know my Xauth username?  My corporation just told me my group(IPSec ID) and group password(IPSec secre) and nothing else. This is the pcf file which works with my Cisco Linux client. Please have a look, do I miss anything?  Thanks.

pcf file content:
[main]
Description=
Host=10.10.10.xxx
AuthType=1
GroupName=cliffz
GroupPwd=
EnableISPConnect=0
ISPConnectType=0
ISPConnect=mycorporation.com
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
VerifyCertDN=
DHGroup=2
ForceKeepAlives=0
PeerTimeout=90
EnableLocalLAN=1
EnableSplitDNS=1
ForceNetLogin=0
enc_GroupPwd=757158EFDAB2F4C4CF10F0F7135A18AEB8B695071735FC8EEFFBFDC6610BF16B1E307D5942A7A95B075CA5DE962279D8

---

### Post by rugge on 2006-04-14
Where did you get your client from?

Rutger

---

### Post by jameszhu on 2006-04-14
[QUOTE=rugge]Where did you get your client from?

Rutger[/QUOTE]

I'm not 100% sure what 'get your client from' mean.  I installed vpnc from Synaptic, version is 0.3.3.  For Cisco VPN client that works, I downloaded it from web(source tar).

Anyone have an idea how can I get my vpnc connect to my corporate? thanks.

---

### Post by marjnap on 2006-04-23
The best instructions I have found on the web for setting up vpnc is at:
[http://www.yellowpigs.net/computers/vpn](http://www.yellowpigs.net/computers/vpn). It got me going in the right direction. Still have one config I can't figure out. In Cisco pcf file I have EnableNat=1 too, but cannot find a VPNC equivilant. I can connect to my corporate, but cannot browse the network. Note - The new version uses vpnc not vpnc-connect.

---

### Post by lee_connell on 2007-02-28
I have same problem, anyone with a solution?

---

### Post by lavinog on 2007-02-28
make a connection file in /etc/vpnc/
call it work.conf if you want
work.conf:
> IPSec gateway 0.10.10.{add rest of ip}
IPSec ID cliffz
IPSec obfuscated secret 757158EFDAB2F4C4CF10F0F7135A18AEB8B695071735FC8EEFFBFDC6610BF16B1E307D5942A7A95B075CA5DE962279D8
Local Port 10000
Xauth username {your username here}
Xauth password {your password here}

# OPTIONAL
# ========

#
#
# Varios options not undestood by vpnc itself but by some other scripts
#
# Target networks 123.234.210.0/24 10.1.0.0/16
# If Target networks is defined here, the default route is not replaced!

# Don't update resolv.conf though resolvconf is installed
# DNSUpdate no

then you can connect by typing:
vpnc-connect /etc/vpnc/work.conf

note this file should work for jameszhu's setup, lee if you have the pcf file from the cisco client you need to take the key from enc_GroupPwd and put it in the IPSec obfuscated secret.
if your key is not encrypted and is just a password remove "obfuscated" from the line.

Good luck...I find that vpnc connects much quicker than the cisco client.

---

### Post by lee_connell on 2007-03-01
lavinog,

thanks for the reply.  I tried your instructions and i still get the same error: 

vpnc-connect: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

I posted on newsgroups for vpnc, still waiting for a response.

Thanks!

---

### Post by lavinog on 2007-03-03
> **lee_connell said:**
> lavinog,

thanks for the reply.  I tried your instructions and i still get the same error: 

vpnc-connect: response was invalid [1]: ISAKMP_N_INVALID_EXCHANGE_TYPE(7)

I posted on newsgroups for vpnc, still waiting for a response.

Thanks!

Do you use the cisco client with windows, or have the setup file for it? If you do can you compare it to the one jameszhu posted. can you connect with another client (on another computer or windows?)
does the server require a group password?
Do you know what port you are supposed to be using? This script is setup for port 10000

---

### Post by lee_connell on 2007-03-03
I do use the cisco client with windows and works fine. I also used the pcf from windows on linux. converted it with the pcftoconf tool or whatever its called.

The server does require group password as well as xauth user/pass.  The PIX's I'm having problem with are the ones that require both the group and xauth credentials.  I've successfully connected to a PIX that only requires group password.

I didn't use the LocalPort parameter in my script since it works now on the PIX that only requires group password.

---

### Post by lavinog on 2007-03-04
> **lee_connell said:**
> I do use the cisco client with windows and works fine. I also used the pcf from windows on linux. converted it with the pcftoconf tool or whatever its called.

The server does require group password as well as xauth user/pass.  The PIX's I'm having problem with are the ones that require both the group and xauth credentials.  I've successfully connected to a PIX that only requires group password.

I didn't use the LocalPort parameter in my script since it works now on the PIX that only requires group password.

do you have a separate pcf for each connection?
in your conf file is there a xauth field and is the password obfuscated?
if it is obfuscated try removing "obfuscated" and put your password in plain text. if it works then we know where the problem lies.
I think i had a problem with having the xauth obfuscated and i had to resort to using plain text...also I am required to change my password every month so it makes it easy to make that change.

---

### Post by lee_connell on 2007-03-04
I do use a seperate pcf for each connection.  I don't use obfuscated at all, only recently i've tried that since you mentioned it with the group password.

---

### Post by lavinog on 2007-03-07
I'm out of ideas.
The only other thing i could say is look at the pcf file for the one that you can't connect to and look at each parameter and see if it is accounted for in the conf file. That conversion script could have missed something.

---

### Post by mad_ady on 2007-03-09
Hello everybody,

Of course, I have the same problem :)

I captured the packets leaving my machine to see where the negociation fails.

The first packet that leaves is a UDP packet going on port 500 to the vpn concentrator, that has, among other things 16 proposed transforms (like AES-CBC + SHA, AES-CBC + MD5, 3DES-CBC + SHA, 3DES-CBC + MD5 and others). By the way, this is a ISAKMP Agressive packet.

The reply from the concentrator also comes as a UDP packet (ISAKMP Informational)  and has a notification payload with the message 'No proposal chosen' (message type 0x000e). After this, there are no more messages.

I will try with the cisco vpn client, to see if it works, but I would like to use vpnc to make the connection.

---

### Post by mad_ady on 2007-03-12
I've done a little digging, and I found why the message appeared.

As I said in my previous message, the proposed transforms negociated included 3DES and AES. Today, I checked on the VPN concentrator, and it only accepted DES + MD5. Checking again the packets captured earlier, it seems that vpnc doesn't advertize DES (simple DES) and so the peers disagree.

I forced vpnc to advertize simple des (vpnc --enable-1des) and it managed to connect to the vpn concentrator without this error message.

Hope it also works for you!

---

### Post by lee_connell on 2007-03-12
mad_ady,

That worked perfectly.  Thank you very much, life is much easier now :)

just issuing `vpnc-connect --enable-1des CONFIG.conf` does the trick.

One issue i do have is having the same ip block as the site I'm connecting too, but that gives me an issue as well with cisco vpn client, I know it has something to do with setting up routes, is there a way to get around this? 

I will just change my local block to something else if I have too.

---

