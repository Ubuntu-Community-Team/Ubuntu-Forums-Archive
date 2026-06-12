---
title: "Openbox compositing?"
date: 2010-08-04
forum: Desktop Environments
---

### Post by Ultra_Man on 2010-08-04
How do I turn on compositing for open box and add it to the autostart.sh file?

BTW I'm on ubuntu-minimal install.

---

### Post by snowpine on 2010-08-04
Openbox does not have compositing buit-in, you need additional packages.

You might want to check out CrunchBang Linux. It uses Openbox as its windows manager and has options to enable compositing using either xcompmgr or cairo-compmgr. I've even heard of people using Compiz with CrunchBang! 

Anyway there is some compositing info in this excellent how to: [http://urukrama.wordpress.com/openbox-guide/](http://urukrama.wordpress.com/openbox-guide/)

---

### Post by mcduck on 2010-08-04
> **Ultra_Man said:**
> How do I turn on compositing for open box and add it to the autostart.sh file?

BTW I'm on ubuntu-minimal install.

Just install the xcompmgr package, and then add it, with whatever options you want (run "xcompmgr --help" for the options), to your autostart file.

The command I'm using is "xcompmgr -cfF -t-9 -l-11 -r9 -o.95 -D6 &"

---

### Post by Ultra_Man on 2010-08-05
I tried to add xcompmgr to autostart.sh before, but it didn't work. I added it like this.

#compositing
xcompmgr

And openbox wouldn't start after I logout/login, uses metacity instead. Gnome/Openbox session was picked.

So it looks like I need to add those commands like yours right?

---

### Post by mcduck on 2010-08-05
Yes "xcompmgr" alone does nothing. You need to tell it what kind of effects you want, which is what all gibberish at the end of the command is for.

Also you must add the "&" in the end of the command to start xcompmgr in the background. Without that your startup script starts xcompmgr and then waits until it finishes (which it will never do) before continuing with your startup script.

edit: Here's an explanation for the options I'm using:

"-cfF" "c" is for soft shadows and transparency support, "f" for fade in & fade out when creating and closing windows, and "F" for fade when changing a window's transparency.

"-t-9 -l-11" shadows are offset 9 pixels from top of the window and 11 pixels from the left edge

"-r9" shadow radius is 9 pixels

"-o.95" shadow opacity is set to 0,95

"-D6" the time between each step when fading windows is set to 6 milliseconds.

"&" isn't actually xcompmgr's option, it's a built-in function in the shell itself, sending the command to run in the background.

edit2:
Depending on what stuff you are using with Openbox, you might actually have to delay xcompmg's startup a bit for everything to work correctly. In that case just use a command like this:
(sleep 3 && xcompmgr -cfF -t-9 -l-11 -r9 -o.95 -D6) &

---

### Post by hansum_rahul on 2011-05-15
Helped me a lot. Thanks for this... :)

---

### Post by henriquemaia on 2012-01-06
> **mcduck said:**
> Yes "xcompmgr" alone does nothing. You need to tell it what kind of effects you want, which is what all gibberish at the end of the command is for.

Also you must add the "&" in the end of the command to start xcompmgr in the background. Without that your startup script starts xcompmgr and then waits until it finishes (which it will never do) before continuing with your startup script.

edit: Here's an explanation for the options I'm using:

"-cfF" "c" is for soft shadows and transparency support, "f" for fade in & fade out when creating and closing windows, and "F" for fade when changing a window's transparency.

"-t-9 -l-11" shadows are offset 9 pixels from top of the window and 11 pixels from the left edge

"-r9" shadow radius is 9 pixels

"-o.95" shadow opacity is set to 0,95

"-D6" the time between each step when fading windows is set to 6 milliseconds.

"&" isn't actually xcompmgr's option, it's a built-in function in the shell itself, sending the command to run in the background.

edit2:
Depending on what stuff you are using with Openbox, you might actually have to delay xcompmg's startup a bit for everything to work correctly. In that case just use a command like this:
(sleep 3 && xcompmgr -cfF -t-9 -l-11 -r9 -o.95 -D6) &

Thanks so much for this brief but very insightful explanation. This is exactly what I was looking for my new Lubuntu.

---

