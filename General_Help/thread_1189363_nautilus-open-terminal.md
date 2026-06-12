---
title: "nautilus-open-terminal"
date: 2009-06-16
forum: General Help
---

### Post by xender69 on 2009-06-16
hi,

had the nautilus-open-terminal installed and working fine, but I see that it defaults to the desktop, how can I change it so it goes to my home directory instead of /home/mydir/Desktop ?

Tks in advance.

---

### Post by Amilo1718 on 2009-06-16
i wouldn't mess with nautilus :p

and it defaults to root cuz it IS root

---

### Post by Muscovy on 2009-06-16
This is a file browser view, right? I don't think there's a way to change it from desktop, though it's only one click to get to home (root).

  And a warning from me as well: be careful what you do with it. You can remove or replace ANYTHING this way. What do you need it for?

---

### Post by mc4man on 2009-06-16
You may wish to explain a little further.

The purpose and use of "nautilus-open-terminal" is to get a right click option on directories that opens a terminal at **that directory** prompt. (simply eliminates the process of opening a terminal and typing 'cd /path/to/directory' 

Where does 'Desktop' and 'home directory' come into play here? (other than opening a terminal at the Desktop prompt

---

### Post by xender69 on 2009-06-17
> **mc4man said:**
> You may wish to explain a little further.

The purpose and use of "nautilus-open-terminal" is to get a right click option on directories that opens a terminal at **that directory** prompt. (simply eliminates the process of opening a terminal and typing 'cd /path/to/directory' 

Where does 'Desktop' and 'home directory' come into play here? (other than opening a terminal at the Desktop prompt

Ah I see that makes sense, because I right click on the desktop to open the terminal, it presents me with the /home/mydir/Desktop.  What I would like to do is open the terminal and default it to /home/mydir instead of /home/mydir/Desktop even if I right click on the desktop.

---

### Post by mc4man on 2009-06-18
What I think your describing is a normal open a terminal (opens at home dir. prompt

If so it would be easier to just put a terminal launcher in your top or bottom panel or on the desktop and click on it.

For a right click on Desktop and open terminal at 'normal' prompt then I quess you could try to find or build a version pre 0.8-1 (though it may have other 'bugs'

or make a right click nautilus script (scripts added to ~/.gnome2/nautilus-scripts will show up in r.click -> scripts

```
#!/bin/bash
cd $HOME
gnome-terminal 
```

For something to show up directly in the r. click on Desktop it need to be a nautilus extension

There may be other ways ..? or a way to edit the source of the current nautilus-open-terminal to revert to r. click on desktop opens terminal at home prompt

(personally I just open the Applications -> accessories menu and drag a terminal to the top panel

If you mean something else then post the prompt you'd like to see

---

### Post by xender69 on 2009-06-18
> **mc4man said:**
> What I think your describing is a normal open a terminal (opens at home dir. prompt

If so it would be easier to just put a terminal launcher in your top or bottom panel or on the desktop and click on it.

For a right click on Desktop and open terminal at 'normal' prompt then I quess you could try to find or build a version pre 0.8-1 (though it may have other 'bugs'

or make a right click nautilus script (scripts added to ~/.gnome2/nautilus-scripts will show up in r.click -> scripts

```
#!/bin/bash
cd $HOME
gnome-terminal 
```

For something to show up directly in the r. click on Desktop it need to be a nautilus extension

There may be other ways ..? or a way to edit the source of the current nautilus-open-terminal to revert to r. click on desktop opens terminal at home prompt

(personally I just open the Applications -> accessories menu and drag a terminal to the top panel

If you mean something else then post the prompt you'd like to see

Awesome! thanks, just what I needed.

---

### Post by adrianx on 2009-06-18
xender69, there is actually a gconf option to change nautilus-open-terminal's behaviour:

1. Applications > System Tools > Configuration Editor
2. Navigate to /apps/nautilus-open-terminal
3. Click on the checkbox next to desktop_opens_home_dir to set it to true.

I prefer to set it to false. IIRC, nautilus-open-terminal used to open "/home/user" from the desktop. To me it makes more sense to open "/home/user/Desktop" from "/home/user/Desktop". :D


**OR **(If you prefer)
```
gconftool-2 --set --type bool /apps/nautilus-open-terminal/desktop_opens_home_dir true
```

---

