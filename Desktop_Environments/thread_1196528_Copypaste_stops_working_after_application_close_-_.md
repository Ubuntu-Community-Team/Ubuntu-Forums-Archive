---
title: "Copy/paste stops working after application close - bug?"
date: 2009-06-25
forum: Desktop Environments
---

### Post by patman0623 on 2009-06-25
Problem is exactly as title describes. After closing an application (e.g., Firefox), the clipboard is destroyed. Is that a bug that I should report at Launchpad? Or is this a "feature"

---

### Post by JEREMIAHBARLOW on 2010-04-27
I am having the same issue with Ubuntu 9.10.

I can Cut or Copy something, and **if I close the program** or application then the OS seems to forget or **looses the Clipboard data**.  

This sure seems like a bug,  Clipboard data needs to stay on the clipboard better.  I wonder if there is an advance clip-board tool that would even let you have multiple clipboards at the same time.

Now that would be cool. ... but until then we have to maintain both applications open until you Paste the data to the new application.

SO STUPID for sure.... or in other words ...  a BUG in the OS.
:confused:

---

### Post by luigi_mb on 2010-04-27
> **JEREMIAHBARLOW said:**
> I am having the same issue with Ubuntu 9.10.

I can Cut or Copy something, and **if I close the program** or application then the OS seems to forget or **looses the Clipboard data**.  

This sure seems like a bug,  Clipboard data needs to stay on the clipboard better.  I wonder if there is an advance clip-board tool that would even let you have multiple clipboards at the same time.

Now that would be cool. ... but until then we have to maintain both applications open until you Paste the data to the new application.

SO STUPID for sure.... or in other words ...  a BUG in the OS.
:confused:

It is not a bug, it is by design. 

/luigi

---

### Post by SnickerSnack on 2010-04-27
> **patman0623 said:**
> Problem is exactly as title describes. After closing an application (e.g., Firefox), the clipboard is destroyed. Is that a bug that I should report at Launchpad? Or is this a "feature"

Do you mean the middle-click buffer, or the Ctrl-C/Ctrl-V buffer?

---

### Post by Old *ix Geek on 2010-04-28
> **luigi_mb said:**
> It is not a bug, it is by design.Then it's a stupid design. IMHO, of course. :)

I like to do things FAST. So if I have an app open and I copy something that I'm going to paste into some other app, and I don't need the first app open any more, I CLOSE IT.  Boom. Closed. Done. It's just plain stupid to lose what I copied just because I closed the app. ](*,)

---

### Post by utnubuuser on 2010-04-28
> 
This sure seems like a bug, Clipboard data needs to stay on the clipboard better. I wonder if there is an advance clip-board tool that would even let you have multiple clipboards at the same time.


If I might point-out the obvious: There are "advanced" clipboard tools available. Eg: Klipper.
[http://sazeit.com/articles/klipper-in-ubuntu-gnome]("http://sazeit.com/articles/klipper-in-ubuntu-gnome")
Install through Synaptic, or with > sudo apt-get install klipper then add it to your start-up apps.
Klipper remembers clipboard history - up to 2048 entries - even after system-shutdown/restart, and enables clipboard-actions.

---

### Post by patman0623 on 2010-04-28
I opened this thread many months ago, and I stand by it. If I hit ctrl-c, then close the application, there is no benefit whatsoever (that I can think of) to losing the data when the application is closed. I may well decide to file a bug - I don't think I should need to install some advanced clipboard project on my computer to do a proper paste operation.

---

### Post by 3rdalbum on 2010-04-28
It's not exactly a bug, because it works exactly the way that Freedesktop.org specifies that the clipboard should work (maintained by the program). It is a bad design though.

Glipper is a Gnome panel applet (as in, you install it and then right-click on your panel and go to Add To Panel... and choose Clipboard Manager) that works around the bad design and gives you a persistent clipboard, and other features.

---

### Post by stinkeye on 2010-04-28
**Parcellite** is another popular clipboard manager.

---

### Post by patman0623 on 2010-04-28
How would one go about making suggestions for freedesktop.org? At the risk of being impolite, I can't imagine who in the world came up with this hairbrained design.

---

### Post by ElSlunko on 2010-05-04
I don't find it intuitive either, but it did lead me to parcellite which is a great little app.

---

### Post by Old *ix Geek on 2010-05-06
> **patman0623 said:**
> I opened this thread many months ago, and I stand by it. If I hit ctrl-c, then close the application, there is no benefit whatsoever (that I can think of) to losing the data when the application is closed. I may well decide to file a bug - I don't think I should need to install some advanced clipboard project on my computer to do a proper paste operation.Exactly. I really don't get the "logic" behind it at all!

---

### Post by WakkiTabakki on 2010-05-07
> **Old *ix Geek said:**
> Exactly. I really don't get the "logic" behind it at all!

Here is the Launchpad bug report which explains it:
[https://bugs.launchpad.net/ubuntu/+bug/11334?comments=all](https://bugs.launchpad.net/ubuntu/+bug/11334?comments=all)

It started in 2004 and has over 200 comments...

/N

---

### Post by JEREMIAHBARLOW on 2010-05-21
I found this glipper and it works good.

In a terminal
Applications > Accessories > Terminal
Code:
**sudo apt-get install glipper**

---

