---
title: "Frets On Fire from (repo and website) won't start"
date: 2008-07-26
forum: Gaming &amp; Leisure
---

### Post by SoftwareExplorer on 2008-07-26
I tried FoF from the website first and when I execute the script, nothing happens. Then I tried the one from the repository and when I click the button for it, nothing happens. I uninstalled the repository's version and tried running the website binary directly from the terminal, and it said ./FretsOnFire.bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory

TIA

EDIT:I'm pretty sure its something to do with sound, because after I installed FoF, I discovered sound didn't work, so I uninstalled the repository version and restarted and sound worked again. I tried running the website version again with -v and it said 

ALSA lib pcm_dmix.c:874: (snd_pcm_dmix_open) unable to open slave
(D) Initializing audio.
ALSA lib pcm_dmix.c:874:  (snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:  (snd_pcm_dmix_open) unable to open slave
(W) Audio setup failed. Trying with default configuration.
ALSA lib pcm_dmix.c:874:  (snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 68, in ?
  File "src/GameEngine.py", line 149, in __init__
  File "src/Audio.py", line 49, in open
pygame.error: No available audio device

---

### Post by Orlsend on 2008-07-26
I also have problems with FoF, except I can get it running but it wont load the real songs only the tutorial....

Dont worry you are not the only one with problems with this game..

---

### Post by SoftwareExplorer on 2008-07-28
I figured it out! The answer to this problem:
under 2-B, Issues when running
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=26005;hl=ubuntu]("http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=26005;hl=ubuntu")

And also here:
(I searched with Ubuntuforums' search tool but didn't see this, then used Google and found it after I solved the problem)

[http://ubuntuforums.org/showthread.php?t=779216](http://ubuntuforums.org/showthread.php?t=779216)

Basically it says to try running it by typing

```
pasuspender fretsonfire

```
to run the repo version and 
```
pasuspender ./fretsonfire
```
from the directory that FoF is in for the website version.

I hope this helps someone.:)

Now, if I could just figure out how to thank myself for this post...:)

---

### Post by benjaminjames on 2008-07-28
ok i had the same issue so i used pa suspender and it was working fine for about 5 mins and then it crashed and i got this message in the terminal '^[OQFatal Python error: (pygame parachute) Segmentation Fault
Aborted' wtf does that mean i havent a clue can anyone help

---

### Post by benjaminjames on 2008-07-29
anyone??????????

---

### Post by Orlsend on 2008-07-29
Still wont work.....

> paez@paez-laptop:~$ pasuspender fretsonfire
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 338, in main
    done = Engine.run(self)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 139, in run
    self._runTask(task)
  File "/usr/share/games/fretsonfire/game/Engine.py", line 130, in _runTask
    task.run(ticks)
  File "/usr/share/games/fretsonfire/game/Resource.py", line 166, in run
    loader.finish()
  File "/usr/share/games/fretsonfire/game/Resource.py", line 85, in finish
    self.onLoad(self.result)
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 383, in songListLoaded
    self.updateSelection()
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 418, in updateSelection
    self.selectedItem  = self.items[self.selectedIndex]
IndexError: list index out of range
Traceback (most recent call last):
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
    return self.mainloop()
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 340, in main
    self.view.render()
  File "/usr/share/games/fretsonfire/game/View.py", line 183, in render
    layer.render(self.visibility[layer], layer == self.layers[-1])
  File "/usr/share/games/fretsonfire/game/Dialogs.py", line 696, in render
    item  = self.items[self.selectedIndex]
IndexError: list index out of range


---

### Post by benjaminjames on 2008-08-01
Bump

---

### Post by SoftwareExplorer on 2008-08-01
> paez@paez-laptop:~$ pasuspender fretsonfire
Traceback (most recent call last):
File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
return self.mainloop()
File "/usr/share/games/fretsonfire/game/GameEngine.py", line 338, in main
done = Engine.run(self)
File "/usr/share/games/fretsonfire/game/Engine.py", line 139, in run
self._runTask(task)
File "/usr/share/games/fretsonfire/game/Engine.py", line 130, in _runTask
task.run(ticks)
File "/usr/share/games/fretsonfire/game/Resource.py", line 166, in run
loader.finish()
File "/usr/share/games/fretsonfire/game/Resource.py", line 85, in finish
self.onLoad(self.result)
File "/usr/share/games/fretsonfire/game/Dialogs.py", line 383, in songListLoaded
self.updateSelection()
File "/usr/share/games/fretsonfire/game/Dialogs.py", line 418, in updateSelection
self.selectedItem = self.items[self.selectedIndex]
IndexError: list index out of range
Traceback (most recent call last):
File "/usr/share/games/fretsonfire/game/GameEngine.py", line 348, in run
return self.mainloop()
File "/usr/share/games/fretsonfire/game/GameEngine.py", line 340, in main
self.view.render()
File "/usr/share/games/fretsonfire/game/View.py", line 183, in render
layer.render(self.visibility[layer], layer == self.layers[-1])
File "/usr/share/games/fretsonfire/game/Dialogs.py", line 696, in render
item = self.items[self.selectedIndex]
IndexError: list index out of range

Maybe try using the website version, because the repository version tells me that too, but the website one doesn't seem to have this problem on my computer.

---

