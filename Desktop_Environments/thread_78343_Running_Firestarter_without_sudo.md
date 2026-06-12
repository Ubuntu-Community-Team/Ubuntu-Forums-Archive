---
title: "Running Firestarter without sudo"
date: 2005-10-18
forum: Desktop Environments
---

### Post by Moonbuzz on 2005-10-18
Hello all, I've installed Firestarter as the firewall, and also added it to the sessions to run at startup. However, the user I'm using does not have sudo rights. When Ubuntu boots up, the firewall asks me for a password, which doesn't do any good... the computer should have the firewall at startup, since it's immediately connected to the Internet, is there any way to solve this?

---

### Post by drewbie on 2005-10-18
firestarter is just a gui to change the firewall settings and moniter the firewall. the firewall will start automaticaly at boot up without needing firestarter.

---

### Post by drewbie on 2005-10-18
the firestarter help at [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php) will be able to tell you how to login to firestarter as a regular user if you really want to.

you can also check that your firewall is running at [Shelids UP]("https://www.grc.com/x/ne.dll?bh0bkyd2")

---

### Post by Moonbuzz on 2005-10-18
I see, I got the impression that it wasn't.

[http://distrowatch.com/dwres.php?resource=review-ubuntu](http://distrowatch.com/dwres.php?resource=review-ubuntu)

[quote=DistroWatch] Though by no means a bug, Ubuntu has been criticized for not including a built-in firewall. The official response to this complaint is that - since most services are turned off by default - no firewall is needed. Personally, I find that explanation as satisfying as saying you don't need to lock the door of your house because there's nothing to steal inside. If nothing else, I'd rather have a firewall for the warm fuzzy feeling it gives me. Fortunately, you can easily add one. Probably the easiest one to install and configure is firestarter. I actually prefer guarddog, because it gives more precise control over the firewall rules, but it's also a little more complex to set up.[/quote]

---

