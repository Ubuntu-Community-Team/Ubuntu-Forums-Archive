---
title: "how-to use the classic controller for gaming emulators"
date: 2008-01-31
forum: Gaming &amp; Leisure
---

### Post by onesojourner on 2008-01-31
Step 1: download xwii from [here.]("http://www.resplect.com/xwii/")

Step 2: right click on the file click extract here. Copy the file into your home directory. Rename the file to ```
xwii
```.


Step 3: Open a terminal window and
```
sudo apt-get install build-essential libbluetooth-dev libxtst-dev
```

Step 4: Again in the terminal window:
```
sudo apt-get install libsdl1.2-dev
```

Step 5: In terminal:
```
cd xwii
```

Step 6: In terminal:
```
make
```
If there are any errors you are most likely missing some dependencies. Post them here and we can try to resolve them.

Step 7: Your terminal should still be in the xwii folder. If it isn't 
```
cd xwii
```

Step 8: run it. There are several profiles to choose from. I am using the classic controller for this example. You need to have your bluetooth adapter plugged in and the wiimote in front of you. As soon as you hit enter after this command you need to press the 1 & 2 button on the main wii remote to connect it.
```
./xwii profiles/classic.xwii
```

Hopefully that works. put a cursor in a text field you should get a response. You will need to map your buttons to those of the wiimote with what ever emulator you are using, In zsnes you have to go to config>input and then click on a and hit the a button on your classic controller. Up down left right and start should all be set already.

Step 9: Creat a custom launcher so you don't have to use the terminal every time. EDIT: I have had issues with this. I think a bash script will have to be written for this.

until then just use this code to run it in the terminal:
```
cd ~/xwii && ./xwii profiles/classic.xwii
```

thanks to fatalglory and para.

---

### Post by gohanssjn on 2008-06-16
Hmm, may want to try this later this week.

Any success stories?

---

### Post by grossaffe on 2008-06-16
how well does xwii work compared to cwiid?

---

### Post by SwitchBlade on 2008-06-26
I've used that method and it works fine.  Been using the Guitar hero guitar to play Frets On Fire.

---

### Post by MrSootentai on 2008-07-09
I keep getting an error, is there anyway to fix this??
> make[1]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/src'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -shared -lm -lbluetooth release-i486-linux-gnu/classic.o release-i486-linux-gnu/dynamics.o release-i486-linux-gnu/events.o release-i486-linux-gnu/io.o release-i486-linux-gnu/io_nix.o release-i486-linux-gnu/ir.o release-i486-linux-gnu/nunchuk.o release-i486-linux-gnu/guitar_hero_3.o release-i486-linux-gnu/wiiuse.o -o ./release-i486-linux-gnu/libwiiuse.so
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/src'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -L../src/release-i486-linux-gnu -lm -lwiiuse release-i486-linux-gnu/example.o -o ./release-i486-linux-gnu/wiiuse-example
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example-sdl'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -I../src/ -I/usr/include/SDL -c sdl.c -o release-i486-linux-gnu/sdl.o
sdl.c:37:21: error: GL/glut.h: No such file or directory
sdl.c: In function &#8216;display&#8217;:
sdl.c:257: warning: implicit declaration of function &#8216;glutSolidTeapot&#8217;
make[2]: *** [release-i486-linux-gnu/sdl.o] Error 1
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example-sdl'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12'
make: *** [libwiiuse.so] Error 2


---

### Post by signifer123 on 2008-07-10
> **MrSootentai said:**
> I keep getting an error, is there anyway to fix this??

do you have the required development files installed?

the sdl developemnt and opengl development libraries are needed for the sdl samples, i guess libglut3 is as well

---

### Post by MrSootentai on 2008-07-10
Yes I followed the instructions exactly, it just tells me that everything is already updated/installed.
What else can i do??

---

### Post by scolbeck on 2008-07-11
> **MrSootentai said:**
> Yes I followed the instructions exactly, it just tells me that everything is already updated/installed.
What else can i do??

Try
```
apt-get install freeglut3-dev
```

---

