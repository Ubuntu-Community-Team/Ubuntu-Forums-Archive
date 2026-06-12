---
title: "Can't forward Xwindows via ssh (&quot;No xauth program&quot;).."
date: 2012-04-16
forum: Desktop Environments
---

### Post by oldskool75 on 2012-04-16
I've done so much searching on this, it's ridiculous.. I didn't think I could exhaust all of Google's search results it threw at me, but I did.. still, no joy.

System
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

```

Associated packages:
```

openssh-server: 1:5.5p1-4ubuntu6
xauth: 1:1.0.4-1
X11: 1:7.5+6ubuntu3.1

```

sshd config (relevant bits):
```

X11Forwarding yes
X11UseLocalhost yes
X11DisplayOffset 10
AllowTcpForwarding yes
XAuthLocation /usr/bin/xauth

```

 * can **_successfully _**forward xwin from other servers

ssh session:
```

[client] &#8594; ssh -X -vvv user@server
OpenSSH_5.9p1, OpenSSL 0.9.8t 18 Jan 2012
debug1: Reading configuration data /etc/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to server [server_ip] port 22.
debug1: Connection established.
debug1: identity file /home/client_user/.ssh/id_rsa type -1
debug1: identity file /home/client_user/.ssh/id_rsa-cert type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.5p1 Debian-4ubuntu6
debug1: match: OpenSSH_5.5p1 Debian-4ubuntu6 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.9
debug2: fd 3 setting O_NONBLOCK
debug3: load_hostkeys: loading entries for host "server" from file "/home/client_user/.ssh/known_hosts   "
debug3: load_hostkeys: found key type RSA in file /home/client_user/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: order_hostkeyalgs: prefer hostkeyalgs: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.co   m,ssh-rsa
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: ecdh-sha2-nistp256,ecdh-sha2-nistp384,ecdh-sha2-nistp521,diffie-hellman-grou   p-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-   sha1
debug2: kex_parse_kexinit: ssh-rsa-cert-v01@openssh.com,ssh-rsa-cert-v00@openssh.com,ssh-rsa,ecdsa-sha2   -nistp256-cert-v01@openssh.com,ecdsa-sha2-nistp384-cert-v01@openssh.com,ecdsa-sha2-nistp521-cert-v01@op   enssh.com,ssh-dss-cert-v01@openssh.com,ssh-dss-cert-v00@openssh.com,ecdsa-sha2-nistp256,ecdsa-sha2-nist   p384,ecdsa-sha2-nistp521,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,b   lowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,b   lowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-s   ha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-sha2-256,hmac-sha2-256-96,hmac-s   ha2-512,hmac-sha2-512-96,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: zlib@openssh.com,zlib,none
debug2: kex_parse_kexinit: zlib@openssh.com,zlib,none
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diff   ie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,b   lowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,b   lowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh   .com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh   .com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit:
debug2: kex_parse_kexinit: first_kex_follows 0
debug2: kex_parse_kexinit: reserved 0
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-ctr hmac-md5 zlib@openssh.com
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-ctr hmac-md5 zlib@openssh.com
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 126/256
debug2: bits set: 498/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 36:5e:a2:9a:d7:a3:f9:a7:51:65:dc:0d:e3:e9:07:2b
debug3: load_hostkeys: loading entries for host "server" from file "/home/client_user/.ssh/known_hosts   "
debug3: load_hostkeys: found key type RSA in file /home/client_user/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug3: load_hostkeys: loading entries for host "server_ip" from file "/home/client_user/.ssh/known_hosts"
debug3: load_hostkeys: found key type RSA in file /home/client_user/.ssh/known_hosts:1
debug3: load_hostkeys: loaded 1 keys
debug1: Host 'server' is known and matches the RSA host key.
debug1: Found key in /home/client_user/.ssh/known_hosts:1
debug2: bits set: 510/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/client_user/.ssh/id_rsa (0x0)
debug1: Authentications that can continue: publickey,password
debug3: start over, passed a different list publickey,password
debug3: preferred hostbased,publickey,password,keyboard-interactive
debug3: authmethod_lookup publickey
debug3: remaining preferred: password,keyboard-interactive
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/client_user/.ssh/id_rsa
debug3: no such identity: /home/client_user/.ssh/id_rsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: keyboard-interactive
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
debug3: packet_send2: adding 64 (len 57 padlen 7 extra_pad 64)
debug2: we sent a password packet, wait for reply
debug1: Enabling compression at level 6.
debug1: Authentication succeeded (password).
**Authenticated to server ([server_IP]:22).**
debug1: channel 0: new [client-session]
debug3: ssh_session2_open: channel_new: 0
debug2: channel 0: send open
debug1: Requesting no-more-sessions@openssh.com
debug1: Entering interactive session.
debug2: callback start
**[COLOR="Red"]debug1: No xauth program.[/COLOR]**
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 1
debug1: Requesting authentication agent forwarding.
debug2: channel 0: request auth-agent-req@openssh.com confirm 0
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 100 id 0
**[COLOR="red"]X11 forwarding request failed on channel 0[/COLOR]**
debug2: channel_input_status_confirm: type 99 id 0
debug2: PTY allocation request accepted on channel 0
debug2: channel 0: rcvd adjust 2097152
debug2: channel_input_status_confirm: type 99 id 0
debug2: shell request accepted on channel 0
Linux server 2.6.35-32-server #66-Ubuntu SMP Mon Feb 13 21:21:41 UTC 2012 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to the Ubuntu Server!
 * Documentation:  http://www.ubuntu.com/server/doc

