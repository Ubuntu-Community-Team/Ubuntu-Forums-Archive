---
title: "Laptop Hard Drives"
date: 2008-03-11
forum: Dell  Ubuntu Support
---

### Post by mpgarate on 2008-03-11
how can i tell if my hard drive is effected by the over activity bug? I have a brand new vostro 1400, but running this command gives me nothing

> root@mike-laptop:/home/mike# smartctl -a /dev/sda | grep Load_Cycle_Count
root@mike-laptop:/home/mike# 




---

### Post by niteshifter on 2008-03-12
Before we begin, do *me* a favor and go back to being a normal user, NOT root. Sometime (rarely) one needs to be the actual super-user, this is not one of those times. It's a bad habit to get into, shifting into SU for every task.

Now, what output is produced when you give just this command:
```
sudo smartctl -a /dev/sda
```

I'm going to bet that this text: Load_Cycle_Count
is not to be found anywhere in the output from smartctl. This is because:
A) Your hard disk is not a S.M.A.R.T. capable drive.

B) Your drive does not report this particular parameter, or the letter-case of smartctl's output is different (i.e. Load_cycle_Count).

Somebody will correct me if I've got this next part wrong, but IIRC only the parameter numbers are defined in SMART, text can vary. Perhaps the below will work for you (if you get output from the code above):
```
sudo smartctl -a /dev/sda | grep 193
```

---

### Post by Arthur Archnix on 2008-03-12
Or maybe the op just hasn't installed it yet.
```
sudo apt-get install smartmontools
```
Then go [here]("http://ubuntuforums.org/showpost.php?p=3675960&postcount=26") and learn all about it.

---

### Post by mpgarate on 2008-03-12
i doublechecked, and smartmontools is installed. I ran the first code and got a long output i can post if you like, but it didnt have anything related to load cycles that i noticed. The second command gave me nothing :

oh and i was su only in effort to get this working, not a habbit of mine

edit: i noticed this... could it be related or bad?
> 4 Start_Stop_Count        0x0032   100   100   000    Old_age   Always       -       1466


but it did show that my drive had smart capabilities
> SMART support is: Available - device has SMART capability.
SMART support is: Enabled


---

### Post by Arthur Archnix on 2008-03-12
The link I posted is the authoritative thread on the issue on these forums. You're best bet is to go there, read it carefully and post any questions you have there.

Instead of using su to become root (you must have enabled the root account) you should use sudo.

---

