---
title: "Can't connect to openvpn"
date: 2015-12-10
forum: Fedora/RedHat and derivatives
---

### Post by Thee on 2015-12-10
Hi,

I tried various suggestions found on the net, I moved the ca.crt file to ~/.cert folder, tried disabling SElinux, etc., but nothing seems to work. It just says "Connection failed" when I try to connect to OpenVPN.
When using the command:

```
sudo journalctl -f
```

I see the following:

```

Dec 10 15:02:02 thee NetworkManager[864]: <info>  Starting VPN service 'openvpn'...
Dec 10 15:02:02 thee NetworkManager[864]: <info>  VPN service 'openvpn' started (org.freedesktop.NetworkManager.openvpn), PID 2055
Dec 10 15:02:02 thee NetworkManager[864]: modprobe: FATAL: Module tun not found in directory /lib/modules/4.2.3-300.fc23.x86_64
Dec 10 15:02:02 thee NetworkManager[864]: <info>  VPN service 'openvpn' appeared; activating connections
Dec 10 15:02:02 thee NetworkManager[864]: <info>  VPN plugin state changed: starting (3)
Dec 10 15:02:02 thee NetworkManager[864]: (nm-openvpn-service:2055): nm-openvpn-WARNING **: Directory '/var/lib/openvpn/chroot' not usable for chroot by 'nm-openvpn', openvpn will not be chrooted.
Dec 10 15:02:02 thee NetworkManager[864]: nm-openvpn-Message: openvpn started with pid 2062
Dec 10 15:02:02 thee NetworkManager[864]: <info>  VPN connection 'vpnde' (ConnectInteractive) reply received.
Dec 10 15:02:02 thee nm-openvpn[2062]: OpenVPN 2.3.8 x86_64-redhat-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Aug  4 2015
Dec 10 15:02:02 thee nm-openvpn[2062]: library versions: OpenSSL 1.0.2e-fips 3 Dec 2015, LZO 2.08
Dec 10 15:02:03 thee nm-openvpn[2062]: WARNING: No server certificate verification method has been enabled.  See http://openvpn.net/howto.html#mitm for more info.
Dec 10 15:02:03 thee nm-openvpn[2062]: NOTE: the current --script-security setting may allow this configuration to call user-defined scripts
Dec 10 15:02:03 thee nm-openvpn[2062]: NOTE: UID/GID downgrade will be delayed because of --client, --pull, or --up-delay
Dec 10 15:02:03 thee nm-openvpn[2062]: UDPv4 link local: [undef]
Dec 10 15:02:03 thee nm-openvpn[2062]: UDPv4 link remote: [AF_INET]62.113.224.211:1194
Dec 10 15:02:03 thee nm-openvpn[2062]: [pmvpn3] Peer Connection Initiated with [AF_INET]62.113.224.211:1194
Dec 10 15:02:05 thee nm-openvpn[2062]: ERROR: Cannot open TUN/TAP dev /dev/net/tun: No such device (errno=19)
Dec 10 15:02:05 thee nm-openvpn[2062]: Exiting due to fatal error
Dec 10 15:02:05 thee NetworkManager[864]: (nm-openvpn-service:2055): nm-openvpn-WARNING **: openvpn exited with error code 1
Dec 10 15:02:05 thee NetworkManager[864]: <warn>  VPN plugin failed: connect-failed (1)
Dec 10 15:02:05 thee NetworkManager[864]: <info>  VPN plugin state changed: stopped (6)
Dec 10 15:02:05 thee NetworkManager[864]: <info>  VPN plugin state change reason: unknown (0)
Dec 10 15:02:05 thee NetworkManager[864]: <warn>  error disconnecting VPN: Could not process the request because no VPN connection was active.

```

Any suggestions on how to fix this problem?
Thanks

---

### Post by QDR06VV9 on 2015-12-10
Well for me a couple of things were needed..
```
$su -
#yum install NetworkManager-openvpn NetworkManager-openvpn-gnome
#systemctl restart NetworkManager

```
If you have done this already then that is great if not it is needed.
Then this fixed my issue by running the following commands :
allow this access for now by executing:
```
# grep openvpn /var/log/audit/audit.log | audit2allow -M mypol
# semodule -i mypol.pp
```
Then made adjustments in the firewall
```
firewall-cmd --direct --add-rule ipv4 filter INPUT 0 -p gre -j ACCEPT
firewall-cmd --direct --add-rule ipv6 filter INPUT 0 -p gre -j ACCEPT
firewall-cmd --reload
```
And there is more info below
[https://docs.fedoraproject.org/en-US/Fedora/18/html/System_Administrators_Guide/sec-Establishing_a_VPN_Connection.html](https://docs.fedoraproject.org/en-US/Fedora/18/html/System_Administrators_Guide/sec-Establishing_a_VPN_Connection.html)
Good Luck, I will try to watch this thread today, but will be in and out most of the afternoon.
Kind regards

---

### Post by Thee on 2015-12-10
Hi,
thanks for your input, I tried what you suggested, but the problem remains the same. The problem seems to be here:

```
Dec 10 15:02:05 thee nm-openvpn[2062]: ERROR: Cannot open TUN/TAP dev /dev/net/tun: No such device (errno=19)
```

But I have no idea what that means. Any other suggestions?

---

### Post by Thee on 2015-12-10
Ok I solved the problem: I'm dual-booting Fedora with Ubuntu, and on  Ubuntu I got a kernel update which triggered GRUB update, which then  detected and added a wrong kernel in the GRUB menu list that caused this  issue and an audio issue too. I just switched to the correct kernel and  everything is working now.
Thanks a lot for your help ;)

---

### Post by QDR06VV9 on 2015-12-10
Nice Detective work!! Great Discovery.
As I was coming in to check on you it hit me that I had never seen that error before.
```
[COLOR=#000000][FONT=Ubuntu Mono]ERROR: Cannot open TUN/TAP dev /dev/net/tun: No such device (errno=19)[/FONT][/COLOR]
```
And was going to ask if you were dual booting, But you are good roll now..
Cheers and good work:D

---

