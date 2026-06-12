---
title: "Cannot get updated signatures for ClamTK Virus Scanner"
date: 2009-02-24
forum: General Help
---

### Post by arvadawest on 2009-02-24
Good day everyone,

**Fyi that I am a newbie**

I am trying to get the latest update signatures for clamtk virus scanner.  It says I need to be root.  I thought I was root since I am the admin of this system?  Thank you for your help.  :)  -aw

---

### Post by Rallg on 2009-02-24
This is a general reply, not specific to ClamTK:

Even though you are an administrative user, you are NOT root. This is for your own protection.

As an administrative user, you can request temporary permission to perform some activities as root. Thus is done using the "sudo" command in Terminal. For example, if you wish to run program "someprogram" you would ordinarily do something like this:

yourname@yourcomputer:~$ someprogram -someinput

That runs the program with your own (non-root) privileges. Some programs do not permit you to do that. If refused, you can request permission this way:

yourname@yourcomputer:~$ sudo someprogram -someinput

You will then be asked for your password. If you have to run several programs with permission, then you would sudo each one, but in most cases you won't be asked again for the password, until some time has elapsed.

If a program asks you to be root, try sudo first. If that fails, you can actually become root using "sudo -s" like this:

yourname@yourcomputer:~$ sudo -s
(password request)
root@yourcomputer:~# someprogram -someinput

You remain as root until you issue the "exit" command, or until you close the Terminal.

When you see the $ symbol, it means you are a user (with or without special permission). When you see the # symbol, it means you are root, and do not need to ask for more permission unless you are trying to do something that excludes root. The ~ symbol means that you are in the user Home directory.

Do not sudo anything, unless you know that it is necessary. Do not change to the root, unless you absolutely know it is necessary.

It is also possible to create users (other than the original administrator, yourself) who are not permitted to use sudo. For example, my version (Ubuntu 8.10) allows creation of a temporary Guest account, useful if a friend wants to use your computer to check E-mail or something.

Fun fact: Windows Vista got many complaints from experienced XP users, because Vista inserted an extra layer of file security. An XP user, who was an administrator, would be allowed to do nearly anything. But in Vista, even an administrator would be blocked vrom doing certain things, unless the extra layer of protection was turned off. The Vista model of protection is closer to what has been in Linux (Ubuntu version) all along. If you have recently migrated from XP to Ubuntu, then you may be surprised by the added security. But if you have been a Vista user, with the security enabled, then the Ubuntu security model is less of a surprise.

---

### Post by arvadawest on 2009-02-24
> **Rallg said:**
> This is a general reply, not specific to ClamTK:

Even though you are an administrative user, you are NOT root. This is for your own protection.

As an administrative user, you can request temporary permission to perform some activities as root. Thus is done using the "sudo" command in Terminal. For example, if you wish to run program "someprogram" you would ordinarily do something like this:

yourname@yourcomputer:~$ someprogram -someinput

That runs the program with your own (non-root) privileges. Some programs do not permit you to do that. If refused, you can request permission this way:

yourname@yourcomputer:~$ sudo someprogram -someinput

You will then be asked for your password. If you have to run several programs with permission, then you would sudo each one, but in most cases you won't be asked again for the password, until some time has elapsed.

If a program asks you to be root, try sudo first. If that fails, you can actually become root using "sudo -s" like this:

yourname@yourcomputer:~$ sudo -s
(password request)
root@yourcomputer:~# someprogram -someinput

You remain as root until you issue the "exit" command, or until you close the Terminal.

When you see the $ symbol, it means you are a user (with or without special permission). When you see the # symbol, it means you are root, and do not need to ask for more permission unless you are trying to do something that excludes root. The ~ symbol means that you are in the user Home directory.

Do not sudo anything, unless you know that it is necessary. Do not change to the root, unless you absolutely know it is necessary.

It is also possible to create users (other than the original administrator, yourself) who are not permitted to use sudo. For example, my version (Ubuntu 8.10) allows creation of a temporary Guest account, useful if a friend wants to use your computer to check E-mail or something.

Fun fact: Windows Vista got many complaints from experienced XP users, because Vista inserted an extra layer of file security. An XP user, who was an administrator, would be allowed to do nearly anything. But in Vista, even an administrator would be blocked vrom doing certain things, unless the extra layer of protection was turned off. The Vista model of protection is closer to what has been in Linux (Ubuntu version) all along. If you have recently migrated from XP to Ubuntu, then you may be surprised by the added security. But if you have been a Vista user, with the security enabled, then the Ubuntu security model is less of a surprise.

Wow!  Thank you for this great response.  I still do not know how to get the updates signatures for clamtk, but what you typed was very useful and have never seen anything like this.

I admit I am a very frustrated Ubuntu user (or admin on my machine) and I'm just trying to learn.  I do not own any Vista machines, but I have set some up for other users/friends and I knew about this extra layer is security, but I admit learning Ubuntu (linux in general) seems to be very difficult, but I guess that is how we all learn by trying.

---

### Post by BGFG on 2009-02-25
ClamTK usually updates itself by it's service running when the machine boots up. 
If you'd like to update manually though go to Applications>>Accessories>>Terminal then type
```

sudo clamTK

```

or 
```

sudo clamTK-gtk

```

I can't remember which as i have uninstalled clamTK myself. This command will launch clamTK in supervisor mode and than you can go ahead and update.

---

### Post by arvadawest on 2009-02-25
> **BGFG said:**
> ClamTK usually updates itself by it's service running when the machine boots up. 
If you'd like to update manually though go to Applications>>Accessories>>Terminal then type
```

sudo clamTK

```

or 
```

sudo clamTK-gtk

```

I can't remember which as i have uninstalled clamTK myself. This command will launch clamTK in supervisor mode and than you can go ahead and update.

Thank you so much BGFG and others.  This worked!  Also the sudo -s is a great shortcut.  I am a newbie, but it's exciting to learn new things.  I know that one day I will have the knowledge and skillset like many of you and realize just how superior this is to windows pc.  I run a Dell XPS 410 system with 2gig of ram and with a dual core.  I hope the hardware will still be compatible with future versions of ubuntu.

Thanks to everyone on this site.  -aw

---

