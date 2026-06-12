---
title: "Sauerbraten Game question"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by waldick on 2006-06-08
total newbie question here...

downloaded and extracted sauerbraten...

how do you install the game ?

thanks,

j

---

### Post by charlieg on 2006-06-09
You don't need to install it IIRC; just cd into the directory and there should be a binary to run.  I'm on a Windows PC right now so can't be specific, sorry.

---

### Post by FredB on 2006-06-09
[QUOTE=waldick]total newbie question here...

downloaded and extracted sauerbraten...

how do you install the game ?

thanks,

j[/QUOTE]

No need to install it ;)

Launch a Konsole and in it type :

```

cd name of directory you downloaded the game/sauerbraten
./sauerbraten_unix &
```

Good play \\:D/

---

### Post by waldick on 2006-06-10
thank you,

i'll do that....


j

---

### Post by FredB on 2006-06-10
[QUOTE=waldick]thank you,

i'll do that....


j[/QUOTE]

You're welcome. Good play.

/me goes back to its angband saved game... Too geeky ? ;)

---

### Post by kybishop on 2006-06-19
I got this error when i tried

```
root@kyle:~/Desktop/sauerbraten# ./sauerbraten_unix
./bin_unix/linux_client: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

```

---

### Post by Gustav on 2006-06-20
Type this in a terminal - 'sudo apt-get install libsdl-image1.2'. Then try again.

---

### Post by MetalMusicAddict on 2006-06-26
[QUOTE=FredB]No need to install it ;)

Launch a Konsole and in it type :

```

cd name of directory you downloaded the game/sauerbraten
./sauerbraten_unix &
```

Good play \\:D/[/QUOTE]
This works and all, cd'ing into the directory but I need to create a launcher so It needs to be one string. So if I:```
/home/atm/.sauerbraten/sauerbraten_unix
```
I get this:
```
/home/atm/.sauerbraten/sauerbraten_unix: line 39: /home/atm/bin_unix/linux_client: No such file or directory
```

Line 39 from the script is:
```
cd ${CUBE_DIR}
**exec ${CUBE_DIR}/bin_unix/${MACHINE_PREFIX}${SYSTEM_PREFIX}client $***
```
Im just trying to make a desktop launcher.

---

### Post by seth0x2b on 2006-06-26
Well if ```
cd name of directory you downloaded the game/sauerbraten
./sauerbraten_unix &
``` works for you, then to create a launcher you can use
```
sh -c "cd <game directory>/sauerbraten && ./sauerbraten_unix & "
``` 
Cheers

---

### Post by MetalMusicAddict on 2006-06-26
Thanx so much sir. Whats the **-c** and **&&** for? I think I get the rest.

---

### Post by MetalMusicAddict on 2006-06-26
OK. So if this is my command:
```
sh -c "cd /home/atm/.sauerbraten && ./sauerbraten_unix &"
```

Where does a argument go? I need to set a res.

Like this ?
```
sh -c "cd /home/atm/.sauerbraten && ./sauerbraten_unix & -w1920 -h1200"
```
Or...
```
sh -c "cd /home/atm/.sauerbraten && ./sauerbraten_unix &" -w1920 -h1200
```
Or... Can it be added to a "autoexec.cfg" file? Where should it be created? Im still tryin to get this game figured out.

OK. I got it. I removed the **&** and the arguments work.
```
sh -c "cd /home/atm/.sauerbraten && ./sauerbraten_unix -w1920 -h1200"
```

---

### Post by seth0x2b on 2006-06-26
Since you don't run the game from the command line, the "&" has no use anyway.Glad it worked for you.

Cheers

---

### Post by evaderus on 2006-08-06
I tried installing using ```
./sauerbraten_unix &
``` and I got ```
evad@ubuntu:~/sauerbraten$ ./sauerbraten_unix &
[1] 7117
evad@ubuntu:~/sauerbraten$ init: sdl
init: enet
init: video: mode
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Unable to create OpenGL screen: Couldn't find matching GLX visual

```

---

