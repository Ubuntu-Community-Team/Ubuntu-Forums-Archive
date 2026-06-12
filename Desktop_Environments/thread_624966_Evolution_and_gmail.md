---
title: "Evolution and gmail"
date: 2007-11-27
forum: Desktop Environments
---

### Post by schweyer on 2007-11-27
Hi,

I try to connect to gmail with Evolution. My problem is, tha tI can receive messages, but I am unable to send messages. I receive a message that the server doesn't exist. I am using smpt.gmail.com. Is there a explanation available? I've googled for hours and couldn't find a hint. To me it looks, that I am doing everything correct, but I am not... .

Appreciate your help.

Volker

---

### Post by edm1 on 2007-11-27
hope [this]("http://mail.google.com/support/bin/answer.py?answer=79344&topic=12762") helps

---

### Post by Snowcat on 2007-11-27
Every time I've had problems with accounts in Thunderbird, it was due to stupid typos on my part.
Make sure that you use smtp.gmail.com (and not smpt, as you wrote), on port 587, with TLS enabled. This is what I currently have and is working just fine.

---

### Post by kweinert on 2007-11-27
It's important to note that using port 587 may be the most important point in the advice you got. I know that some ISPs (Comcast among them) block port 25 in the effort to block the global SPAM hordes :)

587 is the established alternative port, but it's not likely that it would come up randomly in a search on setting up GMail/Evolution (or any other client.)

---

### Post by edm1 on 2007-11-27
Make sure you tick 'Server requires authentication' and select SSL encryption.

---

