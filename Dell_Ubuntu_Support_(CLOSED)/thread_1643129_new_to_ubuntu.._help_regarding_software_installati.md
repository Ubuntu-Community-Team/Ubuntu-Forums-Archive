---
title: "new to ubuntu.. help regarding software installation"
date: 2010-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by anubhavsingh1987 on 2010-12-11
hey, 

new to ubuntu, just intsallled ubuntu 10.10 from ubuntu's site... 

went to mozilla .. tried running youtube videos.. but it asks me to upgrade the flash playter.. so i go to adobe;'s site and download the latest package in .tar.gz format

now i am clueless as to how to install this actually!!


plz help!!

i am new to console programming as well :P

---

### Post by sikander3786 on 2010-12-11
Welcome to the forums :-)

Being the easiest solution, I would suggest to use flash-aid FF add-on.

[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)
courtesy of forum member *lovinglinux*

---

### Post by pbpersson on 2010-12-11
If I were you, I would not install ANYTHING manually from any web site.  

I do not have the latest version of Ubuntu here but if you go to Administration in your menu, do you see something called Synaptic Package Manager?  That is what I use to install everything.

In the search box type "Ubuntu" and see if there is something named "Ubuntu Restricted Extras"

That is the ticket to a bunch of good things, including Flash

---

### Post by sikander3786 on 2010-12-11
I was lazy to mention that. Thanks *pbpersson* :-)

Actually ubuntu-restricted-extras is a better way of installing flash as it also installs all the necessary audio/video codecs (except DVD specific), an open version of java and also some fonts.

Applications > Accessories > Terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

Note: When you type your password in the terminal, it won't show any characters or asterisks against it. Just type blindly and hit enter.

Or Synaptic Package Manager under System > Administration menu. Or Software Center under Application menu. There are multiple choices ;-)

---

### Post by azertyh on 2010-12-12
hello,
new to ubuntu, read [ this thread](http://ubuntuforums.org/showthread.php?t=801404).
and the [how to install software](https://help.ubuntu.com/community/InstallingSoftware).
for the flash, install [the restricted format](https://help.ubuntu.com/community/RestrictedFormats) or [gnash](https://help.ubuntu.com/community/RestrictedFormats/Flash).

---

