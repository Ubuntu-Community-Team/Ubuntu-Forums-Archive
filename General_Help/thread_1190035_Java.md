---
title: "Java?"
date: 2009-06-17
forum: General Help
---

### Post by Monotoko on 2009-06-17
Hiya guys, my friend has downloaded the ubuntu-restricted-extras packagae for her netbook (running ubuntu netbook remix)

but it didnt come with Java, and she needs it, anyone know how i can get it for her?

Since im not running ubuntu at the moment (laptop broke) im not sure how to do it XD

cheers :)

---

### Post by prem1er on 2009-06-17
```
sudo apt-get install sun-java6-jre
```

This is the runtime environment.  If you are trying to develop in java you will need.

```
sudo apt-get install sun-java6-jdk
```

---

### Post by martin_legion on 2009-06-17
Maybe you just need the java-plugin:
```
sudo aptitude install sun-java-plugin
```

Good luck

---

### Post by Monotoko on 2009-06-17
Thanks guys, il get that to her and see what happens :)

---

### Post by Monotoko on 2009-06-17
Okay, we did

```
sudo apt-get install sun-java6-jre
```

but it didnt do anything...so next we tried:

```
sudo aptitude install sun-java-plugin
```

it said Java was not installed....


So then i thought "wait...isnt it supposed to be in the restricted extras package" (which i told her to install a few weeks ago for flash)

So we purged all the ones we'd installed, then purged the restricted extra's packagae and reinstalled it....Java still wont work.....does it not work on the netbook remix??

---

### Post by Hobgoblin on 2009-06-17
> **Monotoko said:**
> 

```
sudo aptitude install sun-java-plugin
```

it said Java was not installed....



Because it's **sun-java6-plugin**

Might be easier to use the package manager GUI, which will prompt to enable multiverse repositories which are required.

---

### Post by hannah2312 on 2009-06-17
(I forgot about these forums)
Ahh still doesn't work... is there any other java things (i'm great with the technical words me) that I could try? I don't see how it would help any but it's runescape i'm trying to go on. thankyou =)

---

### Post by Java Geek on 2009-06-17
> **hannah2312 said:**
> (I forgot about these forums)
Ahh still doesn't work... is there any other java things (i'm great with the technical words me) that I could try? I don't see how it would help any but it's runescape i'm trying to go on. thankyou =)

Runescape has been proven that it doesn't work yet with 9.04, which is a bummer, but I'm hoping the developers will fix it soon enough

---

### Post by Monotoko on 2009-06-17
We solved it, cheers guys, had to purge everything then reinstall :)

(and RS is working!)

---

