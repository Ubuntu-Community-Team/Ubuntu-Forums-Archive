---
title: "Change the   Ubuntu login screen to kubuntu login screen"
date: 2010-06-07
forum: Desktop Environments
---

### Post by creative31 on 2010-06-07
Hi, how would I change the ubuntu login screen to the kubuntu login screen without deleting the ubuntut desktop environment.




P.S. also, how would I make the windows in the kubuntu envirement transparent.  thx

---

### Post by SlidingHorn on 2010-06-07
> **creative31 said:**
> Hi, how would I change the ubuntu login screen to the kubuntu login screen without deleting the ubuntut desktop environment.




P.S. also, how would I make the windows in the kubuntu envirement transparent.  thx

```
sudo dpkg-reconfigure gdm
```

Google is your friend: [http://www.google.com/search?client=ubuntu&channel=fs&q=gdm+to+kdm&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=gdm+to+kdm&ie=utf-8&oe=utf-8)

Regarding transparent windows: [http://www.google.com/search?hl=en&safe=off&pwst=1&&sa=X&ei=ynENTMqJKZPbnAe3u-3XAw&ved=0CBYQvwUoAQ&q=kde+transparent+windows&spell=1](http://www.google.com/search?hl=en&safe=off&pwst=1&&sa=X&ei=ynENTMqJKZPbnAe3u-3XAw&ved=0CBYQvwUoAQ&q=kde+transparent+windows&spell=1)

---

### Post by creative31 on 2010-06-07
I did that, but its still the ubuntu default login screen, I want the Kubuntu login screen, Thx

---

### Post by SlidingHorn on 2010-06-07
sorry bout that

```
sudo dpkg-reconfigure kdm
```

---

