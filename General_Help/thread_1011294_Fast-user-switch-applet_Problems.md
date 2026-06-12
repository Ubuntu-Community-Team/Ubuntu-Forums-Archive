---
title: "Fast-user-switch-applet Problems"
date: 2008-12-14
forum: General Help
---

### Post by dstein on 2008-12-14
I tried fixing this myself but was unsuccessful. When I try to switch users, I get a blank screen and the system seems unresponsive. This is before a password is requested for the user being switched to. I am then required to reboot my computer. If anyone knows a solution to this problem, please let me know. I found the problem mentioned on the internet, but no solution.

I then proceeded to try removing fast-user-switch-applet but get the following error in aptitude: ```
Need to get 0B of archives. After unpacking 3662kB will be freed.
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: fast-user-switch-applet but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
ubuntu-desktop

Score is 119

Accept this solution? [Y/n/q/?] 
```

Entering 'n' repeats the question. How can I remove the fast-user-switch applet? I understand that this may not be a solution to my original question, but it lead to my latest question. I tried removing it as a dependency from Ubuntu-desktop in /var/lib/dpkg, but I am still unable to remove it.

Any help would be great. Thanks.

---

### Post by bren on 2008-12-18
i am also have FUSA problems but my problem is that the applet has disappeared from the top right corner of the screen.

i also thought of uninstalling fast-user-applet by means of 


$sudo apt-get remove fast-user-applet

but did not go through with it when it said it would also remove ubuntu-desktop.

i next tried to find the correct command to force reinstall in apt-get but failed after a general google and a look at man page for apt-get

can anyone help or suggest another tactic.

[ps FUSA seemed to disappear about a week after messing about with adding a skype plugin to pidgin which might have screwed with the IM status config bit of FUSA in some way]

bren

---

