---
title: "Only receive certain packages from a repo (Seveas')?"
date: 2006-10-01
forum: Desktop Environments
---

### Post by Cable on 2006-10-01
I'd like to try to use FreeNX to log into a Xubuntu computer in my home (I use Ubuntu, and administer the Xubuntu computer, I just want to log into the Xubuntu computer to update it and whatnot from my own computer).  I know I can use Seveas' repo to get FreeNX, but I don't want to have the updates to other packages show up from that repo.  Is there a way I can just leave that repo in sources.list and only receive any needed FreeNX packages rather than all of them?

I'm just being cautious as I don't know this repo.  Are the updated packages safe, and why/how have they been changed??

---

### Post by daller on 2006-10-01
Why not use SSH for that?

---

### Post by Cable on 2006-10-01
I guess I could...how would I set that up?  I don't *need* FreeNX, just thought it seemed better from what I've read.

One thing though.  I don't use that computer, but other family members do.  If I use SSH, can someone be using the computer while I am logged into it via SSH?  If someone is using that computer when I want to log into it I want it to be as if I'm not logged into it to whoever is using it, just for the sake of convenience and avoiding confusion.

---

### Post by christhemonkey on 2006-10-01
Yes someone can be using that computer whilst your ssh-ed into it.

You need to install openssh-server.
```
sudo apt-get install ssh
```

Howto here:
[http://ubuntuguide.org/wiki/Dapper#SSH_Server](http://ubuntuguide.org/wiki/Dapper#SSH_Server)

---

### Post by daller on 2006-10-01
ssh is 100% commandline...

You will be logged in, but nobody will ever know, unless they dig deep!

---

### Post by Cable on 2006-10-01
Should I set up an additional user on the computer?  There is only 1 user on it, and I have it set to auto-login upon startup (there is no need for multiple users on it).  I'm assuming I could just use the username/password for the user that already exists even if that user is already logged in?

---

### Post by daller on 2006-10-01
The only user that is setup, can login an infinite number of times, in theory!

It's a long time since I used ssh myself, but run something like this:

ssh -l USER 192.168.0.100

and replace USER with the username, and adjust the IP!

Then you have a commandline, as if you where sitting in front of the other machine!

---

### Post by christhemonkey on 2006-10-01
Or you can enable X forwarding (you may have to uncomment a line in /etc/ssh/ssh_config)

An then type:
```
ssh -X USER@192.168.0.100 
```
This will let you run GUI programs that are on the far distant machine.

---

### Post by daller on 2006-10-01
> **christhemonkey said:**
> Or you can enable X forwarding (you may have to uncomment a line in /etc/ssh/ssh_config)

An then type:
```
ssh -X USER@192.168.0.100 
```
This will let you run GUI programs that are on the far distant machine.

Well, if the only purpose is to update the machine, forwarding X would be a waste of resources!

---

### Post by christhemonkey on 2006-10-01
True, but for some lesser experienced users, being dropped to a command line an then trying to open, say, synaptic package manager to update their system,
they might be like wtf?! why wont it open...

But i suppose yes, X forwarding might be resource wasting overkill in this situation.

---

### Post by Cable on 2006-10-02
Installed SSH, worked perfectly (X tunneling included, if the need arises).  I'm just going to secure it a bit more once I have time.  It does what I need it to do, so I don't need FreeNX, as all I really need to be able to do is update it and install anything that may be needed.  And I'm fine with the command line...I'm no expert with it, but I know how to do what I need to do.

---

### Post by daller on 2006-10-02
> **Cable said:**
> Installed SSH, worked perfectly (X tunneling included, if the need arises).  I'm just going to secure it a bit more once I have time.  It does what I need it to do, so I don't need FreeNX, as all I really need to be able to do is update it and install anything that may be needed.  And I'm fine with the command line...I'm no expert with it, but I know how to do what I need to do.

Nice thing!

---

