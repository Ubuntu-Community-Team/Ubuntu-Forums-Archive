---
title: "fireftp - STAY AWAY FROM THIS CRAP!"
date: 2006-04-13
forum: Desktop Environments
---

### Post by gymsmoke on 2006-04-13
I upgraded firefox to 1.5 on Ubuntu thinking that the "grass was greener"...
So, I get fireftp loaded, since the TLS/SSL ftp sites I need access to just can't be done with gftp (at least not with the watered-down compile that is the default install), and Igloo seems to work sporatically on Ubuntu...
fireFTP is a mess!!!!
I connect to a normal, port 21, PASV, ftp server (my ISP), and, after every 3 file transfers, either the ftp locks up altogether, or, if I "dare" abort, the entire firefox browser shuts down (with all my tabbed pages that I went searching for now GONE) ...

I know it's just too much to ask to have an ftp client that would just work (the command-line seems to have almost NO problems, but is a little bit ungainly to work in for lots of file setup/transfers), but it would really be nice if someone the size of Mozilla could at least think through a bit before releasing this garbage.

---

### Post by endersshadow on 2006-04-13
[QUOTE=gymsmoke]I upgraded firefox to 1.5 on Ubuntu thinking that the "grass was greener"...
So, I get fireftp loaded, since the TLS/SSL ftp sites I need access to just can't be done with gftp (at least not with the watered-down compile that is the default install), and Igloo seems to work sporatically on Ubuntu...
fireFTP is a mess!!!!
I connect to a normal, port 21, PASV, ftp server (my ISP), and, after every 3 file transfers, either the ftp locks up altogether, or, if I "dare" abort, the entire firefox browser shuts down (with all my tabbed pages that I went searching for now GONE) ...

I know it's just too much to ask to have an ftp client that would just work (the command-line seems to have almost NO problems, but is a little bit ungainly to work in for lots of file setup/transfers), but it would really be nice if someone the size of Mozilla could at least think through a bit before releasing this garbage.[/QUOTE]

While I begrudgingly use FireFTP and wait eagerly for the release of Filezilla v3 (for Linux!), I haven't had the crash problems.  In order to ensure yourself, though, try out the [Session Manager](https://addons.mozilla.org/firefox/2324/) extension so you don't have to worry about it.

---

### Post by dasunst3r on 2006-04-13
FireFTP is an extension that is developed by someone outside of Mozilla Corporation.  I hope that will clear things up a little.

---

### Post by gymsmoke on 2006-04-13
Ender~  I, too await FileZilla... It looks promising.
das~ It doesn't, really.  ftp isn't quite the same as brain transplantation, so it shouldn't be too difficult to build on what's already out there in ftp client libraries.  If you're going to release it, especially with the obvious blessing of Moz, it should work.

I actually solved this problem for the moment, thanks to Ubuntu and Nautilus...

Since the shared host is a simple login ftp server, I just opened two instances of file browser - one to the ftp, and the other to my local drive, and started copying...

if gftp would come as a binary compiled for auth ssl/tls, I wouldn't even be trying fireftp in the first place... (if I could get the information needed to re-compile it I would just do that)

The point of all this hair-pulling is just so I can setup a temp home for my existing mail and website while I setup Ubuntu as a server... something I've been itching to do since I started using Ubuntu about a month ago...

---

