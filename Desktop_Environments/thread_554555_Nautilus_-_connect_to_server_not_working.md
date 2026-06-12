---
title: "Nautilus - connect to server not working"
date: 2007-09-19
forum: Desktop Environments
---

### Post by musther on 2007-09-19
A few days ago (not sure if it was after an update), my two Feisty machines developed the same odd bug.  Nautilus cannot open a connection to anything.  Usually nautilus on my laptop opens an SSH connection to my desktop, now it says it's connecting and just hangs.  Similarly my desktop usually connects to my mythtv machine, now it does the same thing.  I also tried an ftp connection from the desktop, nothing.  FTP, SSH and SFTP all work from the terminal or other programs, but not nautilus.  Any ideas?

---

### Post by Aphax on 2007-09-19
I'm getting the exact same issue with my freshly installed Ubuntu machine (it's running Gutsy Ribbon Tribe 5). I have two machines, Hactar ( the Ubuntu machine), Magrathea (A gentoo box). Both have connectivity and can ping eachother, can ftp, ssh to eachother (from a terminal) and have the 'sftp' method setup (see sshd_config). They can even ftp:// to eachother through Nautilus, except SSH, this doesn't work. When I try, it will hang for about 15 seconds and then give a timeout error.

I've made sure to empty the ~/.ssh/known_hosts file on both hosts to prevent any kind of left-over signature conflicsts.

To see what was going on when I connected over sftp:// in Nautilus from my Ubuntu box to my Gentoo box, I set the debug level for sshd on the Gentoo box to DEBUG and monitored the syslog as the connection attempt came in, it gave the following:

```
Sep 19 12:13:17 magrathea sshd[18821]: Connection from 192.168.1.72 port 49122
Sep 19 12:13:17 magrathea sshd[18821]: debug1: Client protocol version 2.0; client software version OpenSSH_4.6p1 Debian-5
Sep 19 12:13:17 magrathea sshd[18821]: debug1: match: OpenSSH_4.6p1 Debian-5 pat OpenSSH*
Sep 19 12:13:17 magrathea sshd[18821]: debug1: Enabling compatibility mode for protocol 2.0
Sep 19 12:13:17 magrathea sshd[18821]: debug1: Local version string SSH-2.0-OpenSSH_4.7
Sep 19 12:13:17 magrathea sshd[18821]: debug1: PAM: initializing for "hans"
Sep 19 12:13:17 magrathea sshd[18821]: debug1: PAM: setting PAM_RHOST to "hactar.lan"
Sep 19 12:13:17 magrathea sshd[18821]: debug1: PAM: setting PAM_TTY to "ssh"
Sep 19 12:13:37 magrathea sshd[18821]: debug1: do_cleanup
Sep 19 12:13:37 magrathea sshd[18821]: debug1: PAM: cleanup

```

(192.168.1.72 is the Ubuntu box, hactar).

At 12:13:37 (where it does do_cleanup) the Ubuntu machine gave up and showed the "timeout" error.

I have no clue what is going on, maybe something with PAM? I'll keep investigating.

---

### Post by Aphax on 2007-09-19
Here's the DEBUG3 version of that log:

