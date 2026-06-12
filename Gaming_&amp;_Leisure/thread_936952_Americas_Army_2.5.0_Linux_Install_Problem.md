---
title: "Americas Army 2.5.0 Linux Install Problem"
date: 2008-10-03
forum: Gaming &amp; Leisure
---

### Post by 69_Fury_96 on 2008-10-03
Ok guys, this is my first post here,
i downloaded americas army 2.5.0, and it installed well, but when i try to open it nothing happens, i tried to run it in terminal, but all i got was

```
ice@Blakes:~$ armyops
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ice@Blakes:~$ 

```
My Pc is more than capable enough to run AA, as i've played in windows since 1.9.0

But, i'm stumped. 
Thanks For The Help I Think I'll Get :)
~Fury.

---

### Post by melojo on 2008-10-03
> **69_Fury_96 said:**
> Ok guys, this is my first post here,
i downloaded americas army 2.5.0, and it installed well, but when i try to open it nothing happens, i tried to run it in terminal, but all i got was

```
ice@Blakes:~$ armyops
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
ice@Blakes:~$ 

```
My Pc is more than capable enough to run AA, as i've played in windows since 1.9.0

But, i'm stumped. 
Thanks For The Help I Think I'll Get :)
~Fury.

I think ubuntu hardy uses libstc++.so.6.0.9
type this in a console and see if this works, its just making a link and calling it libstdc++.so.5  like a shortcut for windows.

 sudo ln -s /usr/lib/libstdc++.so.6.0.9 /usr/lib/libstdc++.so.5

post if you get any errors

---

### Post by Perfect Storm on 2008-10-03
> **melojo said:**
> I think ubuntu hardy uses libstc++.so.6.0.9
type this in a console and see if this works, its just making a link and calling it libstdc++.so.5  like a shortcut for windows.

 sudo ln -s /usr/lib/libstdc++.so.6.0.9 /usr/lib/libstdc++.so.5

post if you get any errors

Don't do that. libstdc++5 is in synaptic package manager.

---

### Post by melojo on 2008-10-03
> **Artificial Intelligence said:**
> Don't do that. libstdc++5 is in synaptic package manager.


I couldn't find it.

---

### Post by Perfect Storm on 2008-10-03
> **melojo said:**
> I couldn't find it.

Just search for libstdc in synaptic. If it doesn't appear you have somehow disabled "universe" in the repo.

---

### Post by melojo on 2008-10-03
> **Artificial Intelligence said:**
> Just search for libstdc in synaptic. If it doesn't appear you have somehow disabled "universe" in the repo.

yea its there, don't know why I couldn't find it earlier.  I am installing AA now just to see if the link thing works.  I have done it in the past and it worked.

---

### Post by melojo on 2008-10-03
What I suggested does not work.

---

### Post by 69_Fury_96 on 2008-10-03
Thanks For your responses guys, Artificial Intelligence, yours worked like a charm. now i have to get good again XD

---

### Post by decades on 2008-11-13
it works, thanks.

---

### Post by JonnyM on 2008-11-14
If your having problems with getting Americas Army 2.5 up and running properly just use 2.5Deploy, It will sort everything out for you... [http://25deploy.co.uk](http://25deploy.co.uk)

---

