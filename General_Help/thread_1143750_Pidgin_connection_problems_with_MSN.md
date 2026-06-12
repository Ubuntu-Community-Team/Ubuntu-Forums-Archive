---
title: "Pidgin connection problems with MSN"
date: 2009-04-30
forum: General Help
---

### Post by rathotron on 2009-04-30
Hi,

I can't connect to MSN in Pidgin at my school, but connection at home is no problem. 

I've talked to the IT peeps at my building, who told me they don't use proxy, so that's not the issue. 
I can connect through WLM in WinXP without problems. 
I've also tried installing the package msn-pecan, and connecting through the added WLM protocol in Pidgin afterward, but that doesn't work either.

I've attached the debug for the WLM protocol connection failure.

Any brilliant suggestions spring to mind?

Cheers

---

### Post by Legace on 2009-04-30
Do you have the latest version of Pidgin?
I had this problem a few months ago, but a Pidgin update fixed it :)

---

### Post by rathotron on 2009-04-30
> **Legace said:**
> Do you have the latest version of Pidgin?
I had this problem a few months ago, but a Pidgin update fixed it :)

Just updated today, version 2.5.5. It seems there's no connection to the messenger.hotmail.com - I tried telnet to this as well, but connection timed out again.

---

### Post by Legace on 2009-05-01
Maybe you could try to disable IPv6..

Type this in Terminal.
```
sudo gedit /etc/modporbe.d/aliases
```

Enter password.

Enter this into the Text Editor window:

```
alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
```

Reboot, and see if problem persists.
If you see no change, enable IPv6 again (= delete the 3 lines above from the aliases file).

---

### Post by rathotron on 2009-05-06
Thanks for the reply Legace, just got time to try it out now.. However, that didn't work either.. 

The IT admin at my institute said it could be that Pidgin maybe uses other UDP ports then WLM. Can anyone confirm/reject that?

Cheers

---

### Post by jefelex on 2009-05-08
I think it may have something to do with the MSN servers - I'm having sporadic unexplainable connection problems with connecting both with pidgin and amsn.

John

---

