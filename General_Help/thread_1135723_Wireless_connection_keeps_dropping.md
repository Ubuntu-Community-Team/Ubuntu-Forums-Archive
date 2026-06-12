---
title: "Wireless connection keeps dropping"
date: 2009-04-24
forum: General Help
---

### Post by Daryl7352 on 2009-04-24
[]

---

### Post by jamessnell on 2009-04-24
I haven't yet updated my Laptop setup to 9.04, but I have the BCM4311 too. It seems to be poorly supported in 8.10... So your post makes me nervous to upgrade.

However, Broadcom does provide their own driver that you can go download and install.. They have some instructions somewhere on their site.. Maybe give that a try.. My experience with that on 8.10 was about the same as the stock setup, for all I know it's actually identical, but I don't know that for a fact.

There's also the uber-lame ndiswrapper option.

---

### Post by anandamide on 2009-04-26
I'm having exactly the same problem, again with Broadcom. Connection will drop then re-establish after 2-3 seconds. Makes listening to radio impossible.

Will try the driver on the BC site and get back to you.

---

### Post by telmac on 2009-04-26
I was never able to get the wireless driver, and ended up using an old wireless card, but the problem that I am having now is that the wireless system that my brother set up uses a wpa password, and my computer only recognises a "WEP 40/128 bit passphrase" or "WEP 128 bit passphrase" or "LEAP" or "Dinamic WEAP".maybe "Dinamic WEP".

---

### Post by anandamide on 2009-04-26
I *think* I've installed the other driver (first time I've manually installed one so I don't actually know...); no difference.

Of course, I might have failed to change my system in any way, in which case the lack of difference is less surprising.

I have lasagne tho, so all is not lost.

---

### Post by kocis on 2009-04-26
I upgraded to 9.04 on my Thinkpad T42.  It has an Intel wireless and dropped the connection a couple of times.  I restarted and deleted the automatic connection.  I setup the connection again and so far it seems to be holding.

---

### Post by Daryl7352 on 2009-04-26
[]

---

### Post by Daryl7352 on 2009-04-26
[]

---

### Post by anandamide on 2009-04-26
> **Daryl7352 said:**
> It would appear as if the problem persists.

Sadness.

Also, I have no more lasagne.

But according to conky I do have a Vandalism remix of CeCe Peniston's 'Finally' playing, so all is not lost.

This does not bring me streaming radio, however.

Swings and roundabouts, innit?

---

### Post by detroit/zero on 2009-04-26
My Wife's Acer laptop (with the same wireless card) had the same problem. Drivers didn't help. The solution that worked was getting rid of nm-applet and network-manager, and installing the wicd network manager.```
sudo apt-get install wicd
```It auto-terminated and auto-removed both the other packages when it installed. Then simply press alt+f2 and enter```
wicd-client
```at the prompt to start the manager. You'll have to re-enter the keys and stuff for the networks you use, but she hasn't had a dropped connection since she started using it. Wicd also offers greater flexibility and more connection options than the default nm-applet does.

---

### Post by Daryl7352 on 2009-04-26
[]

---

### Post by anandamide on 2009-04-26
Brilliant - have been up half an hour with no interruptions, all looks good - thanks so much Detroit!

Now I have an uninterrupted signal *and* streaming audio! Effusive joy!

---

### Post by Daryl7352 on 2009-04-26
[]

---

### Post by riberet on 2009-05-09
Thanks bro for the wicd solution.
Works like a charm. It gets a bit confusing when you're trying to use a PEAP WPA2 type network. But it's preety simple. had to set the encryption to PEAP-GTC rather than PEAP-TKIP(which the university suggests).

---

### Post by ruegsegs on 2009-05-13
I have this same issue.  When I upgraded my T42 Thinkpad from Intrepid to Jaunty my wireless connection (both @ home w/ WEP and work w/ LEAP) got flaky and kept disconnecting.   I have installed WICD, but cannot figure out the setup/configuration.  

How does one figure out the configuration for WICD?  

In particular, the WPA Supplicant Driver.
Thanks
Steve

==============================
3 hr update:

I figured it out.  I went back to the default WPA Supplicant Driver (wext) and tried a different WEP encryption.  I was pretty convinced that WEP (Shared/Restricted) was correct, but it was not.  WEP (Hex) was the right answer.  So, now I'm finally up and running wireless in Jaunty with WICD.

---

### Post by Holden99ca on 2009-05-14
Really good tip. Same problem with my acer aspire one. Seems to have solved it. Thanks!

---

### Post by rakmoh on 2010-02-04
Thanks for posting the solution. This (installing wicd network manager)  fixed the issue for me on Dell Vostro 1520.

-Rakesh

---

### Post by charmedguy18 on 2010-02-04
> **detroit/zero said:**
> My Wife's Acer laptop (with the same wireless card) had the same problem. Drivers didn't help. The solution that worked was getting rid of nm-applet and network-manager, and installing the wicd network manager.```
sudo apt-get install wicd
```It auto-terminated and auto-removed both the other packages when it installed. Then simply press alt+f2 and enter```
wicd-client
```at the prompt to start the manager. You'll have to re-enter the keys and stuff for the networks you use, but she hasn't had a dropped connection since she started using it. Wicd also offers greater flexibility and more connection options than the default nm-applet does.
Perfect! Thank you so much. This works on my MacBook Pro 5,1 (Broadcom STA), which was dropping its already weak signal with no cause whatsoever.

---

