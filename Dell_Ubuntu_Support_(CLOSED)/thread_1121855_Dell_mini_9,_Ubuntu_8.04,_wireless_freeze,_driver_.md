---
title: "Dell mini 9, Ubuntu 8.04, wireless freeze, driver update problem"
date: 2009-04-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Bonneville44 on 2009-04-10
I recently received my Dell Mini 9 with Ubuntu 8.04 Hardy.

The wireless freezes when connecting to my home network causing need for hard reboot.  It does fine connecting to other networks without password protection.  

I went to Broadcom's site to get an updated driver (wl.ko) to replace current driver (wl).  I thought I needed the 32 bit driver, but I could be wrong as I can't seem to make a Linux Loadable Kernel Module with their instructions (4,5).
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

After i enter the command (make -C /lib/modules/2.6.24-19-lpia/build M='pwd')(i am using the correct backwrds straight lines around pwd on the dell mini that I don't see on this keyboard so that isn't a mistake here) it says "No such file or directory.  Stop."  I am cd'ed to the directory that contains the makefile (hybrid_wl).  I don't know what else to do!


Any help?

---

### Post by Bonneville44 on 2009-04-10
"N and Z series Atom models cannot run x86-64 code"

ok so I have the right choice in 32 bit given the n270 couldn't handle the driver for x86-64.  Still doesn't explian why my terminal won't take the commands.

---

### Post by buzzware on 2009-04-10
I had the same issue when I got my Mini back in December.  It was fixed by one of the updates in Jan or Feb.  You might try that before spending too much time on a more complex fix.

I'm trying 9.04 right now, but wireless connects flawlessly when I boot 8.04.

---

### Post by akc42 on 2009-04-11
I have a brand new mini 12, and I have the same freeze.  I wondered if it was a graphics problem rather than the wireless - it seems to be when negotiating keys or something, and that could take a large amount of the CPU time.

---

### Post by armandh on 2009-04-11
a little applied logic

OP only has trouble with home wireless or secure wireless
other open wireless work without problems.

OP needs to try it at a friends secure wireless.

there is a post somewhere about blocking ch 11,12 at the wireless router or hub. 
[because newer equ. like mini9 doesn't go there.]

if still a problem only at home try wpa-2 security which seems to work best

---

### Post by akc42 on 2009-04-11
> **armandh said:**
> a little applied logic
if still a problem only at home try wpa-2 security which seems to work best

I just swapped over to this, to see what happens.

I just noticed that there are separate kernel modules (see /etc/modules) for tkip encryption (there is ieee80211_crypt and ieee80211_crypt_tkip).  Could it be the latter is the one with the bug in it?

---

### Post by buzzware on 2009-04-11
> **akc42 said:**
> I just swapped over to this, to see what happens.

I just noticed that there are separate kernel modules (see /etc/modules) for tkip encryption (there is ieee80211_crypt and ieee80211_crypt_tkip).  Could it be the latter is the one with the bug in it?

I can tell you that, for me, only TKIP will work with WPA2.  My router will accept TKIP or AES.  When I set the Mini to either Auto or AES, I can't connect.  When I set it to TKIP, it connects every time.

---

### Post by Bonneville44 on 2009-04-13
> **buzzware said:**
> I had the same issue when I got my Mini back in December.  It was fixed by one of the updates in Jan or Feb.  You might try that before spending too much time on a more complex fix.

I'm trying 9.04 right now, but wireless connects flawlessly when I boot 8.04.


Is that 8.04.2?  My system manager says i'm at 8.04, Dell says it shipped with 8.04.1

Do I download the 8.04.2 update through canonical?  i think that is the one that came through in January/ February.

The broadcom patch released in march/april by itself is still giving me fits even though I follow their dang directions exactly.

---

### Post by snowpine on 2009-04-13
> **Bonneville44 said:**
> Is that 8.04.2?  My system manager says i'm at 8.04, Dell says it shipped with 8.04.1

Do I download the 8.04.2 update through canonical?  i think that is the one that came through in January/ February.

The broadcom patch released in march/april by itself is still giving me fits even though I follow their dang directions exactly.

8.04 = Ubuntu Hardy Heron
8.04.x = Ubuntu Hardy Heron plus updates and bug fixes. Think of the 'x' as a 'snapshot' of a freshly updated 8.04 system at a particular point in time. 

In other words, as long as you regularly update your system (through the update manager or command line), you will always be up to date with 8.04.2 (or 8.04.3, 8.04.4 etc.).

ps The Dell version of Ubuntu is not interchangeable with the regular version of Ubuntu. I believe Dell Mini 9 wireless does not work out-of-the-box with regular Ubuntu 8.04. It should work using an up to date Dell Ubuntu 8.04.

---

### Post by anjilslaire on 2009-04-13
I'm running i386 8.10 Intrepid on mine, and I had to switch to WPA2 AES to connect to my wireless router.

For what thats worth.

---

### Post by buzzware on 2009-04-13
> **anjilslaire said:**
> I'm running i386 8.10 Intrepid on mine, and I had to switch to WPA2 AES to connect to my wireless router.

For what thats worth.

So maybe it's more the auto setting that it doesn't like.  *shrug*

BTW, I have an updated Dell Hardy install (OEM).

---

### Post by Bonneville44 on 2009-04-16
Updated and updated like this littel thing had never been updated before.  it FINALLY finished and the STA driver seems to be working (and my kernel changed form like 24-19 to 24-22 along the way)

We're in business now and all seems great!

Thanks for your suggestions!

---

