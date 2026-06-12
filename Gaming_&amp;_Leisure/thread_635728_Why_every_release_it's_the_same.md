---
title: "Why every release it's the same ?"
date: 2007-12-09
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2007-12-09
Every new Ubuntu release some games that worked before no longer work.
Is it a library problems ?
How can we avoid it, so it won't be a never ending story ?

---

### Post by hikaricore on 2007-12-09
A lot of the new issues I've had are due to pulse audio and sdl sound not working properly.
Aside from that I couldn't run Gish due to the game linking to static libraries and the developer not updating their product.  I worked around this by installing the outdated version of the library as well.

But without any further info I can't even begin to understand what your troubles are.  :p

---

### Post by MaximB on 2007-12-09
It will be a hell to the developers to update their "compete" games to suite every new release.
There must be some way to make it work on any Linux version.
I'm not a programmer but I'm sure there must be some way to do it.

In windows they include all the libraries with their game, so you always have the libraries you need, Linux works in different way (superior in many ways but thats the Achilles hill).

---

### Post by yabbadabbadont on 2007-12-09
> **hikaricore said:**
> Aside from that I couldn't run Gish due to the game linking to static libraries and the developer not updating their product.  I worked around this by installing the outdated version of the library as well.

If the binary was statically linked, then it wouldn't *need* any libraries...  or did I just misread your post?

---

### Post by hikaricore on 2007-12-09
> **yabbadabbadont said:**
> If the binary was statically linked, then it wouldn't *need* any libraries...  or did I just misread your post?

Sorry I didn't make my post very clear.   The binary was pretty much locked to an exact version of the library, even mucking around making symlinks in *lib* didn't help.
I physically had to track down and install the older version of what it was looking for.  >.<

I didn't mean to confuse this concept with embedded libraries or anything.

(incase anyone stumbles upon this looking for the solution the problem was libssl heh)

---

### Post by yabbadabbadont on 2007-12-09
I figured it was something like that.  It was your use of the word, static, that threw me.  :D

---

### Post by MaximB on 2007-12-09
> **yabbadabbadont said:**
> I figured it was something like that.  It was your use of the word, static, that threw me.  :D

Sorry about the off topic question, but who are those pretty ladies in your avatar ?

---

### Post by yabbadabbadont on 2007-12-09
> **MaximB said:**
> Sorry about the off topic question, but who are those pretty ladies in your avatar ?

No problem.

[http://www.imdb.com/title/tt0348913/](http://www.imdb.com/title/tt0348913/)

---

### Post by hikaricore on 2007-12-09
/offtopic on

Death by falling toilet.  I always loved that.  ^_^

/offtopic off

---

### Post by MaximB on 2007-12-09
That's a discussion for another thread but that's makes me LOL :

Dead Like Me
Certification:
USA:TV-14 / UK:15 / Argentina:**13** / Australia:**M** / Ireland:18 (DVD rating) (season 1)  

Pffffffff....

---

### Post by cogadh on 2007-12-09
> **hikaricore said:**
> A lot of the new issues I've had are due to pulse audio and sdl sound not working properly.
That is exactly what drove me to switch to Kubuntu after sticking with Ubuntu for almost two years (longest I've ever stuck with a single distro). I really don't think Pulse was ready for prime time yet. Sure when it works it is fantastic, but getting it to work correctly and keeping it working with everything was a bitch. I'm sure future versions of it will be great, but for now I am perfectly happy with my clunky old aRTs and ALSA. I haven't had a problem with them working at all since the Kubuntu switch and I also haven't run into any of the "this app used to work now it doesn't" problems, but I may just be lucky that way.

---

