---
title: "Make a window not appear in the window list"
date: 2005-01-24
forum: Desktop Environments
---

### Post by KLineD on 2005-01-24
Hi, I recently managed to have a transparent terminal (Eterm) that seems to "blend" with the wallpaper. It's all nice but I can't seem to make the window list not to list the Eterm window? In KDE it was simple but I can't find anything in GNOME

Thanks!

---

### Post by 23meg on 2005-04-29
this would be handy for me too, for the same purpose

---

### Post by 23meg on 2005-05-03
i'm sure i saw something mentioned on the forums that does this, but i just can't find it. i think it iconified apps to the notification area.

---

### Post by Nis on 2005-05-03
[QUOTE=23meg]i'm sure i saw something mentioned on the forums that does this, but i just can't find it. i think it iconified apps to the notification area.[/QUOTE]
 Try out [Devil's Pie](http://www.burtonini.com/blog/computers/devilspie).  It's in universe and does exactly what you want.  There is one issue however: the version of devilspie is broken if you try to change a windows type or remove window decorations.  It sounds like you've already got Eterm borderless already so this issue shouldn't affect you.  Just make sure to read /usr/share/doc/devilspie/README.gz to learn how to configure and run devilspie.

---

### Post by 23meg on 2005-05-03
oh thanks; i've fiddled with devil's pie before for the tasks you mentioned, and it failed horribly.. i didn't know it could do this. i'll give it a go.

btw, what i saw on the forums *wasn't* devilspie, i'm sure about that.

---

### Post by 23meg on 2005-05-03
i've just reinstalled devilspie via apt but can't find the devilspie-reference.html file which is the main documentation anywhere. the readme file says it's created from the source, and obviously since i've not built it from source it's not around (should have been included in the package, i think) . the man page is blank, and i can't find any info on how to do what i want with devilspie anywhere on the web. 

can a devilspie expert enlighten me on how to remove windows from the window list using devilspie? or maybe just post your devilspie-reference.html?

---

### Post by Nis on 2005-05-03
There should be a sample devilspie.xml in the /usr/share/doc/devilspie directory.
```

sudo updatedb -c
slocate devilspie.xml

```
Basically devilspie configuration consists of "flurbs" followed by matches followed by actions.  The sample config provides a flurb for matching all Xchat windows and the action is to pin them to a certain desktop.  Use that as an example and you can do almost anything.  Match the Eterm window (probably by window name) and perform the actions to remove it from the tasklist and pager (and possibly move it as well).  The README.gz file is really important here since it contains a list of all matchers and possible actions.

---

### Post by 23meg on 2005-05-03
ok, did a reinstall, and got to the file this time. it seems the action i needed was "DevilsPieActionHide". but i have another problem now: every time i hit my shortcut key combination to hide all windows and show the desktop (equivalent of the "show desktop" panel applet) the Eterm window i "hide" disappears, nowhere to be found. 

i've tried using a combination of the skip_pager and skip_tasklist properties to prevent this, but no luck yet.

---

