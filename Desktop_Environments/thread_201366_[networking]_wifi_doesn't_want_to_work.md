---
title: "[networking] wifi doesn't want to work"
date: 2006-06-21
forum: Desktop Environments
---

### Post by evg on 2006-06-21
Hi all,

i installed dapper drake on an hp laptop, and got some really frustating problems with networking.
I got a simple non-encrypted wifi network at home, and just want to be able to connect to it.

First, i used the Gnome network-admin utility, but sometimes it works, sometimes not... So i was a bit frustrated, and make a small shell script with some ifconfig/iwconfig commands, and that worked all the time... so it's not my WLAN.
Having heard about the 'fantastic' NetworkManager, i decided to tried it... no success, but i learned it was because it only works with DHCP... so i switched to DHCP. Doesn't work again, and then i find that i need to comment out all my interfaces in /etc/network/interfaces... hum, very strange, but ok, i'll give it a chance and did it... ok, this time it worked !!! NM found my WLAN, got a dynamic address, and got connected.
But at the next reboot, and since then... impossible !!!!

Now, NM doesn't work, the Gnome network-admin neither, my script neither, and ifconfig lists eth0 and eth1 even if they are commented out in my /etc/network/interfaces file.

So, here i come to see if someone have an idea and can help me, because i really don't understand how the networking worked on ubuntu...

thanks all.

er:k

oh, on this laptop with breezy, i used whereami to handle multiple network configuration (ethernet and wifi) and it worked well, but i really want to give this GUI tools a chance :)

---

### Post by Paerez on 2006-06-21
I used wifi-radar before network manager, and wifi-radar was very good at networking. I think it is in multiverse or universe. Try that out.

---

