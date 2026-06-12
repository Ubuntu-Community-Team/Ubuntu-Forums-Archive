---
title: "kde4+compiz breaks run dialogue (alt+f2)"
date: 2011-03-14
forum: Desktop Environments
---

### Post by bobdobbs on 2011-03-14
Hi all.

I'm using kde4, compiz and emerald.

After I start compiz, I don't have access to a "run" dialogue, that I would expect to see after hitting "alt+f2".

Googling, I can see that this has been a problem for years for many people. There seem to be a number of proposed solutions. However, the solution posts that I can find all seem to be outdated.

What is a current solution for enabling a run menu?

---

### Post by Copper Bezel on 2011-03-15
I don't know what KDE's run dialogue looks like or what features it comes with, but Gnome-Do is a popular replacement on Gnome, and I use XFCE's XFRun4. The latter is GTK, so nasty looking in K, but there are a variety of options out there. How does Cardapio look in KDE, I wonder?

I'd just do a search for "launcher" apps for KDE and pick something pretty.

(Synapse, maybe? It's fully skinned.)

---

### Post by bobdobbs on 2011-03-15
> **Copper Bezel said:**
> I don't know what KDE's run dialogue looks like or what features it comes with, but Gnome-Do is a popular replacement on Gnome, and I use XFCE's XFRun4. The latter is GTK, so nasty looking in K, but there are a variety of options out there. How does Cardapio look in KDE, I wonder?

I'd just do a search for "launcher" apps for KDE and pick something pretty.

(Synapse, maybe? It's fully skinned.)

Thanks, but not what I want.

I really just want a working run dialogue. Not another icon cluttering my desktop.

---

### Post by Copper Bezel on 2011-03-15
Oh, God no, what's the point of a launcher that itself launches from a launcher? Not what I meant at all. When I said I replaced my Alt+F2 Run dialogue, I meant it. = )

You're using Compiz now. That means you can set it (whatever application you choose) as a Compiz command keybinding for Alt+F2. Most of the apps I listed are meant to be used that way. (Cardapio and Do run in the background and appear on a keystroke, but it's functionally the same.)

If you have the fix for GTK app skinning, I'd really suggest XFRun4. It comes with xfce-utils . Very light, autocompletes, runs commands with options (unlike some,) etc. Just drops the thing you put in it into shell, then goes away. = )

[IMG]http://i146.photobucket.com/albums/r256/Kalimol/Screenshot-1.png[/IMG]

---

### Post by bobdobbs on 2011-03-15
Ah! I see what you mean.

That's pretty much exactly what I want. That pretty too.

Try as I might, I just can't figure out how to set keybindings in compiz.

In ccsm, I search for bindings. 
This leads me to "commands" -> "key bindings".
Here, I can set key combinations. But I can't figure out how to associate the combos with commands. :(

I can't believe how frustating this is.

---

### Post by Copper Bezel on 2011-03-15
Yeah, CCSM is a little weird as a UI. Basically, under Commands, you have a tab where you set commands (12 possible spaces), then subsequent tabs like "Keybindings" and "Edge Bindings" where you can assign a command to those actions. You'd want to put xfrun4 in Command Line 1, then hit the Keybindings tab and set Command Line 1 to Alt+F2.

---

### Post by bobdobbs on 2011-03-15
> **Copper Bezel said:**
> Yeah, CCSM is a little weird as a UI. Basically, under Commands, you have a tab where you set commands (12 possible spaces), then subsequent tabs like "Keybindings" and "Edge Bindings" where you can assign a command to those actions. You'd want to put xfrun4 in Command Line 1, then hit the Keybindings tab and set Command Line 1 to Alt+F2.

Hi Copper.

I gave that a go, but still no dice.

This is interesting. I know that I have xfrun4 installed - I can run it from the command line. (I like xfce4, and use it often).

---

### Post by Copper Bezel on 2011-03-16
Huh, weird. Here's an odd thought: is there something from KWin hanging around and conflicting with the keybinding? (I've seen something similar happen on Gnome with Metacity and Compiz.) Try setting it to a different shortcut.

---

### Post by bobdobbs on 2011-03-16
> **Copper Bezel said:**
> Huh, weird. Here's an odd thought: is there something from KWin hanging around and conflicting with the keybinding? (I've seen something similar happen on Gnome with Metacity and Compiz.) Try setting it to a different shortcut.

Ok... finally got it working by playing around with different keybindings in ccsm. I can now invoke xfrun by hitting F3.

Thanks for the help.

A further question... why does your xfrun look so pretty?
Mine looks like it was designed in 1993.

---

### Post by Copper Bezel on 2011-03-16
Cool.

On the other part, I guess you don't have GTK compatibility installed? Mine's running under Gnome, so it's rendered in normal Gnome/Metacity parts. Look up "oxygen-GTK" to get KDE to render GTK apps properly.

---

### Post by bobdobbs on 2011-03-16
> **Copper Bezel said:**
> Cool.

On the other part, I guess you don't have GTK compatibility installed? Mine's running under Gnome, so it's rendered in normal Gnome/Metacity parts. Look up "oxygen-GTK" to get KDE to render GTK apps properly.

Creating an oxygen-gtk deb as we speak.

I'm a bit weary of this really. I don't like having to interfere with the usual smooth running of my package management. But there don't seem to be any oxygen-gtk packages in any repos.

Thanks.

---

### Post by Copper Bezel on 2011-03-16
That is wearying - I think this is what you're looking for, though, and I'm sorry if it's too late to be of any use.

[http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216](http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216)

Via this thread:

[http://ubuntuforums.org/showthread.php?t=1693287&highlight=gtk+kde](http://ubuntuforums.org/showthread.php?t=1693287&highlight=gtk+kde)

The thread also explains how to get those theme settings applied to your GTK apps.

---

### Post by bobdobbs on 2011-03-16
Thanks for providing further pointers.

I cloned the files from the git repository and compiled the files to an rpm. I've installed the rpm via dpkg.

oh yeah... kde's 'run' dialogue mysteriously came back.
(I can hear you slapping your forehead over the internet)

I think that this has something to do with having restarted X.

---

### Post by bobdobbs on 2011-03-17
I take that back...

All of a sudden the alt+f2 function has no longer invokes the run dialogue. Things are back to before.

Drat.

---

### Post by Copper Bezel on 2011-03-17
I thought you set it to F3?

---

### Post by bobdobbs on 2011-03-17
> **Copper Bezel said:**
> I thought you set it to F3?

I set F3 to trigger xfrun4. I still have that setting.

---

