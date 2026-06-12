---
title: "quick question..."
date: 2007-04-01
forum: Gaming &amp; Leisure
---

### Post by iPirates on 2007-04-01
I recently installed sauerbraten/cube2 from source.

I start the game by bringing up the terminal, moving to the sauerbraten folder, and typing "./sauerbraten_unix", which tosses me into the game, and I go from there.

I was wondering if i could simplify the game starting process by making an icon to run the game?  I wasn't sure what the command would look like to run the "./sauerbraten_unix" part...

---

### Post by Jussi Kukkonen on 2007-04-01
First try if you can launch the game from anywhere: run */full/path/of/sauerbraten_unix* from e.g. your home dir.

If that works, create a launcher (right click on Desktop), set command to */full/path/of/sauerbraten_unix*.

---

### Post by iPirates on 2007-04-01
It didn't work, and I tried clicking "run in terminal" and it gave me this message...

Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.

There is a 'src' folder in the sauerbraten folder too, so I'm not sure what's wrong (or if that's even a good way to "run" it anyway...)

---

### Post by Jussi Kukkonen on 2007-04-02
No problem, I was just too lazy to write all the options there, just covered the one I thought was probable... By the way, I'm guessing you understood that I meant the real path of the executable when I said */full/path/of/sauerbraten_unix*. It would be easier to know that we're on the same page if you copy your terminal input/ouput here whenever there are problems...

If running */full/path/of/sauerbraten_unix* didn't work, you'll need to write a short script to first change the dir and then run the executable.
> #!/bin/sh
cd /full/path/
./sauerbraten_unix

Save that in a text file (you can save in the same directory the executable is in), let's say */full/path/sb.sh* . 
Make it executable: *chmod +x /full/path/sb.sh*.
Now try running that from your home dir: */full/path/sb.sh*.
If it works, create a launcher that runs that script.

---

### Post by iPirates on 2007-04-04
Well, I managed to solve my problem anyway...
before you posted your last post, I decided to poke around in the "sauerbraten_unix" file, and discovered that I needed to define where the files to run the game were...

SAUER_DIR=

needed to be changed to

SAUER_DIR=~/sauerbraten

Running the sauerbraten_unix file now jumps into the game, so it's workin great!

thanks for the posts!

---

