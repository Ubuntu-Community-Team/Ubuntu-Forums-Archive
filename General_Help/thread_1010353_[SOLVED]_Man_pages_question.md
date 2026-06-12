---
title: "[SOLVED] Man pages question"
date: 2008-12-13
forum: General Help
---

### Post by ceclauson on 2008-12-13
Hi!

I'm trying to learn how to use man pages, and I recently ran into a problem.

I'm trying to find the man page for the C-language accept() function defined in socket.h.  But when I try "man accept" at the console, I got the man page for a different function of the same name.  How do I get the one I want?

(P.S., I know the page exists, because I found it online: [http://www.rt.com/man/accept.2.html]("http://www.rt.com/man/accept.2.html"))

---

### Post by jbrown96 on 2008-12-13
Sometimes there are more than one page for the same name. I was just doing a network project last week; the page you want is ```
man 2 accept
``` for other things try different numbers

---

### Post by iponeverything on 2008-12-13
man -k accept

---

### Post by ju2wheels on 2008-12-13
The man pages for GNU/Linux development functions typically has to be installed manually:

```

sudo apt-get install manpages-dev

```

Then doing one of the already suggested commands should give you what you want if there is an available man page.

---

### Post by snova on 2008-12-13
Development manpages are in 'manpages-dev'.

Also, manpages are arranged in several sections. Open the page for 'man' itself, there is a list a little ways down.

---

### Post by ceclauson on 2008-12-13
Thanks--I had to apt-get it, and now it's here :-)

---

