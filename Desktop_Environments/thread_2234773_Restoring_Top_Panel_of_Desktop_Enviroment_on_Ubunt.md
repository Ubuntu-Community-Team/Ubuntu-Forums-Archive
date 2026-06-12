---
title: "Restoring Top Panel of Desktop Enviroment on Ubuntu 12.02 - Grub"
date: 2014-07-16
forum: Desktop Environments
---

### Post by cdo on 2014-07-16
After a recent Linux update i somehow managed to remove the Top Panel from the desktop . Hence , no date , time , access to saved data , etc . Anyway to restore the top panel ? 

Thanks for any help

---

### Post by cdo on 2014-07-16
Sorry for the misslabeled version stated as 12.02 . Should be 12.04.02...

---

### Post by grahammechanical on 2014-07-16
Your thread title also mentions "Grub." It is not connected with this problem. There are a couple of things that you can try. They might or might not work.

to reset the Compiz window compositor

```
deconf reset -f /org/compiz
```

to reset Unity

```
setsid unity
```

Ctrl+Alt+T should open a terminal

To shutdown

```
sudo shutdown -h now
```

to reboot

```
sudo shutdown -r now
```

Another trick to try is to right click the desktop and when the menu opens select Change Desktop Background. That will open System Settings and from there we can open Additional Drivers and change video drivers and then reboot. This problem might have been caused by a conflict with a proprietary video driver. 

Regards.

---

### Post by cdo on 2014-07-16
Thanks for the tip.. will wait a bit to see if there are other suggestions and then try ..

---

### Post by cdo on 2014-07-18
Tried he above suggestion but didn't seem to work . Terminal did give me a warning message - something like " this should never happen " , at which point i stopped trying for fear of making things worse ..  Be advised , that i am a 70 yr. old with about as much compuer  savy as a 6th grader...   :-)

---

### Post by kansasnoob on 2014-07-18
Please post the output of this command:

```
echo $DESKTOP_SESSION
```

Then we can be sure which desktop environment is in use.

---

