---
title: "Beyond the Red Line"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by hesaidit on 2007-05-13
ONE OF THE BEST FREE GAMES IV PLAYED

[http://www.game-warden.com/bsg/]("http://www.game-warden.com/bsg/")

What do you think...:KS :KS :KS

---

### Post by mbradlcu on 2007-05-18
I would agree! I'm surprised I haven't heard more around about it.

---

### Post by Nameless One on 2007-05-18
Yeah, it is a pretty decent work of art, Fantastic in almost every way, except I do find the excessive use of 'frak' to be slightly annoying and the voice acting sounds too forced.

You probably don't hear more about it as it's still in a demo form that was only released a few months ago. Also I think they are trying to lay low because of the copyrighing of certain Battlestar Galactica things.

---

### Post by omega_user on 2007-12-23
Yeah,  I only just heard about through a digg story saying it was a top 25 Linux game.  I'm downloading it right now. Psyched to give it a spin.  It looked great on the site and on the blog coverage.

---

### Post by ELD on 2007-12-24
It is a great game!

---

### Post by jingo811 on 2008-01-27
Can somebody help me make this game work?  Here's some things I need to find out before going into any more details.
How do I completely --purge and uninstall this game?
If I have to remove things manually how can I find out where things are located? Since it installed in 3 separate paths and I forgot where these paths are.

I already did this to the 1st path **"sudo chmod 777 -R / /usr/local/games/btrl_demo/"** and the same with the 2nd path **"sudo chmod 777 -R .btrl_demo"**.
Then I tried to run
> linux@pc:/usr/local/games/btrl_demo$ **sudo ./uninstall **
Password:
Could not find a usable uninstall program. Aborting.
linux@pc:/usr/local/games/btrl_demo$ 

---

### Post by Perfect Storm on 2008-01-27
It's in two diffrent path.
The data is in /usr/local/games
and the binary in /usr/local/bin

Just remove them. You local savings and configs are in a hidden folder in your home directory.

---

### Post by jingo811 on 2008-01-27
Ay ay captain then I know what to do to remove the game and install from scratch again.  Before I do that, I managed to start the game's menu and create a player after having chmod 777 -R all the 3 paths.  But when I launch the game I get kicked back to Desktop and the game disappears.  Does this have anything to do with me not setting up my ATI drivers properly?

In that case which method do I use?  There's so many ATI driver tutorials nowadays that I don't even know which the official method is any more. :confused:

AMD Athlon 3200+ | ATI Radeon 9800 Pro - 128 MB | RAM - 1 GB

---

### Post by Perfect Storm on 2008-01-27
Why do you chmod them? There's no need for that.

Please read the note I made for BtRL guide: [http://gaming.gwos.org/doku.php/guides:64bit:beyond_the_red_line](http://gaming.gwos.org/doku.php/guides:64bit:beyond_the_red_line)

ATI? Dunno, I'm a nvidia guy. I have never used ATI so I can't say.
Does you other 3D games work? 
Try launch the game via terminal, then you get the picture of what's wrong.

---

### Post by jingo811 on 2008-01-27
[LIST]
[*]I chmod them becuase the game complains about not having enough disk space when trying to create a player.

[*]That's some nice guide I'm gonna recommend it to the BtrL forums ppl.

[*]eh this is my first 3D game so I dunno.  Seems like I have to revisit the process I did some months ago when I played with Compiz-Fusion.
The thing is the Compiz-Fusion wiki recommended using **"aiglx"** yet the Feisty-ATI-wiki speaks about the opposite **"fglrx"**.
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Then we have this Ubuntu-Moderator-Elliot-programmer-guy who did some auto Graphics driver program for NVIDIA and ATI which I've never used.
   So I'm sort of confused about which of these 3 is the official method for my ATI driver.  Guess that I should stick with the Compiz-Fusion wiki-method since it worked before with my 3D stuff.
[/LIST]

I'll try to fix the hardware setup later need to start studying now.  I'll report the results sometime next week.  Tnx for the tips!

---

### Post by Perfect Storm on 2008-01-27
As far as I understand one of the driver you need to do the compiz stuff the other one is good for gaming, so you have to pick.

(or get a nvidia card).

---

### Post by zorthgo on 2008-01-28
I also have the same problem. When I try to run btrl_demo it kicks me back to the desktop and my display starts to act up, and I'm force to restart my computer to get it to work. I ran it from the terminal and this is the message I'm getting before I have to restart.

X Error of failed request: GLXUnsuportedPrivateRequest
   Major opcode of failed request: 148 (GLX)
   Minor opcode of failed request: 16 (X_GLXVendorPrivate)
   Serial number of failed request: 28
   Current serial number in output stream: 29



Thanks for the help guys!!!!

---

### Post by Perfect Storm on 2008-01-29
```
cat /etc/X11/xorg.conf
```

---

