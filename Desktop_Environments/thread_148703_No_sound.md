---
title: "No sound"
date: 2006-03-22
forum: Desktop Environments
---

### Post by 604 on 2006-03-22
After watching a movie sound just disappeared. I've restarted the computer a few times, checked my speakers' cables but can't still hear anything.
help?

---

### Post by noswal on 2006-03-22
If you open volume control - anything X'd out which shouldn't be?
Click File, change device - anything?

---

### Post by NoNo_231 on 2006-03-22
First of all check if as user you have access to the sound card (doubl click on the sound icon). If you do check this [http://linux.iuplog.com/default.asp?item=94639](http://linux.iuplog.com/default.asp?item=94639)
I had the same problem and did this part:
Run alsamixer and turn off IEC related options
IEC is an input to certain high end sound cards that support optical (fiber optic) sound feed from such things as DVD players etc.. My sound card is SIS on board and certainly doesn't have ability of using IEC. But Ubuntu turned on those options by default.
To turn off those options, rum "alsamixer" (without quote) in gnome terminal. You can move around each option with your arrow key (right and left key.) Move to every IEC related options, turn off all of those options (use keyboard "m" to turn off.) After turning off hit "Esc" key to save, and type "sudo alsactl store" so that it is saved permanently.
Maybe you will need to reboot after this.

---

### Post by 604 on 2006-03-22
I turned off the IEC related options and rebooted, seems like it messed something up real good. Now i'm not able to log on with my user and there's still no sound. Seems i can't paste the error log as i cannot copy it or something, guess i'll have to write it on paper if needed.
anything?

---

### Post by NoNo_231 on 2006-03-22
It is a little bit difficult the problem to came up from alsamixer. At least describe the situation you have. What is the error messages.  Did you the check the priviledges you have as  a user?

---

