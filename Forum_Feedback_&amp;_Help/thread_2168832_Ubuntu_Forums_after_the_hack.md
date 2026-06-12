---
title: "Ubuntu Forums after the hack"
date: 2013-08-19
forum: Forum Feedback &amp; Help
---

### Post by hg-knight on 2013-08-19
Since the hacking of this site, I log into forum via Ubuntu one.
If I am using Firefox browser then I have no problem logging in.
If I use Opera on my netbook or desktop or laptop, I log into forum via Ubuntu One , redirects me to the Forum home screen, but I have to log in again.
No matter how many times I try it repeatedly comes up with "login with SSO"
Its the same Using Ubuntu on laptop.Elementary on netbook.Windows on desktop.
I guess its an Opera problem but has anyone else had this problem or managed to fix it.
Not a major problem although I would prefer to use Opera on my netbook as its lighter than Firefox

---

### Post by stinkeye on 2013-08-19
Opera works fine here.
Check your settings for redirection in preferences > advanced > network
and cookie settings in preferences > advanced > cookies

Are you using any extensions?

You can test with default opera settings by
creating a folder in your home directory called **operatemp**.
In the terminal run...
```
mkdir ~/operatemp
```
...then...
```
opera --pd ~/operatemp
```

This will start a fresh instance of opera with default settings using **~/operatemp** as your personal directory
instead of the normal **~/.opera**
What you change in opera while running with a different personal directory does not affect your normal opera settings.

When finished testing, just delete the **~/operatemp** folder
and start opera as you normally would.

---

### Post by hg-knight on 2013-08-19
cheers for the reply.
have just updated  midori as per the elementary update and i think i will uninstall opera as midori is just as good if not better.

---

### Post by stinkeye on 2013-08-19
> **hg-knight said:**
> cheers for the reply.
have just updated  midori as per the elementary update and i think i will uninstall opera as midori is just as good if not better.
Fair enough.
Guess you don't use opera's mail client which is the reason I've stuck with it.

---

### Post by sandyd on 2013-08-19
moved to forum feedback & help

---

### Post by Frogs Hair on 2013-08-19
FYI , The Opera mail client is a separate program starting with Opera 15 , but there are no Linux builds for the mail client or the browser  yet.

---

### Post by Buntu Bunny on 2013-08-21
> **hg-knight said:**
> Since the hacking of this site, I log into forum via Ubuntu one.
If I am using Firefox browser then I have no problem logging in.
If I use Opera on my netbook or desktop or laptop, I log into forum via Ubuntu One , redirects me to the Forum home screen, but I have to log in again.
No matter how many times I try it repeatedly comes up with "login with SSO"

I'm having the same problem with Opera. No problem with Firefox, but with Opera I seem to be logged in ("Thank you for logging in, Buntu Bunny") but when I'm redirected back to the Forum, I'm not logged in.

---

### Post by cariboo on 2013-08-21
I had to change the title, as the three times I've seen this thread, I thought it was about someone having one of their posts hacked.

---

### Post by carl4926 on 2013-08-22
I have this login issue when using chromium in openSUSE
Additionally if  I use that browser here to post, the message formatting is messed up

---

### Post by coffeecat on 2013-08-22
> **carl4926 said:**
> I have this login issue when using chromium in openSUSE
Additionally if  I use that browser here to post, the message formatting is messed up

Nothing constructive to add at the moment, except that I'm posting from chromium in Ubuntu (Version 28.0.1500.71 Ubuntu 13.04 (28.0.1500.71-0ubuntu1.13.04.1), after logging in without incident. I'll try a few differently formatted with BBCode bits of text:

[size=3]Large-ish text.[/size]

[color=blue]Blue text.[/color]

[center]Centred text.[/center]

> Test quote

...and:

```
test code
```

---

