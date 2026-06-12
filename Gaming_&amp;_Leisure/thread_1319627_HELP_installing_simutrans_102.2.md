---
title: "HELP installing simutrans 102.2"
date: 2009-11-08
forum: Gaming &amp; Leisure
---

### Post by il pepe on 2009-11-08
How do i correctly install this game?
I had 102 of something from te resipartory's, but the versions gives problem with saving and loading.
So i deleted the simutrans version. and i unzipped the new version in the same directory as the old version.
But the thing doesn't work. 

Any help?

---

### Post by Perfect Storm on 2009-11-09
More info is needed.

I hope you didn't replaced the repo. files of simtrans by ectracting the new downloaded version from [http://www.simutrans.com/download.htm#Simutrans_Complete](http://www.simutrans.com/download.htm#Simutrans_Complete) . You can't do that.

If that is not the case, you have to describe what you did more detailed, eventually with terminal in/output.

---

### Post by il pepe on 2009-11-09
> **Artificial Intelligence said:**
> More info is needed.

I hope you didn't replaced the repo. files of simtrans by ectracting the new downloaded version from [http://www.simutrans.com/download.htm#Simutrans_Complete](http://www.simutrans.com/download.htm#Simutrans_Complete) . You can't do that.

If that is not the case, you have to describe what you did more detailed, eventually with terminal in/output.
euhm that is pretty much exactly what i did :S

So how do i get simutrans 102.2 installed correctly?

---

### Post by ddswanson@gmail.com on 2009-12-21
I also had trouble at first...
There is no installer.


After downloading and extracting the file mentioned above

Go into the extracted simutrans directory

Right click "simutrans" 

Goto "properties"

Goto the "Permissions" tab

Check "Allow executing file as program"

Now click on "simutrans"

---

### Post by il pepe on 2009-12-21
Okay. Got it working again! thanks a lot!

---

### Post by chaosx9 on 2010-04-12
Looking for the solution on this, i found a good way to do it, while keeping a menu icon in it. First, use the following

```
sudo aptitude install simutrans
```

so that you get all of the files for simutrans. next, download the zip file, and then open a root nautilus using alt>f2, then type

```
gksu nautilus /home/<username>/
```

copy the zip file from where it's downloaded to /usr/share/games/ and the zip file should make a subfolder called simutrans (or maybe simutrans(2))

If it makes a simutrans(2), just copy what is in simutrans(2) into the original

Next, open a terminal in root mode, by using alt>f2, then typing

```
gksu gnome-terminal
```

Use the following command to delete the executable from /usr/games and make a symbolic link to the newer executable.

```
cd /usr/games && remove simutrans && ln -s /usr/share/games/simutrans/simutrans ./simutrans
```

Now, whenever you want to install a new nightly, extract the new files into /usr/share/games like in the previous steps

---

