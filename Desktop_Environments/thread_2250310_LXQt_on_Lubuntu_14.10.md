---
title: "LXQt on Lubuntu 14.10"
date: 2014-10-28
forum: Desktop Environments
---

### Post by vasa1 on 2014-10-28
Now that LXQt is said to be "already usable on production desktops" according to lxqt.org, I'm giving it a try on Lubuntu 14.10.

First, I installed the lubuntu-daily ppa:```
sudo add-apt-repository ppa:lubuntu-dev/lubuntu-daily
```Then I ran sudo **apt-get update** and **sudo apt-get dist-upgrade**. At this point, 
[LIST]
[*]one new package was installed
[*]23 other packages were upgraded.
[*]one, pcmanfm, was kept back. I had seen this previously when trying out LXQt 0.7 on Lubuntu 14.04. This time, I ran **sudo apt-get install --reinstall pcmanfm** and that took care of things.
[/LIST]

I then ran
```
sudo apt-get install lxqt-session
```. That got me 19 new packages and then I ran
```
sudo apt-get install lxqt-metapackage
``` and that pulled in 80 more packages.

On logging out and back, I got seven options:
[LIST]
[*]LX Games
[*]LXQt Desktop
[*]Lubuntu
[*]Lubuntu Netbook
[*]Lubuntu Nexus 7 session
[*]Lubuntu Qt session
[*]Openbox
[/LIST]I don't know what the difference between "LXQt Desktop" and "Lubuntu Qt session" but I'm going with the former. It's functional and now I'm doing a bit of groping around aka customizing.

---

### Post by TheFu on 2014-10-28
When package dependencies get screwy - I use aptitude, not apt-get.

---

### Post by vasa1 on 2014-10-28
Another route: [Lubuntu ISO prototype, build with LXQt, available for testing]("https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008662.html")

---

### Post by Rob Sayer on 2014-10-29
> **vasa1 said:**
> Another route: [Lubuntu ISO prototype, build with LXQt, available for testing]("https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008662.html")

If you really, really want LXQt that's probably the way to go for you.

You probably don't want to hear this, but there's no *way* I'd install LXQt on my netbook which is running Lubuntu 14.04.1.  When you install LXQt you enable the lubuntu-daily repo.  This is the bleeding edge unstable version.  So what you're talking about is installing a beta DE and making your other DE unstable in the process.

I tried LXQt when I had xubuntu on my netbook ... frankly Lubuntu 14.04 was too buggy, 14.04.1 is much better.  I liked LXQt.  For a beta release it's great, but it's beta.  You can't auto hide panels, which is a deal breaker for me on a netbook.  I like to add an auto hide panel for my most used apps.  I'll wait for a stable LXQT myself, preferably on a long term support version.

---

