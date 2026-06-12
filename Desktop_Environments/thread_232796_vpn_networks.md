---
title: "vpn networks"
date: 2006-08-09
forum: Desktop Environments
---

### Post by walshie on 2006-08-09
hi my name is stephen. i am at university and have just installed linux for the first time.
i live on campus and i am forced to conect to the internet via a vpn. how do i can do this on linux remebering that i cant connect to the internet on my linux computer to install any programs though synaptic manager. any help with this would be appriceated.

---

### Post by kaffelars on 2006-08-09
First of all, you need a VPN client.
There are some open source VPN clients (in the apt repos :-( ), I think one of them is called OpenVPN.

The university I went to used Cisco VPN clients. That client is not open source, but the university should provide it for its users. It's also available for both Windows and Linux (and Mac).

I suggest that you first talk to the university to get all settings etc., and then use the client they provide or use another computer to download OpenVPN and try that.

---

### Post by bigken on 2006-08-09
This might be what your looking its in synaptics VPNC ;)

Cisco-compatible VPN client
vpnc is a VPN client compatible with cisco3000 VPN Concentrator (also
known as Cisco's EasyVPN equipment). vpnc runs entirely in userspace
and does not require kernel modules except of the tun driver to
communicate with the network layer.

It supports most of the features needed to establish connection to the
VPN concentrator: MD5 and SHA1 hashes, 3DES and AES ciphers, PFS and
various IKE DH group settings.

---

