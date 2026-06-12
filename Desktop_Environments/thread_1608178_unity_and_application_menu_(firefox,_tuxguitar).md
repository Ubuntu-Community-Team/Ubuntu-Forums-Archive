---
title: "unity and application menu (firefox, tuxguitar)"
date: 2010-10-28
forum: Desktop Environments
---

### Post by shufla on 2010-10-28
Hello,

I am using unity on 10.10.

I have irritating issue with tuxguitar (java clone of guitar pro). Menu shown on top of unity desktop has only one choice -- File, where I can only do Close (^W). So, for example, I cannot configure tuxguitar. Is it a bug or feature? How can I run this application with own menu, like...

...I have bizzare behaviour of firefox. It's menu is not in top of the screen, but in Firefox own window. Is it a bug or feature? How can I control it from user interface?

Update: Another application which has its menu unavailable is Chromium Browser.
Update2: I am a lame -- there are bugs related to this, eg here: [https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931) I will try to find out the solution and post here.
Regards,
Luke

---

### Post by shufla on 2010-10-28
Hello,

So solution is to use UBUNTU_MENUPROXY= to run application having such issue. More details here: [https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931](https://bugs.launchpad.net/ubuntu/+source/appmenu-gtk/+bug/659931)

I am looking for exclusion list for gconf.

---

### Post by gcbzzzz on 2011-06-06
UBUNTU_MENU_PROXY makes everything even worse.



try that:
1. open an xterm
2. UBUNTU_MENUPROXY=pidgin
3. pidgin

it will open pidgin, with the menu, success.
but now try to minimize or hide the application.... it will disapear and right after will un-minimize from the launcher dock. Fail.

---

### Post by Copper Bezel on 2011-06-06
This is no longer relevant. It refers to the 10.10 implementation of Unity under Mutter.

---

