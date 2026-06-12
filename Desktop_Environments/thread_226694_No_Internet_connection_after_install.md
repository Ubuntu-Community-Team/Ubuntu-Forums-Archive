---
title: "No Internet connection after install"
date: 2006-07-31
forum: Desktop Environments
---

### Post by geovino on 2006-07-31
I just installed ver. 6.06 and everything went fine... except I can't connect to the internet like I could using the live cd. I have dsl. What can I do? I can only go to the ubuntu documentation but no other sites. Any clues?

---

### Post by Titus A Duxass on 2006-07-31
We need more information:

Card type?
Wireless or hardwired?

Output from:

ifconfig
iwconfig

---

### Post by geovino on 2006-07-31
Card type - D-Link DFE-530TX+

Wireless or hardwired? - hardwired

Output from: What do you mean by that?

ifconfig - Link encap:Ethernet HWaddr 00:50:BA:61:02:E4
inet address: 192.168.0.6 Bcast 192.168.0.255  .... what do you need out of all the verbiage?

iwconfig - no wireless connections

I can't copy and paste to my other PC. is that enough? Thanks

Note: I was able to download all the updates, so the dsl connection is working, maybe its Firefox that's not working properly.  Any more clues?

---

### Post by geovino on 2006-07-31
I can get around Ubuntu sites, but nothing else. I had this happen to me with Firefox before and I had to go to about: someting and then turn a network setting to on or off. Do you have any idea what that might be?

---

### Post by geovino on 2006-07-31
I figured out the problem with Firefox.

In the address bar type:  about:config

A long list of items will come up and scroll down to:
network.dns.disableIPv6 
if it's set to false > toggle to true

That fixed my problem! :smile:

---

### Post by gwenbasil on 2006-08-05
Snazz, that worked for me, too. :D

---

