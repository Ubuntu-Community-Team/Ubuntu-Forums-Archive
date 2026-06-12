---
title: "How do i seach for hidden files?"
date: 2011-11-18
forum: Desktop Environments
---

### Post by Azyx on 2011-11-18
Hi.
I wonder how I can find hidden files? Normal seach do not find hidden files or folders :( 
I you what to totally remove an application, including configuration-files they do not allway disappear, probably cos configurationfiles placement in the home-folder have switched place.

---

### Post by Azyx on 2011-11-18
I find how :) There are an option in seach files you can add. /cheers

---

### Post by silviutp on 2011-11-18
You can mark your thread as 'Solved' if you got an answer, from Thread Tools Button. Cheers! :)

---

### Post by nixblog on 2011-11-18
From a terminal you can see all hidden files and directories in the current location by using the following,

```
ls -lad .*
```For example, if in your home directory, you can search for all bash config files

```
ls -lad .bash*
```

---

### Post by Azyx on 2011-11-18
> **silviutp said:**
> You can mark your thread as 'Solved' if you got an answer, from Thread Tools Button. Cheers! :)

I thought I have done it?

---

### Post by Azyx on 2011-11-18
> **nixblog said:**
> From a terminal you can see all hidden files and directories in the current location by using the following,

```
ls -lad .*
```For example, if in your home directory, you can search for all bash config files

```
ls -lad .bash*
```

This does not find files in folders I think (or files in dirictorys)? Recusively?

---

