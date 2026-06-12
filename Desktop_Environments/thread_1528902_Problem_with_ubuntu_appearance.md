---
title: "Problem with ubuntu appearance"
date: 2010-07-11
forum: Desktop Environments
---

### Post by Vipii on 2010-07-11
Hi everyone,

I tryed to install Gnome-power-manager, but it kinda failed  installing....
and now i restarted and i have this :s

[IMG]http://www.nighthawx.com/Screenshot.png[/IMG]

How can i restore it back to the default looks from ubuntu 10.04   without reinstalling?

Thank you for helping

Need help asap.

---

### Post by Naitsirhc Hsem on 2010-07-11
```
sudo apt-get -f install
```

This should fix all broken packages

---

### Post by Vipii on 2010-07-11
> **Naitsirhc Hsem said:**
> ```
sudo apt-get -f install
```This should fix all broken packages
Result:

```
root@V-Who:/home/vipii# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by howefield on 2010-07-11
I just had the same thing after closing Kaffeine, logging out and back in sorted it.

---

### Post by Vipii on 2010-07-11
> **howefield said:**
> I just had the same thing after closing Kaffeine, logging out and back in sorted it.
logging out isn't working, still same looks :(.

---

### Post by cosine352 on 2010-07-11
did you tried changing the appearence theme ? 

> gnome-appearance-properties

---

### Post by Vipii on 2010-07-11
> **cosine352 said:**
> did you tried changing the appearence theme ?
Yes not working to, only thing it changes is the color... for rest nothing

---

### Post by Vipii on 2010-07-11
> **Vipii said:**
> Yes not working to, only thing it changes is the color... for rest nothing
problem solved, quick reinstall of ubuntu.. :)

---

### Post by KdotJ on 2010-07-11
> **Vipii said:**
> Result:

```
[COLOR="Red"]**root**[/COLOR]@V-Who:/home/vipii# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

are you logged in as root?
Not recommended at all, this can cause big issues when installing and configuring stuff

---

### Post by Vipii on 2010-07-17
> **KdotJ said:**
> are you logged in as root?
Not recommended at all, this can cause big issues when installing and configuring stuff
Not logged in as root, but sometimes i use the root terminal :)

---

