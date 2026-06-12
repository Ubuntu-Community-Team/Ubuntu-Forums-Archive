---
title: "quickie: uptime displays 2 users?"
date: 2005-12-22
forum: General Help
---

### Post by KurtB on 2005-12-22
Hello,

probably no big deal, but can anyone tell me why the "uptime" command says that there are 2 users on my box?

And what are the figures after "load average" supposed to say?
```
 12:34:32 up  1:05,  2 users,  load average: 0.05, 0.12, 0.22

```

---

### Post by codejunkie on 2005-12-22
[QUOTE=KurtB]Hello,

probably no big deal, but can anyone tell me why the "uptime" command says that there are 2 users on my box?

And what are the figures after "load average" supposed to say?
```
 12:34:32 up  1:05,  2 users,  load average: 0.05, 0.12, 0.22

```[/QUOTE]
i don't know exactly why it's doing this but either, but i don't think it's any thng to worry about. mine says this also but if i check the currently active users with 
```
sudo users
``` it only shows me logged in twice so im thinking that it's maybe counting me logged into the gui and to a tty/terminal.

---

### Post by KurtB on 2005-12-22
>  it only shows me logged in twice so im thinking that it's maybe counting me logged into the gui and to a tty/terminal.

Now you mention this, it could be it. Anyway it sounds very plausible...

---

