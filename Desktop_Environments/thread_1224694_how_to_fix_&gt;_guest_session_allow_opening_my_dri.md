---
title: "how to fix &gt; guest session allow opening my drives ?"
date: 2009-07-27
forum: Desktop Environments
---

### Post by Wanas on 2009-07-27
I use guest session to let others use my computer without opening my personal data on my drives, it was working okay on ubuntu 9.04 till one day when I open the guest session I see my drives mounted on the desktop and allowed to be opened :(, I tried to make unprivileged user the same problem accure :( 

Is there a way to make the guest session works like before ?

---

### Post by komputes on 2009-07-27
Not sure if this will work but you can try System > Administration > Authorizations

In here there are a few things where you can set yourself as the only user to preform these actions. These policies can be found under:

org > freedesktop > hal > storage

- Mount file systems from internal/removable drives


Besides this I think another thing you can do is make these drives ext2/3/4 and setup the permissions so that only you can see the content.

---

### Post by Wanas on 2009-07-27
thanks for replaying 
but I didnt find what I was looking for 
is there any other suggestions ?
is there a way to delete config files to restore it to the default ?

---

### Post by Wanas on 2009-07-28
any other suggestions plzz?

---

### Post by Wanas on 2009-07-29
...... help please

---

### Post by Wanas on 2009-08-05
any suggestions plz

---

