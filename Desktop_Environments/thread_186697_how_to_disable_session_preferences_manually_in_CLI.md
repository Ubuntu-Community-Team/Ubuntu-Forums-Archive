---
title: "how to disable session preferences manually in CLI ?"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Izzie on 2006-06-02
I was trying to get Xgl/Compiz to work on my machine using wiki.ubuntu.com guide. Now my X session crashes at startup. 
From that point I've been searching for how to disable these session preferences I've set. Couldn't find any useful info about where is the file to modify, or how to do it. 

I checked gnome.org guide and [http://www.gnome.org/learn/admin-guide/latest/sessions-3.html](http://www.gnome.org/learn/admin-guide/latest/sessions-3.html) didn't help. 

BTW help.ubuntu.com could provide the info I'm looking for here:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)
> 9.3.	How do I run programs automatically when GNOME starts?
   1.Choose System->Preferences->Sessions.
   2.Click on the Startup Programs tab.
   3.Use the Add, Edit, and Delete buttons to manage programs to run at startup. 

Last step I did in tryng to get Xgl/compiz to work was:

[https://wiki.ubuntu.com/CompositeManager/InstallingCompiz](https://wiki.ubuntu.com/CompositeManager/InstallingCompiz)
> Method A: Session (GNOME)

You can start compiz at the beginning of each Xgl server session by placing the following two commands in your session file located at "System > Preference > Sessions". Go to the right-most tab, create a new entry and type in the following:

compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher water

Now create a new entry for the window-decorator:

gnome-window-decorator

Close the Session Preference Panel. Now compiz should start every time you log into Xgl-Gnome. 

---

### Post by jobezone on 2006-06-02
Delete or edit (how I wouldn't know) **~/.gnome2/session**.

---

### Post by Izzie on 2006-06-02
I already tried that, that's why I said:> I checked gnome.org guide and [http://www.gnome.org/learn/admin-gui...essions-3.html](http://www.gnome.org/learn/admin-gui...essions-3.html) didn't help. 

the .gnome2/session file exists is where it is supposed to be but is empty

for the how, you can open a console via ctrl+alt+F1 and do it in command line interface (CLI) or simply boot on the ubuntu cd and do it from there.


anyways, as it was a fresh install for the sole purpose of testing Xgl/Compiz I fixed my problem by reinstalling from scratch, I am now trying to *not* end in the same stuck situation.

--edit-- got Xgl/compiz to work on a nvidia 6600GT athlon64 3200+ machine with the [https://wiki.ubuntu.com/CompositeManager/Xgl](https://wiki.ubuntu.com/CompositeManager/Xgl) I followed Method A: Xgl session for Xgl and Method B: Script for compiz now 
to run it I just have to choose a Xgl session, and then execute the script.

---

### Post by jobezone on 2006-06-02
ah, sorry about that.. Didn't fully read your post.

---

