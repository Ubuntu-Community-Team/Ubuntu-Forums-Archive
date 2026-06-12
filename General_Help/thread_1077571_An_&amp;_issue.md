---
title: "An &amp; issue"
date: 2009-02-22
forum: General Help
---

### Post by Lars Stokholm on 2009-02-22
In my configuration file for the slrn newsreader I have this:
```
set Xbrowser "firefox '%s' > /dev/null 2>&1 &"
```
But if slrn is responsible for opening an instanse of Firefox, that instanse is killed when I quit slrn. To avoid this I tried:
```
set Xbrowser "nohub firefox '%s' > /dev/null 2>&1 &"
```
But that does nothing at all. How can I avoid Firefox is killed when I quit its parent (slrn)?

---

### Post by andrew.46 on 2009-02-23
Hi Lars,

I cannot reproduce this behaviour and I am using:

```
set Xbrowser "firefox '%s' &"
```

Can I ask which version of slrn you are using? The line above works without your error with:

```

andrew@skamandros~$ slrn --version | head -n 1
slrn pre1.0.0-2

```

BTW The real 'home' for slrn is news.software.readers, most of the slrn mafia can be found there and are usually happy to answer queries about the best newsreader in the entire world :-).

Andrew

---

### Post by Lars Stokholm on 2009-02-23
It's not related to slrn specifically. Try this: Open a terminal (I used gnome-terminal), run 'gedit &'. Now close the terminal and gedit will close along with it.

Now that we are talking about slrn, your Xbrowser command will give you all kinds of crap in the slrn window if Firefox gives you errors. My redirections will avoid this.

---

### Post by andrew.46 on 2009-02-23
Hi Lars,

OIC. I will admit I don't use the gnome terminal for slrn I use the xfce terminal under slackware. This effect is not seen in this setup. So I suspect this is a problem with the gnome terminal rather than slrn?

Andrew

---

### Post by KeyserSoze93 on 2009-02-23
> **Lars Stokholm said:**
> In my configuration file for the slrn newsreader I have this:
```
set Xbrowser "firefox '%s' > /dev/null 2>&1 &"
```
But if slrn is responsible for opening an instanse of Firefox, that instanse is killed when I quit slrn. To avoid this I tried:
```
set Xbrowser "nohub firefox '%s' > /dev/null 2>&1 &"
```
But that does nothing at all. How can I avoid Firefox is killed when I quit its parent (slrn)?

Sorry, but I have to check. You mean:
```
set Xbrowser "nohup firefox '%s' > /dev/null 2>&1 &
```
don't you?

---

### Post by Slim Odds on 2009-02-23
you're looking for nohup

:D  LOL (split second timing)

---

### Post by Lars Stokholm on 2009-02-23
Haha, yeah, I meant nohup with a P, but wrote it with a B in my configuration.

Thanks guys.

---

