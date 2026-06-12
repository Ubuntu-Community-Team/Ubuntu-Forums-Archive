---
title: "Anyone using FedEx Desktop?"
date: 2009-02-10
forum: General Help
---

### Post by yther on 2009-02-10
[FedEx Desktop]("http://www.fedex.com/desktop/") is an Adobe AIR application that I use every day at work, and one of the few things preventing me from dumping Vista for my everyday use.  I do have Air working, and I managed to install it (apparently successfully) on my laptop running Intrepid x64, but it seems to immediately exit when I start it.

So, I'm curious as to whether anyone else has managed to get this thing working under Linux.  The wording on the FedEx page makes it sound like they just don't want you to use it except in Windows or MacOS X, but I'm wondering if there are technical reasons it won't work.

Anyone?  :)

---

### Post by yther on 2009-02-11
Well, in case anyone finds this useful, I can now say that I *have* gotten this thing to start up and stay running long enough for me to sign in and track some shipments.  The experience has been strange.

Today when I logged in, I noticed a large gray rectangle in the upper left corner of my screen, like a drop shadow without an object.  There was a corresponding button for "FedEx Desktop" in my KDE taskbar, but try as I might I could not get the actual window to appear, only its shadow.  I killed the window and examined the K-menu entry for it, and discovered that the path to the application was rather odd-looking:  [FONT=Lucida Console]'/opt/FedEx'/'FedEx Desktop'/bin/'FedEx Desktop'[/FONT].  I tested in a terminal and found that [FONT=Lucida Console]/opt/FedEx/FedEx\ Desktop/bin/FedEx\ Desktop &[/FONT] would start the app.  I changed the path in the menu item to [FONT=Lucida Console]"/opt/FedEx/FedEx Desktop/bin/FedEx Desktop"[/FONT] (including quotation marks) and the application now starts.

So, I don't know what the problem was the first couple of times, but it seems to be working now, and I doubt my change really had anything to do with it.  There's still the cosmetic problem of the drop shadow, however.  It seems that the program insists on making its own shadow, and there is no option to disable this.  Oh well, I need it for its features; I don't need it to look pretty.  :P

(Oh, yes—I did read through the EULA that ships with the application itself, and there is no mention of operating systems.  That leaves me wondering why they bothered to mention them on the app's web page.)

---

