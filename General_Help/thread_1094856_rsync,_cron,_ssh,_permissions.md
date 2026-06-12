---
title: "rsync, cron, ssh, permissions"
date: 2009-03-13
forum: General Help
---

### Post by RavX on 2009-03-13
Hi everyone, thanks for taking the time to read through this post. Please allow me to preface my question by stating that I am still relatively unfamiliar with linux, especially the command line interface. If I'm doing anything wrong, do not hesitate to scold my novice ways.

My goal: I am trying to get rsync (over ssh) to work using cron. (Essentially, I am just making scheduled backups to another computer on my LAN).

My problem: The ssh script works when executed from the command line (gnome-terminal), but fails to work when executed as a cron task. 
The script itself is executed, but I receive a "permission denied" error from rsync - essentially SSH is not letting me log in. (I use ssh keys to log in, not password login).

Hypothesis: I've googled a bunch on this, with other people having similar problems, (but I was not able to extract a solution). It seems that the problem might be due to cron not running as the same user as I. (I guess when I execute commands in bash, it executes under my username, but not so under cron? As such, it creates a wealth of problems dealing with permissions etc.)

My own diagonstics:
-The backup script works fine when run in a terminal
-therefore, SSH is configured correctly, Logins are successful, Rsync parameters are configured correctly.
-Another backup script I wrote, this time rsyncing only to my local computer (and so not SSH into another computer on the LAN) works fine.
-therefore, cron executes the commands listed in crontab, so I don't have to worry about it being a problem of incorrect crontab configuration.

Some details:

My installation: Ubuntu 8.04 Desktop, for 64-bit. 

