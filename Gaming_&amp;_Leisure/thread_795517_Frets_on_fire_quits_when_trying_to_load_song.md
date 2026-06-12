---
title: "Frets on fire quits when trying to load song"
date: 2008-05-15
forum: Gaming &amp; Leisure
---

### Post by anfractuosities on 2008-05-15
Trying to play frets on fire.  The tutorial works fine, except the audio quits about 1/2 way through.  When ever I go to "play" the game it goes to the song selector and then quits...giving me 

Fatal Python error: (pygame parachute) Segmentation Fault

I have pygame installed which was someones suggestion for a similar problem.

---

### Post by anfractuosities on 2008-05-16
Weird thing is...I just kept trying to play and eventually It worked.  I even finished a song, and then it quit again, and hasnt worked since..

her is fretsonfire -v
```

(W) PyAmanith not found, SVG support disabled.
(D) Initializing audio.
(D) Audio configuration: (44100, -16, 1)
(D) Initializing video.
(D) Enabling high priority timer.
(D) 0 joysticks found.
(N) Loading Data.star1 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/star1.png' instead of '/usr/share/games/fretsonfire/data/star1.svg'.
(N) Loaded Data.star1 in 0.011 seconds
(N) Loading Data.star2 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/star2.png' instead of '/usr/share/games/fretsonfire/data/star2.svg'.
(N) Loaded Data.star2 in 0.007 seconds
(N) Loading Data.left synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/left.png' instead of '/usr/share/games/fretsonfire/data/left.svg'.
(N) Loaded Data.left in 0.001 seconds
(N) Loading Data.right synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/right.png' instead of '/usr/share/games/fretsonfire/data/right.svg'.
(N) Loaded Data.right in 0.001 seconds
(N) Loading Data.ball1 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/ball1.png' instead of '/usr/share/games/fretsonfire/data/ball1.svg'.
(N) Loaded Data.ball1 in 0.002 seconds
(N) Loading Data.ball2 synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/ball2.png' instead of '/usr/share/games/fretsonfire/data/ball2.svg'.
(N) Loaded Data.ball2 in 0.002 seconds
(N) Loading Data.loadingImage synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/loading.png' instead of '/usr/share/games/fretsonfire/data/loading.svg'.
(N) Loaded Data.loadingImage in 0.009 seconds
(N) Loading Data.font asynchronously
(N) Loading Data.bigFont asynchronously
(N) Loading Data.screwUpSounds asynchronously
(N) Loading Data.acceptSound asynchronously
(N) Loading Data.cancelSound asynchronously
(N) Loading Data.selectSound1 asynchronously
(N) Loading Data.selectSound2 asynchronously
(N) Loading Data.selectSound3 asynchronously
(N) Loading Data.startSound asynchronously
(D) Ready.
(N) Loading MainMenu.background synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/keyboard.png' instead of '/usr/share/games/fretsonfire/data/keyboard.svg'.
(N) Loaded MainMenu.background in 0.054 seconds
(N) Loading MainMenu.guy synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/pose.png' instead of '/usr/share/games/fretsonfire/data/pose.svg'.
(N) Loaded MainMenu.guy in 0.020 seconds
(N) Loading MainMenu.logo synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/logo.png' instead of '/usr/share/games/fretsonfire/data/logo.svg'.
(N) Loaded MainMenu.logo in 0.014 seconds
(W) Unable to enable psyco.
(N) Loaded Data.font in 0.000 seconds
(N) Loaded Data.bigFont in 0.000 seconds
(N) Loaded Data.acceptSound in 0.011 seconds
(N) Loaded Data.screwUpSounds in 0.069 seconds
(N) Loaded Data.selectSound1 in 0.006 seconds
(N) Loaded Data.cancelSound in 0.007 seconds
(N) Loaded Data.selectSound3 in 0.006 seconds
(N) Loaded Data.startSound in 0.012 seconds
(N) Loaded Data.selectSound2 in 0.016 seconds
(D) View: Push: MainMenu
(D) View: Push: Menu
(D) Starting server.
(N) Loading MainMenu.session synchronously
(D) Connecting to host 127.0.0.1.
(D) Session #1 connected.
(N) Loaded MainMenu.session in 0.001 seconds
(D) View: Pop all
(D) View: Pop: MainMenu
(D) View: Pop: Menu
(D) Connected as session #1.
(D) View: Pop: Menu
(D) View: Push: Lobby
(D) 1 phrases taught.
(D) 2 phrases taught.
(D) View: Pop: MainMenu
(D) Learned about World.CreatePlayer, 1 phrases now known.
(D) 1 phrases taught.
(D) Learned about World.StartGame, 2 phrases now known.
(D) Learned about World.PlayerJoined, 1 phrases now known.
(D) 2 phrases taught.
(D) 3 phrases taught.
(D) 4 phrases taught.
(D) 5 phrases taught.
(D) Learned about World.GameStarted, 2 phrases now known.
(D) View: Pop: Lobby
(D) Learned about World.SceneCreated, 3 phrases now known.
(D) Learned about World.EnterScene, 4 phrases now known.
(D) Learned about World.SceneEntered, 5 phrases now known.
(D) View: Push: SongChoosingSceneClient
(N) Loading SongChooser.libraries asynchronously
(N) Loaded SongChooser.libraries in 0.001 seconds
(N) Loading SongChooser.songs asynchronously
(N) Loaded SongChooser.songs in 0.003 seconds
(N) Loading SongChooser.cassette synchronously
(N) Loaded SongChooser.cassette in 0.222 seconds
(N) Loading SongChooser.label synchronously
(N) Loaded SongChooser.label in 0.024 seconds
(N) Loading SongChooser.libraryMesh synchronously
(N) Loaded SongChooser.libraryMesh in 0.055 seconds
(N) Loading SongChooser.libraryLabel synchronously
(N) Loaded SongChooser.libraryLabel in 0.011 seconds
(N) Loading SongChooser.background synchronously
(D) Loading cached bitmap '/usr/share/games/fretsonfire/data/cassette.png' instead of '/usr/share/games/fretsonfire/data/cassette.svg'.
(N) Loaded SongChooser.background in 0.012 seconds
(D) View: Push: SongChooser
(N) Loading SongChooser.None asynchronously
(W) Unable to load guitar track: matrices are not aligned for copy

Fatal Python error: (pygame parachute) Segmentation Fault
Aborted

```

