---
title: "useradd"
date: 2009-02-20
forum: General Help
---

### Post by miazma on 2009-02-20
Hello,

I have created a user with `useradd`, but I have no clue how to get a desktop file and so on in the home-directory (added it via SSH). So how do I get all the missing files:

```

lichtenberger@rusconi:~$ ls
Examples
lichtenberger@rusconi:~$

```

greetings,
Johannes

---

### Post by geirha on 2009-02-20
Don't use useradd, use adduser instead.

The Desktop directory should be created automatically when the user logs in (graphically) for the first time though.

---

### Post by miazma on 2009-02-20
And a way without graphically logging in? :-)

---

### Post by miazma on 2009-02-21
Mh no suggestions? I can login per SSH, but not locally until monday, and I would have to do something until then remotely :(

---

### Post by WaffleCode on 2009-02-21
If your not logging in graphically, why do you need a Desktop folder specifically?

Why can't you just use another folder?

Why can't you just *mkdir Desktop*?

---

### Post by adult swim on 2009-02-21
you could manually make folders in the new users home.
```
mkdir Videos Documents Music Pictures
```

---

### Post by geirha on 2009-02-21
You might want to have a look at [FreeNX](https://help.ubuntu.com/community/FreeNX). It allows you to login graphically over ssh.

---

