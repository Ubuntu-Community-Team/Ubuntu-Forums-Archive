---
title: "Will I still need XGL Server when I upgrade to Gutsy?"
date: 2007-10-08
forum: Desktop Effects &amp; Customization
---

### Post by Afkpuz on 2007-10-08
I am curious as to whether compiz is going to work for me out of the box when I upgrade to gutsy.  I currently have to use a XGL session to get compiz to work.  Is gutsy going to automatically realize this and set up XGL for me?  I don't understand much about XGL, but will it ever be possible to use the default X server and still run compiz?

---

### Post by FuturePilot on 2007-10-08
What graphics card do you have? If you absolutely need XGL, you will still have to set it up yourself in Gutsy.

---

### Post by Forlong on 2007-10-09
> **FuturePilot said:**
> If you absolutely need XGL, you will still have to set it up yourself in Gutsy.
No (s)he doesn't. See the last screenshot in the "Possible problems for ATI users" section [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710).

> **Afkpuz said:**
> will it ever be possible to use the default X server and still run compiz?
Depends on what you consider "the default X server".
Ubuntu has AIGLX implemented by default  - that will hopefully work *soon* with the fglrx driver.

But with Gutsy, you don't need to log into a separate session. It's still Xgl, though.

---

### Post by Forlong on 2007-10-09
> **FuturePilot said:**
> If you absolutely need XGL, you will still have to set it up yourself in Gutsy.
No (s)he doesn't. See the last screenshot in the P*ossible problems for ATI users* section [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710).

> **Afkpuz said:**
> will it ever be possible to use the default X server and still run compiz?
Depends on what you consider "the default X server".
Ubuntu has AIGLX implemented by default  - that will hopefully work soon with the fglrx driver.

But with Gutsy, you don't need to log into a separate session when installing xserver-xgl. It's still Xgl, though.

---

### Post by FuturePilot on 2007-10-09
> **Forlong said:**
> No (s)he doesn't. See the last screenshot in the P*ossible problems for ATI users* section [here](http://forlong.blogage.de/article/2007/10/2/Desktop-effects-by-default-in-Gutsy---how-Compiz-Fusion-enhances-Ubuntus-desktop-of-version-710).

Interesting. I didn't know about that. But what I meant was that you will still have to install XGL. It's not going to automatically install itself

---

