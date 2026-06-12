---
title: "kppp/pppd Problem"
date: 2005-05-17
forum: Desktop Environments
---

### Post by Blodhevn on 2005-05-17
So I finally got around to installing Kubuntu [5.04] last night, and must say I like the "look and feel" of it (well, KDE) so far. I've tried a few distributions in the past (Red Hat 8 and more recently Ubuntu 4.10) but they've either rubbed me the wrong way (as in, I don't really like the "look and feel" of GNOME) or had problems in their own right (Ubuntu 4.10 didn't seem to like my modem *at all*), so i've never really had Linux installed for more than a day or two at any specific time; anyway - back on-topic - all was going well until I tried to dial-up to the internet.

I got everything set-up nicely to dial the internet, but after KPPP finishes dialling (successfully) it drops the connection and the log window's status bar hangs at "Starting pppd.."

The error that KPPP gives me says:
"The pppd daemon died unexpectedly
Exit status: 1"

KPPP's log says:
"The remote system is required to authenticate itself
But I couldn't find any suitable secret (password) for it to use to do so.
(None of the available passwords would let it use an IP address.)"

So, being somewhat of a Linux noob, i'm at a bit of a loss for what to do here. I made the resolv.conf that KPPP was initially complaining about not finding, so I assume it's not related to that?

If anyone could help me here i'd be grateful. I mean, i'm having a few other minor problems with Kubuntu, but i'd like to get this fixed up first so that I can at least get on to the internet (and therefore post here if I need to) from *within* Kubuntu.

Thanks in advance.

---

### Post by wwwolf on 2005-05-17
[QUOTE=Blodhevn]I got everything set-up nicely to dial the internet, but after KPPP finishes dialling (successfully) it drops the connection and the log window's status bar hangs at "Starting pppd.."

The error that KPPP gives me says:
"The pppd daemon died unexpectedly
Exit status: 1"

KPPP's log says:
"The remote system is required to authenticate itself

Thanks in advance.[/QUOTE]

Try editing the file /etc/ppp/peers/kppp-options and change 'auth' to 'noauth'

See if that works for you,

HTH,

---

### Post by Blodhevn on 2005-05-17
[QUOTE=wwwolf]Try editing the file /etc/ppp/peers/kppp-options and change 'auth' to 'noauth'

See if that works for you,

HTH,[/QUOTE]

Yes, it did. :)

Awesome. Many thanks.

Although it already had 'noauth', it was #'d out which was causing the problem. The only other thing I had to do is add my ISP's DNS servers (which I retrieved the IP addresses of earlier today when I was having the problem) otherwise it wasn't recognising any sites. Not something i'm used to having to do in Windows (which seems to detect the DNS stuff itself) but at least I managed to finally get it working. :]

---

