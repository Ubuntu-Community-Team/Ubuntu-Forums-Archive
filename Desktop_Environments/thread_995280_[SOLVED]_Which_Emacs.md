---
title: "[SOLVED] Which Emacs???"
date: 2008-11-27
forum: Desktop Environments
---

### Post by Barriehie on 2008-11-27
In my endeavors to find an editor I've decided on Emacs, although the learning curve has kept me at bay for awhile!  So I installed via Synaptic and now I've got 3 Emacs entries in my Accessories.  1st is Emacs 22 Client, 2nd is Emacs 22 GTK and 3rd is Emacs 22 X11.  Are all of these necessary???  I can understand the Client entry but what about the GTK and X11 ones???

TIA,
Barrie

---

### Post by hictio on 2008-11-27
[b]
Which Emacs???
[/b]

Anyone!! :D

They are basically the same thing, the "Emacs 22 GTK" is the one designed to be used on a graphical environment like Gnome, you'll have things like drag and drop, etc.

"Emacs 22 X11" it is designed to be used within the CLI, although, it has color syntax, etc.

"Emacs 22 Client" is sort of a server, an Emacs server, listening all the time to your input, and if you are going to edit something, and type "emacs", the client will open an already started session, instead of opening a new one.

My recommendation, learn to use it on CLI, on the Terminal, what you'll learn there will be useful to use emacs whether you are editing a text file on your box, or accross the internet.

Also, don't forget to edit your $HOME/.bashrc file and include:

```

export EDITOR=emacs
export VISUAL=emacs

set -o emacs

```

Close the terminal, and open a new one, or type:

```

source ~/.bashrc (ENTER)

```

To load thoe values.

---

### Post by Barriehie on 2008-11-27
Thank You Hictio!  Glad you mentioned about my .bashrc file; I forgot that...

Barrie

---

### Post by hictio on 2008-11-27
No mention, if you want to take it to the "next level" :D
Add Emacs keybinds to Nautilus, Firefox, etc, etc.

```

gconftool-2 --set /desktop/gnome/interface/gtk_key_theme Emacs --type string

```

Or open gconf-editor, and navigate to '/desktop/gnome/interface/gtk_key_theme', and set it to 'Emacs'.


To revert, from the CLI, use --unset

---

### Post by Barriehie on 2008-11-27
Keybinds yes!!!  After I find an emacs cheat sheet...  This was part of the learning curve thing I was talking about.  Last time I saw emacs was early '80ties...

Barrie

---

### Post by hictio on 2008-11-28
If you want a few key binds examples, take a look at [my DOT emacs file]("http://oesediez.blogspot.com/2008/01/oh-emacs-my-emacs.html"), also, perhaps you might find this [Emacs comparisons I did]("http://oesediez.blogspot.com/2008/05/emacs-love-it-bloat-it.html").

---

### Post by Barriehie on 2008-11-28
> **hictio said:**
> If you want a few key binds examples, take a look at [my DOT emacs file]("http://oesediez.blogspot.com/2008/01/oh-emacs-my-emacs.html"), also, perhaps you might find this [Emacs comparisons I did]("http://oesediez.blogspot.com/2008/05/emacs-love-it-bloat-it.html").

Cool thing about the backup files going in a specific dir.  For what I'm going to do with emacs, so far at least, it is massively bloated.  I did have the need to generate a shell script with a macro repeated many times and emacs was all I could think of, and find, that could do the macros.  For that one feature I've installed it.  Also removed bluefish and geany...    :-)

So far I'm impressing myself!  Don't know why I've waited so long to do this.  'Course it's been about 20+ years since I've even heard of emacs...  :-)

Barrie

<ignore>btw: If I've copied something say from the browser how do I paste it into the buffer??? C-y isn't working!</ignore>

Thanks

---

### Post by hictio on 2008-11-28
> **Barriehie said:**
> 
<ignore>btw: If I've copied something say from the browser how do I paste it into the buffer??? C-y isn't working!</ignore>

Thanks

No, it won't... Specially on the CLI version, paste it doing a Shift + Insert.

---

### Post by Barriehie on 2008-11-28
> **hictio said:**
> No, it won't... Specially on the CLI version, paste it doing a Shift + Insert.

Thank you, and the cheat sheet grows a bit more...  :-)

Barrie

---

### Post by hictio on 2008-11-28
> **Barriehie said:**
> Thank you, and the cheat sheet grows a bit more...  :-)

Barrie

Ja ja ja, the good thing about this one is that works on any other app as well, the bad thing, you need that key (Insert) on your keyboard!

---

