---
title: "Font mystery"
date: 2006-06-27
forum: Desktop Environments
---

### Post by anders.ostling on 2006-06-27
Hi

Please have a look at the attached screenshot. Something strange has happened to some of the fonts. This seem to be isolated to Picasa and Wine (Crossover) applications. I have no idea what I did to provoke this, I dont recall installing anything related to fonts or font servers.

Help?

Anders

---

### Post by bjourne on 2006-06-27
Seems like it is requesting a font you don't have. Maybe you should apt-get install the package windows' font package? I think it is called msttcorefonts. Also check ~/.wine/config if you can find a problem there.

---

### Post by anders.ostling on 2006-06-27
I did re-install the msttcorefonts, but no improvment. The strange thing is that Picasa is (should be?) a completely self-contained package, incl all wine stuff. Same with Codeweavers crossover (I have 5.0.3 installed). The problem seems to be system-wide, if I login as another user I get the same problem (so not related to my private .wine files, or?). 

Anyone else?

Anders

---

### Post by cesera on 2006-07-02
Did you get any further with this? I seem to have a similar problem, where I can run a windows application, but I don't get any text on the buttons (and some other controls). I am not actually using Picasa or Codeweavers crossover, but the symptoms are the same.

---

### Post by anders.ostling on 2006-07-03
No, I did not manage to solve this. MS fonts worked fine in all other applications, so I ran out of ideas and re-installed from scratch. Now all is fine of course :-)

Anders

---

