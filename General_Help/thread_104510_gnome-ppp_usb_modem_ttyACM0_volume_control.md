---
title: "gnome-ppp usb modem ttyACM0 volume control"
date: 2005-12-16
forum: General Help
---

### Post by maglis on 2005-12-16
I'm testing for the best (=easiest) dialup method for a new user on Ubuntu-5.10. I run to a problem with gnome-system-tools (which I'll explain in another post). After searching the forum, I tested gnome-ppp. It seems perfect for the job. It has a good and simple interface and allows for user accounts to activate ppp interfaces without any admin configuration.

I have a usb connected isdn terminal which appears like a modem at /dev/ttyACM0 via usb kernel driver cdc_acm. The modem follows a restricted set of AT commands. It has been successfully connecting to ISP's for years using wvdial. It only needs simple things like ATZ, ATX3 and ATDT Dial Command. It does not like other AT commands found in default gnome-ppp Init strings. These I can delete.

The problem is with gnome-ppp volume control setting that sets a ATM1L3DT command in .wvdial.conf file. This specific modem aborts with an error if you try to set volume levels. The problem is really with gnome-ppp, because it does not respect my editing of .wvdial.conf file on start. It overrides my Dial Command directive with one like the above. It is an interface design problem with gnome-ppp. It does not allow for this case. I tried to make .wvdial.conf read only but on exit it returns the file to rw before saving! I tried to chown the file and I successfuly crashed the app!

Can anyone give a solution? I would prefer a simple one and rather not dive into source code and rebuilding. If there isn't such a quick fix, I guess I have to report a bug.:(

---

### Post by maglis on 2005-12-17
I managed to talk to a gnome-ppp developer named [COLOR=#a82f2f]**vladeck**[COLOR=black] over icq.
He thinks this is something easy to fix and that he will:

[/COLOR][/COLOR]> [SIZE=1][COLOR=#a82f2f](18:12:20) **vladeck:**[/COLOR][/SIZE][SIZE=1] just a minor code change, but don't think i represent big problem to be fixed
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:12:36) **vladeck:**[/COLOR][/SIZE][SIZE=1] it should be easy[/SIZE] 
He also seemed far away from active development on gnome-ppp. 

> [SIZE=1][COLOR=#a82f2f](18:06:05) **vladeck:**[/COLOR][/SIZE][SIZE=1] there are so many things i have been ignoring about gnome-ppp: translations, requests and bug reports...
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:06:43) **vladeck:**[/COLOR][/SIZE][SIZE=1] i believe that i will have linux installed, soon, on my home computer, so i could address some of these issuses, but the overall development WILL stop[/SIZE] 
I encouraged him to either come back himself or arrange for some sort of group development for others to continue the work. He seemed willing to consider:

> [SIZE=1][COLOR=#a82f2f](18:09:32) **vladeck:**[/COLOR][/SIZE][SIZE=1] well
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:09:39) **vladeck:**[/COLOR][/SIZE][SIZE=1] i do have svn server of my own
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:09:43) **vladeck:**[/COLOR][/SIZE][SIZE=1] so i could set it up there
[/SIZE] [SIZE=1][COLOR=#16569e](18:09:49) **Menelaos:**[/COLOR][/SIZE][SIZE=1] 8-)
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:09:52) **vladeck:**[/COLOR][/SIZE][SIZE=1] with the informations and all
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:10:05) **vladeck:**[/COLOR][/SIZE][SIZE=1] maybe someone will pick up some kind of development on gnome-ppp
[/SIZE] [SIZE=1][COLOR=#a82f2f](18:10:24) **vladeck:**[/COLOR][/SIZE][SIZE=1] i guess doing this will be my homework in the next few days[/SIZE] 
I suggested using sourceforge or gnomefiles instead, and thanked him for the attention.

Just thought you should know...

---

