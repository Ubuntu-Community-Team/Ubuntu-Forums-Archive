---
title: "Unreal tournament 2004 problems"
date: 2008-03-01
forum: Gaming &amp; Leisure
---

### Post by VinceYoungXpress on 2008-03-01
Hi I recently tried to install unreal tournament 2004.  I followed this guide for the installation:  

[http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd)

When I try to run ut2004 this error comes up in terminal
```

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
WARNING: ALC_EXT_capture is subject to change!
Either GL_EXT_bgra or glDrawRangeElements not supported- bailing out.
```

Does anyone know how to fix this?

---

### Post by FrozenFox on 2008-03-01
I suspect your video drivers aren't properly installed.

In the terminal, what does glxinfo | grep direct  give you?

Also, what video card are you using?

---

### Post by VinceYoungXpress on 2008-03-01
```
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

That is what I get when I put that in terminal.  My graphics card is an An ATI radeon xpress 200m.

---

### Post by VinceYoungXpress on 2008-03-01
I just noticed that I was using the wrong guide I should have been using the 64bit one.  However, when I followed those instructions I still came up with an error message when I tried to run unreal tournament 2004.  
```

./ut2004-bin-linux-amd64: 1: cannot create &#65533;R@@&#65533;&#65533;@@@@@@@&#65533;&#65533;@@@@&#65533;: Permission denied
./ut2004-bin-linux-amd64: 1: ELF: not found
./ut2004-bin-linux-amd64: 2: Syntax error: ")" unexpected
```

---

### Post by FrozenFox on 2008-03-01
Indeed, no direct rendering = video drivers are not installed correctly or at all.

However, i'm not sure if glxinfo will work correctly w/ ati cards, so try checking the top of fglrxinfo (i think that was the command) for rendering stuff. mesa indirect = not correctly loaded driver, it should be ati. It will most likely say something similar. In which case, I'd like to ask how you installed the drivers and from such refer you to a different means of installing.

As for the error from the 64 bit deal, I'm not sure if it's meant to be like that, but a lot of it is showing up as jibberish letters for me. 

That said, I don't think this info will help you, but I'll throw it out in case you want to try anyway if/after your drivers are correctly set up for your video card.

However, permission denied usually means (obviously) your permissions are wrong on the file. sudo chmod 777 -R ~/ut2004 (assuming ut is installed in /home/yourname/ut2004) from within the folder via cd (folder). or a+x the binary itself instead of 777 on the whole folder.

The syntax deal is often because a script is told to be run by sh when it should be run by bash. The file you're dealing with seems to be a binary, but it's possible the issue is the same.. this is usually fixed by opening the script in question and changing the first line from #!/bin/sh to #!/bin/bash.

---

### Post by SandmanXC on 2008-04-05
I have the same problem as VinceYoungXpress . I have followed the guide [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
I have an ATI Radeon x1100, and the output is exactly the same.

---

### Post by Lok! on 2008-12-30
I get the same output:

"./ut2004-bin-linux-amd64: 1: cannot create &#65533;R@@&#65533;&#65533;@@@@@@@&#65533;&#65533;@@@@&#65533;: Permission denied
./ut2004-bin-linux-amd64: 1: ELF: not found
./ut2004-bin-linux-amd64: 2: Syntax error: ")" unexpected"

I tried changing the bin file to #!/bin/bash and now i get this output:
/usr/local/bin/ut2004: line 49: /usr/local/games/ut2004/System/ut2004-bin-linux-amd64: cannot execute binary file
/usr/local/bin/ut2004: line 49: /usr/local/games/ut2004/System/ut2004-bin-linux-amd64: Success

The entire ut2004 directory is owned by me and /usr/local/games/ut2004/System/ut2004-bin-linux-amd64 is executable so i am lost.  I looked at the file to see if it had a place i should try to change so bash would run it but it looks very different than the other bin file i edited.

Any ideas?

---

### Post by noerrorsfound on 2008-12-31
What about
```
bash ./ut2004-bin-linux-amd64
```

---

### Post by Lok! on 2008-12-31
it is running!!! finally!!  I found out that i had installed 32bit ubuntu on my 64bit platform...oops.  Followed the ubuntu gamers tutorial, used synaptic to get some libraries that i didnt have and now it is up an running.

---

