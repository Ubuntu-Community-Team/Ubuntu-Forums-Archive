---
title: "Daemons being killed on  logout"
date: 2011-01-20
forum: Desktop Environments
---

### Post by f0rmat on 2011-01-20
How do I prevent ubuntu from killing my server daemons on user logout. I have the user irc which I run Unrealircd on but unfortunately I have to be logged into that user in terminal to keep it running, the moment i exit it loses connection in xchat.

---

### Post by Cheesehead on 2011-01-20
Well, the easy way is to have them started by root upon startup instead of by you upon login.

There are easy ways to do it:
  For example, a script in /etc/network/if-up.d 
  Another example, a command that uses 'sudo -u' to start the process as a different authorized user instead of the logged-in user

There are also complicated ways to do it if you need more control on when/how to start up (like listening for Upstart events or dBus messages).

---

### Post by psusi on 2011-01-20
I don't know what you are running, but if it is killed when you log out, then it isn't a daemon.

---

### Post by f0rmat on 2011-01-20
When I run ./unreal start it does this 

```
adam@archangel:~$ su irc
Password: 
irc@archangel:~$ ./Unreal3.2/unreal start
Starting UnrealIRCd
 _   _                      _ ___________  _____     _ 
| | | |                    | |_   _| ___ \/  __ \   | |
| | | |_ __  _ __ ___  __ _| | | | | |_/ /| /  \/ __| |
| | | | '_ \| '__/ _ \/ _` | | | | |    / | |    / _` |
| |_| | | | | | |  __/ (_| | |_| |_| |\ \ | \__/\ (_| |
 \___/|_| |_|_|  \___|\__,_|_|\___/\_| \_| \____/\__,_|
                           v3.2.8.1
                     using TRE 0.7.5 (LGPL)
                     using OpenSSL 0.9.8o 01 Jun 2010
                     using zlib 1.2.3.4

* Loading IRCd configuration ..
* Configuration loaded without any problems ..
* Loading tunefile..
* Initializing SSL.
* Dynamic configuration initialized .. booting IRCd.
---------------------------------------------------------------------
irc@archangel:~$ 
```

and stays running even after returning control but when I run 'exit' command or just close terminal then it ends the process I immediately lose server connection. I don't understand why, I have been using this system for ages on Ubuntu server and Ubuntu desktop a few times and never had the issue of needing to be logged in to maintain a server

---

### Post by psusi on 2011-01-20
The program is bugged and isn't disconnecting from the terminal.

---

### Post by f0rmat on 2011-01-20
Oh :| ok I'll have to check with the team at Unreal. Thanks for your help :)

---

### Post by f0rmat on 2011-01-20
I just checked in /var/log/syslog and found

Jan 21 03:24:45 archangel ltsp-cluster-accountmanager: Killing user "irc"

is that normal?

---

### Post by warg on 2011-01-20
> **psusi said:**
> The program is bugged and isn't disconnecting from the terminal.

Hello, I'm an official supporter of UnrealIRCd and have been for many years. This is the first I've heard of such an issue in the history of UnrealIRCd and I can assure you this is not an UnrealIRCd bug. 

@psusi just how much time or effort did you invest in coming to the conclusion this is an UnrealIRCd bug?

I cannot reproduce this issue on Ubuntu 10.10, 10.04, 9.10 or 9.04.

---

### Post by f0rmat on 2011-01-20
I did > sudo apt-get remove ltsp-cluster-accountmanager and now it doesn't kill the user started daemon on exit from su

---

### Post by psusi on 2011-01-21
Werid... ltsp is the linux terminal server project.  I've never messed with that.

Still though, if the program forks, disconnects from the tty, and starts a new process group, then it should be no different than any other daemon started at boot time, so that program shouldn't be able to find and kill it.

---

