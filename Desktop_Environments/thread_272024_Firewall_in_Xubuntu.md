---
title: "Firewall in Xubuntu?"
date: 2006-10-05
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-10-05
Hey, I'm having problems with my downloads in aMule.

I started wondering: is there a defult firewall in Xubuntu? Sounds unlikely, but still: Kad is always firewalled, and my downloads seem really stuck...

Thanks

Gabriel

---

### Post by moore.bryan on 2006-10-05
*did you just start having the problem?  do you have iptables rules setup to allow for the downloads?*

---

### Post by john.nicholls on 2006-10-05
There is no default firewall in Xubuntu.

John

---

### Post by GabrielWolff on 2006-10-06
> **moore.bryan said:**
> *did you just start having the problem?  do you have iptables rules setup to allow for the downloads?*

1) Yes, I started having that problem after having smooth downloads for a few weeks. Suddenly all went slow and stucky

2) Hmmmm. No clue. I don't even exactl knwo what you are talking about. How would I check that iptables rules issue?

Thanks


Gabriel

---

### Post by moore.bryan on 2006-10-06
[I](1) had you recently downloaded any programs?
(2) iptables is the built-in linux "port protection" system... i think that's a ridiculously simplistic description, but i'm not expert.  i've read other people having issues with download speeds related to iptables.  so, you do not currently have a firewall and there are no iptables rules.  what does ```
sudo iptables
``` give you?
[/I]

---

### Post by GabrielWolff on 2006-10-06
gabriel@gabriel:~$ sudo iptables
Password:
iptables v1.3.3: no command specified
Try `iptables -h' or 'iptables --help' for more information.
gabriel@gabriel:~$

I guess that's a no?

G

---

### Post by kikinovak on 2006-10-06
Hi,

You have two distinct problems.

1) There have been problems with the latest version of Amule. I can't say more, because I don't use it. But other people have had the same problem.

2) No, there's no firewall. If you want one, I recommend you bite into iptables. Take at least a few rainy afternoons to get into it.

To show the state of your firewall (as root):

```
# iptables -L -v; iptables -t nat -L -v
```

Cheers from another Xubuntu user.

---

### Post by GabrielWolff on 2006-10-06
> **kikinovak said:**
> Hi,

You have two distinct problems.

1) There have been problems with the latest version of Amule. I can't say more, because I don't use it. But other people have had the same problem.

Cheers from another Xubuntu user.

Praise the Lord, another Xubuntu user was found!! :-) 

Where'd you get that info from? I searched the forums and came up with nothing except for people really happy with their downloads...

G

---

