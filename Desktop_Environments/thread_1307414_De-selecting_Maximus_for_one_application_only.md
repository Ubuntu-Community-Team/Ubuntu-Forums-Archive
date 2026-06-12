---
title: "De-selecting Maximus for one application only ?"
date: 2009-10-31
forum: Desktop Environments
---

### Post by NE Key on 2009-10-31
I am happy with maximus set to default "on" on my netbook and know how to turn it "globally" off.

What I want to do is disable maximus only when running one specific application - Gambas2.

Is there a way of inserting "Maximus Off" into the command line that runs the application (and reverting when the application closes) ?

Perhaps a short script that says;
-Maximus Off
-Run Gambas2
-When Gambas2 closes then Maximus On

How do I do that ?

Any kind souls able to advise ?

---

### Post by Aearenda on 2009-10-31
I'm not on a machine with Maximus installed at the moment, but if I remember correctly there is a list of apps (or perhaps window classes) to ignore in Maximus' gconf settings - take a look in gconf-editor under apps->maximus. You should be able to add your program to the list.

UPDATE: It's /apps/maximus/exclude_class.

---

### Post by NE Key on 2009-11-03
Doh !  After hunting for the file you suggested - and failing to find it

I went;

System Tools>Configuration Editor from the menu and found the "Maximus Off" option.
Then turned it off for Gambas2

That worked but it does not work for the gambas applications that I then run.

Thanks for your help - It has got me very close to a solution with just a minor twitch for full success.

---

