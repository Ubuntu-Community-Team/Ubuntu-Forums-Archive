---
title: "One Last Thing Before I Install"
date: 2009-05-20
forum: General Help
---

### Post by The_Lost_World on 2009-05-20
Call me paranoid, but I'm here again to confirm one last issue before I go one with the install of Ubuntu 9.04 (I'm typing this from the Live CD boot).

I'm manually installing, by the way.

On this section of the installation process:

[IMG]http://i538.photobucket.com/albums/ff341/the_cake_is_a_lie/Screenshot.png[/IMG]

I should click the "New partition" button down there and create a 
"/", "/home", and "swap" partition, and then click "Forward", and it'll do the rest, right?

If I've got it wrong, please tell me. I'm excited to begin the install as soon as possible! ^_^

---

### Post by empty_spaces on 2009-05-20
Correct.
At the very least, you will need a root(/) partition and a Swap partition.
Usually swap partition is equal to the ram.
Having a separate /home partition is recommended, but its not absolutely necessary.

---

### Post by The_Lost_World on 2009-05-20
Thank you! Installing now. ^_^

---

### Post by The_Lost_World on 2009-05-20
WAIT!

Sorry.

It tells me to enter the size of partitions in megabytes. So should I consider 1000 megabytes to be 1 gigabyte when entering the number, or 1024?

---

### Post by RD1 on 2009-05-20
I always use 1024

---

### Post by The_Lost_World on 2009-05-20
Excellent, thanks.

---

### Post by empty_spaces on 2009-05-20
Not really sure, but how much difference would it make?
I have a feeling it might be 1024 though.

---

### Post by lisati on 2009-05-20
In "computer-speak", 1024 is common, but 1000 is "more correct"

---

### Post by The_Lost_World on 2009-05-20
I've used 1024. Clear to launch?:p

---

### Post by kdorf on 2009-05-20
> **lisati said:**
> In "computer-speak", 1024 is common, but 1000 is "more correct"

False. Everything a computer does is in binary at its most basic level. That's why there are exactly 8 bits in a byte, 1024 bytes in a kilobyte, etc.

Sometimes hard drive manufacturers like to report their sizes in base 10 though. Go figure.

---

### Post by lisati on 2009-05-20
> **kdorf said:**
> False. Everything a computer does is in binary at its most basic level. That's why there are exactly 8 bits in a byte, 1024 bytes in a kilobyte, etc.

Sometimes hard drive manufacturers like to report their sizes in base 10 though. Go figure.

Perhaps I should rephrase: binary-based numbering schemes (as used in computers) lend themselves to "1k=1024", even though the prefix "kilo" really means 1000.

(TV commercials which measure weights in "cageys" irritate me too, as do commercials which measure distance and speed in "kays" - but these irritations are better dealt with in other threads in the community cafe)

---

