---
title: "GAME OF THE YEAR: 420BLAZEIT installation."
date: 2015-03-26
forum: Gaming &amp; Leisure
---

### Post by ricky-flammia on 2015-03-26
I know that there are probably no threads on this because the solution is simple but I cant seem to figure out how to assemble or extract this game so that it's playable. Here is the link to the download website so that you can get a better understanding of the problem [http://www.gameoftheyear420blazeit.com/](http://www.gameoftheyear420blazeit.com/). Please let me know if anyone has a solution or an idea of how to solve this. Thank you.
Specs: Ubuntu 14.10 x64, AMD A10 7800 CPU, AMD R7 GPU, 8 GB RAM.

---

### Post by oldrocker99 on 2015-03-26
The executable for this game is not set. The quickest way to make it executable is:
```
cd /path/to/GAMEOFTHEYEAR_LINUX/Linux/
chmod + x GAM{TAB}
```
If you just type the first three letters of the filename and hit TAB, the filename will auto-complete in the proper format:
```
GAME\ OF\ THE\ YEAR\ 420BLAZEIT
```
The other way to do it is to open the directory in a file manager, right-click the file and select "Properties." Then click the **Permissions** tab and check "Allow executing file as Program."

That'll do it.

EDIT: By the way, that's a pretty funny website.

---

### Post by ricky-flammia on 2015-03-27
Thanks for the info. When you extract the file you get a folder called Linux. Within that folder you get another folder named GAME OF THE YEAR 420BLAZEIT_Data and a file named GAME OF THE YEAR 420BLAZEIT.x86 which can be set as an executable but doesn't run when I attempt to run it. What am I missing or doing wrong? Thanks again. P.S. I noticed that you're from Norwich, CT. Are you familliar with Waterbury? lol

---

### Post by oldrocker99 on 2015-03-27
Oh, yes, I know Waterbury):P.

Try this:
```
cd /path/to/GAMEOFTHEYEAR_LINUX/Linux
./GAME{TAB}.x86
```
You have to add the .x86, since there is a folder with the same name, and post what the terminal returns.

---

### Post by ricky-flammia on 2015-03-27
It says "No such file or directory" so I attempted to edit it in accordance with its file path on my system and I got the same response. The file path is  home/richard/downloads/GAMEOFTHEYEAR_LINUX/Linux/GAME OF THE YEAR 420BLAZEIT.x86. A folder named GAME OF THE YEAR 420BLAZEIT_Data is also contained at the end of the same file directory.

---

### Post by oldrocker99 on 2015-03-28
Try this:```
sh "home/richard/downloads/GAMEOFTHEYEAR_LINUX/Linux/GAME OF THE YEAR 420BLAZEIT.x86"
```

The path needs quotes, since it has spaces in it. Just like Windows, you have to put paths or filenames with spaces in quotes. "sh is a command language interpreter that executes commands read from a command line string, the standard input, or a specified file." It will ignore the folder.

That should do it.

---

### Post by ricky-flammia on 2015-03-28
It didn't launch so I tried putting "sudo" in front of it and it still didn't work. It says "Can't open". At least I learned something new about the terminal though. Thanks for your patience.

---

### Post by oldrocker99 on 2015-03-29
Have you tried cd-ing to the directory that contains the executable? Then```
./"GAME OF THE YEAR 420BLAZEIT.x86"
```
Please post results.

EDIT: You **did** set the executable bit as I said in the first post, didn't you? I say this because of the "can't open" response you got. Open the file manager and go to that directory and right-click on GAME OF THE YEAR 420BLAZEIT.x86, then Properties, then Permissions and make sure the "E(x)ecute file as Program" box is checked.

---

### Post by ricky-flammia on 2015-03-29
It was set as an executable before I even came to the forum but when I attempt to launch it simply by clicking on it, nothing happens, and when I try it through the terminal it either says "can't open" or "no such file or directory". Would it help if I post (a) screenshot(s)?

---

### Post by oldrocker99 on 2015-03-30
At this point, I'd just try redownloading the game, and see if that helps. I don't know what else to offer, I'm afraid:(.

---

### Post by ricky-flammia on 2015-03-30
I tried but it was to no avail. I actually messaged the developer first and he was actually the one who suggested that I come here so the developer doesn't even know lol. Thanks for all of your help.

---

### Post by R33D3M33R on 2015-03-30
Run the command ldd on the game executable, like this:

