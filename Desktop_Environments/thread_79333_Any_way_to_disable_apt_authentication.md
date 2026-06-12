---
title: "Any way to disable apt authentication?"
date: 2005-10-20
forum: Desktop Environments
---

### Post by iH8forcedRegistration on 2005-10-20
I feel like this must be a really stupid question, but I'm asking anyway:

I came to Ubuntu from Debian. For a while, every time I would do apt-get upgrade or apt-get install, it worked the way I expected it to-- I'd get prompted to make sure I wanted to install stuff, then the stuff would be installed. After about a week of that, it started prompting me a second time because none of my packages were "Authenticated." I was mildly annoyed at first, but I got over it, and I got used to having to press 'y' twice all the time.

Now, I think APT may be broken entirely on my machine, since I now get a GPG error every time I run apt-get update, and apt-get upgrade hasn't found any new packages in an extraordinarily long time (4 days and counting).
```
W: GPG error: http://archive.ubuntu.com breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

As you can probably tell from the error, this is on breezy. I've found several guides to fixing this problem, but all of them involve key managment in some way. If I have to, I'm willing to do that, but, I really fail to see what the point of software authentication is when all the software I use is open source. If anyone knows what it is, I welcome any enlightenment.

My goal is to disable the gpg keys on APT entirely. I want to trust everyone on my sources.list implicitly, because really, as far as I can tell, not trusting them is getting me nothing but annoyance. All of the guides I can find online for this refer to the nonexistant file apt.conf. I have an /etc/apt/apt.conf.d, but nothing in there looks familiar enough that I'm willing to mess with it.

If someone could point me to a guide for disabling APT authentication, tell me how to do it, or convince me that it's a bad idea, I'd be very grateful. Thanks in advance.

---

### Post by migueljacq on 2005-10-20
I don't know about disabling the authentication, but as for the BADSIG...

According to this thread, removing the 'us' from your repositories in sources.list gets rid of the BADSIG error.
might be worth copying the sources.list by dbott67 and then running apt-get update

[http://ubuntuforums.org/showthread.php?t=78010](http://ubuntuforums.org/showthread.php?t=78010)

---

### Post by iH8forcedRegistration on 2005-10-20
[QUOTE=migueljacq]I don't know about disabling the authentication, but as for the BADSIG...

According to this thread, removing the 'us' from your repositories in sources.list gets rid of the BADSIG error.
might be worth copying the sources.list by dbott67 and then running apt-get update

[http://ubuntuforums.org/showthread.php?t=78010](http://ubuntuforums.org/showthread.php?t=78010)[/QUOTE]

```
[arcturus:~] user> grep us /etc/apt/sources.list
## your rights to use the software. Also, please note that software in
[arcturus:~] user>

```

---

### Post by jackmacokc on 2005-10-20
[QUOTE=iH8forcedRegistration]```
[arcturus:~] user> grep us /etc/apt/sources.list
## your rights to use the software. Also, please note that software in
[arcturus:~] user>

```[/QUOTE]
i had these problems until i updated my repos to look like [this]("http://www.psychocats.net/sources.html")

---

