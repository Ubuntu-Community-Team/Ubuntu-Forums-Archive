---
title: "https + roaming wife = unsecure?"
date: 2005-05-19
forum: Desktop Environments
---

### Post by moon2js on 2005-05-19
I know wireless is by design very hard to secure, but I'm just wondering how secure using https in a coffeeshop is versus WEP on my home wireless network.

---

### Post by cwaldbieser on 2005-05-19
The comparison is a little odd.  Also, you did not elaborate what kind of network traffic happens over your home wireless network.  For example, you might only ever connect to another machine using ssh, or you might just telnet using the same password you log into your online bank account with.

In a strict sense, a computer in a coffee shop is insecure, because it is out of your control.  The owner could install keystroke loggers on it, and record everything you type, https or no.

I do not think there is really a definitive answer to your question.  Is there a practical application to which you wish to put it, or are you simply curious?

---

### Post by az on 2005-05-19
A wireless cafe may attract more crackers because there will be more users and therefore more potential for for stealing someting useful, but the nature of the risks are the same in both scenarios.

I had to apply for parental benefits from the government of Canada.  At the time, they did browser detects for online security and I was denied access to the site until I installed the useragent plugin for Mozilla.

When I complained to a representative, I was told to go to a public internet cafe and use a windows box to make sure that I was secure enough.

I complained again, pointing out the blatant flaw in logic of their argument.

I then got an answer along the lines that their software was newly implemented and was going to be improved in the future....

---

### Post by moon2js on 2005-05-19
[QUOTE=cwaldbieser]The comparison is a little odd.  Also, you did not elaborate what kind of network traffic happens over your home wireless network.  For example, you might only ever connect to another machine using ssh, or you might just telnet using the same password you log into your online bank account with.[/quote]Well, I'm under the impression that anything I do in a coffeeshop is transparent as there is no encryption going on (as opposed to my home wireless network which is WPA). But I'm wondering if, let's say, accessing my web-based email with https in that coffeeshop hotspot makes it less transparent?

[QUOTE=cwaldbieser]In a strict sense, a computer in a coffee shop is insecure, because it is out of your control.  The owner could install keystroke loggers on it, and record everything you type, https or no.[/quote]Well, that's actually why I avoid public terminals and prefer to use my own laptop in a coffee shop.

[QUOTE=cwaldbieser]I do not think there is really a definitive answer to your question.  Is there a practical application to which you wish to put it, or are you simply curious?[/QUOTE]Well, how about a school's online student account services? I would normally connect via https from my home WPA'd wireless or wired network. But how does accessing the same services via https from a coffeeshop or library open wireless network via https compare security-wise?

---

### Post by jcooper on 2005-05-19
A good response by azz here... though if your wife is roaming, you probably are unsecure ;)

Sorry... couldn't resist!

> Well, I'm under the impression that anything I do in a coffeeshop is transparent as there is no encryption going on (as opposed to my home wireless network which is WPA). But I'm wondering if, let's say, accessing my web-based email with https in that coffeeshop hotspot makes it less transparent? 
Accessing anything over the internet using https will use a secure session - i.e. there is effectively a secure tunnel between your machine and the server. However, the browser has to initiate this session with the server, hence any malicious person could snoop this traffic, capture the SSL details, then masquarade as your machine. My understanding of how SSL works is limited, but you should be very wary of using **any** unencrypted and open wireless network.

---

### Post by brandan on 2005-05-19
i'd worry more about the roaming wife.

---

