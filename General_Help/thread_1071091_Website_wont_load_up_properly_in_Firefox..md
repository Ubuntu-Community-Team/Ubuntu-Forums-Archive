---
title: "Website wont load up properly in Firefox."
date: 2009-02-15
forum: General Help
---

### Post by tigshadorakie on 2009-02-15
I am trying to get a website that I use for a community college to load up properly. It seems that I am just getting basic text and hyperlinks without any real web GUI. If I look at the error console I see that Firefox is is reporting this problem. There are several but they all say the same thing basically. 

[B]
Error: The stylesheet [https://webadvisor.camdencc.edu/WebAdvisor/stylesheets/themes/ORIGINAL/MenuStyle_BARS.css](https://webadvisor.camdencc.edu/WebAdvisor/stylesheets/themes/ORIGINAL/MenuStyle_BARS.css) was not loaded because its MIME type, "text/html", is not "text/css".[/B]

Any ideas? I really do not know what any of this means. Thank You

---

### Post by sumguy231 on 2009-02-15
It appears that the server is sending the wrong MIME type (file type) for the stylesheet, so Firefox can't render it and the page ends up looking wrong. Basically, this is a server-side error which probably depends on incorrect behavior in Internet Explorer to work.

If you have access to Internet Explorer in any way it would probably be easiest to use it for this. Options include using Windows in a virtual machine (if you have a spare copy laying around), using IEs4Linux (which uses WINE to install IE in Ubuntu), or just using a Windows machine you have access to. Also complaining to the people who are in charge of the page might help since it probably would be a fairly easy fix.

---

### Post by tigshadorakie on 2009-02-15
I am dual booted XP and Ubuntu so I have access to IE explorer. It is just annoying haveing to go into a different OS for something like that. How do you get the IE4Linux? Is there any security vulnerability using IE in Linux?

---

### Post by sumguy231 on 2009-02-16
According to the webpage, all you need to get it is install wine (from the repositories), and download, extract, and run it.

As far as security goes, you're unlikely to mess up anything other than your wine installation. By default wine gives apps access to your home folder but you can turn that off in the settings and most Windows malware is too stupid to touch your stuff anyway. If you mess something up you can just delete your .wine directory and start fresh.

---

### Post by tigshadorakie on 2009-02-24
thanks

---

