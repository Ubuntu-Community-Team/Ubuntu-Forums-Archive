---
title: "Display username instead of full name 12.10"
date: 2012-11-24
forum: Desktop Environments
---

### Post by aykoola on 2012-11-24
Hi.

Didn't manage to find a google solution for this, but i'm wondering how could i have my upper panel display my username instead of full name in the top right corner? It's taking way too much space on my panel this way...

Thank you!

---

### Post by JoeHallenbeck on 2012-11-25
Hey, 

I'd definitely be interested too if there's any way how to set that.

A few weeks ago I was forced to get rid of the Action Buttons panel plugin and use the normal Log Out menu option for the same reason as you described. Maybe that would work out for you at the moment?

---

### Post by aykoola on 2012-11-25
Will try. Thank you!

---

### Post by Toz on 2012-11-25
It appears the plugin is displaying the value in the name/comment field of the /etc/passwd file. You can either change it manually in that file (not recommended) or use the "Users and Groups" application in Settings Manager. Select the user account and click on the first "Change" option. The change you make here will change the name that is displayed by the Actions plugin.

It also appears that this field is used by lightdm on the login screen.

---

