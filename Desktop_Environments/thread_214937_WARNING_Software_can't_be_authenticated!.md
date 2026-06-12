---
title: "WARNING: Software can't be authenticated!"
date: 2006-07-13
forum: Desktop Environments
---

### Post by lonelypauly on 2006-07-13
I was installing updates this morning and came across the following message...should I be concerned?

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/Screenshot.jpg[/IMG]

---

### Post by Rackerz on 2006-07-13
Not at all. I get that problem all the time, it just happens. Nothing to worry about, as long as you want to install the packages shown then there in nothing to worry about.

---

### Post by lonelypauly on 2006-07-13
hmmm, i dont think one person telling me not to worry is enough...at least, i would like to hear some reasons WHY i shouldn't be concerned.

---

### Post by cbudden on 2006-07-13
> **lonelypauly said:**
> hmmm, i dont think one person telling me not to worry is enough...at least, i would like to hear some reasons WHY i shouldn't be concerned.

It happens.  That's it.

---

### Post by bbarrons on 2006-07-13
I believe that it happens when you are installing or upgrading from a source other than the safe ubuntu repositories.....  I do not see this warning all the time.
Bill

---

### Post by cptnapalm on 2006-07-13
This has to do with the encrypted keys.  For the Ubuntu repositories, you have the signed key.  For the other repositories, however, unless you go get and install the public key, that warning pops up.

Functionally, it is like (I think) going to an insecure webpage after being on a secure one.  The warning is just telling you that the program cannot verify that the repository is what it says that it is.  As long as you don't have the key installed, it will pop up the warning.

I hope that made sense...

---

### Post by PriceChild on 2006-07-13
Yeah, basically if you install the public keys, then you can be sure that what you're downloading, hasn't been tampered with, and is from the original source unchanged.

Doubt anyone's gonna want to compromise you though :P

---

### Post by Ramses de Norre on 2006-07-13
I get this with wine all the time.. I don't know the GPG key and I haven't searched for it yet. As long as you keep an eye on your sources.list and only put trusted sources in there, all should be fine.

---

### Post by lonelypauly on 2006-07-13
ok, fair enough...but now i have more questions...

1.  why wouldn't a more appropriate message appear relating to the repositories being public, etc?

2.  how long before joe-uber-haxxor takes advantage of the fact that this message is largely ignored?  could said uber-haxxor possibly hijack or emulate an ubuntu update server in order to unleash his/her favorite linux exploit en masse?

i realize that i dont understand how this works exactly.  i would like to know, however. before you get all fussy about my questions, take a deep breath, calm yourself, and remember that i am not an uber-linux user like you, so please, go easy on me.

---

### Post by cptnapalm on 2006-07-13
I was initially going to assuage your concerns, but actually you are right about something important: Warnings should not be so common that they are disregarded.

I think that it would be a very good idea if a public key was made for the other repositories so  that no warning pops up *because* it has been authenticated.

---

### Post by Charles Hand on 2006-07-19
I get the NOT AUTHENTICATED warning no matter what I install. I just installed GCC straight out of the Ubuntu repository. If GCC out of the Ubuntu repository is not authenticated, what is the point of this whole authentication business?

---

