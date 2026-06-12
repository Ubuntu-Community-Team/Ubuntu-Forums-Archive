---
title: "Can anyone help a newbie with some command line kung fu?"
date: 2009-02-25
forum: General Help
---

### Post by elanning on 2009-02-25
Greetings,

Just trying to get my feet wet working with the shell and with creating custom commands.

Very simply, I found this post online about a little trick to use mplayer to play an .avi file in the console.  The command is this:

     ```
mplayer -vo caca filename.avi
```

so I created a file, named it "shellvid" and in the file i put just one line:
     ```
mplayer -vo caca
```

Then I made it exacutable by:

     ```
sudo chmod +rx shellvid 
```

Basically what I want to end up with, is a command where I can just type:

     ```
shellvid filename.avi
```

instead of typing the whole command with arguments each time.  But I must be missing something, because it doesnt work heh.  

Im thinking its because there is something I have to put in that shellvid file to tell it to use the next thing the user enters as the filename?

Suggestions?  
Thanks!

---

### Post by adult swim on 2009-02-25
it seems to me that you want to create an alias to do what you were trying to do.  
you could run ```
alias shellvid='mplayer -vo caca'
``` and then do ```
shellvid filename.avi
```  
see this page to learn more about alias's and how to make them stick if you want to
[http://www.ubuntuhacker.com/index.php/2007/06/18/adding-terminal-aliases-to-ubuntu/](http://www.ubuntuhacker.com/index.php/2007/06/18/adding-terminal-aliases-to-ubuntu/)

---

### Post by elanning on 2009-02-25
Thanks! Worked like a charm.

---

### Post by adult swim on 2009-02-25
are you trying to play videos in ASCII?

---

### Post by KeyserSoze93 on 2009-02-25
Yes, aliases are the way to go for simple commands.

If you want to create a shell script wrapper for any future stuff, just do what you did, but follow the command in the script with $1 (that's dollar one), because that will pick up the file you called the script on.

---

### Post by anaconda on 2009-02-25
wow.. that was fun. Video in ASCII  Never seen that before.

Just like matrix...

---

### Post by anaconda on 2009-02-25
> **KeyserSoze93 said:**
> Yes, aliases are the way to go for simple commands.

If you want to create a shell script wrapper for any future stuff, just do what you did, but follow the command in the script with $1 (that's dollar one), because that will pick up the file you called the script on.

yep, and then you need to use ./ in front of the shellvid..

./shellvid video.avi

if you dont want to use the ./ you can eg. copy the script to /usr/bin so that the shell will find your script even without specifing that search from current directory..

---

