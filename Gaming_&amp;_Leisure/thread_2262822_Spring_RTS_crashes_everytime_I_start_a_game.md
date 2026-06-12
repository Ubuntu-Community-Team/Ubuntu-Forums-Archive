---
title: "Spring RTS crashes everytime I start a game"
date: 2015-01-27
forum: Gaming &amp; Leisure
---

### Post by %(gej%) on 2015-01-27
I installed Spring RTS using the following PPA.
```
sudo add-apt-repository ppa:spring
sudo apt-get update
sudo apt-get install spring springlobby
```

I downloaded several games & maps, but when I start a game it crashes, everytime. I get this error message.
> 
Spring has crashed:
Segmentation fault (SIGSEGV)

:confused: How can I fix this?

---

### Post by oldrocker99 on 2015-01-28
That error usually is traceable to a video driver problem. Post results of
```
lspci | grep VGA
```

We may be able to help you, but more information is needed.

---

### Post by %(gej%) on 2015-01-29
```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
```

BTW, I found [this]("http://springrts.com/phpbb/viewtopic.php?f=11&t=32959") in Spring RTS Forums & it's the exact problem I'm having. According to it my graphics card is not sufficient enough to play Spring.

---

