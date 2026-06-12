---
title: "Gedit plugins"
date: 2007-05-22
forum: Desktop Environments
---

### Post by el3ktro on 2007-05-22
I'm searching for two Gedit plugins but can't find anything: First, it would be nice to have sort of an integrated console/terminal window within the Gedit window, something like the Python console, but with the Bash as a shell. The second thing I'm searching for is a "code folding" plugin which enables me to fold & unfold a Python function/class definition. Does anybody know of such plugins?

Tom

---

### Post by benmoreassynt on 2007-05-22
You might prefer Kate by the sound of it. Kate has those capibilities by default. I've never really used gedit for coding, but the impression I got was that it is a bit too basic by default.

---

### Post by onbongos on 2007-05-23
the console thing is built in, i think. look under the view menu. i have it and i don't remember installing any plugins

---

### Post by el3ktro on 2007-05-23
Hmm, I see only a "bottom sidebar" there (Ctrl+F9, my gedit is in German so I don't know the exact english term). But it just opens an empty plane with a tab saying "terminal output" or something similar, but there's no output at all and I don't see a Bash prompt there either :-(

Tom

---

### Post by onbongos on 2007-05-23
ah it is a plugin - gedit-plugins package. it adds another tab to the bottom pane with a terminal view [http://live.gnome.org/GeditPlugins](http://live.gnome.org/GeditPlugins)

---

### Post by Soybean on 2007-05-23
It's not enabled by default, but there is a terminal plugin in my gedit. I installed the "gedit-plugins" package (from the ubuntu universe repository) a while ago, so it may have come from there. The plugin is called "Embedded Terminal" in English.

As for code folding, I'm not sure. In general, I try not to expect too much from gedit. ;)

---

### Post by liviubero on 2007-09-05
I enabled this Embedded Terminal plugin in Gedit but it doesn't seem to work, I don't see any prompt and I can't write anything in it. Does anyone know how can I fix this?
And isn't Kate for KDE?

---

### Post by liviubero on 2007-09-06
I never tried, due to my fragile Ubuntu installation, with a fglrx video driver, to make any silly experiments, but would it be any problem to install Kate on a Ubutnu (Gnome) system?
I looked in Synaptic and the Kdesktop is not in the dependencies, how is the case with Konqueror.

And does anybody know how to make that terminal plugin work in gedit?

And does anybody know if, in case I install Kdesktop (which tempts me a lot), would kde use the same fglrx driver, or not?

---

### Post by mcduck on 2007-09-07
Yes, I have the terminal plugin working. But I haven't found any code folding plugin yet. Still, I can manage without that as Gedit does pretty much everything else I need my editor to do.. (like play music while I'm working ;))

[http://www.elisanet.fi/~z626117/random/gedit-plugins.png]("http://www.elisanet.fi/~z626117/random/gedit-plugins.png")

I just installed the gedit-plugins package, then in Gedit went to Edit/Preferences and enabled "Embedded Terminal" in the Plugins-tab. Then I can show the terminal from View/Bottom Panel or with Ctrl-F9.

---

### Post by liviubero on 2007-09-07
I also installed the plugin and the Ctrl+F9 works fine, but the terminal wont take any input from me... it just stays there, empty and pointless...:(
And what kind of a plugin are you using to edit css???
And how come are you using Flash in Ubuntu??? Wow, I would really want to do that.

---

### Post by mcduck on 2007-09-08
I really don't know why it doesn't work for you. I'm using gedit and gedit-plugins staright from feisty's repositories.

The code popup window is the Snippets plugin. It allows you to insert pre-defined pieces of code by either typing a keyword and pressing tab to open a popup box or by using a keyboard shortcut. It handles wide variety of programming- and markup languages and you can add new keywords, keyboard shortcuts & snippets. Really useful plugin. :)

The Project Manager plugin is also nice, and I'm running a bunch of others as well. But I'd still like to find code folding plugin, that's pretty much the only feature I' missing.


Flash is Flash 8 Professional, I installed it on a Windows machine and then copied all it's files and registry keys to wine. It runs quite nice, the only problem I've found this far is that the help browser crashes the whole program. But I'm using CHM Viewer to read the help file instead.

---

### Post by liviubero on 2007-09-11
> then copied all it's files and registry keys to wineCould you be more exact?
I am booting in win just for Flash and would really like to use Flash in Ubuntu...
Did you also tried with Dreamweaver?

---

### Post by mcduck on 2007-09-11
> **liviubero said:**
> Could you be more exact?
I am booting in win just for Flash and would really like to use Flash in Ubuntu...
Did you also tried with Dreamweaver?

No, I didn't try Dreamweaver, as I prefer writing the code myself. But I found you a nice instruction that covers both: [http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper]("http://luiscosio.com/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper")

---

### Post by liviubero on 2007-09-18
I got the embedded  terminal in Gedit working.
Actually it worked already, but I had in the actual gnome-terminal set both the background and the font white, with transparency. And the embeded terminal doesn't have any transparency... so, white fonts on white background... therefore I couldn't see anything. Am I stupid or what? :mrgreen:

---

### Post by rudasn on 2008-06-01
> **mcduck said:**
> Yes, I have the terminal plugin working. But I haven't found any code folding plugin yet. Still, I can manage without that as Gedit does pretty much everything else I need my editor to do.. (like play music while I'm working ;))

[http://www.elisanet.fi/~z626117/random/gedit-plugins.png]("http://www.elisanet.fi/~z626117/random/gedit-plugins.png")

I just installed the gedit-plugins package, then in Gedit went to Edit/Preferences and enabled "Embedded Terminal" in the Plugins-tab. Then I can show the terminal from View/Bottom Panel or with Ctrl-F9.

hey, i'm very curious, which plugin are you using for intellisense (that popup with css properties)? I installed the auto complete plugin but it doesnt seem to work at all.

Cheers

---

