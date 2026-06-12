---
title: "Running google talk in ubuntu"
date: 2010-08-12
forum: Desktop Environments
---

### Post by rahul_cse25 on 2010-08-12
I have a laptop which is dual booted with ubuntu 10.4 and Vista.I have Google talk installed in Windows Vista through which i chat with my friends.Is it possible that i can use google talk in ubuntu as well,because whenever i want to chat with my friends i have to log off ubuntu and log into windows vista.

---

### Post by skarme on 2010-08-12
> **rahul_cse25 said:**
> I have a laptop which is dual booted with ubuntu 10.4 and Vista.I have Google talk installed in Windows Vista through which i chat with my friends.Is it possible that i can use google talk in ubuntu as well,because whenever i want to chat with my friends i have to log off ubuntu and log into windows vista.
Why not use Empathy or Pidgin to chat.
Google talk can be installed on Ubuntu though.
First install Wine:
```
sudo apt-get install wine

```
Now run the setup and choose Wine as the application runner in case you are prompted for one.

---

### Post by BriceHulse on 2010-08-12
You can use Wine, but some programs run in Wine aren't able to access the internet. You could download the Crossover Linux demo to see if Google Talk works in it. If it does, you can buy a licence. Crossover is pretty much a more powerful Wine, in fact, it's actually based on Wine.

[http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

### Post by Zeike on 2010-08-12
> **rahul_cse25 said:**
> I have a laptop which is dual booted with ubuntu 10.4 and Vista.I have Google talk installed in Windows Vista through which i chat with my friends.Is it possible that i can use google talk in ubuntu as well,because whenever i want to chat with my friends i have to log off ubuntu and log into windows vista.

Both pidgin and empathy have built-in support for the google talk protocol.

---

### Post by Gaygerbil on 2010-08-12
Just use Empathy it's integrated into Ubuntu better than any other IM Client I've ever used and it'll take way less resources than using Wine to run Google Talk.

---

### Post by rahul_cse25 on 2011-01-16
Could you kindly let me know how can i use Empathy in ubuntu.I mean where will i find it.Do i have to download it,or shall i find it inbuilt.

---

