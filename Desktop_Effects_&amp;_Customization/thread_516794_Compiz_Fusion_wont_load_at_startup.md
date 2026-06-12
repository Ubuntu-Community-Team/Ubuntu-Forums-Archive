---
title: "Compiz Fusion wont load at startup"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by Malice007 on 2007-08-03
I just installed Compiz Fusion to my computer and was wondering how I would make it load every time when I turn on my laptop, without doing it in terminal all the time?

---

### Post by atomkarinca on 2007-08-03
system > preferences > sessions > startup programs > new

type "compiz --replace" in the command section and name it whatever you like.

---

### Post by bruckwine on 2007-08-05
I was just about to ask that - thanks!

---

### Post by walkerk on 2007-08-05
also.. if you are using emerald to decorate windows:
```
compiz --replace -c emerald &
```

---

### Post by ljkwesi on 2007-08-17
Thanks for the tip... but I have an extra question...

From what I understood (correct me if I'm wrong), loading compiz with "compiz --replace" closes metacity and loads compiz's own window manager... so it's basically a waste of time to have metacity load at startup to be immediately replaced by compiz... 
Isn't there any way to have compiz and it's window manager load directly, without launching metacity ?

---

### Post by canadiangg on 2007-08-17
I've tried putting those commands
compiz --replace
emerald --replace 
in the session manager but they still don't load at startup and I continually have to alt - F2 when I reboot.
Not that I have to reboot often .. it just would be nice to have it stick and load at startup.

I'm running 64
any other ideas?

---

### Post by cwgannon on 2007-11-27
> **walkerk said:**
> also.. if you are using emerald to decorate windows:
```
compiz --replace -c emerald &
```

Thanks walkerk.

That command fixed several issues I've been having, e.g., above/below rules not working, but I had to remove the ampersand (&) to make it work in my Sessions window.  Not sure if/how it works for you as such (or for me), but if others have this problem, this may be helpful.

---

