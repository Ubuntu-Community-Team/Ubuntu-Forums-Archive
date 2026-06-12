---
title: "(dot profile) .profile manipulation - setting up an alias"
date: 2009-04-20
forum: General Help
---

### Post by jzacsh on 2009-04-20
[COLOR="Red"][B]UPDATE: THIS IS A DUPLICATE - just found this:
[http://ubuntuforums.org/showthread.php?t=264917](http://ubuntuforums.org/showthread.php?t=264917)
[/B][/COLOR]

****I'm still quite new to UNIX/Linux, but trying to learn so bear with me**
I don't know if this falls under all linux variants or just Ubuntu, etc..

I learned in an Intro UNIX class that .profile holds all kinds of login commands. I'd like to add the following to my .profile, so I can use the alias every day:
```
alias edu="cd $HOME/Dropbox/Public/edu_school ; pwd ; ls -la"
```
I tried placing this in the .profile of my account on my school's server and it works (*once logged, I can type **edu** and the specified commands execute*).

_Here on Ubuntu 8.10. _
I also tried this plainly at my terminal's prompt (before sticking it into .profile) and it works. For some reason I can't get it to work when appending it to the .profile file. Should I be doing something differently on this system (is .profile an old way of doing things?)?

---

### Post by Alterax on 2009-04-21
> **jzacsh said:**
> [COLOR="Red"][B]UPDATE: THIS IS A DUPLICATE - just found this:
[http://ubuntuforums.org/showthread.php?t=264917](http://ubuntuforums.org/showthread.php?t=264917)
[/B][/COLOR]

****I'm still quite new to UNIX/Linux, but trying to learn so bear with me**
I don't know if this falls under all linux variants or just Ubuntu, etc..

I learned in an Intro UNIX class that .profile holds all kinds of login commands. I'd like to add the following to my .profile, so I can use the alias every day:
```
alias edu="cd $HOME/Dropbox/Public/edu_school ; pwd ; ls -la"
```
I tried placing this in the .profile of my account on my school's server and it works (*once logged, I can type **edu** and the specified commands execute*).

_Here on Ubuntu 8.10. _
I also tried this plainly at my terminal's prompt (before sticking it into .profile) and it works. For some reason I can't get it to work when appending it to the .profile file. Should I be doing something differently on this system (is .profile an old way of doing things?)?

I wouldn't call it outdated per se, but the normal place to put aliases is in the user's .bashrc file (nano ~/.bashrc).  It'll even have commented-out examples showing the proper syntax.  Once you make the alteration, it won't take effect until a new instance of bash is started--which you can accomplish by either logging out and back in, or closing the window and opening a new one.

---

### Post by jzacsh on 2009-04-21
> **Alterax said:**
> I wouldn't call it outdated per se, but the normal place to put aliases is in the user's .bashrc file (nano ~/.bashrc).

So its not quite what i thought:
anything you want executed at login, you can place in one file (thought that file would be .profile, but turns out to be .bashrc, regardless...)  - but you said "normal place to put _**aliases**_", does that mean there's still some use to .profile? (i noticed a .bash_profile as well)

---

