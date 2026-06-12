---
title: "How to disable the Gnome panel completely?"
date: 2008-11-11
forum: Desktop Environments
---

### Post by 0x_ on 2008-11-11
How to disable the Gnome panel completely?
If I kill it restarts.

---

### Post by anando on 2008-11-11
> **0x_ said:**
> How to disable the Gnome panel completely?
If I kill it restarts.

Right click on the panel(s) and choose 'Delete This Panel'

---

### Post by hictio on 2008-11-11
> **anando said:**
> Right click on the panel(s) and choose 'Delete This Panel'

That option is not enabled for the main, the one on the top, Gnome Panel; at least on Intrepid.

[URL=http://img528.imageshack.us/my.php?image=notenableddr2.png]
[IMG]http://img528.imageshack.us/img528/997/notenableddr2.th.png[/IMG]
[/URL]

---

### Post by dlm4849 on 2008-11-11
Not positive its the same for Intrepid, but what I do in Hardy is go to Sessions, click on current sessions, remove the gnome-panel entry, then close everything you dont want starting up with your computer then go to the session options tab and click remember currently running apps.

Hope this helps.

---

### Post by brodae on 2008-11-11
There is no gnome-panel session option for me. I have no need for it anymore, now that I use AWN, and I'd MUCH rather have the desktop space than a black bar sitting there. I notices that the other person on this thread who is having problems has installed the Dust theme. I think it's fair to assume that we both are readers of Tombuntu, considering the Dust theme and the want to get rid of gnome-panel.

---

### Post by dlm4849 on 2008-11-11
You are looking on the current session tab, not startup programs, right? If so, Im not sure of any other way to disable it short of uninstalling it...

Hopefully someone with Intrepid can help out soon.

---

### Post by scradock on 2008-11-12
I'm running Intrepid, and the top panel does show "Delete this panel" as enabled when I right-click. I don't want to get rid of the panel, so I haven't tried clicking on "Delete this Panel", but it should work.

Maybe it is greyed out if that is the last active panel - I have a bottom panel too.

I would take the suggestion of uninstalling the gnome-panel package(s) if you really want to be rid of it completely. Why have the package installed if you aren't going to use it? Even worse would be to have the package running, using resources, but not showing any panels......

---

### Post by hictio on 2008-11-12
> **scradock said:**
> 
~snip~
Maybe it is greyed out if that is the last active panel - I have a bottom panel too.
~snip~


Forgot to mention, I'm only running with one Panel, the top one.

---

### Post by free-martin on 2008-11-12
try:

```

sudo mv /usr/bin/gnome-panel /usr/bin/gnome-panel.bak
killall gnome-panel

```

:-)

but remember it!

---

### Post by 0x_ on 2008-11-12
thanks for your input!
the "delete" option is also grayed out for me! there has to be a other way to do this than deleting (renaming) the binary!

---

### Post by maep on 2008-11-22
> **free-martin said:**
> try:

```

sudo mv /usr/bin/gnome-panel /usr/bin/gnome-panel.bak
killall gnome-panel

```

:-)

but remember it!

i would not recommend doing that. it breaks the gnome-panel for all other users as well.
this is better:

start gconf-editor
navigate to /desktop/gnome/session/required_components_list
remove panel from the list
log out, log in
done

best regards, maep

---

### Post by 0x_ on 2008-11-28
thanks maep!

---

