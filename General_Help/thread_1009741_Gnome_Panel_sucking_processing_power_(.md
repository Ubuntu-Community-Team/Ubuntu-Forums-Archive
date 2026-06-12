---
title: "Gnome Panel sucking processing power :("
date: 2008-12-12
forum: General Help
---

### Post by skeetlez on 2008-12-12
my gnome panel is sucking 50% of my processing power and i would like to have it removed completely, i have cairo dock anyways...

so can someone be kind enough to help me? :)

---

### Post by eternalnewbee on 2008-12-13
Right-click on the panel, and click on Delete This Panel.
Btw, it's advised to keep one panel, if you're not an experienced user, and might end up looking for apps you can't find.

---

### Post by skeetlez on 2008-12-13
oh i should've been more clear, sorry...what i wanted to do is to delete the last panel, the one that does not have the delete option

and i'm fairly confident that i have enough experence with ubuntu to survive with my cairo dock ^_^

---

### Post by eternalnewbee on 2008-12-13
> You can delete all panels, although not the last one through the right click menu. The last one can be removed by going into the Sessions utility and removing from the list there.
From here:
[http://brainstorm.ubuntu.com/idea/921/](http://brainstorm.ubuntu.com/idea/921/)

---

### Post by skeetlez on 2008-12-13
hmm...odd...i dont have a gnome-panel launcher in my sessions utility

maybe beacuse i am on 8.10?

---

### Post by jlochhead on 2008-12-13
You could try and add a session command to kill gnome-panel at startup.

Might not work...

...Just tried a killall on gnome-panel and it pops straight back up again. Very strange, sure I could do it in 8.04.

Maybe consider going to 8.04 in the mean time?

---

### Post by eternalnewbee on 2008-12-13
> Maybe consider going to 8.04 in the mean time?
Just for the panel?...

---

### Post by jlochhead on 2008-12-13
If it is sucking that much power then why not?

The difference between 8.04 and 8.10 is only minimal.

---

### Post by eternalnewbee on 2008-12-13
> If it is sucking that much power then why not?

The difference between 8.04 and 8.10 is only minimal.
There just might be a way to solve this in 8.10.

> to remove gnome panel completely just delete gnome-panel from your /usr/bin/ folder keep in mind that you might need it at an later time so make a copy of it
From here:
[http://ubuntuforums.org/showthread.php?t=405721](http://ubuntuforums.org/showthread.php?t=405721)

> Code:

$killall gnome-panel

From here:
[http://ubuntuforums.org/showthread.php?t=652367](http://ubuntuforums.org/showthread.php?t=652367)

---

### Post by skeetlez on 2008-12-13
thanks! it worked perfectly ^_^

---

### Post by eternalnewbee on 2008-12-13
Glad it worked. Please remember to mark your thread as solved, under [COLOR="Red"]Thread Tools[/COLOR].

---

