---
title: "Banned from Ubuntu's IRC server :-["
date: 2009-06-21
forum: General Help
---

### Post by unimatrix on 2009-06-21
**Reason**: Voluntarily providing a Tor relay server.
**Reward**: Getting banned from irc.ubuntu.com (and many other IRC servers).

Big thanks.

---

### Post by DeMus on 2009-06-21
I don't know what happened and i don't think I want to know since I don't want to be in the middle of it, but using these kind of words here on the forum is not appropriate, is it?
You obviously have a dispute with the irc channel and you react here. Maybe it's because you can't find another place, but hey, did we do something wrong here?
If you like to explain what happened, what caused all of this, there might be a way to solve it. Shouting bad names without telling what's going on is useless and far from decent.

---

### Post by mhgsys on 2009-06-21
lol, 

Thnk you for making my day with posting this.
:P

---

### Post by unimatrix on 2009-06-21
OK then.
Here are the steps to reproduce this:

1) Install Tor server
2) Configure it to be a public relay
3) Wait a few minutes

Et voila, you're banned.

---

### Post by DeMus on 2009-06-21
> **unimatrix said:**
> OK then.
Here are the steps to reproduce:

1) Install Tor server
2) Configure it to be a public relay
3) Wait a few minutes

Et voila, you're banned.

Is there an address you can contact to inform about the why and how? I know nothing about irc since I never use it, so I am not familiar with it.
Maybe it was done automatically because a server noticed "something strange happening".
Try to get in touch with whoever is handling the irc to get things solved. I think that is the best you can do.

---

### Post by Soul-Sing on 2009-06-21
They are not very pleased with TOR, in the past there some
"attacks/issue's" on freenode which were related to TOR.

---

### Post by kerry_s on 2009-06-21
it could be as simple as a proxy its using is banned or you just configured it wrong.

---

### Post by DeMus on 2009-06-21
> **leoquant said:**
> They are not very pleased with TOR, in the past there some
"attacks/issue's" on freenode which were related with TOR.

Here you go, now you have an idea why you were banned. They see it as some kind of attack and don't want that.
Just talk to the guys, get rid of the server and try to get back in.

---

### Post by unimatrix on 2009-06-21
The things is freenode now wants me to use their secret tor service or something. But of course I'm not gonna do that, because I've removed Tor. There's **no way** I'm providing Tor relay service to the world if you get banned from IRC in return.

Also, I don't know who to contact. Any clues here?

---

### Post by unimatrix on 2009-06-21
> **kerry_s said:**
> it could be as simple as a proxy its using is banned or you just configured it wrong.

They've banned my static IP.

---

### Post by Soul-Sing on 2009-06-21
try: [http://t0x.in/ircfreenode.html](http://t0x.in/ircfreenode.html) with TOR, and your not able to access the page. Only a warning message.

---

### Post by Soul-Sing on 2009-06-21
> **unimatrix said:**
> The things is freenode now wants me to use their secret tor service or something. But of course I'm not gonna do that, because I've removed Tor. There's **no way** I'm providing Tor relay service to the world if you get banned from IRC in return.

Also, I don't know who to contact. Any clues here?

Contact freenode staff. Maybe someone here could help you.....

---

### Post by Elfy on 2009-06-21
Try #ubuntu-ops

---

### Post by unimatrix on 2009-06-21
> **forestpixie said:**
> Try #ubuntu-ops

Brilliant, now all I need to do to get there is get my IP unbanned. Oh, wait...

:P

---

### Post by Elfy on 2009-06-21
try another pc then :)

---

### Post by unimatrix on 2009-06-21
> **forestpixie said:**
> try another pc then :)

And what if I live in the middle of nowhere?

EDIT: Fine, I'm on my own. Guess Linus was right when he said the FOSS community was all about "do it yourself".

---

### Post by sdennie on 2009-06-21
If you setup a public proxy then your IP address is associated with anyone using your proxy.  If they get an IP ban, you get an IP ban.  People using Tor for IRC very well may use it to engage in activities they know well get them banned while avoiding the consequences of getting an IP ban on their real IP address.

---

### Post by memilanuk on 2009-12-21
Nuts.  I just got bit by this too.  Searched here and found this thread; guess I can take consolation in not being the only one.

In my case, I run Ubuntu 9.10 desktop from a Virtualbox guest on my Win Vista host.  The virtual NIC eth0 is bridged to my regular wireless network connection on my PC.  I registered a nick on Freenode a short while back, and either yesterday or today I figured, what the heck, I'll help Tor out and run a relay here on my Windows PC through my firewall.  The next time I fired up Ubuntu and tried to open Xchat, I found myself banned.

The really bizarre part is the language present on Freenode's policy page:

> 
Tor and Freenode

The Electronic Frontier Foundation's Tor project is a special case in freenode's treatment of proxy servers. Tor provides anonymous access to internet services, including IRC, and protects its users' privacy from various forms of traffic analysis. Currently under 100 users connect to the network via Tor, but that number continues to grow. **_[COLOR="Red"]The freenode network welcomes Tor users.[/COLOR]_**

Anonymous access to internet services is frequently abused. To provide reliable access while reducing the impact of any abuse on the rest of our users, we label user sessions conducted through various gateways, including Tor, with cloak hostnames beginning with gateway and ending in a token x-N... (where N... is a set of random hexadecimal digits which are different each time the user reconnects, and thus useless in denying any specific user access for very long).

Channel owners are free to deny access to their channels by various gateway users. But freenode and PDPC urge you not limit access to gateways too broadly or completely. Please don't ban *@gateway/* . Please use a "quiet" command instead of a "ban" if at all possible. For example, **_[COLOR="Red"]please don't ban Tor users[/COLOR]_**, as in the following command:

    /mode #foo +b *@gateway/tor/* 

Instead, please consider using a "quiet" command:

    /mode #foo +q *@gateway/tor/* 

and make such denials-of-access temporary, not permanent, whenever possible. Network staff can turn off new gateway connects on a temporary basis and kill out abusive users. We're happy to do so; simply contact a staffer whenever your channel experiences abuse.

Please remember that some users have very little choice about using gateways, and be considerate in your control of access.

The staff of freenode works to weed out various forms of abuse (such as user harassment, denial-of-service attacks and channel flooding) on a daily basis. Achieving this goal involves the use of a number of automated and semi-automated tools. We're often in a hurry to resolve a problem. Because of this, and because Tor creates special needs, access to the network by Tor users will occasionally be blocked. We apologize in advance for any problems of this sort and we ask for your patience and understanding. We support Tor and will do everything we can to resolve any access issues in a timely fashion.

Yet I got banned for simply hosting a TOR relay, much less trying to connect to Freenode via TOR?

WTF?!? (pardon my French)

Monte

---

### Post by unimatrix on 2010-02-02
I've talked to the guys on #freenode and they've unbanned me.

Marking as solved.

---