...

No mail.
Last login: Mon Apr 16 18:33:24 2012 from IP

#[18:45:43] user@server [~]> echo $DISPLAY

#[18:45:56] user@server [~]>


```

Now before you say, "Install xauth in the right place."

```


#[18:53:15] user@server [~]> strings `which sshd` | grep xauth
/usr/bin/xauth
...
#[18:53:19] user@server[~]> ls -lA `which xauth`
-rwxr-xr-x 1 root root 40K 2009-12-07 09:36 /usr/bin/xauth*
#[18:54:34] user@server[~]> ls -lA .Xauthority
-rw------- 1 user user 50 2012-04-13 14:39 .Xauthority
#[18:54:35] user@server [~]>

```


Someone **[COLOR="Red"]please [/COLOR]**tell me why this isn't working, or what I can do to provide more info to debug this?

This is frustrating the heck out of me...

Thanks!

---

### Post by oldskool75 on 2012-04-20
Is there any more info I can provide...?

---

### Post by markbl on 2012-04-20
When you log in user@server can you actually run xauth by hand? i.e. try "xauth list" and/or "xauth info".

Also trying deleting ~/.Xauthority then log out and log in again? (Maybe it is corrupt?)

---

### Post by oldskool75 on 2012-04-20
Hm... Well, that's interesting..

> 
#[22:33:26] user@server [~]> xauth list
user/unix:0  MIT-MAGIC-COOKIE-1  4249986180375380042499861803753800
#[22:33:39] user@server [~]> xauth info
Authority file:       /home/user/.Xauthority
File new:             no
File locked:          no
Number of entries:    1
Changes honored:      yes
Changes made:         no
Current input:        (argv):1
#[22:33:44] user@server [~]> mv .Xauthority .Xauthority.bak_00
#[22:34:12] user@server [~]> exit


Logging in again.. 

> 

# ssh -X -vvv user@server
...
debug1: Entering interactive session.
debug2: callback start
debug1: No xauth program.
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 1
debug1: Requesting authentication agent forwarding.
debug2: channel 0: request [email]auth-agent-req@openssh.com[/email] confirm 0
debug2: client_session2_setup: id 0
debug2: fd 3 setting TCP_NODELAY
debug2: channel 0: request pty-req confirm 1
debug2: channel 0: request shell confirm 1
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug2: channel_input_status_confirm: type 100 id 0
X11 forwarding request failed on channel 0
...

#[22:34:24] user@server [~]> ls -lA .Xauthority
[B][COLOR="Red"]ls: cannot access .Xauthority: No such file or directory
[/COLOR][/B]#[22:35:02] user@server [~]> xauth list
**_xauth:  creating new authority file /home/user/.Xauthority_**
#[22:35:29] user@server [~]>xauth info
**_xauth:  creating new authority file /home/user/.Xauthority_**
Authority file:       /home/user/.Xauthority
File new:             yes
File locked:          no
Number of entries:    **[COLOR="Red"]0[/COLOR]**
Changes honored:      yes
Changes made:         no
Current input:        (argv):1
#[22:35:36] user@server [~]> ls -lA .Xauthority
[B][COLOR="Red"]ls: cannot access .Xauthority: No such file or directory
[/COLOR][/B]

Looks like xuth does not create the file, even though it says it does.. 

And I have write permissions on my own home dir (755)..

Any more tips to try?
Running xauth with -v did not reveal any more info..

---

### Post by oldskool75 on 2012-04-20
Well, thanks markbl!

Based on what you suggested, I searched for the .Xauthority error, and came up with [this thread]("http://ubuntuforums.org/showthread.php?t=1575585")...

Which suggested to try this:

> 
X11UseLocalHost **[COLOR="Red"]no[/COLOR]**

(as counter-intuitive as it sounds)

Lo and behold, new .Xauthority file, $DISPLAY variable set, and X11 is now forwarding.. :confused:

Thanks for responding and putting me down the right track! :)

---

