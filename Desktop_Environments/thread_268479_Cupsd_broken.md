---
title: "Cupsd broken?"
date: 2006-09-30
forum: Desktop Environments
---

### Post by jago25_98 on 2006-09-30
I've upgraded the cups daemon but it's still crashing? I'm now upgrading everything to try and fix it. What could be causing this?

```
root@isolated:~ # /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd         [ ok ]
root@isolated:~ #   

root@isolated:~ # cupsd
cupsd: Child exited with status 99!
root@isolated:~ #   
```  

By coinsidance I though I'd try the ssh server but even that it isn't running? Stange!

```
root@isolated:~ # /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...           [ ok ]
root@isolated:~ #

root@isolated:~ # sshd
sshd re-exec requires execution with an absolute path
root@isolated:~ # 
```

The annoying thing with all this is the init scripts are giving `ok` messages.

I have now enabled debug in cupsd.conf and read the log file to find it complaining that it can't bind to 127.0.0.1:631, no firewall so that's strange. So I disabled that line in cupsd.conf and tried again. This time, no complaint but it's still listening on 0:631.

Now I tried the KDE print manager in kcontrol panel and it's frozen again on `initialising manager`.... 

In fact, any attempt to communicate with cups results in a crash, as an example:

```
root@isolated:/etc/cups # lpadmin -u allow:user
```

just never completes the command


What a pain, we now need printing in the office as Windows is messed up :/

---

### Post by mitch.c on 2006-09-30
> **jago25_98 said:**
> I've upgraded the cups daemon but it's still crashing? I'm now upgrading everything to try and fix it. What could be causing this?

```
root@isolated:~ # /etc/init.d/cupsys start
 * Starting Common Unix Printing System: cupsd         [ ok ]
root@isolated:~ #   

root@isolated:~ # cupsd
cupsd: Child exited with status 99!
root@isolated:~ #   
```

Cupsd should be running, as indicated by the [ok] when you ran the init script. When you try to run cupsd from the shell, it exits with an error because you aren't passing the correct parameters and/or becuase it's already running.

> **jago25_98 said:**
> By coinsidance I though I'd try the ssh server but even that it isn't running? Stange!

```
root@isolated:~ # /etc/init.d/ssh restart
 * Restarting OpenBSD Secure Shell server...           [ ok ]
root@isolated:~ #

root@isolated:~ # sshd
sshd re-exec requires execution with an absolute path
root@isolated:~ # 
```

Ditto. If you want to test sshd, try starting an ssh session.
```
ssh localhost
```
Assuming you haven't change anthing in the config that wouldn't allow you to logon.

> **jago25_98 said:**
> The annoying thing with all this is the init scripts are giving `ok` messages.

Again, the messages are correct.

> **jago25_98 said:**
> I have now enabled debug in cupsd.conf and read the log file to find it complaining that it can't bind to 127.0.0.1:631, no firewall so that's strange. So I disabled that line in cupsd.conf and tried again. This time, no complaint but it's still listening on 0:631.

Now I tried the KDE print manager in kcontrol panel and it's frozen again on `initialising manager`.... 

In fact, any attempt to communicate with cups results in a crash, as an example:

```
root@isolated:/etc/cups # lpadmin -u allow:user
```

just never completes the command
Can't help you with kde, but your lpadmin syntax is wrong. It should be:
```
# replace <nameofyourprinter> and <username> with the appropriate info
lpadmin -p <nameofyourprinter> -u allow:<username>
```
Maybe you should man lpadmin; -u is an option to -p. Obviously you need to replace <nameofyourprinter> and <username> with the appropriate info. If you don't have a printer set up yet, let me know and I'll post some help.

So far, it appears your problems (exluding possibly the KDE print manager), are a misunderstanding in your expecations.

---

### Post by jago25_98 on 2006-10-01
ok, I can't connect to 127.0.0.1:637, port 22 or anything at all.

And nmap can't can 127.0.0.1 with no options,

got to be something in the Ubuntu news related to the zero ports policy I've missed

---

