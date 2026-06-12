---
title: "Preferred Applications - Text editor"
date: 2004-12-06
forum: Desktop Environments
---

### Post by Leif on 2004-12-06
Try as I might, I can't get the default text editor changed to emacs. I set the path to /usr/bin/emacs %s, which is saved, but the setting always gets switched back to the default text editor, and not the 'custom' one.

Cheers,

Leif

---

### Post by HungSquirrel on 2004-12-06
I don't even see an option for text editor.

---

### Post by Cygnia on 2004-12-06
I had a similar situation here; try right-clicking on a text file in Nautilus and choose "Properties" and changing the default preferred program there. That's what finally worked in my case.

---

### Post by HungSquirrel on 2004-12-06
Yay!  Now I have GVim as my editor!  :-D

---

### Post by Leif on 2004-12-06
Thanks Cygnia, that does the trick !

Leif

---

### Post by JonAtkinson on 2004-12-06
If it helps you, to change emacs to the default editor on the command line, you can pick your favourite by using```
$ sudo update-alternatives --config editor
```Hope that helps :-)

--Jon

---

### Post by dcraven on 2005-04-06
[QUOTE=Cygnia]I had a similar situation here; try right-clicking on a text file in Nautilus and choose "Properties" and changing the default preferred program there. That's what finally worked in my case.[/QUOTE]
The only problem with that is that you need to make the change for all file types that are opened by a text editor (ie. ChangeLog, COPYING, README, txt, etc). There must be a way in GNOME to change the default text editor and I'm determined to find it!

I'll post here when I do.

Cheers,
~djc

---

### Post by dcraven on 2005-04-06
Well, I haven't gotten it working yet but here is what I've found so far.

The most sane method, I'm guessing, is to use the "alternatives" method that seems to be the norm for Debian-based distros. There is an alternative called gnome-text-editor of which gedit is the only choice. Theoretically from what I've found, one should be able to issue the command```
# update-alternatives --config gnome-text-editor
``` and choose the editor of your choice from a provided list. Unfortunately gvim (my choice) or emacs does not appear as a choice as I presumed it should. 

My journey took me to the Debian bugzilla where I found a filed bug for vim-gnome ([bug 243443](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=243443)) that appears to be fixed/closed in May 2004. Then I visited the Ubuntu bugzilla and found [bug 4834](https://bugzilla.ubuntu.com/show_bug.cgi?id=4834) that Sabastien opened that states the bug is pending in Debian as of January of this year.

This doesn't seem to be fixed yet, at least for me. I am quite a newbie to the "alternatives" method that seems popular, but I tried to make an interim fix by doing the following:```
# update-alternatives --install /usr/bin/gnome-text-editor gnome-text-editor /usr/bin/gvim 50
# update-alternatives --config gnome-text-editor
``` and then choosing /usr/bin/gvim from the provided list.
Now this appears at first glance to have worked as per this output:
```
dcraven@sigma:~ $ ls -l /etc/alternatives/ | grep gnome-text-editor 
lrwxrwxrwx  1 root root  13 2005-04-06 12:11 gnome-text-editor -> /usr/bin/gvim
dcraven@sigma:~ $
```
But clicking a file of mime type text/* still opens in gedit by default.

I also found in /usr/share/mime-info/ a file called gedit.keys that when opened, seems to assign all text mime types (text/*) to gedit. I thought a dirty hack to help me find out what was going on would be to rename this to gvim.keys and make the appropriate changes in the file. This also had no affect, so I changed it back (after logout/login). I figured this was a bad fix anyway, so I abandoned it for the time being.

I could be barking up the wrong tree, or I could be misusing the update-alternatives command somehow. But it looks correct according to the man page and the results. If anyone else has more insight on the topic, maybe we can get this to work properly?

I'll keep digging in the meantime...
~djc

---

### Post by aipotu on 2005-06-17
**Here is the solution ! **

The default apps for gnome are defined in the /etc/gnome/defaults.list file.
In order to set your favorite editor (scite for me), just replace the line 
*text/plain=gedit.desktop*

by this one : 

*text/plain=scite.desktop*

and restart the X session.

---

### Post by tread on 2005-06-17
Nice, thank you! I created a symlink called gedit to gvim in /usr/local/bin .. since its the first path checked for the application, it worked. (Bad hack though :))

---

### Post by razaza on 2005-12-15
A nicer method would be the solution given in [#295829]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=295829"):

  Right-click on a text file, choose "Open with Other Application...".

  Type in favourite editor (I use /usr/bin/gvim) and click Open.

  Get a terminal, and cd to ~/.local/share/applications. There is now a
  new file in there called "gvim.desktop"

  Create a new file called "defaults.list" with the following info:
  (this is equivalent to the system-wide defaults.list file in
  /usr/share/gnome/applications)

---8<---
[Default Applications]
text/plain=gvim.desktop
---8<---

  Restart nautilus with "killall nautilus"

In my case, the file was named gvim-usercreated.desktop but that doesn't matter much. 
Now, if Gnome gets updated and it changes /etc/gnome/defaults.list, your change would still be in place.

---

### Post by hardskinone on 2007-06-11
I modified "Text editor" in Applications->Accessories menù to launch "gvim" instead of "gedit". Now all text/* mime-type are open with gvim. Hope helps.

---

