---
title: "Ubuntu 8.10 and no window borders"
date: 2008-12-19
forum: General Help
---

### Post by BWF89 on 2008-12-19
First my computer had a problem with not remembering my resolution. So I went into terminal and entered:
```
gksudo nvidia-settings
```
and than used nvidia-settings to adjust my resolution and than saved the configuration to the xorg.conf file.

So I restart my computer and log in to make sure if it worked, and it did.

This is where the problems started. I went into Firefox and there was no window borders. I thought it might just be Firefox so I went into other programs and they also had no window borders.

After an hour or so of searching around I came across a thread on these forums where someone said that the solution to go into terminal and enter:
```
sudo metacity --replace
```

The first thing I noticed that there was no terminal GUI at all. There was just a white box where the terminal was supposted to be. But I knew the program was still working because when I hit the backspace key I heard the sound my system makes when theres no letters/numbers left to delete. So I typed in the command, entered my password, pressed enter, and a second later all the window borders were back and everything is the way it should be.

But than when I tried restarting my computer and logging back into my account to make sure that the settings had saved. But they didn't.

Does anyone here have a solution to my problem other than having to go into terminal and running the "sudo metacity --replace" command every time I log into my computer?

---

### Post by jerome1232 on 2008-12-19
Yes basically we'll create a small script that runs this command automaitcally when you log in.


first pop open a terminal:
```
mkdir ~/bin
gedit ~/bin/metacity-loader

--------Now enter the text below---------
#!/usr/bin
metacity --replace
----Save the file and close gedit-------

chmod +x ~/bin/metacity-loader

```

Now click System-Prefrences-Sessions

select "Add"

Name: Metacity
Command: metacity-loader
Comment: doesn't matter :)

Now click "Add" and logout then login it should work for you.

---

### Post by nordmichael29 on 2008-12-19
I think to get them back you can open a terminal and type in sudo gtk-window-decoratorI think that works not entirely sure though.

---

### Post by BWF89 on 2008-12-19
> **jerome1232 said:**
> [COLOR="Red"]**#!**[/COLOR]/usr/bin
metacity --replace
The script you had me create only works if you don't include the part I made red. But other than than thanks a lot.

Do you have any idea as to why I was having this problem to begin with? Did my editing of the xorg.conf file have anything to do with it, or was that completely unrelated?

---

### Post by jerome1232 on 2008-12-19
my bad, that should've been #!/bin/bash

That's what I get for working from memory

---

