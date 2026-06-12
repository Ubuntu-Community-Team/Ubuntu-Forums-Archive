---
title: "Trouble Getting to Internet Through Win2000 Network w./ Gateway"
date: 2006-01-03
forum: General Help
---

### Post by kenquad on 2006-01-03
Hi:

I'm a new Linux user (just migrating from "Win-doze" 2000) but I can't figure out how to get on the Internet from my terminal at work, where we have a Windows network.  I can get on the LAN, but when I try to specify the DNS server IP address in Kcontrol, the system says: "You must first type an alias".  Huh?  I'm running a Dell Optiplex with a 1.2 processor, about 256 MB of RAM, and onboard LAN with Kubuntu Breezy fresh installed.  (BTW, I'm having to type this from my old Windows box.  Aaaagh!)  I'd appreciate any help anyone can offer.  Thanks.

Kenquad

---

### Post by N6546R on 2006-01-03
Does your network use DHCP to automatically configure network settings? If it does, a quick 'sudo dhclient eth0' should put things right. Substitute your own interface for eth0.

If it doesn't, you should be able to ignore the warning in kcontrol. As a check, look at /etc/resolv.conf to see if the DNS server you added was appended to the list of resolvers.

Perry

---

### Post by kenquad on 2006-01-03
We don't use DHCP and I've tried ignoring the kcontrol warning but with no results.  Possibly I was using the wrong IP address at the time.  I'll try it again.  Thanks.  I'll post again with results.

---

### Post by kenquad on 2006-01-04
Maybe DNS isn't the problem.  I tried ignoring the error on my "live" system, again with no results.  I can browse the network and make changes, but I can't get on the Web.  One odd thing: When I input the IP address of the gateway, the machine appears to accept it--then as soon as I apply the changes and leave the applet, it disappears.  Anyone encountered this?

---

### Post by GeneralZod on 2006-01-04
[QUOTE=kenquad] One odd thing: When I input the IP address of the gateway, the machine appears to accept it--then as soon as I apply the changes and leave the applet, it disappears.  Anyone encountered this?[/QUOTE]

Yep - [http://bugzilla.ubuntu.com/show_bug.cgi?id=9871](http://bugzilla.ubuntu.com/show_bug.cgi?id=9871)

Best to make the changes directly in your /etc/network/interfaces

He's a portion of mine to use as a sample - this is for a wireless card, though, so the "gateway" line and its position in the file will probably be the only things you'll want to take from it.  

```

# The primary network interface
iface eth0 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid MYSESSID
        address 192.168.1.110
        netmask 255.255.255.0
        gateway 192.168.1.1

```

When you've edited it to your liking, do

```

sudo /etc/init.d/networking restart

```

to try it out!

---

### Post by kenquad on 2006-01-04
People, I'm happy to say I'm typing this from my brand-new KUBUNTU BREEZY system!  Editing the interfaces file did the trick, though I had to restart the box instead of just reloading the network.  Thanks so much for the help, all! If it weren't for this forum, I probably would have had to go back to the OS that starts with W.  Speaking of which, is someone working to correct that bug with the control panel Network applet?  It would be enough to stonewall anybody who hadn't encountered it. 

Thanks again!

---

### Post by GeneralZod on 2006-01-04
[QUOTE=kenquad] Speaking of which, is someone working to correct that bug with the control panel Network applet?  It would be enough to stonewall anybody who hadn't encountered it. 

Thanks again![/QUOTE]

Glad you got it all working! :) 

jriddel stated in the linked report that it has been fixed in the Dapper development release, but I don't know if it the fix will be backported for Breezy.

---

