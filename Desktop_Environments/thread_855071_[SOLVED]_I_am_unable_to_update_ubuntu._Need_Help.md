---
title: "[SOLVED] I am unable to update ubuntu. Need Help"
date: 2008-07-10
forum: Desktop Environments
---

### Post by mirchichamu on 2008-07-10
Ubuntu cannot be updated. Every time it tries to update, I get a message _dpkg _not found. I cannot even add other programmes. I don't know what to do?
Any Help Please?

---

### Post by kdcoetzee on 2008-07-10
:confused: 

Did you remove it ?

try to install it again with

```
 sudo apt-get install dpkg 
```

EDIT

Sorry, did you mean that when you try to update with apt-get you get a error message that dpkg does not exists.

---

### Post by Malac on 2008-07-10
> **mirchichamu said:**
> Ubuntu cannot be updated. Every time it tries to update, I get a message _dpkg _not found. I cannot even add other programmes. I don't know what to do?
Any Help Please?
 Can you post the actual error as this may help?

---

### Post by kdcoetzee on 2008-07-10
> **Malac said:**
> Can you post the actual error as this may help?

Yes thanks that would be helpful.

---

### Post by mirchichamu on 2008-07-10
Thanks for all of you for helping me.
awhen I update or install new programmes, I get a message that not all updates could be applied. When I click on details it says dkpg not found.....

---

### Post by kdcoetzee on 2008-07-10
With what are you trying to install or update your system.

are you doing it in Add/Remove , with commands like apt-get and synaptic in your terminal.


Can you please copy the output exactly and paste it here so we can better understand your problem.
:-k

---

### Post by mirchichamu on 2008-07-10
Thanks a lot. Now I am on my desktop. When I open my laptop, I will inform you of the output. I am using update manager.

---

### Post by kdcoetzee on 2008-07-10
Open up a terminal and type
```
dpkg
```
And see if it exists.

Then you can try this command. it tries to "fix" broken packages.
```
sudo apt-get -f install
```

Then
```
sudo apt-get install dpkg
```

And now I wait for the output... :D
because all this is just thumb sucking.

---

### Post by mirchichamu on 2008-07-10
Thanks. I took the screen shots, please at this. thanks.

---

### Post by sayakb on 2008-07-10
--post removed--

---

### Post by mirchichamu on 2008-07-10
> **LinuxIsInnovation said:**
> --post removed--

Thanks but why you removed your post?

---

### Post by sayakb on 2008-07-10
Sorry, posted the wrong command. At a terminal, do:
```
sudo dpkg --configure -a
```

---

### Post by mirchichamu on 2008-07-10
> **LinuxIsInnovation said:**
> Sorry, posted the wrong command. At a terminal, do:
```
sudo dpkg --configure -a
```

Thanks a lot once again.
I got this reply after command:
"dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory"

This is the same I get when updating.

What next sir?

---

### Post by mirchichamu on 2008-07-11
My problem not yet solved. Help please.

---

### Post by mirchichamu on 2008-07-11
Whatever I install or do update through update manager, I get this message:
"dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory"

What should I do? Please I request the big brains to help me.

---

### Post by sayakb on 2008-07-11
At a terminal, type in:
```
sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by mirchichamu on 2008-07-11
> **LinuxIsInnovation said:**
> At a terminal, type in:
```
sudo dpkg --clear-avail
sudo apt-get update
```

Thanks Million. It solved my problem. But I am still having one more unsolved problem. I will post now. Please help.

---

### Post by sayakb on 2008-07-11
Glad I could help :)
But do mark this thread as solved! (Thread Tools->Mark thread as solved)

---

