---
title: "laptop harddrive Load_Cycle_Count issue and Dell xps m1330"
date: 2008-11-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by bigbrovar on 2008-11-04
I was during a research to see if my laptop a dell xps m1330 (which came preinstalled with Ubuntu) was affected by the laptop harddrive Load_Cycle_Count issue i ran 2 test in 15 minute following the guide here [http://ubuntuforums.org/showthread.php?t=795327](http://ubuntuforums.org/showthread.php?t=795327) and the result was really disturbing .

when i ran the first test i got this result

190 Temperature_Celsius     0x0022   062   054   045    Old_age   Always       -       639303718
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       **20939**
194 Temperature_Celsius     0x0022   038   046   000    Old_age   Always       -       38 (Lifetime Min/Max 0/23)


15 minute later when i ran the same test 

190 Temperature_Celsius     0x0022   062   054   045    Old_age   Always       -       639303718
193 Load_Cycle_Count        0x0032   090   090   000    Old_age   Always       -       **20967**
194 Temperature_Celsius     0x0022   038   046   000    Old_age   Always       -       38 (Lifetime Min/Max 0/23)


from this result my load cycle count number listed in this commands output changed by 28 meaning my load cycle count increases by 28 every fifteen minute. from the look of things its really scary and i want to ask if anyone has the same problem should i apply the patch 

my hard disk is 320gb in size and made by samsung the speed is 7200 RPM and it comes with freefall sensor. point is i am afraid and i dont know if i should apply thge patch becasue i dont want to do anything that would hurt the the harddrive does anyone have the same problem?

---

### Post by ponman on 2008-11-21
I can confirm that I had this issue on my Dell m1330 with a 160G 5400rpm HD.  I was getting 60 cycles per hour which is way too many.  It sounds like you're even worse off.  I applied the patch and my cycles have basically dropped to zero.  My temperature didn't even change (still 37-38 ).  I know that it's a little scary to be applying these home-brew patches to fix these issues, but consider the consequence of doing nothing = a dead HD in 9 months.  Make backups of the 4 files the guy calls out so you can revert if strange things start happening and give it a shot.

---

### Post by bigbrovar on 2008-11-22
it seems this issue has been fixed in ibex ..  can anyone confirm this?

---

### Post by bluelamp999 on 2008-11-30
Bump!

My Dell Latitude D810 is showing crazy figures.

Is this really an issue? Has it been fixed in Intrepid?

Peace...

---

### Post by bigbrovar on 2008-12-01
> **bluelamp999 said:**
> Bump!

My Dell Latitude D810 is showing crazy figures.

Is this really an issue? Has it been fixed in Intrepid?

Peace...

It seems most pple are not interested in this issue :( look at the date it was originally posted and see this huge* amount of response it has gotten. i guess most pple are more interested in webcams and blue tooth working than getting than fixing something that could save their hard-drive from an early grave

---

### Post by bluelamp999 on 2008-12-01
> **bigbrovar said:**
> It seems most pple are not interested in this issue :( look at the date it was originally posted and see this huge* amount of response it has gotten. i guess most pple are more interested in webcams and blue tooth working than getting than fixing something that could save their hard-drive from an early grave

I know! 

But you'd think Canonical would make some kind of statement on the matter if it was a genuine issue which could possibly kill peoples hardware...

---

### Post by anachoret on 2008-12-27
Actually, it is a Linux's bug for using SATA HDDs.

Look at the posting "laptop harddrive Load_Cycle_Count issue" in the   	Ubuntu Forums > The Ubuntu Forum Community  > Main Support Categories  > Hardware & Laptops.

---

