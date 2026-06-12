---
title: "Firefox 2.0.0.2 crashes (disappear)"
date: 2007-03-05
forum: Desktop Environments
---

### Post by canopytruder on 2007-03-05
Hi, I 've been working with Ubuntu 6.10 for two weeks, and I'm not sure when exactly but Firefox 2.0.0.2 started to crash. There is no specific thing I do that actually causes this crashes.
The browser just closes (disappear) out of the blue and then when I restart it it asks me "do you want to restore the session?".:confused: 

Someone has an idea?

thanks

---

### Post by konungursvia on 2007-03-05
It can depend on the extensions you've added on to firefox, or the nature and number of the tabs you're opening. Try getting rid of a few addons you don't really use any more.

---

### Post by canopytruder on 2007-03-08
Thanks for posting a reply, though I tried with the add ons, I just left (delicious bookmarks, stumble upon, down them all and flash got)..
but it keeps crashing....

---

### Post by Rui Pais on 2007-03-08
hi.
try with a fresh profile to see if you just got some broken config.

Close all firefox window and on terminla do:
```
mv .mozilla/firefox .mozilla/firefox_TEMP_BACKUP
```

Launch browser and see if it stills crash.

---

### Post by Robor on 2007-03-08
Launch firefox from the command line and see if you get any errors when it crashes.  I've got Firefox crashing on 2 different systems.  I filed a bug on it.  Not sure why but when I tried to insert a link it's only giving me the link popup - the text window doesn't show.  Anyway, here's the URL:  [https://launchpad.net/ubuntu/+source/firefox/+bug/86338](https://launchpad.net/ubuntu/+source/firefox/+bug/86338)

---

### Post by der_joachim on 2007-03-08
I had similar issues. It turned out that flash had automagically reverted to version 7 instead of version 9. Anyhoo, reinstalling flash 9 did the trick.

---

### Post by canopytruder on 2007-03-14
thanks to anyone who replied me so far

i tried uninstalling all the plugins, resetting firefox from the terminal and I checked i have flash 9, and obviously it keeps crashing

---

### Post by canopytruder on 2007-03-15
I'm not sure it may help, but the same thing happens when I'm using openoffice/presentation, could it be a common/crossed problem , though presentation is not always open when firefox crashes..

---

