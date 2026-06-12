---
title: "Two Openbox Issues"
date: 2008-10-19
forum: Desktop Environments
---

### Post by avidyachild on 2008-10-19
I have been running Openbox in Linux Mint for a few months now with no issues, but after the switch to Ubuntu I can't seem to sort out two final things:

1. Putting "export OOO_FORCE_DESKTOP=Gnome &" in my autostart.sh file does not give openoffice gtk styling. Everything I find on the net says it should, and it worked before, but not on this fresh installation of Ubuntu. Any ideas why this is happening?

EDIT: solved the below with "(sleep 3 && trayer) &

2. How can I make trayer appear on all desktops? I added 
<application class="trayer">
<desktop>all</desktop>
</application> 
to my rc, but to no avail.

I would really appreciate any help with these problems.

---

