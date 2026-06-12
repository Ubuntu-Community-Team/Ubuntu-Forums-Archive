---
title: "Evince - problems with printing with Unity / Gnome3"
date: 2017-06-28
forum: Desktop Environments
---

### Post by nicolasdiogo on 2017-06-28
Hi,

I was looking for a solution to this problem a while ago and since I solved it but I can not find it anywhere ... I decided to put it in this forum in case others have similar issues

In my case I had an application that would not print any documents.

The menu showed a greyed out option for 'print'

after looking around, I found that the problem in my case was a setting changed in he configuration of gnome/unity

and it can be changed by:

[LIST=1]
[*]open  dconf-editor
[*]go to 'Desktop' / 'Applications' / 'lockdown'
[*]change value of 'Disable printing' to 'false'
[/LIST]

Your applications should have the option to print available again

---

