---
title: "Add Remove Programs Blank"
date: 2009-03-14
forum: General Help
---

### Post by Agent Smith on 2009-03-14
Hello all, i am hoping someone out there has seen this problem before.
When i go to "add/remove" programs in the applications menu, it doesn't show anything. Any help would be appreciated.
Please don't tell me i should be using synaptic to add remove stuff. I know, but i just like this way. Thanks Jon.

---

### Post by artheus on 2009-03-14
Do this:

```

sudo apt-get remove gnome-app-install
sudo apt-get install gnome-app-install apturl ubufox ubuntu-desktop
```

And voila! It should now work! :)

EDIT : Just to clearify .. you do this in the Terminal

---

### Post by ajgreeny on 2009-03-14
Have you recently installed adobe air, as I have read that this can do what you've found.  I don't know how to get it all back, however, so you will need to look further, if this is the reason for your problem.

---

### Post by Agent Smith on 2009-03-14
Thanks very much artheus. That worked fine. @ ajgreeny, i do have adobe air installed, but i havent had any problems with it. I use it for BBC iplayer. Thanks Jon

---

### Post by ajgreeny on 2009-03-14
> **Agent Smith said:**
> Thanks very much artheus. That worked fine. @ ajgreeny, i do have adobe air installed, but i havent had any problems with it. I use it for BBC iplayer. Thanks Jon
I didn't mean there was a problem with using air, just that it seems to remove all the entries from Add/Remove for some weird reason.  However, glad all is now well again.

---

### Post by celticJedi on 2009-03-18
it happened to me just after I updated Adobe Air

---

