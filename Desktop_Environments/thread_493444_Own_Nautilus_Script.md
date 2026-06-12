---
title: "Own Nautilus Script?"
date: 2007-07-05
forum: Desktop Environments
---

### Post by codypumper on 2007-07-05
How could I make a nautilus script, so I can right click on a video and convert according to these instructions:
[URL="http://ubuntuforums.org/showthread.php?t=463500"]
http://ubuntuforums.org/showthread.php?t=463500[/URL] or
```
ffmpeg -i 'Input.avi' -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 Output.mp4
```

---

### Post by kevinlyfellow on 2007-07-06
```
#!/bin/bash

cd $NAUTILUS_SCRIPT_CURRENT_URI
mogrify -rotate 270 $1
```

Here is a small script I wrote to rotate an image CounterClockWise.  Basically, the first line is for the shell you want to use, in your case, it can be just about anything.  The second brings you to the directory you are issuing the command in.  The third one is for the command.  $1 is the file to act on (in my case the image).  The file needs to be in ~/.gnome2/nautilus-scripts and needs to be executable.  Also a custom icon is handy!

I think yours would look something like

```
#!/bin/bash

cd $NAUTILUS_SCRIPT_CURRENT_URI
ffmpeg -i $1 -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 Output.mp4
```

But that will cause the output to be always called Output.mp4.  You can do this however,

```
#!/bin/bash

cd $NAUTILUS_SCRIPT_CURRENT_URI
ffmpeg -i $1 -f mp4 -vcodec xvid -qmin 5 -qmax 6 -bufsize 4096 -g 300 -acodec aac -ac 2 -ar 44100 -ab 128 -s 240x176 "$1".mp4
```

Let me know if it works

---

### Post by codypumper on 2007-07-06
Thanks so much! I tried, but didn't get anywhere  :D
Now it works great.

---

### Post by kevinlyfellow on 2007-07-06
Yeah there are a few tricks that require special knowledge.  I'm not sure where I even learned about nautilus scripts, but [here is a website (about.com)]("http://linux.about.com/library/gnome/blgnome6n13a.htm") that has a list of the environmental variables used with nautilus scripting.  The rest is just bash scripting.  [Beginner]("http://tldp.org/LDP/Bash-Beginners-Guide/html/Bash-Beginners-Guide.html") [Advanced]("http://tldp.org/LDP/abs/html/")

---

### Post by codypumper on 2007-07-06
Well thank you. I was looking for a site like that. Next time, I should be able to do it myself.

---

