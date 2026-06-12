---
title: "M3U File Maker"
date: 2009-03-29
forum: General Help
---

### Post by accooper on 2009-03-29
I am in need for a program that will easily make m3u playlist files.  Anyone now if any are out there?

:guitar:

TIA
Andrew

---

### Post by kuja on 2009-03-29
If I do recall correctly, m3u files are just one URL per line, very simple files. I don't know of any dedicated playlist making programs (though several popular players have the option to export as m3u), but if you want I could write you one, I suppose :D (wow, wait, I'm already half done ... oops)

---

### Post by kuja on 2009-04-01
Tah dah.

:popcorn:

---

### Post by accooper on 2009-04-01
OK, if you could now explain to me how to install it?

Remember eye's from Texas

:guitar:

Andrew

---

### Post by kuja on 2009-04-01
Well, for the moment it will just run rather than actually install, I'll take care of that tonight I think (ie: make a .deb package that you can install with gdebi, or something, and add a menu entry to your applications menu). 

For now, you'll need to extract it with your favorite archive program because it's a bzip2'd tar archive. 

(to do it from a terminal, you can use the command "tar xf m3uplaylisteditor_1.0.tar.bz2")

Next, if you don't have pykde installed (which is what I wrote it with ... made it very easy) then you'll need to install it for it to work. Either pull up your favorite graphical package manager and install "python-kde4", or run "sudo apt-get install python-kde4". (depending on things, this step may take a while.)

Next, in a terminal (until I cook up the *.deb), navigate to the folder containing main.py, and run "python main.py"


I guess that stuff isn't exactly newbie friendly ... I'll see how fast I can cook up the *.deb.

---

### Post by kuja on 2009-04-02
I've made a deb that should work, and attached it, as well as fixing up a few small issues. Install it with GDebi and it should install any dependencies automagically, I think. I've made a .desktop launcher for it, but I haven't set the category for it yet, which means either you won't see it or it will be in lost + found (if applicable). You can run it from the terminal by pulling it up and typing "m3uplaylisteditor" and hitting enter. 

Let me know what you think, because I have a lot of ideas floating around with regards to it.

---

### Post by kuja on 2009-04-02
Seems I let a couple bugs slip through the cracks. They're fixed now.

---

### Post by sideaway on 2011-03-21
just used this editor, bumping to say thank you :)

---

