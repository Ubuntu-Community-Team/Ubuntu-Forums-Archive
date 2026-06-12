---
title: "keeping two machines in sync"
date: 2009-04-17
forum: General Help
---

### Post by marks_linux on 2009-04-17
I have two Ubuntu laptops and a large USB drive (would have been great to have a NAS, but sadly not!).

Essentially I'm wanting to try to keep the two laptops in sync with each other via the external drive. By in Sync I mean Documents, Pictures and Music folders under /home/

I'm not worried about keeping deletes in sync, just new and updated files. I would prefer to keep the copy on the external drive 'readable' i.e. not an archive or a .tar file. But would prefer If I could make the contents of the external drive encrypted.

Is there an easy way to do this?

---

### Post by Slim Odds on 2009-04-17
You might want to try unison [http://www.cis.upenn.edu/~bcpierce/unison/]("http://www.cis.upenn.edu/%7Ebcpierce/unison/")

---

### Post by fcuk112 on 2009-04-17
have you considered using something like dropbox for this?  check my sig.

---

### Post by rhcm123 on 2009-04-17
> **marks_linux said:**
> I have two Ubuntu laptops and a large USB drive (would have been great to have a NAS, but sadly not!).

Essentially I'm wanting to try to keep the two laptops in sync with each other via the external drive. By in Sync I mean Documents, Pictures and Music folders under /home/

I'm not worried about keeping deletes in sync, just new and updated files. I would prefer to keep the copy on the external drive 'readable' i.e. not an archive or a .tar file. But would prefer If I could make the contents of the external drive encrypted.

Is there an easy way to do this?

look up rsync (google is your friend or man rsync), then just make it a scheduled cron job. Or if your lazy, make cp -r /home/directories /location/you/want a cron job - slower but more blunt, and will update all the files.

---

### Post by marks_linux on 2009-04-17
Yes I'm currently using rsync for one laptop to the drive using a simple script. Any ideas how to get the script to run whenever the external drive (USB) is plugged into the laptop?

Unison looks promising!

---

### Post by rhcm123 on 2009-04-18
> **marks_linux said:**
> Yes I'm currently using rsync for one laptop to the drive using a simple script. Any ideas how to get the script to run whenever the external drive (USB) is plugged into the laptop?

Unison looks promising!

no clue, but i suggest trying the hardware forums. im not to good with uuids and the like

---

