---
title: "Startup Script Annoyances"
date: 2006-07-05
forum: Desktop Environments
---

### Post by chillydawg on 2006-07-05
Hey All,

This is my first post and sadly its a whine :(

I have 6.06 installed and running sweet on this Intel HT laptop. What I want to do is run a script from the ~/.config/autostart as you would normally with gnome. So I add the correct file (with the right syntax) into the autostart directory and nothing happens.

The file I want to run is a regular bash file, starting with #!/bin/bash as you would expect, if I go to console and ./script it runs as expect, but if I click on it and select "run in console" it appears and vanishes in an instant (the script takes hours to run, so its not a case of printf("foo\n"); return 0;  and then dumping the console, it *should* sit there doing its thing for ages. This is the same behavior I get when I add it to the autostart directory.

I also cant seem to get regular programs to run from there, if I put gnome-terminal into a startup file there, it simply doesnt run. Sometimes, I can see the program that *should* be running in the "Current Sessions" screen from preferances, it normally has a little clock next to it - sadly I havnt a clue what this means, even though I've had a good look at the forums and a few googles, and even clicked the help button on the screen!

Any ideas?

Cheers

Chilly

---

### Post by Ramses de Norre on 2006-07-05
Have you tried copying the file to /usr/bin, _making it executable_ and then making a file in ~/.config.autostart with this inside it: ```
[Desktop Entry]
Name=Name
Encoding=UTF-8
Version=?.?
Exec=Script name (how it's in /usr/bin)

```

---

### Post by chillydawg on 2006-07-06
No, and why would that help? Surely an executable file is an executable file. I specify absolute paths to my scripts and the permissions are correct, I do know my way around linux and this particular "feature" of ubuntu seems to be broken?

If there is some unwritten rule that only stuff in /usr/bin can be executed via autostart, then why is it not made plainly obvious when adding startup scripts via the gui - and in fact why would it be there at all, it makes no sense whatsoever.


Chilly

---

