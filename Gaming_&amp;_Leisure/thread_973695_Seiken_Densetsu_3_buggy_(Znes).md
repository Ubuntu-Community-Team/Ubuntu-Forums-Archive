---
title: "Seiken Densetsu 3 buggy (Znes)"
date: 2008-11-06
forum: Gaming &amp; Leisure
---

### Post by pixarinc on 2008-11-06
I don't know if it's only me but I think the actualy GAME is buggy. I managed to fix the sound as that seems to be a common problem around here but my problem is within the game itself. My tech bar doesn't seem to work for one. I have a tech bar, that slowly gets filled as I hit the enemies with my attack. Once the bar is filled then I can unleash my tech skill. But whenever I enter new maps the bar, whether filled or half-filled, gets reset to zero. Sometimes it'll even reset while I'm in the middle of fighting. I noticed that NPCs that are supposed to turn into wolves only at night are roaming around in broad daylight as wolves!

I don't know if it's just the rom or what. If it is, can someone please link me a fully-functioning, tested one? I've tried three different roms so far with the same result. I'm not sure if they were the exact same rom however.

---

### Post by DoktorSeven on 2008-11-07
They frown on linking to copyrighted ROMs on this forum, regardless, so asking for one probably isn't a good idea.  They want to avoid any legal issues, ya know.  

Just so you know.  

Don't remember having any problems with SD3 when I tried it in zsnes, but that was quite some time ago.  Good luck.

---

### Post by pixarinc on 2008-11-08
I appreciate the warning, I'll keep that in mind. 

Maybe you can help me with something else. Apparently there's this program for ZSNES that checks whether the ROM is working or not, and if it isn't, can fix it. 

It's called NSRT:
[http://snesemu.black-ship.net/index.php?page=tools](http://snesemu.black-ship.net/index.php?page=tools)

Of course, they had to make it impossible for a newb like me to install by packaging it in tar.gz. Now I'm not even sure if it's the source code, but I can't even find it in console. I copied the tar.gz file into a folder called "Compiling" and I uncompressed it there.

nico@Nico-desktop:~$ cd /home/nico/Desktop/
nico@Nico-desktop:~/Desktop$ ls
Compiling 
nsrt34l.tar.gz
nico@Nico-desktop:~/Desktop$ 
nico@Nico-desktop:~/Desktop$ cd /Compiling
bash: cd: /Compiling: No such file or directory
nico@Nico-desktop:~/Desktop$ pwd
/home/nico/Desktop
nico@Nico-desktop:~/Desktop$ cd /home/nico/Desktop/Compiling
bash: cd: /home/nico/Desktop/Compiling: No such file or directory

---

### Post by FranMichaels on 2008-11-08
I can vouch that SD3 works fine in zsnes, it's probably a bad rom, if you found one pre-patched in English, I would advise against that for many reasons. You can grab the patch from romhacking.net, even a nice color pallete patch. I will not give a link to the rom.

That aside, 
```
cd Compiling
```
would work from where you left off
You can use tab (hit it once or twice) to help you with file/dir names...

Try cd ~/De
then hit tab, you get the idea :)

There is a gui and all that, I think the site you link has it, looks like OS independent... but last time I used nsrt I just used the binaries from commandline... 
Make sure the file called nsrt is executable, right click, set permissions to executable. Just play with the command, from terminal, or if you make a folder in your home called bin and put stuff in there, you can just run it like so

```
nsrt
```

Otherwise, from the directory
```
./nsrt
```

From there you'll get the options you need to verify your rom.

Good luck!

---

### Post by tukuyomi on 2008-11-11
You don't have to compile nsrt, it's already compiled!
- Download nsrt from the link to your Desktop, then extract the archive with the right-click.
- Open the folder 'nsrt34l' and a terminal from Application -> Accessories.
Drag'n'drop nsrt on the terminal, then drag'n'drop the rom on the terminal. the command will look like this:
```
tukuyomi@dejikochan:~$ '/home/tukuyomi/Desktop/nsrt34l/nsrt' '/home/tukuyomi/Desktop/seiken_densetsu_3.smc'
```
Hit Enter to probe your rom
To get a bit of help, drag'n'drop nsrt on the terminal, then write '| less' after that
```
tukuyomi@dejikochan:~$ '/home/tukuyomi/Desktop/nsrt34l/nsrt' | less
```
Browse with UP and DOWN keys; hit Q to quit.

---

