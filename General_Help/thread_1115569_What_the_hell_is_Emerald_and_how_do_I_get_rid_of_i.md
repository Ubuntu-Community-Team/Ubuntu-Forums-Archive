---
title: "What the hell is Emerald and how do I get rid of it?"
date: 2009-04-04
forum: General Help
---

### Post by pan69 on 2009-04-04
Hi guys,

So I installed Compiz and with it came this thing called Emerald which seems to be some sort of theme manager. It wouldn't be so bad if this Emerald wouldn't shuff some pretty nasty looking themes down my throat. I'm pretty happy with my normal Gnome desktop theme (Human) and I don't need my window borders to look like a bloody Christmas tree. Unfortunately when I remove this Emerald I'm no longer able to enable Visual Effects.

I'd like to keep my normal Gnome theme while using desktop effects enabled. I didn't seem to have this problem in the past when using Compiz.

Any help would be very much appreciated.

Thanks,
Luke

---

### Post by mb_webguy on 2009-04-04
Emerald is the default window manager for Compiz, and allows for nifty things like transparency.  You can get good themes for Emerald at [Gnome-look.org]("http://www.gnome-look.org/index.php?xsortmode=down&page=0&xcontentmode=102").  

However, if you prefer, you can force Compiz to use Gnome's default window manager, Metacity, instead.  Just go to System->Preferences->Advanced Desktop Effects Settings, Window Decoration.  In the Command line, put "/usr/bin/metacity --replace".  Now restart X with Ctrl+Alt+Backspace.

---

### Post by pan69 on 2009-04-04
Hi. Thanks for your help!

Unfortunalty I do not have an option "Advanced Desktop Effects Settings" I figured you meant the "CompizConfig Settings Manager". When I go in there and select the option "Window Decoration" and replace "/usr/bin/compiz-decorator" with "/usr/bin/metacity" then issue a "metacity --replace" from the command line followed by a CTRL+ALT+BACKSPACE and log in again, my screen flickers like crazy and I do not have any borders on my windows.

Any ideas?

Thanks,
Luke

---

### Post by mb_webguy on 2009-04-04
Do "metacity --replace" from the Run dialog (Alt+F2) instead of the terminal.  When you're running it from the terminal, it's only going to last until the process is killed (with Ctrl+C) or the terminal closes, whichever comes close.  Guess what's happening when you use Ctrl+Alt+Backspace?  :)

Of course, you really shouldn't have to enter that command at all if you have it in the Command line of the Window Decoration plugin, and have that plugin enabled.  Whenever you login (such as when you restart X) Compiz should use the specified window decorator.

---

### Post by pan69 on 2009-04-04
Hi. Sorry to bother you with this but when I select Metacity as my window decorator my visual effects are also reset back to normal mode. I only seem to be able to use visual effects when selecting Emerald as a window decorator. Any ideas why that is?

I currently have in window decorator command line "/usr/bin/metacity --replace".

Thanks,
Luke

---

