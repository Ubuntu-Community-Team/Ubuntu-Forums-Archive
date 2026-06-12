---
title: "I broke it. My new Xubuntu install."
date: 2006-06-30
forum: Desktop Environments
---

### Post by Flaystus on 2006-06-30
XMMS wouldn't close so I restarted the box via the restart command on the menu.

It took like 3 min for it to do so. Upon reboot it loads, but the menu bars at the top and bottom are gone. Help?

edit:oops was gonna make title more descriptive but can't now, sorry.

---

### Post by K.Mandla on 2006-06-30
Yikes! :o

Try right clicking on the desktop. If you get a menu, pick Settings > Settings Manager. That should pop up some settings options, and one of them is "Panel." From there, you can rebuild those toolbars from scratch.

---

### Post by Flaystus on 2006-06-30
Yikes indeed.

The Panel button does nothing. All other buttons in there work fine.

---

### Post by K.Mandla on 2006-06-30
Hmmm. See if you have a folder like this inside your home directory. ...

.config/xfce4/panel

If you can open thunar (the file manager), it's inside your home directory, at that location. Remember that the .config file is hidden, so you'll have to show hidden files to see it (press CTRL+H).

You should see a mess of files in there, which represent the panel items, along with panels.xml. 

I'm guessing your folder is either missing or empty ... ?

---

### Post by Flaystus on 2006-06-30
Just went there to try to delete the panel config file as I saw suggested on another forum.

All the files are there. Deleting the config did nothing.

Their section suggestion was to reinstall XFCE but I Have no idea how to do that.

---

### Post by Flaystus on 2006-06-30
If I manually start the XFCE4-panel it shows up but if you, say for example, try to shut down using it it gives an error about the session not running.

If you shut down by right clicking the desktop it does NOT come back upon reboot unless you manually run it again.

Meanwhile the little mouse in the wheel when it loads is no longer centered on my screen. 



At least once every major release I give linux a change, each time I get dangerious and break it. :-\"

---

### Post by Flaystus on 2006-06-30
Have I stumped the Linux gurus?

---

### Post by K.Mandla on 2006-07-01
Hmm. I haven't run into this problem before, so I don't have a solid suggestion for you. But it sounds like something is seriously broken. 

If it were me, I would rebuild from scratch, but I don't know if that's an option for you. Keep poking around though, and see if anyone has an idea for you.

---

### Post by Flaystus on 2006-07-03
Well it IS an option but its just kinda scarey that one frozen app could bring an entire OS down.

Maybe I'll give it a try next week when i get more time.

---

### Post by trash on 2006-07-04
bittorrent just caused the same problem for me, what to do is:

open a terminal
start xfce4-panel and leave it running
restart your machine but remember to save session.

Once you reboot your panel should start automatically... mine did.

---

