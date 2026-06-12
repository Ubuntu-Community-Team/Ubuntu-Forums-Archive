---
title: "help: GNome will only load in failsafe"
date: 2007-08-13
forum: Desktop Environments
---

### Post by GuidoCalvano on 2007-08-13
Hey posted this in general help. This may be a more appropriate category:
[http://ubuntuforums.org/showthread.php?t=524468](http://ubuntuforums.org/showthread.php?t=524468)


The post:

 help: GNome will only load in failsafe
Yesterday night I shut down my computer a bit fast. I was in a rush. You know how it goes. The next morning having had very little sleep I wanted to show a girl my wonderful and downright morally superior OS. Logged in and all that loaded was a big brown screen and a sound juicer that was barely in it (the title bar was above the top edge of the screen).
None of the other characteristics of an OS like the two bars on the top and bottom of the screen or the cluttery icons on the desktop (the true symbol of the disorganised mind!). I am writing this message in the GNome failsafe session, that has just about everything running without problems, so I will be able to fulfil my plights, but I want to know what's wrong, because it really is quite unlike Linux to do this strange thing called screwing up I only vaguely recall from the time I used windows.
A further note is that I used the save session option from system->preferences-> session -> session options -> automatically save session.
Turning that option using the failsafe gnome did nothing for the conventional gnome. Can't get the gnome interface loaded after login. Just a ponderous brown plain of nothingness. How can I regain access to my conventional gnome?
Also note that during the turning off of the computer I kindof didn't pay attention to the computer that much as some of you by now might understand ehm... So not much more details I'm afraid...

Oh and do I run any risk of further screwing up my system if I install anything?

And I dont mind losing any configurations of my desktop by the way. Quite willing to reconfigure that. I just want things to go according to specs and not have to use failsafe anymore.

Thanks!!

---

### Post by GuidoCalvano on 2007-08-13
Problem solved!!

I had some advise elsewhere on the forum, where I stated very clearly I was willing to sacrifice some configurations of gnome but was not willing to reinstall applications.

He/she said; 
remove the .gnome directory. It was hidden so when I used failsafe gnome to get to my filesystem by getting places -> home folder and nautilus opened I also had to check view -> show hidden files to true.

I didn't remove it but instead moved it to a backup folder. This didn't work. Noticed another folder called gnome2. Moved this to the same backup folder: Loged in again using ctrl alt backspace Success.

---

