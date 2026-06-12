---
title: "using wget without compromising password"
date: 2009-04-15
forum: General Help
---

### Post by d3dtn01 on 2009-04-15
I was thinking of using wget to backup my Google Sites pages, but then of course I thought about the fact that these pages require my google account authentication credentials. So, I see that you can pass a username and password with wget, but then I don't want my google password to be sent in the clear across the internet by wget. Is there are way to send encrypted username & password with wget?

---

### Post by JochenJung on 2009-04-16
If Google sites supports https, you should use this URL. In this case the URL is sent encrypted over the internet.

---

