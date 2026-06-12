---
title: "Openbox: close application via menu"
date: 2012-01-06
forum: Desktop Environments
---

### Post by mardybear on 2012-01-06
Greetings.

I realize Openbox isn't a true desktop environment but i didn't see a window manager category and thought this might be the most relevant forum. I recently started using Openbox and enjoy it's simplicity. I'm able to utilize all my favourite applications via alt-tab (don't want a panel), terminal or by modifying the openbox config files.

Sorry if this has already been solved but i couldn't find the answer via openbox's documentation or any online forums.

Is it possible to close open applications directly from the centre mouse-click menu without having to select the application/change focus and then click to close the application via the window manager's 'X'/close button?

I regularly use 'exit' in terminal, alt-F4 for most applications or right-click & 'c' in the application window but there are times when i simply want close an application without the extra clicks/keystrokes - something like centre mouse-click to get the open applications menu, scroll up the the application i wish to close then simply press 'delete' or 'backspace' or right mouse-click or something similar.

Thanks for your help.

mardybear

---

### Post by m_duck on 2012-01-07
That sounds doable. I usually have a bind to ctrl+q to close things (useful for those programs which ignore this bind anyway).

In ~/.config/openbox/rc.xml, find the section that begins:```
<context name="Titlebar">
    ...
```You will see a number of mouse binds there. I suspect that adding the following mouse bind into that section should achieve what you want.

```
<mousebind button="Middle" action="Click">
    <action name="Close"/>
</mousebind>
```I should note that I am unable to test this at the moment but I see no reason why it would not work.

---

### Post by mardybear on 2012-01-08
```
<mousebind button="Middle" action="Click">
    <action name="Close"/>
</mousebind>
```I should note that I am unable to test this at the moment but I see no reason why it would not work.[/QUOTE]

m_duck - thanks for the reply.

Your code made it easier to close an open window by simply center mouse-clicking on the title bar.

It still, however, does not allow me to do what i wanted, which is to perform this simple center mouse-click type action directly from Openbox's open applications menu to close open applications/windows.

I think it would be great if this was a default action of Openbox. Any other suggestions are appreciated?

mardybear

---

### Post by m_duck on 2012-01-08
Oh, I see what you mean. If it is possible, there might be a different context to which the same mousebind as above could be added.

I will have a look a bit later and see if such a thing can be done.

EDIT: I'm stumped - this is a tricky one. As far as I can see, there is no (immediately obvious) functionality in Openbox to allow defined middle clicking in menus at all, and oddly enough I have not seen the question asked before. Now that you have mentioned it, I can see myself using also, if there is in fact a way of achieving it.

Sorry I can't be more help at the moment!

---

### Post by mardybear on 2012-01-08
> **m_duck said:**
> 
EDIT: I'm stumped - this is a tricky one. As far as I can see, there is no (immediately obvious) functionality in Openbox to allow defined middle clicking in menus at all, and oddly enough I have not seen the question asked before. Now that you have mentioned it, I can see myself using also, if there is in fact a way of achieving it.

Thanks for thinking over the issue m_duck.

Anyone else have any ideas?

mardybear

---

### Post by mardybear on 2012-01-13
-- bump --

Got a puzzle for all Openbox users...

Openbox is supposed to be so configurable and flexible, i didn't think this would be such a stumper.

Anyone got any ideas?

mardybear

---

