---
title: "Transferring GPG key"
date: 2009-05-06
forum: General Help
---

### Post by dr_pressure on 2009-05-06
Hey folks,

Recently got a new laptop and I'm trying to transfer my gpg key over. However I only copied the secret key and now I've lost the public key and the trustdb.

What I want to do is:
new$ gpg --import public.asc private.asc
new$ gpg --import-ownertrust trustdb

Now I can probably get the public key off the keyserver. But what should I do about the trustdb. Am I screwed?!

-Pressure

---

### Post by kryptikos on 2009-05-06
Getting your public key back is fairly easy with gpg, you could pull the pub key down from a keyserver, but gpg has a method to pull and create your pub key again from your private key...

>  I still have my secret key, but lost my public key. What can I do?

All OpenPGP secret keys have a copy of the public key inside them, and in a worst-case scenario, you can create yourself a new public key using the secret key.

A tool to convert a secret key into a public one has been included (it's actually a new option for gpgsplit) and is available with GnuPG versions 1.2.1 or later (or can be found in CVS). It works like this:

[QUOTE]$ gpgsplit --no-split --secret-to-public secret.gpg >publickey.gpg

One should first try to export the secret key and convert just this one. Using the entire secret keyring should work too. After this has been done, the publickey.gpg file can be imported into GnuPG as usual. [/QUOTE]

As far as the trustdb I'd just let gpg recreate it once you have your private key established again.

---

### Post by dr_pressure on 2009-05-06
Hi, thanks for replying.

My main issue is how to mark my private key as ultimately trusted / owned by me. I assume that information is stored in trustdb?

It works for signing stuff, but when I try to encrypt stuff to myself it warns that the key is not trusted.

---

### Post by kryptikos on 2009-05-06
You should be able to run gpg --edit and then type "trust" when prompted and choose "trust this key fully". 

Not sure if that is what you are looking for.

---

### Post by dr_pressure on 2009-05-06
That's exactly what I needed. Thanks very much!!

---

### Post by kryptikos on 2009-05-07
Happy to help :)Glad it worked for you....

---

