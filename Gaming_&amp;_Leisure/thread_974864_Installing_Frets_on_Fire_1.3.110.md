---
title: "Installing Frets on Fire 1.3.110"
date: 2008-11-07
forum: Gaming &amp; Leisure
---

### Post by lexen on 2008-11-07
Hey guys, I recently found out that [_frets on fire_]("http://fretsonfire.sourceforge.net/") updated.  I can usually get it to work just from the source, but I am having a hard time with the new version.  I saw that there were some dependencies, so I installed them one at a time.  They can all be installed at once with this command:

```
sudo apt-get install python-pygame python-opengl python-numpy python-psyco
```

The problem is that I can't run the game with this camand like they tell me.

```
python '/home/lexen/fretsonfire/src/FretsOnFire.py' 
```

If you wanted to try that, you would have to change the location.  There is a setup.py, but when I try to run that, the cursor changes, but nothing else happens.  When I click anywhere, the cursor changes back.

So, when I try the above command, I get this error.

```
Traceback (most recent call last):
  File "/home/lexen/fretsonfire/src/FretsOnFire.py", line 74, in <module>
    engine = GameEngine(config)
  File "/home/lexen/fretsonfire/src/GameEngine.py", line 192, in __init__
    self.data = Data(self.resource, self.svg)
  File "/home/lexen/fretsonfire/src/Data.py", line 48, in __init__
    self.loadSvgDrawing(self, "star1",   "star1.svg", textureSize = (128, 128))
  File "/home/lexen/fretsonfire/src/Data.py", line 106, in loadSvgDrawing
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/home/lexen/fretsonfire/src/Resource.py", line 157, in load
    return l.finish()
  File "/home/lexen/fretsonfire/src/Resource.py", line 68, in load
    self.result = self.function()
  File "/home/lexen/fretsonfire/src/Data.py", line 106, in <lambda>
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/home/lexen/fretsonfire/src/Svg.py", line 559, in __init__
    self.svgData = open(svgData).read()
IOError: [Errno 2] No such file or directory: '../data/star1.svg'
```

Has anyone gotten it to work?


Thanks,
Lexen

---

### Post by mrtisoy on 2008-11-08
I'm installing on an amd64 Ubuntu 8.04. I tried following several forum threads to get many different flavors of FOF working, to no avail. Finally I tried downloading 1.3.110 directly from ForgeSource. The first time I tried running the script it failed and complained about numpy. I checked synaptic but it said that I had it installed. Just for kicks I apt-got python-numpy and it installed a couple of libraries (libblas3gf liblapack3gf). Now it works!

---

### Post by lexen on 2008-11-09
Okay... can you walk me threw the process... in great detail.

---

### Post by cronosh2o on 2009-06-13
I had the same problem, but I could doing this:

```
cd ~/fretsonfire/src
```

And now, run the game as usual:

```
python FretsOnFire.py
```

Note: I'm sure you already made this, but I wrote this for the records. ;)

---

### Post by lexen on 2009-06-13
Thanks.  Yeah, I did figure it out, but your right, it's good to say how we got it to work for the record.  Nowadays I am playing Frets on Fire X, which is commonly known as [fofix]("http://code.google.com/p/fofix/").  You should check it out, they have added a lot of features.

---

### Post by steelxenon on 2010-08-07
mine works when I just open the folder and double click the icon (or the same thing as cd and execute in terminal) but I just can't figure out what to put in the command line to add a nice clean main menu entry for it :/

---

