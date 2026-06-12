---
title: "VPN to LAN behind Symantec SGS"
date: 2006-06-23
forum: Desktop Environments
---

### Post by pchr on 2006-06-23
At work we've got a Symantec firewall and I'd like to be able to vpn in from my Linux box, vpnc keeps mentioning cisco a lot?  If someone knows of any good How-to's or can even just can confirm that it's possible (and with what client software) then let me know and I'll dig further.

Cheers.

---

### Post by aglauser on 2006-08-09
Hi,

I am trying to do something similar ... I've looked at kvpnc (which supports many different VPN protocols), but haven't gotten too far.  The Symantec SGS uses IPSec, which is built into the kernel, but can be set up using FreeSwan.

I hope that these names help you find something ... I'm a bit lost and two heads are better than one!

HTH,
Adam

---

### Post by dahlec on 2006-11-08
Hi,

I have had the same problem for a while and after a lot of trying and failing, I finally managed to get this working using racoon (directly, not using the racoon-tool) and ipsec-tools on Ubuntu dapper. I have included my config files below, just in case you are still wondering how to set this up.

Notes to the configuration:
In this example, the client has IP 10.0.0.2 and the SGS (360R) gateway 10.0.0.1. The key.txt file contains the VPN client user and the psk.txt holds the gateway IP and the pre-shared key. On the SGS side I created the client user with the pre-shared key, but I also had to enable dynamic VPN client tunnels and enter the same pre-shared key on the advanced tab of the VPN section (which makes me think you can't login with different user ids, but I haven't bothered testing this yet!) The gateway phase 1 id is set to IP address and the default policy to IKE default crypto strong.

racoon.conf:
###
path pre_shared_key "/etc/racoon/psk.txt";

remote 10.0.0.1 {
	exchange_mode aggressive;
	my_identifier keyid "/etc/racoon/key.txt";
	nonce_size 16;
	proposal_check claim;
	initial_contact off;
	proposal {
		encryption_algorithm 3des;
		hash_algorithm sha1;
		authentication_method pre_shared_key;
		dh_group 2;
	}
}
 
sainfo address 10.0.0.2/32 any address 0.0.0.0/0 any {
	pfs_group 2;
	lifetime time 480 minutes;
 	encryption_algorithm 3des;
 	authentication_algorithm hmac_sha1;
 	compression_algorithm deflate;
}
###

ipsec-tools.conf:
###
flush;
spdflush;

spdadd 10.0.0.2/32 0.0.0.0/0 any -P out ipsec
esp/tunnel/10.0.0.2-10.0.0.1/require;
spdadd 0.0.0.0/0 10.0.0.2/32 any -P in ipsec
esp/tunnel/10.0.0.1-10.0.0.2/require;
###


Cheers,
Charles

---

### Post by aglauser on 2006-11-23
> **dahlec said:**
> 
 
sainfo address 10.0.0.2/32 any address 0.0.0.0/0 any {
	pfs_group 2;
	lifetime time 480 minutes;
 	encryption_algorithm 3des;
 	authentication_algorithm hmac_sha1;
 	compression_algorithm deflate;
}
###

ipsec-tools.conf:
###
flush;
spdflush;

spdadd 10.0.0.2/32 0.0.0.0/0 any -P out ipsec
esp/tunnel/10.0.0.2-10.0.0.1/require;
spdadd 0.0.0.0/0 10.0.0.2/32 any -P in ipsec
esp/tunnel/10.0.0.1-10.0.0.2/require;
###


Cheers,
Charles

Hi Charles -
Thanks to your suggestions I've at least attempted to establish a connection.  If I'm understanding the above correctly, it is encrypting all of the traffic in and out of 10.0.0.2.  Is that correct?

I think I'll need to play around with this to get it to work in my situation.  I want my computer at home to connect to an SGS at work, so that my PC becomes part of the network.

Thanks again for your help,
Adam

---

