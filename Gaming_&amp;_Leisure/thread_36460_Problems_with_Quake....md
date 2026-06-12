---
title: "Problems with Quake..."
date: 2005-05-23
forum: Gaming &amp; Leisure
---

### Post by Muiske on 2005-05-23
Hello everyone!

I'm new on this forum, and I'm also new with Linux (and Ubuntu). I'm learning all there is to learn, but in the meantime I'm having some troubles, and I would certainly appreciate some help from more experienced users. Ok, so what's the problem?

1 - I cannot install the original quake.

I did everything according to [http://www.tldp.org/HOWTO/Quake-HOWTO.html](http://www.tldp.org/HOWTO/Quake-HOWTO.html), but when I try to execute glquake or quake.x11 it stops with the error "segmentation fault". Strange, since running Equake actually IS possible....
Anyone?

2 - Equake.

First of all, I have the original games and I copied the *.pak files to the /id1 directory. However, I cannot play episodes 2 till 5. Do I need to 'tell' the program that the paks are there? If so, how?

Then, the sound doesn't work. ALSA is installed.. and the sound works, but not in quake. Do I have to change something?

Another problem. When I exit EQuake, I get this error:

/dev/dsp: Broken pipe
X Error of failed request: BadValue (integer parameter out of range for operation)
Major opcode of failed request: 135 (XFree86-VidModeExtension)
Minor opcode of failed request: 10 (XF86VidModeSwitchToMode)
Value in failed request: 0x2a00002
Serial number of failed request: 1153
Current serial number in output stream: 1155

X is stretched and distorted. It gets back to normal when I change the resolution and then turn it back on the original value, but it would be nice if this problem could be avoided. Anyone?

Thanks

---

### Post by Muiske on 2005-05-30
Bump....  ](*,)

---

### Post by Muiske on 2005-06-12
Hmm... still can't get it working. I think it might have something to do with the library linking, but that's just a wild guess since I'm pretty ignorant about the Linux library stuff.

Another problem: the sound isn't working, and EQuake only runs in windowed mode. 

I don't know where to begin... :(

---

### Post by jdodson on 2005-06-12
[QUOTE=Muiske]Hmm... still can't get it working. I think it might have something to do with the library linking, but that's just a wild guess since I'm pretty ignorant about the Linux library stuff.

Another problem: the sound isn't working, and EQuake only runs in windowed mode. 

I don't know where to begin... :([/QUOTE]

i am going to create a monster thread dedicated to solving various sound issues with games.  look for the post in a few days.

---

### Post by crane on 2005-06-12
[QUOTE=Muiske]Hmm... still can't get it working. I think it might have something to do with the library linking, but that's just a wild guess since I'm pretty ignorant about the Linux library stuff.

Another problem: the sound isn't working, and EQuake only runs in windowed mode. 

I don't know where to begin... :([/QUOTE]

I know this is a silly question, but isn't there a selection in the menu for running at full screen? Have you tryied this? Just asking.

As far as sound, do ither apps work with sound? What other apps are you running. 
Do you get error messages?
Be sure to post them. All the info you can get is helpful for other to under stand the problem.

---

### Post by Muiske on 2005-06-12
[QUOTE=crane]I know this is a silly question, but isn't there a selection in the menu for running at full screen? Have you tryied this? Just asking.

As far as sound, do ither apps work with sound? What other apps are you running. 
Do you get error messages?
Be sure to post them. All the info you can get is helpful for other to under stand the problem.[/QUOTE]

Hehe, nope, there's no selection for running at full screen. I can change the resolution of the game by typing it at the console, but that just changes the size of the window. I'll have a look at the documentation, maybe I can find something there; although the game should start at fullscreen. 

I have other applications running with sound. MPlayer and XMMS both are installed and working properly. The GNome sound also is working fine.... 

However, I get an error message immediately after starting the game:

"/dev/dsp: Broken pipe"

Which concerns the sound. I however have no idea what to do with this.


There's another thing. When playing quake and going underwater and picking up items, there's a screen flash not only in the quake-window but on the whole screen... I don't think this is a sign everything is working as it should be...
HELP!  :???:

---

### Post by Muiske on 2005-06-14
Ok, I got the sound working and the game is in fullscreen running at a nice 75 Hz refresh rate.

However. I get this error when I return to X:

[I]X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  135 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3000002
  Serial number of failed request:  2490
  Current serial number in output stream:  2492[/I]

So yeah, it has got to do with XFree86; but can anyone help me with this? What should I do??

Thanks.

---

### Post by Ranime on 2005-06-14
for teh sound problem... Perhaps **esd** is hogging your sound device for the game.

I made this for Quake3, maybe you can use it to run Quake?

```
esdctl off
sleep 2
quake3
esdctl on
``` 

It sets esd idle while running the game and turns it back on when the game terminates.

Copy the code into a text editor of choice and save it as some bash script.
e.g.: quake.sh or something.

goodluck!

---

### Post by Muiske on 2005-06-16
[QUOTE=Ranime]for teh sound problem... Perhaps **esd** is hogging your sound device for the game.

I made this for Quake3, maybe you can use it to run Quake?

```
esdctl off
sleep 2
quake3
esdctl on
``` 

It sets esd idle while running the game and turns it back on when the game terminates.

Copy the code into a text editor of choice and save it as some bash script.
e.g.: quake.sh or something.

goodluck![/QUOTE]

Ranime, thanks for your help; I had the sound working already though. I only need to solve that problem with Quake and X...

---

### Post by zoly on 2006-01-02
[QUOTE=Muiske]Ok, I got the sound working ...[/QUOTE]

Muiske: how did you do that??
I try to solve this problem on my notebook with i852GM chipset (with ALSA driver) without any success...
(I've tried to stop ESD or 'echo' a process suggested in other post somewhere here at Ubuntuforums.org, but no sound till now.....)

Also: I've very choppy sound in Quake II using the SDL sound driver (this is the only one what I can use). Any suggestion for this?

---

