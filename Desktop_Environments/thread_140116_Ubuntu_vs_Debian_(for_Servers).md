---
title: "Ubuntu vs Debian (for Servers)"
date: 2006-03-05
forum: Desktop Environments
---

### Post by yamagami on 2006-03-05
Hi all
I'm running ubuntu as my primary os on my laptop for quite a while now and I'm very happy with it. Works a treat. 
I'm currently configuring a server with debian sarge, and as I was doing it, I thought - why not simply install ubuntu on it? 

Does anybody have any thoughts (experience?) on Ubuntu vs Debian for live/production web servers? 

Harel

---

### Post by 4dz0 on 2006-03-05
The stable release cycle for ubuntu is much shorter than it is for debian, so in my opinion ubuntu is the better choice. Ubuntu enables you to run a stable server with access to packages which are more up to date than those in sarge.

---

### Post by skymt on 2006-03-05
[QUOTE=4dz0]The stable release cycle for ubuntu is much shorter than it is for debian, so in my opinion ubuntu is the better choice. Ubuntu enables you to run a stable server with access to packages which are more up to date than those in sarge.[/QUOTE]
What he said, only with one provision. Debian, *because* of the longer release cycle, is actually a tad more stable than Ubuntu. If uptime is the deciding factor, choose Debian. Otherwise, Ubuntu is a good choice for servers, despite the desktop focus.

---

### Post by woob on 2006-03-05
I also would recommend Debian if stability is your major concern. Debian is like a 12 legged coffee table.

---

### Post by 4dz0 on 2006-03-05
[QUOTE=skymt]What he said, only with one provision. Debian, *because* of the longer release cycle, is actually a tad more stable than Ubuntu. If uptime is the deciding factor, choose Debian. Otherwise, Ubuntu is a good choice for servers, despite the desktop focus.[/QUOTE]

This is a good point, you can see that the final decision as to which distro to use will ultimately be based on what your requirements are.

---

### Post by BeeWee on 2006-03-05
I can recommend Ubuntu for servers, because I'm from the web-team of the German ubuntuusers forum where we use Ubuntu on our servers - without problems.

BeeWee

---

### Post by yamagami on 2006-03-07
Eventually I went with Sarge for the only reason that I haven't got it running around here anywhere and I didn't mind to be familiar with yet another distro. 

Thanks for all your input
Harel
:) 

Btw - do you know why the gnome version in sarge is labeled 2.8?

---

### Post by woob on 2006-03-08
Yamagami, 2.8 is the version of gnome that was released with sarge. Ubuntu breezy uses 2.12 and dapper will use 2.14. If I want something more up to date on my sarge install then I use backports.org. There you can find 002 and a lot of other newer apps. Good Luck, woob

---

### Post by nocturn on 2006-03-08
[QUOTE=4dz0]The stable release cycle for ubuntu is much shorter than it is for debian, so in my opinion ubuntu is the better choice. Ubuntu enables you to run a stable server with access to packages which are more up to date than those in sarge.[/QUOTE]

I went the Ubuntu route for my home server and it's running fine.
But it is also still on Hoary.  I'm thinking of upgrading it in the next couple of months, but going directly to Dapper is not supported (and maybe not even recommended).

So my point is, for a server, the 6 month release cycle is to much.  I would like to have a semi up-to-date system with a dist-upgrade to a new version every year.

---

### Post by nocturn on 2006-03-08
[QUOTE=woob]I also would recommend Debian if stability is your major concern. Debian is like a 12 legged coffee table.[/QUOTE]

To be fair, Ubuntu on the server is too.

One advantage of Debian is that stuff like ClamAV (for E-mail scanning), is updated via a volatile repository, while mine on Ubuntu is stuck in an old version and gives constant warnings about that.

---

### Post by yamagami on 2006-03-08
Woob, 
Thanks for the clarification. 

I doubt i'll upgrade any X related desktops for that server. It's command line all the way for that box. I only installed the desktops because I could (That 120GB drive is actually the biggest my household have seen - we might have lots of boxes around, but they are all a bit old-ish. What can I say - I am are barefoot cobbler).

Harel

---

### Post by nix4me on 2006-03-08
Debian for production server.  Ubuntu for desktop.

nix4me

---

### Post by powder on 2006-03-08
Debian, unless you absolutely need the 2.6 kernel vs. the 2.4 kernel in Debian.

---

### Post by cjazz on 2006-03-08
[QUOTE=powder]Debian, unless you absolutely need the 2.6 kernel vs. the 2.4 kernel in Debian.[/QUOTE]

To be fair, the 2.6 kernel is easily installed in Debian.

---

### Post by woob on 2006-03-09
[QUOTE=yamagami]Woob, 
Thanks for the clarification. 

I doubt i'll upgrade any X related desktops for that server. It's command line all the way for that box. I only installed the desktops because I could (That 120GB drive is actually the biggest my household have seen - we might have lots of boxes around, but they are all a bit old-ish. What can I say - I am are barefoot cobbler).

Harel[/QUOTE]
Yamagami, you are welcome. We have 6 puters here at home, most of which have been built from whatever I could scrounge, so I can relate. Good Luck, Woob

---

### Post by reech on 2006-03-28
Bit OT but here goes - anyone know how long Debian releases are supported / updated for? ie If I were to install sarge server today - for how long could I reasonably expect to get updates for?

---

### Post by woob on 2006-03-28
[QUOTE=reech]Bit OT but here goes - anyone know how long Debian releases are supported / updated for? ie If I were to install sarge server today - for how long could I reasonably expect to get updates for?[/QUOTE]
Reech, as long as you keep updating from Debian stable repositories you will be supported because once Etch is released it will become the stable version and so on, and so on, and so on,....   Woob

---

