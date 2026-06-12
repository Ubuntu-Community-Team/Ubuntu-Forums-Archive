---
title: "frets on fire don't work"
date: 2009-07-26
forum: Gaming &amp; Leisure
---

### Post by ThaDoctor99 on 2009-07-26
Why is it that I wanted to play frets on fire, oh yeah comsidered buying guitar hero.
Well just wanted to see how it works.
But it do not work.
My problem is strange indeed.
The immediate problem is that it starts with some sound but then it closes again just before something comes to the screen (aka it goes black but goes back shortly before anything that looks like guitar heroes comes on.)
My problem is also clear as I do try to run from terminal I did not understand any of it.
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 312, in loading
    done = Engine.run(self)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 139, in run
    self._runTask(task)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 130, in _runTask
    task.run(ticks)
  File "/usr/share/games/fretsonfire/game/Resource.py", line 166, in run
    loader.finish()
  File "/usr/share/games/fretsonfire/game/Resource.py", line 68, in load
    self.result = self.function()
  File "/usr/share/games/fretsonfire/game/Data.py", line 72, in <lambda>
    font1     = lambda: Font(font,    fontSize[0], scale = scale, reversed = reversed, systemFont = not asciiOnly)
  File "/usr/share/games/fretsonfire/game/Font.py", line 48, in __init__
    self.font         = pygame.font.Font(fileName, size)
IOError: unable to read font filename
Exception in thread Thread-16 (most likely raised during interpreter shutdown):
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 486, in __bootstrap_inner
  File "/usr/share/games/fretsonfire/game/Resource.py", line 56, in run
  File "/usr/lib/python2.5/threading.py", line 331, in release
<type 'exceptions.AttributeError'>: 'NoneType' object has no attribute 'release'
Unhandled exception in thread started by <bound method Loader.__bootstrap of <Loader(Thread-16, started)>>
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
    from apport.packaging_impl import impl as packaging
ImportError: No module named apport.packaging_impl

Original exception was:
Traceback (most recent call last):
  File "/usr/lib/python2.5/threading.py", line 462, in __bootstrap
    self.__bootstrap_inner()
  File "/usr/lib/python2.5/threading.py", line 527, in __bootstrap_inner
    _active_limbo_lock.acquire()
AttributeError: 'NoneType' object has no attribute 'acquire'

that is the err msg.
What could help
I run ubuntu 8.04 LTS what should I do to upgrade as a side note.

---

### Post by Ericj1186 on 2009-07-26
Try Frets on Fire X - [http://code.google.com/p/fofix/](http://code.google.com/p/fofix/)

I couldn't get my PS3 Drums to register at all (it saw all of the pads as one controller), but the game works.

---

### Post by doorknob60 on 2009-07-27
> **Ericj1186 said:**
> Try Frets on Fire X - [http://code.google.com/p/fofix/](http://code.google.com/p/fofix/)

I couldn't get my PS3 Drums to register at all (it saw all of the pads as one controller), but the game works.

+1 It has some amazing features in there

---

### Post by ThaDoctor99 on 2009-07-27
It is sure worth a try.

---

### Post by ThaDoctor99 on 2009-07-27
That works only now I need some songs to play.

---

### Post by ThaDoctor99 on 2009-07-27
This would sure be funny, But I cant seem to get any songs recognized by this game. Think I am gonna let it rest for a minute and try later.

---

