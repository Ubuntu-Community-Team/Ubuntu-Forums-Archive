---
title: "Google Earth Proxy"
date: 2006-06-13
forum: Desktop Environments
---

### Post by cbonner on 2006-06-13
I have just installed the new beta version of Google Earth for Linux. Everything works fine apart from connecting to the google server.

I need to tell google earth to go through our proxy server. I have tried doing:

export http_proxy=[proxy address]

Like is says to do in the readme file, but this seems to have no effect.

Has anyone else got it working through a proxy yet, and what steps did they take?

Running a clean install of 6.06.

---

### Post by Lunar_Lamp on 2006-06-13
I haven't tried using google-earth yet, but just to check something.

When you do "export http_proxy..." if you just type it in a terminal, it will only be valid for that terminal.  If you want it to be valid for all programs, you need to add the line to the end of your bash profile:

sudo gedit ~/.bashrc

---

### Post by cbonner on 2006-06-13
Thanks, that works when I run it from a teminal.

---

