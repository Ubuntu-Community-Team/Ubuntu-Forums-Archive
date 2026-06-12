---
title: "How do i change shortkeys in CompizFusion?"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by Duranxl on 2007-08-19
Ey all.

Got a quick question
How do I change shortkeys like i could before installing compiz fusion?
e.g., i want to:
change the show desktop key
add a open terminal key
change the initiate cube key.

Now i found a "open terminal" option in general options..but i can only enable/disable and not see/change the shortkey for it!

thanks:]

---

### Post by Tylerofl on 2007-08-19
I'm having the exact same problem. You used to be able to do that in the previous version of Compiz-fusion, but yesterday's update got rid of that somehow (along with my settings profile :mad:).

---

### Post by psyopper on 2007-08-19
I'm running a slightly oder version of CF - around July 20th or so...

To change keybindings you need to determine what plugin that keybinding is associated with, then go to the Actions tab for that plugin and change it. For instance, to change the initiate cube:

Go to the "Rotate Cube" plugin -> Actions Tab -> General -> Initiate to set what key you would  like to use to initiate the cube.

---

### Post by Duranxl on 2007-08-19
> **psyopper said:**
> I'm running a slightly oder version of CF - around July 20th or so...

To change keybindings you need to determine what plugin that keybinding is associated with, then go to the Actions tab for that plugin and change it. For instance, to change the initiate cube:

Go to the "Rotate Cube" plugin -> Actions Tab -> General -> Initiate to set what key you would  like to use to initiate the cube.

But there is no "action tab" There's just this list where i can enable/disable stuff.. 
Initiate is in the list..but i can only disable/enable it :confused:

---

### Post by Duranxl on 2007-08-19
Here's a screenshot:
[http://wpxldk.googlepages.com/compizpicture.png]("http://wpxldk.googlepages.com/compizpicture.png")

---

### Post by Shne on 2007-08-19
I have the exact same problem since the recent update (I think it was yesterday the update came, I just installed it now). Plus it reverted my settings to some default settings.
Can't assign the hotkeys of lots of the plugins, actually all of the plugins I need to assign hotkeys for. some plugins, however, still have the 'actions' tab.

Any easy way to revert to the version i had before?

---

### Post by psyopper on 2007-08-19
There might be with Aptitude, but only if you manually updated it with Aptitude and used a particular switch (that I don't recall off the top of my head).

The alternative is to use [Vorian's repositories]("http://debs.vorian.org/") but it will require removing the currently installed CF and replacing it with his from late July. I do believe that Trevino is working on getting his broken build/deb fixed, you could hang out for a few days and see if the next update fixes it...

---

### Post by Duranxl on 2007-08-19
> **psyopper said:**
> There might be with Aptitude, but only if you manually updated it with Aptitude and used a particular switch (that I don't recall off the top of my head).

The alternative is to use [Vorian's repositories]("http://debs.vorian.org/") but it will require removing the currently installed CF and replacing it with his from late July. I do believe that Trevino is working on getting his broken build/deb fixed, you could hang out for a few days and see if the next update fixes it...

Ok
what link do i need to use to add vorians repositories?
nvm: found it

---

### Post by Shne on 2007-08-23
Even with the update today, most of the plugins are inconfigurable with CCSM.
But despair not, there is another way.

use the Configuration Editor from Applications -> System Tools (right click and edit menus to add it if it's not there already).
in the configuration editor, go to /apps/compiz/plugins/<insert_plugin_you_want_to_edit_settings_for>/allscreens/options and you can access and edit some settings inaccesable with CCSM as easy as with CCSM (or almost).

---