### Post by MrSootentai on 2008-07-11
Thank you so much that actually seemed to help. But not I got another error message...
"cannot find -lwiiuse"
How would I install that??
> make[1]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/src'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -shared -lm -lbluetooth release-i486-linux-gnu/classic.o release-i486-linux-gnu/dynamics.o release-i486-linux-gnu/events.o release-i486-linux-gnu/io.o release-i486-linux-gnu/io_nix.o release-i486-linux-gnu/ir.o release-i486-linux-gnu/nunchuk.o release-i486-linux-gnu/guitar_hero_3.o release-i486-linux-gnu/wiiuse.o -o ./release-i486-linux-gnu/libwiiuse.so
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/src'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -L../src/release-i486-linux-gnu -lm -lwiiuse release-i486-linux-gnu/example.o -o ./release-i486-linux-gnu/wiiuse-example
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example'
make[2]: Entering directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example-sdl'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -I../src/ -I/usr/include/SDL -c sdl.c -o release-i486-linux-gnu/sdl.o
gcc -Wall -pipe -fPIC -funroll-loops -O2 -L../src/release-i486-linux-gnu -lm -lGL -lGLU -lglut -lSDL -lbluetooth -lwiiuse release-i486-linux-gnu/sdl.o -o ./release-i486-linux-gnu/wiiuse-sdl
make[2]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12/example-sdl'
make[1]: Leaving directory `/home/greg/Desktop/XWii_2.5_source/wiiuse_v0.12'
ln wiiuse_v0.12/src/release-i486-linux-gnu/libwiiuse.so ./libwiiuse.so
g++ xinterpret.cpp -c
g++ actionset.cpp -c -I ./wiiuse_v0.12/src
g++ main.o xinterpret.o actionset.o -o xwii -lbluetooth -ldl -lXtst -lwiiuse
/usr/bin/ld: cannot find -lwiiuse
collect2: ld returned 1 exit status
make: *** [xwii] Error 1
greg@gregsNotebook:~/Desktop/XWii_2.5_source$ sudo make install
make: *** No rule to make target `install'.  Stop.


---

### Post by MrSootentai on 2008-07-12
After some more busting my head, I just removed the downloaded files and redownload it all. After that everything seemed to work perfectly. Thank you for all the help.

---

### Post by waltzie on 2008-08-29
to solve the error: GL/glut.h: No such file or directory

just do this 

```
sudo apt-get install freeglut3 freeglut3-dbg freeglut3-dev libglu1-mesa libglu1-mesa-dev libglui2c2 libglui-dev libglut3 libglut3-dev
```

CiauZ

WaltZie :popcorn:

---

### Post by umicko on 2009-02-13
for others out there.

yes

sudo apt-get install freeglut3-dev

is required

and running

sudo make

will fix the problem, it tried to create module in /usr/lib/ so sudo is required.

cheers.

---

### Post by rfLarke on 2009-08-08
Okay I know we're a good six months old'd in this topic but I can't escape this problem:

Every single time I attempt to "Make" Xwii, I get an error:

```
<myname>@<box>:~$ cd ~/Desktop/xwii
<myname>@<box>:~/Desktop/xwii$ make
make[1]: Entering directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12'
make[2]: Entering directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/src'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -shared -lm -lbluetooth release-i486-linux-gnu/classic.o release-i486-linux-gnu/dynamics.o release-i486-linux-gnu/events.o release-i486-linux-gnu/io.o release-i486-linux-gnu/io_nix.o release-i486-linux-gnu/ir.o release-i486-linux-gnu/nunchuk.o release-i486-linux-gnu/guitar_hero_3.o release-i486-linux-gnu/wiiuse.o -o ./release-i486-linux-gnu/libwiiuse.so
make[2]: Leaving directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/src'
make[2]: Entering directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/example'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -L../src/release-i486-linux-gnu -lm -lwiiuse release-i486-linux-gnu/example.o -o ./release-i486-linux-gnu/wiiuse-example
make[2]: Leaving directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/example'
make[2]: Entering directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/example-sdl'
gcc -Wall -pipe -fPIC -funroll-loops -O2 -I../src/ -I/usr/include/SDL -c sdl.c -o release-i486-linux-gnu/sdl.o
sdl.c:38:17: error: SDL.h: No such file or directory
sdl.c: In function ‘display’:
sdl.c:260: warning: implicit declaration of function ‘SDL_GL_SwapBuffers’
sdl.c: In function ‘resize_window’:
sdl.c:296: warning: implicit declaration of function ‘SDL_SetVideoMode’
sdl.c:296: error: ‘SDL_RESIZABLE’ undeclared (first use in this function)
sdl.c:296: error: (Each undeclared identifier is reported only once
sdl.c:296: error: for each function it appears in.)
sdl.c:296: error: ‘SDL_OPENGL’ undeclared (first use in this function)
sdl.c: In function ‘main’:
sdl.c:357: warning: implicit declaration of function ‘SDL_Init’
sdl.c:357: error: ‘SDL_INIT_VIDEO’ undeclared (first use in this function)
sdl.c:358: warning: implicit declaration of function ‘SDL_GetError’
sdl.c:358: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
sdl.c:362: warning: implicit declaration of function ‘SDL_WM_SetCaption’
sdl.c:364: warning: implicit declaration of function ‘SDL_GL_SetAttribute’
sdl.c:364: error: ‘SDL_GL_DOUBLEBUFFER’ undeclared (first use in this function)
sdl.c:365: error: ‘SDL_GL_DEPTH_SIZE’ undeclared (first use in this function)
sdl.c:370: error: ‘SDL_RESIZABLE’ undeclared (first use in this function)
sdl.c:370: error: ‘SDL_OPENGL’ undeclared (first use in this function)
sdl.c:395: error: ‘SDL_Event’ undeclared (first use in this function)
sdl.c:395: error: expected ‘;’ before ‘event’
sdl.c:397: warning: implicit declaration of function ‘SDL_PollEvent’
sdl.c:397: error: ‘event’ undeclared (first use in this function)
sdl.c:399: error: ‘SDL_VIDEORESIZE’ undeclared (first use in this function)
sdl.c:405: error: ‘SDL_QUIT’ undeclared (first use in this function)
sdl.c:408: warning: implicit declaration of function ‘SDL_Quit’
make[2]: *** [release-i486-linux-gnu/sdl.o] Error 1
make[2]: Leaving directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12/example-sdl'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/<myname>/Desktop/xwii/wiiuse_v0.12'
make: *** [libwiiuse.so] Error 2
<myname>@<box>:~/Desktop/xwii$ 

```

