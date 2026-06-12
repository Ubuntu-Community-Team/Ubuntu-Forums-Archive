---
title: "Is Cinnamon available for 14.04?"
date: 2014-11-21
forum: Desktop Environments
---

### Post by Novitk on 2014-11-21
I've google it and found a lot of different procedures for installing Cinnamon in Ubuntu 14.04 (adding mint repositories, different PPA links etc). I don't know how to tell which one is the best and/or safest way of installing Cinnamon. So, is Cinnamon really available for Ubuntu 14.04? And if yes, how should I install it in a safe way? Thanks in advance for the help.

---

### Post by Rex Bouwense on 2014-11-21
You should be able to install the Cinnamon DE by entering the following in the terminal:
```
sudo add-apt-repository ppa:lestcape/cinnamon
sudo apt-get update
sudo apt-get install cinnamon
```
To uninstall
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:lestcape/cinnamon
```

---

### Post by Rob Sayer on 2014-11-23
The OP is right to be wondering whether the stuff he finds on web searches is correct or safe.  I wish more linux novices were that careful.  The best way for newbies is to search here or askubuntu.com ... the latter is harder to navigate but users there are ranked and the answers are voted on.

One thing the OP should also realize is that installing multiple desktops can really cause problems, and they're hard to diagnose.  I've done it myself.  But I wouldn't do it anymore unless one is something based on the Qt C++ libraries like KDE and the other is GTK based, like the other 3 ubuntu supported DE's.  And also Cinnamon.  This is also what linux geeks here who are way over my head say as well, and they convinced me.

But Cinnamon isn't supported by Canonical.  I wouldn't install it in a ubuntu system ... or any other DE that needs a 3rd party ppa ... at all.  If you really want to try Cinnamon, download a live CD of Mint 17 with Cinnamon.  Burn to USB stick if possible because it runs much faster that way.  Boot and see how you like it.

This is what I'd recommend with other ubuntu DEs, let alone someone else's.  There have been problems running Cinnamon in previous ubuntu releases.  If you like Cinnamon that much you'd be better off installing Mint 17 Cinnamon, which is ubuntu 14.04 based.

---

### Post by lestcape on 2014-11-26
[**[COLOR=#000000]Novitk[/COLOR]**]("http://ubuntuforums.org/member.php?u=1929249") launchpad it's the way to install software on ubuntu that is not include in the official repo...
You don't need to change your distro for do a thing like this... [**[COLOR=#000000]Rob Sayer[/COLOR]**]("http://ubuntuforums.org/member.php?u=1678250") have his own experience...

There are not problem with the cinnamon repo. I'm the maintainer.
If you have any problem with the repo, you can contact me withou any problem...

I'm also the author of:
[http://cinnamon-spices.linuxmint.com/applets/view/171](http://cinnamon-spices.linuxmint.com/applets/view/171)
[http://cinnamon-spices.linuxmint.com/desklets/view/12](http://cinnamon-spices.linuxmint.com/desklets/view/12)
[http://cinnamon-spices.linuxmint.com/desklets/view/18](http://cinnamon-spices.linuxmint.com/desklets/view/18)

I'm an external contributor of Cinnamon also:
[https://github.com/linuxmint/Cinnamon/graphs/contributors](https://github.com/linuxmint/Cinnamon/graphs/contributors)

And ofcourse i use ubuntu and i have Cinnamon as a desktop.
Good day!!!

---

### Post by Rob Sayer on 2014-11-26
I never said there was a specific problem with that ppa or that it's not maintained properly.  I am still never going to install a DE that isn't in the ubuntu repos.  And that's not "just my experience".

Actually I tried Cinnamon yesterday by booting Mint 17 from usb, which is really the best way to try a desktop.  I'd do that first.

It's quite nice ... fast, and you can turn off video effects for speed.  I'm pretty impressed.  I've been thinking to replace my kubuntu 12.04 on my laptop with 14.04 since KDE 4.10 is much nicer.  Now I'm considering mint instead.  Esp. since ubuntu 14.04 lts apparently doesn't use the lts *kernel* release now.  Mint uses a 6 month or so old kernel version and that's looking appealing.

But I still wouldn't recommend mint or anything else but ubuntu for linux beginners.  There's often some config involved so newbies need good tech support.  Mint's isn't that good.  I've never seen an other distro besides ubuntu that's suitable for beginners *and* has such good support.  In fact I've used mint before and had to read here and askubuntu to solve problems.  But raw beginners don't know how to do that effectively yet.

---

### Post by coffeecat on 2014-11-26
The OP&#8217;s original question was how to install Cinnamon safely in Ubuntu. Although the suggestion to use Mint instead was a valid one, the thread became derailed by discussion around this issue, so I have removed a few posts to get this thread back on track again. 

No criticism intended of those whose posts have been removed &#8211; thanks to all for their contributions &#8211; but please can we focus on how to install Cinnamon in Ubuntu in this thread? Discussion about whether one is best using Ubuntu or Mint for Cinnamon, or Mate, or any other desktop, belongs in a chat area.

Thanks, all.

---

### Post by grahammechanical on 2014-11-26
The safest way that I know off to install software in Ubuntu is through the software centre.

Has anyone searched the software centre recently for Cinnamon? I do not know if cinnamon is in the 14.04 software centre but it may be in the 14.10 USC. It certainly is in the Vivid Vervet (15.04) software centre.

It is described as "a desktop environment which provides innovative features and a traditional user experience ... The desktop layout is similar to Gnome 2. The underlying technology is forked from Gnome shell."

Regards.

---

### Post by coffeecat on 2014-11-26
Cinnamon package version 2.2.16-3 is in the Universe repository for 14.10, but a search for "cinnamon" in trusty here revealed no results:

[http://packages.ubuntu.com/search?keywords=cinnamon&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=cinnamon&searchon=names&suite=trusty&section=all)

So for Trusty, it seems that the lestcape ppa would be the answer.

---

