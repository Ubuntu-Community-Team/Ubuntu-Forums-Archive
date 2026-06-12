---
title: "Being &quot;root&quot; in Xubuntu 9.04"
date: 2009-04-25
forum: General Help
---

### Post by Ambertone on 2009-04-25
Hi all, new user. I've installed Xubuntu 9.04 in my Dell Inspiron 700M laptop and I must sayI'm really impressed. What a quality distro this is.

Now, coming from PCLinuxOS which had the root account enabled I'm stuggling a bit with Xubuntu. I need to copy a theme file into /usr/share/icons but can't. 

I've tried "su" &"sudo" in terminal to run Thunar but I got asked to run "sudo apt-get install root" (which I did)

I would prefer to enable the root account as I'm used to it. So how do I either:

* Get Thunar running with root privledge?
* Turn the root account on?

All help appreciated.

Rod

---

### Post by lisati on 2009-04-25
It can be done but telling users how to activate the root account in Ubuntu is frowned upon here in the forums.

The preferred method for temporarily enabling root privileges is with the sudo command.

---

### Post by conscious on 2009-04-25
See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dcstar on 2009-04-25
> **Ambertone said:**
> Hi all, new user. I've installed Xubuntu 9.04 in my Dell Inspiron 700M laptop and I must sayI'm really impressed. What a quality distro this is.

Now, coming from PCLinuxOS which had the root account enabled I'm stuggling a bit with Xubuntu. I need to copy a theme file into /usr/share/icons but can't. 

I've tried "su" &"sudo" in terminal to run Thunar but I got asked to run "sudo apt-get install root" (which I did)

I would prefer to enable the root account as I'm used to it. So how do I either:

* Get Thunar running with root privledge?
* Turn the root account on?

All help appreciated.

Rod
This might launch the browser with root privileges:
```
gksudo "dbus-launch thunar"
```

---

### Post by Ambertone on 2009-04-25
> **dcstar said:**
> This might launch the browser with root privileges:
```
gksudo "dbus-launch thunar"
```

Nope, didn't work. 

On the issue of the root account. I've come across the people who believe that it should not be enabled and I understand why. For me I've been using a distro with it for years and have no issue with it.

At the end of the day no one should tell me how to use my computer, people can choose not to share the info if they wish. Linux is about choice isn't it?

Rod

---

### Post by lisati on 2009-04-25
> **Ambertone said:**
> 
At the end of the day no one should tell me how to use my computer, people can choose not to share the info if they wish. Linux is about choice isn't it?

Have a look here:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Ambertone on 2009-04-25
Hi all, figuered it out:

sudo -i
(enter password)
thunar

All done.

Cheers

Rod
P.S. What a superb OS this is :-) It flies on my Dell!

---

### Post by conscious on 2009-04-25
I think you can achieve the same effect with "gksudo thunar".

---

### Post by stwschool on 2009-04-25
gksudo gets round the whole having to keep a terminal window open thing. It also means you can just Alt+f2 and type the command in there. If you're using graphical (non command-line) stuff, always use gksudo. You can even make a launcher use gksudo, so you could for instance copy your thunar launcher and edit the copy to launch "gksudo thunar" with a label on it saying "Root Thunar" or whatever.

---

### Post by Ambertone on 2009-04-25
> **conscious said:**
> I think you can achieve the same effect with "gksudo thunar".

Good tip, thank you.

---

### Post by Ambertone on 2009-04-25
> **stwschool said:**
> gksudo gets round the whole having to keep a terminal window open thing. It also means you can just Alt+f2 and type the command in there. If you're using graphical (non command-line) stuff, always use gksudo. You can even make a launcher use gksudo, so you could for instance copy your thunar launcher and edit the copy to launch "gksudo thunar" with a label on it saying "Root Thunar" or whatever.

Another good tip :-) That works a treat!

Cheers

Rod

---

### Post by Gamfrek on 2009-07-11
What ever happened to 

su - root
(enter password)

???

---

### Post by CatKiller on 2009-07-11
> **Gamfrek said:**
> What ever happened to 

su - root
(enter password)

???

You've not read the link that was posted, have you? I suggest you do.

Your (enter password) step will fail because it's asking you for root's password, and root doesn't have a password.

---

### Post by manishthatte on 2012-08-17
> **Ambertone said:**
> Hi all, figuered it out:

sudo -i
(enter password)
thunar

All done.

Cheers

Rod
P.S. What a superb OS this is :-) It flies on my Dell!

Worked perfectly for me !!!
Cheers.
Mani

---

### Post by nothingspecial on 2012-08-17
Old Thread.

Closed.

---