```
ldd "GAME OF THE YEAR 420BLAZEIT.x86"
```

It will show you which libraries the game needs. Paste the output here.

---

### Post by ricky-flammia on 2015-03-30
It says "No such file or directory". This is the directory I used: home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/GAME OF THE YEAR 420BLAZEIT.x86. Am I typing it into the terminal incorrectly or something? Cool YouTube channel by the way. I subscribed.

---

### Post by R33D3M33R on 2015-03-31
Hmm. Can you open the terminal and do:

```
cd /home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/
```

and after that:

```
ldd "GAME OF THE YEAR 420BLAZEIT.x86"
```

If there is no line that says <= Not Found, then rename

GAME OF THE YEAR 420BLAZEIT_Data to Data and GAME OF THE YEAR 420BLAZEIT.x86 to game.x86 and try to run it. Works for me :).

---

### Post by ricky-flammia on 2015-03-31
SWEET! Here is the output.

                        linux-gate.so.1 =>  (0xf7715000)
     libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf76e8000)
     libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf76c8000)
     librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf76b8000)
     libGLU.so.1 => not found
     libGL.so.1 => /usr/lib32/fglrx/libGL.so.1 (0xf7610000)
     libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf74c0000)
     libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf74a8000)
     libXcursor.so.1 => not found
     libXrandr.so.2 => not found
     libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7460000)
     libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7440000)
     libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7290000)
     /lib/ld-linux.so.2 (0xf7718000)
     libatiuki.so.1 => /usr/lib32/libatiuki.so.1 (0xf7270000)
     libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf7248000)
     libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf7240000)
     libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf7238000)

---

### Post by R33D3M33R on 2015-03-31
This command should install the missing packages:

```
sudo apt-get install libglu1-mesa libxcursor1 libxrandr2
```

You might need to reboot after installation. Don't forget to rename the GAME OF THE YEAR 420BLAZEIT_Data folder to **Data** and binary GAME OF THE YEAR 420BLAZEIT.x86 to **game.x86** after the packages are installed.

Good luck! :)

---

### Post by ricky-flammia on 2015-03-31
Thanks. It says that I already have them installed and I now get the following output from the terminal. /home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/game.x86: error while loading shared libraries: libGLU.so.1: cannot open shared object file: No such file or directory

---

### Post by R33D3M33R on 2015-04-01
You probably have only 64-bit libraries installed, try to install 32-bit ones:

```
sudo apt-get install libglu1-mesa:i386 libxcursor1:i386 libxrandr2:i386
```

---

### Post by ricky-flammia on 2015-04-01
Wow! It worked! Thanks! For some reason the audio doesn't work though. Any idea why?

---

### Post by R33D3M33R on 2015-04-01
Do you have multiple sound cards? It might be outputting the audio to the wrong output. Use Pavucontrol (in repositories) to select the default card.

---

### Post by ricky-flammia on 2015-04-01
I only have one.

---

### Post by R33D3M33R on 2015-04-02
What output do you have if you run the game via terminal? Any errors?

---

### Post by ricky-flammia on 2015-04-02
This is what I get. Found path: /home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/game.x86
Mono path[0] = '/home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/Data/Managed'
Mono path[1] = '/home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/Data/Mono'
Mono config path = '/home/richard/Downloads/GAMEOFTHEYEAR_LINUX/Linux/Data/Mono/etc'

---

### Post by R33D3M33R on 2015-04-03
Nothing unusual is in the output ... I'm out of ideas, sorry.

---

### Post by ricky-flammia on 2015-04-03
Thanks for all of your help. I'm thinking that I might be missing a 32 bit plug in or something because I only have 1 output so I'll probably proceed by trying to find out if that is the case.

---

### Post by ricky-flammia on 2015-04-04
I just wanted to let you know that it turned out that I needed to install libasound2:i386 and libasound2-plugins:i386. Thanks again.

---

### Post by R33D3M33R on 2015-04-05
Great you got it working! It's interesting that the libraries were not detected as missing with ldd.

---

### Post by ricky-flammia on 2015-04-29
I recently updated to Ubuntu 15.04 and once again the game refuses to launch so I ran the command that was posted earlier in this thread to verify that all of the required packages are still installed and they are. That leads me to the conclusion that the problem most likely lies in some changes to Ubuntu as a whole as part of the update. Is anyone aware of any changes in 15.04 that may have caused this application to stop working? Thanks.

---

