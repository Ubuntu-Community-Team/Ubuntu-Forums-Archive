---
title: "Chromium 64 bit browser issues"
date: 2009-05-24
forum: General Help
---

### Post by afrodeity on 2009-05-24
```
afrodeity@afrodeity-desktop:~$ chromium-browser
chromium-browser: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

I see this quite a lot because of the 64bit hell that I live in, anyway, I was wondering if there was an easy and understandable workaround for the chromium-browser?

I have tried to make head or tail of the advice on [Ubuntu wiki]("https://wiki.ubuntu.com/Chromium/Build") but it assumes lots of prior knowledge and can't understand it. Anywone with a better shot, better solution?

---

### Post by Vadi on 2009-05-24
Need to install from the chromium ppa. then it'll install the 32bit stuff it needs.

---

### Post by utnubuuser on 2009-05-24
Totally off-topic here, but for your information...

Who gets advertising revenue if you use Chrome?

That little Google bar in your Firefox browser means advertising revenue for Mozilla.

---

### Post by Vadi on 2009-05-24
I don't see a search bar in chrome to begin with.

---

### Post by paradigm2 on 2009-05-24
> **utnubuuser said:**
> Totally off-topic here, but for your information...

Who gets advertising revenue if you use Chrome?

That little Google bar in your Firefox browser means advertising revenue for Mozilla.

Chromium isn't Chrome.  Chrome is merely based off of Chromium and branded by Google.

---

### Post by utnubuuser on 2009-05-29
> Chromium isn't Chrome. Chrome is merely based off of Chromium and branded by Google. - Duly noted.  ...learn something new every day.  My Bad.  Thanks.

---

### Post by afrodeity on 2009-06-01
> **Vadi said:**
> Need to install from the chromium ppa. then it'll install the 32bit stuff it needs.

```
http://ppa.launchpad.net/chromium-daily/ppa/ubuntu
```

I have the above in my software sources, but still no working chromium.

What must I do, purge and start again or what?

---

