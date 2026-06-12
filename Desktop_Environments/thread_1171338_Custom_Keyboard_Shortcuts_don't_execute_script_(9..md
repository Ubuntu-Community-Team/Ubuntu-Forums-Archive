---
title: "Custom Keyboard Shortcuts don't execute script (9.04 Jaunty)"
date: 2009-05-27
forum: Desktop Environments
---

### Post by romuald on 2009-05-27
I've just installed ubuntu jaunty and wanted to make some customizations. but when mapping a custom shortcut to a script, let's say
> 
echo "vlc" > ~/test.sh
chmod 755 ~/test.sh

then i get following error 
> 
Error while trying to run (~/test.sh)
which is linked to the key (<Shift><Control>a)


any clue why?

---

### Post by plewisfdx on 2009-05-27
Add ```
#!/bin/bash
``` to the beginning of the file and change ```
vlc
``` to ```
vlc &
```

Adding the first line tells linux to use the bash shell, and id's it as a shell script.  The & after vlc tells it to run in the background.  Not sure if that's required, but it can't hurt.

---

### Post by romuald on 2009-05-27
> **plewisfdx said:**
> Add ```
#!/bin/bash
``` to the beginning of the file and change ```
vlc
``` to ```
vlc &
```

Adding the first line tells linux to use the bash shell, and id's it as a shell script.  The & after vlc tells it to run in the background.  Not sure if that's required, but it can't hurt.

just tried, didn't change anything.
.~/test in a shell works, but it just won't work through a custom shortcut

---

### Post by romuald on 2009-05-28
bump

---

### Post by glancep on 2009-07-11
Did you get anywhere with this?  I am having trouble setting up shortcuts for shell scripts as well.  I am not seeing the error you are, but nothing happens when I press the key after assigning it!  Frustrating...

---

### Post by okplayer on 2009-08-13
edit: I'm sorry, I'm using openbox, so if you also use it, this should help.
 
Hi,
just registered to help you solving this problem, as I had to work on it for hours to get it working, and it was really annoying and nowhere on the web is a solution.
So, the keyboard shortcut itself is working but if you press the keys nothing happens.
 
You should set the keybindings like this:
 
```
 
<keybind key="W-space">
<action name="Execute">
<startupnotify>
<enabled>yes</enabled>
<name>Terminal</name>
<icon>konsole</icon>
</startupnotify>
<command>gnome-terminal</command>
</action>
<action name="Execute">
<prompt>Are you sure you want to run a calculator!?</prompt>
<startupnotify>
<enabled>yes</enabled>
<name>Calculator</name>
<wmclass>xcalc</wmclass>
</startupnotify>
<command>xcalc</command>
</action>
</keybind>

``` 
I don't know wheter this exact code is working or not, but i found out, that if you use the "startupnotify" and "name" lines, it works. The "prompt" line you wont have to use. I'm sorry not being able to post you exactly the keybinding thats working on my PC, but I can't since I'm at work right now, so the code above is just an example to show you how to make it work.
 
once again: dont just execute the script, but make a startupnotify line, and it will work.
 
If you still cant get it running, send me a message in case I dont follow this thread and I'll post the code that worked.

---

### Post by sdaau on 2009-11-17
Had the same problem in karmic - it seems that the tilde '~' is the problem; if you instead change to '/home/[username]/scriptname' it should start OK (at least did for me)...  Btw, I was wandering where this information from gnome-keybinding-properties is being stored, and I managed to find a file @ ```
 ~/.gconf/desktop/gnome/keybindings/custom0/%gconf.xml 
```  Containing my original added entry (with ~). However, after I replaced the tilde with full path, things started working - yet, this %gconf.xml still keeps the tilde ??!! :confused:  Cheers...

---

