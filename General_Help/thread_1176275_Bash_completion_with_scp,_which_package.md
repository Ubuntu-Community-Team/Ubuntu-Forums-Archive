---
title: "Bash completion with scp, which package?"
date: 2009-06-02
forum: General Help
---

### Post by tnek on 2009-06-02
It seems some have it: 
[URL="http://www.linuxquestions.org/questions/linux-general-1/tab-completion-with-scp-294593/"]http://www.linuxquestions.org/questions/linux-general-1/tab-completion-with-scp-294593/
[/URL]
I want it too, but I can't find which package it is in. Any suggestions?

---

### Post by regala on 2009-06-02
> **tnek said:**
> It seems some have it: 
[URL="http://www.linuxquestions.org/questions/linux-general-1/tab-completion-with-scp-294593/"]http://www.linuxquestions.org/questions/linux-general-1/tab-completion-with-scp-294593/
[/URL]
I want it too, but I can't find which package it is in. Any suggestions?


do you have a public/private RSA or DSA key to authenticate on ssh ?
this is a prerequisite. maybe this is the only thing you need.

br, mathieu

---

### Post by tnek on 2009-06-03
Yes I have passwordless login using keys, it still doesn't work. There is some other requirement. :-|

---

### Post by tnek on 2009-08-04
It turns out, when I added the custom port to my ssh config it started to work. So passwordless key + correct config to authenticate on a custom port (in my case) made it work for me.

---

