---
title: "How well does ubuntu share with windows?"
date: 2009-01-16
forum: General Help
---

### Post by dtrot55 on 2009-01-16
I think I have decided to use my other computer with ubuntu as a storage computer...loading all my ide hard drives in it while keeping my sata's in this computer...I was wondering how easy it is to setup the ubuntu computer to share hard drives and if i would need to do anything in windows so that i could access them if i need to?  Or is this just a bad idea?  I know a lot of people hate windows and thats why they are using Linux..but for the industry im in ... windows in kind of critical...

Thanks,

Dan

---

### Post by DeMus on 2009-01-16
> **dtrot55 said:**
> I think I have decided to use my other computer with ubuntu as a storage computer...loading all my ide hard drives in it while keeping my sata's in this computer...I was wondering how easy it is to setup the ubuntu computer to share hard drives and if i would need to do anything in windows so that i could access them if i need to?  Or is this just a bad idea?  I know a lot of people hate windows and thats why they are using Linux..but for the industry im in ... windows in kind of critical...

Thanks,

Dan

Building a network with a Ubuntu and a Windows machine is relatively easy. Install Samba (smb) in Ubuntu and most of the work is done already.
Read the man pages about samba on how to share folders which should be accessible from the windows machine and do the same there so you can read the windows folders you need.

DeMus

---

### Post by hyperdude111 on 2009-01-16
using samba for windows in ubuntu is easy. You just set the settings to share and it installs for you, however you will need to re-start after that although you get no prompt.

---

### Post by king.pest on 2009-01-16
dtrot55, if you're running ubuntu 8.10 with gnome, all you have to do is to right-click on a directory you want to share, go to its properties, and then choose a name of the share, and decide whether you want others to have a "rw" or "ro" access to the share. if you don't have samba installed yet, you will have the option to install it automatically. 

piece of cake!

---

### Post by dtrot55 on 2009-01-17
What you guys keep talking about will work across the board right?  Kubunt and Xubuntu??? Just incase i decide to use a different one.

---

### Post by earthpigg on 2009-01-17
> **dtrot55 said:**
> What you guys keep talking about will work across the board right?  Kubunt and Xubuntu??? Just incase i decide to use a different one.

any directions involving a terminal are pretty universal.

any directions involving "right click and then bla bla" are DE (desktop environment) specific... KDE (kubuntu), XFCE (xubuntu), and Gnome (Ubuntu) are examples of desktop environments. ;)

you can have multiple DEs on the same machine:

```
sudo apt-get install xubuntu-desktop
```

on a kubuntu install, for example, will result in you having both on the same machine. after installing: log out, click around, and log back into xubuntu.

---

### Post by king.pest on 2009-01-17
> **earthpigg said:**
> any directions involving a terminal are pretty universal.


earthpigg is right, samba network shares are DE-independant. I haven't used KDE 4, but in Kubuntu with KDE 3.x setting up shares was quite simple, so I guess under KDE 4 it works similar. in case you want to use Xfce environment, you'll probably need to configure samba manually (please correct me if it's changed in new Xubuntu versions, haven't been using that for a while).

---

### Post by upchucky on 2009-01-17
my current home network is 4 machines, one is my wifes ubuntu for her video photog stuff, one 200 mhz 160m ram xp machine for phone system (magicjack wont run on linux yet), one xp machine for beta testing games that are not yet ported to linux, and my main ubuntu pc for really important stuff.

they are all talking to each other but the monopoly of windows does not like linux files, however linux can handle windows files just fine.

---

### Post by dtrot55 on 2009-01-18
so would i run into issues with windows not wanting to read the files i store on my ubuntu computer???  Cause if thats the case...i wouldn't want to waste my time or my data

---

### Post by DeMus on 2009-01-18
> **dtrot55 said:**
> so would i run into issues with windows not wanting to read the files i store on my ubuntu computer???  Cause if thats the case...i wouldn't want to waste my time or my data

Yes, Windows can read files on your Ubuntu machine over the network. The network protocol takes care of that. That's the nice thing of networking. Also on the internet is happening the same thing. Most of the servers on the internet run some kind of unix/linux OS. You can approach the files with your Windows machine without problems. Vice versa also doesn't give any problems.

---

