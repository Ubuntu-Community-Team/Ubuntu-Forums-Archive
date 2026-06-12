---
title: "Niggling Unity issues, and a few questions on design."
date: 2011-07-15
forum: Desktop Environments
---

### Post by pjd99 on 2011-07-15
First off, my aim here is not to rant about Unity being not ready for use. I've done that already in other posts, but have calmed down enough since upgrading to Natty to give it a fair go. To be clear, I'm using Classic in my native install as Unity just doesn't suit my requirements yet.

But, I decided to give Oneiric a run in a VM to try and get used to Unity (only gave it about 2 hours in Natty before wanting to defenestrate my laptop) and to do my bit for testing. The following are a few comments/questions about my experience so far, and was wondering if there are solid design reasons for the way certain things behave or if it's more a lack of polish for the sake of functionality (this post is not about stability, just UI elements and design).

Screen:
1920x1200, 17" monitor (16:10). I have a feeling that this is where a lot of my issues stem from as it's not a common setup on a laptop (size or res).
Usage:
General: web, mail, document composition, audio/video. Basically, the stuff everyone does.
Engineering: CAD, PLC & HMI programming. Usually in a WinXP VM.
Uni: Octave/Matlab/Xilinx use. Microcontroller programming (mostly avr-gcc stuff).
Typesetting with Latex/XeLatex/Context.
So, I can have a lot of windows open at a time, and like to seamlessly switch between workspaces, as one might have mail and web, the next might have a few latex related windows, and lastly a VM or 2 open for CAD and programming. And lots of terminal windows (often 2+ at a time, never really liked tabs for terminal)


Things that have frustrated me the most, as the design/implementation feels counter to seamless work flow:
1. No option to enable/disable global menus.
Why is there no system/dconf setting to disable the global menu? Global menus aren't ideal for every screen configuration. Most frustrating when I have multiple programs open in a tiled setting. e.g. 4 windows open, each taking 1/4 of the screen. For the program in the bottom right, the cursor has to move a longer distance than the vertical height of the program window just to access its menu.
The min/max/close buttons have changed since using Unity in Natty, for the better. In Natty I couldn't close a program unless it was in focus, now I can. Only problem I see now is that when the program is maximised, there are two sets of min/max/close. One set to the right of the BFB, and one set below it. A spit & polish issue methinks.
Some of the remedies out on the web are using an ugly hack to disable the global menu without uninstalling it, but this will still fail if multiple users want a different setting for it. I don't want to remove it completely (as I want to keep my testing environment close to what is being released by the devs), but would like to disable it as I find it a hindrance.

2. Design question: Why were the overlay scrollbars implemented? I understand that increasing vertical space is a good idea, but what was the idea of making the scrollbars so small? It's not like the extra horizontal space is useful. esp with the inconsistent behavior. Which brings me to my next point...

3. Inconsistencies in the overlay scrollbar's behavior.
In a windowed application, it appears to the right, outside the window. Why is this? Because when an application is maximised, it has to appear inside the window... Also, it appears too early, as it can't be targeted when it first shows up (pointer is more than the width of the overlay away). If it is approached from the right (i.e. pointer moving left), it is almost impossible to target it without moving the pointer to the right again. This screams either poor design or poor implementation.
The proportional sizing leaves a lot to be desired. When you need to target it the most, like in a long PDF, it is at its hardest to target. The opposite is also true, if there's little to scroll, the mouse has to move an incredibly long way to make it scroll at all.
Also, I don't know if its due to the slight colour impairment I have, the size and resolution of my screen or if it's just a general issue, but I find it incredibly had to see, even compared to grey-on-grey old style scroll bars.

Because of the issues I have with the scrollbars, I have disabled them on my native (Natty) install.

4. Lack of categorically sorted applications (at least ootb). This is what Ubuntu did well for years with Gnome, changing the ugly, default Debian menus into something that was a joy to work with, and was what made Ubuntu >> Windows IMO (I hate the start menu in Windows with a passion, it's just awful). 2 clicks (max) to get to any program (even if I had to occasionally edit a .desktop file to get it there.) I feel this is more lack of polish, and i'll be customising mine soon.

5. Launcher application switching (Not alt-tab, that works great).
When 2 instances of a program are running, I wouldn't mind how the switcher works, except that it's so damn slow. Unity could actually learn a thing or two from *shudder* Windows 7 here, switching to another open window of an application is very nice, with the thumbnails that pop up upon mouse over. I think something like that would be better than the current implementation, even though personally I'd like separate icons until the launcher (or taskbar in Win 7) fills up.

6. Workspace switching.
Went from a single mouse click in Gnome to three in Unity (+ delay for launcher to un-hide). Why? Just... Why? Could do something like the application switcher in Win 7 as well. It'd be slower than Gnome, but much faster than the current implementation. And why do I need to click a workspace twice to make it have focus? I'd even settle for using the right mouse button if there's a valid reason as to why so many clicks are required.
Something that would be nice, that I don't recall existing in Gnome would be an Alt-Tab equivalent for workspaces. I don't simply mean switching like you can do already with ctrl+alt+L/R, but it cycles the workspaces and brings one into focus when held on for a prescribed time.

So, after that wall of text, I still want to use Unity with Oneiric in my VM, try to set it up with the programs I need at work and uni, and run it most of the time (only falling back to host when necessary). Is there anything that you think is a must-do to make the Unity experience better?

---

