---
title: "This installation doesn't support glibc-2.1 on Linux / x86"
date: 2005-08-04
forum: Gaming &amp; Leisure
---

### Post by Bloke on 2005-08-04
I'm trying to install savage, and this is the error I receive:


one@localhost:~/Desktop$ ./INSTALL.linux
This installation doesn't support glibc-2.1 on Linux / x86

Please contact Loki Technical Support at [email]support@lokigames.com[/email]


How can this be fixed?
(screenshot attached)

---

### Post by strikeforce on 2005-08-04
Whats in your logs?  Can you check the spec's required to run it?

---

### Post by Bloke on 2005-08-05
[QUOTE=strikeforce]Whats in your logs?  Can you check the spec's required to run it?[/QUOTE]


Which logs? 

My system "spec's" are fine. This exact system with FC3 ran the game fine.

---

### Post by Bloke on 2005-08-05
bump

---

### Post by Bloke on 2005-08-07
bump

---

### Post by Bloke on 2005-08-08
bump

---

### Post by Bloke on 2005-08-09
bump

---

### Post by strikeforce on 2005-08-09
I might need a later version of glibc Fedora uses semi-bleeding edge versions of programs.  Sorry for not repling sooner I've been away.

```

[root@fcserver ~]# gcc -v
Reading specs from /usr/lib/gcc/i386-redhat-linux/3.4.4/specs
Configured with: ../configure --prefix=/usr --mandir=/usr/share/man --infodir=/usr/share/info --enable-shared --enable-threads=posix --disable-checking --with-system-zlib --enable-__cxa_atexit --disable-libunwind-exceptions --enable-java-awt=gtk --host=i386-redhat-linux
Thread model: posix
gcc version 3.4.4 20050721 (Red Hat 3.4.4-2)

```

Thats an FC3 box that I have.

---

### Post by Bloke on 2005-08-09
Can multiple versions of gcc exist on the same system? Or is it impossible being the system is built around a specific version of gcc?

---

### Post by wmcbrine on 2005-08-12
[QUOTE=Bloke]Can multiple versions of gcc exist on the same system? [/QUOTE]
Sure, no problem. I have gcc-3.3, gcc-3.4, and gcc-4.0, all from Synaptic.  3.3 is the default, which I get if I type "gcc" alone.

But I don't think that helps you. It's a different glibc it wants, not gcc. Have you contacted Loki Technical Support?

Hmm... it's complaining about glibc-2.1, but current Hoary (you are on Hoary, right?) is at 2.3.2. Looks like a bogus check.

---

### Post by hammett111 on 2005-08-12
If you are running an AMD64 machine, not x86 then you are gonna have to use the command linux32 to install it. You will have to get this from synaptic/kynaptic.
 ;-)  ;-)

---

### Post by Bloke on 2005-08-13
[QUOTE=wmcbrine]Sure, no problem. I have gcc-3.3, gcc-3.4, and gcc-4.0, all from Synaptic.  3.3 is the default, which I get if I type "gcc" alone.

But I don't think that helps you. It's a different glibc it wants, not gcc. Have you contacted Loki Technical Support?

Hmm... it's complaining about glibc-2.1, but current Hoary (you are on Hoary, right?) is at 2.3.2. Looks like a bogus check.[/QUOTE]


I contacted Loki support first thing. My email was returned saying they dont exist.

I'm runnin Hoary 5.04 / Gnome 2.10.0 / kernel 2.6.10-5-686.

If its a bogus check, can I 'trick' the installer to not check gcc?

---

### Post by Bloke on 2005-08-13
[QUOTE=hammett111]If you are running an AMD64 machine, not x86 then you are gonna have to use the command linux32 to install it. You will have to get this from synaptic/kynaptic.
 ;-)  ;-)[/QUOTE]


x86 here

---

### Post by Bloke on 2005-08-14
I found this on another board, but I dont understand how to "set LD_PRELOAD" (if it will help):

------------------------------------------------------------------------------------------------------------------

Posted August 31, 2003 03:02 AM

    quote:  
    Yeah I'm also waiting for the linux version!
    Anyone knows if it requires a specefic glibc?
    Is there a list of requirtments for the Linux version?


reply:
I know that it requires to set LD_PRELOAD
environment variable if you have gcc-3.2.x
to libstdc++.so.5.0.1

------------------------------------------------------------------------------------------------------------------

---

### Post by Bloke on 2005-08-15
bump

---

### Post by Bloke on 2005-08-17
bump

---

### Post by Bloke on 2005-08-21
bump

---

### Post by rottenart on 2010-04-20
Bump because I have the exact same problem.

---

