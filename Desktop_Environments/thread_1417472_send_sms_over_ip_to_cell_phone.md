---
title: "send sms over ip to cell phone"
date: 2010-02-27
forum: Desktop Environments
---

### Post by carolinason on 2010-02-27
does anyone know of an app to send sms texts to phones from gnome desktop? 

i can use web based services but didn't know if it was possible using ubuntu. it was my hope i could receive them, but i could live without that. i can receive free texts on my phone but a person has to send me a new text because there is no way to reply to the web sent sms directly.

---

### Post by tgalati4 on 2010-02-27
smstools and smsclient

---

### Post by carolinason on 2010-02-28
oops a simple search in aptitude - thanks!

---

### Post by carolinason on 2010-02-28
there are many sites that show smstools/client configured for a ppp/modem with pots, but not for dsl/broadband.... :(

---

### Post by tgalati4 on 2010-02-28
If you do a wider google search for sms clients for linux, you will find scripts for various cell phone operators.  Basically, you need to log into your provider's sms server with proper credentials then send the message.  Not all providers have a server to send sms this way, but many do.

I think some of the instant messaging clients have cell provider hooks, but again, you will have to search.

This might help:

apt-cache search gnokii

---

