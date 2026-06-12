---
title: "unable to play savage"
date: 2006-09-04
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2006-09-04
I've installed the Linux version of savage
but I can not enter the game
I run the savage shell script but nothing happens
I looked at the permissions and it's executable.
who do I run this game ?

---

### Post by mwolfe on 2006-09-04
what happens when you try to run it?
try typing
savage from the command line, thats assuming you had the option on to put a symlink in your /usr/bin or /usr/local/bin
directory..
if not you need to find executable to run savage and try and run it from the command line. I spent several hours today getting savage working and i think i will post a how to on it later.

---

### Post by MaximB on 2006-09-05
maxim@maxim-home:~/games/Savage$ savage
bash: savage: command not found

---

### Post by almostlinux on 2006-09-05
> **MAXDDARK said:**
> maxim@maxim-home:~/games/Savage$ savage
bash: savage: command not found

try with './savage' in that directory :
```

maxim@maxim-home:~/games/Savage$ ./savage
```

---

### Post by MaximB on 2006-09-05
maxim@maxim-home:~/games/Savage$ ./savage
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libtiff.so.3: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out


what to do now ?

---

### Post by mwolfe on 2006-09-05
try this 
```

sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

```

---

### Post by MaximB on 2006-09-05
thanks
I've managed to enter the game
but I cannot connect to any server
it says that I may need the patch 2.00e
but in the site - it's only for windows.
what can I do ?

---

### Post by mwolfe on 2006-09-05
go to 
[http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=55](http://www.evolvedclan.com/index.php?ind=downloads&op=entry_view&iden=55)

and download SEP-2F.tar.gz

put that in the directory where you installed savage and extract the files (the same way you did the other 2 updates)
and you should be able to connect to servers.

---

### Post by MaximB on 2006-09-05
should I extract those files OVER my existing ones ?

and what file should I run ? graveyard or the original ?

---

### Post by mwolfe on 2006-09-06
yeah overwrite the other files.. i just ran savage..

---

### Post by MaximB on 2006-09-06
thanks - it worked
BUT
the graphics was low so I set the resolution higher and then I got this error :

maxim@maxim-home:~/games/Savage$ ./savage
System_Init()
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x76
  Serial number of failed request:  105
  Current serial number in output stream:  107


now I can't even enter the game to change it
what can I do ? (besides reinstalling and playing with poor graphics)
I have ATI radeon 9800 pro graphic card.

---

### Post by Casey on 2006-09-06
Did you ever install the 2.00 patch (from the thread I posted) before you installed SEP?  I think that could be a major issue.  SEP assumes it's being installed over 2.00.

-- Casey

---

### Post by MaximB on 2006-09-07
first I installed savage
then the patch that came with it
and then I extracted the SEP.

---

### Post by Casey on 2006-09-07
That's odd, savage uses my desktop's resolution (and no option to change this shows up).

Perhaps ask here:
[http://www.notforidiots.com/forum/viewforum.php?f=9](http://www.notforidiots.com/forum/viewforum.php?f=9)

WhiteDwarf from that forum is a linux user with access to the SDK so he knows more about how the program is written than anyone else.

---

### Post by Marsan on 2006-09-09
hello!

I have problem to start this game up. i get this:

```
 marsan@marsan-desktop:/usr/local/games/Savage$ ./savage
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out
```

anyone who can help me with this?

---

### Post by MaximB on 2006-09-11
in terminal write :
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

---

### Post by slowdeath on 2006-09-26
hi, ive tried installing savage, ive searched all the forums i can, i am still getting this error:

```
Traceback (most recent call last):
  File "<string>", line 11, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 362, in doimport
  File "/home/slothy/cvs/src/s2update/builds2update/out1.pyz/wxPython", line 20, in ?
  File "iu.py", line 277, in importHook
  File "iu.py", line 338, in doimport
  File "iu.py", line 184, in getmod
  File "archive.py", line 386, in getmod
  File "iu.py", line 46, in getmod
ImportError: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
There was an error (error 65280 - Unknown error 65280) running the updater!  bailing out
```

thanks

---

### Post by jdunn on 2006-09-26
I'm having a different issue with Savage.  Usually (but, not always) when I exit the game, my mouse freezes with my desktop at game-resolution.  My only solution is to CTRL-ALT-Backspace to restart the X server.

Anyway, if you are having problems with Savage and have tried everything, post a message on  [http://www.notforidiots.com/forum/index.php?sid=5828bcf475e614d304f83fe398f5a93b](http://www.notforidiots.com/forum/index.php?sid=5828bcf475e614d304f83fe398f5a93b) and WhiteDwarf will hopefully have a solution for you.  I think another SEP update will be coming out soon.  As of now, the latest SEP version is 3T.

---