Any help greatly appreciated

---

### Post by FreezWay on 2009-09-06
```
Which profile would you like to use (pick a number)? 15
./xwii "profiles/Tilt Mouse.xwii"
Press 1 + 2 to put the Wiimote in discoverable mode.

[INFO] Found 1 bluetooth device(s).
[INFO] Found wiimote (00:1A:E9:4D:CC:FD) [id 1].
connect() output sock: Invalid argument
Failed to connect to any wiimote.
wiiuse v0.12 loaded.
  By: Michael Laforest <thepara[at]gmail{dot}com>
  http://wiiuse.net  http://wiiuse.sf.net

```

any ideas?

---

### Post by acomputerdood on 2010-04-17
did you ever solve this?  i'm having the same problems:

```
XWii_2.8_source # ./xwii profiles/mythtv.xwii 
wiiuse v0.12 loaded.
  By: Michael Laforest <thepara[at]gmail{dot}com>
  [http://wiiuse.net](http://wiiuse.net)  [http://wiiuse.sf.net](http://wiiuse.sf.net)
Hold 1 + 2 to put the Wii Remote in discoverable mode.
[INFO] Found 1 bluetooth device(s).
[INFO] Found wiimote (00:17:AB:31:D0:56) [id 1].
connect() output sock: Invalid argument
Failed to connect to any wiimote.
```

---

### Post by acomputerdood on 2010-04-17
ahh, this worked for me:

[http://old.nabble.com/wiiuse-and-csound-p25463592.html](http://old.nabble.com/wiiuse-and-csound-p25463592.html)


```
[INFO] Found 1 bluetooth device(s). 
[INFO] Found wiimote (00:1F:32:F1:8D:0C) [id 1]. 
connect() output sock: Invalid argument 
Failed to connect to any wiimote. 

Michael LaForest suggests modifing the source of libwiiuse in the 
following way: 

memset(&addr, 0, sizeof (addr)); //is missing in the line 174 of io_nix.c 
```

---

### Post by kingcrim on 2011-01-30
I had this working earlier today but the battery on my wiimote died.  So I charged it up and tried running this and now it says permission denied in the terminal when I do ./profiles/test.xwii.  I tried rebooting the comp and still the same thing happens.  I am logged in as root so this confuses me.  Can someone help please?

---

### Post by Quadunit404 on 2011-01-30
[IMG]http://tandemgeek.files.wordpress.com/2010/09/threadnecromancyjk7.jpg?w=500&h=375[/IMG]

Don't worry, it's a common noob mistake to revive threads dead for years (or, in this case, 9 or so months ago)

---

### Post by Perfect Storm on 2011-01-30
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)

---

