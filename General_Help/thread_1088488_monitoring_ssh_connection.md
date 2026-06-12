---
title: "monitoring ssh connection"
date: 2009-03-06
forum: General Help
---

### Post by seng1978 on 2009-03-06
Hi

I have question
I got a ssh ubuntu server 8.04( did the sudo apt-get install openssh-server thing)

now I like to know how to check how many ppl or users r connected to my
 ssh server. 

Like my vino server, once i connect to my vino server it shows me on the top how many users r connected via vnc to my server.

Is it possible to look up the same thing just for ssh?


Thanks

---

### Post by brian_p on 2009-03-06
> **seng1978 said:**
> 

now I like to know how to check how many ppl or users r connected to my ssh server. 

```
man who
```

```
man last
```

---

### Post by albandy on 2009-03-06
finger

---

