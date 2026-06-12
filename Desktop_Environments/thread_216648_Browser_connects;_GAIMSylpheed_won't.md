---
title: "Browser connects; GAIM/Sylpheed won't"
date: 2006-07-15
forum: Desktop Environments
---

### Post by argotnaut on 2006-07-15
Hello,

I'm using 6.06 with all updates installed, using wireless on eth1. Everything was working perfectly until my husband accidentally shut down our Actiontec DSL modem.

When we restarted the modem, my browsers (both Opera and Flock) would connect to some sites after a long delay, but mostly wouldn't connect to anything. GAIM and Sylpheed-Claws-GTK2 could not connect to anything.

Restarted my computer, turned off ipv6 for the heck of it, restarted the modem, and finally browsers would connect reliably. However, other things won't. Here's what's working and what's not:

CONNECTS OK:
Opera browser 9
Flock browser 0.7.1
CheckGmail v1.9.2

WON'T CONNECT AT ALL:
Sylpheed-Claws-GTK2 2.1.1
GAIM 2.0.0b3
gFTP 2.0.18

I'm using DHCP, Actiontec is modem/router, and I did check the DNS numbers on it. I tried manually changing the DNS in my network settings to the ones listed by the Actiontec, but this didn't help.

I don't know if this is related, but when I open GAIM in a terminal, I get "Attempt to register the same DBusConnection with the message bus, but it is already registered." All others just give me a timeout error.

Any ideas? Any other info I need to post?

Thank you!

---

### Post by argotnaut on 2006-07-17
(bump)

---

### Post by Supermort on 2006-07-19
I'm in the same boat here.  Fresh install of 6.06, updated.  Turned off ipv6 and firefox connected but gaim still wont connect.  I also have an Actiontec DSL modem, maybe this has something to do with it?

---

### Post by argotnaut on 2006-07-19
Probably -- I've had problems with it in the past. I hate that #$@!!! piece of #%!@@!!

---

### Post by argotnaut on 2006-07-20
BTW, Supermort, I presume that since you say you're using a fresh install, the problem has existed right from the beginning, rather than cropping up later?

---

### Post by Supermort on 2006-07-20
Yes, thats true, a fresh install of kubuntu gave the same results.

---

### Post by Supermort on 2006-07-24
Got it, changed network setting under Gaim from 'no proxy' to 'use environmental settings'.  Bingo.  Oddly enough 'no proxy' works just fine for my XP machine running Gaim on the same network.

---

### Post by argotnaut on 2006-07-25
I can't find that setting in Gaim -- which version are you using?

Anyway, I haven't used my computer in a few days, and it magically worked when I turned it back on today. [shrug]

---

