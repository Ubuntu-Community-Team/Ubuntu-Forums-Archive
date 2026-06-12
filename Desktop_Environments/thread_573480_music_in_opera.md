---
title: "music in opera"
date: 2007-10-11
forum: Desktop Environments
---

### Post by Balvinder25 on 2007-10-11
hi all,
          ive just installed opera on ubuntu 7.04 could any one tell me how to play music on youtube website..it jsut says tht u dont have flash pluging ,installing tht dosent work aswell..any help any one.

---

### Post by por100pre1 on 2007-10-11
Flash plugin with Opera? They both work fine together here. Use this Opera:

```
sudo su -c 'echo deb http://archive.canonical.com/ubuntu feisty-commercial main >> /etc/apt/sources.list'
```

```
sudo aptitude update && sudo aptitude install opera
```

Be sure to use Flash from the repos too.

---

### Post by D-EJ915 on 2007-10-11
Simply install firefox and download all the plugins you want (flash, etc.) and then in Opera go to tools->options then click on advanced, on the list on the left click on "content" then it'll have a "plug-in options" button, click on that and depending on what you have installed there is a list at the bottom, mine looks like this:

/usr/lib/opera/plugins:/usr/lib/mozilla/plugins:/usr/lib/firefox/plugins

you can put where your firefox/whatever plugins are then click "find new" and it should update to include them.  Voila!  This is at least how it works for me.

---

### Post by Balvinder25 on 2007-10-12
hi all,     
           thans for that quick response..sorry to dissapoint but i couldnt get the the music working even now..>what i did is i copied all the plugins used by mozilla firefox from /usr/lib/mozilla/plugins to /usr/lib/opera/plugins..even tht  didnt click...so could any one please explain in simple terms as to what i have to do to get this working..i use youtube alot and switching back to mozilla just for youtube seems a big nuisance..

---

