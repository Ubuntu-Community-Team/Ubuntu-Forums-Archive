---
title: "My friend needs to get his dial-up running."
date: 2006-01-10
forum: Desktop Environments
---

### Post by UltraSonicSite on 2006-01-10
edit

---

### Post by healychan on 2006-01-10
Please provide more information, such as "ifconfig", "route -n".
Nobody can help without the details of the system...........
Because different people have a different stroy, there are no standard solution.

There should be a thread somewhere in the forum saying that "Provide enough information will have a better chance to get help". This is really true.

---

### Post by UltraSonicSite on 2006-01-10
I see, well sorry, that might not be in order due to the fact that I dunno where he lives and cant go to him to helo him myself. Sorry man...

---

### Post by Dark Damo on 2006-01-11
ppp-config 

Or pppconfig. 

Either one i am not sure. Thats what i did when i had dialup. I dont think it works with internal modems though.

---

### Post by leech on 2006-01-11
Dial up should be fairly easy (assuming his modem is supported).

Open up System -> Administration -> Networking.

After typing in the password, you'll see Modem Connection.  The rest should be pretty self explanitory.

Leech

---

### Post by L Campbell on 2006-01-11
[QUOTE=leech]Dial up should be fairly easy (assuming his modem is supported).

Open up System -> Administration -> Networking.

After typing in the password, you'll see Modem Connection.  The rest should be pretty self explanitory.

Leech[/QUOTE]
......................

WOW!!!!!

I'm sorry but I had to laugh when I read your post.  (No disrespect intended)

You know, what you say is ABSOLUTELY correct, IMHO but it is not the fact of the matter.

Dial up modems are Linux's 'dirty little secret'.  I have been trying for almost 3 months to get my Ubuntu 5.10 to connect and I have had a lot of help from several good people, including linmodems.org but, so far, NOTHING has worked.

I _know_ that the modem can connect with Linux because my Mepis works perfectly and setting it up was a slam dunk.

Eventually I'll get there and then I'll have a method that I can share with anyone who is interested but the bottom line at this point is that trying to connect with a dial up through Ubuntu is close to impossible for a lot of people.

Kind regards.

---

### Post by GeneralZod on 2006-01-11
[QUOTE=L Campbell]
Dial up modems are Linux's 'dirty little secret'.  I have been trying for almost 3 months to get my Ubuntu 5.10 to connect and I have had a lot of help from several good people, including linmodems.org but, so far, NOTHING has worked.
[/QUOTE]

Well, I'm not so sure that is is secret, but it's certainly dirty :)

To be quite honest, modems are no different from any other piece of hardware; get something that is well-supported by Linux (which does not include winmodems, as we are at the mercy of a proprietary third-party driver provider, and cannot include the drivers in the default install nor do much to improve them) and life will be easy; get something that's not, and you're in a world of hurt :)

For the record, I bought a PCMCIA modem from eBay for &#163;10 inc p&p (a xircom one) which "just works" with my laptop and any distro - the drivers are part of the stock kernel, and all you need to know is the /dev/ entry where the modem is located and your ISPs phone number, username and password and that's it! I seem to recall that I once used an external serial modem with Linux and that worked similarly effortlessly - no drivers or configuration required.  The /dev/ entry will show up in dmesg when you plug the PCMCIA modem in.

So if you value your time (and hair!) more than your bank-balance, I'd advise going with one of these :)

---

### Post by L Campbell on 2006-01-11
[QUOTE=GeneralZod]Well, I'm not so sure that is is secret, but it's certainly dirty :)

To be quite honest, modems are no different from any other piece of hardware; get something that is well-supported by Linux (which does not include winmodems, as we are at the mercy of a proprietary third-party driver provider, and cannot include the drivers in the default install nor do much to improve them) and life will be easy; get something that's not, and you're in a world of hurt :)

For the record, I bought a PCMCIA modem from eBay for £10 inc p&p (a xircom one) which "just works" with my laptop and any distro - the drivers are part of the stock kernel, and all you need to know is the /dev/ entry where the modem is located and your ISPs phone number, username and password and that's it! I seem to recall that I once used an external serial modem with Linux and that worked similarly effortlessly - no drivers or configuration required.  The /dev/ entry will show up in dmesg when you plug the PCMCIA modem in.

So if you value your time (and hair!) more than your bank-balance, I'd advise going with one of these :)[/QUOTE]

Good to hear from you again.

We have corresponded about my modem issues in the past, as you may remember but, despite the help of yourself and others, I'm still searching.

You're right, I could throw down a few bucks and get another modem but I'm too bloody stubborn (its my British blood).  

Logic tells me (well, MY logic) that, if I can connect with Mepis, its not the 'Linux' that is at fault here, its the Ubuntu.  The Ubuntu program lacks something which facilitates the communication between my modem and the internet.  Something which Mepis obviously has.

Since the modem I have only cost me 99 cents (brand new, long story, I won't bore you) and this same type of modem can be purchased for $3 on E-bay, I think it would be nice for other people to be able to avail themselves of this, too, instead of paying $20, $40, etc. or, worse, becoming convinced that they _have_ to subscribe to cable or DSL.

Then he stepped of his podium and bid you good day.   :-)

---

### Post by UltraSonicSite on 2006-01-14
So what solution should i take =P

---

