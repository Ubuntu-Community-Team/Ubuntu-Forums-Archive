---
title: "this is my ubuntu problem"
date: 2010-02-27
forum: Egypt Team
---

### Post by kemoledo on 2010-02-27
slamo 3alikom m3lesh ana kont mstb el ubuntu w lma d5lt 3la kol partation la2et partation maby3mlsh mount w byktbli :


      
[B]Error mounting: mount exited with exit code 13: ntfs_attr_pread_i:
ntfs_pread failed: Input/output errorFailed to read NTFS $Bitmap: Input/output errorNTFS is either inconsistent, or there is a hardware fault, or it's aSoftRAID/FakeRAID hardware....... In the first case run chkdsk /f on Windowsthen reboot into Windows twice. The usage of the /f parameter is veryimportant! If the device is a SoftRAID/FakeRAID then first activateit and mount a different device under the /dev/mapper/ directory, (e.g./dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentationfor more details[/B]



f m3lsh ya3ni momkn 7d y2oli 7l el moshkla de eh ana 3aiz agrbo bs msh 3arf

---

### Post by thelinuxer on 2010-02-27
It looks like you have some inconsistent NTFS partition. 

Here is the hint for the solution from the error message you sent:
> **kemoledo said:**
>       
... run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! ...



try doing this and tell us if it worked.

---

### Post by kemoledo on 2010-02-28
i do this but it doesn't work thats why make me return to windows

---

### Post by korkony on 2010-02-28
What I have understood from you that you have 2 operating systems. Windows and Ubuntu. Before booting into Ubuntu, do you completely shutdown or restart the Windows? or you just hibernate it?
If you are hibernating it, try a complete shutdown or a restart and try to boot again into Ubuntu then mount your partition.

---

### Post by kemoledo on 2010-03-01
i do as was said totally shutdown and totally restart but nothing happens and the problem steals ---- and i think it is a corruption in ubuntu 9.10

---

### Post by Sensiva on 2010-03-02
> **kemoledo said:**
> i do as was said totally shutdown and totally restart but nothing happens and the problem steals ---- and i think it is a corruption in ubuntu 9.10
No its not, it is your NTFS partitions marked as not clean. When you restarted your Windows  did it prompt for checking hard disk? did you cancel it? please don't.

In case it didn't prompt for disk checking you may try to force it by entering the following command in your Windows cmd window
if the problem with partition c: then 
```
 chkdsk c: /f /v /x 
```And follow the on screen instructions.

Good luck

---

### Post by spaik on 2010-03-24
its not Ubuntu problem or corruption... its your partitions ... try what Sensiva said and u should be ok.

---

### Post by gazal on 2010-06-10
thanks

---

### Post by confy on 2010-06-25
I'm having similar situation but on my USB drive :(

---

### Post by Sensiva on 2010-06-25
> **confy said:**
> I'm having similar situation but on my USB drive :(

Do NOT ever remove any USB storage without unmounting (or safely removing it if in Windows)

Did you try instructions here? [http://ubuntuforums.org/showpost.php?p=8903074&postcount=6](http://ubuntuforums.org/showpost.php?p=8903074&postcount=6)

---

