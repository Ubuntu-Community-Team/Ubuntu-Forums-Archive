---
title: "gmrun :: ~/.gmrunrc examples?"
date: 2009-06-07
forum: Desktop Environments
---

### Post by Salute on 2009-06-07
Hi, does anyone use this nifty little app? If so please post your .gmrunrc example so I can follow suit

---

### Post by kerry_s on 2009-06-07
i use gmrun for my alt+f2 on jwm, i don't even bother with the "~/.gmrunrc" or "/usr/share/gmrun/gmrunrc" i'll usually just use the history or type it out.

---

### Post by Nythain on 2009-06-07
i use gmrun in awesome, but im with kerry_s on this one... i didnt even realize there WAS an rc for it

---

### Post by Salute on 2009-06-08
[http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg155843.html](http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg155843.html)
[https://bitbucket.org/ursm/dotfiles/src/ace02d846c5e/dot.gmrunrc](https://bitbucket.org/ursm/dotfiles/src/ace02d846c5e/dot.gmrunrc)

Pretty much got it now , just touch ~/.gmrunrc and my example:

```

# Set window geometry
Width = 500
Top = 350
Left = 250

# You can make aliases withing gmrun, for example:
# My second firefox profile (made with `firefox -ProfileManager`)
URL_ff =`/usr/bin/firefox -P 2`                         #type ff:

Terminal = gnome-terminal                               #type ctrl-enter
TermExec = gnome-terminal -e
URL_http = /usr/bin/firefox %u
URL_https = /usr/bin/firefox %u
URL_uf = /usr/bin/firefox http://ubuntuforums.org/      #type uf://
URL_mail = /usr/bin/firefox https://mail.google.com/    #type mail://

URL_top = ${TermExec} '%s'                    #type [command] ctrl-enter
URL_mc = ${TermExec} '%s'
```

---

### Post by HungryMan on 2009-08-06
I never knew URL_ can be used to make aliases... great work, Salute.
I salute you. lol

---

### Post by jjgomera on 2009-08-06
wow, i knew the gmrun_history, but i dont realize I can use a rc, thanks

---

### Post by HungryMan on 2009-08-07
I just wanted to share this.
```

# Google Desktop-esque search. Just type 'google:keyword' to use.
URL_google = x-www-browser 'http://www.google.com.ph/search?q=%s'

```

---

### Post by SushiR on 2009-09-15
> **HungryMan said:**
> I just wanted to share this.
```

# Google Desktop-esque search. Just type 'google:keyword' to use.
URL_google = x-www-browser 'http://www.google.com.ph/search?q=%s'

```

Nice! :-)

---

### Post by Tibuda on 2010-01-29
this will open mailto:name@host.com urls in gmail compose box
```
URL_mailto = x-www-browser https://mail.google.com/mail?view=cm&tf=0&to=%s
```

---

### Post by sumadartsan on 2010-05-02
From version 0.9.1-1

---

### Post by phaedrus54 on 2010-10-02
Thanks for posting your example.

I've used Launchy very happily on Windoz but it's buggy in Linux, so I'm going for Gmrun instead.

---

