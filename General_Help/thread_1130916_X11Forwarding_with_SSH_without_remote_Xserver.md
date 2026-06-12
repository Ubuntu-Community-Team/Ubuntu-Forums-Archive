---
title: "X11Forwarding with SSH without remote Xserver"
date: 2009-04-20
forum: General Help
---

### Post by Dr Small on 2009-04-20
People have said that it can be done, so I'm trying to do it myself, but haven't had much luck with it.

My remote server (headless) is just CLI and does not have Xserver installed on it. It has SSH connection, though.

My desktop (has Xserver, of course) is attempting to connect to the server (with the -X flag) and forward the output of my conky script to my desktop.

So, to begin, my Server's SSHd config includes these lines:
```
X11Forwarding yes
X11DisplayOffset 10
```

I connect to the server:
```
[drsmall@darkghost]$ ssh -X drsmall@mycroft
drsmall@mycroft:~$ echo $DISPLAY

drsmall@mycroft:~$ conky -c bin/conky/1
Conky: can't open display: 
drsmall@mycroft:~$ 
```

As you can see, it can not open the display (the nonexistent one). Even if I set $DISPLAY to something like ":0", it still complains. I feel as though I am missing something obvious, but I just don't know what.

---

### Post by albandy on 2009-04-20
have you restarted the sshd daemon in the server?
sudo /etc/init.d/ssh restart

---

### Post by Dr Small on 2009-04-20
> **albandy said:**
> have you restarted the sshd daemon in the server?
sudo /etc/init.d/ssh restart
Yes, I have.

---

### Post by rockhopper on 2009-04-20
Can you try:
```

ssh -X -vv drsmall@mycroft "conky -c bin/conky/1"

```

and paste its output?

---

### Post by Dr Small on 2009-04-20
> **rockhopper said:**
> Can you try:
```

ssh -X -vv drsmall@mycroft "conky -c bin/conky/1"

```

