---
title: "question: does filesystem cache slows down the performance when loading a program"
date: 2006-09-16
forum: Desktop Environments
---

### Post by robert114 on 2006-09-16
Hi everybody, I have a question on witch I couldn't find an answer on google.

I've just bought a new computer, an AMD 4600 X2 with an Nvidia motherboard with 1GB or RAM.  Now I didn't feel much performance improvements after the upgrade from my old machine, an AMD 2200. Still the hard disk speed has improved big time so does the Memory and CPU speed.

The overall performance has increased but the load times of lets say Firefox and OpenOffice is still a bit slow. Now, I do believe this is due to the fact that my memory is always full of cache so when I start OpenOffice the system should first free the cached pages from the memory before it is able to load the new program into the system. This causes a delay am I right?

Now my question is: Is there a way to limit the amount of caching and keep some memory free so programs load faster?
After a few hours of googling I have came to the conclusion that chache is a good thing however I think that a filesystem cache of more than 2/3 is a little bit to much.

A second question: since my computer is caching so much into its memory will the speed of loading applications being inproved when I add more memory.
I didn't notice a big improvement after I upgraded my old machine from 700 MB to 1500 because even than I did have a few MB's free

---

### Post by lagagnon on 2006-09-16
> **robert114 said:**
> The overall performance has increased but the load times of lets say Firefox and OpenOffice is still a bit slow.

Firefox and OO are two of the largest memory hogging programs in the Open Source world. There is not too much you can do about that. However, once they are loaded up the first time their libraries are cached so if you have to close and reopen them again the load time becomes much faster.

If it still bothers you the only answer I know of is to change to lighterweight programs (ie Dillo, AbiWord, Gnumeric). I think Opera and SeaMonkey load slightly faster than Firefox.
> 
 Now, I do believe this is due to the fact that my memory is always full of cache so when I start OpenOffice the system should first free the cached pages from the memory before it is able to load the new program into the system. This causes a delay am I right?

No. You have MORE than enough RAM to handle both Firefox, OO and many other programs all loaded at the same time.
> Now my question is: Is there a way to limit the amount of caching and keep some memory free so programs load faster?
See above. You have more RAM than you already need I suspect. Use the "free" command from a terminal to see what I mean. If you are not using any swap memory (and I bet you aren't) then there is not much more you can do to improve system speed.

---

