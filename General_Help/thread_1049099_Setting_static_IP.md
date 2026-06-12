---
title: "Setting static IP"
date: 2009-01-24
forum: General Help
---

### Post by YigalB on 2009-01-24
It seems that the interface for changing IP was changed lately.
Now I cant set static IP any more. Whenever I enter the system-preferences-networg configuration, I go to wired tab, select auto eth0, press edit, IPv4 settings.
Then I set the method to manually and set the IP: 
192.168.2.109
255.255.255.0 (in the past - this field was automatically filled for me)
192.168.2.1

This didn't change the IP, including after restart.
The information I set before always go back to auto-DHCP.

What am I doing wrong?

---

### Post by StOoZ on 2009-01-24
Edit the file

[PHP]/etc/network/interfaces [/PHP]

and adjust it to your needs (in this example setup I will use the IP address 192.168.0.100):

[PHP]# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1[/PHP]

P.S : the mapping thing is optional , I guess.

---

### Post by Iowan on 2009-01-24
You didn't mention which version, but [this]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") How-To might be helpful.

---

### Post by YigalB on 2009-01-25
I gave up. Ubuntu is not mature enough to allow simple usage of home networking.
I certainly not going to edit system files manually - this is very unsafe method.

Lucky for me, I told the router to set static IP for this specifically network ID. So Ubuntu is asking the DHCP for an automatic IP, while the router assigned pre-defigned IP.

So it works, but my sad conclusion is that Ubuntu is not mature enough to be used by "regular people". Not yet.

Thanks for the help!

---

### Post by Chris Musampa on 2009-01-25
One of the first things I do on a fresh ubuntu is install WICD, miles better than network manager as it is rock solid with wireless connections and has no problems with static IPs.  In my near infinite experience with linux - almost a whole year :lolflag: - I've found NM to be a disaster.

---

### Post by HereInOz on 2009-01-25
YigalB, I have to say that "regular people" generally don't set static IP addresses.  "Regular People" don't have a clue as to what a static IP address is and why they would use it.  

I, too, was a tad cheesed off that the the Network Manager would no longer accept a static IP assignment, but the file which was mentioned (/etc/network/interfaces) is not really a "system" file, it is a configuration file, much like the "hosts" file in both Windows and Linux.

The remedy is to uninstall the Network Manager, and simply edit the interfaces file as described above.  Just follow good process and copy the file to make an interfaces_orig file or something like that, so that if you completely mess it up, you can rename the copied file and you are back to square one.

Ubuntu is a system which "just works" and for "regular people" that means DHCP.  "Simple usage of home networking" generally means DHCP.  "Technical People" set static IP addresses.

---

### Post by YigalB on 2009-01-25
I agree that most people donwt know what statis IP is.
But still, the network manager is buggy.
If you add that i try to fight my NVIDIA FX5200 to give me better resolution than 640*400, you find out that the Ubuntu doest work "as is".
if it had - I wouldn't be here asking these questions, right?

I like Ubuntu. i try spreading the word around, but we must admit - it's still not there.

And NO - editing files is something user never do.

Thank you
Yigal

---

