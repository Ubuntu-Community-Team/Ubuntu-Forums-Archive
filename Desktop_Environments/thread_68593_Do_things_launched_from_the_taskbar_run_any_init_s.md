---
title: "Do things launched from the taskbar run any init script?"
date: 2005-09-23
forum: Desktop Environments
---

### Post by Blueshell on 2005-09-23
When launching an application from the taskbar, are any init scripts run immediately before launch?  I know, for example, that I can use .gnomerc to set environment variables and the like before the desktop gets launched when I log in, but that only runs once per login.  I'm looking for something that runs once per launch.  I've done quite a bit of searching, but have yet to find any hint that this might happen, nor is it clear to me even where to look to find the code that Gnome uses to launch something from the taskbar.  (E.g., when I click, what code runs?  What function and what file is it in?  If I could find the start of the entire cascade, it's conceivable that I could at least read the code directly, but figuring out that entrypoint without knowing where to start is a major undertaking.)

[This came up in the context of wanting Emacs to inherit environment variables when launched from the taskbar, as opposed to from within a shell.  Sure, I can make .gnomerc define those, but changing my mind means logging out & in again.  And sure, I could make Emacs itself be intelligent on startup, but other applications aren't nearly so flexible, and it'd be nice to know if there's a defined way that this is supposed to happen.]

Thanks!

---

### Post by garlito on 2005-09-23
Why don't you launch a script instead your app ?

For example, few gtk1 applications don't look very well with my locale utf-8. I launch it after changing locale:

#!/bin/bash
export LANG=en_US
audacity&

And I put the script into the panel like it was an application

Try that

---

### Post by Dooglus on 2005-09-23
Alternatively, right-click on the icon in the taskbar, choose "properties", and in the command box, instead of just having:
```
emacs
```
for example, edit it to say:
```
sh -c "LANG=en_US TROOSERS=baggy NAME=debbie emacs"
```
That will set the 3 environment variables for the duration that Emacs runs.  Don't use semi-colons between them - if you do, you'll need to use 'export' as well, and it all starts getting (even more) ugly.  You do need the quotes however.

---

### Post by Blueshell on 2005-09-24
Both good suggestions.  I'd hoped that there was a more elegant way (I'm surprised that there's no generalized hook mechanism for things launched from the panel---though of course nobody has yet said it -doesn't- exist, just that no one has pointed out that one -does-), because having to write a script per application doesn't  scale well, and having to hand-craft a command-line per application is a maintenance disaster if they need to stay in sync.  But for the small number of apps I actually expect to put in the taskbar, I suppose I can just write a one-liner for each that just calls out to a common worker.

(Some experimentation reveals that no arguments or environment variables seem to be -set- by the launch, or I could write a single script that uses its arg (or whatever) to know which program to launch, hence not having to write one per app on the taskbar.  That's why I said that having to have a script per app doesn't scale.  OTOH, I -could- use a command line whose argument to a script (same script for each item in the taskbar) is the app to run, which -would- scale---it's just more work per app 'cause I'd have to put that one-liner in each definition instead of being able to just write the name of the application and that's all.  But at least it would mean that I'd write one launch script no matter how many apps I put in the taskbar.)

Still kinda surprised that taskbar launch neither sets any variables nor tries to enable any hooks by calling a script, if present.  Seems like a strange design omission.

---

### Post by Dooglus on 2005-09-24
[QUOTE=Blueshell]Both good suggestions.  I'd hoped that there was a more elegant way (I'm surprised that there's no generalized hook mechanism for things launched from the panel---though of course nobody has yet said it -doesn't- exist, just that no one has pointed out that one -does-), because having to write a script per application doesn't  scale well, and having to hand-craft a command-line per application is a maintenance disaster if they need to stay in sync.  But for the small number of apps I actually expect to put in the taskbar, I suppose I can just write a one-liner for each that just calls out to a common worker.

(Some experimentation reveals that no arguments or environment variables seem to be -set- by the launch, or I could write a single script that uses its arg (or whatever) to know which program to launch, hence not having to write one per app on the taskbar.  That's why I said that having to have a script per app doesn't scale.  OTOH, I -could- use a command line whose argument to a script (same script for each item in the taskbar) is the app to run, which -would- scale---it's just more work per app 'cause I'd have to put that one-liner in each definition instead of being able to just write the name of the application and that's all.  But at least it would mean that I'd write one launch script no matter how many apps I put in the taskbar.)

Still kinda surprised that taskbar launch neither sets any variables nor tries to enable any hooks by calling a script, if present.  Seems like a strange design omission.[/QUOTE]
 I don't really see your problem.

If you need to see a variable for all apps, set it in .gnomerc.

If you need to set it differently for one of the apps, set it in the properties of the app's launcher.

What's your need that this doesn't cater for?

---

