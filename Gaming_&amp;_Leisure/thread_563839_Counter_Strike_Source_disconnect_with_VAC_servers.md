---
title: "Counter Strike Source disconnect with VAC servers"
date: 2007-09-30
forum: Gaming &amp; Leisure
---

### Post by mikeym on 2007-09-30
I'm posting this here on the off chance that this is somehow an issue that I'm unaware of with Counter strike itself rather than a wine issue.


The problem is that counter strike source gives an error "Disconnect: client timed out" when connecting to VAC secured servers, but not non-secured servers.

I don't believe that it's a network issue because I have disabled my firewall and port-scanned myself to check that it worked. I have also tried setting the cl_timeout option in counter strike to a ridiculously large number but it didn't help (it did let it load till you could see the select team menu - with no options - but it still timed out).

---

### Post by Aesir09 on 2007-09-30
steam had a big update a lil bit ago, do you have the latest client with the new overlay feature?

thats the only thing i could think of:lolflag:

---

### Post by frodon on 2007-10-01
Got the same issue and solved it, i asked valve to update their documentation but all i got is a wall in front of me, so you can thanks valve for not updating its documentation despites user feedback.
Basically when i got the problem i met some other users with the same issue and we found out that steam is now using UDP ports after 27015 so all the users who have a firewall or a router which only allow UDP ports from 27000 to 27015 like the official documentation recommend it may have the problem.
The solution is simple, just allow UDP ports from 27000 to 27020, it fully solved my issue.

Hope it helped you though i'm not sure seing that you tried without your firewall enabled.

Official valve page for this issue there :
[http://support.steampowered.com/cgi-bin/steampowered.cfg/php/enduser/std_adp.php?p_faqid=374&p_created=1114462836&p_sid=6U8Q54Ni&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQyJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXBvcnRzIHN0ZWFt&p_li=&p_topview=1](http://support.steampowered.com/cgi-bin/steampowered.cfg/php/enduser/std_adp.php?p_faqid=374&p_created=1114462836&p_sid=6U8Q54Ni&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NDQyJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXBvcnRzIHN0ZWFt&p_li=&p_topview=1)

---

### Post by mikeym on 2007-10-01
I am running the latest version of Wine but I have tried 0.9.46-CVS, 0.9.46, 0.9.45-CVS, 0.9.45, 0.9.43, and 0.9.40 all with the same error. 

The only way I can see that it could be a networking issue is if my supplier (UK Virgin - Ex-NTL) was blocking my ports. Is there some way to scan my UDP ports? And how could I set up port forwarding to make sure that my supplier couldn't block me?

Here is a screenshot of my router's NAT screen:

[[IMG]http://img458.imageshack.us/img458/3347/screenshotss6.th.png[/IMG]](http://img458.imageshack.us/my.php?image=screenshotss6.png)

---

### Post by mikeym on 2007-10-01
Port Scan under network tools doesn't show any of those ports open when running Counter Strike source???

In fact it doesn't show any new ports opening for it?

---

### Post by mikeym on 2007-10-01
Active Network services in network tools does show them but with IP 0.0.0.0

---

### Post by mikeym on 2007-10-01
The port showing up as 0.0.0.0 seems to be normal for active ports as I have checked *tcp* ports with this and they are open. The reason that no new ports appeard may be that there were no *tcp* ports being opened by CSS only *udp*. So I can't detect them using a normal internet port scan either.

So,

[LIST]
[*]Is it normal for Steam/VAC/CSS to only request UDP ports?
[*]Can I scan my computer for open UDP ports somehow (like an internet scan)?
[*]How would I set up port forwarding on my router (see thumbnail above) to avoid potential service provider issues?
[/LIST]

Thanks :)

---

### Post by mikeym on 2007-10-01
Oh! That is so (and I'm sorry if I offend) bloody rubbish!

This was the problem:

Instead of launching the game from Steam or with:

wine Steam.exe -applaunch 240

I was launching the game with:

wine hl2.exe -game cstrike -steamlocal

I was doing this so that I could put a wrapper script round hl2.exe and set the graphics modes before and after. :(

I cannot believe it would discriminate just on the ground of how you launched it! Nevermind giving you such a useless error message!

I am deeply unimpressed with valve with this one (yet chuffed at getting it to work).

---

