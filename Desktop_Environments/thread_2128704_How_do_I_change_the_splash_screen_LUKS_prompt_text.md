---
title: "How do I change the splash screen LUKS prompt text?"
date: 2013-03-24
forum: Desktop Environments
---

### Post by strid3r on 2013-03-24
I use LUKS to encrypt one of my partitions (I dual boot 4 gaming) and I used plymouth to change the splash screen to something cool :cool:
but when it asks me for my password, it has all of this garbled text that doesn't look too pleasing.

It says "Unlocking the disk /dev/disk/by/uuid/*****/blah/blah/blah/"
and it runs off the screen.

How do I change the text to just say "Enter Decryption Password"

---

### Post by strid3r on 2013-03-24
Okay, so I figured it out myself

Ran these commands:

```

cd /lib
grep -ir "unlocking the disk"

```

Which returned this file:
[SIZE=4]** /lib/cryptsetup/cryptdisks.functions**[/SIZE]

There are two instances of "Unlocking the disk" in that file, and I changed em both.

Worked like a charm!

---

### Post by strid3r on 2013-03-24
Okay, I found something

Ran these commands:

```

cd /lib
grep -ir "unlocking the disk"

```

Which returned this file: /lib/cryptsetup/cryptdisks.functions

There are two instances of "Unlocking the disk" in that file, and I changed em both.


Rebooted, same old stuff!

---

