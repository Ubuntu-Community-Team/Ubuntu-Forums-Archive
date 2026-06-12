---
title: "Using SSH: How to run/open program or updates program/Ubuntu?"
date: 2008-01-03
forum: Desktop Environments
---

### Post by xdefconx on 2008-01-03
Hye all!

I would like to ask how we can do by using SSH client on others PC "to tell" my Ubuntu server to run some application and updating my Ubuntu version.

So what i need from SSH is:

a- updating my Ubuntu
b- to run Xchat/any IRC program

thanxs

---

### Post by PeterJS on 2008-01-03
> **xdefconx said:**
> Hye all!

I would like to ask how we can do by using SSH client on others PC "to tell" my Ubuntu server to run some application and updating my Ubuntu version.

So what i need from SSH is:

a- updating my Ubuntu

SSH works just like a local terminal so to upgrade your machine:
```

sudo apt-get update
sudo apt-get upgrade

```> 
b- to run Xchat/any IRC program

thanxsirssi is the king of command line irc clients. Running irssi inside of a screen on a high uptime machine, like say a server, that you have ssh access to is a great way to have an irc session that persists even when you aren't actively using it.
```

screen -S *Session_Name* irssi

```The session name can be what ever you like, I generally use a nice descriptive name like IRC. To detach the screen for later use press ctrl+a and then d. To reconnect to your screen session
```

screen -r *Session_name*

```

---

### Post by xdefconx on 2008-01-03
> **PeterJS said:**
> SSH works just like a local terminal so to upgrade your machine:
```

sudo apt-get update
sudo apt-get upgrade

```irssi is the king of command line irc clients. Running irssi inside of a screen on a high uptime machine, like say a server, that you have ssh access to is a great way to have an irc session that persists even when you aren't actively using it.
```

screen -S *Session_Name* irssi

```The session name can be what ever you like, I generally use a nice descriptive name like IRC. To detach the screen for later use press ctrl+a and then d. To reconnect to your screen session
```

screen -r *Session_name*

```


Thanxs bro, u really help me a lot heheh now start googling about irssi hehehe :guitar:

---

