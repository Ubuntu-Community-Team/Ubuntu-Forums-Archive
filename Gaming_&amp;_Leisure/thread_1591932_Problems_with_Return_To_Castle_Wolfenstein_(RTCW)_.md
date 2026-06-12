---
title: "Problems with Return To Castle Wolfenstein (RTCW) in Ubuntu 10.10"
date: 2010-10-10
forum: Gaming &amp; Leisure
---

### Post by gdbutcher on 2010-10-10
I have had two problems running Return to Castle Wolfenstein in Ubuntu 10.10 64 bit. The first of which I have solved thanks to mhitar on the debian forums:

[http://http://forums.debian.net/viewtopic.php?f=6&t=48415#p281774]("http://forums.debian.net/viewtopic.php?f=6&t=48415#p281774")

On opening, Return to Castle Wolfenstein would crash with following line:

**Received signal 11, exiting...**

I've read that this is an issue with RTCW not liking recent Nvidia drivers. Anyway heres how to solve this issue:

Navigate to your RTCW game directory (mine is named wolfenstein and is in my home directory) and enter the following:

```
cd ~/wolfenstein
cp wolfsp.x86 wolfsp.86x.backup
sudo apt-get install ghex
sudo ghex2 wolfsp.x86
```

Press Ctrl and F (or go to Edit Menu > Find)
In the box on the right type the following (exactly as written):

GL_EXTENSIONS:

You should now see the text highlighted in the right hand pane in ghex.

You may need to scroll down slightly to read the the line you want to modify. The line you need to modify states:

GL_EXTENSIONS: %s..

Close the find window, click on the % symbol in the line

Delete the % symbol and replace it with any letter:

GL_EXTENSIONS: gs..

Be careful not to make any other change.
Save the file, close ghex and your done.

You should be able to play the game now, although if your like me it won't be with sound. 

My second problem is no sound in RTCW, I had sound problems before that I solved by adding:

```
echo "wolfsp.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
```

to /etc/rc.local 

This doesn't work anymore, and neither does any other solution I've seen on the internet basically becuase they all point to /proc/asound/card0/pcm0p/oss and the **'oss'** file does not exist.

Anyone have any ideas how to solve this?

Heres the relevant lines from the terminal:

```
------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------
```

---

### Post by Sockerdrickan on 2010-10-10
I really want the return to castle wolfenstein source code be up and running so these bugs can be fixed. Some people have taken this task but nothing is happening. I tried to get the source running myself but it contains ASM and I have no knowledge of assembly.

I think your best shot might be to wait until someone gets the source running that was released almost 2 months ago. Then someone could just switch to ALSA api.

---

### Post by Dip_Switch on 2011-02-27
I found that this kind of works. I say kind of because it fixes the sound but I seem to keep getting kicked off of the servers with messages that say my installation of the game is bad. 

Anyway, on to the sound fix.

First, download this:

```
http://members.lycos.co.uk/lordbanter/wolfsp-sdl-sound.gz
```It is a nice script that was written by Pyry Haulos to resolve this issue on a previous version of Ubuntu.


Now unzip the file and open it in gedit.

Find the part that looks like this:

```
# SDL audio driver
SDL_AUDIODRIVER="alsa"
```[COLOR=Black][COLOR=Blue]Change "alsa" to "pulse[/COLOR]"[/COLOR]

Then look for the part that looks like this:

```
# Do not touch anything below this line!
SCRIPT_NAME='wolfsp-sdl-sound'
GAME_BIN='wolfsp.x86'
GAME_DIR='rtcw'
```[COLOR=Blue]Change GAME_BIN='wolfsp.x86' to GAME_BIN='et.x86'[/COLOR]

and [COLOR=Blue]change GAME_DIR='rtcw' to GAME_DIR='enemy-territory'[/COLOR]

Save the changes to the file.

Now go to where the file is saved.  Probably in your Downloads directory. Click Places>Downloads

Right click on the file and go to properties.

Then in the Properties windows go to the Permissions tab and tick the box that says "Allow executing file as program" , then click close.

Now all you have to do, when you want to play the game is double click the file then click the "Run in terminal" button. 

Hope this works for you, and if anyone can help out with fixing the problem of getting kicked from the game servers, please let me know.



:)

