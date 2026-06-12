---
title: "changing konsole name from shell"
date: 2008-11-25
forum: Desktop Environments
---

### Post by g.a. on 2008-11-25
Hi,

I would like to change the session name of the Konsole application from the shell so that I can put the command in a script. 

This is currently done with the mouse with the command "rename session" under the menu "view".

Any hint?

Thanks,
g.

---

### Post by GameManK on 2008-11-25
You can run konsole like this:

konsole -p tabtitle=mynewfancytitle

To get customize the tab title of a newly launched session.
(Got this from konsole --help and some guessing)

---

### Post by g.a. on 2008-11-27
thanks for the reply,

however, the -p option is not available, I run the --help-all to list the available options but the only one 'close' to my need is -T that opens a new window with my funcy name. However I would like to change the session name of the current tab, is there a way to use the -T option without opening a new window?

Here is my konsole version:

konsole -v

Qt: 3.3.8b
KDE: 3.5.9
Konsole: 1.6.6

bye,
g.

---

### Post by g.a. on 2008-11-27
thanks for the reply,

however, the -p option is not available, I run the --help-all to list the available options but the only one 'close' to my need is -T that opens a new window with my funcy name. However I would like to change the session name of the current tab, is there a way to use the -T option without opening a new window?

Here is my konsole version:

konsole -v

Qt: 3.3.8b
KDE: 3.5.9
Konsole: 1.6.6

bye,
g.

---

### Post by GameManK on 2008-11-27
I think the -p tabtitle option is just the KDE4 equivalent of the -T option :-\

---

### Post by g.a. on 2008-11-28
thanks, but is there a way to avoid opening a new window and apply the name change to the "current" tab ?

the rational for that is the following:

I need to open several ssh on remote machines and I have each ssh in a different tab. to avoid confusion I rename the tab with the machine name. since the ssh is made automatically in a script I would like the script to change the tab name too without doing it by hand.

thanks again,
g.

---

### Post by GameManK on 2008-11-29
Since presumably you're launching new tabs in konsole anyway, then why can't you use the option in your script?

konsole --new-tab -p tabtitle=foo
(on KDE4)

---

### Post by somekool on 2008-12-30
> **g.a. said:**
> thanks, but is there a way to avoid opening a new window and apply the name change to the "current" tab ?

the rational for that is the following:

I need to open several ssh on remote machines and I have each ssh in a different tab. to avoid confusion I rename the tab with the machine name. since the ssh is made automatically in a script I would like the script to change the tab name too without doing it by hand.

thanks again,
g.

With Konsole from KDE3, you can do 

echo -en "\e]0;Set Window Title\a"

and

echo -en "\e]33;Set Tab Name\a"

in KDE4, I don't know, there is a bug report you can vote for if you want.

[http://bugs.kde.org/show_bug.cgi?id=179142](http://bugs.kde.org/show_bug.cgi?id=179142)

---

