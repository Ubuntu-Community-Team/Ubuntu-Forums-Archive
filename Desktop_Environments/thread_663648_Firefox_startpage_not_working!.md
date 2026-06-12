---
title: "Firefox startpage not working!"
date: 2008-01-10
forum: Desktop Environments
---

### Post by Syzygi on 2008-01-10
Hey!
I have a little problem with my startpage in Firefox..
It is set to go to [www.google.com](www.google.com),
though, it always ends up starting with opening up an
about:blank page.

When I open Firefox in the terminal, it works fine.
And also, I use Kiba-Dock, so maybe it has something to do with that..? 

Anyone out there able to help?? It's getting really annoying...

---

### Post by Margus81 on 2008-05-20
> **Syzygi said:**
> Hey!
I have a little problem with my startpage in Firefox..
It is set to go to [www.google.com](www.google.com),
though, it always ends up starting with opening up an
about:blank page.


Anyone out there able to help?? It's getting really annoying...

I have had the same problem.

A good trick is to default the software:

sudo debconf firefox

I also lost once my gnome-panel... My desktop was just empty, I could do nothing... 
In terminal I
sudo debconf gnome-panel

and it fixed it...
JUHUU!

PS
For any missing default packages:
sudo apt-get install ubuntu-desktop


greetings...

---

