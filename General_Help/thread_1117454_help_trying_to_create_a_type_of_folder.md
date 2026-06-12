---
title: "help trying to create a type of folder"
date: 2009-04-06
forum: General Help
---

### Post by brandon88tube on 2009-04-06
Note: Sorry, this may be confusing as I am having a hard time trying to word what it is I exactly want to do so please bear with me. If you need any further information or don't quite understand please say so and I will try to rephrase/reword it the best I can.

I'm trying to create a folder that either acts similar to /dev/null or /tmp. I would have gone with a "ln -s /dev/null folder",but that doesn't work as the file needs to create itself and to read from it or at least think it read from it. Essentially, I need to make a folder that will either make a temp file and delete itself right away or have it sent to something like /dev/null where it thinks it is reading from the file.

---

### Post by Bakon Jarser on 2009-04-06
It seems like what you want is a symlink to /dev/null

[http://www.ss64.com/bash/symlink.html](http://www.ss64.com/bash/symlink.html)

---

### Post by Hospadar on 2009-04-06
Are you writing a program or script that generates temporary files?  Why not just put them in /tmp?
Alternatively, if you're writing you're own scripts, why not just delet your own files when you're done with them?

More info on exactly what is making and using these files would be helpful

---

### Post by mb_webguy on 2009-04-06
There's a pretty big difference between /dev/null and /tmp.  I really don't know exactly what you're asking, but...  If you need something that acts like /dev/null (which it sounds like you do), why can't you just use /dev/null?

---

### Post by brandon88tube on 2009-04-06
Well I am not writing my own script. I'm trying to stop unwanted files from being created when I use flash. Doing a symlink to /dev/null doesn't work as the players need to do something with the file. I can, on the other hand, delete the file right after its created and it will still work. That is why I thought of something maybe similar to /tmp ,but that only deletes files when the computer shuts down.

---

### Post by Bakon Jarser on 2009-04-06
Every post I have read has either made the folder read only or symlinked to dev/null.  I was considering this solution myself.  What problmes do you run into when you symlink to /dev/null?

Edit:  Here's a link to this in the fedora forums.  Nobody seems to have any trouble with it.
[http://forums.fedoraforum.org/showthread.php?t=203321](http://forums.fedoraforum.org/showthread.php?t=203321)

---

### Post by brandon88tube on 2009-04-06
> **Bakon Jarser said:**
> Every post I have read has either made the folder read only or symlinked to dev/null.  I was considering this solution myself.  What problmes do you run into when you symlink to /dev/null?

Edit:  Here's a link to this in the fedora forums.  Nobody seems to have any trouble with it.
[http://forums.fedoraforum.org/showthread.php?t=203321](http://forums.fedoraforum.org/showthread.php?t=203321)

Well, in the past /dev/null hasn't worked for me. Veoh, Myspace etc. would only play the loading animation and never load the video. My solution was to symlink these folders to my firefox cache folder, which deleted itself whenever I closed firefox. I really don't like that as a solution and I tried changing the permissions on the folders to access only and it works for some players, but ones such as imeem don't work and never load. So I have been trying to come up with a better solution to these.

---

### Post by Bakon Jarser on 2009-04-06
I wonder if someone has written a firefox add on that deletes these cookies when firefox is closed.  You could write a script to launch firefox and then when firefox is closed clear those directories.  Or you could write a script that is always running that clears it out at certain time intervals.  Maybe you could even write a script that monitors the folder for changes and deletes all files shortly after they are written.

Edit:  Firefox add-on  [https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)

---

### Post by brandon88tube on 2009-04-06
Truthfully I don't like the idea of Firefox having control over folders and files on my system.

---

