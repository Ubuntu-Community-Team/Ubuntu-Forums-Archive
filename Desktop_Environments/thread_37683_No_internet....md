---
title: "No internet..."
date: 2005-05-28
forum: Desktop Environments
---

### Post by master of all on 2005-05-28
When I use Kubuntu. When I'm either on Knoppix live boot or when I was on ubuntu It worked perfectly. Might it be something to do with an error messgae I got during installation about network configuration failing? If it is that, what can I do? (My computer is connected to my dads who has the internet connection. I think his acts as a Proxy server... or something. I know next to bothing of networking.)

---

### Post by GeneralZod on 2005-05-28
It's odd  that it works under Ubuntu but not under Kubuntu.  At a command prompt, try:

```

sudo kcontrol

```

Click Internet and Network -> Network Settings and try to enable your network interface.  If that doesn't work, please post the output of ifconfig.

Cheers,
Simon

---

### Post by master of all on 2005-05-28
When I did sudo kcontrol it open up control but gave me an error message in the terminal. ```
ERROR: Communication problem with kcontrol. It probably scrashed
```  when It opend up fine. I can access the shared network folder that my and my dad's computer share perfectly. But still no internet.

---

### Post by GeneralZod on 2005-05-28
[QUOTE=master of all]When I did sudo kcontrol it open up control but gave me an error message in the terminal. ```
ERROR: Communication problem with kcontrol. It probably scrashed
```  when It opend up fine. I can access the shared network folder that my and my dad's computer share perfectly. But still no internet.[/QUOTE]

I guess it's a DHCP problem, then, or something - I also know very little of networking, I'm afraid.  Try disabling then enabling the network card.  If this doesn't work, post the output of ifconfig.

---

### Post by master of all on 2005-05-28
Well, it's sorted now. I accidentally cicked the reset button which did something to one of the important files in / so I reinstalled Kubuntu and all is fine. Thanks for trying to help me. :)

---

