---
title: "Endian ordering"
date: 2008-12-03
forum: General Help
---

### Post by sambarusty on 2008-12-03
I have a question about endian ordering. I know what it is and how to fix it from one machine to another, so please don't fill the thread with lessons on how to exchange the two. The question that I have is we are porting 3/4 mill sloc from Unix to a new Linux arch.  Without getting into detail the code is a combo of ADA(exciting) and C(even more exciting), along with a portion of C++, this doesn't include some perl scripts etc. So the unfortunate part is that we are going from HP_UX to Linux and the HP_UX is big endian, the Linux is little endian.  Once all the code is on the linux boxes, problem solved, but the issue is that in mean time we need to communicate from one machine to the next, almost a hundred processes in total, some multi-threaded.  How do people normally handle endian interfaces?  It can't possibly be by going through several hundred different types of messages and handling all of them individually right?  It's one of those things I think I can make it work, but it feels like I am making it too difficult.  Is there a better way?  I have some understanding that open mpi may help, but I believe you still need to spec all the messages.  Why does it seem like there is such a difficult answer to such an old problem. Is there some sort of middle ware available that just does this?  Let me know your thoughts.  I have spent several hours bit and byte flopping, and I don't what to do it anymore if I don't have to (I hate tedious busy work)?  I am really hopping that where is some magical answer, but I am guessing that there isn't. Remember the fun part about ADA is that there are repspecs, so these are all messed up also. Thanks for any exciting ideas which will help me move past this painfull experience.  HA HA .  By the way I am aware of the ada bit_order attribute, this A) only handles the ADA side, B) doesn't handle the problem, only the bits inside of a type, and C) is not supported by the compiler.  So I still need to fix byte order and bit order for packed data structures. Thanks in advance for any thing that will make my life in the near future easier.  And just as an FYI if you know of a solution that is not free but worth it, I would like to know that also. Since if it worth while, this is not a school project, it may be an option.  -Thanks

---

### Post by mdurham on 2008-12-03
Sorry I have no info for you but I'm just curios (and ignorant). What is endian about source code? It's just text isn't it?
Cheers, Mike

---

### Post by sambarusty on 2008-12-03
It's not the source code, it is the storage of the data.  So now when you send a buffer from one machine to the other, the data is interpreted incorrectly and you need to untangle the mess.  There has got to be some sort of standard for this, isn't there?   Thanks

---

### Post by mdurham on 2008-12-03
Oh I see what you mean, it's just that you mentioned C++. I don't see how you could sort out C++ data, who knows how it's stored? Maybe in structures containing bytes, strings, ints and floats etc all packed in together. Also maybe strings are stored using 16 bit chars, or maybe not!
I wish you luck with your task.
Cheers, Mike

---

### Post by mixmaster on 2008-12-03
Generally if you plan for this in advance you use a canonical representation of the data and have access methods for each data type.  When you compile the code the correct access method is pulled in depending on the target architecture.

Of course, this assumes you were planning the project to me multi-architectured from the start.  If you have just inherited a mass of code which simply writes binary data to disk without consideration of the underlying representation then you have a fairly long and tedious task in adapting it.  There may be some automated porting tools available but I've never used any.

---

### Post by sambarusty on 2008-12-03
> **mixmaster said:**
> Generally if you plan for this in advance you use a canonical representation of the data and have access methods for each data type.  When you compile the code the correct access method is pulled in depending on the target architecture.

Of course, this assumes you were planning the project to me multi-architectured from the start.  If you have just inherited a mass of code which simply writes binary data to disk without consideration of the underlying representation then you have a fairly long and tedious task in adapting it.  There may be some automated porting tools available but I've never used any.

True, but if you were planning ahead, it wouldn't really be porting, or trial porting(you already know where you were going), well I guess if you were planning for the unforeseeable, in this case, unfortunately I am getting the impression that the second part of your statement is very very true.  :(  However, the majority of the task is very enjoyable, you learn a lot.  Downside is the byte swapping busy work.

---

