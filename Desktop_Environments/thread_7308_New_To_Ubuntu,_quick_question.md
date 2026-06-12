---
title: "New To Ubuntu, quick question"
date: 2004-12-05
forum: Desktop Environments
---

### Post by jlacroix on 2004-12-05
hello all, I just set up Ubuntu, installed the nvidia drivers and went to town on synaptic. I have my desktop set to 1024x768, and it looks great. However, the login screen is not set to this resolution, it switches itself to 1024x768 when I login in. How do I make EVERYTHING 1024x768?

Oh one more very important thing. My mobo has some crappy soundcard built in. I have a PCI Soundblaster Surround card that I use instead. I have to tell each application to use the Soundblaster one by one, how do I make it globally the default? I have my internal soundcard disabled in my bios but Ubuntu wants to try to use it anyway.Thanks in advance!

---

### Post by JProgrammer on 2004-12-05
I can answer the first one.

edit /etc/X11/XFree86.conf and find your resolutions section and make 1024x768 the first resolution in the list for all depths

---

### Post by jlacroix on 2004-12-05
Thanks, I already changed that in my config file, I will know if it corrected the problem the next time I log out.

By the way, anyone know how to change the Ba$h prompt in Konsole? Mine says  "jeremy@JLACROIX:~ $"

---

### Post by jlacroix on 2004-12-05
Oh and what about KDE 3.3? The one that I got from universe was like KDE 3.2 I think...

---

### Post by HungSquirrel on 2004-12-06
> By the way, anyone know how to change the Ba$h prompt in Konsole? Mine says "jeremy@JLACROIX:~ $"
Open ~/.bashrc and look for the line that starts with *PS1=* .  Comment it out by placing a # at the beginning of the line.  Then make a new line that starts with *PS1='* , write in the code to make the prompt how you want it, and close the line with a *'*.

Examples of what sorts of code you can put in PS1 to make a custom bash prompt including color codes, etc. can be found [here](http://www.google.com/search?q=bash+prompt+howto&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official).

Save the file.  You may need to logout and log back in to see the effects systemwide, but you can test your prompt by opening a terminal and entering *su $USER*.

---

### Post by jlacroix on 2004-12-06
I'll check that out, thanks!

By the way, I fixed the resolution problem with the tip that was posted above, thanks alot!

Edit: I was able to edit the Bash Prompt! You guys rule, I think Ubuntu and I will get along quite well.

---

### Post by jlacroix on 2004-12-06
Alrighty, everything is solved, except for my audio problem. Is there a way to make my PCI the default for everything, versus the internal soundcard?

---

### Post by clasqm on 2004-12-06
Can you disable the internal card in the BIOS? I did that on mine and while the internal card still shows up in the mixer app, at least no pragram tries to send any music through it.

---

### Post by jlacroix on 2004-12-06
Yes, it's disabled in the bios. Fedora had a way of selecting the default soundcard, but I don't remember how I did it, or if it can be done in Ubuntu.

---

