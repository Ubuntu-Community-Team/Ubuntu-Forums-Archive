---
title: "sendmail problems"
date: 2005-12-11
forum: General Help
---

### Post by maino82 on 2005-12-11
I'm trying to set up a web server on my ubuntu box and want users to be able to email me from a form within my webpage. Whether this form be made and processed with perl or PHP doesn't matter to me (I already have scripts set up for both possibilities), but sendmail does not seem to be cooperating. The scripts seem to be working fine and do not give me any kinds of errors, but the message never actually gets sent. I've looked on the forums here and have noticed a lot of issues with postfix, which I've tried some of the things suggested but none have seem to have worked. I have tried changing ownership of sendmail to my main user, but that also has not worked. Is there something specific to sendmail that needs to be change? Is there something that needs to be changed with the default ubuntu installation to allow sendmail to be used properly?

Also, just FYI, my /var/log/mail.log has the following in there:

> Dec 11 12:26:53 localhost postfix/cleanup[19832]: F1F932006C6: message-id=<20051211172653.F1F932006C6@maino.psu.edu>
Dec 11 12:59:02 localhost postfix/pickup[19474]: 55AB3200955: uid=33 from=<www-data>


I have no idea what this means.

Thanks,

Dave

---

### Post by maino82 on 2005-12-15
ok so i've gotten a little further on this problem on my own, but not much further. apparently gmail is bouncing this back at me saying there's no such user, when i know that there is. also, there may be additional problems that i'm not seeing. i just sent myself a message from the form, and this is what the mail.log has to say about that. i'm not too great at interpreting all of this... basically the only thing i got out of it was that gmail was unable to verify who i was. any hints would be greatly appreciated. 

> 
Dec 15 07:45:26 localhost postfix/cleanup[27278]: 21EA320054E: message-id=<20051215124526.21EA320054E@gmail.com>
Dec 15 07:45:26 localhost postfix/local[27280]: 21EA320054E: to=<dave@gmail.com>, orig_to=<root>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")
Dec 15 17:29:36 localhost postfix/pickup[1169]: F0EAB20054E: uid=33 from=<www-data>
Dec 15 17:29:36 localhost postfix/cleanup[2371]: F0EAB20054E: message-id=<20051215222935.F0EAB20054E@gmail.com>
Dec 15 17:29:36 localhost postfix/local[2373]: F0EAB20054E: to=<david.maino@gmail.com>, relay=local, delay=1, status=bounced (unknown user: "david.maino")
Dec 15 17:29:36 localhost postfix/cleanup[2371]: 5883F200560: message-id=<20051215222936.5883F200560@gmail.com>
Dec 15 17:29:36 localhost postfix/local[2373]: 5883F200560: to=<www-data@gmail.com>, relay=local, delay=0, status=sent (delivered to command: procmail -a "$EXTENSION")


also, just fyi, this is from my PHP script. the cgi script is still having some issues. it doesn't really matter to me which way this problem is resolved, however, so long as it's resolved.

---

