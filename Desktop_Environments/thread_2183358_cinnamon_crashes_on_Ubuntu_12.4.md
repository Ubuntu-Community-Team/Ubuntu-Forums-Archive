---
title: "cinnamon crashes on Ubuntu 12.4"
date: 2013-10-24
forum: Desktop Environments
---

### Post by maru2 on 2013-10-24
Hi there 
I installed Cinnamon on Ubuntu 12.4, but every time i start up, I get the message 'Cinnamon just crashed. You are currently running in Fallback Mode'. I can click yes or no, but that doesn't help. I tried all the terminal commands I could find on it, but nothing is working yet.
What should or can I do?

---

### Post by whitesmith on 2013-10-24
> **maru2 said:**
> I installed Cinnamon on Ubuntu 12.4, but every time i start up, I get the message 'Cinnamon just crashed. You are currently running in Fallback Mode'.Cinnamon is Yet Another Linux distro, just like Ubuntu. How did you install it on Ubuntu 12.4 (I assume you meant to say 12.04)?

---

### Post by Frogs Hair on 2013-10-24
The latest version of the Cinnamon Desktop has been causing problems on different versions of Ubuntu . You need file bug reports on the Launchpad page and keep in mind it is not an official Ubuntu package. 

Please Read  [http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html](http://www.webupd8.org/2013/10/cinnamon-20-released-becomes-entire.html)

---

### Post by fantab on 2013-10-25
> **whitesmith said:**
> Cinnamon is Yet Another Linux distro, just like Ubuntu. How did you install it on Ubuntu 12.4 (I assume you meant to say 12.04)?

Cinnamon is _N O T_ "Yet Another Linux Distro". Its a desktop interface, like gnome-shell or unity and is forked from gnome-shell. The common thing behind gnome-shell, unity and cinnamon is Gnome3.x. Since Cinnamon 2.0 it is considered as complete new "Desktop Environment".

---

### Post by whitesmith on 2013-10-26
> **fantab said:**
> Cinnamon is _N O T_ "Yet Another Linux Distro". Its a desktop interface, like gnome-shell or unity and is forked from gnome-shell. The common thing behind gnome-shell, unity and cinnamon is Gnome3.x. Since Cinnamon 2.0 it is considered as complete new "Desktop Environment".I tried it once, back in I-erase-ram-after-using-bad-products, which I suppose I should have made clear. Cute smileys, by the way.

---

### Post by Rob Sayer on 2013-10-27
I kind of hate to say this but I would *never* install Cinnamon over ubuntu.  Or any other non ubuntu supported desktop.

As mentioned, cinnamon is most emphatically *not* a linux distro.  It is a Linux Mint desktop.

Now, the important thing to realize here IMHO is that Linux Mint may be ubuntu based, but it is not based on current ubuntu kernel versions.  Their kernel versions are generally about 6 months old.

So you're talking about a potential bucket of worms here, because ubuntu cannot be expected to support a mint desktop, and the mint support ... which is terrible compared to ubuntu's at the best of times ... will tell you to ask ubuntu support.  Ie., no support.

As an example, if you have cinnamon installed and you want to install ubuntu 13.10 you have to purge cinnamon first or it won't work.

If you really want to use cinnamon, fine.  But you'd be much better off installing mint.

---

### Post by fantab on 2013-10-27
Firstly, Cinnamon is in Ubuntu Repositories, just like Gnome-Shell is.
Secondly, Mint's kernel versions are same as Ubuntu's. Linux Mint is released a month or so after Ubuntu release. In this sense and IMO, cinnamon works best on Ubuntu after Mints' release. since its in active development.
Thirdly, even though its developed by Mint team, its not a proprietory ware AFAIK.

The latest Cinnamon 2.0 was released quite recently and with this version it has become a Desktop Environ, DE. In other words it does not need Gnome anymore to work as such. 
[http://segfault.linuxmint.com/2013/10/cinnamon-2-0-released/](http://segfault.linuxmint.com/2013/10/cinnamon-2-0-released/)

Personally, I like Unity and Gnome-Shell more, however Cinnamon is a very good alternative for those who miss Gnome2 interface/desktop but want all the latest GNU/Linux technologies. IMO its better than Gnome-Classic and MATE. 

Linux is all about choice. Whatever taste you find most palatable, is yours.

My two cents...

---

### Post by pomke on 2014-01-04
Such a typical response, and so very sad. the OP came here looking for advice on a technical problem, yet recieved several personal opinions entirely unrelated to their technical difficulty.  To the OP, I'm having the same issue after installing Cinnamon 2.0 from the PPA on 13.10, I just get dumped into fallback mode. Did you have any luck resolving the issue?

---

### Post by Ian_M._Stewart on 2014-03-25
Me too.  I've just installed Ubuntu 13.10 and then the Cinnamon desktop from the repos.  Any attempt to use the menu crashes the system and the only way out seems to be a re-boot.  I was hoping to experience the latest and greatest Ubuntu, but can't stand Unity.  Oh well, back to Mint I suppose, unless anyone here can point me in the right direction.

---

### Post by edcompsci on 2014-07-10
Yes it is a DE. That's not trhe problem here though. Cinnamon is a DE but can only be installed through a Mint distro.   If you look in your package manager you won't see Cinnamon unless you have the Mint repo included in your sources.list file (or at least you won't with lubuntu).  That said, we don't have to argue anymore about it.  I tried installing it by adding the mint distro to my lubuntu setup and I get the same problem with the fallback. 

I found this link, but I don't know if I want to uninstall bumblebee, might than ruin my lxde installation?  I think if I use Synaptic it will tell me what other packages might also be uninstalled, then  can use ctrl-alt-f1 and reinstall them but I hope that won't break my system.

Actually not going to try it, just noticed it's by switching to ATI drivers, not nvidia. Maybe an nvidia update will be needed? 

[URL="http://ubuntuforums.org/showthread.php?t=1988789"]http://ubuntuforums.org/showthread.php?t=1988789


I am going to guess it will work from git, so I'm going to try it. [https://github.com/linuxmint/Cinnamon](https://github.com/linuxmint/Cinnamon)
[/URL]

---

### Post by deadflowr on 2014-07-10
First off, Moved to ***Desktop Environments***

> **edcompsci said:**
> Yes it is a DE. That's not trhe problem here though. Cinnamon is a DE but can only be installed through a Mint distro.   If you look in your package manager you won't see Cinnamon unless you have the Mint repo included in your sources.list file.  That said, we don't have to argue anymore about it.  I tried installing it by adding the mint distro to my lubuntu setup and I get the same problem with the fallback. 


What?
You don't add mint repo, you add a ppa, which is independent of mint.
Mint devs have stopped the ppa for cinnamon-stable, and as of now only have a ppa for cinnamon-nightly.

But others have tken up the cause and have made ppa's of the stable builds.
[http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html](http://www.webupd8.org/2014/06/new-cinnamon-stable-ubuntu-ppas-ubuntu.html)

and for the lovers of the bleeding edge
[https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly](https://launchpad.net/~gwendal-lebihan-dev/+archive/ubuntu/cinnamon-nightly)

Beyond that though, how it works is something to be taken up with the devs, probably.
I stopped using cinnamon, but it never launched fallback.The only problem I ever had was it borked Unity when 13.10 first came out.

---

