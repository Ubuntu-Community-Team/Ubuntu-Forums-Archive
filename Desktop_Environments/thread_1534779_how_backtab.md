---
title: "how? backtab"
date: 2010-07-20
forum: Desktop Environments
---

### Post by betlog on 2010-07-20
I am trying to make my 'Walk through windows Alternate" work as expected.. and can't.

alt-tab = walk through windows (regular)
alt-shift-tab = walk through windows backwards  (regular)
..i am sure we are all familiar with these
and...
meta-tab = walk through windows (alternative) ... sure, no problem
BUT
meta-shift-tab = walk through windows backwards (alternative)
totally doesnt work
looking at the regular alt-shift-tab, it's binding is  labelled as alt-shift-BACKTAB
...wtf is backtab?
...how do i bind the alternative window cycler to it?

has nobody else noticed this? (looks like a bug to me)
(the binding shown in the attached screenshot SHOULD work, but fails)

---

### Post by betlog on 2010-07-20
i just tried binding alt-shift-tab to 'walk through windows' (the normal/primary one) and this too fails.. despite those being the buttons actually pressed to use it on its default binding.

... something about ?shift? being held that makes tab into backtab?

What text file are global shortcuts stored in?

---

### Post by betlog on 2010-07-20
Easiest option is to 
$ systemsettings 
general tab > mouse & keyboard > global keyboard shortcuts
select 'KDE Component' ...kWin 
select "file" "export scheme"
save it somewhere,, edit the file, replace Tab with BackTab wherever needed
then "file" "import scheme"
sheesh... workaround much!? 
x}

original (broken):
```
 Walk Through Windows=Alt+Tab
Walk Through Windows (Reverse)=Alt+Shift+Backtab
Walk Through Windows Alternative=Meta+Tab
Walk Through Windows Alternative (Reverse)=Meta+Shift+[COLOR=Red]Tab[/COLOR]
```edited better
```
 Walk Through Windows=Alt+Tab
 Walk Through Windows (Reverse)=Alt+Shift+Backtab
 Walk Through Windows Alternative=Meta+Tab
 Walk Through Windows Alternative (Reverse)=Meta+Shift+[COLOR=SeaGreen]BackTab[/COLOR]
```

---

### Post by betlog on 2010-07-20
oh. I may have markde this as SOLVED, but as far as I am concerned its also a bug... or more like an oversight.

---

