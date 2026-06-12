---
title: "evolution connect problem"
date: 2009-04-27
forum: General Help
---

### Post by mcrene on 2009-04-27
So after the recent Ubuntu version upgrade I have had a few quirks, which I have cleared up mostly.
In fact I can even watch video's on the internet now, which I haven't been able to do since I installed Ubuntu, good news.

However since the upgrade I haven't been able to connect to 127.0.0.1 in Evolution, which is trying to retrieve my Hotmail emails.

the error msg;

Could not connect to 127.0.0.1: Connection refused

Could not connect to 127.0.0.1: Connection refused

Could not connect to 127.0.0.1: Connection refused

Could not connect to 127.0.0.1: Connection refused

is what I am getting after pressing Send/Receive in Evolution.


I have followed the "how-to get hotmail in Evolution" thread, and done a few searches for different similar problems, but none are soling this situation for me.

Any thoughts on why this could be happening?

Thanks for your help on the subject.

---

### Post by ophysis on 2009-07-04
Same here...

---

### Post by Soul-Sing on 2009-07-04
Hotmail server down?

---

### Post by wojox on 2009-07-04
When you configure for Recieving

Server Type: POP

Server: pop3.live.com:995

SSL encryption


For Sending

Server Type: SMTP

Server: smtp.live.com:25
check server requires auth.

Use TLS

---

### Post by jlabeaga on 2009-11-10
great tip wojox, it worked perfectly

thanks![U]

[/U]

---

### Post by arcs123 on 2009-11-26
Thanks for the above advice. had the same problem and the provided instructions solved it. Just add in Evolution you also need to specify an Authentication which should be set to "Login" and then also check "Remember password"

---