```

Sep 19 12:23:33 magrathea sshd[18959]: Connection from 192.168.1.72 port 58901
Sep 19 12:23:33 magrathea sshd[18959]: debug1: Client protocol version 2.0; client software version OpenSSH_4.6p1 Debian-5
Sep 19 12:23:33 magrathea sshd[18959]: debug1: match: OpenSSH_4.6p1 Debian-5 pat OpenSSH*
Sep 19 12:23:33 magrathea sshd[18959]: debug1: Enabling compatibility mode for protocol 2.0
Sep 19 12:23:33 magrathea sshd[18959]: debug1: Local version string SSH-2.0-OpenSSH_4.7
Sep 19 12:23:33 magrathea sshd[18959]: debug2: fd 3 setting O_NONBLOCK
Sep 19 12:23:33 magrathea sshd[18959]: debug2: Network child is on pid 18960
Sep 19 12:23:33 magrathea sshd[18959]: debug3: preauth child monitor started
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 0
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_moduli: got parameters: 1024 1024 8192
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_send entering: type 1
Sep 19 12:23:33 magrathea sshd[18959]: debug2: monitor_read: 0 used once, disabling now
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 4
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_sign
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_sign: signature 0x[removed]
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_send entering: type 5
Sep 19 12:23:33 magrathea sshd[18959]: debug2: monitor_read: 4 used once, disabling now
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 6
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_pwnamallow
Sep 19 12:23:33 magrathea sshd[18959]: debug3: Normalising mapped IPv4 in IPv6 address
Sep 19 12:23:33 magrathea sshd[18959]: debug3: Trying to reverse map address 192.168.1.72.
Sep 19 12:23:33 magrathea sshd[18959]: debug2: parse_server_config: config reprocess config len 218
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_pwnamallow: sending MONITOR_ANS_PWNAM: 1
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_send entering: type 7
Sep 19 12:23:33 magrathea sshd[18959]: debug2: monitor_read: 6 used once, disabling now
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 45
Sep 19 12:23:33 magrathea sshd[18959]: debug1: PAM: initializing for "hans"
Sep 19 12:23:33 magrathea sshd[18959]: debug1: PAM: setting PAM_RHOST to "hactar.lan"
Sep 19 12:23:33 magrathea sshd[18959]: debug1: PAM: setting PAM_TTY to "ssh"
Sep 19 12:23:33 magrathea sshd[18959]: debug2: monitor_read: 45 used once, disabling now
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 3
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_authserv: service=ssh-connection, style=
Sep 19 12:23:33 magrathea sshd[18959]: debug2: monitor_read: 3 used once, disabling now
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 48
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_pam_init_ctx
Sep 19 12:23:33 magrathea sshd[18959]: debug3: PAM: sshpam_init_ctx entering
Sep 19 12:23:33 magrathea sshd[18961]: debug3: PAM: sshpam_thread_conv entering, 1 messages
Sep 19 12:23:33 magrathea sshd[18961]: debug3: ssh_msg_send: type 1
Sep 19 12:23:33 magrathea sshd[18961]: debug3: ssh_msg_recv entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_send entering: type 49
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: monitor_read: checking request 50
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_answer_pam_query
Sep 19 12:23:33 magrathea sshd[18959]: debug3: PAM: sshpam_query entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: ssh_msg_recv entering
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_send entering: type 51
Sep 19 12:23:33 magrathea sshd[18959]: debug3: mm_request_receive entering
Sep 19 12:23:53 magrathea sshd[18959]: debug1: do_cleanup
Sep 19 12:23:53 magrathea sshd[18959]: debug1: PAM: cleanup
Sep 19 12:23:53 magrathea sshd[18959]: debug3: PAM: sshpam_thread_cleanup entering


```

EDIT: Actually it seems that I *can* connect from my Gentoo box to the Ubuntu box through sftp://, so it's just Ubuntu -> Gentoo that isn't working for me.
EDIT2: I can also connect to a third machine running FreeBSD from my Ubuntu box over sftp://

---

### Post by Aphax on 2007-09-19
I think I figured it out (at least for my case, not sure if you actually have the same problem), this being a fresh install I hadn't copied over my keys for key-auth, so it was trying to logon using the normal method, but since I have configured my gentoo box to authenticate by my private key passphrase instead of a normal user password through PAM, gnome-vfs chokes up. (Looking at the source it clearly doesn't seem capable of handling the passphrase prompt "SSH passphrase:":  [http://svn.gnome.org/viewcvs/gnome-vfs/trunk/modules/sftp-method.c?annotate=5263](http://svn.gnome.org/viewcvs/gnome-vfs/trunk/modules/sftp-method.c?annotate=5263) (see line 1314)

---

### Post by c.los on 2008-05-24
I was having the same problem, was working perfectly fine before then I upgraded and it broke. I also did a fresh install on my laptop and nautilus still wouldn't connect to ftp/sftp like it used to.

All I had to do was install sshfs and curlftpfs (fuse for mounting ssh/sftp and ftps). Not sure what happened during the upgrade because it was already installed, so I removed and then installed again and it worked!

Remove old sshfs & curlftpfs (skip if fresh install):
```
sudo apt-get remove sshfs curlftpfs
```

To install sshfs & curlftpfs:
```
sudo apt-get install sshfs curlftpfs
```

Of course if you only use one you don't have to install both.

Hope this helps..

---

