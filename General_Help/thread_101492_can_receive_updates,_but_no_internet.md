---
title: "can receive updates, but no internet"
date: 2005-12-09
forum: General Help
---

### Post by linrasta on 2005-12-09
Someone help please!  I am trying to setup linux to use it as a server.  I have 2 winxp boxes that I want to connect to the internet through the linux box.  I did a standard install on ubuntu, and other times when I have installed it, it automagically detected my dsl router.  But on the most recent installation, it will connect and get updates, but it can't seem to browse through firefox.  Why is it different all of the sudden? The installation isn't any different; same setup.  Please help! I can't get passed step 1!

---

### Post by ninotob on 2005-12-10
I had this recently on a fresh install of Breezy.  If you have the same problem I had, then it's just a DNS issue.

First, make sure you can ping your router, eg,

ping 192.168.1.1
(replace the address w/ whatever your router address is at of course).

If that works, use a browser to see the DNS entries on your router ... alternatively, if you wanna be lazy and skip this step, or if you just want a good set of DNS servers (for example, if you are unfortunate enough to have comcast as your provider), use verizon's DNS servers: 4.2.2.1, 4.2.2.2 .... 4.2.2.n (I don't know exactly how high they go, but two or three is plenty).

Then click on the network settings program, highlight your ethernet card, click the DNS tab, and add the entries, deactivate and activate, save.  Test:

ping google.com

If you get response, you're live.

---

### Post by ninotob on 2005-12-10
As to your second question, using the ubuntu box as a firewall, that is easy too.  Your setup will be (and I appologize if this too basic):

dsl/cable---->Ubuntu.Box----->router------>2 winXP computers

You do need to have 2 ethernet cards in the ubuntu box.  Then just install "firestarter" -- you'll have to activate an additional repository but you can do that in synaptic by asking to look at the disabled repositories -- I can't recall which you have to activate but just activate one, search for "firestarter" and deactivate if you don't see it.

First time you run firestarter, the wizard will quite competently guide you through.  I have the same setup as you want (except for the windows machines) and works great.

---

