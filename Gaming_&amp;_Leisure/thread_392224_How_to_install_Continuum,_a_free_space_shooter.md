---
title: "How to install Continuum, a free space shooter"
date: 2007-03-24
forum: Gaming &amp; Leisure
---

### Post by zeroblitzt on 2007-03-24
What is Continuum, you ask?

Well, have you ever imagined playing multiplayer asteroids?  You're going at it with people all across the world, in various "zones", where gameplay can range from free-for-all kill everyone you see, to soccer, to flagging events, (theres even a Star Wars themed zone called Death Star Battle).


Installing it on Windows is easy enough, you just need to follow some graphical installer. For us Linux users, its not fun at all, and it requires compiling a custom version of WINE.


[http://wine.getcontinuum.com/](http://wine.getcontinuum.com/) - this is what I base the guide off of. There is an option to try and get it running with an existing installation of WINE, but I never got that to work. So instead, we have to patch WINE, then make/install it.

*Note: This will not affect Wine in any harmful way. It actually adds a feature that Continuum needs to run.

**Retrieve needed downloads**
```
http://www.winehq.com/
http://www.getcontinuum.com/

```
Download the source package of Wine. Then download the Windows version of Continuum. During this step you can also extract both, each to new, different directories.

**Remove any previous Wine installations**
```
sudo apt-get remove wine
```
We need to remove previous configurations, as they would interfere with us installing a newer version ourselves.

**In your Wine directory...**
In the directory you created before when extracting Wine, create a new file called "cont.diff" (name really doesn't matter, just remember it for later). Open the new file in a text editor of your choice and paste this:

```
diff --git a/dlls/kernel32/process.c b/dlls/kernel32/process.c
index 33f9ee1..d50cb7d 100644
--- a/dlls/kernel32/process.c
+++ b/dlls/kernel32/process.c
@@ -2460,6 +2464,7 @@ HANDLE WINAPI OpenProcess( DWORD access,
     OBJECT_ATTRIBUTES   attr;
     CLIENT_ID           cid;
 
+if (access & PROCESS_VM_WRITE) return NULL;
     cid.UniqueProcess = (HANDLE)id;
     cid.UniqueThread = 0; /* FIXME ? */
```
Save it and quit.

**Open a terminal...**
Open a terminal and type:
```
cat cont.diff | patch -p1 
```
Of course, replace cont.diff with whatever you named the file.

Alright, now Wine is patched (unless of course you received some sort of error message. If so... tell me, but I've never experienced problems).

Now it's time to configure and make.

```
./configure
```
```
make depend && make
```

When its done make-ing, you can type:
```
sudo make install
```

And hopefully you'll have a fresh, new Wine capable of playing Continuum.


Now, just open the Continuum EXE you downloaded before, open it in Wine. You'll be able to install it, but its still not playable, theres one last step you must go through.

**winecfg time!**
at a terminal type
```
winecfg
```
to start the wine configuration editor.

Click the "Drives" tab, and click "Show Advanced". Now click the "manually assign" radio button. In the serial # field, put in some number that is greater than 2000. You'll need to do this as Continuum uses this number as an identifier of sorts for all clients, and if you do not set this, you may see messages that you were banned from a zone. 

Alright, so now you'll be able to run Continuum. You should go into options and make sure that in the "graphics" tab, your color depth is the same as your X session. Now you'll be able to join zones. You can click  the "Zones" button to download new zones. One that you may want to check out is PSS Omega Fire, a friend of mine and I run that, and we're always looking for fresh faces. Also, SSCU Trench Wars is the biggest, and usually is appealing to new players.


Alright, this was my first guide, so hopefully it worked out great for everyone. If not, post here and I'll do my best to field the questions!

---

