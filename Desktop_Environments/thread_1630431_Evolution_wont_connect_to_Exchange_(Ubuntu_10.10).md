---
title: "Evolution wont connect to Exchange (Ubuntu 10.10)"
date: 2010-11-25
forum: Desktop Environments
---

### Post by dave2ym on 2010-11-25
Hello,
I had decided to give Ubuntu a go on my work notebook. At work we use Exchange 2003 (at the moment) for email.
I had open **Evolution** and tried to configure it.
I got the welcome screen (wizzard), I clicked *Forward* and then I skipped *Restore from backup* (since this is a new install) and clicked *Forward. *It asked for identity and I gave the details (as shown in the first screenshot) then hit *Forward* and made the necesary settings as shown in the second screenshot.
Then I click *Authenticate* and it asks for my exchange password. i type it and then it gives me the error ***"Could not locate server."***.
I am sure the server name is correct and I am sure it resolves correctly (tried it with firefox and works just fine).
I also tried username as follows:
[EMAIL="user@DOMAIN.RO"]user@DOMAIN.RO[/EMAIL]
DOMAIN\user

It simply does work. Do you guys have any ideas?

Thanks.


[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by dave2ym on 2010-11-25
It seems that the Exchange is 2007. Could that be the cause? Is Evolution working with Exchange 2007?
I had read some threat that say Evolution is only working with Exchange 2003.

---

### Post by Weazel on 2010-12-20
I have almost the same problem, My office uses Exchange 2010
and when i enter the address like in your screenshots only with the "/owa" part, it seems it thinks its exchange 5.5 or something, its giving an error "

```
The Exchange server is not compatible with Exchange Connector.

The server is running Exchange 5.5. Exchange Connector 
supports Microsoft Exchange 2000 and 2003 only
```

I think Evolution just doesn't support Microsoft Exchange 2007 and up... shame.

Weazel.

---

### Post by Mathieu.F on 2011-01-05
try installing and using evolution-mapi instead of evolution-exchange, it workds better with newer version of MS exchange.

---

### Post by AjitDingankar on 2011-02-24
Just installed evolution-mapi (0.30.3-1) but I get the error 
"MAPI_E_LOGON_FAILED" 
when I try to connect with my Office 2010 Exchange server.

---

### Post by akvik on 2011-03-07
> **AjitDingankar said:**
> Just installed evolution-mapi (0.30.3-1) but I get the error 
"MAPI_E_LOGON_FAILED" 
when I try to connect with my Office 2010 Exchange server.

Same problem here (as with many others) - are there any efforts made to fix the Evolution connection to Exchange 2010 servers?

---

