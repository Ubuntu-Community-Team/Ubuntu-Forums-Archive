---
title: "no synaptic package manager??? crap now what'd i do?!"
date: 2009-05-29
forum: General Help
---

### Post by r3l3ntl35 on 2009-05-29
im having a problem with opening my synaptic package manager. it will not open at all. i tried downloading frostwire and since then synaptic wont work, and frostwire doesnt even work so basically i got the shaft on both ends.... when i try 2 open synaptic, it reads this:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

im a total linux noob... what should i do? im using hardy heron... and also what would u guys reccomend i use for a music downloader?

---

### Post by abyrne on 2009-05-29
First of all, i'm really agaist limewire/frostwire, but I'm not here to judge.

Open up the terminal. Just search through your applications menu for it.
Run this command
```
sudo dpkg --configure -a
```
just copy it in to your terminal  and press enter. it will ask for your password. just enter it and press enter.
that should fix it

---

### Post by r3l3ntl35 on 2009-05-29
cool, i can actually open it now, but upon opening it tells me:

"You have 1 broken package on your system!

Use the "Broken" filter to locate it."

---What does this mean?

---

### Post by CatKiller on 2009-05-30
> **r3l3ntl35 said:**
> What does this mean?

It means that there's a package that can't be installed properly. In Synaptic, show the packages by status and there will be one in the Broken list.

---

### Post by r3l3ntl35 on 2009-05-30
i try to remove this package and it gives me this:

E: sun-java6-jre: Package is in a very bad inconsistent state - you should

---

### Post by jowilkin on 2009-05-30
Is that the whole message or did you mistakenly paste only part of it?

---

### Post by Elfy on 2009-05-30
Can you run these in a terminal and paste the outputs please

```
sudo apt-get install -f
sudo dpkg --configure -a
```

When you were trying to install did you see the java window - it needs the licence to be accepted.
> 
what would u guys reccomend i use for a music downloader?Depends what sort of music and where you're getting it from ...

---

