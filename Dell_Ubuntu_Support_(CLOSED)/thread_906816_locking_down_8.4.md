---
title: "locking down 8.4"
date: 2008-08-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Anditsu on 2008-08-31
Hello Ubuntu fans,
I just ordered a dell inspiration 1525,and while I'm waiting I going to be planing security for it. This way I have every thing in place before it gets here. I'm looking for a fire wall to use with wifi. I all so want to know where I can find a manual for trip wire. Is there any way I can down load it to a flash drive and install from there. I want to have every thing on a flash drive so I don't have go on line until my system is up set up to face the big bad internet. hmm I all so want to encycped however that's spelled,but don't know any ubunto friendly tools to do. If there is any one that could help it would be great. It's my little project of sorts.

Anditsu

---

### Post by pytheas22 on 2008-09-01
Kudos for buying an Ubuntu machine from Dell!

First of all, I wouldn't be as worried as you seem about doing everything before plugging into the Internet.  You should be pretty safe, especially if you connect from behind a router or firewall.

Keep in mind that Linux has a built-in firewall called iptables.  By default, it's configured on Ubuntu to allow all traffic, so it effectively doesn't do anything.  But you don't need to install additional firewall software.

iptables can be configured from the command-line, but if you want a nice GUI frontend to it, install Firestarter:
```

sudo apt-get install firestarter
```

(You could download the firestarter package from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install it from a USB drive if you really are worried about going online without having a firewall up first.)

As for Tripwire (which I wouldn't bother installing unless you plan on running a web server or something on this computer; if it's just a regular desktop, I don't think any intrusion-detection stuff is really going to be necessary), I'd recommend using [OSSEC]("http://ossec.net/") instead--it's completely free (as in free of cost and GPLv3 source code) and does everything that Tripwire can.  I also think that OSSEC is a little easier to manage from a central location.  There is documentation for it on its website--keep in mind that you're going to have to invest some time if you want to learn how to use OSSEC, but it's a very effective tool once you learn it.

As for full-disk encryption on Ubuntu, take a look [here]("http://learninginlinux.wordpress.com/2008/04/23/installing-ubuntu-804-with-full-disk-encryption/").  You'll have to reinstall Ubuntu completely, I think, if you want to encrypt the whole disk (if you only want to encrypt one folder or partition, you can use TrueCrypt).

---

### Post by Anditsu on 2008-09-01
While I have read some post expressing concern over the Price of Ubuntu machine vs that of one that comes with vista; I decided to buy regardless to help support the Ubuntu community. After I use it for while I'm going to write a review,and post it here to help other make up their mind. 

In regards to security your post raises the question how much security is need. I tend to like being prepared. I have heard about the Linux fire wall before,but don't know to much about setting it up from the shell,so a good GUI one seems to be the ticket until I can get up to speed. The problem I have had with fire starter is that It did not work with WIFI as it kept looking for a ethernet connection or dial up. True cryped is a cool idea,being as ubuntu comes pre install it would like a waste of energy to take it off put it back. This is mainly because I would be in hurry to play with it out of the box I have not really looked at the other program you suggest yet,but will shortly.

Anditsu

---

### Post by pytheas22 on 2008-09-01
You can tell Firestarter which network interface to use by clicking Preferences>Firewall>Network Settings.  Also I think that the first time you run Firestarter on a new system, it will ask you which interface is connected to the Internet.

As for the disk encryption, if you don't want to reinstall Ubuntu completely, you can still create an encrypted folder using TrueCrypt and put in it all of the files that you don't want anyone to have access to.  Full-disk encryption is obviously the best method because it ensures that every single file on your hard disk is inaccessible to everyone but you, but a single encrypted folder or partition can be just as effective as long as you remember to always put your sensitive data in it.

---

### Post by Anditsu on 2008-09-01
That sounds interesting. I will do some study and once my Laptop gets here I'll give it a shot.

---

### Post by Anditsu on 2008-09-06
I just was told about a front for IPtabes installed on 8.4 called UFW so far it plays well with wifi. Do where I can find a good guide for using it.

---

### Post by pytheas22 on 2008-09-06
I've never used UFW but [this page]("http://ubuntuforums.org/showthread.php?t=823741") and [this page]("https://wiki.ubuntu.com/UbuntuFirewall") may help you get started.

There's also apparently a GUI for UFW [here]("http://gufw.tuxfamily.org/index.html"), if you don't want to use the command-line.

---

