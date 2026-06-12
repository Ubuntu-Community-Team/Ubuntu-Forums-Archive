---
title: "Launching a specific application via terminal to a certain desktop number."
date: 2008-12-22
forum: General Help
---

### Post by ww711 on 2008-12-22
Is anyone familiar on how to launch an application via terminal to a specific virtual desktop number?

alt f2 launches the run application window.

Typing the name of a particular application e.g. firefox, skype, pidgin, thunderbird, etc will launch that application. This only launches in the virtual desktop that the user is using.

Also I know that you can launch several programs at once with the & command e.g. Skype & Pidgin - launches both programs at once.

So what I'm trying to achieve, as an example,

To launch Firefox into desktop 1, launch Pidgin and Skype into desktop 2 and Opera into desktop 3, gnome-terminal into desktop 4. Only via the run application window.

Or another example, to be browsing Firefox in desktop 1 and then want to launch vlc into desktop 2, while still being in desktop 1 and once loaded I can navigate to desktop 2 using Ctrl+Alt+ Arrow left/right.

Is there a way to do this all through the 'run application' window?

---

### Post by sedawk on 2008-12-22
My first idea was to use the DESKTOP environment variable but
that doesn't seem to work (can't find a proper syntax description and
trial and error didn't work so far).

Another way would be to use command line tool "wmctrl". It
can be used to move windows to different virtual desktops if
the window manager supports the required interface.
To move windows with identity ID to Desktop No. 2 use
wmctrl -r ID -t 2 (or wmctrl -i -r ID -t 2).

I think it takes some time to get used to wmctrl, e.g. to
identify applications by "windows name" and to get the
values needed as input parameters for the useful commands ...

---

### Post by drs305 on 2008-12-22
Do you have the capability to set the parameters in compiz or does the setup have to be done on the command line as well? It is not difficult to set specific window titles (or other specs) to open in a specific workspace, but I only know how to set it up via the ccsm gui. Once it is set up any terminal launch will work the same.

---

### Post by ww711 on 2008-12-23
> **drs305 said:**
> Do you have the capability to set the parameters in compiz or does the setup have to be done on the command line as well? It is not difficult to set specific window titles (or other specs) to open in a specific workspace, but I only know how to set it up via the ccsm gui. Once it is set up any terminal launch will work the same.


I already have ccsm gui installed. I would be interested in knowing how your set up works and experiment with that. I guess I'll have to look up more about the run application and its commands too

---

### Post by Zorael on 2008-12-23
edit: Ah, blah, virtual desktop and not display. Ignore me.
> To give an answer to the topic, the variable is DISPLAY.
```
$ DISPLAY=:0 gedit &
```

---

### Post by ww711 on 2008-12-23
I've attempted

```
firefox -display=:0.4
```

this launches firefox but not into my 4th virtual desktop...

---

### Post by drs305 on 2008-12-23
> **ww711 said:**
> I already have ccsm gui installed. I would be interested in knowing how your set up works and experiment with that. I guess I'll have to look up more about the run application and its commands too
System, Preferences, CompizConfig Settings Manager (or in terminal: ccsm ). Windows management:
Place Windows > Fixed Window Placement > "Windows with fixed viewport"
New. Click on + Button.
Select the Type (Window Class, Title, Type, etc)
Value: You can either enter it or use "Grab" and just click on an open window of the type you are trying to set up. 
Select X and Y viewport positions. 
Add.

Whenever you open a window with the specified Title/Class/etc it will open in the assigned viewport/workspace. 

You can tweak the window position on the workspace with the 'Windows with fixed positions' on the same setup page.

---

### Post by ww711 on 2008-12-23
> **drs305 said:**
> System, Preferences, CompizConfig Settings Manager (or in terminal: ccsm ). Windows management:
Place Windows > Fixed Window Placement > "Windows with fixed viewport"
New. Click on + Button.
Select the Type (Window Class, Title, Type, etc)
Value: You can either enter it or use "Grab" and just click on an open window of the type you are trying to set up. 
Select X and Y viewport positions. 
Add.

Whenever you open a window with the specified Title/Class/etc it will open in the assigned viewport/workspace. 

You can tweak the window position on the workspace with the 'Windows with fixed positions' on the same setup page.

I'll try out your method.

---

