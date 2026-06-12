---
title: "Black list of modules"
date: 2009-04-27
forum: General Help
---

### Post by zeroed on 2009-04-27
Hi,

I have noticed that file /etc/modprobe.d/blacklist is empty now.

Is it ok?

I used it to disable pc speaker. Should I still use it?

---

### Post by mcduck on 2009-04-27
Yes, you can still use it. It's just empty simply because there's nothing blacklisted. :)

---

### Post by zeroed on 2009-04-27
> **mcduck said:**
> Yes, you can still use it. It's just empty simply because there's nothing blacklisted. :)

thanks :)

---

### Post by kirsis on 2009-04-27
You can use it, but note that (as of Jaunty, as far as I know) modprobe issues a warning about files without .conf extension and, presumably, in the future it will ignore them. 

You might want to rename it to have a .conf extension. I also suggest you change the name of the file to something more descriptive, so you can easily see which file blacklists what (e.g. blacklist-pc_speaker.conf).

---

### Post by zeroed on 2009-04-27
> **kirsis said:**
> You can use it, but note that (as of Jaunty, as far as I know) modprobe issues a warning about files without .conf extension and, presumably, in the future it will ignore them. 

You might want to rename it to have a .conf extension. I also suggest you change the name of the file to something more descriptive, so you can easily see which file blacklists what (e.g. blacklist-pc_speaker.conf).


What are the requirements for file name? Should it start with blacklist- ?

---

### Post by rajeev1204 on 2009-04-27
> **kirsis said:**
> You can use it, but note that (as of Jaunty, as far as I know) modprobe issues a warning about files without .conf extension and, presumably, in the future it will ignore them. 

You might want to rename it to have a .conf extension. I also suggest you change the name of the file to something more descriptive, so you can easily see which file blacklists what (e.g. blacklist-pc_speaker.conf).


/etc/modules/blacklist is moved to /etc/modules/blacklist.conf.

But adding to the old file also works and i have blacklisted pcspkr in it.

---

### Post by kirsis on 2009-04-27
> **zeroed said:**
> What are the requirements for file name? Should it start with blacklist- ?

There are no requirements. It may become a requirement to have it end in '.conf' but at the moment it's not required (just recommended).

---

### Post by zeroed on 2009-04-27
Thanks to everybody.

I have found .conf file in my system. I have installed 9.04 from the scratch.

One quick question. What will be on system, upgraded from 8.10 to 9.04? Two files? One file? Renamed? Any conflicts?

---

