---
title: "memory upgrade and swap"
date: 2006-07-18
forum: Desktop Environments
---

### Post by brownrl on 2006-07-18
Howdy,

I have added memory to my machine...

Should I change the main partition and swap size to be 3x the new memory size?

What about a server edition install?

Both machines have recieved more memory. Wonder if I should use gparted to change the partitions and swap to be 3x the memory?

Thanks in advance.

-- Rob

---

### Post by mrbaz on 2006-07-18
Ubuntu handles memory a lot different (but in a very good way) than windows.

The more RAM you have, the less likely Ubuntu is even going to use teh swap file.  

Ubuntu will only use your swap file if it has run out of system RAM to use.

I have 1.5GB of ram in mine, and I've never seen teh swap file ever being used, even with a ton of stuff running.

---

### Post by brownrl on 2006-07-18
Ok good call for the desktop to take the swap out. Now got 2gb in the desktop.

However, in the server I have 1.5gb but would apache, mysql, postfix etc... in a high traffic evironment need some swap? 

Since upgrading I too have yet to see the swap be used. I don't want to cross the bridge of having to repartition after I have put this thing in the data center can no longer put in the nice Live CD.

Thanks for the help.

---

