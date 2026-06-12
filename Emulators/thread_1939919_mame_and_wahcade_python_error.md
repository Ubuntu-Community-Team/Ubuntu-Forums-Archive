---
title: "mame and wahcade python error"
date: 2012-03-12
forum: Emulators
---

### Post by eternal_sage on 2012-03-12
i followed [this guide]("http://ubuntuforums.org/showthread.php?p=11755682") with a little help from [here]("http://www.anti-particle.com/wahcade_quick.shtml") as well. everything seems fine, but when i start wahcade from terminal everything comes up as if it is fine but i get a window with this message. running this on ubuntu 11.10 64 bit if that matters, with the setup files that are found [here]("http://sdlmame.wallyweek.org/"). thanks in advance!

```
Traceback (most recent call last):
  File "wahcade.py", line 81, in <module>
    app = WinMain(options)
  File "/usr/local/share/games/wahcade/win_main.py", line 300, in __init__
    self.load_emulator()
  File "/usr/local/share/games/wahcade/win_main.py", line 1078, in load_emulator
    self.load_list()
  File "/usr/local/share/games/wahcade/win_main.py", line 1121, in load_list
    self.pop_games_list()
  File "/usr/local/share/games/wahcade/win_main.py", line 1384, in pop_games_list
    self.emu_ini)
  File "/usr/local/share/games/wahcade/filters.py", line 369, in create_initial_filter
    gd = mi.next()
  File "/usr/local/share/games/wahcade/filters.py", line 271, in get_xml_game_item
    d['controller_type'] = _controllers[ctrl.attrib['type']]
KeyError: 'joy'

```

---

### Post by junglist313 on 2012-11-29
Looks like a problem with the joystick, it's either looking for one that's not there or it's configured wrong. Can you post your config file?

---

