---
title: "Sauerbraten crash / freeze at launch"
date: 2008-02-09
forum: Gaming &amp; Leisure
---

### Post by wumagna on 2008-02-09
Hi,

I'm having a problem with the assassin's edition of sauerbraten.

I previously installed the game from synaptic and it worked fine. Unfortunately it's an old protocol and I can't go multiplayer.

I then downloaded the assassin's edition and after extracting just ran sauerbraten_unix. 

It enters the game, loads and when entering the default map it immediately freezes continuing music for a while and then passing to a black screen. I tried ctrl+alt+f1 and nothing happens so I keep hard-rebooting the system everytime I try to play the game.

Here's my specs:

Acer aspire 56.. with Nvidia Gforce Go 7300 and 2gb ram.

I have a double partition and Sauerbraten runs fine both singleplayer and multiplayer in windows.

Can anyone help me with this? Is there a way to get the assassin version from synaptic?

(New to ubuntu/linux, please be specific)

Tks

---

### Post by wumagna on 2008-02-09
Just a quick update on this problem:

I tried changing the starting resolution - Freezes all the same.

I now started sauerbraten and called a virtual console while the engine was loading. I hit ctrl+alt+f7 after a while and it was running fine!

I don't get it...

I try loading it again normally and it freezes again,

Does this help anyone?

---

### Post by daigidan on 2008-02-14
Can you run Sauer from a terminal and post the output? Also, I had an issue with gnome-screensaver where it would cause similar behavior. If you're running Gnome, you might want to "sudo killall gnome-screensaver" and see if that helps.

---

### Post by wumagna on 2008-02-14
Here goes what you asked for:

Using home directory: /home/wumagna/.sauerbraten
init: sdl
init: enet
init: video: mode
init: video: misc
init: gl
Renderer: GeForce Go 7300/PCI/SSE2 (NVIDIA Corporation)
Driver: 2.1.1 NVIDIA 100.14.19
Rendering using the OpenGL 1.5 GLSL shader path.
init: console
init: gl: effects
init: world
init: sound
init: cfg
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime
game mode is ffa/default

Again to get this terminal output I have to enter the game and immediately press ctrl+alt+f1... wait for the music and then go in.

I now found that after a few seconds of playing it automatically quits the game and logs out.

The screen saver issue would only affect after a while right? I'll test it now anyways.

---

### Post by daigidan on 2008-02-14
Yes, the screensaver should only kick in after X minutes have passed, as based on your settings. Just to confirm, you get no additional output when the game exits?

Also, it sounds like you installed from repositories (Synaptic) and then downloaded the game separately, so you may have two Sauer executables on your system. "which sauerbraten_unix" should tell you which one is starting up.

Lastly, are you running on a 64-bit platform by any chance (uname -a would include x86_64)? If so, compiling Sauer may help. Check out Artificial Intelligence's instructions here: [http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten](http://gaming.gwos.org/doku.php/guides:64bit:sauerbraten)

---

### Post by wumagna on 2008-02-15
Hey,

Can you explain step by step how to check if I am in a 64bit system?

tks

---

### Post by wumagna on 2008-02-15
wumagna@wumagna-laptop:~$ uname -a
Linux wumagna-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

I guess it's not 64 bit... any other options?

---

### Post by daigidan on 2008-02-15
No, that's not 64-bit. Can you open a terminal and post the output of:

```
which sauerbraten_unix
```

It helps to know whether we're working with the Ubuntu-packaged version of Sauer or the one you downloaded.

---

### Post by wumagna on 2008-02-15
Hummm nothing happens, am I doing this right?

wumagna@wumagna-laptop:~$ which sauerbraten_unix
wumagna@wumagna-laptop:~$

---

### Post by wumagna on 2008-02-15
Ok, it's finally working...

It missed the latest patch at sauerbraten.org

Thanks for the help

---

### Post by elkanguro on 2008-03-09
I have the same problem, but in my case the patch didn't help. The game still freeze. It is write in left corner that i.e. VS: chaingundisplay EXCEEDED NATIVE LIMITS. Only hard-reboot can help. It is the version from the official page. I use CoreDuo (32bit) and Feisty and graph from ATI (x200m).

---

