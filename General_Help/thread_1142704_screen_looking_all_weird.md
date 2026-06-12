---
title: "screen looking all weird"
date: 2009-04-29
forum: General Help
---

### Post by nbv4 on 2009-04-29
I have this command:

urxvt -geometry 160x42 -e sh -c "screen -r || screen -U irssi"

in a launcher that rests on my desktop that I use to open my IRC window. I've been using this bit of code for the past 2 years or so. Recently I upgraded to 9.04 and not screen looks completely different. It used to just look like a regular terminal window, but now theres all this dumb crap at the bottom and a scroll bar on the side. How do I get rid of this? Here is a screenshot:

[img]http://img91.imageshack.us/img91/7992/irssi.png[/img]

---

### Post by CatKiller on 2009-04-29
I'm sure that you can turn it off, although I don't know how.

This is what it is, though:

[http://arstechnica.com/open-source/news/2009/04/ubuntu-brings-advanced-screen-features-to-the-masses.ars](http://arstechnica.com/open-source/news/2009/04/ubuntu-brings-advanced-screen-features-to-the-masses.ars)

---

### Post by geirha on 2009-04-29
Seems the defaults for screen and rxvt has changed. To get the scrollbar away, edit ~/.Xdefaults and add the line
```
Rxvt*scrollBar: False
```

alternatively, you can add the +sb option to urxvt.

By dumb-crap at the bottom, I assume you mean the date and time at the bottom right, and the window list on the second-last line? I'm guessing /etc/screenrc has been changed in the newer version, and adds those. Look at /etc/screenrc and look for lines starting with hardstatus and caption. Comment them out. What those commands do are documented in screen's man-page
```
man screen
```

---

### Post by nbv4 on 2009-04-30
Yeah I got the scroll bar removed, thanks. As for the status bar at the bottom, I still can't figure out how to get rid of it. I want the line thats says "[(status)]" to be at the very bottom, like how it is when irssi is running outside of screen. I tried running screen-profiles and unchecking all the items, but an empty status bar appears. I also tried to delete ~/screen-profiles and ~/.screenrc, but the status bar is still there. In /etc/screenrc, this is what I have:

```
# turn sending of screen messages to hardstatus off
hardstatus off
# Set the hardstatus prop on gui terms to set the titlebar/icon title
termcapinfo xterm*|rxvt*|kterm*|Eterm* hs:ts=\E]0;:fs=\007:ds=\E]0;\007
# use this for the hard status string
hardstatus string "%h%? users: %u%?"

# An alternative hardstatus to display a bar at the bottom listing the
# windownames and highlighting the current windowname in blue. (This is only
# enabled if there is no hardstatus setting for your terminal)
#
#hardstatus lastline "%-Lw%{= BW}%50>%n%f* %t%{-}%+Lw%<"

```

Looks to me like it's turned off. Yet it's still there...

---

