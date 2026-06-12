---
title: "Thunderbird window not getting focus"
date: 2007-06-13
forum: Desktop Environments
---

### Post by mattack on 2007-06-13
This is nitpicky behavior, probably on Metacity's part, but I want a fix.

I'm running Ubuntu 7.04 with Gnome.

When I have Thunderbird open and click a mailto: link in Firefox, a compose window opens *behind* the open Firefox window. That make no sense to me... When Thunderbird is closed, mailto: links open a focused compose window in front of Firefox, where I think they should be. 
I leave Thunderbird open all day, as I am constantly checking my email and want mailto: links to open a compose window in focus if Thunderbird is open. Is there an easy way to do this?

---

### Post by gfixler on 2007-06-15
No idea, but here are a few things to poke at, based on my settings, as everything works fine for me on the same setup.

in Firefox, in a new tab, or window, type in the address bar:

about:config

In the Filter line up top in the config settings, type mailto. Check that the results look like this:

network.protocol-handler.expose.mailto - false
network.protocol-handler.external.mailto - true
network.protocol-handler.warn-external.mailto - false

In Thunderbird, go to Edit->Preferences, and then the Advanced tab, and click the Config Editor button to bring up a similar window to the settings in Firefox. Type mailto in the Filter box, and check that it's this:

network.protocol-handler.expose.mailto - true

In a shell, type:

gconf-editor

In the Configuration Editor that pops up, hit Ctrl+F and search for mailto. You should see:

/desktop/gnome/url-handlers/mailto

Click it, and in the Name/Value are up top, you should have:

command - mozilla-thunderbird %s
enabled (checked)
needs_terminal (unchecked)

You could try checking the terminal one, which will pop open a shell when you click a mailto, then open a new mail window, then close the shell. That may make it pop to the front. Btw, careful in the conf-ed - everything you change changes instantly. Know what you're changing before you change it.


Failing all that, you could install Devil's Pie, and add a script to its ~/.devilspie folder that focuses new mail windows. It's a cool app that lets you do things to windows that match rules whenever they first appear. I have it moving my shells and apps to the correct monitors and desktops, and fullscreening, or maximizing them where I want. Pretty powerful, and very cool.

It's not as simple as you might like, but here's how to make it work for you (hopefully):

install it from [here]("http://burtonini.com/blog/computers/devilspie")

Go to System->Sessions->Preferences in your main Ubuntu panel, click New, and put in:

Name: Devil's Pie
Command: devilspie

That will make sure it starts up whenever you power up, or reboot.

In whatever editor you use, make a file with a .ds extension (e.g. mailtofix.ds), and save it in your homespace, under the .devilspie folder that the Devil's Pie install should have made for you.

That file should be a single line of code, and it should be something like this:

(if (matches (window_name) "^Compose") (begin above focus))

That's Lisp (programming language) syntax, but is pretty self-explanatory. New Thunderbird mail windows start with "Compose." The "matches" command says to look for a new window with the window_name starting with "Compose." The ^ symbol is regular expression syntax for the beginning of a string, and Compose should be at the beginning of the title of the new mail window. I tested this, and though mine always works fine, so I couldn't tell the difference, if I changed "above" to "below," the new mail window would pop below all other apps.

Again, not as simple as a setting, but once you have Devil's Pie installed, you can take over what all of your Metacity windows do.

Good luck.

---

### Post by mattack on 2007-06-15
All my settings were already set as you described...
Devils Pie sounds interesting. Maybe I'll give it a try, as I don't like the way some other windows behave.
It's in Universe, btw.

---

