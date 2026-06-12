---
title: "Scribus - Font Problem AND Solution"
date: 2005-11-25
forum: Desktop Environments
---

### Post by darrensnospam on 2005-11-25
I installed Scribus from using Synaptic.
When I ran it, after the splash screen appeared, I received a Fatal Error window with the text:
There are no suitable Fonts on your System
Exiting now

I searched around on the web and the only reference I was able to find on the issue was located here: [http://www.webservertalk.com/message1111714.html](http://www.webservertalk.com/message1111714.html)

So I connected to the IRC forum for Scribus.
(for info on how to connect, see: [http://docs.scribus.net/index.php?lang=en&page=resources](http://docs.scribus.net/index.php?lang=en&page=resources)) 
where mrdocs helped me.

He had me create a folder called .scribus in my HOME folder.
I then created a file called scribusfont.rc inside the newly created folder.

In the file, I added the following lines:
/usr/share/fonts/truetype

/usr/share/fonts/type1
/usr/share/X11/fonts/Type1
/usr/share/fonts/type1/gsfonts

I saved the file, launched Scribus and the problem was solved.

mrdocs mentioned that this issue is presently being seen in Debian and Ubuntu distributions.

Enjoy!

---

### Post by darrensnospam on 2005-12-01
Need a little help on this.

Scribis works fine with the above tweak on my login.

I noticed that when I logged in as a different user, I experienced the same problem before the tweak.

I know that I can create the tweak in this users home account and resolve the issue but is there a global home account that I can put the tweak in so that any and all users are ready to go without having to add this tweak to everyone's home directory?

- darrensnospam

---

### Post by dada1958 on 2006-01-25
You can also get the latest stable Scribus, version 1.2.4.1 by adding:

# Ubuntu breezy
deb         [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted
deb-src     [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted

deb         [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted
deb-src     [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted[/

to your source.list, after you've done this:

apt-get update

But I have to tell you that I never had the problems you described with the version in the official repositories. I had those problems when I added an old Adobe Type 1 Garamond (1989) so I replaced that one with the OpenType version. No fonts related problems since then.

---

### Post by emperor on 2006-02-09
I had the same problem on my AMD desktop machine. However, both Dell laptops did NOT have this problem.

Creating ~/.scribus/scribusfont.rc

[quote=darrensnospam]
 /usr/share/fonts/truetype
/usr/share/fonts/type1
/usr/share/X11/fonts/Type1
/usr/share/fonts/type1/gsfonts
[/quote] 
Solved the problem, thanks!

---

### Post by John Jason Jordan on 2006-02-09
[QUOTE=dada1958]You can also get the latest stable Scribus, version 1.2.4.1 by adding:

# Ubuntu breezy
deb         [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted
deb-src     [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) breezy main restricted

deb         [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted
deb-src     [http://debian.tagancha.org/debian/](http://debian.tagancha.org/debian/) breezy main restricted[/QUOTE]
I just tried that and got:

Could not download all repository indexes

Followed by all four of the above repositories. 

Then it dawned on me that I have 64-bit Ubuntu. Are there 64-bit repositories for these sources?

---

