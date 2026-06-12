---
title: "No network after kernel upgrade"
date: 2009-04-07
forum: General Help
---

### Post by rafemonkey on 2009-04-07
I just took the recent kernel upgrade (4/7/09) in 8.10 and after a reboot, I had no network. I assume there is no problem with my local network or gateway, since all my other computers can still connect.

I have tried recreating the connection in the "Network configuration" tool. ifconfig reports eth0, but ifdown says eth0 not configured and ifup says "Ignoring unknown interface eth0=eth0". Finally, attempting to ping out results in "ping: sendmsg: Operation not permitted". 

At first, I thought this might be a permissions issue, but I cannot connect to the machine from the outside either. (ping, http, etc...)

Also of note, after reboot, the default Gnome GDM splash had replaced the usual human screen.

Thoughts?

TIA!

---

### Post by rafemonkey on 2009-04-07
I just checked to see if the firewall had gotten turned on, but, as far as I can tell it's off... (iptables is not loaded, and service --status-all shows firewall off)

---

### Post by rafemonkey on 2009-04-07
Ok... I have a workaround Looks like ipmasq is starting before eth0 is up causing bad rules to be generated. In the short term running /etc/init.d/ipmasq restart fixes my networking. Now I just need to figure out how to delay ipmasq...

(see: [http://jonmccune.wordpress.com/2008/11/11/ping-sendmsg-operation-not-permitted/]("http://jonmccune.wordpress.com/2008/11/11/ping-sendmsg-operation-not-permitted/") )

---

### Post by michcook on 2009-04-10
I have just found the same problem after patches had been applied.

As an aside, I also suffered (Xubuntu) from a second problem where my users & groups (passwd file) were completely screwed up with empty files.
([https://bugs.launchpad.net/ubuntu/+source/liboobs/+bug/240437](https://bugs.launchpad.net/ubuntu/+source/liboobs/+bug/240437))

I've not found a solution to the ipmasq problem other than restarting it once I've manually configured the two eth0 and eth1 interfaces.  

<rant>
The network manager is a random piece of crap which completely screws up even basically connectivity on my computer.)  This was not a problem it was just buggy... until the most recent set of (kernel) patches in the last two weeks which completely toasted network connectivity.
</rant>

---

### Post by Wolfhere on 2009-04-10
I completely agree. After reading your post, I found the solution at:
[http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/]("http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/"). I no longer have the cool network icon in the panel, but I no longer get the fail on reading the interfaces error during boot up and get wired connectivity every boot. 
I am on an AMD64 8.10 2.6.27.12-15. I am not exactly sure when the issue occurred, obviously fairly recently. And like you above, I was having intermittent problems until the latest update. I was having to periodically fix the /etc/network/interfaces file for static assignment. The  fix mentioned above certainly works for me. I might miss the cool little gui in the panel for managing the network....but obviously it was not playing nicely with network-manager-gnome. I removed both during the process...but used the synaptic manager to remove rather than the manual (which did not want to work for me anyway).
Thanks for all the help here, this is the best place for help on Ubuntu

---

### Post by rafemonkey on 2009-04-10
> **Wolfhere said:**
> I completely agree. After reading your post, I found the solution at:
[http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/]("http://www.nalinmakar.com/2008/11/08/static-ip-address-on-ubuntu-810/"). I no longer have the cool network icon in the panel, but I no longer get the fail on reading the interfaces error during boot up and get wired connectivity every boot. 
I am on an AMD64 8.10 2.6.27.12-15. I am not exactly sure when the issue occurred, obviously fairly recently. And like you above, I was having intermittent problems until the latest update. I was having to periodically fix the /etc/network/interfaces file for static assignment. The  fix mentioned above certainly works for me. I might miss the cool little gui in the panel for managing the network....but obviously it was not playing nicely with network-manager-gnome. I removed both during the process...but used the synaptic manager to remove rather than the manual (which did not want to work for me anyway).
Thanks for all the help here, this is the best place for help on Ubuntu

Did you try [wicd]("http://wicd.sourceforge.net/")? it looks pretty slick...

---

