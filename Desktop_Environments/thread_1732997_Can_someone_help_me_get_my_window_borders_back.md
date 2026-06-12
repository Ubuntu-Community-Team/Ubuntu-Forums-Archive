---
title: "Can someone help me get my window borders back?"
date: 2011-04-18
forum: Desktop Environments
---

### Post by twtgd09 on 2011-04-18
After a reinstall of compiz using this guide: [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)
I've managed to re-enable compositing and advanced dekstop effects... at the expense of my window borders. Could someone please guide me through torubleshooting and eventually getting them back, without disabling desktop effects? Thanks

---

### Post by deconstrained on 2011-04-19
You may be using Emerald/Beryl as your window decorator, and it's hella glitchy in my experience. I always had that exact problem. Go into the CompizConfig Settings Manager, and look for "Window Decoration" in the "Effects" section. Replace the content of "Command" with "gtk-window-decorator --replace", or experiment with other commands (i.e. emerald) to see if you can get a command that works for you.

---

### Post by Herazio on 2011-04-19
Isn't it possible to change this via a program named compiz-icon ? I believe there's a package for this.

As the previous post stated. Try that and check which window decorator you're using. After you installed compiz-icon you can easily switch between the window decorators. Click on it and set your desired window decorator.

You should also try to switch to one decorator and afterwards go back to the other. See if that makes a difference.

It's a stupid idea but I'd like to have my share of helping in the community ^^'

Regards

Herazio

---

### Post by Copper Bezel on 2011-04-19
It's called *fusion*-icon. But that toggles window managers, not decorators (I.e., Compiz with Emerald or Compiz with gtk-window-decorator would just switch to Metacity with Metacity and back.)

To the OP, you probably missed the package compiz-gnome, which includes the GTK window decorator for the Compiz window manager. Check if it's installed.

---

### Post by Krytarik on 2011-04-19
> **Copper Bezel said:**
> It's called *fusion*-icon. But that toggles window managers, not decorators (I.e., Compiz with Emerald or Compiz with gtk-window-decorator would just switch to Metacity with Metacity and back.)
Nope. It toggles window decorators as well, as if you would run "emerald --replace" or "gtk-window-decorator --replace" respectively. And if you do so, it changes the "Command" in the settings of Compiz' "Window Decoration" plugin to the one you have selected, instead of just "/usr/bin/compiz-decorator", the default.

---

### Post by twtgd09 on 2011-04-20
I added the gtk replace thing and now both my window borders and my better effects are gone. reinstalling.

---

### Post by Copper Bezel on 2011-04-20
Again, I think you might just be missing some key packages, like compiz-gnome, on which the gtk-window-decorator command depends.

[QUOTE=Krytarik]Nope. It toggles window decorators as well, as if you would run "emerald --replace" or "gtk-window-decorator --replace" respectively. And if you do so, it changes the "Command" in the settings of Compiz' "Window Decoration" plugin to the one you have selected, instead of just "/usr/bin/compiz-decorator", the default.[/QUOTE]

Oh, huh. I didn't realize. Thanks for the correction!

---

### Post by twtgd09 on 2011-04-21
i dont see any of those packages missing.

---

### Post by Copper Bezel on 2011-04-21
I'm kind of a moron, because I didn't check your link until just now. Are you really still using Feisty Fawn? Only the spring releases of even-numbered years are Long Term Support releases, so if you want old and stable, you should at least upgrade to 8.04 - 7.04 is quite dead.

If you're not using Feisty, the warning on the page applies. There have probably been package name changes since '07.

Edit: Misspoke, there; I meant that I could understand being on 8.04 more easily than being on 7.04. You'd want to upgrade to 10.04, which is the latest LTS, if you want something you can keep for a while.

---

### Post by deconstrained on 2011-04-21
> **twtgd09 said:**
> I added the gtk replace thing and now both my window borders and my better effects are gone. reinstalling.
I hope you mean just Compiz. It's not worth your time to reinstall Ubuntu for a little problem like that. You should fire up jockey-gtk and check to see if you're using the latest graphics driver for your video hardware. Another thing you could try is leaving the window decorator field empty.

Something else to try: open a terminal and issue the command "which [window decorator command]" (without option flags) to get the full path to the executable of the window decorator command you wish to use, and then use that. If the command returns nothing, something is wrong.

---

### Post by twtgd09 on 2011-04-22
I reinstalled all of compiz's stuff, everything works again, and im using 10.10 to the person who asked

---

### Post by Copper Bezel on 2011-04-23
Oh, good, so it probably was just something that had changed since the guide was written. Glad that worked out. = )

---

