---
title: "No &quot;Network&quot; location in web browsers upload or download?"
date: 2010-06-15
forum: Desktop Environments
---

### Post by 3boxes on 2010-06-15
I use a shared drive through a router for several computers on my home network.

Nautilus shows "Network" in the places pane, and shared drives can be accessed.

However, in Opera and Firefox, the file browser that comes up (for instance if you right-click to save an image) does NOT show "Network" in Places.  

The same is true if you are trying to attach a file to an email in a web-based email program.  The file browser that comes up in Opera and Firefox does not show "Network" in Places.

How do I access shared (Network) drives from the file browser that pops up when you use a web broswer's upload or download?

I'm on 10.04

---

### Post by cwmccabe on 2012-06-12
> **3boxes said:**
> How do I access shared (Network) drives from the file browser that pops up when you use a web broswer's upload or download?


I have the same issue a couple years later, on Precise.  A work-around is the following:

[LIST=1]
[*]In the download dialog window, navigate to your home directory.
[*]Right-click and show hidden files.
[*]Enter into the .gvfs directory where you'll see your network drives and you're able to save your file.
[/LIST]

The same method works for uploads.

---

