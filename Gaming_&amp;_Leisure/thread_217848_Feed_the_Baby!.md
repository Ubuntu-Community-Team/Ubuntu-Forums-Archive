---
title: "Feed the Baby!"
date: 2006-07-17
forum: Gaming &amp; Leisure
---

### Post by ballzypeters on 2006-07-17
Ok not trying to repeat too much on other posts. Is there a quick and easy process for getting .run files to install?  Where is the best place to download  the file to and run from?  Is the terminal the tool for best installations?  It's all a bit of a "DOS" type flashback to me!](*,) any of the popular 3d free games(alienarena, tremulous, americas army) would encourage me to learn more!

---

### Post by vem0m on 2006-07-17
linux is mainly 90 console(terminal prompt) and 10% GFX so ur either using the wrong OS or just being lazy :P i think the second as linux u can't go wrong however to use a .run file goto terminal(prompt) ant type "sudo chmod +x nameOfFilehere.run then hit enter then type "./nameOfFilehere.run" and it should start the installer weather Graphical or text based ENJOY!

---

### Post by Fass on 2006-07-17
The "best" place to download the file and run it from is, IMHO, your home directory. You can place your own files elsewhere if you want to, of course, but unless you know what you're doing your home is the most conveniently accessible and safest place to put them.

If you don't want to go into a terminal and start the file by issuing a command like ./binfile.bin, you can double click (or whatever you mouse setting is) it in your GUI filemanager if the file is executable (which you can make it by right clicking it and changing its file permissions). Should you need to run the file as root you can, again, right click it and choose to run it as another user.

As you can see, it's just a whole lot easier to go into a terminal and type, hence why most people choose that route. It's not "DOS" type - it's DOS that was "unix type."

---

### Post by Cure777 on 2006-07-17
Here read this thread [http://www.ubuntuforums.org/showthread.php?t=216980]("http://www.ubuntuforums.org/showthread.php?t=216980"). Read christhemonkeys post, it is the most informative. I too am a Linux n00b, so don't worry about it, I had trouble too :p

---

### Post by firezip on 2006-07-17
What I usually do is save the .run file(Usually a game of some sort) to a particular directory, CHMOD the file permissions, and then usually do these commands in the terminal.

```

cd Directory

- - - - - - - - - - 

Name@Name:~/Downloads$ sudo **./name.run**

```

---

### Post by vem0m on 2006-07-17
yep what i said :P

beat ya too it hehe

---

### Post by ballzypeters on 2006-07-20
Thank you!  It was the permissions settings.  Not so bad!  Now just need to get the games to run?  Terminal as well to launch the bin file or am I in the wrong place here too?

---

### Post by goobers on 2006-07-20
It'd probably just be easier to right click on the file, go to properties then permissions, then check execute for all users, that way, you don't have to use the terminal at all...

---

