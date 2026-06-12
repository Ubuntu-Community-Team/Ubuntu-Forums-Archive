---
title: "Sync &amp; Explore a Nokia 6630"
date: 2007-03-18
forum: Desktop Environments
---

### Post by brunomiguel on 2007-03-18
Hi, I have a Nokia 6630 and I want to sync it with Ubuntu Edgy. Also, I want to be able to explore de phones' memcard and internal memory, because I have several photos there.
I already read some how/to and tutorials, but I can't manage to do it.

Can you please help me?

Thanks in advance!!

---

### Post by airtonix on 2007-03-18
could you post urls to the tutorials you found?

would be good help...otherwise you could try (and i dont recomend this with a garuntee that it will work or that you wont get visits from a middle aged inner-city tooth-fairy)
...you could try using the cat command on some of the block devices under the dev directory : 

```
sudo ls /dev/ 
```

- examine the result to be aware of current state
- now plugin in phone to usb port(or is it bluetooth?)
- repeat listing to reveal any new block devices.
```
sudo ls /dev/
```


if you see new directories then they are most probably representing the phone. try using the cat command on the folder see if something funky happens : 

```
sudo cat /dev/blah/blah

```

thats all i can help you with.

---

### Post by brunomiguel on 2007-03-18
I found th tutorials here in ubuntuforums.
I was able to detect my phone with kmobiletools and wammu, but I can't sync it because this apps don't support this yet.

I also want to access my phone memcard and internal memory, but I cant seem to do it.

bwt, I'm a linux n00b.

---

### Post by brunomiguel on 2007-03-19
Anyone knows how to do it? I really need to know how to do it. It's important for me to sync my contacts, calendar, acess my memory card, and so on.

---

### Post by amonsul on 2007-03-27
No chance, i have a 6630 too, no chance... :(

---

