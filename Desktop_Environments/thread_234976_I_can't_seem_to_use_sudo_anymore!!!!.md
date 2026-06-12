---
title: "I can't seem to use sudo anymore!!!!"
date: 2006-08-12
forum: Desktop Environments
---

### Post by benwahwah on 2006-08-12
I've just come to use my computer and found that anything that requires sudo will no longer work!!

I first realised this when I went on the net and my hosts file wasn't working (which has worked happily for a week now). I went to change the hosts file with the following command in a terminal.

```
sudo gedit /etc/hosts
```

I was then given this message

```
sudo: unable to lookup Benwahwah via gethostbyname()
```

I have since tried to use different apps such as synaptic package manager via the desktop and they wont load while other apps that don't require a password do work. 

Any suggestions on how to remedy this?

---

### Post by mlind on 2006-08-12
You need to gain root privileges without sudo to fix the /etc/hosts. Boot into recovery mode from GRUB menu and fix /etc/hosts as root user.

---

### Post by benwahwah on 2006-08-12
I had already changed the hosts file by using sudo before though and also surely that wouldn't help things like synaptic package manager? I do appreciate your input though. It just seems that I have managed to lose the ability to enter my password. I am the only user setup on the computer as well so I should have sudo privileges I think ( although I am a new user of Ubuntu and Linux in general.

---

### Post by ajgreeny on 2006-08-12
It is also worth having a looki at the following site which helped me out of a similar situation some time ago.

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

  I just got the error message saying "Conversation with su failed".  This panicked me for a few minutes but a search soon got me up and running again with no problems.

---

### Post by mlind on 2006-08-12
> **benwahwah said:**
> I had already changed the hosts file by using sudo before though and also surely that wouldn't help things like synaptic package manager? I do appreciate your input though. It just seems that I have managed to lose the ability to enter my password. I am the only user setup on the computer as well so I should have sudo privileges I think ( although I am a new user of Ubuntu and Linux in general.

According to your error your /etc/hosts file is messed up (and hostname probably doesn't match with entry on /etc/hostname).
sudo doesn't work if it cannot resolve your hostname correctly, it's not problem with synaptic.

---

### Post by gossea on 2006-08-30
I had the same thing happen after changing the hostname to <blank> (oops).

I booted with a CD and changed it back in /etc/hosts and it started working.

Then, I took the laptop home and got denied yet again because I wasn't using the office's internal nameservers anymore.

](*,) 

Having sudo access reliant on gethostbyname() is huge headache.

---

