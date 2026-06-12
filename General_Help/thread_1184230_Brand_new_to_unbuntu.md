---
title: "Brand new to unbuntu"
date: 2009-06-10
forum: General Help
---

### Post by bg26892 on 2009-06-10
Just installed unbuntu on my desktop...love it so far.

However, I've had a couple snags and was hoping someone could provide me with some direction.

- I can not figure out how to enable support for dual monitors.
- I am unable to open firefox.  Each time i click on the icon, i get a msg at the bottom toolbar that says "starting firefox" and then it completely disappears after about 10 seconds.  

Any help would be greatly appreciated.

Thanks!

---

### Post by _Purple_ on 2009-06-10
Welcome! :)
For your second problem, open a terminal (Application > Accessories > Terminal) and type
```
firefox
```

Can you post the error message from the terminal here?

---

### Post by bg26892 on 2009-06-10
Thanks for your response.

The thing is - I don't even get an error msg, the firefox screen just disappears without any notification!

---

### Post by _Purple_ on 2009-06-10
After you type firefox in terminal, nothing else appears in terminal?

---

### Post by DaftPyramid on 2009-06-10
When you type firefox into terminal, you should get a message *inside the terminal.*

---

### Post by bg26892 on 2009-06-11
> **DaftPyramid said:**
> When you type firefox into terminal, you should get a message *inside the terminal.*

Took a while to find the terminal :)

The msg reads...

"Could not find compatible GRE btwn version 1.9.0.1 and 1.9.0.*

Does this help?

---

### Post by merlinus on 2009-06-11
You might try uninstalling and then reinstalling.  Before that, open nautilus, press Ctrl+H to show hidden files, and delete the .mozilla directory.

---

### Post by Soul-Sing on 2009-06-11
etc/gre.d. problem.Not a ./mozilla problem imo
launchpad(bugs) suggests: ```
xulrunner --register-global
```
or ```
sudo xulrunner --register-global
```
:[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/248493/comments/2](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/248493/comments/2)

---

### Post by bg26892 on 2009-06-11
> **leoquant said:**
> etc/gre.d. problem.Not a ./mozilla problem imo
launchpad(bugs) suggests: ```
xulrunner --register-global
```
or ```
sudo xulrunner --register-global
```
:[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/248493/comments/2](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/248493/comments/2)

PRESTO!  

Thanks for your help!

---

### Post by Chronon on 2009-06-11
What have you done to set up dual screens so far?  There should be some sort of system settings accessible from the menu bar.  (I don't know what desktop manager you are using.)

---

### Post by danastasio on 2009-06-11
:mrgreen:cool, my first help post! :KS

for dual monitors, use nvidia settings

```
sudo apt-get install nvidia-settings
```

and for that you need to enable restricted drivers

```
System--->Admin--->restricted drivers
```

and click on the driver package that you wish to enable. Just go with the higher number, it is the latest release. 
Best of luck! :D

---

