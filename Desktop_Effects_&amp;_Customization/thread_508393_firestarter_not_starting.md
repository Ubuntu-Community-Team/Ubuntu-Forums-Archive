---
title: "firestarter not starting"
date: 2007-07-24
forum: Desktop Effects &amp; Customization
---

### Post by Balvinder25 on 2007-07-24
hi all,
im just a newbie in the linux world..and ive installed ubuntu 7.04 .>i read somewher tht ubuntu dosent have firewall of its own so we should download one.>i have installed firestarter.>now the probs is tht it dosent start automatically when i start the pc.>i was wondering if someone could show me how to do this..?that would be really great.and i dont like the bib circle icon for the firewall.>isnt there any way we would change this.??just out of curiosity.??any help would be great...

Thanks.
_______

---

### Post by obbe on 2007-07-24
I use firestarter as firewall too and as far as i know even though u don't see its icon on the panel, it starts likewise, bye ;)

---

### Post by Gremlinzzz on 2007-07-24
A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program.
[http://www.fs-security.com/docs/tutorial.php](http://www.fs-security.com/docs/tutorial.php)
:guitar:

---

### Post by musky on 2007-07-25
Gota a coupla feisty's on the go & got firestarter going on the other one. Can't find it on this one :confused:
--------------------------------
ubuntu noob feisty

---

### Post by wnelson on 2007-07-25
Firestarter is automaticly started from the init script in /etc/firestarter/firestarter.sh start. Look in /etc/rc5.d/ you will see S20firestarter this starts iptable at the startup. 

For the GUI to monitor incoming / outgoing traffic under System / Administration / is firestarter.

Walt
Tacoma, WA

---

### Post by ctschap on 2007-07-26
I see the files you mention on my system, but why doesn't Firestarter show up as a service in the Services manager?

---

