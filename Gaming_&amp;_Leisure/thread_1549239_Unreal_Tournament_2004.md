---
title: "Unreal Tournament 2004"
date: 2010-08-09
forum: Gaming &amp; Leisure
---

### Post by szaqlon on 2010-08-09
I have installed UT2004 on 32bit Lucid. The game runs great, but as soon as I patch it it will no longer start. I have the 3369-2 patch and copied all of the files over to the ut2004 directory. I don't know what the problem could be. I have been through the posts on this site but can't find anything.

---

### Post by Perfect Storm on 2010-08-09
Download and use the megapack instead. You'll get the latest patch + all the bonus stuff that have been released.

[http://www.gamershell.com/download_11937.shtml](http://www.gamershell.com/download_11937.shtml)

```
tar jxfv ut2004megapack-linux.tar.bz2 
cd UT2004MegaPack
sudo cp -r * /usr/local/games/ut2004
```

---

### Post by szaqlon on 2010-08-12
I get the same problem, nothing happens when I try to run the game. When I put all the folders back that had files overwritten it works fine again. Even if I leave the new folders from the megapack. Don't understand what the problem could be.

---

### Post by rizzeh on 2010-08-12
you'll need to run UT2004 from terminal to see what the problem is. Just type ut2004 in terminal if you have standard install. Check the terminal output for any obvious error messages.

---

### Post by szaqlon on 2010-08-12
It says 
"ut2004: command not found"

---

### Post by rizzeh on 2010-08-13
in that case navigate to ut2004 directory and run the ut2004 executable file.
```
cd /home/ut2004 (change path to your ut2004 installation folder)
./ut2004
```

---

### Post by szaqlon on 2010-08-14
Nothing. I have the game installed in my home directory. Does that make a difference?
Does the game have to be in the default install directory?

---

### Post by rizzeh on 2010-08-14
you can have it installed in home no problems, difference is if the game is installed in default /usr/local/games then all users on your pc can play the game with their own settings.

---

### Post by szaqlon on 2010-08-14
Don't understand then why it works fine until it's patched then will not work at all.

---

### Post by szaqlon on 2010-08-19
So, I take it no one has any idea as to what the problem may be here?

---

### Post by Brebs on 2010-08-20
You're being too vague. Run ut2004 from a terminal, and show the error message. We need more info than "it dern't werk."

---

