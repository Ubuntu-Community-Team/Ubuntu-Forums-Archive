---
title: "[SOLVED] emacs process-environment under gnome"
date: 2008-11-27
forum: Desktop Environments
---

### Post by phorminx on 2008-11-27
When I start emacs from the gnome applications menu, it seems to start in a strange setting concerning environment variables (available inside emacs via the emacs variable process-environment). It seems that emacs doesn't know about my ~/.bashrc. But even a basic variable like HOSTNAME is undefined. What do I have to do in order to make these environment variables available within emacs?

I guess all this is not specific to emacs but it seems to be related with how gnome starts a process like emacs. ps says that the ppid of the emacs process is 1.

---

### Post by jpkotta on 2008-11-29
Try using the function getenv.

---

### Post by phorminx on 2008-11-29
> **jpkotta said:**
> Try using the function getenv.

You mean the emacs built-in getenv? Inside emacs, getenv gives you the environment variables individually. The emacs variable process-environment gives you all the environment variables known to emacs. So both methods give you the same. Of course, there is also setenv, i.e., I could set inside emacs all the missing variables via setenv. But that means to reinvent the wheel. If at all, it appears more reasonable to make emacs a subprocess of a shell so that this shell can first set the environment variables.

Am I missing something here?

---

### Post by phorminx on 2008-11-29
I guess, being new to gnome, my question is really why (all?) applications are started directly by the root process with "nothing else in between".

---

### Post by jpkotta on 2008-11-30
I've never used the process-environment function, only the getenv function (Xemacs doesn't have process-environment AFAICS).  I also don't use Gnome, so I guess I have always specified exactly how I want Emacs to start.

I suspect that the ppid becomes 1 because Gnome is exec'ing at some point when it starts up Emacs.  This is something that I do to achieve that effect:
```

function daemon
{
    (exec "$@" >&/dev/null &)
}
alias E="daemon xemacs"
```
It makes sense because then you don't have a shell running for each launched app (Gnome), and the app is completely independent of the shell that initially launched it (if I used the above in a terminal).  When a process's parent dies, it gets reparented to init (pid 1).  This doesn't necessarily have anything to do with the lack of environment though.  

You are absolutely right that it should be started as a subprocess of a shell to get a proper environment.  A quick fix is to make a small script to start Emacs and add that to the menu.  It seems like there should be a way to get Gnome to be not-braindead though.

---

### Post by phorminx on 2008-11-30
> **jpkotta said:**
> I suspect that the ppid becomes 1 because Gnome is exec'ing at some point when it starts up Emacs. 

Thanks, that makes sense.
 
> **jpkotta said:**
> You are absolutely right that it should be started as a subprocess of a shell to get a proper environment.  A quick fix is to make a small script to start Emacs and add that to the menu.  It seems like there should be a way to get Gnome to be not-braindead though.

OK, I guess I found the proper solution:

When gnome is started by Xsession, the latter program sources

/etc/X11/Xsession.d/40x11-common_xsessionrc

The man page of Xsessino says:

```
  /etc/X11/Xsession.d/40x11-common_xsessionrc
     Source  global  environment  variables.  This script will source
     anything in $HOME/.xsessionrc  if  the  file  is  present.  This
     allows  the user to set global environment variables for their X
     session, such as locale information.
```

So putting these things into $HOME/.xsessionrc should be what I want.

---

