---
title: "My game engine, OpenBlox"
date: 2010-08-11
forum: Gaming &amp; Leisure
---

### Post by DangerOnTheRanger on 2010-08-11
I'm making a game engine/game development framework, called OpenBlox. It's not finished yet, but I've attached a preview of what you can do with it.

Its site is at [http://openblox.sourceforge.net]("http://openblox.sourceforge.net/")

Its project/download site is at [http://sourceforge.net/projects/openblox](http://sourceforge.net/projects/openblox)

I'll be sure to update this post as soon as i make an actual release!

-DangerOnTheRanger

---

### Post by juancarlospaco on 2010-08-11
wonderfull, does the box fly?, i want to play!
:)

---

### Post by DangerOnTheRanger on 2010-08-11
There will also be block-like figures that will be the user's avatar

And technically, you don't *directly *play with OpenBlox. You *make games *with it, using those bricks(that you can resize, change color, and in the future, even shape!), Lua scripts, and extra 3D meshes.

Think about it. 3D RAD for games! For free! :shock:

(I'm also planning to implement networking, so it will be 3D RAD for MMOs! Wahoo! :biggrin:)

---

### Post by DangerOnTheRanger on 2010-08-11
Thanks, and no the boxes don't fly, they are basically Lego bricks, that  you build with. Although, as soon as i get ODE physics working, who  knows what might happen with flying...
There will also be block-like figures that will be the user's avatar.

And technically, you don't *directly *play with OpenBlox. You *make games *with it, using those bricks(that you can resize, change color, and in the future, even shape!), Lua scripts, and 3D meshes.

Think about it. 3D RAD for games! For free! :shock:

(I'm also planning to implement networking, so it will be 3D RAD for MMOs! Wahoo! :biggrin:)

---

### Post by DangerOnTheRanger on 2010-08-11
Whoops, double post...:redface:

---

### Post by spocchio on 2010-08-12
:popcorn: but, there is something to  download beyond the screenshot?

---

### Post by cliffdodger on 2010-08-12
What's your aim with this engine? Have you had a look at Crystalspace and Irrlicht? Also Nel (MMORPG engine)

---

### Post by DangerOnTheRanger on 2010-08-13
No, there's nothing to download besides the screenshot, as I'm finalizing the avatar code, and looking over the design one last time.

My aim is to make it easy for non-programmers to make games. It's kinda like 3D CAD for Lego bricks, with Lua scripts for interactivity. Nel is fine, but I'm currently using Python, which I'm more comfortable with than C++. That said, I might make a transition sometime in the future to Nel from Panda3D.

And I've looked at Crystal Space and Irrlicht. They are far more general-purpose than OpenBlox. The closest open-source game engine to OpenBlox is the Blender Game Engine.

---

### Post by cliffdodger on 2010-08-16
Interesting idea.

Are you a fan of Lego mindstorms? Granted their software deals with very limited logic but that's a great example of how by limiting logic and potential decisions you can simplify things for the average person - in regards to program A.I.

Have you looked at either of these free game maker programs before?
[http://gamemaker.nl/](http://gamemaker.nl/)
[http://www.yoyogames.com/gamemaker](http://www.yoyogames.com/gamemaker)

---

### Post by DangerOnTheRanger on 2010-08-18
Yes, I have looked at Mindstorms, although I don't see what that has to do with OpenBlox.
And I tried GameMaker long ago, too simplistic for my tastes...

---

### Post by juancarlospaco on 2010-08-19
*Sweeeeeeeeeeeet Python*

---

### Post by eggplantanimation on 2010-08-20
What python modules are you using?

---

### Post by Naiki Muliaina on 2010-08-21
When are you going to have a downloadable version? What licence will it be released under? (guessin GPL but 2 or 3) :)

---

### Post by DangerOnTheRanger on 2010-08-25
I'm using Panda3D, and the Python standard library. It'll be released under the GPL v3, and I'm releasing it for the first time today or tomorrow!

---

### Post by DangerOnTheRanger on 2010-08-26
I just released it! [https://sourceforge.net/projects/openblox/files/Releases/openblox-0-1.tar.gz/download](https://sourceforge.net/projects/openblox/files/Releases/openblox-0-1.tar.gz/download)

---

### Post by Naiki Muliaina on 2010-08-26
Haven't downloaded yet, I am curious to know, GPL v3 means you cant repackage and sell right? Does that mean you couldn't sell a game made by this engine?

---

### Post by Modplanman on 2010-08-26
> **Naiki Muliaina said:**
> Haven't downloaded yet, I am curious to know, GPL v3 means you cant repackage and sell right? Does that mean you couldn't sell a game made by this engine?

Nothing in any GPL license says you cannot sell or repackage. The main difference between GPL3 and GPL 2 is patent and "Tivo-ising" stuff.

[http://www.gnu.org/licenses/quick-guide-gplv3.html](http://www.gnu.org/licenses/quick-guide-gplv3.html)

> &#8220;Free software&#8221; does not mean &#8220;noncommercial.&#8221; A free program must be available for commercial use, commercial development, and commercial distribution. Commercial development of free software is no longer unusual; such free commercial software is very important. You may have paid money to get copies of free software, or you may have obtained copies at no charge. But regardless of how you got your copies, you always have the freedom to copy and change the software, even to [sell copies]("http://www.gnu.org/philosophy/selling.html").

[...]

However, rules about how to package a modified version are acceptable, if they don't substantively limit your freedom to release modified versions, or your freedom to make and use modified versions privately. Rules that &#8220;if you make your version available in this way, you must make it available in that way also&#8221; can be acceptable too, on the same condition. (Note that such a rule still leaves you the choice of whether to publish your version at all.) Rules that require release of source code to the users for versions that you put into public use are also acceptable. It is also acceptable for the license to require that you identify your modifications as yours, or that, if you have distributed a modified version and a previous developer asks for a copy of it, you must send one. 

[http://www.gnu.org/philosophy/free-sw.html](http://www.gnu.org/philosophy/free-sw.html)
 

---

### Post by Naiki Muliaina on 2010-08-26
Okis, sorry, my thinkings off. GPL 3 you cant package with closed source right? So if you make a game with that engine you will have to open source everything that goes into it?

---

### Post by DangerOnTheRanger on 2010-08-28
Yes, you can package closed-source software on the same medium as GPL'ed software. You just can't mix their code.

And to answer your second question, you will have to make all the source code open source, as you will have to make API calls to the game engine, to make it(your game) interactive. You do not have to release the artwork and non code-related stuff as open source, though.

EDIT: OpenBlox just broke 770 downloads, as of last hour!

563 downloads from Windows, 152 from Linux, 21 from Mac OSX, 33 from various other OSes, and even 1 from Android!
203 downloads from the US, 131 from China, 42 from the UK, and 36 from Canada. The rest are from various other countries, like Russia, India, Germany, and even Vietnam.

---

### Post by JerBear64 on 2012-01-03
I cannot seem to get OpenBlox to work. I have Ubuntu 11.10, and my terminal says there are unmet dependencies when trying to install the Panda3D SDK 1.7.2.
Here's my terminal window:


The following packages have unmet dependencies:
 panda3d1.7 : Depends: libswscale0 (>= 4:0.6-1~) but it is not installable or
                       libswscale-extra-0 (>= 4:0.6-1~) but it is not installable
              Recommends: panda3d-runtime but it is not going to be installed
              Recommends: python-profiler (>= 2.6)
              Recommends: libpython2.6 (>= 2.6) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Therefore, I can't use OpenBlox. :(

---

### Post by DangerOnTheRanger on 2012-01-03
Oneric wasn't ready by the time Panda3D 1.7.2 was released, and as you've found out, attempting to install a Lucid or Maverick .deb on Oneric doesn't always work. What you can do is install Panda3D 1.8, which is backwards-compatible with 1.7.2. Here's a download link for the latest pre-release of 1.8 (1.8 hasn't been officially released yet): [http://www.panda3d.org/download.php?platform=oneiric&version=devel&sdk]("http://www.panda3d.org/download.php?platform=oneiric&version=devel&sdk")

---

### Post by JerBear64 on 2012-01-04
Thanks! i got it to work. Unfortunately, OpenBlox crashes after I move my character.

---

### Post by DangerOnTheRanger on 2012-01-04
Hmm, that's odd. What sort of message do you get in the console when that happens?

---

### Post by JerBear64 on 2012-01-05
> **DangerOnTheRanger said:**
> Hmm, that's odd. What sort of message do you get in the console when that happens?

I am using the GUI. I will start OpenBlox via Terminal and see if that will give me a message; the GUI just completely closes.

Perhaps it's the build I downloaded. I got the i386 package made a couple days ago, I am using 32-bit Ubuntu. I could probably get the second latest.

---

### Post by JerBear64 on 2012-01-05
Here is the command line startup:

Known pipe types:
  glxGraphicsPipe
(all display modules loaded.)
:display:glxdisplay(warning): No suitable FBConfig contexts available; using XVisual only.
depth_bits=24 color_bits=24 alpha_bits=8 back_buffers=1 force_hardware=1 
:net(error): Unable to open TCP connection to server 127.0.0.1 on port 5185
: pstats(error): Couldn't connect to PStatServer at localhost:5185
Traceback (most recent call last):
  File "oblaunch.py", line 90, in <module>
    load_world(sys.argv[1])
  File "oblaunch.py", line 83, in load_world
    obengine.gfx.run(run_world)
  File "/home/jeremy/OpenBlox/obengine/gfx/__init__.py", line 112, in run
    main_method(rootwin)
  File "oblaunch.py", line 49, in run_world
    world_file = zipfile.ZipFile(os.path.join(__file__[:len(__file__) - len('oblaunch.py') - 1],os.path.join('games', game + '.zip')))
  File "/usr/lib/python2.7/zipfile.py", line 697, in __init__
    self.fp = open(file, modeDict[mode])
IOError: [Errno 2] No such file or directory: 'oblaunch.p/games/World.zip'


So does the game see the file but thinks it's in another directory?

---

### Post by DangerOnTheRanger on 2012-01-08
> **JerBear64 said:**
> Here is the command line startup:

Known pipe types:
  glxGraphicsPipe
(all display modules loaded.)
:display:glxdisplay(warning): No suitable FBConfig contexts available; using XVisual only.
depth_bits=24 color_bits=24 alpha_bits=8 back_buffers=1 force_hardware=1 
:net(error): Unable to open TCP connection to server 127.0.0.1 on port 5185
: pstats(error): Couldn't connect to PStatServer at localhost:5185
Traceback (most recent call last):
  File "oblaunch.py", line 90, in <module>
    load_world(sys.argv[1])
  File "oblaunch.py", line 83, in load_world
    obengine.gfx.run(run_world)
  File "/home/jeremy/OpenBlox/obengine/gfx/__init__.py", line 112, in run
    main_method(rootwin)
  File "oblaunch.py", line 49, in run_world
    world_file = zipfile.ZipFile(os.path.join(__file__[:len(__file__) - len('oblaunch.py') - 1],os.path.join('games', game + '.zip')))
  File "/usr/lib/python2.7/zipfile.py", line 697, in __init__
    self.fp = open(file, modeDict[mode])
IOError: [Errno 2] No such file or directory: 'oblaunch.p/games/World.zip'


So does the game see the file but thinks it's in another directory?

What actually happened is the game messed up when it tried to extrapolate the location of the games directory from the location of the launcher script. I've noticed a lot of other people having this problem - what you should probably do is try the beta version of OpenBlox, which you can get here: [http://sourceforge.net/projects/openblox/files/Releases/openblox-0.7-beta.zip/download](http://sourceforge.net/projects/openblox/files/Releases/openblox-0.7-beta.zip/download). Just extract the zip file anywhere you like, and start up a game using the following command (make sure you're in the directory that you extracted the beta version to):

```

python tools/oblaunch.py <game name>

```You can see what games are currently installed by taking a look at the "games" subdirectory - for example, to start up the new Lua scripting demo game (called "Snow Day", located in "games/Snow Day.zip"), use this command:

```

python tools/oblaunch.py "Snow Day"

```Hope this helps! :)

---

### Post by JerBear64 on 2012-01-09
More errors show up. I downloaded the 0.7 beta, and this is what I get:

Traceback (most recent call last):
  File "tools/oblaunch.py", line 97, in <module>
    load_world(sys.argv[1])
  File "tools/oblaunch.py", line 47, in load_world
    game_file = zipfile.ZipFile(game)
  File "/usr/lib/python2.7/zipfile.py", line 697, in __init__
    self.fp = open(file, modeDict[mode])
IOError: [Errno 2] No such file or directory: 'World'

The file "World.zip" DOES exist in the games folder, though.

Thanks for the help so far. I've gone from unplayable to playable for half a second :p

---

### Post by Carpentr on 2012-01-09
Nice work.

How long have you been programming in Python? I'm just curious. I've just started to learn Python 3 after taking a few programming classes for college.

---

### Post by JerBear64 on 2012-01-10
Just an update on my problem- When I start the oblaunchgui script and select a game, no players are generated. The camera shoots an awkwardly random view of the game and exits a few seconds afterward.

---

### Post by DangerOnTheRanger on 2012-02-07
> **JerBear64 said:**
> Just an update on my problem- When I start the oblaunchgui script and select a game, no players are generated. The camera shoots an awkwardly random view of the game and exits a few seconds afterward.

Sorry for taking so long to respond - life dragged me away, kicking and screaming :)

I've seen this bug a few times before; I recommend using the Mercurial/trunk version, which you can get here:[http://openblox.hg.sourceforge.net/hgweb/openblox/openblox/archive/tip.tar.gz]("http://openblox.hg.sourceforge.net/hgweb/openblox/openblox/archive/tip.tar.gz")


> **Carpentr said:**
> Nice work.

How long have you been programming in Python? I'm just curious. I've just started to learn Python 3 after taking a few programming classes for college.

Around 3 years, but I've been programming for almost 8 years.

---

### Post by JerBear64 on 2012-02-10
It's okay. We're all busy.

My uncle currently has my computer that has Ubuntu on it. He is performing repairs, such as replacing my faulty DVD-RW drive and reseating the memory. When I get my computer back, I'll download and let you know.

---

