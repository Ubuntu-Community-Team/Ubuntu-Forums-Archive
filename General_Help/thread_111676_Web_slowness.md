---
title: "Web slowness?"
date: 2006-01-02
forum: General Help
---

### Post by radio1 on 2006-01-02
Hi,

I am new to Linux in general and I have a question about web performance.

My Ubuntu box: 768MB and AMD Athlon XP 2800+
My gaming box (Win XP): 2GB and AMD64 3200+

My Ubuntu box takes significantly more time (eg. 15-30 sec vs 5 sec) to load web pages than my WinXP box. I can't believe that it is just a difference in hardware. 

The last time I had a Linux box running I had a Duron 800 w/512 MB (Suse 8.1) get and render pages faster than my Athlon 2800+ w/1GB (WinXP).

Could someone point me in the right direction, maybe /etc/network/interfaces, or some protocol I may have on or off that could explain the difference...?

tia

---

### Post by Zelut on 2006-01-02
I know there are a few tips on speeding up firefox on the [UbuntuGuide]("http://www.ubuntuguide.org/#loadwebsitefasterfirefox") but I don't know if those would give you that much difference..

---

### Post by scaine on 2006-01-02
There's an excellent chance that you have a router which is susceptible to IPV6 which is enabled by default in both Ubuntu and Firefox.

I had the same problem with Mepis, but Ubuntu got round this - perhaps you're the opposite!

Here's the thread to disable IPV6 in Ubuntu (which I found was necessary in Mepis - disabling in Firefox wasn't enough, because even DNS lookups took forever) :
[http://www.ubuntuforums.org/showthread.php?t=87798](http://www.ubuntuforums.org/showthread.php?t=87798)

And here's the Firefox guide for disabling IPV6 :
[http://ubuntuguide.org/#loadwebsitefasterfirefox](http://ubuntuguide.org/#loadwebsitefasterfirefox)

Good luck.

---

### Post by radio1 on 2006-01-02
Thanks k & s,

I know IPV6 is a new/newer protocol, but what makes it slow things down?
I'll take the advice.

thx

---

### Post by Traxis on 2006-01-02
Hey guys. I'm new to Ubuntu and I have the same problem. It happens in Opera as well as Firefox. I've disabled IPv6 in Ubuntu and Firefox, but I still have this problem. Any ideas?

---

### Post by radio1 on 2006-01-02
Hi,

Is not Opera based on the Mozilla engine? There maybe a similar setting...

Anyways, I did try the two changes: /etc/modprobe.d/aliases and Firefox- worked like a charm.

---

### Post by handy on 2006-01-02
Type "about:config" no quotes into the location bar in firefox (don't know about Opera?  Perhaps you can let us know?)

Then type "ipv6" into the "Filter" field.

Double left click on the line that comes up to change it's boolean value to "True"

Open  "/etc/modprobe.d/aliases" in your text editor - sudo gedit - or whatever.

find this line:  alias net-pf-10 ipv6

make it look like this:  #alias net-pf-10 ipv6

(commented out),   save & exit

Forget about ipv6.

Another thing that can slow your internet down is if you have "Static IP Address" selected instead of "DHCP"

Goto -  Menu: System/Administration/Networking  double left click on your ethenet device - usually "eth0".  

Check the "Conection Settings" "Configuration" pull down.  "DHCP" is much faster when changing conections from server to server.

I hope that helps someone?  ;)

handy

---

### Post by s_spiff on 2006-01-03
Had the same problem in firefox and Opera. I installed Firefox 1.5, and the problem seems to have been solved, as for opera, I used to think opera is much better than FF, I think my opinion is about to change. It bloody slow! takes ages just to load any page except google. :(

---

### Post by handy on 2006-01-03
Can you use the "about:config" in Opera?

handy

---

