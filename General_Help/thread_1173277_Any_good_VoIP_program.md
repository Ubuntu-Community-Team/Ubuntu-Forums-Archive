---
title: "Any good VoIP program?"
date: 2009-05-29
forum: General Help
---

### Post by fontis on 2009-05-29
Hey!
I was wondering if there are any good and easy free pc-to-landline VOIP programs available for Ubuntu.

I currently reside in Czech Republic and my family is in Sweden. I used to re-register multiple accounts on VoIP Discount so I could use the program and call for free to my Swedish landline. So you see it's rather problematic that this can't be done in Ekiga for instance.

So my question is, are there any equivalents for this? Or do I have to run voipdiscount under Virtualbox or Wine? And the further problem is that in Virtualbox, for some reason my mic wont work properly. There's some "delay" in the audio transmission and also my sound is not recorded properly so the recipient cant hear me properly.

This is a very delicate question for me because it has been the deciding factor for me switching back full-time to win before..

Thanks.

---

### Post by upbeat.linux on 2009-05-29
If you already have a land-line you can use Asterisk:

[http://www.asterisk.org/](http://www.asterisk.org/)

---

### Post by jonobr on 2009-05-29
Hello

Could you provide a bit more info?

When you mention a voip program are you looking for a client piece of software to make free calls?

If so, could you not run Skype on both ends and make like a bit easier for your self?


With Skype of course, your not running traditional standards based SIP, your traffic is encrypted and there are security concerns, however as said if your just looking to make free calls, I would have your ubuntu and the other end on skype.

---

### Post by brian_p on 2009-05-29
> **fontis said:**
> 

I was wondering if there are any good and easy free pc-to-landline VOIP programs available for Ubuntu.

twinkle has no problems with dealing with calls via VoipDiscount.

---

### Post by fontis on 2009-05-30
Well I'm looking for a client which is natively run under linux, which offers a quick "register new account" thing whenever the "free minutes pass".

To make an example, I want something like the Voipdiscount client but for linux, utilizing such a service. In voipdiscount, whenever my "free minutes" are out I can always re-register a new account and keep calling for free.

---

### Post by brian_p on 2009-05-31
> **fontis said:**
> 

To make an example, I want something like the Voipdiscount client but for linux, utilizing such a service. In voipdiscount, whenever my "free minutes" are out I can always re-register a new account and keep calling for free.

As I said - twinkle. Use the VoipDiscount website to get a new account. If you want something **exactly** like the VoipDiscount software you are asking too much.

---

### Post by DeMus on 2009-05-31
> **fontis said:**
> Hey!
I was wondering if there are any good and easy free pc-to-landline VOIP programs available for Ubuntu.

I currently reside in Czech Republic and my family is in Sweden. I used to re-register multiple accounts on VoIP Discount so I could use the program and call for free to my Swedish landline. So you see it's rather problematic that this can't be done in Ekiga for instance.

So my question is, are there any equivalents for this? Or do I have to run voipdiscount under Virtualbox or Wine? And the further problem is that in Virtualbox, for some reason my mic wont work properly. There's some "delay" in the audio transmission and also my sound is not recorded properly so the recipient cant hear me properly.

This is a very delicate question for me because it has been the deciding factor for me switching back full-time to win before..

Thanks.

On our Windows machine we use a program called Voipbuster. It's like Skype, but cheaper. There are many countries to which you can call for free, to a normal phone that is. Take a look at voipbuster.com
The problem is: they don't have a linux version yet. That's why we still keep one machine with Windows here. We have family in Indonesia and America and use it a lot. To the US it is completely free, to Indonesia only 3ct/min. We are calling from Holland.
PC to PC is completely free of course.
But as said: no Linux version yet.

---

### Post by Legace on 2009-05-31
> **DeMus said:**
> But as said: no Linux version yet.

You can always try to manually set the settings.
The guide below is for VoipCheap, but use the settings in the quotes below.
[http://ubuntuforums.org/showthread.php?t=309218](http://ubuntuforums.org/showthread.php?t=309218)

Here are settings for VoipBuster:
> 
	SIP port : 5060
	Registrar : sip.voipbuster.com
	Proxy server : sip.voipbuster.com
	Outbound proxy server : leave empty
	Account name : your VoipBuster username
	Password : your VoipBuster password
	Display name/number : your VoipBuster username or voipnumber
	Stunserver (option) : stun.voipbuster.com

and for VoipDiscount:
> 
	SIP port : 5060
	Registrar : sip.voipdiscount.com
	Proxy server : sip.voipdiscount.com
	Outbound proxy server : leave empty
	Account name : your VoipDiscount username
	Password : your VoipDiscount password
	Display name/number : your VoipDiscount username or voipnumber
	Stunserver (option) : stun.voipdiscount.com

---

### Post by DeMus on 2009-05-31
> **Legace said:**
> You can always try to manually set the settings.
The guide below is for VoipCheap, but use the settings in the quotes below.
[http://ubuntuforums.org/showthread.php?t=309218](http://ubuntuforums.org/showthread.php?t=309218)

Here are settings for VoipBuster:



Where should I set these settings? We have a Voipbuster account but no Linux voipbuster program. The Windows version does not run in Wine so what should I do?

---

### Post by brian_p on 2009-05-31
> **DeMus said:**
> 

The Windows version does not run in Wine so what should I do?

Use twinkle.

---

### Post by DeMus on 2009-05-31
> **brian_p said:**
> Use twinkle.

Well, I tried .... and failed big time.
I downloaded Twinkle, used the instruction "./configure" after having used tar, but it says sipwitch is missing.
So I  searched for, found and downloaded sipwitch. Using "./configure" I see I don't have ucommon library.
So I searched for, found and downloaded ucommon. Using "./configure" I don't see any errors, so I use "make" and "make install" and still no errors. Okay, let's continue.
Back to sipwitch. "./configure" still says I don't have ucommon library. I rebooted because I thought maybe the library isn't registered or read yet. Still sipwitch does not want to be configured.

What's next? Please help.

---

### Post by DeMus on 2009-05-31
> **fontis said:**
> Hey!
I was wondering if there are any good and easy free pc-to-landline VOIP programs available for Ubuntu.

I currently reside in Czech Republic and my family is in Sweden. I used to re-register multiple accounts on VoIP Discount so I could use the program and call for free to my Swedish landline. So you see it's rather problematic that this can't be done in Ekiga for instance.

So my question is, are there any equivalents for this? Or do I have to run voipdiscount under Virtualbox or Wine? And the further problem is that in Virtualbox, for some reason my mic wont work properly. There's some "delay" in the audio transmission and also my sound is not recorded properly so the recipient cant hear me properly.

This is a very delicate question for me because it has been the deciding factor for me switching back full-time to win before..

Thanks.

Sorry for taking over your thread. But I have news for you. After having tried to make twinkle work the way brian_p wrote it turned out twinkle is in the repositories. You can simply install it using using Synaptic.
I looked for you on the voipbuster.com page and a call from a PC in the Czech Republic to a landline in Sweden cost 1 ct/min. Phone to phone also costs 1 ct/min plus 5 ct. to start the call.
Is this a good deal for you? I hope so.

---

### Post by Legace on 2009-05-31
Why don't you use Ekiga?

---

### Post by DeMus on 2009-05-31
> **Legace said:**
> Why don't you use Ekiga?

I don't really understand Ekiga. It looks to me I have to make an account for something and I don't want that. I have an account with voipbuster.com and that is enough.
I can be wrong about Ekiga but when I start the program it sure looks like I have to make an account.

---

### Post by Legace on 2009-05-31
> **DeMus said:**
> I don't really understand Ekiga. It looks to me I have to make an account for something and I don't want that. I have an account with voipbuster.com and that is enough.
I can be wrong about Ekiga but when I start the program it sure looks like I have to make an account.

When it asks you, enter your name.
Then it will ask you to creata a free account. You need to check the "I do not want to signup --" thing and press Forward. Now check the checkbox again, and press Forward. Select your connection type, and press Forward. Once you can see Ekiga, select Edit -> Accounts. Once the Accounts window opens, select Accounts -> Add a SIP account.


:)

---

### Post by DeMus on 2009-05-31
> **Legace said:**
> When it asks you, enter your name.
Then it will ask you to creata a free account. You need to check the "I do not want to signup --" thing and press Forward. Now check the checkbox again, and press Forward. Select your connection type, and press Forward. Once you can see Ekiga, select Edit -> Accounts. Once the Accounts window opens, select Accounts -> Add a SIP account.


:)

OK, I did that but I get the message at the bottom of the main screen: Can't register <accountname>@sip.voipbuster.com. I am online, atleast the program says so.
Also I noticed I can't send sms's using this program, Twinkle can do that. 
Thanks for the help, but I think I will stay with Twinkle.

---

### Post by xx58 on 2010-02-18
:rolleyes: I use round one year now VoipBuster and it very good program, but it run nicely only under Windows.Problem are, how I try VoipBuster nicely regristred under Ekiga, but cannot find out, how it works?
Skype under Linux works like charm.
If somebody have working VOIPBUSTER UNDER Linux, then please give detailed instraction how do too? Also under what program you run it. 
Thanks up front for your help.

---

### Post by VanillaMozilla on 2010-03-17
There is a thread here, with my summary of what I found:  [http://ubuntuforums.org/showthread.php?t=1408679&page=3](http://ubuntuforums.org/showthread.php?t=1408679&page=3) on VoIP programs.  The only one I have gotten working completely (for making calls) is Twinkle, with Diamondcard for computer-to-phone calls.

Ekiga has numerous problems, which may or may not be caused by sound packages (ALSA and others).

---

