---
title: "Invalid output for dead key combination"
date: 2005-11-03
forum: Desktop Environments
---

### Post by marcelop on 2005-11-03
Hi,

I am having lots of fun with Ubuntu.  I think I finally can get ride of the M$ crap and use something I feel confortable.  There are only some problems I still have to solve.  Usually google gives me all the information I need, but this time I do some help.

When installing Breezy, I set the keyboad as "Brazil International" (or something like that).  The result was almost perfect...  I can use the dead key combinations to generate all the symbols I want (such as á,ã,ä and so).  The only problem is when I press '+c.  The symbol I am getting is **&#263;** when any brazillian would expect **ç** - actually the former doesn't exist in the Portuguese language.

So... is there any way to fix this - I mean how can I tell Ubuntu/gnome to output **ç** instead of **&#263;**?

Thanks in advance.

Some details:

- System->Preferences->Keyboard
        U.S. English International (with dead keys)

- xorg.conf
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
        Option          "XkbVariant"    "intl"

- Thinkpad T40

---

### Post by rbgkofi on 2005-11-03
Not Brazilian, and not sure... but try ,+c instead.

---

### Post by marcelop on 2005-11-04
Thx.  It didn't work - ',' is not considered a dead key.  The idea was good though ;-)

Btw, I have never experienced this problem on other systems such as M$, Debian+KDE, and RH.

---

### Post by easy_target on 2005-11-06
I am having the same problem but the answer I got in the forums was that I should enable composing and use the Right Win Key as the compose key. That way you can press "compose"  "," and "c". I think it is way too cumbersome but that's how I got around it.

---

### Post by marcelop on 2005-11-07
That works.  Thx a lot!

As you've said, it is not the perfect solution but, at least, I will be able to write Ç which is a *very* important letter in Portuguese.

Btw, for completeness purposes, <alt> works fine (my keboard doesn't have a "win key").

---

### Post by melissawm on 2005-12-10
I have a Dell laptop and that doesn't  work at all, since i don't have the right win key and the ALT key gives me the same &#263; as before. Please help... :(

---

### Post by simosx on 2006-01-28
To type Brazilian Portuguese, try out the (Flash) tutorial at
[http://planet.hellug.gr/misc/bra/](http://planet.hellug.gr/misc/bra/)

You get ç when you press ;

Make sure that you do not change xorg.conf; you can do all the steps from the graphical interface, which is the correct way to do things (tm).

---

