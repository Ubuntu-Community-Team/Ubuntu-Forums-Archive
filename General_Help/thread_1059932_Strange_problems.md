---
title: "Strange problems"
date: 2009-02-04
forum: General Help
---

### Post by FearlessPc on 2009-02-04
Hi

After a long time of using the combination of Firestarter+IPBlock+rTorrent I'm having strange problems in the past week.

Long story short:
Firestarter & IPBlock loads on boot.
when i start rTorrent:
1) The download is very slow 15~20k (on dsl).
2) Ping localhost 100% loss.
3) Checkgmail don't work (broken envelope icon).
4) Firestarter don't work (not responding).
5) Ncmpc can't connect to MPD
When i restart Firestarter all the above start working normally, but IPBlock stop working.
Restarting IPBlock makes everything works until the next run of rTorrent.

*I didn't do any changes to the config files of this programes before the problems began (at least not intentionally).
*Browsing with FireFox was effected only one time (unable to connect to sites), updating IPBlock lists solved it.

Things i tried (from google search):
Check hosts file -> everything is Ok
Run "ifconfig" to see if Loopback is there -> he is
Run "sudo iptables -L" to see if Firestarter settings still there -> and they are
Manual IPBlock update (its on auto) -> no effect
Manual system update -> no effect
I tried to look in /var/log/* for somthing about Firestarter -> there was nothing weird (or i didn't look at the right place)
Check if Firestarter block pings -> its not

Specs:
Hardy + openbox + gnome
rTorrent 0.8.0/.0.12.0
"iptables -L" is all my knowleg in iptables
I know Firestarter GUI dont have to be runing for it to work, but this is how i fond it's heving problems
My english is not perfect

Thanks


----Update----

I installed the new version of IPList
also i found this in [Iplist FAQ]("http://iplist.sourceforge.net/faq.html")
> Does IPblock work with other firewall applications ?
Yes. But IPblock needs to be started after other firewall applications. 
so i learned from [here]("http://ubuntuforums.org/showthread.php?t=711067") about setting the order of boot services.
I can find ipblock in /etc/rc2.d (runlevel told me I'm on N 2) but firestarter isn't there,
i ran "locate firestarter" and found it in:
/etc/network/if-down.d/50firestarter
/etc/network/if-up.d/50firestarter
/etc/ppp/ip-down.d/50firestarter
/etc/ppp/ip-up.d/1firestarter
/etc/ppp/ip-up.d/50firestarter
/etc/rcS.d/S65firestarter

Is this normal or i need to add it to rc2.d or just run update-rc.d with defaults ?

----Update 2----

I checked with "dpkg -L firestarter" and this is how firestarter was installed,
and also all the links of ipblock in /etc/rc*.d are with the value of S99 so thay the last to load anyway...

That's the end of my Linux wisdom, i don't know what to do next.

(This is getting too long #-o)

---

### Post by FearlessPc on 2009-02-11
Solved, see [this thread.]("http://ubuntuforums.org/showthread.php?p=6783910#post6783910")

---

