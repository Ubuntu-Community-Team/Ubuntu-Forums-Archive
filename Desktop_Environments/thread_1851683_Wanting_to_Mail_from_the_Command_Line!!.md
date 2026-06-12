---
title: "Wanting to Mail from the Command Line!!"
date: 2011-09-28
forum: Desktop Environments
---

### Post by mikaelcrocker on 2011-09-28
Afternoon from the west coast!

Kinda new to Ubuntu and these forums, I was wanting to know how I could send emails with attachments from the command line.

I did a tried using Mutt but i need to install additional packages, which ones should i install?

Thanks in advance fellas

-Mike

---

### Post by Subliminal Aura on 2011-09-28
sudo apt-get install pine

I used to use it a lot but was like 17 years ago ;)

---

### Post by IWantFroyo on 2011-09-28
Try alpine instead of pine. Alpine is the continuation.

---

### Post by Subliminal Aura on 2011-09-28
> **IWantFroyo said:**
> Try alpine instead of pine. Alpine is the continuation.

wow - that's amazing !

Reading this brought back some fond and not so fond memories 

[http://en.wikipedia.org/wiki/Comparison_of_e-mail_clients](http://en.wikipedia.org/wiki/Comparison_of_e-mail_clients)

---

### Post by IWantFroyo on 2011-09-28
> **subliminal aura said:**
> wow - that's amazing !

Reading this brought back some fond and not so fond memories 

[http://en.wikipedia.org/wiki/comparison_of_e-mail_clients](http://en.wikipedia.org/wiki/comparison_of_e-mail_clients)

lol :)

---

### Post by drawkcab on 2011-09-29
I was going to say, find a time machine and send yourself back to the early 90s.

---

### Post by SeijiSensei on 2011-09-29
If you only want to send a message from the command prompt, without using a full-featured client like alpine, install the bsd-mailx package.  Make sure you have Postfix or sendmail installed as well.  Then you can run:

```
$ echo 'this is a test' | mail -s 'testing testing testing' someone@example.com
```

or send the contents of a text file with

```
$ mail -s 'my file' someone@example.com < /path/to/myfile
```

---

### Post by aeiah on 2011-09-29
to send an attachment on the command line (again, without using something like mutt or alpine - useful for scripts) you could do this: 
```

uuencode filename displayname | mail email@address.com

```
from [http://www.shelldorado.com/articles/mailattachments.html](http://www.shelldorado.com/articles/mailattachments.html)

---

### Post by Subliminal Aura on 2011-09-29
> **aeiah said:**
> ....
```

uuencode ....

```


Christ! These reminds me the early 90s and teadiously joining usenet posts... finally decoding them only to find a checksum error \\:D/

Thank God 40gig ISOs didn't exist back then :)

---

### Post by mikaelcrocker on 2011-09-29
I know it's a wicked old thing to do, but I got it working, thanks guys!

---

### Post by SeijiSensei on 2011-09-29
I still find alpine invaluable for managing dodgy user mail accounts.  I can ssh to the mail server, use su to become the user in question, then manipulate the user's mail folders as needed.

---

### Post by BitJunkie on 2011-09-29
I have had success with sendEmail ([http://caspian.dotconf.net/menu/Software/SendEmail](http://caspian.dotconf.net/menu/Software/SendEmail)). Simple and it supports TLS.

---

### Post by andrew.46 on 2011-10-01
> **drawkcab said:**
> I was going to say, find a time machine and send yourself back to the early 90s.

Mind you I maintain this web page:

Using Mutt with Gmail
[http://www.andrews-corner.org/mutt.html](http://www.andrews-corner.org/mutt.html)

and it is very popular in 2011 :).

---

