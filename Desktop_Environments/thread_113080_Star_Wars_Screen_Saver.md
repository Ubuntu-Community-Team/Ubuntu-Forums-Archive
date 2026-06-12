---
title: "Star Wars Screen Saver"
date: 2006-01-05
forum: Desktop Environments
---

### Post by luv2cmwork on 2006-01-05
I'm learning...I hope this will teach me more than one lesson.

I've tried using the Star Wars Screen saver.  This is what it does:

Draws a stream of text slowly scrolling into the distance at an angle, over a star field, like at the beginning of the movie of the same name. Written by Jamie Zawinski and Claudio Matauoka.

I tried writing and saving my own text, for it to use.  I saved the text in my home directory, under my username (I think)

Now, when the text scrolls across the screen, it says:
sh: home/username/filename: Permission denied.

Obviously, it appears to be a permissions error.  I went into file management and clicked on the PROPERTIES of the file and changed it to READ, WRITE and EXECUTE for OTHERS.

Still doesn't work....what else do I need to do? 

Remember, I'm a newbie....be gentle.  But I have gotten this far!!

Thanks!

---

### Post by superm1 on 2006-01-05
Well I believe that screen saver won't take in a text file, but actually any app that will output text to a console.  Instead you might be able to use 'cat /home/username/filename'.  Cat will typically echo text to a console, so it should be usable.

---

