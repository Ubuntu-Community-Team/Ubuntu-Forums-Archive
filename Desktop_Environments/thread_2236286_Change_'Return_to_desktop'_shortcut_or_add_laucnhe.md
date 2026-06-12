---
title: "Change 'Return to desktop' shortcut or add laucnher icon ?"
date: 2014-07-25
forum: Desktop Environments
---

### Post by LaNouille974 on 2014-07-25
Hi everybody,

I just installed Ubuntu 14.04 and looking for a way to quickly return to desktop. 

Of course, I can use Alt+Tab or Ctrl+Super+D (not very practical on a gamer keyboard, my Super key is on the right...).

I figured out that MyUnity is no longer compatible with 14.04 and Ubuntu Tweak doesn't work either for enabling "return to desktop" mouse shortcuts...

Moreover, configuring "Hide all normal windows" shortcut in keyboard settings doesn't work as expected and didn't get me back to desktop... (It just hides terminal if open)

So, what I'm looking for is a way to **create a shortcut into Unity launcher** or** how to set another keyboard/mouse shortcut**.

Thanks for you help guys ! :)

BR,
Robin.

---

### Post by LaNouille974 on 2014-07-25
In fact, **I've just found how to add "Show desktop" icon into Unity launcher**...

Just right-click on the desktop and choose "Change desktop background" (the last option, don't know its label in english, sorry), then switch to 'Behaviour' tab and tick "Add 'Show desktop' icon to launcher". That's all ! ^^

But if anybody knows how to change Ctrl+Super+D keyboard shortcut... ;)


-------------------------------------------------------------------------------------------------------
*[Edit]* Pane on which you can activate launcher desktop shortcut, in French :

[IMG]http://img11.hostingpics.net/pics/528696capturedcran2.png[/IMG]

---

### Post by mc4man on 2014-07-25
> But if anybody knows how to change Ctrl+Super+D keyboard shortcut... 
It's all over the place...
So your best bet is to open compizconfig-settings-manager (ccsm)
Once there then set to Disabled in General Options > Key bindings > Show Desktop
Then go to Ubuntu Unity Plugin >  General & set binding as desired there.

If the binding you choose works but then gets unset down the road you'll possibly have to edit /usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override > show-desktop =  to reflect chosen binding

---

