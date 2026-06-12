---
title: "Trouble installing correct HP printer drivers on 5.10"
date: 2006-05-21
forum: Desktop Environments
---

### Post by pspotts on 2006-05-21
Folks,

I'm using 5.10 on a Toshiba Satellite 1905-s303 laptop. I have two HP Deskjet printers, a 6540 and 6122. Their drivers do not appear in the set that installs from apt-get. And the "recommended" setting using Gnome's CUPS management tool gives me 300 dpi black and white printouts, rather than the BW/color I need. So I downloaded the specific Linux drivers for my printers from HP, put them in /usr/share/ppd/HP and tried to install them with the Gnome tool. They show up in the listing, but when I selected them, I got the following error message...

 Missing asterisk in column 1 at
1:'/usr/share/ppd/HP/HP-DeskJet_6540-hpijs.ppd.gz'

For chuckles, I copied that file into my home directory and unziped it
for a look-see. It's hard for this neophyte to see where the "missing"
asterisk is missing from. What have I overlooked?

With best regards,

Pete

---

### Post by Sef on 2006-05-21
If you can wait till Dapper is stable on 1 June or install the beta, it has support in the printer menu for both of those printers.

---

### Post by pspotts on 2006-05-21
Many thanks...patience is a virture...;-)

---

