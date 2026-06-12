---
title: "Help with Wc3"
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by iamBevan on 2007-09-23
Hi guys, I'm having a bit of trouble with wc3. I have installed it with Wine no probs, but its extremely laggy when it runs - completely unplayable.

And it used to be fine with Windows :( - Just wondering if anyone has any idea's what the problem may be, or suggestions on a fix.

Cheers - Kev

---

### Post by tgeorge on 2007-09-23
How are you running it? make sure you disabled movies from starting by renaming the movies folder. one thing you can do is this:

```
wine war3.exe --opengl
```

FROM THE DIRECTORY that you installed warcraft III. You might be trying to play it in Directx mode. Also, do you have a good system? These are my suggestions. I am still having trouble with warcraft 3, though I finally got it running. The KB shortcuts dont work.

---

### Post by iamBevan on 2007-09-23
> **tgeorge said:**
> How are you running it? make sure you disabled movies from starting by renaming the movies folder. one thing you can do is this:

```
wine war3.exe --opengl
```

FROM THE DIRECTORY that you installed warcraft III. You might be trying to play it in Directx mode. Also, do you have a good system? These are my suggestions. I am still having trouble with warcraft 3, though I finally got it running. The KB shortcuts dont work.

When I try that code I get the following message:

```
wine: could not load L"c:\\windows\\system32\\war3.exe": Module not found
```

---

### Post by tgeorge on 2007-09-23
> **FROM THE DIRECTORY that you installed warcraft III.**[/SIZE][SIZE="6"]

you have to navigate to where it is installed...

this is typically the home/yourusername/.wine/drive_c/Program Files/Warcraft III directory. Dont forget the . on the .wine, indicating that it is a hidden folder.

---

### Post by iamBevan on 2007-09-23
Sorry, buy could you be a little more specific, I've only had Ubuntu for a few days and am struggling with the Terminal commands.

---

### Post by tgeorge on 2007-09-23
sure...
do this

type pwd to make sure youre in your /home/YOURUSERNAME directory

then, type cd ./.wine/drive_c/Program\ Files/Warcraft\ III and hit [Enter]

This is assuming that you installed wc3 to the default directory. 

Then type the following code:

```
wine war3 --opengl --windowed 
```

this worked for me, and this most recent time I was able to use the keyboard, for some reason.. but it did not go into windowed mode like it was supposed to...

another thing I suggest is to go into the terminal and type winecfg

this should bring up the wine configuration utility. Click the graphics tab at the top and ensure that allow window manager to manage windows is checked. With it NOT checked, some people have had trouble with the keyboard working.

Let me know fi this helps

---

### Post by iamBevan on 2007-09-24
Ok. I did that exactly as you said, and I got the following message:

```
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b1380) : stub, simulating 64MB for now, returning 64MB left
fixme:wave:DSD_CreateSecondaryBuffer (0x203248,0x1bd89bc,180e0,0,0x20181c,0x20192c,0x2017f8): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x2017d0
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
```

Then the game runs in full screen mode, and lags as it did before.

---

### Post by tgeorge on 2007-09-24
you may not have a capable system then, or you are using vesa drivers. Anyone else feel free to chime in, as I am a noob too and I'm out of things to try. This will be my last reply for the evening, as I am going to bed. I work tomorrow at 8AM, and its 12:30 here!

At least you have functionality. It took me a weekend to get that. Youre on the right track! I just got done playing my second bnet game. Works slicker than snot on a doorlock... err something like that, but sometimes it doesnt work. Like sometimes when I exit it, it will crash the windowing system and I will see only a blank screen. I try pressing control + alt + backspace to restart X, but that doesnt work so a manual reboot is necessary.

Hang in there... If I have to, you have to :D Ok, well I dont have to but I  dont have any more downloaded windows xp discs... ive given them all away and I am using the excuse of "not feeling" like downloading another. At first there were mountains to climb, but theyre getting smaller with each new thing I learn about Ubuntu!

---

### Post by iamBevan on 2007-09-24
Could anyone else suggest a fix for this?

---

### Post by tgeorge on 2007-09-25
What kind of video card do you have / what are your system specs? I dont know much about wine, but I do know that I have seen memory useage as high as 700MB when I'm playing, and I have a very current video card. Even with these things, I still have issues with WC3 crashing and not loading sometimes. 

Another thing you should do is make sure your desktop is in 800x600 resolution before attempting to launch WC3, WC3 has a default res of 800x600, and if you put your desktop in this resolution it wont have to switch.

HAVE YOU RENAMED YOUR MOVIE FOLDER YET? This is very important, as having the movies run on start can cause some major issues.

---

### Post by iamBevan on 2007-09-25
I have renamed the movies folder, but there is no change. My system specs are as follows:

CPU: AMD Athlon XP 2.4Ghz
GFX: Radeon 9600XT (128 )
RAM: 1Gig

---

