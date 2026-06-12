---
title: "Can't use xfce"
date: 2012-08-21
forum: Desktop Environments
---

### Post by 25tom on 2012-08-21
Hi,
I am trying to use xfce (not xubuntu-desktop) on Lubuntu Oneiric.
When I try to log in, I select the xfce desktop and then log in. This simply returns me to the login screen.
How can I fix this?
Also, I am, while not an absolute beginner, still fairly new to the various *buntus; no uber-difficult explanations please :)

---

### Post by zombifier25 on 2012-08-21
Can you log in as other desktop environment?

Either ways, press Ctrl + Alt + F1 to get into a tty, login and type this command:
```
sudo chown yourusername:yourusername ~/.Xauthority
```
don't forget ro replace yourusername of course.

---

### Post by 25tom on 2012-08-21
No, I tried Openbox Session and that gave the same response.
I presume that the code you gave changes permissions for me to use other desktops?

---

### Post by 25tom on 2012-08-21
Have managed to do the
```
sudo chown yourusername:yourusername ~/.Xauthority
```
but I still can't log in to Xfce...

---

### Post by 25tom on 2012-08-21
Some more info about the problem:
I can login to "Lubuntu" and "Openbox", but not "Openbox Session" or "Xfce session".

---

### Post by black veils on 2012-08-21
did you actually manually install the xfce desktop, or was it just an option in the menu already? if so, what package did you select?

---

### Post by 25tom on 2012-08-21
> **black veils said:**
> did you actually manually install the xfce desktop, or was it just an option in the menu already? if so, what package did you select?

I used the metapackage 'xfce4', from Synaptic Package manager. Once I had installed it the option 'Xfce Session' appeared in the desktop choosing menu at the login screen. I selected that from the menu and then the login failed as described before.

---

### Post by cmcanulty on 2012-08-21
it is certainly work trying reinstalling xfce

---

### Post by 25tom on 2012-08-22
> **cmcanulty said:**
> it is certainly work trying reinstalling xfce

That didn't work... still just reloads login screen.

---

### Post by 25tom on 2012-09-03
I think the technical term I need to use is "bump".

---

### Post by black veils on 2012-09-03
my solution would be to install ubuntu from minimal or alternate image, and install xfce desktop from there. i cant remember the difference between minimal and alternate, all i know is minimal gives you groups of packages to choose from, xfce isnt one of them, so you can install lubuntu desktop, then when you get into your system ```
sudo apt-get install xfce4
```

[http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main](http://www.youtube.com/watch?v=JLAQ2uQgTAY&playnext=1&list=PL365F9BF47955BA5F&feature=results_main)

---

### Post by 25tom on 2012-09-03
Is there a solution that doesn't involve a new install of Ubuntu?

---

### Post by s1baker on 2012-09-03
have you tried the xfce forums for any info they may have?

[http://forum.xfce.org/index.php]("http://forum.xfce.org/index.php")

---

### Post by Lemuriano on 2012-09-04
Perhaps you should try to install another display manager like GDM. 

Regards.

---

### Post by 25tom on 2012-09-08
> **Lemuriano said:**
> Perhaps you should try to install another display manager like GDM. 

Regards.

How do I go about doing that?

---

### Post by Lemuriano on 2012-09-08
I suggest gdm but you could use others like xdm ect. This happen to me with other distro while using lxde and it solve the problem. You can have only one display manager so the system will ask you to change the one you have for gdm. Hope this help.

```
sudo apt-get install gdm
```Regards.

You can also install the display manager from synaptic package manager if you chose to.

---

### Post by 25tom on 2012-10-24
Thanks :)

---

