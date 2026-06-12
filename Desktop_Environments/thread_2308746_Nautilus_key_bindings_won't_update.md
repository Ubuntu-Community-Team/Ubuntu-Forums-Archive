---
title: "Nautilus key bindings won't update"
date: 2016-01-05
forum: Desktop Environments
---

### Post by Trevor Burton on 2016-01-05
Since upgrading to 14.04 with Unity, the F2 key for renaming in nautilus hasn't worked.
I am using global menus.


I've found what I believe is the key bindings configuration file at ~/.config/nautilus/accels and edited it accordingly.

I tried the instructions in this thread [http://ubuntuforums.org/showthread.php?t=2188938](http://ubuntuforums.org/showthread.php?t=2188938) (though that is for Gnome rather than Unity).

I killed nautilus before editing the file to get the following line 
```
(gtk_accel_path "<Actions>/DirViewActions/Rename" "F2")
```
then, when I started nautilus, the F2 key still didn't trigger renaming of a file.  Even after logging out and in again, it wouldn't work.
Finally, on checking ~/.config/nautilus/accels it had reverted to the original where all the accelerators are commented out with semicolons.

I don't understand why I can't get f2 to bind to the Rename function nor why the ~/.config/nautilus/accels file keeps reverting to the default.

Any ideas?

Thanks in advance

---

### Post by CantankRus on 2016-01-05
Does your nautilus "edit" menu still show F2?
Were you using any third party ppas before upgrading?

Test in guest or different user session.

---

### Post by mc4man on 2016-01-05
By default that line should already be in ~/.config/nautilus/accels & working, here it's on line 112

If not for you maybe try deleting the accels file & _rebooting_, a new default one will be regenerated, then see if line is included

---

### Post by Trevor Burton on 2016-01-11
> **CantankRus said:**
> Does your nautilus "edit" menu still show F2?
Were you using any third party ppas before upgrading?

Test in guest or different user session.

Hi CantankRus,

Thanks for your help.
Yes, the "edit" menus does show F2.
Yes, I was using a third party ppa - the R statistical package.  I also have this on my desktop machine at home which is not suffering from the nautilus key binding problem.

I've tested it in a guest session.  Same problem.  Oddly, I've noticed that the new nautilus icon which I think appeared in 14.04 does appear in the guest session, but doesn't in my usual login.

---

### Post by Trevor Burton on 2016-01-11
> **mc4man said:**
> By default that line should already be in ~/.config/nautilus/accels & working, here it's on line 112

If not for you maybe try deleting the accels file & _rebooting_, a new default one will be regenerated, then see if line is included

Yes, I have it around there too, but all the lines are commented out with semicolons.  I just removed the semicolons, but they keep coming back.
I did try deleting the accels file, but it came back again with everything commented out with semicolons.
I'll try again and report back.

I'm beginning to wonder if it is a hardware fault on my keyboard.  Not sure how to test the F2 key for a hardware fault.

---

### Post by Trevor Burton on 2016-01-11
Sigh, sorry guys, problem was between keyboard and chair.
It turns out my keyboard was one of those fancy ones with pre-programmed F keys to do things like undo, redo etc.  To actually generate F key codes, I had to "lock" the keyboard to F key mode with a little extra button first.
Because I have simple keyboards at home and on laptop, there was no problem there.

Thanks for your time.

---

