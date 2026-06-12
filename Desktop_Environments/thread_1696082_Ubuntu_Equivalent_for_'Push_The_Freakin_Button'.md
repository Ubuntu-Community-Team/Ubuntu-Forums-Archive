---
title: "Ubuntu Equivalent for 'Push The Freakin Button'"
date: 2011-02-26
forum: Desktop Environments
---

### Post by wdavro on 2011-02-26
I'm looking for a program for my 64bit Lucid that will 'watch the screen' and when it sees a predefined window title or a window with specific content it will execute a series of predefined keystrokes and mouse clicks automatically.  I don't want to have to click or type anything to start the execution of this 'macro'.

An excellent Windows equivalent is called PTFB or Push The Freakin Button.

Anyone know of a Ubuntu equivalent?  Or does Ubuntu have something built-in that would accomplish this?

Thx

---

### Post by ankspo71 on 2011-02-26
Hi,
I found one so far by searching through synaptic package manager. It is called 'kautoclick'. I think it is used for automating mouse clicks only though.

---

### Post by Copper Bezel on 2011-02-27
KAutoClick really is just for mouse clicks (not mouse actions, just the click) and they're set on a timer event. It sounds like wdavro is in a situation of - is this about right? - running a long process overnight that will stop at certain times and spawn a dialog box that asks for permission to continue at certain steps.

Another KDE app called autokey-gtk *looks* to be a closer match than kautoclick for creating and executing a macro of keystrokes or mouse actions, but it still needs something to start it. 

If the reaction you want from this window event is as simple as a simple click or a keystroke, it would be just as simple to use xdotool, a command-line application used for sending keystrokes and such. If the action is more complex, it would make sense to create an autokey-gtk macro set to a particular keystroke, then create an xdotool command to *hit* that keystroke. So either way, the last bit we need is an app to watch for window titles and run an xdotool command.

I *think* that could be accomplished with a bash script using wmctrl, which can list presently running windows, including dialog boxes, but you'd have to build that from the ground up, and it's over my reading level, frankly.

Going back to ankspo71's suggestion, would it be enough to run the macro on a timer? You could use cron to trigger xdotool to trigger the autokey-gtk macro every minute. Is it a problem if it's sometimes clicking when the button isn't there?

---

### Post by Cheesehead on 2011-02-28
Normally, when listening for a signal, it's much easier to leave the GUI out of it when possible. For example, if you're listening for a system notification, it's easier for your listener to monitor dBus than to 'watch' the screen. For web content, a python or shell filter may be sufficient instead of 'watching' a browser window.

If you give us a little more detail on what exactly you're trying to monitor, what the trigger should be, and what you want to happen, we may be able to suggest more useful solutions.

---

### Post by wdavro on 2011-03-01
Copper Bezel is about right.  During the lengthy run, there may be a few browser windows or some dialog windows that might pop up.  Most just need to be closed, however a couple might need to stay up so I can see them later in the day.  So it needs to be able to read either the window title or something specific in the window content. It's an internal corporate program.  I don't know the language, much (but not all I suspect) is browser and java based.

---

