---
title: "lightdm and isc-dhcp-client problem"
date: 2015-07-04
forum: Desktop Environments
---

### Post by hydrochronik_90 on 2015-07-04
Hello,

I have 300 computers on running on 14.04 64bits Ubuntu, i use isc-dhcp-client to get ip and name from my dhcp server.

 I encounter the classic problem with lightdm "your system is running in low-graphics mode" at startup, but it's not a driver problem, it's very strange and i spend a lot of time to try to fix that :

1) if my computers are not connected on network, i don't encounter the problem, lightdm starts.

2) if my computer are configured with statics adresses and connected, i don't encounter the problem, lightdm starts.

3) if my computer are configured with dchp client and connected to a 1Gb network i don't encounter the problem, lightdm starts.

The pb happened when for a reason or an other (switch, wire etc ...) the computer are connected on a 100Mb network. It seems that isc-dhcp-client take more time to get the address and lightdm (i don't understand why) display the low graphic message. 

When I get the message if i switch to a new tty, after a while, i see the computer get the name and the address, so i can't do /etc/init.d/lightdm restart and everything is fine. 

Or another way to fix the problem, accelerate isc-dhcp-client, tell lightdm to launch after isc-dhcp-client got the ip parameters etc...

Is anyone have never encounter the problem?

Thanx

---

### Post by dino99 on 2015-07-04
hello,
you should directly ask devs for help on Askubuntu, copying/pasting the above explanations, to know if there is some hidden limitation settings you need to tweak; or if lightdm have to be blamed (maybe test with gdm instead of lightdm, or other xdm,...)

i suppose your logs does not help you digging more; which DE is used ? (unity, gnome-shell, ...)
you then probably needs to open a bug report against lightdm, isc-dhcp-client (maybe install the -dbg package to get more details)
[https://www.isc.org/support/](https://www.isc.org/support/)

---

### Post by hydrochronik_90 on 2015-07-04
Hello,

I've tried gdm and i have the same pb. Users can choose betwen 3 DE, unity, gnome-shell and gnome classic. Before installing the 14.04 we used 12.04 and we also had problems with computer connected to 100Mb network, to get dhcp configuration, it was slower than those connected on 1Gb network, and impact user authentication. but that did not impact lightdm.

As you said The logs did not help me.

Thanx for the advices, i'll post on the dev forum, but keep this one open...

---

