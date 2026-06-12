---
title: "HELP!!! Envy + ATI MR X1450 + fglrx + Beryl + (AIXGL vs XGL) on 64bit(Edgy vs Feisty)"
date: 2007-06-07
forum: Desktop Effects &amp; Customization
---

### Post by Enginirical on 2007-06-07
Ok, I popped my Linux cherry last weekend by installing Dapper. I updated to Edgy and set about sorting out my ATI card with a view to getting Beryl working. I tried to install the fglrx driver for ATI as I understand Beryl will not work with the official ATI driver, It didn’t reboot so I copied my backed up xorg.conf to restored the system. I then found out about ENVY, it worked awesomely. I then downloaded Beryl and it wouldn’t load (kept reverting to metacity default).

I also reinstalled Dapper to try the official driver from ATI, and that didn’t work at all. It was only after doing this that I learnt It would not have worked with Beryl anyway. 

So, for my sake and all the other noobs with ATI :

To get Beryl working with Edgy I understand I need to use a restricted driver (fglrx), can I use ENVY, does it install a compatible driver for Beryl? If fglrx is no good for me how do I blacklist it, Do I need to even bother?

I have tried twice installing fglrx and it just won’t configure&#61516;

I also understand if I use Edgy (despite having AIGLX embedded in X.org) I have to use XGL to have any chance of success with Beryl on ATI. (I had xgl session option in beryl manager but it flipped straight back to regular session when activated)

Im also unsure as to which Beryl version I should use, I have read posts where people have only got it working by downgrading it, but they were using Feisty. Does the same apply to Edgy 64bit? If so how do I downgrade it?

Im planning on re-installing 2day and starting again, I was hoping someone could tell me what I should and shouldn’t be doing. Am I better of using Feisty instead of Edgy?

How do I actually get fglrx to install properly on ATI X1450? Or can I just use ENVY again, as it is the only thing that has got my graphics card working so far.

After the graphics card is working do I need to disable AIGLX before attempting to implement an XGL session. If so how?

Do I download Beryl last? And which version should I use? If it is not the latest version that I should be using, how do I downgrade?

Finally am I just wasting my time, is there another option out there?

Any help or advice will be greatly greatly appreciated as I’m really confused! 

Please keep it simple as I’m very new to all this fun! thanks

---

### Post by viciouslime on 2007-06-08
> tried to install the fglrx driver for ATI as I understand Beryl will not work with the official ATI driver

Firstly, fglrx IS the "official" driver. The "ati" driver is the free, open source one which doesn't work with modern cards very well. There are an awful lot of questions here, but I think the best way to answer most of them would be with this link: [https://help.ubuntu.com/community/Beryl/ATI/Feisty]("https://help.ubuntu.com/community/Beryl/ATI/Feisty")

If you still have questions after following that post back :)

---

### Post by Enginirical on 2007-06-08
Hey, Thanks for looking at this post for me!

Is this the same with Edgy? or should I upgrade to Feisty?

cheers

---

