---
title: "Setting Google Chrome to open on startup opens two windows"
date: 2012-08-07
forum: Desktop Environments
---

### Post by Sir Wallsy on 2012-08-07
Evening.

I am running Lubuntu 12.04, I have set Google Chrome to open on startup by adding this line:

```
@/opt/google/chrome/google-chrome %U
```

to the bottom of /etc/xdg/lxsession/Lubuntu/autostart

However, when I login, TWO windows of Google Chrome load.

Any ideas on how to remedy this?

Thanks in advance,

Wallsy

---

### Post by vasa1 on 2012-08-07
> **Sir Wallsy said:**
> ...

I am running Lubuntu 12.04, I have set Google Chrome to open on startup ...
I don't know the answer to your question but why do you want Google Chrome to open on startup (other than for convenience)?

---

### Post by stanciugabriel on 2012-08-08
Did you checked Chrome's settings for pages on start-up?

---

### Post by Austin Texas on 2012-08-08
I just tried it and it worked for me.
I didn't edit /etc/xdg/lxsession/Lubuntu/autostart though.
I just opened the Startup Applications program, and added a launcher named Google Chrome with the command: /opt/google/chrome/google-chrome %U
You will notice there is no @ sign.

---

