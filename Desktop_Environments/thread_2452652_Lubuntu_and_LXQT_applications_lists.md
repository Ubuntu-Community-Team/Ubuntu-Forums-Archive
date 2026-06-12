---
title: "Lubuntu and LXQT applications lists"
date: 2020-10-26
forum: Desktop Environments
---

### Post by wugubee on 2020-10-26
Do we have list of supported LXQT applications list for Lubuntu (like 20.10 maybe?)

*currently I need email client with pop3 support,
what about virtualbox ?

Thank you,

---

### Post by ActionParsnip on 2020-10-26
What do you mean by "supported LXQT applications"?

If an application is coded in QT then it will run OK. If it is coded using GTK then you will need to install the GTK deps to make it work. These are all fully "supported". Everything you can install from the official Ubuntu repositories is fully "supported".

Virtualbox is in the repositories. You can install it using
```

sudo apt update
sudo apt install virtualbox

```

POP3 support is pretty basic. Thuderbird will do this well. If you want something lightweight on resources the Sylpheed or Clawsmail are 2 options I can think of quickly

---

### Post by wugubee on 2020-10-26
I mean applications that runs on LXQT, 
other distro has the list mentioned in their site,

Anyway is Thunderbird using GTK or what? thanks!

---

### Post by guiverc on 2020-10-27
LXQt should run any GTK2, GTK3 or Qt5 application; LXQt refers to the desktop itself; which will run other applications too.

I've been using `evolution` as my MUA (*mail user agent, or mail program*) since the GNOME 2 days, it's now GTK3 and won't be the most efficient on my Qt5 based Lubuntu LXQt system, but I'm not willing to change so I don't.  My desktop is also a dell from 2009, so it's somewhat resource challenged by today's standards, but it still works, and it's not the only old GTK program I'm using, so I'm willing to live with the resource hit (on this machine; I'm more careful when I've less RAM though).

I'll provide the following from Fedora - [https://fedoraproject.org/wiki/LXQt:_Suggested_Applications](https://fedoraproject.org/wiki/LXQt:_Suggested_Applications)

There is no difference with LXQt in different distributions, except the versions differ slightly (Fedora is only slightly behind my Ubuntu system, but openSuSE *tumbleweed* is actually ahead of my Lubuntu, Debian *sid* currently a fair bit behind :( )

One comparison in the Lubuntu wiki is as follows - [https://phab.lubuntu.me/w/bugs/](https://phab.lubuntu.me/w/bugs/)

but the list was created with the purpose being in helping users find the applications used, and thus where bugs should be filed.

If you want to look at what libraries are used by a program, ie. using your example of `thunderbird`, you can look at the dependencies ie.

[https://packages.ubuntu.com/groovy/thunderbird](https://packages.ubuntu.com/groovy/thunderbird)

one of which is **libgtk-3-0** which tells me it's GTK3 based.

If you compare with `trojita` which comes with Lubuntu desktop ([https://packages.ubuntu.com/groovy/lubuntu-desktop](https://packages.ubuntu.com/groovy/lubuntu-desktop))

[https://packages.ubuntu.com/groovy/trojita](https://packages.ubuntu.com/groovy/trojita)

you'll quickly see Qt5 libraries as required, eg. **libqt5core5a**.

That was only done for example purposes, with only a single library chosen (if you look you'll see more), plus you can look using commands too (eg. `apt-cache show thunderbird`)

You haven't specified any release details, so I've used the latest (*groovy*).

---

### Post by wugubee on 2020-10-30
Thank u help me alot...

---

