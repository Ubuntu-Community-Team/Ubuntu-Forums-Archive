---
title: "Application and the terminal"
date: 2008-09-05
forum: Desktop Environments
---

### Post by patricksan on 2008-09-05
Dear All,

I've just installed TORA in my Ubuntu.

What happens is: I created a link in the PANEL, but when I click it does not open. I changed the type to Application Terminal, but it does not work also.

So, to run this application I always have to open the terminal and them write eg: "tora & ".


Do you have an idea why I have this problem?

Thank you,
Patrick

---

### Post by Rocket2DMn on 2008-09-05
I haven't seen this problem, but have you tried specifying the full path to the program in the launcher?  Probably /usr/bin/tora
```
whereis tora
```

---

### Post by patricksan on 2008-09-11
I saw that I have it in 3 places:
 /usr/bin/tora /usr/lib/tora /usr/share/tora

But I also used:
```
>which tora
/usr/bin/tora
```


I tried with all paths, but none of them work.
The only difference that could be is that I compile TORA myself to have support to Oracle.

Thank you,
Patrick

---

