---
title: "how can i stay logged in using dillo?"
date: 2006-03-05
forum: Forum Feedback &amp; Help
---

### Post by fuscia on 2006-03-05
and while you're at it, how can i stop mispelling my username? ...dammit!

---

### Post by towsonu2003 on 2006-03-06
from their website:
[quote=dillo people]Cookies:

Because of privacy considerations, cookies are disabled by default in dillo. That is, if you just compile and use dillo, it will reject every single cookie sent to it!

If you want to know how to enable cookies in dillo, please read Cookies.txt. It explains everything in a brief and clear way (it's just a matter of setting up cookiesrc). [/quote]

Cookies.txt:
[quote=Cookies.txt]
Jan 2002, Jörgen Viksell - [email]xxxxxxxxxxxxxxxxx[/email],
          Jorge Arellano Cid --
Last update: May 2002


==================
 Cookies in Dillo
==================

 The cookie support in Dillo aims to support cookies of the old
original Netscape style, as well as the kind specified in RFC 2109.
 Between sessions, the cookies get saved to ~/.dillo/cookies.
At the moment the only enforcements on the amount of cookies to
save to disk is max 20 per domain.
 There's also a file for controlling cookies: ~/.dillo/cookiesrc. Dillo
initially sets it to ignore (reject) all cookies, so if you want to use
cookies, change it to meet your needs.

 If you don't want cookies at all, you have two options:

1.- Delete ~/.dillo/cookiesrc (or leave it just as dillo creates it).
2. Configure Dillo with ./configure --disable-cookies. Then all the
   cookie stuff will be skipped at compilation.


=====================
 Controlling cookies
=====================

 There is a small and simple way to restrict urls from setting cookies
in Dillo. In the file ~/.dillo/cookiesrc You may specify rules
for different domains. The syntax looks something like this:

DEFAULT       DENY
slashdot.org  ACCEPT
.host.com     ACCEPT_SESSION

 The first line says that we should deny all cookies from all domains
by default.
 The second one tells Dillo to save all cookies from slashdot.org
across sessions, until it expires.
 And finally, the third says that all subdomains of host.com should be
allowed to set cookies. But these cookies will only be saved in
memory until you exit.


===================
 Cookies & Privacy
===================

 Cookies can be a severe threat to personal privacy, as the pages you
visit can be tracked, logged, and associated to a peronal data-record,
allowing the possibility of building a more than detailed profile of your
browsing habits.

 This data is sold to companies that profit from direct use of such
information (SPAM, Spying, etc).

 If this data is cross-referenced with other databases, they can end up
with more information than you have about yourself.

 Some people may tell you this is "paranoid", but please, take my words
as of someone that has written a web browser, a cookies implementation,
and that has deep understanding of HTTP (RFC-2068) and cookies (RFC-2965).

 Non technical persons may like to read:
   [http://www.junkbusters.com/cookies.html](http://www.junkbusters.com/cookies.html)
   [http://www.newsfactor.com/perl/story/16455.html](http://www.newsfactor.com/perl/story/16455.html) (about user-spying)

 Dillo project is specially concerned about privacy and security issues,
and our advice is to avoid cookies whenever possible, and at most set
ACCEPT_SESSION to specific, trusted sites.  -- you have been warned.


==============
 Restrictions
==============

 If you use a single dillo with multiple windows, then there's no
problem, but if you launch different dillos the latter ones will
have cookies disabled.



Thats all folks![/quote]

Links are very interesting

---

### Post by fuscia on 2006-03-06
[QUOTE=towsonu2003]from their website:

Cookies.txt:

Links are very interesting[/QUOTE]

this was the content of my *~/.dillo/cookiesrc* file at the time i started this thread...

[i]"ubuntuforums.org
upstandingf***ingcitizens.org"[/i]

i have a lot less trouble staying logged into the second site than i do this one. i don't know what the old netscape treatment of cookies was, so perhaps therein lies the answer to my difficulty. would you happen to have an interesting link to such info?

---

### Post by towsonu2003 on 2006-03-06
sorry, I'm clueless about that...

---

### Post by majikstreet on 2006-03-06
umm maybe put "ACCEPT" afterwards? 

about the username, maybe you should put a huge banner above your monitor that says FUSCIA

---

### Post by towsonu2003 on 2006-03-06
found this:
[quote=Dillo People]
Q: Why doesn't Cookies work for me?
Please read Cookies.txt (also available in the tarball).

In a nutshell: Because of privacy considerations Dillo comes with cookies disabled by default. The above document explains it in detail.

Configuring cookies in Dillo is easy. For instance, some lines like these inside "~/.dillo/cookiesrc" could be enough to get you started:

DEFAULT DENY
slashdot.org ACCEPT
freshmeat.net ACCEPT_SESSION
.host.com ACCEPT_SESSION
.ebay.com ACCEPT_SESSION

Note: only the first Dillo instance, and all its child windows, will be cookies-enabled. If you launch another Dillo, it will disable cookies. This is a BUG and it will be fixed in the future, either by making cookies a plugin or by handling the race condition.[/quote]
[http://www.dillo.org/FAQ.html](http://www.dillo.org/FAQ.html)

---

### Post by fuscia on 2006-03-10
[QUOTE=towsonu2003]found this:

[http://www.dillo.org/FAQ.html](http://www.dillo.org/FAQ.html)[/QUOTE]

thanks for the suggestion, but i've already done all the stuff suggested by dillo. i've even recompiled it with a number of options, including the ssl one. i was hoping someone could explain how i could make it work as using cookies the way they suggest just doesn't work. i guess i'll just try their mailing list again (no luck with a previous attempt).

---

