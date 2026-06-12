---
title: "Extra configuring of Alarm Clock"
date: 2009-05-04
forum: General Help
---

### Post by turinturambar on 2009-05-04
I have Alarm clock installed and use it to wake up every morning to music.  In the options for each alarm, I'm allowed to make the music fade in for a period of up to 480 seconds.  

Is there a way to lengthen this amount of time?  A text file somewhere that I can edit or a utility or something like that?  Any help would be appreciated greatly.

Thank you

p.s.  If you know of another alarm clock that can do this, please let me know.  Thanks again.

---

### Post by _Purple_ on 2009-05-05
The settings are saved in ~/.config/alarm-clock or /home/username/.config/alarm-clock. Try to replace 480 with a higher number in that file and see if it works.

---

### Post by turinturambar on 2009-05-05
I went to that directory and opened the 'alarms' file, edited that alarm to 960 instead of 480, and then saved and closed.

When the alarm went off, no audio was played.  Also, a new file was created in that directory called 'alarms~' and it seemed to think it was a backup file.  My altered alarm was in the backup, but not in the original.

Any other ideas?  Maybe I need to edit the other files too?  Thank you.

---

### Post by dli8ilb on 2009-05-06
it could possibly be a limitation of the software.

you could always try contacting the developer by email: tsalacinski {at} gmail {dot} com

i've spoken with him before, and he seems very reasonable and willing to listen to users questionas & concerns.

---

