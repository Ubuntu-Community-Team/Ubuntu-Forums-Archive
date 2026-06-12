---
title: "Problem displaying thumbnails in Thunar"
date: 2014-02-02
forum: Desktop Environments
---

### Post by PianosBTT on 2014-02-02
I'm fairly inexperienced at using Linux, so I'm not sure what to do here.

Thunar doesn't seem to handling my thumbnails very well.  It'll work for a little while and display them correctly for photos and videos, but after a little bit of navigating around they'll just stop loading altogether.

I have thumbnails enabled via the Display/Desktop menu and via Thunar preferences.

Any help would be appreciated, thanks!

---

### Post by Toz on 2014-02-02
Hello and welcome to the forums.

After they stop loading, what do you need to do to get them to load again? Restart Thunar? Log out and back in again? Restart the computer?
And is it a specific graphic or video or folder that always causes the thumbnailing to stop?

The next time it happens, have a look at the bottom of the ~/.xsession-errors log file to see if there is an indication of what might have happened.

---

### Post by PianosBTT on 2014-02-02
I usually log in and log out and that does the trick, restarting Thunar doesn't seem to do anything.

It seems to happen whenever I open a folder with a large amount of pictures.  I'll watch the thumbnails start loading for the pictures, then it'll stop at a picture then Thunar will stop loading thumbnails completely, even if I re-open the folder.  None of the thumbnails displayed before will load.

My x.session-errors file is:
```
Script for cjkv started at run_im.Script for default started at run_im.
openConnection: connect: No such file or directory
cannot connect to brltty at :0

```

I can't make anything out of it.

---

### Post by Toz on 2014-02-02
When it stops loading at a picture, is it always the same picture?

And does closing thunar, running:
```
thunar -q
```
...and starting thunar again help to start re-displaying the thumbnails?

Also, try starting thunar from the command line:
```
thunar
```
...and try to get the thumbnails to stop. Then look back at the command prompt and see if any error messages are displayed.

---

### Post by PianosBTT on 2014-02-02
It's hard to tell to be honest, scrolling down it doesn't completely stop displaying thumbnails, there's a few scattered around.  But yes, it does seem to stop for the most part after a certain picture.  And again, if I open the folder again none of the thumbnails that were displayed before are there.

The only error I got in terminal was:
```
Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.
```

---

### Post by Toz on 2014-02-03
Try removing that picture and see if it helps. Maybe the picture is somehow damaged/incorrect. How many pictures are in that folder?

---

### Post by PianosBTT on 2014-02-03
I tried it, no luck :(.

There's around 5,000 pictures in that folder.

**Edit:**  I found another folder of pictures that seems to have the same effect, this one with around 200 pictures.  They're both folders of iPhone photos if that helps at all.

---

### Post by Toz on 2014-02-03
I wonder if its related to [this bug report]("https://bugzilla.xfce.org/show_bug.cgi?id=8004").

Do the following commands return anything:
```
dmesg | grep -i tumblerd
```
```
cat /var/log/syslog | grep -i tumblerd
```

Does deleteing your ~/.thumbnails directory help?

---

