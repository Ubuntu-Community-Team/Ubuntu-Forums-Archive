---
title: "W3M internet browser installation"
date: 2009-01-29
forum: General Help
---

### Post by Admiral Yi on 2009-01-29
Hello,
Im trying to install the internet browser W3M. I have downloaded and extracted the tarball, then proceeded to try and install like a source. I use 'cd w3m' to move to the folder. When I run ./configure however, I get this:

```
configure: error: gc.h not found
```

Obviously i'm doing something wrong. I've not got much experience doing things like this, so don't really know what to do. Im assuming that im not installing it the right way. Anyone able to help?

---

### Post by ibutho on 2009-01-29
You are missing a required dependency. In your case, its libgc-dev which you can install using synaptic or by doing
```
sudo apt-get install libgc-dev
```

---

### Post by x33a on 2009-01-29
you can install it directly from the repos using

sudo apt-get install w3m

---

### Post by geirha on 2009-01-29
There's [w3m](apt:w3m) in the repositories. Any reason why you don't just install that one?

---

### Post by Admiral Yi on 2009-01-29
I downloaded 'libgc-dev' and got past that stage, but then got this error:

```
collect2: ld returned 1 exit status
make: *** [w3m] Error 1
```

I can't use synaptic to get it because it says I already have the newest version, which I am 100% sure I don't.

---

### Post by jerome1232 on 2009-01-29
w3m is installed by default my friend

```
w3m www.google.com
```

The verision on sourceforge is 0.5.2, the version in intrepid's repositories is 0.5.2

---

