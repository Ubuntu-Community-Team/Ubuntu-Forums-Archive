---
title: "Frets on Fire error"
date: 2007-12-01
forum: Gaming &amp; Leisure
---

### Post by magicman692 on 2007-12-01
I installed FoF with the Add/Remove on Ubuntu, but it won't start. Terminal says this:

```
eric@eric-desktop:~$ fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 68, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual

```

As a new Ubuntu user, I have barely any clue what this all means. Please help?

---

### Post by magicman692 on 2007-12-02
Please, anyone?

---

### Post by jimmux on 2007-12-03
I don't have any answers, but I have exactly the same problem. 

I've seen some indications elsewhere that it can have trouble on 64-bit versions (as I am running).

---

### Post by go_beep_yourself on 2007-12-09
I'm running a 32 bit os and have the same problem. You are probably using the deb from getdeb.net right? I will try installing it through a different method.

---

### Post by magicman692 on 2007-12-15
hmm... thought I had it earlier... but nope, still wont work. Can anyone else help?

---

### Post by magicman692 on 2007-12-21
Got it!!!!!

```
sudo gedit /etc/X11/xorg.conf
```

This should open xorg. Next, go to about 40 lines down, and you should see this:

```
Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E773c"
	DefaultDepth	16
```

Just change the default depth (in my case, 16, but could be any other number) to 24, restart "X" (or if you dont know how, just restart your computer), and start FoF. It should work, but mine goes pretty slow.

Thanks alot to the guy who found this out! ([http://avokadaro.blogspot.com/2007_09_01_archive.html](http://avokadaro.blogspot.com/2007_09_01_archive.html))

---

### Post by doorknob60 on 2007-12-21
I recommend running the version from [http://fretsonfire.sourceforge.net](http://fretsonfire.sourceforge.net) , the version from the repos went super slow for me but from the website it ran perfectly.

---

### Post by blakfire80 on 2008-01-01
> **doorknob60 said:**
> I recommend running the version from [http://fretsonfire.sourceforge.net](http://fretsonfire.sourceforge.net) , the version from the repos went super slow for me but from the website it ran perfectly.

I am not sure how to install it from the .tar file in KUBUNTU (7.10). can anyone give some advice.:confused:

---

### Post by xc3RnbFO8P on 2008-01-02
You dont install it.
Unpack
find FretsOnFire
double click on file
run.

---

### Post by go_beep_yourself on 2008-01-04
Is anyone else having sound problems with this game in 64 bit Ubuntu?

---

### Post by Mr.NiceGuy on 2008-01-04
Hi,

I recently installed this game on my computer and am having no problems at all. I suggest you get rf-mod because it makes the game look way way better. 

[http://rapidshare.com/files/55005134/rf-mod-4-linux-i686.tar.bz2.html]("http://rapidshare.com/files/55005134/rf-mod-4-linux-i686.tar.bz2.html")
download for gusty ^

[http://rapidshare.com/files/55040296/rfmod-4-linux-i686-feisty.tar.bz2.html]("http://rapidshare.com/files/55040296/rfmod-4-linux-i686-feisty.tar.bz2.html")
download for feisty ^

I just want to tell you that i did not make these packages and that buttons did.

Now, to run rf-mod you download either gusty or feisty depending on what version of ubuntu you are running on, extract the file to where you want it and then when you want to play just open up the folder and click on FretsonFire it is an sh script. Also before you play you have to go into to folder, then click on data, and then add a folder called songs which you can find the originl songs for fof in your other download that you got from [http://fretsonfire.sourceforge.net](http://fretsonfire.sourceforge.net)

also if you want to add more songs you can go to [www.keyboardsonfire.net](www.keyboardsonfire.net) and click on songs, or just simply google fof + the song you want im sure you will find it. :)

---

