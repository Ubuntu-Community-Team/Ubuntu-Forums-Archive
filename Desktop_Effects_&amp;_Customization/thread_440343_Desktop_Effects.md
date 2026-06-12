---
title: "Desktop Effects"
date: 2007-05-11
forum: Desktop Effects &amp; Customization
---

### Post by ep3w on 2007-05-11
I have a dell M65, just installed feisty on it and everything seems to be working good so far...even wireless :)  but when i enable desktop effects, everything seems to work but the title bars on gaim/firefox with the close/minimize/maximize buttons disappear.  It doesn't lag or anything and I am pretty sure my nividia drivers are installed correctly.  I can access all the nvidia options for it and it runs smooth just the lack of title bars.  Is it supposed to do this?

---

### Post by btaub on 2007-05-11
It could be a problem with your installation of emerald.

From within your gnome session, open a console and see if it's running:

**ps -ef | grep emerald**

it should spit something out like this:
user    27977     1  0 15:02 pts/1    00:00:00 emerald

If you don't see it running, try starting it from the same console:

**emerald &**

If there is a problem, it should spit out some useful info for you to google.  If there's no problem, it should start and you should see your title bars.

Good luck,
-B

---

### Post by ep3w on 2007-05-11
This is what it gives me after I type in the first command:
ryan      6168  6110  0 23:19 pts/0    00:00:00 grep emerald
This is what it gives me when I type in the second command:
[1] 6171
ryan@ryan-laptop:~$ emerald: Could not acquire decoration manager selection on screen 0 display ":0.0"
I did not have emerald installed before but thought synaptic package manager I installed emerald and what it told me was neccesary and also the emerald themes package.
I still have no titlebars though.  I am enabling the desktop effects through the system>preferences not in beryl.  I don't have beryl installed.

---

### Post by MasonM on 2007-05-11
Emerald is for Beryl not Compiz.

The problem comes from Compiz using "Texture from Pixmap" rendering path. In Beryl you simply change it to Copy and the problem is solved.

The detailed settings for Compiz can be changed in the GConf Editor.

---

### Post by ep3w on 2007-05-11
so for bein a noob but how would i go about changing it in the gconf editor?

---

### Post by tyler22 on 2007-05-11
hmmm I think you can solve this problem by downloading the gnome compiz manager in synaptic. A friend had this problem and there was a setting in the compiz manager that was similiar to the "copy" selection in the beryl manager. I would give it a try!

---

