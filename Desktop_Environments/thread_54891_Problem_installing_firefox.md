---
title: "Problem installing firefox"
date: 2005-08-06
forum: Desktop Environments
---

### Post by coogor on 2005-08-06
Gents, I'm new to ubuntu....

Tried to install Mozilla-firefox, and it seemed to work:

root@tp770:/home/axel # aptitude search Mozilla-firefox
pi  firefox                            - lightweight web browser based on Mozilla
pi  mozilla-firefox                    - dummy transitional package
...
i A mozilla-firefox-locale-de-de       - Mozilla Firefox German language/region packa
...
..at least if I want to install it again it claims that it is already installed. But I cant find it anywhere, so I assume there is another package required.
But which one?

TIA!

---

### Post by Darkscot on 2005-08-06
Ubuntu comes with Firefox already installed, it is the default web browser.  In fact it is the only browser.  You should see a blue globe at the top of your desktop?  Clicking on that will open Firefox.

---

### Post by varunus on 2005-08-06
Open up synaptic using system->administration->synaptic package manager.  Make sure that mozilla-firefox and firefox are both installed, along with each corresponding "gnome-support" package.

---

### Post by coogor on 2005-08-08
[QUOTE=Darkscot]Ubuntu comes with Firefox already installed, it is the default web browser.  In fact it is the only browser.  You should see a blue globe at the top of your desktop?  Clicking on that will open Firefox.[/QUOTE]
well, not on my machine....*no* firefox was installed by default, konqueror was the default browser.
I run an 'aptitude install firefox' again, this time it installed the browser, but didnt create an entry in the k-startmenu....which is not perfect, but the least problem to me.
Thanks to all who replied.

---

### Post by C38a7r1zvl on 2005-08-08
Run kappfinder to add missing programs conveniently to your kmenu,

---

### Post by Lem on 2005-08-08
I got konqueror installed as default. The firefox in universe seems to be gnome-specific and wouldn't work for me.

I downloaded from getfirefox.com and followed the install instructions. Works fine, and this is my first day as a linux user.

---

### Post by Darkscot on 2005-08-08
[QUOTE=coogor]well, not on my machine....*no* firefox was installed by default, konqueror was the default browser.
I run an 'aptitude install firefox' again, this time it installed the browser, but didnt create an entry in the k-startmenu....which is not perfect, but the least problem to me.
Thanks to all who replied.[/QUOTE]

Sounds like you are using Kubuntu, rather than the standard Ubuntu?

Erm Duuh!  This question is in the Kubuntu forum isnt it?  Ooops!

---

### Post by C38a7r1zvl on 2005-08-08
I can't understand your problem. I personally use Kubuntu and the standard firefox package without any problem.

---

### Post by Gezzer on 2005-08-08
[QUOTE=][/QUOTE]
 i downloaded Ff 1.0.6 from the Mozilla site and installed it on the home partition as a stand alone program
have it working that way on 3 systems here at home

very easy to change or upgrade ...

---

