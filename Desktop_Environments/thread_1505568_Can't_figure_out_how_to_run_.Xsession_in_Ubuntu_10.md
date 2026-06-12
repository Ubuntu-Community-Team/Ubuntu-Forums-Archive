---
title: "Can't figure out how to run .Xsession in Ubuntu 10.04"
date: 2010-06-09
forum: Desktop Environments
---

### Post by Phiwum on 2010-06-09
Hello.

I recently upgraded to 10.04, but I'll be darned if I can get GDM to run my personal .Xsession (or .xsession or .xinitrc or .Xclients...) when I log in.  I don't see any option on the session menu.  The only entries are window managers and "xterm".

My script works when I log in from the console.

Please don't tell me that Ubuntu (or GDM) has made things simpler by taking away the option of a .Xsession!  Nah, couldn't be.  That would be too nutsy.

Any help would be greatly appreciated.  (And surprising, since my previous two threads have no replies.  I must be asking the wrong questions or something.)

Thanks.

---

### Post by Brandon Williams on 2010-06-09
It seems like that option should still be there. I can't find it either.

Try adding a file called /usr/share/xsessions/default.desktop, with the following context:
```
[Desktop Entry]
Encoding=UTF-8
Name=Run .xsession script
Comment=This session runs the .xsession script
Exec=default
Type=Application
```

This is essentially the .desktop file that defines this session on previous releases.

---

### Post by Phiwum on 2010-06-09
> **Brandon Williams said:**
> It seems like that option should still be there. I can't find it either.

Try adding a file called /usr/share/xsessions/default.desktop, with the following context:
```
[Desktop Entry]
Encoding=UTF-8
Name=Run .xsession script
Comment=This session runs the .xsession script
Exec=default
Type=Application
```

This is essentially the .desktop file that defines this session on previous releases.

I'm sorry to say that this didn't seem to work.  I don't see any relevant output in .xsession-errors, so I can't figure out why it doesn't work.  ("Exec=default" looks a little different than other sample xsessions, but I can't say it's wrong, of course.)

Why on earth would they remove this functionality in the first place?  Xsession is *useful* and surely doesn't confuse novices, who never encounter it unless they're looking for it.

Also, I think that my .Xdefaults file is also being ignored.  I wonder if this is another change.  ("xrdb .Xdefaults" works, but I think I shouldn't have to do that.)

Thanks much.

---

### Post by Phiwum on 2010-06-10
> **Phiwum said:**
> I'm sorry to say that this didn't seem to work.  I don't see any relevant output in .xsession-errors, so I can't figure out why it doesn't work.  ("Exec=default" looks a little different than other sample xsessions, but I can't say it's wrong, of course.)


I changed that Exec line to "Exec=/etc/X11/Xsession" and it worked.  Thanks for the tip!

> **Phiwum said:**
> 
Why on earth would they remove this functionality in the first place?  Xsession is *useful* and surely doesn't confuse novices, who never encounter it unless they're looking for it.


I'd still like to know the answer to this.  I wish that Ubuntu wouldn't remove (well, hide) functionality that has been present for, what, 15 years?  More?

Thanks again, Brandon!

---

### Post by Brandon Williams on 2010-06-10
I just assumed that it would still work to use default, since the code block for recognizing "default" as a special value is still in /etc/gdm/Xsession. However, I see now that it's been mucked up quite a bit and the special Exec values "default" and "custom" will no longer work.

I would avoid running /etc/X11/Xsession, even though it appears to be working for you, because that will result in everything under /etc/X11/Xsession.d/ being applied twice.

Instead, I would add a file called /etc/X11/Xsession/01x11-common_setup-vars with the following content:
```
OPTIONFILE=${OPTIONFILE:-/etc/X11/Xsession.options}
SYSRESOURCES=${SYSRESOURCES:-/etc/X11/Xresources}
USRRESOURCES=${USRRESOURCES:-$HOME/.Xresources}
SYSSESSIONDIR=${SYSSESSIONDIR:-/etc/X11/Xsession.d}
USERXSESSION=${USERXSESSION:-$HOME/.xsession}
USERXSESSIONRC=${USERXSESSIONRC:-$HOME/.xsessionrc}
ALTUSERXSESSION=${ALTUSERXSESSION:-$HOME/.Xsession}
ERRFILE=${ERRFILE:-$HOME/.xsession-errors}
```

This will ensure that the variables expected by some of the scripts in /etc/X11/Xsession.d/ are present, which should cause 50x11-common_determine-startup to do the right thing with Exec=default.

Also, if you rename .Xdefaults to .Xresources, the above file should also be enough to get your settings activated without having to run xrdb by hand.

---

### Post by Phiwum on 2010-06-11
> **Brandon Williams said:**
> 
I would avoid running /etc/X11/Xsession, even though it appears to be working for you, because that will result in everything under /etc/X11/Xsession.d/ being applied twice.

Instead, I would add a file called /etc/X11/Xsession/01x11-common_setup-vars with the following content:
```
OPTIONFILE=${OPTIONFILE:-/etc/X11/Xsession.options}
SYSRESOURCES=${SYSRESOURCES:-/etc/X11/Xresources}
USRRESOURCES=${USRRESOURCES:-$HOME/.Xresources}
SYSSESSIONDIR=${SYSSESSIONDIR:-/etc/X11/Xsession.d}
USERXSESSION=${USERXSESSION:-$HOME/.xsession}
USERXSESSIONRC=${USERXSESSIONRC:-$HOME/.xsessionrc}
ALTUSERXSESSION=${ALTUSERXSESSION:-$HOME/.Xsession}
ERRFILE=${ERRFILE:-$HOME/.xsession-errors}
```

That did it!  Although you had a minor typo in the directory name.  The above file should be placed in /etc/X11/Xsession.d, of course.

> 
Also, if you rename .Xdefaults to .Xresources, the above file should also be enough to get your settings activated without having to run xrdb by hand.

That worked too.

Thanks much for your help.  I suppose I should have traced through some of those scripts myself.

---

