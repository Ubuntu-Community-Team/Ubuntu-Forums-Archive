---
title: "Problem Setting Up MySQL for Amarok"
date: 2008-12-13
forum: General Help
---

### Post by jpoRS on 2008-12-13
Hey All,

I am having [some problems]("http://ubuntuforums.org/showthread.php?t=1010410") with collection management in Amarok (currently using SQLite), and I have been meaning to set up MySQL anyway, so I figured this was as good an excuse as any.

When trying to do the install described [HERE]("http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html") mysql-client goes fine, no problems there, but mysql-server gives me this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Being able to read, I listen to the error message and try:

```
owner@ubuntu:~$ sudo apt-get -f install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  mysql-server: Depends: mysql-server-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Oh, so you just want me to do -f install, ok:

```
owner@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  mysql-server-5.0
The following NEW packages will be installed:
  mysql-server-5.0
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/27.4MB of archives.
After this operation, 90.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 146033 files and directories currently installed.)
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.0.67-0ubuntu6_amd64.deb) ...
ERROR: There's not enough space in /var/lib/mysql/
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.67-0ubuntu6_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.67-0ubuntu6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

. . . am I missing something here?

After trying all this several times, restarting (both the process and the computer) several times, and getting the same results every time, I have decided to Ubuntu's limitless collective wisdom.  What am I doing wrong, or what do I need to do?

The particulars:
8.10, System76 Pangolin, Amarok 1.4.10 (I don't see how that could be relevant, but who knows).  Pretty standard setup for nearly everything.

Thanks,
jim

---

### Post by Sami_Sdata on 2008-12-13
Well, there are walkthroughs areound that will show you how to set this up.  However, Amarok 2 doesn't have the option to use mysql so as soon as that is pushed out to Ubuntu you will just be importing them into the new Amarok database.

---

### Post by jpoRS on 2008-12-13
Hey Sami,

I was following the walk through I linked, and after that failed I every other walk through I could fine with the same problem presenting itself every time.

Thanks for the heads up about Amarok 2 though.  Definitely reassuring that if no one can help me, the problem will solve itself soon enough.  That said I would prefer to have get this working on my own, because I want to listen to my music sooner rather than later.

jim

---

