---
title: "I'm a n00b and I can't find this program..."
date: 2008-12-17
forum: General Help
---

### Post by Celestika6 on 2008-12-17
Where can I find a version of MSN messenger that will run on Ubuntu? I swear I've Googled every combination of the words MSN, Ubuntu, Linux and Messenger known to man.:confused:

---

### Post by |{urse on 2008-12-17
open a terminal and type this.

sudo apt-get install amsn

then to launch it type

amsn

---

### Post by PocketDog on 2008-12-17
Pidgin (which you've already got because it comes pre-installed with Ubuntu) is MSN Messenger compatible too.

---

### Post by binbash on 2008-12-17
if you want to use a webcam, you will use amsn

---

### Post by teddks on 2008-12-17
Pidgin, which comes installed by default on Ubuntu, handles MSN. It also integrates nicely into the desktop, and lets you use one client for AIM, MSN, ICQ, XMPP (which is "Google Talk"), IRC, SILC, Bonjor, and a lot of others. If you have 8.10, the User Switch Applet can also change your Pidgin status.

Yes, you can't do voice or video over Pidgin, so if you use those, you should install aMSN. But Pidgin is a great client, and worth checking out before you install singletons for every protocol you use.

---

### Post by Celestika6 on 2008-12-17
sorry... open a terminal? I thought I mentioned I'm a n00b. lol. You're going to have to walk me through this one.:redface:

---

### Post by SuperSonic4 on 2008-12-17
System -> Administration -> Terminal

---

### Post by teddks on 2008-12-17
> **Celestika6 said:**
> sorry... open a terminal? I thought I mentioned I'm a n00b. lol. You're going to have to walk me through this one.:redface:

You don't need to open a terminal for anything in this thread. You can just go to Applications>Add/Remove, or [click here to install amsn](apt://amsn).

---

### Post by aysiu on 2008-12-17
The terminal is wholly unnecessary for installing aMSN.

Go to Applications > Add/Remove

Show All Available Applications

Search for *amsn*

Check it

Click Apply

That's it. It's that simple.

---

### Post by ubuntu27 on 2008-12-17
[Click here to install emesene]("apt://emesene")

 Instant Messenger for the Windows Live Messenger network

or you can open the Terminal (Applications/Accessories/Terminal)

and then type (or you can copy and paste)

```
sudo apt-get install emesene
```

---

### Post by |{urse on 2008-12-18
lol, i'm seeing a lot of hate for the terminal. Ya know, it is possible to teach someone more than one thing at a time.

---

### Post by aysiu on 2008-12-18
> **|{urse said:**
> lol, i'm seeing a lot of hate for the terminal. Ya know, it is possible to teach someone more than one thing at a time. Yeah, but if the person is a new user, why start with the terminal before introducing the GUI?

Besides, you didn't teach more than one thing at a time. You taught only one thing - the terminal. If you had taught more than one thing, you would have presented both terminal and GUI instructions.

> **Celestika6 said:**
> sorry... open a terminal? I thought I mentioned I'm a n00b. lol. You're going to have to walk me through this one.:redface: See?

The OP doesn't want to open a terminal just yet.

I don't hate the terminal. I love it. Probably a lot of other people do, too. But why does that mean the first thing you have to present to a new user is the terminal?

---

### Post by |{urse on 2008-12-18
> **aysiu said:**
> Yeah, but if the person is a new user, why start with the terminal before introducing the GUI?

Besides, you didn't teach more than one thing at a time. You taught only one thing - the terminal. If you had taught more than one thing, you would have presented both terminal and GUI instructions.

 See?

The OP doesn't want to open a terminal just yet.

I don't hate the terminal. I love it. Probably a lot of other people do, too. But why does that mean the first thing you have to present to a new user is the terminal?

I'm rereading this and i see that I showed the user how to install through aptitude with a simple command as well as how to invoke a program they would have found in their menu anyways. I guess thats just how I learned linux, command line first. Perhaps I'm oldschool. :-?

---

