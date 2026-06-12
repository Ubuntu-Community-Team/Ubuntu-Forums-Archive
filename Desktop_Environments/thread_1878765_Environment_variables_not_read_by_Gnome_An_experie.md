---
title: "Environment variables not read by Gnome: An experience report and some questions."
date: 2011-11-10
forum: Desktop Environments
---

### Post by lupoph on 2011-11-10
Hello!

*Actually, I figured out a solution for my problem already. It's just that, wherever I looked, I found only solutions that didn't work in my case. So I figured a little experience report might help other people with the same or a similiar problems. *

My problem basically came down to the question "how does the system get its environment variables for each user?". 

_My way to solving the problem_
[LIST]
 [*]When opening emacs with the Alt+F2 "Run Application" dialog, the *(getenv "VARIABLE")* function gave nil (i.e. "not defined") for my custom variables defined in .bashrc, causing my emacs scripts not to be loaded.
 [*]When running *sh* in the Alt+F2 dialog, I found that here too the variables were not defined. I concluded, that gnome never ran 
 the .bashrc. Also I found, that "sh" was pointing to "/bin/dash" rather than "/bin/bash" on my system ("$SHELL" was "dash"). 
 [*]Using Google I found countless advices, basically each telling me to use different files and redirect to the .bashrc, e.g. the files .profile, .bash_profile and .xsession. Checking some of those I found that they checked whether the variable BASH_VERSION is defined (here only meaning "not empty") with *[ -n "$BASH_VERSION" ]*). However, because my .bashrc makes heavy use of bash features (e.g. export functions) removing that check obviously was not an option.
 [*]In /etc/passwd I found that many system-internal "users" had /bin/sh as their shell. So I figured, changing sh a link to /bin/dash to a link to /bin/bash might cause my .bashrc to be read, and indeed it did. 
[/LIST]

_The open question_

What is the proper POSIX way of setting user variables, especially when NOT having root access to the target platform?

I figured that maybe .profile is the way to go, but is this true? I.e., will any POSIX compatible platform indeed run this file, when the user logs in with any shell or desktop environment?

Or is there just no way around figuring out the startup process for each platform?

---