### Post by vasa1 on 2014-10-29
> **Rob Sayer said:**
> ...  You can't auto hide panels, which is a deal breaker for me on a netbook.  I like to add an auto hide panel for my most used apps.  ...
[https://github.com/lxde/lxde-qt/issues/134](https://github.com/lxde/lxde-qt/issues/134)

Re. most used apps, I have those appear "on demand" by pressing the super key and the spacebar together if they're "complicated". The apps can be specified in menu.xml (if Openbox is the window manager). For easy ones, I set those in rc.xml or (lubuntu-rc.xml):
W+F = Firefox
W+G = Google Chrome
W+L = leafpad
W+T = lxterminal
etc.

So I don't really need a panel to launch apps, autohide or not, in LXQt or in regular Lubuntu or in an Openbox session (no DE).

Here are two links that helped me a lot:

[http://pclosmag.com/html/Issues/201011/page09.html](http://pclosmag.com/html/Issues/201011/page09.html) ::: LXDE: Meet The Heart & Soul &#8212; lxde-rc.xml
[http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html) ::: Openbox - Edit rc.xml to Gain Control

---

### Post by bapoumba on 2014-10-29
Thanks, I had tried a while back on 14.10 but everything broke. Kept keeping an eye on my 14.04 install, I like LXQt. I may need to partition again to have a closer look with 14.10.

---

### Post by vasa1 on 2014-10-29
> **bapoumba said:**
> Thanks, I had tried a while back on 14.10 but everything broke. Kept keeping an eye on my 14.04 install, I like LXQt. I may need to partition again to have a closer look with 14.10.
I think the lead lubuntu dev wants people to test using the iso route he indicated. That will be difficult for me.
All the same several users are in favor of going ahead for making 15.04 an LXQt release despite any shortcomings so that all/most wrinkles are sorted out by the time of the next LTS. They suggest that conservative users can stay with 14.04: [https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008676.html](https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008676.html) and following posts.

---

### Post by mikodo on 2014-11-26
> **vasa1 said:**
> Another route: [Lubuntu ISO prototype, build with LXQt, available for testing]("https://lists.ubuntu.com/archives/lubuntu-users/2014-October/008662.html")
I tried this, and was not able to install. I followed the link to: [http://people.ubuntu.com/~gilir/](http://people.ubuntu.com/~gilir/) I downloaded the latest .iso, checked the MD5sums, verified the burn, but no joy.

As soon as tried to go into the live session or to install, I got the message:

```
GDBus.ERROR:org.freedesktop.DBUS.Error.ServiceUnknown:
The Name org.freedesktop.PolicyKit1 was not provided by any .service files
```

I downloaded the AMD-64 .iso of Lubuntu 14.10 earlier, to try the PPA for the daily build update but, I see that the devop, used the 32-bit install in his .iso, so maybe I'll download the 32-bit Lubuntu 14.10 instead and then try the PPA, to update to what has been added for LXQT. But, not tonight. It is getting late now.

I didn't try to reach the devop, or file any bugs against it.

Regards.

Addendum: I sent a message to Julien Lavergne at [email]lubuntu-users@lists.ubuntu.com[/email] about this.

---

### Post by kalehrl on 2014-11-26
Just install policykit-1.

---

### Post by mikodo on 2014-11-26
> **kalehrl said:**
> Just install policykit-1.

Wait. I need to figure out how to install this on the install medium, (CD).

---

### Post by mikodo on 2014-11-26
I am using the QupZilla browser provided by the live CD in Lubuntu.

I installed policykit-1 in the live environment, but it has no icon on the desktop to install and I don't know what to do next.

When I rebooted with the install cd, and selected install Lubuntu, it threw the same error as in the initial post and took me back to the live environment. I installed policykit-1 again, but still I have no install icon.

I tried going into a tty and doing this, but either I am not hitting the right keys or, it is not letting me.

Stumped!


======


I installed it with the .iso of Lubuntu 14.10 and by following the ppa and commands vasa1 suggested in post #1. I used aptitude and it was complaining a bit, when I was installing the QT stuff, as it had to remove some of the LX stuff. But, that was what I wanted to see.

It looks nice. I am still customizing the desktop though.

No deal breakers yet, for my simple needs.


======


Well, I broke the install, when I was shutting off services, that it apparently needed.

That's all right. I wanted to see how LXQT was coming along. I was going to delete it before the day ended anyway.

All in all, it is very nice already. It was a little confusing, when configuring GTK and QT settings together, but I had enough time with it, to set the desktop pretty much to my liking.

I think it uses more cpu for display than does Xubuntu, as I saw some screen tearing with closing/minimizing pages. But, I have an older computer with intel integrated graphics. I'm sure, if I added a cheap GPU to it, I wouldn't see that.

It was very responsive and usable, with familiar settings, I expect with a light DE. All and all, a very nice experience. I hope it continues to grow.

Maybe next time, I will take a crack at installing Kwin, when it might be a little more user friendly to do. The guys in Arch doing it, are using more advanced piecing together for LXQT and Kwin, than I am prepared to deal with now.

---

### Post by vasa1 on 2014-11-28
> **mikodo said:**
> Well, I broke the install, when I was shutting off services, that it apparently needed.

That's all right. I wanted to see how LXQT was coming along. I was going to delete it before the day ended anyway.

All in all, it is very nice already. It was a little confusing, when configuring GTK and QT settings together, but I had enough time with it, to set the desktop pretty much to my liking.

I think it uses more cpu for display than does Xubuntu, as I saw some  screen tearing with closing/minimizing pages. But, I have an older  computer with intel integrated graphics. I'm sure, if I added a cheap  GPU to it, I wouldn't see that.

It was very responsive and usable, with familiar settings, I expect with a light DE. All and all, a very nice experience. I hope it continues to grow.
At least one of the LXQt devs is looking into making things more efficient: [http://sourceforge.net/p/lxde/mailman/message/33088016/](http://sourceforge.net/p/lxde/mailman/message/33088016/)

---

### Post by mikodo on 2014-11-28
> **vasa1 said:**
> At least one of the LXQt devs is looking into making things more efficient: [http://sourceforge.net/p/lxde/mailman/message/33088016/](http://sourceforge.net/p/lxde/mailman/message/33088016/)
Yes, I think he is a master. I forgot to mention in my earlier post(s), that I really like his [PCMan File Manager]("https://en.wikipedia.org/wiki/PCMan_File_Manager"). It reminded me of the old Nautilus FM before Gnome changed it to what it is now, but with extra features. I forget all I noticed but, being able to easily change it to twin panels is cool. The tabbed browsing is a nice feature. I think it had a button to use the FM in root, that was in the drop down list. I didn't take the time to see all it could do. I felt very comfortable with it, and felt some familiarness because of it reminding me of the old Nautilus.

---

