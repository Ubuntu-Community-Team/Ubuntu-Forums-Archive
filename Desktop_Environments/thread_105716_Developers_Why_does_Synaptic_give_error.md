---
title: "Developers: Why does Synaptic give error?"
date: 2005-12-19
forum: Desktop Environments
---

### Post by kalos on 2005-12-19
I had the problem of Synaptic giving a bunch of "Couldn't stat source package" errors after doing a fresh install of Ubuntu. I looked around and there are *many* people who have the same problem. (Just search for *synaptic stat source package*.)

(If you're wondering, the solution is to run *sudo apt-get update* or click the Reload button in Synaptic.)

But my question is, why? If (almost) everyone has to update before they can use Synaptic, why not update automatically the first time? When most users see an error message, they associate it with something going wrong.

When Synaptic first runs, it pops up a window explaining packages and how Synaptic works. Why doesn't it prompt the user to update or something? Or the update could happen earlier, like at the end of the installation, or after the first login.


Then again, these steps could have already been taken and they are just not working for me. I did have problems with my network card and my solution (running ifup in an /etc/init.d script) might not be ideal.

I don't think it happened when I first installed Ubuntu (on a different machine). But I can't remember.

I haven't reported this as a bug because I was hoping for some feedback first. What do other people think about this? It seems like a minor issue, but I would want a new user to see as few error messages as possible (i.e., it Just Works).

-kalos

PS: Sorry if I posted in the wrong forum. I don't really know where this should go.

---