and same when trying to adjust options
(abridged version)
```

(N) Restarting.
(W) PyAmanith not found, SVG support disabled.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
(D) Initializing audio.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
(W) Audio setup failed. Trying with default configuration.
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
Traceback (most recent call last):
  File "FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: u'/var/crash/_usr_share_games_fretsonfire_game_FretsOnFire.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 149, in __init__
    self.audio.open(frequency = frequency, bits = bits, stereo = stereo, bufferSize = bufferSize)
  File "/usr/share/games/fretsonfire/game/Audio.py", line 49, in open
    pygame.mixer.init()
pygame.error: No available audio device

```

---

### Post by jnuz on 2008-05-21
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20933&st=1240#entry217499](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST&f=11&t=20933&st=1240#entry217499)

check that out!

---

### Post by DoktorSeven on 2008-05-21
I haven't gotten that mod to work (keeps complaining about missing files), but if the original poster is using FoF 1.2.512, you need to go back down a version; that version is known to be very buggy and has the problems you talked about.

Go to [its Sourceforge page](http://sourceforge.net/projects/fretsonfire/) and get the 1.2.451 Linux version (FretsOnFire-1.2.451-linux.tar.gz), extract as a directory in your home directory and run the "FretsOnFire" binary.

(I use a launcher program like this:
```

#!/bin/bash
cd ~/FretsOnFire
./FretsOnFire

```

Depending on where you extract it, you may have to change the "cd" line, which specifies what directory it's in -- the ~ is a shortcut for your home directory.  Save this launcher somewhere, set it to be Executable, then point to it with a shortcut on your desktop or menu.)

---

### Post by iheartubuntu on 2008-05-21
Did you get the game from the repositories? I downloaded the linux version straight from the game website and it works great. I then decided to install it from the reps as well and notice the Ubuntu installed version has hardly any files in the folders compared to the version I downloaded off of the official Frets website.

---

### Post by ponchomx on 2008-11-11
```
sudo aptitude install numpy
```

---

