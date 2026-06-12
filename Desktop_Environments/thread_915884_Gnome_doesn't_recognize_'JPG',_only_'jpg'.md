---
title: "Gnome doesn't recognize 'JPG', only 'jpg' ?"
date: 2008-09-10
forum: Desktop Environments
---

### Post by bsmith1051 on 2008-09-10
In my photos directory, I have files named both .jpg and .JPG but only the lower-case ones are recognized and given preview icons.  Is there some way to fix this?  Honestly, it seems like a dumb bug but I don't know how to report it to anyone.

---

### Post by Idefix82 on 2008-09-10
What disrtibution are you using? Are you sure that this has not got to do with the size of the pictures rather than lower case/upper case? Becuase In the preferences you can tell the file browser to only show previews for pictures which are smaller than ...MB and the default value is 5MB, which a picture can easily exceed.

---

### Post by bsmith1051 on 2008-09-11
Ubuntu 8.04.1, and simply renaming the "JPG" files to "jpg" makes the preview work.

Hmm, I'm at work now (where I also run 8.04.1) and it works ok here.  So there must be something tweaked with my home computer.  Probably, it's a combination of filename-extension and mime-type that's causing the problem.

---

### Post by Idefix82 on 2008-09-12
That's very strange. I just had a look at my mime definitions and it's all case insensitive. But what you could try is this:
go to /usr/share/mime/packages and open the file freedesktop.org.xml in gedit:
```
gksu gedit freedesktop.org.xml
```
Now locate the entry corresponding to jpegs, for example by searching for the string <mime-type type="image/jpeg">. Scroll down until you find the lines starting with <glob pattern=...> and add one such line saying
```
<glob pattern="*.JPG"/>
```

Now save and see if it solves the problem. I suspect though, that these definitions are case insensitive. I am not sure if you need to tell Ubuntu to update it's mime definitions. To really make sure that the changes took effect you can also add some silly <glob... > line like 
```
<glob pattern="*.sillyline"/>
```
and change the extension of your picture to .sillyline. See if you get a preview in the file browser. If you do then the changes took effect, so now you can try changing it to JPG. If .sillyline didn't give you a preview then you might need to restart the computer and try it again. I am sure there is a quicker way to force Gnome to update the mime definitions but I don't know of one.

I hope all this kind of makes sense to you.

---

### Post by total_moron on 2009-12-02
I have this problem too.  I tried the directions above, but I get the following error when I try to save:

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

Thing is, mine is the root account, so I don't know why I wouldn't have the permissions.

Is it possible to do this through the terminal, so that I can sudo it?

---