My network setup: I have two computers (local computer is Lebesgue, remote computer that I'm ssh-into is Fourier). I have set them up to use ssh-keys, and not using password authentication.

My crontab, as output by "crontab -u yun -l".

```

SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=yun
HOME=/home/yun/
USER=yun
LOGNAME=yun

* * * * * echo hello >> /home/yun/hello_from_cron.txt
* * * * * ./backuptest_local
* * * * * ./backuptest_remote >> /home/yun/cronlog.log 2>&1

```

The first command "echo hello..." is just a simple test to see if crontab even runs anything. It does.

The second, "./backuptest_local", is to see if cron executes rsync locally. It does. The script is as follows:
```

#!/bin/sh
RSYNC=/usr/bin/rsync
LPATH=/home/yun/test/
RPATH=/home/yun/test2/

$RSYNC -r -t -o -v -u -c $LPATH $RPATH

```


The third, "./backuptest_remote", is to see if cron execute rsync over SSH. It does not. The script:
```

#!/bin/sh
RSYNC=/usr/bin/rsync
LPATH=/home/yun/test/
RPATH=yun@Fourier:/home/yun/test/

$RSYNC -r -t -o -v -u -c -e 'ssh -p 2400 -v' $LPATH $RPATH

```

and the error it outputs to a logfile I've specified (/home/yun/cronlog.log):
```

OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config

debug1: Applying options for *

debug1: Connecting to Fourier [192.168.1.65] port 2400.

debug1: Connection established.

debug1: identity file /home/yun/.ssh/identity type -1

debug1: identity file /home/yun/.ssh/id_rsa type 1

debug1: identity file /home/yun/.ssh/id_dsa type -1

debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2

debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*

debug1: Enabling compatibility mode for protocol 2.0

debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2

debug1: SSH2_MSG_KEXINIT sent

debug1: SSH2_MSG_KEXINIT received

debug1: kex: server->client aes128-cbc hmac-md5 none

debug1: kex: client->server aes128-cbc hmac-md5 none

debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP

debug1: SSH2_MSG_KEX_DH_GEX_INIT sent

debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY

debug1: checking without port identifier

debug1: Host 'fourier' is known and matches the RSA host key.

debug1: Found key in /home/yun/.ssh/known_hosts:2

debug1: found matching key w/out port

debug1: ssh_rsa_verify: signature correct

debug1: SSH2_MSG_NEWKEYS sent

debug1: expecting SSH2_MSG_NEWKEYS

debug1: SSH2_MSG_NEWKEYS received

debug1: SSH2_MSG_SERVICE_REQUEST sent

debug1: SSH2_MSG_SERVICE_ACCEPT received

debug1: Authentications that can continue: publickey

debug1: Next authentication method: publickey

debug1: Trying private key: /home/yun/.ssh/identity

debug1: Offering public key: /home/yun/.ssh/id_rsa

debug1: Server accepts key: pkalg ssh-rsa blen 533

debug1: PEM_read_PrivateKey failed

debug1: read PEM private key done: type <unknown>

debug1: read_passphrase: can't open /dev/tty: No such device or address

debug1: Trying private key: /home/yun/.ssh/id_dsa

debug1: No more authentication methods to try.

Permission denied (publickey).

rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(454) [sender=2.6.9]

```

Just for comparison, I thought I'd display the output of an SSH login session through the terminal:

Results of "ssh -v yun@Fourier -p 2400" in gnome-terminal
```

yun@Lebesgue:~$ ssh -v yun@Fourier -p 2400
OpenSSH_4.7p1 Debian-8ubuntu1.2, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to Fourier [192.168.1.65] port 2400.
debug1: Connection established.
debug1: identity file /home/yun/.ssh/identity type -1
debug1: identity file /home/yun/.ssh/id_rsa type 1
debug1: identity file /home/yun/.ssh/id_dsa type -1
debug1: Remote protocol version 2.0, remote software version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: match: OpenSSH_4.7p1 Debian-8ubuntu1.2 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-cbc hmac-md5 none
debug1: kex: client->server aes128-cbc hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: checking without port identifier
debug1: Host 'fourier' is known and matches the RSA host key.
debug1: Found key in /home/yun/.ssh/known_hosts:2
debug1: found matching key w/out port
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering public key: /home/yun/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 533
debug1: Authentication succeeded (publickey).
debug1: channel 0: new [client-session]
debug1: Entering interactive session.
debug1: Sending environment.
debug1: Sending env LANG = en_US.UTF-8
Linux Fourier 2.6.24-23-generic #1 SMP Mon Jan 26 00:13:11 UTC 2009 i686


```


And that's all I've got.
Apologies for the long post; apologies for crappy code; apologies for breaking any forum rules (this is my first post).
And thank you so much for reading. I would really appreciate any insight at this point.

-Yun

---

### Post by heindsight on 2009-03-13
That crontab is your user crontab, so commands in there do run with as your user. 

The problem is with the following:
```
debug1: PEM_read_PrivateKey failed

debug1: read PEM private key done: type <unknown>

debug1: read_passphrase: can't open /dev/tty: No such device or address

```

Your ssh key is encrypted with a passphrase, normally when you ssh interactively from a terminal, ssh will either ask you to enter your passphrase or (in GNOME) the seahorse agent will unlock the key for you.

When your script is running under cron, there is no way for ssh to ask your passphrase and the agent is not available either.

The only solution I'm aware of (someone else might have a better idea) is to create a new unencrypted ssh key - ie. run
```
ssh-keygen
```
and give a blank passphrase (so just press return when asked for a passphrase)

---

### Post by RavX on 2009-03-13
Yes! That did the trick for me. Thank you so much.
I am now able to gain ssh access through cron.

However, I'm just curious as to the consequences of an empty passphrase. Doesn't that mean the ssh-key is unencrypted? For me personally it's not a big deal but on the other hand I guess I just don't know enough to form an opinion yet.

Your advice also led me to do some research on ssh-agent and keyring. Apparently people have gotten passphrased ssh-keys to work during cron, but I couldn't understand the instructions, and certainly could not make it work.

But thanks a bunch nonetheless!

---

### Post by heindsight on 2009-03-13
Yes, without a passphrase your private key is unencrypted. The main purpose of encrypting your private key with a passphrase is to provide some extra security in case someone somehow got hold of your private key. 

As long as you're careful to make sure no one can get their hands on your private key, having an unencrypted key shouldn't be too much of a problem though. As long as you don't do something silly, like putting your private key on a USB stick, the only way anyone can get access to your private key is if they already have access to your user account anyway.

---

