---
title: "Usings docs downloaded from apt-get"
date: 2009-04-10
forum: General Help
---

### Post by kumoshk on 2009-04-10
How do I access the docs (for various programs) that I download through apt-get or the synaptic package manager?

Are there different programs for browsing them conveniently? I assume these docs aren't related to the man pages.

For instance, how do I access python2.4-doc after I download it? Where is it after I download it for that matter?

---

### Post by maheshasolkar on 2009-04-10
Specifically for python2.4-doc, you can try opening the following file in your browser, like so:

```
  firefox /usr/share/doc/python2.4/html/index.html
```

Or use the browser of your choice.

---

### Post by tjwoosta on 2009-04-10
im not really sure where ubuntu puts their docs but you could try looking in any of theese directories

/usr/doc, /usr/info, /usr/share/doc, and /usr/share/info


i dont use ubuntu myself, so if im wrong somebody please correct me

---

### Post by kumoshk on 2009-04-10
Thanks for the information! Now I know where to find them.

So, does anyone know of any utilities specifically designed for browsing what docs you have installed (so you can avoid all the packages that don't have docs installed)?

---

