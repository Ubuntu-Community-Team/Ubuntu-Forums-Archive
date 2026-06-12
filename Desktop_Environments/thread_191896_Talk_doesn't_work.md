---
title: "Talk doesn't work"
date: 2006-06-08
forum: Desktop Environments
---

### Post by katiad on 2006-06-08
I did a fresh install of Dapper, and am a bit alarmed to find that talk no longer works. I use it frequently. Installed talk, talkd, and xinetd with no errors. This is what I get when I attempt to use talk:

> No Connection
Error on read from talk daemon: Connection refused. Press any key... 

Anybody know what's up with this?

(I have turned messages on [mesg y] for both parties.)

---

### Post by ns2048 on 2006-06-08
Hello,

Just do the following to get talk/ntalk working on your Dapper system.

**1. Paste the following lines into '/etc/xinetd.d/talk'**

# default: off
# description: The talk server accepts talk requests for chatting with users \
#       on other systems.
service talk
{
        flags                   = IPv4
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = nobody
        group                   = tty
        server                  = /usr/sbin/in.talkd
}

**2. Paste the following lines into '/etc/xinetd.d/ntalk'**

# default: off
# description: The ntalk server accepts ntalk connections, for chatting \
#       with users on different systems.
service ntalk
{
        flags                   = IPv4
        disable                 = no
        socket_type             = dgram
        wait                    = yes
        user                    = nobody
        group                   = tty
        server                  = /usr/sbin/in.ntalkd
}

**3. Restart xinetd**

ns2048@dapperhost:~$ sudo /etc/init.d/xinetd restart

Now talk should work between users who are logged in.

-- ns2048

---

### Post by katiad on 2006-06-08
Thanks! It worked - though just restarting xinetd didn't do the trick - had to reboot the whole computer. But it works again!

---

### Post by a_hippie on 2006-08-19
oh YES!  thanks for this post folks.  I just got it working on my box and my buddies amd64.  Very nice but it seems like apt-get talkd should have done this for us during install.

shrug


best regards!

---

### Post by a_hippie on 2006-08-19
but here's a dumb question:

what should I do with inetd.conf entries?

---

### Post by hayalci on 2006-10-06
They are obsolete :)

---

