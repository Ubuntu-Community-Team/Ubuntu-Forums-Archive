---
title: "Wireless worked on 5.04, but not 5.10"
date: 2005-12-09
forum: Desktop Environments
---

### Post by Bjamin0325 on 2005-12-09
Hi everybody,
I've tried searching, but I couldn't find anything.  Does anyone know why my internet worked with Hedgehog but not Breezy?  I didn't have to do anything with the 5.04 install, it just started right up.

Now, I can't get any connection with 5.10, wireless or wired.  

Can anyone offer advice?

Thanks a million, everybody.

Ben

---

### Post by Bjamin0325 on 2005-12-09
Sorry, I'm connecting on a Vaio notebook with built in Atheros 802.11abg NIC to a cable connection on Linksys wireless router.

Thanks.

---

### Post by mad_phoenix on 2005-12-09
IMO the Ubuntu wireless tools suck.  Is your network device present?  What happens if you open a terminal and do sudo iwconfig (possibly /sbin/iwconfig if it's not in your path).  As much as I like Ubuntu, I still use standard iwconfig commands from the command line because the GUI applet sucks.

If you try the above and your network device isn't there (it will say "no wireless extensions" next to every network device), you probably don't have the right kernel modules loaded for it.  Do you have the hotplug service turned on?  Do an lsmod and see if the proper modules for your card are there.  

These are all kind of general network troubleshooting tips, so try poking at it and see what you find.  If you have any results for these questions, post here and we can move forward.

---

