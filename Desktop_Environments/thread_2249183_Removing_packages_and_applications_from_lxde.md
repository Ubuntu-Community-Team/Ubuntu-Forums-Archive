---
title: "Removing packages and applications from lxde?"
date: 2014-10-20
forum: Desktop Environments
---

### Post by chaaderf on 2014-10-20
I just installed the lxde desktop environment on top of Ubuntu 14.04 to replace Unity:

```
sudo apt-get install lxde
```

But I'm not removing Unity, as I may need it at some point. Now I'm wondering can I remove some packages that are listed as recommended [on this page]("http://packages.ubuntu.com/trusty/lxde")? 

There are also some other applications that I don't need, but they are listed as depends. I mean like gpicview and leafpad (instead I'd use eog and gedit respectively). Can I remove them also or does the lxde get mixed somehow? I've read somewhere that those applications that come within the desktop environment, should not be removed. But perhaps someone could clarify what does this actually means. Thank you! ^^

---

### Post by ian-weisser on 2014-10-20
> **chaaderf said:**
> Now I'm wondering can I remove some packages that are listed as recommended [on this page]("http://packages.ubuntu.com/trusty/lxde")? 

Yes.

The package manager will respond with a list of packages that will actually be removed in response to your request.

Read that list carefully each time. If it includes something you wish to keep, abort the removal.

---

### Post by slickymaster on 2014-10-20
Before removing them, you can always run```
apt-cache depends package_name
```on each package to get a list of dependencies for a certain package.

Have a read at the Debian policy manual chapter 7: [https://www.debian.org/doc/debian-policy/ch-relationships.html](https://www.debian.org/doc/debian-policy/ch-relationships.html)

---

### Post by chaaderf on 2014-10-20
Thank you!

---

### Post by Rob Sayer on 2014-10-20
You're right that many apps that came with lxde shouldn't be removed unless you know *exactly* what they're doing.  They're system related.  Leave that alone.

But ordinary GUI apps like leafpad are fine.  You can mix and match them as much as you want.  I install leafpad as my default simple text editor on any DE whether it came with it or not because it's my favorite.

Another example is dolphin, which you get with KDE/Kubuntu.  I use it other DEs because it's by far my favorite file manager.  But if you install a KDE app like dolphin it'll also install a ton of dependencies.  That's because KDE is a highly integrated environment and is written using Qt libraries rather than GTK ones like the other 3 official ubuntu DEs.  That doesn't bother me.  Dolphin isn't as fast as the file manager you get with Xubuntu or Lubuntu (I actually just finished reinstalling Lubuntu 14.04.1).  But it's so powerful it speeds *me* up.  Just an example.

Actually installing multiple DEs can cause problems.  I've done it in the past but I won't do it anymore, though I'd make an exception with installing a Qt based system like kubuntu-desktop on an existing GTK based install.  There'd be much less chance of conflict.

The problems that can arise are likely to be caused by something like both DEs using the same package somewhere but different versions.  This is not easy to diagnose, can't be solved by deleting system packages, and is actually fairly advanced stuff.  Definitely not for novices.

I don't want to scare you here ... I've had some problems when I had more than one DE installed in the past but they weren't catastrophic.  I still didn't like it.  I had xubuntu 14.04 on my netbook until a couple of hours ago but I just reinstalled Lubuntu 14.04.1.  Xubuntu seems a lot slower in this version than I remember, and Lubuntu 14.04 was too buggy.  14.04.1 doesn't seem to have any of the problems it had before.  And it's *fast*.  But I digress.

My advice would be to try lxde for a while and if you like it do a clean reinstall of lubuntu 14.04.1.  While that seems a lot of bother it's actually not hard.  I've done some distro/DE hopping on my netbook for  hardware support reasons and have lost my fear of reinstalling.  It's definitely better than doing a release upgrade.  In fact if your system config gets really messed up it's sometimes easier just to reinstall.

If you do reinstall I would very highly recommend selecting "something else" at the HD partition stage and setting up a separate partition for your /home folder.  There's a ton of info on that and on askubuntu.

This is so useful I wish it was the default in Ubuntu.  I think it is in debian linux.  The big advantage is that you can reinstall the OS and keep your user data and settings.  Just don't tell the installer to format the /home partition when reinstalling, and have your data backed up anyway.  AN example: when I reinstalled Lubuntu all my LXDE preferences were intact because I didn't bother deleting them from /home when I installed Xubuntu 14.04 replacing Lubuntu.

And be careful what sources you read.  Stick to here and askubuntu until you get more experienced.  There are some really good linux blogs.  And many bad ones.  Just because someone writes a linux blog does not mean they know what they're doing, and novices can't tell the difference.

Much of the stuff I see on blogs is out of date or just plain wrong.  And these guys *never* seem to tell you how to undo the changes they recommend.

A good example is how a ton of noobs on the forums have sound problems so they purge pulse audio because some blog clown said to.  That is a bad idea.  Pulse has a ton of complex dependencies so it's not a good idea to remove it.

---

### Post by vasa1 on 2014-10-20
And then there's **apt-cache rdepends** as well.

Because [http://packages.ubuntu.com/trusty/lxde](http://packages.ubuntu.com/trusty/lxde) lists gpicview and leafpad as "depends", I would not remove them, whether they are really necessary or not.

If your problem is that these items clutter up the Dash or menus, you can edit their .desktop files so that they don't appear in either.

---

### Post by ibjsb4 on 2014-10-20
For future reference, if you do not want to install recommended packages use --no-install-recommends.
```
sudo apt-get install --no-install-recommends lxde
```
And that will leave them off.

Also you may of been better off just installing lxde-core.
[http://packages.ubuntu.com/trusty/lxde-core](http://packages.ubuntu.com/trusty/lxde-core)
```
sudo apt-get install --no-install-recommends lxde-core
```

---

### Post by chaaderf on 2014-10-20
Thank you so much to all of you! There are so many excellent hints and comments. ^^

Rob Sayer: Yes, I've heard that there may be some problems having different DEs. How I came here was that I'm not sure, which DE would suit best for me and what I need. I've used Ubuntu (and Unity) only since spring but I've also installed pure Lubuntu 14.04 on my low resource netbook. The lxde works quite well, that's true. However, I'm not yet ready to replace the Ubuntu 14.04 on this laptop which I'm using more. (I'm also thinking, is *buntu really the best one for me, or should I even look for some other distros, but this is a different story.) Indeed, if I'll come accross any severe problems, I'll do a pure installation of Lubuntu. And thank you for the tip of separate home partition. At the moment I have all my data backed up on a single USB stick. In this case it wouldn't be so hard to recover everything if something really bad happened. And yes, there are many misleading instructions on the web. Usually I try to google some days before I actually run any commands on terminal. Just to make sure it'd work like I wish. :D

---

### Post by chaaderf on 2014-10-21
Okay. I changed my mind and installed pure Lubuntu. I'd think it suits me better than Unity. So thank you again! ^^

---

