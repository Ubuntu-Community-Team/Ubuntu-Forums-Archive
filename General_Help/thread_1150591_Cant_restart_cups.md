---
title: "Cant restart cups"
date: 2009-05-06
forum: General Help
---

### Post by _sAm_ on 2009-05-06
Hi

I am trying to use cups to share my printer on the lan. When I run; sudo /etc/init.d/cupsys restart I get "Command not found". 

The command: ls -al /etc/init.d/cups gives;
-rwxr-xr-x 1 root root 2526 2009-04-17 11:17 /etc/init.d/cups

Why cant I restart cups?

I am using Ubuntu server 9.04.

Thanks

---

### Post by amingv on 2009-05-06
Try:

```
sudo /etc/init.d/cups restart
```

(There's not a cupsys script in init.d)

---

### Post by _sAm_ on 2009-05-06
Thanks, it worked. Strange I just used copy/paste from 3 different guides(the command that did not work)..

---

### Post by trigoman05 on 2009-11-23
> **amingv said:**
> Try:

```
sudo /etc/init.d/cups restart
```

(There's not a cupsys script in init.d)

Thanks this did the trick.

---

### Post by ozzyprv on 2009-12-15
Does anybody know why those guides keep referring to 
```
sudo /etc/init.d/cupsys restart
```
or
```
sudo /etc/init.d/cupsd restart
```

when it is actually restarted by:
```
sudo /etc/init.d/cups restart
```

---

### Post by Queue29 on 2009-12-15
> **ozzyprv said:**
> Does anybody know why those guides keep referring to 
```
sudo /etc/init.d/cupsys restart
```
or
```
sudo /etc/init.d/cupsd restart
```

when it is actually restarted by:
```
sudo /etc/init.d/cups restart
```

Because all three are correct. (Or incorrect, depending on your viewpoint.) Different package managers across different distros use different commands, and even Ubuntu is guilty of changing the command used across versions. 

Proof of cupsys being what I have to use:

[IMG]http://i56.photobucket.com/albums/g185/Trombe29/cupsys.png[/IMG]


It's just a byproduct of the inherent anarchy of open source development.

---

### Post by ozzyprv on 2009-12-30
Thank you!

---

