---
title: "LAN chat program?"
date: 2009-04-18
forum: General Help
---

### Post by pickarooney on 2009-04-18
I'm looking for a very simple LAN chat program which doesn't require account creation or passing by a server on the internet, preferably in the repositories. I've been searching for a while but have found nothing usable that I've been able to compile.

i picked the wrong distro by accident, I'm actually using Xubuntu

---

### Post by pickarooney on 2009-04-22
anyone? Bueller, Bueller, anyone, anyone?

---

### Post by lisati on 2009-04-22
If memory serves correctly, there is one. I think it's name is something like "Linpop".

---

### Post by Menschenfresser on 2009-04-22
Just use Pidgin and add a new "bonjour" account (it'll make your name "user@host") and you will be visible in the LAN. I have been using it as a very simple and fast way to e.g. transfer files without setting up any shares, etc. I am not sure about empathy or kopete, but I would be surprised if they didn't support it as well.

---

### Post by pickarooney on 2009-04-24
Thanks. I tried pidgin before but couldn't get connected without an MSN account. What's the name of the pacakge I need to install to get bonjour to work?

---

### Post by nquinnathome1 on 2009-04-24
You'll need Zeroconf/Avahi to get the Bonjour services.

See here: [https://help.ubuntu.com/community/HowToZeroconf](https://help.ubuntu.com/community/HowToZeroconf)

---

### Post by Menschenfresser on 2009-04-24
> **nquinnathome1 said:**
> You'll need Zeroconf/Avahi to get the Bonjour services.

Yes you need that too, I thought it was installed by default

---

### Post by ahood on 2009-09-04
I just want to confirm that I was able to configure our home machines to send messages across the lan. The configuration was pretty simple, but I admit not zero effort.

Our lan uses four machines (1 DellMini9/Ubuntu 8.04, 2 Desktop/9.04, 1 OldLaptop/Xubuntu 8.04).

All had Pidgin + avahi + bonjour already installed.

On each machine, I did the following...

1. Start Pidgin
2. Add new account and specified Bonjour for protocol
3. Specified a user name and entered 'homelan' for server

Hope this helps.

---

