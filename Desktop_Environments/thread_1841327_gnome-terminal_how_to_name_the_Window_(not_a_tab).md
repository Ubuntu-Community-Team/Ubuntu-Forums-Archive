---
title: "gnome-terminal: how to name the Window (not a tab)"
date: 2011-09-09
forum: Desktop Environments
---

### Post by doubi on 2011-09-09
Hi all,

I've seen questions *similar* to this posted in many places, but not answering this exact query.

I know how to set the Title of an individual tab in gnome-terminal, so that when that tab is selected the Window takes on that title (generally right-click on the tab and use "Set Title..."; xterm -t foo, as is suggested in some places, doesn't seem to work).

It would be nice not to have to name each of my tabs separately though.

Is there a way to set the name of a gnome-terminal Window, irrespective of the names of the terminal tabs?

I looked my CompizConfig Settings Manager as well, but couldn't see anything relevant.

Cheers!

---

### Post by Krytarik on 2011-09-09
"Edit -> Profile Preferences -> Title and Command":

[LIST]
[*]Set "Initial title" how you want it.
[*]Change "When terminal commands set their own titles" to "Keep initial title".
[/LIST]
Notice that the names of the individual tabs will be the same then, but it seems that you are fine with that.

Greetings.

---

### Post by doubi on 2011-09-18
This doesn't get me precisely what I'm looking for, as it's reliant on using profiles - in order to give one name to window A with one set of tabs, and another name to window B with another set of tabs, I have to use a different profile for each window.

I was hoping to avoid mucking about with profiles - admittedly not *that* much of a hassle, but a simple "name this window 'foo'" command would have been preferable.

Still, the problem is solved acceptably for the time being, until I stop whining and add the feature I want to gnome-terminal myself :)

Thanks for the pointer.

---

### Post by haqking on 2011-09-18
> **doubi said:**
> This doesn't get me precisely what I'm looking for, as it's reliant on using profiles - in order to give one name to window A with one set of tabs, and another name to window B with another set of tabs, I have to use a different profile for each window.

I was hoping to avoid mucking about with profiles - admittedly not *that* much of a hassle, but a simple "name this window 'foo'" command would have been preferable.

Still, the problem is solved acceptably for the time being, until I stop whining and add the feature I want to gnome-terminal myself :)

Thanks for the pointer.


[s]terminal>set title[/s]

Edit: i see you already said you had done that ;-)

---

### Post by Krytarik on 2011-09-18
There is a command line option for setting the title of the invoked terminal window, but unfortunately this only affects the first created tab, any further tab opened through the menu would have the title specified in the profile settings.

Anyway, this is how the command would look like (if you don't use spaces, no quotation marks are needed):
```
gnome-terminal --title="Set what you want."
```For this to work, you still need to change the profile setting "When terminal commands set their own titles" to "Keep initial title", as described previously.

---

