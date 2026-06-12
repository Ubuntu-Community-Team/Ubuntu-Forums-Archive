---
title: "BASH Tab Backtick Completion Disabled by Default?"
date: 2009-05-27
forum: General Help
---

### Post by snesreviews on 2009-05-27
Hi Guys,

I was just wondering why the packaged version of bash comes compiled in a way which disables backtick command completion? It's one of the strangest things I had to get used to when I went FreeBSD -> Ubuntu. I assume it's a compile time thing because when I downloaded and compiled my own bash install, using the same profiles, it worked fine. This is the behaviour I'm talking about:


ls `pwd`/
<tab> -> dynamically changes the command line to:
ls /current/working/directory/

I finally have a workaround now after searching for ages to see if there was some obscure bash configuration or script required to enable this. Hopefully this post will save some people the hassle in the future...

---

