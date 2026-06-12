---
title: "pSX and Precise amd64"
date: 2012-07-14
forum: Emulators
---

### Post by HisDudeness3008 on 2012-07-14
Hi everybody! I'm new to the community but not to Ubuntu. I've joined now because I don't have the experience to help anyone, and I've found right now the first problem I have not managed to resolve searching for solutions on the Internet, so I decided to come here and beg for help :mrgreen:

I currently have Ubuntu 12.04 Precise Pangolin amd64 on a laptop, which I plan to never let see Windows. One of the few things I still miss to be complete is a PlayStation emulator. Actually, I already have pcsx working, but I'd wish to get pSX (also called psxfin) for a bunch of reasons:


[LIST=1]
[*]It can make instant saves (save state), of which I've got plenty from my Windows past (yes, it is like cheating, but I'm a horrible gamer)
[*]It can speed up the game to avoid boring unskippable parts
[*]It plays the SCEE and PS logos at the beginning (although that's obviously the minor reason, you might think I'm crazy, and you are probably right, but for someone who have been grew up by the mythic Play Station 1 those images and sounds have got a particular meaning).
[/LIST]
Now, it is notorious pSX have got some serious troubles with 64 bit systems because of some libs and packages. I had found some ways to make it run, declared as working until Natty Narwhal excluded (posts by Mystro256 and dfreer), so my question was if it is any way to make it run on a Precise 64 bit system, as I did not find any, anywhere.


I already used getlibs and I solved (did I?) the _libgtkglext-x11-1.0.so.0: *wrong ELF  class*: _*_ELFCLASS64_ *issue by copying (in an homicidal raptus due to frustration and desperation)  the 32-bit lib into all the folders possible: /lib, /lib32, /usr/lib, /usr/lib32, and I did the same with an _error while loading shared libraries: libglade-2.0.so.0: cannot open shared object file: No such file or directory_



Now, pSX starts, but repeatedly writes these error messages in the terminal


```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(pSX:23369): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(pSX:23369): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:23369): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
```And, as soon as I select the bios, immediately crashes, after writing

```
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0

(pSX:23369): GdkGLExt-WARNING **: Cannot open \xb8$=
L.so
Segmentation fault (core dumped)
```in the terminal.

Now, I don't know how to solve the EFLCLASS issue both because the library is given with a full address of subfolders (and so I don't know how to search the 32 bits one in the internet) and 'cause I'm not sure that ignorant and savage way of copying the 32bit lib everywhere is the solution. Do anybody know how to solve that?

---

### Post by Perfect Storm on 2012-07-14
Thread moved.

---

### Post by HisDudeness3008 on 2012-07-19
Thanks, sorry for the mistake. I didn't see there are subcategories.

No one has any idea? I managed to replace that last library too, but that's not the best way possible. It's not nice having wrong libraries installed in my computer, looks like screwing up my system. In fact, some other programs now recognize those libraries to have wrong elfclass (32 instead of 64). They work anyway, but I don't want to make things the dirty way, making all system less stable and safe. And pSX doesstill not work.

Am I forced to use Wine or go through a virtual machine? Or is there a way to tell a program (in this case, pSX) to go search a lib in a specific path, instead of the default one? Or can pcsx save states and speed up too? Any answer and help is very welcome!

---

### Post by DarkAmbient on 2012-07-21
I'm kinda interested in this as well. Tried to get pSX to work some time ago... no luck here either. I think pSX is kinda old though.. so the soundproblem you experience is most likely related to that Pulseaudio didn't exist or wasn't the standard "soundhandler" at the time. The Gtk and Glib warnings is probably also because pSX is old.. Gtk (Gimp toolkit, the default toolkit for windows/graphics in ubuntu) have been updated pretty much in later years.

I'll try to get pSX started later tonight or tomorrow on my x64-machine and I'll get about my progress. :-)

---

### Post by DarkAmbient on 2012-07-24
**sudo apt-get install pcsxr**

Runs flawlessly for me. :-)

Google PSX Bios to download bios. Unpack them if needed and move them to **<homefolder>.pcsx/bios**. You need need press ctrl+h in Nautilus to be able to see that hidden .pcsx folder.

---

### Post by conformer on 2012-08-07
Hey HisDudeness, I know its been a couple of weeks but I was having the *exact* same error as you so I thought Id put up how got around it. Turns out you don't really need the correct version of libappmenu.so, I didn't mess with it at all. The real problem was the 

[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'

part. pSX has some problem with pulseaudio I guess, so after alot of research I came up with this:
```
#!/bin/bash
killall pulseaudio
sleep 1
exec ~/Desktop/pSX/pSX #or wherever your pSX file is
sleep 1
pulseaudio -D
```
I just wrote that in text editor and saved it as pSXrun (or whatever).

Now you might have to go to ~/.pulse and make a new file called "client.conf" and in it you'll write "autospawn=no". Then I just ran the pSXrun file in terminal. so:
```
sudo sh ~/Desktop/psX/pSXrun
```
It should start up without problems. After you've got it working, go to the configuration and change the audio device to something else. After you've done that you should delete the client.conf file cause it makes problems with pulseaudio later if its still there. Now that youve changed the audio device you shouldn't need it anymore.

Well, thats how I got it working anyways. Kind of annoying but at least it works now. Hopefully it works for you too, unless of course you've already gotten it working. Let me know how it goes!

---

