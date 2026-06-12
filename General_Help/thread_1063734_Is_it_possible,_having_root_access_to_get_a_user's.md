---
title: "Is it possible, having root access to get a user's password?"
date: 2009-02-08
forum: General Help
---

### Post by Mamsaac on 2009-02-08
The server I own recently got hacked by a lamer. While he no longer has access to the server, he did change the guest password (which was the only account he got access to).

Is there a way to know what password he chose? I know I could simply change it, but I would like to know what he put.

Thanks

---

### Post by jouni on 2009-02-08
> **Mamsaac said:**
> Is there a way to know what password he chose? I know I could simply change it, but I would like to know what he put.

Only by running [_crack_]("http://en.wikipedia.org/wiki/Crack_%28software%29") or other similar software, and then only if the password is weak enough or you are willing to run the program long enough.

---

### Post by Mamsaac on 2009-02-08
I don't feel like bruteforcing into it.

Meh, I guess I will just reset it. Thanks.

---

### Post by Nepherte on 2009-02-08
The only option is brute forcing. The passwords are hashed before being stored.

---

### Post by albinootje on 2009-02-08
> **Mamsaac said:**
> The server I own recently got hacked by a lamer.

If your server was broken into, then the first thing I'd recommend is to do a *complete* reinstall!

If you have time, make a cloned image of your disk, and do some forensic research on it, before doing the reinstall.

If you did use some data integrity software like tripwire, fcheck, samhain etc. and/or you had your user chrooted severly, and you've checked all relating that, even then I would personally prefer a fresh install, and finding out how the attacker came in, anyway.

---

### Post by Mamsaac on 2009-02-08
I've search at the auth logs, the only thing that bothers me is this line:

Feb  2 13:26:29 XXXXXXX-laptop polkit-grant-helper[23673]: granted authorization for org.freedesktop.systemtoolsbackends.set to pid 23641 [uid=1000] [auth=XXXXXXX]


Where XXXXXXX is the name of the root user. It bothers me because it's right before the following line:

XXXXXXXX-laptop usermod[23740]: change user `guest' password

Thing is, it really bothers me. There's a known bug which I'm not sure if it ever got fixed.

[http://www.juniper.net/security/auto/vulnerabilities/vuln28702.html](http://www.juniper.net/security/auto/vulnerabilities/vuln28702.html)

I've closed all access to server. I don't want to reinstall, but check what he did and try to figure out the way to prevent it in the future.

---

### Post by Mamsaac on 2009-02-08
I think I will post this in the forum for servers, as it's more fitting.

---

