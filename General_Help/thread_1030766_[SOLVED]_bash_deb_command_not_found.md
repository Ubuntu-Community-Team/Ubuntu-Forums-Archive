---
title: "[SOLVED] bash: deb: command not found"
date: 2009-01-04
forum: General Help
---

### Post by BoxingTux on 2009-01-04
Hello everyone,

sorry to bother you, but what does that error message means (the one in the title).
I'm not at my first Ubuntu version (I've freshly installed Intrepid Ibex) and that's the first time I see this one (strange if you consider the fact that I used the deb command with success on previous versions).
Here are the details:
```
***@***:~$ deb http://debian.ettin.org/allacrost unstable main
bash: deb: command not found
```
The repository of course is not at blame.

P.S.: Sorry if my English isn't always correct. I don't live in an English-speaking country.

---

### Post by RealPSL on 2009-01-04
To my knowledge there is not "deb" command but it is a directive in the /etc/apt/sources.list file that lists your software repositories. e.g.

```
deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe

```

---

### Post by BoxingTux on 2009-01-04
It's nice to point out an error, but it does not help me in solving my probleme
(sorry for the sarcasm)

---

### Post by dragos240 on 2009-01-04
go to system > administration > Software sources > Third party software > add,  and paste the line you copied for example:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main
That should help. I got confused with the same thing!

---

### Post by bodhi.zazen on 2009-01-04
deb is not a command.

That looks like an entry you would add to your apt sources

/etc/apt/sources.list

Take care not to mix ubuntu and debian repositories (can cause breakage).

What is it you are trying to do ?

---

### Post by BoxingTux on 2009-01-04
Trying to install the Hero of Allacrost game from their custom repository

---

### Post by BoxingTux on 2009-01-04
> go to system > administration > Software sources > Third party software > add, and paste the line you copied
seems to be working.
Thanks a lot, I'll remember the trick.

---

### Post by dragos240 on 2009-01-04
> **BoxingTux said:**
> seems to be working.
Thanks a lot, I'll remember the trick.
No problem, i really had  the same issue so i looked it up. I'm happy i helped

---

### Post by PaulHuffman on 2009-06-14
When I tried adding the software source deb, I got The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Don't understand how to do the step about going to that link to get a key.

---

### Post by snova on 2009-06-14
> **PaulHuffman said:**
> When I tried adding the software source deb, I got The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

Don't understand how to do the step about going to that link to get a key.

It should still work, but the system used to verify the packages won't.

This looks pretty good at showing how to add the key: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

