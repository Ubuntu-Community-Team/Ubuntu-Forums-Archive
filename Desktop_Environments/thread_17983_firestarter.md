---
title: "firestarter"
date: 2005-03-03
forum: Desktop Environments
---

### Post by danip on 2005-03-03
I just insatlled firestarter firewall and its great except for one thing.  I connect to a direct connect hub that runs on the internal network of my college and firestarter is preventing me from connecting to it.  Can anyone help me in configureing it so that I can connect to it?

---

### Post by bored2k on 2005-03-03
another firestarter question:

Does firewall hav anywhere someplace to allow specific ports already forwarded? [i do a LOT of .torrent download, gotta keep `em ports open  :p ]

---

### Post by JmSchanck on 2005-03-03
[QUOTE=bored2k]another firestarter question:

Does firewall hav anywhere someplace to allow specific ports already forwarded? [i do a LOT of .torrent download, gotta keep `em ports open  :p ][/QUOTE]

I have firestarter working with bittorrent, the way i did it is just open up firestarter:

```

$ sudo firestarter

```

Hit the tab over to "Policy" click add rule and give it:

Name: BitTorrent
Port: 6881-6889
When Source is: Anyone

hit add and you should be good to go (assuming of course that if you have a router you've already forwarded that range to your box).

:)

---

### Post by bored2k on 2005-03-03
[QUOTE=JmSchanck]I have firestarter working with bittorrent, the way i did it is just open up firestarter:

```

$ sudo firestarter

```

Hit the tab over to "Policy" click add rule and give it:

Name: BitTorrent
Port: 6881-6889
When Source is: Anyone

hit add and you should be good to go (assuming of course that if you have a router you've already forwarded that range to your box).

:)[/QUOTE]


I love you ...  :rolleyes:

... my add rule is grayed out !!! ?!

---

### Post by JmSchanck on 2005-03-03
Ok then, haha, glad it worked.

Edit:// ah tricky you edited you're post, ok well try right clicking in the area where it has 3 catagories for a list, "Allow Service, Ports, For" see if it lets you add from there

---

### Post by bored2k on 2005-03-03
[QUOTE=JmSchanck]Ok then, haha, glad it worked.[/QUOTE]

dude its working but the add rule option is greyed out...help ??

---

### Post by JmSchanck on 2005-03-03
I think if you click anywhere in those 2 fields there it should "un-grey"

O and make sure you're on "Inbound Traffic Policy"

---

### Post by bored2k on 2005-03-03
[QUOTE=JmSchanck]I think if you click anywhere in those 2 fields there it should "un-grey"

O and make sure you're on "Inbound Traffic Policy"[/QUOTE]


thnx i started juggling and it suddenly ungreyed

it instantly catched a sub7 entry


ill say it again ... i love u

lol

---

### Post by JmSchanck on 2005-03-03
sub7 aye? damn those script kiddies.

---

### Post by danip on 2005-03-04
anybody want to answer my question?

---

### Post by trash on 2005-03-04
danip, have you tried the other connection type settings? 'etho' or 'ppp' in the setup wizard.


[QUOTE=JmSchanck]

Name: BitTorrent
Port: 6881-6889
When Source is: Anyone

:)[/QUOTE]


I can't seem to forward port ranges:(. If I use '6881-6889' i get...

NETFILTER detected
Firewall started
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
Firewall started

it only seems to work if I forward each port individually... is that normal or just how it is for PPC firestarter?

---

### Post by bored2k on 2005-03-04
[QUOTE=trash]
I can't seem to forward port ranges:(. If I use '6881-6889' i get...
NETFILTER detected
Firewall started
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
Firewall started[/QUOTE]

As u can see here, im getting no problems at all with Firestarter; try running the wizard again, and selecting Bittorrent ports from the drop down box .
[[IMG]http://img56.exs.cx/img56/4072/firestarter6ac.th.jpg[/IMG]](http://img56.exs.cx/my.php?loc=img56&image=firestarter6ac.jpg)

---

### Post by trash on 2005-03-04
ok I think the PPC version is just WAY more limited, no drop down box to be found in the setup wizard... I guess we are stuck putting in each single port which really sucked when I was setting up gnomemeeting!

---

### Post by danip on 2005-03-04
[QUOTE=trash]danip, have you tried the other connection type settings? 'etho' or 'ppp' in the setup wizard.





I can't seem to forward port ranges:(. If I use '6881-6889' i get...

NETFILTER detected
Firewall started
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid TCP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.2.9: invalid UDP port/service `6881-6889' specified
Try `iptables -h' or 'iptables --help' for more information.
Firewall started

it only seems to work if I forward each port individually... is that normal or just how it is for PPC firestarter?[/QUOTE]


my choices are ath0, eth0 and sit0 if i choose anything except eth0 the firewall will not start.

---

### Post by trash on 2005-03-04
oh, I do remember reading somewhere either on their website or in the manual that firestarer can't or shouldn't run on a client/routed machine... maybe this is your problem?

---

### Post by bored2k on 2005-03-04
[QUOTE=trash]oh, I do remember reading somewhere either on their website or in the manual that firestarer can't or shouldn't run on a client/routed machine... maybe this is your problem?[/QUOTE]


im running on a routed "machina" ... its working ...

add ports here is simple

policy> clic on the space below allowservice, right clic > add rule > select BT from the drop down...thazzit, 6881-6999 automatixxx

---

### Post by trash on 2005-03-04
i'm going to write to the firestarter peopel and ask em for port ranges in the PPC version... it seems silly why it's not working.

My drop down box has new rule, edit and remove i cannot even specify for BT or GM.

anyway i am still happy it works, newer and beter features will come no doubt:)

---

### Post by trash on 2005-03-04
Just tried ':' instead of '-' and it works!

of course only after I emailed the Firestarter people lol.. oh well, they deserved a big thank you anyway.

---

