---
title: "Er, how do I set up a printer...?"
date: 2006-10-07
forum: Desktop Environments
---

### Post by kenquad on 2006-10-07
Hi all:

I feel like an idiot having to post this, but as it happens I have never set up a printer in Ubuntu, only Kubuntu.  The latter has a very nice setup utility.  The former doesn't seem to.  Do you go through the browser?  If so, what address do I need to put it?  Any help would be appreciated.  BTW, I'm trying to set up an HP Designjet 110+.

Thanks!
Ken Quad:-k

---

### Post by Fass on 2006-10-07
You can do it through CUPS' web interface at [http://localhost:631/](http://localhost:631/) or you can install gnome-cups-manager (if it isn't already installed - look in System -> Administration -> Printing).

---

### Post by sethmahoney on 2006-10-07
Or click on System->Administration->Printing and double-click on the New Printer icon.

---

### Post by Fass on 2006-10-07
> **sethmahoney said:**
> Or click on System->Administration->Printing and double-click on the New Printer icon.

"(if it isn't already installed - look in System -> Administration -> Printing)"

Is there an echo in here? ;)

---

### Post by kenquad on 2006-12-02
Belated thanks, guys.  Problem #2: I'm being prompted for the CUPS user and password, and don't know the defaults.  What are the defaults and how do I change them?  Thanks again!!

---

### Post by coffeecat on 2006-12-02
I'm fairly sure it's your own username and password, so long as you have sudo rights.

---

### Post by kenquad on 2006-12-02
Thanks, I tried that: after 2 attempts, it gave me the blank screen and didn't add my printer:(

---

### Post by coffeecat on 2006-12-02
Not sure what's going on there. Are you using the gnome print manager or localhost:631? As far as I remember the gnome print manager in Ubuntu only asks you for your user password. I've only used localhost:631 in another distro and, again as far as I can remember, I had to put in 'root' for name and the root password. A bit difficult in a default Ubuntu install.

If the gnome app is playing up (it doesn't usually - it's quite reliable) try localhost:631 in firefox or whichever is your favourite browser. If it does ask you for a root password, or your ordinary user one doesn't work, here is one way to enable the root account in Ubuntu. There is a simpler way from the terminal but I've forgotten it.

Go to System > Administration > Users and Groups. (You are prompted for your user password). Tick the 'show all users and groups' tick-box. Highlight root (at the top of the list). Click on properties and set a password of your own choosing where it says. OK all the way out and you now have a usable root password in Ubuntu. Do not misuse it! :wink:

Best of luck.

---

### Post by kenquad on 2006-12-02
coffecat:

Thanks; I was actually using localhost:631, but when I located the other utility it worked great.  I'm sure I read somewhere how to set the CUPS passwd, but as long this works I guess it doesn't matter.

Thanks!

---

