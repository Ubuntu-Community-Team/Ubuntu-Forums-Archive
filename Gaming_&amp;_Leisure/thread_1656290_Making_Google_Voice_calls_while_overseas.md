---
title: "Making Google Voice calls while overseas?"
date: 2010-12-30
forum: Gaming &amp; Leisure
---

### Post by daqron on 2010-12-30
I am in the US and have been using [Google Voice calling]("http://googlevoiceblog.blogspot.com/2010/08/make-and-receive-calls-in-gmail.html"). Google indicates this is only for US customers, but I was wondering if anyone has tried:
[LIST=1]
[*]Making calls from your US Google Voice account while overseas (specifically, in Europe), or if that won't work, 
[*]Tunneling through SSH or a VPN to a US-based computer to make calls 
[/LIST]
All calls would be made *to* US phone numbers, and although my Google Voice-associated cell phone will not work overseas, the number will remain active so I will remain a legitimate US phone subscriber eligible for a Google Voice account.

Cheers in advance for any advice!

---

### Post by mips on 2011-01-01
> **daqron said:**
> I am in the US and have been using [Google Voice calling]("http://googlevoiceblog.blogspot.com/2010/08/make-and-receive-calls-in-gmail.html"). Google indicates this is only for US customers, but I was wondering if anyone has tried:...


That link you provided actually answers your question:
> Google Voice lets you manage all your phone communications and seamlessly make and receive calls on any of your existing phones. But what if you don’t have your phone with you? Or what if you’re in a place with poor cell phone reception, **or you’re travelling internationally and don’t want to incur expensive roaming charges?** *Wouldn’t it be great if you could use your computer to make or receive calls?*

**Starting today you can use Gmail to receive or place Google Voice calls.**

---

### Post by daqron on 2011-01-01
Cheers for the response.

That post doesn't clarify whether the calls are free (as though I was in the US) or charged as international GV calls. It says "international calls will use your Google Voice calling credit and are offered at the same low Google Voice rates." Does Google consider a call from my US-based number to be "international" if I am making the call from a non-US IP address?

I tried to test this by SSH-tunneling my browser connections through a UK-based server and it seemed to work (free of charge), but I'm not convinced by that. I'd like to know if anyone's tried this from overseas with any success.

---

### Post by mips on 2011-01-01
You are confusing international calls originating in the USA to other countries with calls made to the USA. The service is not available to outside countries and getting your call from the UK to the USA involves VoIP to the USA from where it breaks out to the PSTN. You don't pay for the TCP/IP part, costs are only incurred from the breakout point to the PSTN. So whatever the charges are in the USA they would be the same for originating from Kazakstan on where ever you can get a good internet connection from.

---

### Post by daqron on 2011-01-01
That makes sense. Thanks for the explanation.

---

### Post by mips on 2011-01-02
If I could get access to a temporary account I would be willing to test this in order to confirm my theory which I reckon is correct anyway.

---

