---
title: "Compiz problems"
date: 2006-12-21
forum: Desktop Environments
---

### Post by huviduc on 2006-12-21
i just installed compiz on my laptop, i have direct rendering enabled on my ATI 200m and i read that it is compatible. but when i started compiz, i lose all of my minimize, close, title bar, and window moving capabilities. I read that i need to turn on the window decorator, but it gives me this error:
root@huviduc-laptop:/home/huviduc# $ gtk-window-decorator --replace &
[1] 6591
root@huviduc-laptop:/home/huviduc# bash: $: command not found


someone please help me figure this out

---

### Post by iamhugeinjapan on 2006-12-21
Back when I used Compiz  (I use Beryl now) the command was 

```
gnome-window-decorator
```

Try that instead? You'll probably have to put it in your Startup preferences if it works.

---

### Post by lupine_nickt on 2006-12-22
When a command has $ at the beginning of it, it signifies that it should be run as a normal user (# shows it should be as the root user).

So yeah, copying the $ isn't a good idea :p

xF,

...Nick

---

### Post by d-E-a-D on 2006-12-22
lupine_nickt lol you're right...
I have the same issue with ATI 200M and Compiz! Beryl worked just fine but compiz don't and i don't like very much beryl... 
If you manage to work with please report!
Cumps

---

