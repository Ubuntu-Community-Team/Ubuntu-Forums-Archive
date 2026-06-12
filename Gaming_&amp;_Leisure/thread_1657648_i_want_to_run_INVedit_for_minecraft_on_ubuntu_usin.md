---
title: "i want to run INVedit for minecraft on ubuntu using mono, how do i do this?"
date: 2011-01-01
forum: Gaming &amp; Leisure
---

### Post by acornty on 2011-01-01
so I've compiled mono from source and i have it installed and whatnot. my question is how do i now use mono? I'd like to use it for a tool called INVedit that uses .net framwork. wine can't run it because of the .net framework. can anyone help me? 

P.S: I know mono is the only way because that's what ubuntu users have said online on other forums.

---

### Post by Nytram on 2011-01-01
Mono runs in the background just like the Java JRE.

Do you need to compile INVedit from source? If that's the case you'll need Mono Develop (or is there a native Linux version)

---

### Post by acornty on 2011-01-01
> **Nytram said:**
> Mono runs in the background just like the Java JRE.

Do you need to compile INVedit from source? If that's the case you'll need Mono Develop (or is there a native Linux version)
well i have the windoes .exe file of INVedit. i was told online by other minecraft gamers that i could run it with mono. I'm pretty sure there aren't any linux versions as of now.

---

### Post by Nytram on 2011-01-01
have you tried running the exe in wine after installing mono

---

### Post by acornty on 2011-01-01
> **Nytram said:**
> have you tried running the exe in wine after installing mono


yep, gives me this error ```
The file '/home/tyler/Desktop/INVedit/INVedit.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.
```

---

### Post by Nytram on 2011-01-01
to make it executable, open the folder in nautilus, right click on the file, properties, permission tab, and click the executable box

---

### Post by acornty on 2011-01-01
ok, i did that, now when i open it, it says opening INVedit, but then nothing happens

---

### Post by Nytram on 2011-01-01
you could try running it from the terminal, sometimes the error messages are helpful

> 
wine /home/tyler/Desktop/INVedit/INVedit.exe


EDIT this might work in a terminal:

> 
mono /home/tyler/Desktop/INVedit/INVedit.exe


---

### Post by acornty on 2011-01-01
the mono one worked! thank you!!

---

### Post by Nytram on 2011-01-01
youre welcome got there eventually :)

---

### Post by g123386761 on 2011-03-12
OMG THANK YOU! I HAVE BEEN WANTING TO EDIT MY MINECRAFT INVENTORY FOR FO-EVAH!:grin:

---

### Post by Cam! on 2011-03-12
If you want unlimited objects, much like every other person who uses INVedit, just use Zombe's mod.

---

### Post by poco377 on 2012-02-16
i am having the same problem, but i'm trying to run NBTedit. i tried your code, (i edited some of it though).   but it isn't working.

---

### Post by BeRoot ReBoot on 2012-02-16
I'm using mcplayeredit currently, it's terminal-based and much more powerful than other editors I've tried.

---

### Post by directhex on 2012-02-17
> **poco377 said:**
> i am having the same problem, but i'm trying to run NBTedit. i tried your code, (i edited some of it though).   but it isn't working.

Seems to run fine here? What are you trying to do, what is it doing, and what are you expecting it to do?

---

### Post by donkyhotay on 2012-02-17
I'm glad we were able to help you get this going but for future reference if you need help with using a windows program on linux with wine (game or not) you are more likely to get a useful response if you post in the [ubuntu wine sub-forum](http://ubuntuforums.org/forumdisplay.php?f=313). Also don't forget to mark this thread as 'solved'.

---

