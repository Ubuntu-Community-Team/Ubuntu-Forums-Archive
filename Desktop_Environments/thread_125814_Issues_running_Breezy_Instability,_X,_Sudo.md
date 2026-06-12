---
title: "Issues running Breezy: Instability, X, Sudo"
date: 2006-02-04
forum: Desktop Environments
---

### Post by thechris on 2006-02-04
i've had nothing but problems with ubuntu, further, my questions typically stay unanswered.  every day, the computer just goes crazy.  i try to open an app, and X crashes.  i try to download a debain ISO and wget segfaults.

and the 'no root' thing just gets in the way.  it seems i have to sudo to do commands that don't require root access.

this is not a hardware issue either.  i think it has to do with needing to run too many things with sudo, even when there is no reason.

also, i cannot cleanly shutdown or reboot...

maybe i'll take a look at dapper sometime, but this is just getting ridiculous.  i've been trying to get some work done and end up just fighting with ubuntu for hours...

---

### Post by Stormy Eyes on 2006-02-04
[QUOTE=thechris]i've had nothing but problems with ubuntu, further, my questions typically stay unanswered.  every day, the computer just goes crazy.  i try to open an app, and X crashes.  i try to download a debain ISO and wget segfaults.[/QUOTE]

You sure it's not a hardware issue? X shouldn't just crash, unless you screwed up the config. Neither should wget.

---

### Post by aysiu on 2006-02-04
[QUOTE=thechris]
this is not a hardware issue either.  i think it has to do with needing to run too many things with sudo, even when there is no reason.[/QUOTE] It sounds like a hardware issue to me. If you have X crashing that often, it's only one of three things:

1. Something's wrong with the OS
2. You screwed up the OS by installing something bad
3. Your hardware's busted

I can tell you now it's not Breezy. If it were, there would be threads all over the place about this problem. It's the first I've heard of it.

P.S. I run commands with *sudo* several times a day--no problems here.

---

### Post by mstlyevil on 2006-02-04
[QUOTE=thechris]i've had nothing but problems with ubuntu, further, my questions typically stay unanswered.  every day, the computer just goes crazy.  i try to open an app, and X crashes.  i try to download a debain ISO and wget segfaults.

and the 'no root' thing just gets in the way.  it seems i have to sudo to do commands that don't require root access.

this is not a hardware issue either.  i think it has to do with needing to run too many things with sudo, even when there is no reason.

also, i cannot cleanly shutdown or reboot...

maybe i'll take a look at dapper sometime, but this is just getting ridiculous.  i've been trying to get some work done and end up just fighting with ubuntu for hours...[/QUOTE]

You can enable root by entering this command in the terminal.

```
sudo passwd root
```

After you create a password root will be enabled. I have run with sudo with no problems whatsoever. It is rare that I can not do with sudo what I could do as su (root). I believe it is a hardware issue because most people do not have those issues upon a clean install. (Unless they have done something to break their system.) Sudo is the same system OSX uses and it works just fine for them also. How many times have you tried reinstalling Ubuntu? maybe a fresh install will clear up the problem.

---

### Post by gord on 2006-02-04
id also recomened running memtest, it should be on the grub menu

---

### Post by tom-ubuntu on 2006-02-05
[QUOTE=gord]id also recomened running memtest, it should be on the grub menu[/QUOTE]
I would recommend running a memory test aswell. This all sounds very strange; don't believe it is Ubuntu's fault.....

---

### Post by chimera on 2006-02-05
lol, it seems creating a whining thread is the only way to get help around here :D

---

### Post by thechris on 2006-02-05
memory is fine.  gentoo worked fairly well.  it fared better then ubuntu at least.  i just got sick of setting things up all the time in gentoo.

debian has issues with sata, so i haven't been able to make the switch.

i'm pretty sure it has to do with the command:

sudo startx -- --config=~/xorg.1.conf :1

which fails for magic cookie errors when it decides to start fluxbox on :0 (which it obviously has no permission to do).

i usually try a simple:  sudo startx -- :1

if i do this from :0, then i can no longer get apps to run on :0.
if i do it from the cli, things work for a bit.  but it seems like it eventually crashes.

but there is no need to run sudo to run startx.  yet it seems to be the only way to get startx to work.

for those who now want to ask about "why use startx" -- i want a second X11 session with specific and different settings for use with an engineering application.    this can be done in X11 and the -- :1 tells X to create a second session and load commands from .xinitrc.

and the X11 issue is not the only issue.

i am fairly close to moving back to gentoo and just setting up fluxbox to make it a fast install.

---

### Post by thechris on 2006-02-05
[QUOTE=mstlyevil]You can enable root by entering this command in the terminal.

```
sudo passwd root
```

How many times have you tried reinstalling Ubuntu? maybe a fresh install will clear up the problem.[/QUOTE]

i now have a root account.  but i didn't want to run X11 with root privledges in the first place, so having a dedicated account with root access doesn't help.

this is a fresh install, minus the technologies i need to use -- nvidia, shfs, xfce.  the install has pretty much lasted 1 week.  well, not a full week, more like 3 days, but i haven't installed anything over it yet.

---

### Post by RAOF on 2006-02-05
[QUOTE=thechris]i now have a root account.  but i didn't want to run X11 with root privledges in the first place, so having a dedicated account with root access doesn't help.

this is a fresh install, minus the technologies i need to use -- nvidia, shfs, xfce.  the install has pretty much lasted 1 week.  well, not a full week, more like 3 days, but i haven't installed anything over it yet.[/QUOTE]
X gets run with root privs whether you want to or not, as far as I know.  Either you sudo startx, or the X server is setuid root.  It (stupidly) needs root privs to do all the funky graphics driver stuff that should be in the kernel ;)

---

