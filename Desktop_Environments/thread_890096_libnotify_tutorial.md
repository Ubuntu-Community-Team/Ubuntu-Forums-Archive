---
title: "libnotify tutorial"
date: 2008-08-14
forum: Desktop Environments
---

### Post by puntino on 2008-08-14
Hi 

I'm looking for a tutorial concerning libnotify.
I'd like to develop my own desktop application which notifies me about a new incoming messagein mail.box, I desire to see a message with the object and the sender of that email. 
I also want to notify myself about a low battery level. 
Can I write an application in C/C++? 
Where can I find some guides/tutorials ? 
At least I'd need a page showing the API of libnotify.
Thank you in advance.

---

### Post by arist0tle on 2008-08-14
Hey! I wrote a small app using libnotify to tell me when the next issue of a certain famous hacker zine was released. I wouldn't do it in c or c++ though if I were you. Go with a scripting language that has bindings for libnotify. I wrote my script in Perl. I would go with Perl or Python. The docs are pretty straight forward in the Perl lib if I remember correctly.  Install Gtk2::Notify and run perldoc Gtk2::Notify on the command line. Good luck and happy programming :-)

---