and paste its output?
Sure:
```
[drsmall@darkghost ~]$ ssh -X -vv drsmall@mycroft "conky -c bin/conky/1"
OpenSSH_4.7p1, OpenSSL 0.9.8h 28 May 2008
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to mycroft [192.168.0.70] port 22.
debug1: Connection established.
debug1: identity file /home/drsmall/.ssh/identity type -1
debug1: identity file /home/drsmall/.ssh/id_rsa type -1
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug2: key_type_from_name: unknown key type '-----END'
debug1: identity file /home/drsmall/.ssh/id_dsa type 2
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.3p2 Debian-9etch3
debug1: match: OpenSSH_4.3p2 Debian-9etch3 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha256,diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,umac-64@openssh.com,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: none,zlib@openssh.com,zlib
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: kex_parse_kexinit: diffie-hellman-group-exchange-sha1,diffie-hellman-group14-sha1,diffie-hellman-group1-sha1
debug2: kex_parse_kexinit: ssh-rsa,ssh-dss
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,arcfour128,arcfour256,arcfour,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: hmac-md5,hmac-sha1,hmac-ripemd160,hmac-ripemd160@openssh.com,hmac-sha1-96,hmac-md5-96
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: none,zlib@openssh.com
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: 
debug2: kex_parse_kexinit: first_kex_follows 0 
debug2: kex_parse_kexinit: reserved 0 
debug2: mac_setup: found hmac-md5
debug1: kex: server->client aes128-cbc hmac-md5 none
debug2: mac_setup: found hmac-md5
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug2: dh_gen_key: priv key bits set: 128/256
debug2: bits set: 490/1024
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host 'mycroft' is known and matches the RSA host key.
debug1: Found key in /home/drsmall/.ssh/known_hosts:1
debug2: bits set: 519/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/drsmall/.ssh/identity ((nil))
debug2: key: /home/drsmall/.ssh/id_rsa ((nil))
debug2: key: /home/drsmall/.ssh/id_dsa (0x8095170)

debug1: Authentications that can continue: publickey,password
debug1: Next authentication method: publickey
debug1: Trying private key: /home/drsmall/.ssh/identity
debug1: Trying private key: /home/drsmall/.ssh/id_rsa
debug1: Offering public key: /home/drsmall/.ssh/id_dsa
debug2: we sent a publickey packet, wait for reply
debug1: Server accepts key: pkalg ssh-dss blen 434
debug2: input_userauth_pk_ok: fp df:52:61:f8:59:ab:66:8d:28:33:3c:99:1d:da:ed:2a
debug1: read PEM private key done: type DSA
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug2: channel 0: send open
debug1: Entering interactive session.
debug2: callback start
debug2: x11_get_proto: /usr/bin/xauth -f /tmp/ssh-awLDFF4406/xauthfile generate :0.0 MIT-MAGIC-COOKIE-1 untrusted timeout 1200 2>/dev/null
debug2: x11_get_proto: /usr/bin/xauth -f /tmp/ssh-awLDFF4406/xauthfile list :0.0 2>/dev/null
debug1: Requesting X11 forwarding with authentication spoofing.
debug2: channel 0: request x11-req confirm 0
debug2: client_session2_setup: id 0
debug1: Sending environment.
debug1: Sending command: conky -c bin/conky/1
debug2: channel 0: request exec confirm 0
debug2: fd 3 setting TCP_NODELAY
debug2: callback done
debug2: channel 0: open confirm rwindow 0 rmax 32768
debug1: Remote: No xauth program; cannot forward with spoofing.
debug2: channel 0: rcvd adjust 131072
debug2: channel 0: rcvd ext data 7
Conky: debug2: channel 0: written 7 to efd 6
debug2: channel 0: rcvd ext data 20
debug2: channel 0: rcvd ext data 1
debug1: client_input_channel_req: channel 0 rtype exit-status reply 0
debug2: channel 0: rcvd eof
debug2: channel 0: output open -> drain
debug2: channel 0: rcvd close
debug2: channel 0: close_read
debug2: channel 0: input open -> closed
debug2: channel 0: obuf_empty delayed efd 6/(21)
can't open display: 
debug2: channel 0: written 21 to efd 6
debug2: channel 0: obuf empty
debug2: channel 0: close_write
debug2: channel 0: output drain -> closed
debug2: channel 0: almost dead
debug2: channel 0: gc: notify user
debug2: channel 0: gc: user detached
debug2: channel 0: send close
debug2: channel 0: is dead
debug2: channel 0: garbage collecting
debug1: channel 0: free: client-session, nchannels 1
debug1: Transferred: stdin 0, stdout 0, stderr 0 bytes in 0.1 seconds
debug1: Bytes per second: stdin 0.0, stdout 0.0, stderr 0.0
debug1: Exit status 1
```

---

### Post by kpatz on 2009-04-20
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/51774](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/51774)

You'll need to install xauth on the server you're ssh-ing to.

---

### Post by gtr32 on 2009-04-20
Install xauth on the remote machine: sudo apt-get install xorg-x11-xauth

---

### Post by Dr Small on 2009-04-20
Ok, so I installed xauth and now when I ssh in, it gives me a DISPLAY variable of localhost:10.0, but conky dies now. (Hey, conky is the only GUI type application on the server, and I don't have anything else to test...)

```
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x6a52fd
  Serial number of failed request:  79
  Current serial number in output stream:  80

```

There is nothing wrong with the conky script. It's running on my desktop right now, so it works...

---

### Post by ddjjzz on 2009-07-20
It seems the problem is in /etc/hosts. Try to remove unnecessary strings from there. Here is my /etc/hosts for example:
```
127.0.0.1       localhost
127.0.1.1       dharma.ru
```

P.S. I'm sure I'm late with this answer. But I've faced this problem just hour ago. Hope it might be heplful for someone.

---

