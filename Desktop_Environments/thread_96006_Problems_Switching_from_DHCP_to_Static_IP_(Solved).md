---
title: "Problems Switching from DHCP to Static IP (Solved)"
date: 2005-11-27
forum: Desktop Environments
---

### Post by VTHokie on 2005-11-27
Hey everyone,
I have a dual boot Windows XP and Ubuntu machine which I set up over the Thanksgiving break and while at home I used DHCP.  The problem is when I got back to campus I use a static IP and I tried to go through System>Admin>Networking and changed over the setting to my static IP, netmask, and gateway over to 192.168.1.3, 255.255.255.0, and 192.168.1.1 respectively.  However when I try to connect to any website, firefox just seems to hang for a while and doesn't do anything which seems awfully strange.  Can anyone please give my some sugestions as to what I might be doing wrong?  Thanks in advance.

VTHokie

---

### Post by Lambert on 2005-11-27
When you're at school try this

ping 216.239.57.99

Should get someout put like this
64 bytes from 216.239.57.99: icmp_seq=1 ttl=235 time=89.9 ms
64 bytes from 216.239.57.99: icmp_seq=2 ttl=235 time=96.3 ms
64 bytes from 216.239.57.99: icmp_seq=3 ttl=235 time=88.6 ms
64 bytes from 216.239.57.99: icmp_seq=4 ttl=235 time=90.2 ms

You can hit ctrl+c to cancel after a few lines.

If that works then try this

ping [www.google.com](www.google.com)

If that doesn't then it's a dns problem.

---

### Post by VTHokie on 2005-11-27
Thanks for your quick reply Lambert :D 

Okay, I went and pinged 216.239.57.99 and google respectively and pinging the former looked very similar to what you said it should look like but when I pinged the latter the packet information that came in stalled in spurts than sped up again constantly and the information at the end after I hit ctrl+c said there was a 10% packet loss.  Strangely I entered 216.239.57.99 it brought up google in firefox and I could actually use the search engine and I could ironically bring up ubuntu forms but I couldn't seem to bring up anything else such as yahoo or reuters still.  I must have done something really strange but I don't know what? :confused: 

VTHokie

---

### Post by greenway on 2005-11-27
Like Lambart told you, it's most probably a DNS problem. Go to System>Administration>Networking and check if you have any servers listed under the DNS tab, if not enter the right DNS servers here manually.

It also might be that the DNS servers provided by your DHCP server at home are still listed there (this has happened to me several times in the past).

---

### Post by VTHokie on 2005-11-28
Thanks Lambert and Greenway! ;) 

Okay, I solved the problem I went to DNS as you mentioned and although the DNS info was correct I noticed beneath it under Search Domains vz.dsl.genuity.net and since vz is Verizon which is our service provider at home I guess Ubuntu was looking for it but couldn't reach it and that was causing the problem just like both of you said .  As soon as I removed it, everything worked flawlessly.  Thanks again, although I feel kind of stupid because I should have noticed that earlier. :(

VTHokie

---

### Post by greenway on 2005-11-28
If you only knew how many hours I spend on itty bitty stuff like this! Anyway, glad you solved the issue.

---

