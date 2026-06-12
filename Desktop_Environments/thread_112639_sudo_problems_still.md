---
title: "sudo problems still"
date: 2006-01-04
forum: Desktop Environments
---

### Post by bullfrog on 2006-01-04
[/B]i have 2 pcs. both have 2 h. drives.h. drives are not connted together. ebuntu installed on all 4.ebuntu worked so good i didnt believe it would be so easy to change over from $$$$$$$ but it was. after 2 to 3 months i have a problem with sudo. it will not take my password which is the same on all h.drives.can go to add-app.--synaptic--type in export  editor=gedit && sudo  visudo.they all take password.i have never set a password in root on any h. drive.i am on a home net work with 3 pcs.  have been almost every where looking and reading cant seem to find a problem like this. can someone help as i sure wont start over re loading until i find out what when wrong.    thanks for any help  bullfrog:confused:

---

### Post by linuxted on 2006-01-04
[QUOTE=bullfrog][/B]i have 2 pcs. both have 2 h. drives.h. drives are not connted together. ebuntu installed on all 4.ebuntu worked so good i didnt believe it would be so easy to change over from $$$$$$$ but it was. after 2 to 3 months i have a problem with sudo. it will not take my password which is the same on all h.drives.can go to add-app.--synaptic--type in export  editor=gedit && sudo  visudo.they all take password.i have never set a password in root on any h. drive.i am on a home net work with 3 pcs.  have been almost every where looking and reading cant seem to find a problem like this. can someone help as i sure wont start over re loading until i find out what when wrong.    thanks for any help  bullfrog:confused:[/QUOTE]

That's a weird one... you could try    "sudo passwd" to reset the password.   It might help but wait to see if others have better ideas.  Make sure you back up your data as you might be tinkering on the edge of a system crash.

---

