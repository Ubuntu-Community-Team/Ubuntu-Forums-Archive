---
title: "Ubuntu Wireless won't start up and is very slow! Help!?"
date: 2010-11-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Gordaripper on 2010-11-02
So, I'm using a Dell Inspirion 1525, with a broadcom BCM4312 network controller card, and I have a driver working (Broadcom STA) However, my wifi is extremely slow when it does work, and will often DISCONNECT for NO REASON. Sometimes the driver will "Unactivate" its self. How can I make sure that my wifi ALWAY works at optimal speed and WILL NOT disconnect randomly? Also, I will sometimes not have a connection, and I'll look at the available ones and MY WIFI IS RIGHT THERE. :l Help? Thanks.:guitar:

---

### Post by SteveDee on 2010-11-03
> **Gordaripper said:**
> So, I'm using a Dell Inspirion 1525, with a broadcom BCM4312 network controller card, and I have a driver working (Broadcom STA) However, my wifi is extremely slow when it does work, and will often DISCONNECT for NO REASON. Sometimes the driver will "Unactivate" its self. How can I make sure that my wifi ALWAY works at optimal speed and WILL NOT disconnect randomly? Also, I will sometimes not have a connection, and I'll look at the available ones and MY WIFI IS RIGHT THERE. :l Help? Thanks.:guitar:

Start with the basics and check signal level & quality. Also look at the channel you and other local access points are using. You should select a channel that is as far away as possible from strong local access points.

In a terminal run:-
```

sudo iwlist scanning

```
...and repeat this several times as other local APs may not be on 24/7.
The "quality" figure is usually more important than signal level.

---

