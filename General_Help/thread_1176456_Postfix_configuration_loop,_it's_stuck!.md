---
title: "Postfix configuration loop, it's stuck!"
date: 2009-06-02
forum: General Help
---

### Post by juicymixx on 2009-06-02
So I just installed Jaunty, and I started adding in other programs using apt-get.   Postfix is stuck in some sort of loop in it's configuration.   I found other threads which mentioned this, but none of their fixes worked.   I'm stuck at:

-¦ Postfix Configuration +------------------------+
¦ ¦
¦ ?
¦ No configuration: ¦
¦ Should be chosen to leave the current configuration unchanged. ¦
¦ Internet site: ¦
¦ Mail is sent and received directly using SMTP. ¦
¦ Internet with smarthost: ¦
¦ Mail is received directly using SMTP or by running a utility such ¦
¦ as fetchmail. Outgoing mail is sent using a smarthost. ¦
¦ Satellite system: ¦
¦ All mail is sent to another machine, called a 'smarthost', for ¦
¦ delivery. ¦
¦ Local only: ¦
¦ The only delivered mail is the mail for local users. There is no ?
¦ network. ?
¦
¦ <Ok>


I CANNOT select an option, or OK. If I hit escape then I'm taken to:

-¦ Postfix Configuration +------------------------+
¦ ¦
¦ ?
¦ General type of mail configuration
¦ 
¦ No confguration
¦ Internet site
¦ Sattelite system
¦ Local only
¦ 
¦
¦ <Ok>    <Cancel>

Here I can choose an option, but hitting enter takes me back to the first screen in an endless loop between the two.

I can hit Ctrl-C between the screens and stop the configuration, but then apt-get stops also.   Any other program I try to install triggers the Postfix configuration now.

Any hints on how to get through this annoying problem?

Thanks.

---

### Post by juicymixx on 2009-06-02
Okay, well I found my way around the problem.   For anyone else who runs into this...

I was installing stuff using apt-get
when postfix was stuck in this loop, it would foul up apt-get since postfix's configuration wasn't completing.

Well, to make a long story short...   I tried installing postfix using synaptic (the graphical interface).   The install went well (without a hitch), and now I can get back to the command line since apt-get no longer tries to run postfix's configuration.

I dunno why it was fouled up earlier, but at least this gets me past the problem.   Enjoy.

---

