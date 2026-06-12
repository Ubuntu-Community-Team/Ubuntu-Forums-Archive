---
title: "Fluxbox Keybinds: Execute Maximized Command?"
date: 2007-07-05
forum: Desktop Environments
---

### Post by mbsullivan on 2007-07-05
Hi All,

Like many of you, I'm running a customized version of Fluxbox under Ubuntu. One thing that I've been wondering for a while (though I've been too lazy to delve into the matter deeply) is the following: is there any (easy) way to configure a hotkey to run an application maximized? The following (placed in the ~/.fluxbox/keys file):

Mod1 x :MacroCmd {ExecCommand x-terminal-emulator &} {MaximizeWindow} 

Does not seem to work reliably, which may be due to the fact that the commands are executed in parallel. Is there any way to bind a key to doing multiple commands serially?

One last possibility is that this may be possible using some wmctrl and/or Devil's Pie voodoo. Does anybody have any experience with either of these programs (which allow access and fine control of windows based on window IDs or names)?

Thanks!
Mike

---

### Post by RedSquirrel on 2007-07-07
I couldn't get that to work very well either.

Another way is to use make Fluxbox remember the size (and position) of the window. (You probably already tried this.)

Maximize the application window and then:

right-click on titlebar -> Remember -> Dimensions

right-click on titlebar -> Remember -> Position

and then just make the shortcut key open the application. It is not a particularly elegant solution because it will do that every time you run that application which may not be what you had in mind.

---

### Post by mbsullivan on 2007-07-11
> right-click on titlebar -> Remember -> Dimensions

right-click on titlebar -> Remember -> Position

Hi RedSquirrel,

Thanks for the reply. Yeah, that's the closest (working) thing that I've tried, but it's not quite what I'm looking for. I'll let you know if I figure out anything better (please do the same).

In the meantime, does anybody have any stories about wmctrl and/or Devil's Pie? What have you done with them (if anything)? One thing (that I haven't tried) would be to create a system whereby your startup script could place all of your autostarted programs on the workspace / position / state that you would normally leave them in.
 
Mike

---

