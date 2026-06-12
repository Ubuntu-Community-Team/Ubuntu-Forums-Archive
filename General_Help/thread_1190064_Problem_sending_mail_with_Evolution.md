---
title: "Problem sending mail with Evolution"
date: 2009-06-17
forum: General Help
---

### Post by Benjamin Franklin on 2009-06-17
Hi,  I am running Jaunty 64-bit.  My ability to send e-mail with Evolution randomly stops. I have not found a pattern to it and haven't been able to find anyone else with this specific problem.  Sometimes I am able to send messages with no problem. Other times when I send a message, the progress bar at the bottom immediately reads &quot;100% complete,&quot; but the message stays in the outbox and won't send when the send/receive button is pressed. I am consistently able to send mail with Thunderbird, and both programs are configured to use the same port, so I am assuming that the problem is with Evolution.  thanks

---

### Post by cdillard-hsp on 2009-09-14
There are others with this problem.  I've found that starting Evolution from a Terminal apparently makes it work all day without failing to send.

[http://ubuntuforums.org/showthread.php?p=7855873](http://ubuntuforums.org/showthread.php?p=7855873)

---

### Post by betsy_kevin on 2009-12-14
Hello,
I successfully set up my evolution POP3 email with one of my accounts about a month ago and was using it without problems until today. What happens is that it simply doesn't send, and I wait minutes and minutes for any sign of life but only see the "sending message 1 of 1" for my test messages. Eventaully it times out with "Error while performing operation. could not connect to smtpout.secureserver.net: *(which is the correct name for my smtp server)* Connection timed out."

What happened today that's different from before?

I connected it with the fact that I added another email account that uses IMAP, leaving the POP3 as the default account.

In trying to troubleshoot, I noticed that for some reason the POP3 Account now specified using SSL encryption and "Plain" authentication. I know that this is not correct, and wasn't the way I'd initially set it up, so I changed this to remove SSL encryption and set up login authentication.  No luck.

I tried "forget passwords" since two weeks ago I updated my POP3 email password and thought maybe the old one was stuck there. No luck.

Since I had not done a lot of customization, I deleted the POP3 account entirely and set it up again, carefully following all the settings from my provider, with my spouse proofreading. No luck.

I tried setting the IMAP account as my default, but I could not send from that one either.

After reading other posts where it successful started from within a terminal, I tried that, and still no luck.  

Other suggestions please? A reader on the list serve suggested removing and reinstalling Evolution, and plenty of others have suggested Thunderbird instead, but this is the installation that came with the machine, and I'm not yet ready to try that.

Thank you!
Betsy

---