---

### Post by R33D3M33R on 2011-02-27
You get kicked, because the game executable is modified and fails the CRC check. You can't fix that, but you might be able to play on servers without cheat protection.

---

### Post by gdbutcher on 2011-03-03
Your instructions seems to refer to 'Enemy Territory' not to 'Return to Castle Wolfenstein' but I tried playing around with them
but the script is not working for me. :(

Thanks very much for your suggestion though, it was definitely worth a try.

---

### Post by Toz on 2011-04-17
OSS support is no longer compiled in the kernel. I was able to get RTCW to work with full sound by re-compiling the kernel using instructions at: [http://vanvalkinburgh.org/blog/3511/comment-page-1#comment-797](http://vanvalkinburgh.org/blog/3511/comment-page-1#comment-797). That site also has pre-built 64-bit kernel debs, but I run the 32-bit pae kernel and needed to re-compile.

---

### Post by mbradlcu on 2011-07-22
thanks for the posts. the ghex edit did fix the crash on startup however it seems a simpler fix is starting the game with:```
__GL_ExtensionStringVersion=17700 wolfsp
```

Note, the game is crashing at certain points. I suspected it maybe due to the modified exec but after running it with __GL-Ex... it still crashed. I got the sound working by rebuilding the kernel with oss support.. 

here's the link were I found the info.. apparently another user is experiencing the crashing issue.

[http://forums.gentoo.org/viewtopic-t-833221-start-0.html]("http://forums.gentoo.org/viewtopic-t-833221-start-0.html")

BTW, my standing workaround is just to install 8.04 x86 on an external HD, everything old is new again ; )

---

### Post by julien2233 on 2011-08-28
Hi,

I still have the problem for the sound in RTCW. I am using Kubuntu 11.04.
Here is what I got in the terminal:
```
------- sound initialization -------
/dev/dsp: No such file or directory
Could not open /dev/dsp
------------------------------------

```

I used the script wolfsp-sdl-sound but without any success.
What's really puzzling me is that I was able to solve the sound issue with enemy territory with the script et-sdl-sound.
I tried the wolfsp-sdl-sound script with "pulse" and "alsa" but none of them work (for ET, alsa works fine in the script).
I don't really want to recompile my kernel only to get the sound in RTCW.

I would like to make the sound work. I looked on google and tried tons of scripts and tricks but without being successful.
Has anyone managed to have the sound under natty?

Julien

(I also had the problem of X11 segmenting fault and I get around thanks to the trick given by gdbutcher -GL Extension)

---

### Post by R33D3M33R on 2011-08-29
Try this before you run the game:

```
sudo apt-get install oss-compat
sudo modprobe snd-pcm-oss
 

```

---

### Post by ss900 on 2011-10-26
After 1 year long fight I finally managed RTCW to work with Ubuntu version > 10.04.
Now I'm running RTCW fine with sound on Ubuntu 11.10 Oneiric Ocelot.
To run it properly I did the following:


[LIST]
[*]Installed using [wolf-linux-1.41-3.x86.run]("http://linux.xulin.de/wolf/binaries/wolf-linux-1.41-3.x86.run")
[*]Changed the GL_EXTENSIONS using ghex2 as shown in the [first message]("http://ubuntuforums.org/showthread.php?p=9946588#post9946588") of this thread
[*]Changed the source of et-sdl-sound in order to pass the CRC check (then recompiled)
[*]Updated wolfsp-sdl-sound in order to avoid creating et-sdl-sound.so at runtime and load my customized version
[/LIST]
I posted my customized et-sdl-sound at [this]("http://www.uploadstation.com/file/fpatUmV/et-sdl-sound-custom.tar.gz") ([mirror]("http://ubuntuone.com/7czbBxrGFRqhRH1QBfm728")) page it contains the patched source code the compiled et-sdl-sound.so and my patched wolfsp-sdl-sound.

Please note that for now in order to be used wolfsp-sdl-sound and et-sdl-sound.so must reside in the directory where wolfsp-sdl-sound is launched. I'm planning to improve the startup script in order to avoid this limitation.

Hope this helps.

---

