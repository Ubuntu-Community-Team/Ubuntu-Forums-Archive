---
title: "sudo"
date: 2005-09-30
forum: Desktop Environments
---

### Post by Simian on 2005-09-30
Why can't I 'sudo kate' I get: Error: "/var/tmp/kdecache-ben" is owned by uid 1000 instead of uid 0. Link points to "/var/tmp/kdecache-root" 'kate: ERROR: Communication problem with kate, it probably crashed.' 

kdesu works though, is that what I'm supposed to use in Kubuntu? (I doubt this isn't the case)

---

### Post by mlomker on 2005-09-30
I've heard of that error before.  What I usually do when I'm in a terminal is to use the **su** command to become root, rather than using sudo.  I know that's a non-Ubuntu approach but it's more universal among linux variants.

---

### Post by geearf on 2005-10-01
[QUOTE=mlomker]I've heard of that error before.  What I usually do when I'm in a terminal is to use the **su** command to become root, rather than using sudo.  I know that's a non-Ubuntu approach but it's more universal among linux variants.[/QUOTE]
This might not work without a modification of the .Xsession

---

### Post by mlomker on 2005-10-01
> This might not work without a modification of the .Xsession

You either issue the **xhost +** command before **su**ing to root or do what I do...put the command into the ~/.bashrc file.

---

### Post by geearf on 2005-10-01
I have it in my .Xsession file, cause it seems to be the debian way to do so, but yes that is what I meant.

---

### Post by Simian on 2005-10-01
Sorry this has all gone over my head. The fact that I can't sudo kate implies that that something is wrong or not? And why doe kdesu kate work and not sudo kate?

I don't have a problem with su instead of sudo but I would like to know why sudo isn't always working?

---

### Post by geearf on 2005-10-01
can you do sudo kwrite ?

---

### Post by mlomker on 2005-10-01
[QUOTE=geearf]can you do sudo kwrite ?[/QUOTE]

I get the same error as the OP with Kate--kwrite does work.

I'd speculate that there's some kind of interprocess communication occuring that requires root permissions.  The program is looking an existing instance of kate rather than opening a second window.  If you have Kate already running (minimized in your taskbar) and then sudo it'll bring up the existing instance.

This is a bug and not something that you're doing wrong.

---

### Post by geearf on 2005-10-01
both sudo kate, and sudo kwrite work here

---

### Post by mlomker on 2005-10-01
> both sudo kate, and sudo kwrite work here

Not suprising.  The different versions of Ubuntu all behave a little differently.

1) On Hoary amd64 with KDE 3.4.1 it doesn't work.  
2) On Hoary i386 with KDE 3.5 beta it pops up a dialog box asking what X session I wanted it on and then opens it fine.  
3) On Breezy i386 with KDE 3.4.2 it doesn't work.

---

### Post by Simian on 2005-10-01
I see. Can you explain the difference between the sudo and kdesu commands. Or are they the same thing?

Thanks for helping out a noob.

---

### Post by mlomker on 2005-10-01
> Or are they the same thing?

I had thought that they were the same thing, but this seems to prove otherwise.

---

### Post by paxmark on 2005-10-02
I had been wondering about that also.

Kate will not work on kubuntu 5.04 on two machines via sudo.  Tried su for kate also on one - does not work also.

Kate gives me line numbers, I haven't figured out yet how to find the line numbers on pico-nano.

---

### Post by Gezzer on 2005-10-02
in a konsole try

kdesu kate

see if that works

sorry didn't realise that there where 2 pages ...

---

### Post by knappen on 2005-10-02
Perhaps you are not in the sudoers file. Have a look in /etc/sudoers

Remember to edit it with visudo.

Worth a try!

---

### Post by Simian on 2005-10-02
[QUOTE=knappen]Perhaps you are not in the sudoers file.[/QUOTE]


this is my sudoers contents:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin  ALL=(ALL) ALL

can anyone see if it's all in order?

---

### Post by Simian on 2005-10-02
I guess that it must be fine as I can sudo apt-get......

---

### Post by knappen on 2005-10-03
I also had some problems with sudo, but it was fixed when I added myself to the sudoers file.

This link will explain how to edit the file. You have to use visudo, very important.

[http://www.unixcities.com/sudo/](http://www.unixcities.com/sudo/)

Let me know if it works after you added yourself.

---

### Post by Simian on 2005-10-03
I found this.

[http://www.ubuntuforums.org/showthread.php?t=41618&highlight=sudo+kate](http://www.ubuntuforums.org/showthread.php?t=41618&highlight=sudo+kate)

I guess there's nothing wrong with my sudoers file. It seems to be a common problem with kate.

---

### Post by knappen on 2005-10-03
Ok, good to know that its a known bug. 

I guess you do not have to edit the sudoers list then :-)

---

### Post by Simian on 2005-10-03
[QUOTE=knappen]Ok, good to know that its a known bug. 
I guess you do not have to edit the sudoers list then :-)[/QUOTE]

I guess not. But thanks for trying anyway. :)

---

### Post by farfargoth on 2005-10-03
When you sudo something you are executing a command as root, but with your own enviroment thingies. Like, it uses your theme, not the one for root and so on...

When you su something you BECOME root and then you execute whatever you do, with root's enviroment thingies. same with kdesu. that includes lockfiles and so on, wich is why you should use kdesu for gui apps (su doesn't configure the enviroment for x and kde)...

---

