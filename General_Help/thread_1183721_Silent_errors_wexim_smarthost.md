---
title: "Silent errors w/exim smarthost"
date: 2009-06-10
forum: General Help
---

### Post by atrus on 2009-06-10
I've been googling a bit, but i can't find an answer.

I'm using exim in a smarthost configuration, on a system with *no* local delivery. the smarthost configuration changed, and required a change in my exim configuration (specifically, authentication). However, since there's no local delivery, there was no way for exim to bounce a message back to me, to tell me something was wrong. Is it possible for exim to not tell local mail clients that a message is finished sending out until it's confirmed that it can get out to the smarthost?

Silently leaving messages in a queue it will never escape from is about the worst possible configuration -- and left me with no mail delivery for several days until I happened to realize what happened.

---

