---
title: "(Gnome) Panel shortcut not working"
date: 2011-03-16
forum: Desktop Environments
---

### Post by rschauer on 2011-03-16
Hi all,

I've been using Ubuntu for years now, and I don't think I've ever seen this problem before. I've given as much relevant detail as I can think of below; please let me know if anything else can help.

On Ubuntu 10.10 (32-bit), I have compiled TOra 2.1.2 from source (obtained from the repo) to enable Oracle support. I need to run it socksified, which works just fine by executing it from the terminal:

```
toxsocks tora
```However, a panel shortcut using that exact command doesn't launch anything.

I don't think it has to do with the `toxsocks` part, as I have a Firefox launcher using a similar command working perfectly:

```
toxsocks firefox -no-remote -P *username*
```And, for the record:
```
$ which toxsocks
/usr/bin/toxsocks
$ which tora
/usr/bin/tora
$ which firefox
/usr/bin/firefox

```I've tried searching for a solution, but the only results I've found so far are for users who had their command entered improperly, misconfigured file associations, etc. Any ideas on this one?

Thanks in advance. :-)

---

### Post by rschauer on 2011-03-16
A user on another forum I posted this on suggested creating an entry in the main menu (stating that he'd had a similar problem in 10.10), testing that, and creating the panel shortcut from that if it worked. I created a menu entry, and no, it did not work.

So what is it about running this particular command from a launcher instead of the terminal? The only thing terribly different about the application is that it was compiled from source; the resulting .deb was installed normally and is recognized by the package manager. `which` indicates it's in the path. I'm not sure what else to try... ?

By the way, I have also logged out/in and even rebooted since installing TOra. Nothing. It should also be noted that when I had the regular version of TOra installed from the repo, the shortcut worked fine.

---

### Post by Krytarik on 2011-03-16
You may try putting the command in the launcher that way:
```
sh -c "toxsocks tora"
```

Explanation: When you run commands from a launcher, they run in a different environment than if you run them in a terminal/console. The latter run in the shell, whereas the launcher runs them in more simple environment. Because of this, some commands which run fine in a terminal don't work when run from a launcher. The prefix "sh -c" tells the launchner to run the enclosed command(s) in the shell. But imo your command should also work without it. Just try it.

Btw., it doesn't matter at all where the launcher is located, generally.

---

### Post by rschauer on 2011-03-19
> **Krytarik said:**
> You may try putting the command in the launcher that way:
```
sh -c "toxsocks tora"
```

Works! That's really interesting; I don't quite understand why that was needed for TOra but not Firefox. I do know what you're saying, though, as I'm pretty familiar with shell environments (having used Linux personally for a number of years, and on the job for a couple of years now).

It must have something to do with the fact that TOra was built from source and installed from the resulting .deb. I'm not sure why it would, but I do know that the exact same launcher command (`toxsocks tora`) worked fine when I had TOra installed from the repo.

Problem solved, at any rate. Thanks very much!

---

### Post by Krytarik on 2011-03-19
In fact, it's also not quite clear to me why a similar combined command with Firefox works, but not with TOra. If there is indeed a difference self-compiled install and the packaged version, which requires a shell environment in order to run properly, it should also not run from a launcher when called separately just that way:
```
tora
```
Could you please try it, if it would run at all that way generally!?

---

### Post by rschauer on 2011-03-19
OK, now it really just got weird.

I tried it with just the command `tora` and it DID work. Then, just for kicks, I tried `toxsocks tora` again. Guess what? IT WORKS NOW.

I am now thoroughly confused. Maybe one of yesterday's updates fixed something?

---

### Post by Krytarik on 2011-03-20
That's indeed weird!
> **rschauer said:**
> Maybe one of yesterday's updates fixed something?
Well, you may check apt's history, if you find some which seems to be even remotely related. ;-)

---

