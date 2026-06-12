---
title: "Setting up an (anonymous?) proxy server at home"
date: 2009-03-31
forum: General Help
---

### Post by spades on 2009-03-31
Hello all

My firm is instituting some new web filtering (using BlueCoat) that really restricts my online life at work. The usual anonymous proxy servers are already blocked so I am considering hosting an proxy server on my home ubuntu machine. 

My intent is to be able to add my home.domain.com to firefox proxy settings at work and surf the web freely. My home domain is not (yet) blocked with the new filtering so Im good. Are there any instructions on how to accomplish this?


(sidenote: this is not my first post, just my first post in a long time and they seem to have deleted my old account)

---

### Post by kanikilu on 2009-03-31
I haven't tried this, but here is a guide to tunneling traffic to your home server:

[http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/](http://ubuntu-tutorials.com/2008/06/18/tunnel-web-and-dns-traffic-over-ssh/)

By the way, I'm sure you don't need a lecture from me, but if your workplace has web filtering setup, they may not look too kindly at circumventing their restrictions. You may want to see what the consequences of doing so are before setting this up. If the worst they will do is block you, then I'd say go for it. If there is a risk of anything more severe, it's probably not worth it...

---

### Post by spades on 2009-03-31
thanks for the level-headed advice. Im the IT R&D guy...if stuff hits the fan I can chuck it up as "evaluating potential security breaches" :-)

I'll try the tunneling, I like the ssh proto :twisted:

---

### Post by kanikilu on 2009-03-31
> **spades said:**
> if stuff hits the fan I can chuck it up as "evaluating potential security breaches" :-) There you go 8-)

---

