---
title: "Is there a Norton Internet Security type program for ubuntu?"
date: 2006-01-08
forum: General Help
---

### Post by pianoboy3333 on 2006-01-08
Is there a Norton Internet Security type program for ubuntu? Some program with internet controlls like Norton? My parents want to use parental controlls to block certain web pages etc.

---

### Post by handy on 2006-01-08
If you are not serving to windoze, & you have a router that uses NAT, then you really shouldn't need to worry about the security situation, it is nothing at all like the windoze system.

Have a read of this it explains it very well:

 [http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

I hope that helps you, I asked the same kind of question, & was given the same kind of answer & this link!  :KS 

Cheers,

handy

---

### Post by jon_z on 2006-01-08
its not a matter of viruses i think, hees asking about parental controls, and content filtering for young'ins.  I have no information i can give on this though I apologize.

---

### Post by pianoboy3333 on 2006-01-08
I understand that but, my parents want some kind of internet parental control program so I don't go off looking at porn or somthing.

---

### Post by Quirky on 2006-01-08
A simple way to block a web site is to add the address to /etc/hosts as follows. For example to block the advert/spam company adclick:

```

127.0.0.1   adclick.com

```

Providing you don't have root access, you can't change this file and access that site. If you have root access then your parents can't do much to prevent you looking at whatever web site you want...

(this works by saying the site adclick.com has the address 127.0.0.1 - the local computer - where the page will not exist)

---

### Post by jon_z on 2006-01-08
checking out synaptic quick i saw this
try:
sudo apt-get install dansguardian   *edit* fixed typo


another option is privoxy

---

### Post by bunced on 2006-01-08
[http://www.censornet.com/?sc=0](http://www.censornet.com/?sc=0)

---

### Post by socrazy143 on 2006-01-08
Actually there is a program for what you are looking for.  DansGuardian can be found at [http://www.dansguardian.org]("http://www.dansguardian.org")

Here is some info from their site:

> DansGuardian is an award winning Open Source web content filter which currently runs on Linux, FreeBSD, OpenBSD, NetBSD, Mac OS X, HP-UX, and Solaris. It filters the actual content of pages based on many methods including phrase matching, PICS filtering and URL filtering. It does not purely filter based on a banned list of sites like lesser totally commercial filters.

DansGuardian is designed to be completely flexible and allows you to tailor the filtering to your exact needs. It can be as draconian or as unobstructive as you want. The default settings are geared towards what a primay school might want but DansGuardian puts you in control of what you want to block.

DansGuardian is a true web content filter. 

;)

---

### Post by pianoboy3333 on 2006-01-08
It seems like I installed DansGuardian with the Synaptic Package Manager, but how do I run/open the program? I'm a bit new to ubuntu.

---

### Post by lynx2cross on 2006-01-08
I'm new to Ubuntu, but I've noticed that sometimes when I install a program it's not visible in the menu right away so I would restart the pc and then check the applications menu and the program is now there.  Maybe try that.  Unless it's a prgram that can be only run from a terminal window.

---

### Post by kaamos on 2006-01-08
[QUOTE=lynx2cross]I'm new to Ubuntu, but I've noticed that sometimes when I install a program it's not visible in the menu right away so I would restart the pc and then check the applications menu and the program is now there.  Maybe try that.  Unless it's a prgram that can be only run from a terminal window.[/QUOTE]
No need to restart. "killall gnome-panel" in a terminal refreshes the the panel, and you can see the new programs.

---

### Post by handy on 2006-01-08
[QUOTE=jon_z]its not a matter of viruses i think, hees asking about parental controls, and content filtering for young'ins.  I have no information i can give on this though I apologize.[/QUOTE]

Oops, that was me speed reading again in the early ours of the morning...:rolleyes: 

Some people just don't know when to go to bed. :razz: 

At least I left an informative link!

Cheers,

handy

---

### Post by pianoboy3333 on 2006-01-08
Its a terminal program, but I don't know how to use it. Can anyone help me? *edit* OR it's my graphics card, I have an ATI X600 256 MB... I can't play any games right now...

---

### Post by Wallakoala on 2006-01-09
[QUOTE=pianoboy3333]Its a terminal program, but I don't know how to use it. Can anyone help me? *edit* OR it's my graphics card, I have an ATI X600 256 MB... I can't play any games right now...[/QUOTE]

I'm pretty sure its not your graphics card....
You might want to try this: [https://addons.mozilla.org/extensions/moreinfo.php?id=226&application=firefox](https://addons.mozilla.org/extensions/moreinfo.php?id=226&application=firefox)

It's a firefox extension (assuming you use firefox) that blocks explicit sites. Password protected. Good stuff. You might want to do a forum search on that dansguardian to learn how to use it.

Good Luck,
Walla

---

### Post by Wallakoala on 2006-01-09
[http://www.savs.hcc.edu.tw/~chuavv/articles/dansguardian-en.html](http://www.savs.hcc.edu.tw/~chuavv/articles/dansguardian-en.html)

Try that guide. Seems very easy to follow and will help you set up dans guardian.

---

### Post by pianoboy3333 on 2006-01-09
I have no freakin idea how to use it... oy...

---

### Post by danoyoto on 2006-01-20
I have no idea either!  Looking for some help here......do I NEED to install Squid?  I want to set this up on my home computer (no proxy or anything) does anyone know if this is possible?

---

### Post by eric.duveau on 2006-01-20
[QUOTE=danoyoto]I have no idea either!  Looking for some help here......do I NEED to install Squid?  I want to set this up on my home computer (no proxy or anything) does anyone know if this is possible?[/QUOTE]

There is a procedure in French, you can translate it easily with altavista or google.

[http://www.s2ii.com/blog/index.php/?2005/12/23/50-filtrage-de-contenu-web-avec-squid-et-dansguardian](http://www.s2ii.com/blog/index.php/?2005/12/23/50-filtrage-de-contenu-web-avec-squid-et-dansguardian)

I would be happy to sponsor a automatic script to achieve that ($100)

---

### Post by nocturn on 2006-01-20
[QUOTE=pianoboy3333]It seems like I installed DansGuardian with the Synaptic Package Manager, but how do I run/open the program? I'm a bit new to ubuntu.[/QUOTE]

Dansguardian is not a GUI program, it runs in the background.

You have to configure it (starts up at boot time) and enter the IP of your computer as a proxy in firefox.

---

### Post by chaumurky on 2006-01-20
There appears to be a frontend for webmin:

[http://sourceforge.net/project/showfiles.php?group_id=51969&release_id=157263](http://sourceforge.net/project/showfiles.php?group_id=51969&release_id=157263)

---

### Post by ace2005 on 2006-01-20
[QUOTE=pianoboy3333]I understand that but, my parents want some kind of internet parental control program so I don't go off looking at porn or somthing.[/QUOTE]

Well most of this will be useless because you installed it, you can get arround it, by turning the proxy off, creating a second user account without restrictions (Alt + F2, Options > Runs as different user), using a different browser which can only be accessed via a custom command, using a p2p app... lets not give you too many ideas now

I doubt my parents know what konqueror is, and then they'd have to figure out that files starting with a full stop "." are hidden and then figure out how to mount a drive, for which they'd need the root password, its all an illusion, just because the system logs in on startup, and gives the user access to all the apps and the stuff in the my documents area, doesn't mean that stuff can't be hidden, however it makes them feel like nothing is hidden. ;)

Although this would suck if your parents know how to use linux well

Edit: I haven't set any of this up, i'd be too much trouble, just stick it in ~/kde/share/apps/Ksomething/ and name it something like sys.x instead of xxx.avi incase someone does a search

---

