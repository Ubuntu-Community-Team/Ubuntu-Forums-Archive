---
title: "&quot;T-ish&quot; scroll arrow glitch"
date: 2007-04-01
forum: Desktop Environments
---

### Post by fearpi on 2007-04-01
Some weeks ago, I installed Glossy P ([here]("http://art.gnome.org/themes/gtk2/571")), Glossy P2 ([here]("http://www.gnome-look.org/content/show.php/?content=43843")), and T-ish [aqua styles] ([here]("http://www.gnome-look.org/content/show.php/?content=30859")). They all had the same glitch - whenever a scrollbar was taken all the way to the top or bottom, that particular scroll arrow was replaced by a boring default arrow. Interestingly, the only application that doesn't exhibit this behavior is Firefox.

Now, I was installing Ubuntu 6.06 LTS on a friend's machine the other day. Once it was installed, I downloaded the themes, and they all appeared to work perfectly - until I upgraded to 6.10 and updated all the packages. Then they didn't work at all. At that point I installed gtk2-engines-pixbuf. Then, the themes seemed to work again, except that now the scroll arrows were exhibiting the exact same glitch that they do on my machine. Why would this be, and how can I fix it?

---

### Post by fearpi on 2007-04-01
Bump.

---

### Post by 4KvRMU7Nnv on 2007-04-05
I hear ya' man.  I have the same problem.  I don't think its a glitch though, i think its just laziness.  keep looking around though, some themes go the extra 9 yards to get those working right...you might be able to fix it yourself...try renaming stuff in the theme file.

EDIT:
I tried doing this but it was too complicated and i don't think itll work.  you say it worked fine on dapper though?  interesting...

---

### Post by fearpi on 2007-04-06
A few days ago I was messing around with the theme file and got it working. My guess is that the specs for themes using that particular engine were made more strict since these themes were released. I can't look at the files right now because I'm in Windows, but I can tell you from memory that it has to do with the INSENSITIVE state of the arrows not being explicitly specified. All I had to do was copy the data from the regular state for each arrow and change it to INSENSITIVE and all was well.

---

