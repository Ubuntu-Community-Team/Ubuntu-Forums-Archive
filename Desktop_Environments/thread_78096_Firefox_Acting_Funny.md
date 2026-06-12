---
title: "Firefox Acting Funny"
date: 2005-10-17
forum: Desktop Environments
---

### Post by the_purulent on 2005-10-17
I have my default home page set to [www.google.com](www.google.com)
each time I load firefox however it is loading whatuseek Web search...
I can't figure out how to make it stop!! Really irratating.

---

### Post by the_purulent on 2005-10-18
bump!

---

### Post by bdash on 2005-10-18
I don't understand. Do you mean that your home page is supposed to be Google, but whatuseek is loaded instead?

Which Firefox extensions do you have?

---

### Post by GeneralZod on 2005-10-18
That's a weird (and slightly disturbing!) one :)

Firstly, make absolutely, 100% sure that your homepage is [http://www.google.com](http://www.google.com), with no spelling mistakes.

Secondly, open up a new tab and click the "Home" button, and see what happens.

Thirdly, open up a new tab and type [www.google.com](www.google.com) in the URL bar, click enter, and see what happens.

Fourthly, post the results of 

```

sudo cat /etc/hosts

```

---

### Post by flaming_monkey on 2005-10-18
I remember someone else having a similar problem with Firefox, that turned out to be a kind-of spy-ware installed by a dodgy extension

Try moving your Firefox preference folder then restarting firefox.

```
mv ~/.mozilla ~/.mozilla-backup
```

If the problem is solved then it was probably an extension thing.

---

### Post by Jonne on 2005-10-18
don't worry, it's not spyware ;).

You're probably using gDesklets, and you entered 'Firefox %U'. In reality, only 'Firefox' is needed, and the '%U' part gets sent as a command line option. This causes firefox to use the 'I'm feeling lucky' google search for the query '%U' (which results in that whatuseek site). Just strip the %U away, and you won't have that problem any more.

This is answered elsewhere on this forum. Just google for 'ubuntu whatuseek' to find some other posts about it.

---

### Post by the_purulent on 2005-10-18
I am running gdesklets, and I did notice the %U switch on the launcher, but I was unsure if it should be there or not.

I took that out and fixed it was!  I didn't add it there though, does gdesklets automaticlly change it?

---

### Post by Jonne on 2005-10-18
I'm not sure. I had to enter Firefox manually in my launcher, and I just copied the settings from the launcher in my top bar. I'm a Linux n00b myself, so I can't really tell why, where and when %U is needed. 

But google has saved me a lot of times lately. Ubuntu has a good community with al lot of n00bs like myself, and you can rest assured they encounter the exact same problems ;). I usually use 'ubuntu + issue I'm having' in my query, and the right answer comes out on top ;).

---

