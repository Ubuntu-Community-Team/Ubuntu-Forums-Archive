---
title: "Kubuntu start compiz &amp; emerald automatically without replacing kwin"
date: 2007-07-27
forum: Desktop Effects &amp; Customization
---

### Post by menox on 2007-07-27
I don't know about everyone else but all I've found about compiz and emerald in KDE has required the KDE session to start with kwin as the window manager.  Most of these instructions say to put some script in the ~/.kde/Autostart folder.  I don't like this because kwin will start up just to be killed a few seconds later.  I would like emerald to be my WM by default.

Keep in mind this requires compiz and emerald to be installed from the ubuntu repositories.

After digging through /usr/bin/startkde I've found this is very easy.

Instructions:

1. Create a script in whatever editor you like and call it "startcompiz" (make sure you sudo it)

Add these lines to the file:

#!/bin/bash
compiz --replace &
sleep 3
emerald --replace || kwin --replace

//End of file

Save this file in /usr/bin or /usr/local/bin.  Wherever it will be accessible in your PATH.

Add this line to your ~/.profile

export KDEWM=startcompiz

And you're done!

Log out of KDE and log back in.  Compiz and Emerald should start instead of kwin.

If for any reason you have problems with compiz or emerald just remove the line in your ~/.profile

---

### Post by menox on 2007-07-27
Forgot to mention:

startcompiz will need to be chmod +x

kwin will be the fallback WM if emerald dies.

---

### Post by maestrobwh1 on 2007-08-08
You note this:

Add this line to your ~/.profile
export KDEWM=startcompiz

I have no .profile in my home directory.  Do you mean .bash_profile?  I know with beryl, I had to put something in  .bashrc

---

### Post by menox on 2007-08-08
if .profile doesn't exist in your home directory you can create it.


Here's my .profile

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
export KDEWM=startcompiz


It looks like you could put the "export KDEWM=startcompiz" in your .bashrc also.  It should have the same effect.

---

### Post by maestrobwh1 on 2007-08-08
Not in .bashrc.  I tried that and when the desktop loaded, my tray icons didn't show up and I had no decorator.

Do I have to have beryl launch as well then.  I had a beryl desktop shortcut in my .kde/Autostart directory for a while but half the time it fell back to kwin that way and there was no point in having it there.

I'll try creating a .profile like you and see what happens.  I'll post back either way.

Peace!

---

### Post by menox on 2007-08-08
Can you run startcompiz from within KDE?

If you remove the export line out of .bashrc or .profile does startcompiz start compiz and emerald?

---

### Post by maestrobwh1 on 2007-08-08
Okay, 

I just created a .profile and then logged out and in, and everything looks groovy... (I moved my launcher (I made using some forum) for beryl to /.kde/Autostart)  **EXCEPT** everything that would normally be in my tray is now minimized in my lower panel... except for the beryl icon.  (Kmix, kwifimanager, kneststats).

Have to meet with people for lunch.  I'll play around more in the afternoon.  I am wondering if I place the startcompiz in my /.kde/Autostart rather than in /usr/local/bin and then removed the beryl launch item.  

Also, maybe I can change my beryl launch item. The beryl launcher looks like:

[Desktop Entry]
Comment=
Comment[en_US]=
Encoding=UTF-8
Exec=beryl-manager
GenericName=
GenericName[en_US]=
Icon=beryl-manager
MimeType=
Name=Beryl-Manager
Path=
StartupNotify=false
Terminal=false
TerminalOptions=
Type=Application
X-DCOP-ServiceType=
X-KDE-SubstituteUID=false
X-KDE-Username=
 
I also wonder if I can change 
EXEC=beryl-manager 
to
EXEC=compiz

---

### Post by menox on 2007-08-08
If you put startcompiz in ~/.kde/Autostart kwin will still start and emerald will replace it after KDE starts.

I wanted to start compiz & emerald as the default to save from starting kwin and killing it right after.  This is what the export line does in your .profile.

I have the same problem with the tray icons.  I usually have to exit all the applications and restart them.  Then they show up in the tray.  I think this might be a problem with kicker not playing nice with emerald.  Since I usually suspend my pc this hasn't really bothered me much.

If you're using compiz, you should stop using beryl.  I think they merged into compiz fusion which is what you're getting from the ubuntu repos.

---

### Post by maestrobwh1 on 2007-08-08
I had my .profile in my home, just like yours.

I have my startcompiz in /usr/bin and /usr/local/bin (I've been trying all sorts of things)

I get compiz, but with no window decorator. I opened konsole, and typed startcompiz... my desktop flickered and poof, everything was right (until I close konsole).  

For now, I created a desktop item like the one I had for beryl and just have it on my desktop.  I replaced
EXEC=beryl-manager
with
EXEC=startcompiz
renamed the desktop item to compiz
If I click it, everything re-launches nicely.  

so... For now, I put .profile in another folder until I can sort this out.

If it falls back as it is seeming to do on load with the .profile in my home directory, compiz IS running but with no decorator.  Odd... so Emerald is not loading properly from this kind of launch for me.

Currently, I have my own solution at the bottom because, I might want to be able to switch back here and there, as I know some of my wine programs are unstable/unusable with compiz as they were with beryl (they just "close" when certain menu items are activated... usually graphics programs like Paint Shop Pro and XnView).

So I created another desktop item with
EXEC=kwin --replace

Just for appearance, I changed the icons to something cool.

I know I could do all of this stuff from konsole, but with all the work I do, fewer keystrokes is a plus.

This way, my tray icons end up where they are supposed to as well.  Your help was very useful though, as now I don't need beryl running to switch things around.

If you have any ideas as to why emerald is not loading, I can try the more convenient method you use.

I attached my startcompiz (with a text extension so I could upload it).

My .profile looks exactly like yours, as I did a copy and paste from your post.

---

### Post by menox on 2007-08-08
Yes, you can reload kwin (the default KDE window manager/decorator) with `kwin --replace` if you need to kill compiz and emerald.

I've had the same problem with emerald not loading also.  But it doesn't do it all the time.  I'll look at this and see if I can find the problem.

If anyone else has any input it would be nice.

I'll post back when I find a solution.

---

### Post by menox on 2007-08-08
Ok, I think I might have found the problem.

Change your startcompiz file to look like this:

#!/bin/bash
compiz &
sleep 5
emerald --replace || kwin --replace


Basically just take out the --replace from the second line.
I also changed the sleep to 5 instead of 3.

I've logged out and in about 8 times and its worked every time.
I still have problems with the tray icons though...

Let me know what happens.

---

### Post by maestrobwh1 on 2007-08-08
I appreciate it but there is no hurry, as my solution works.  I even put the launcher I created into ./kde/Autostart and it has worked several times in a row.

Compiz has even become more stable with wine, as I tried a few apps and they didn't crash.  Cool beans.  I am 38 years old... can I say "cool beans?"

---

### Post by menox on 2007-08-08
> **maestrobwh1 said:**
>  I am 38 years old... can I say "cool beans?"

I think thats allowed.  I'm getting borderline to asking those questions too.  26.

Anyway, if you get a chance, try that and see if it works.  Its been working for me..

---

### Post by maestrobwh1 on 2007-08-09
I did try the new startcompiz file, but nothing at all happened. Still, my solution works with a desktop item in /.kde/Autostart. to the original startcompiz file in my /usr/bin.

Works great and hasn't crashed yet!.... yet?

---

