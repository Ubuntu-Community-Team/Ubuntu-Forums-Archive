---
title: "Pysolfc Not Loading Afer Latest System Update"
date: 2024-06-06
forum: Gaming &amp; Leisure
---

### Post by Mark76 on 2024-06-06
> pysolfc
Traceback (most recent call last):
  File "/usr/games/pysolfc", line 36, in <module>
    from pysollib.main import main  # noqa: E402,I202
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/share/games/pysolfc/pysollib/main.py", line 30, in <module>
    from pysollib.app import Application
  File "/usr/share/games/pysolfc/pysollib/app.py", line 31, in <module>
    from pysollib.gamedb import GAME_DB, GI, loadGame
  File "/usr/share/games/pysolfc/pysollib/gamedb.py", line 25, in <module>
    import imp
ModuleNotFoundError: No module named 'imp'

:-s

---

### Post by currentshaft on 2024-06-06
What "system update"?

What have you already tried to debug this?

Have you followed any instructions in [https://github.com/shlomif/PySolFC](https://github.com/shlomif/PySolFC)?

---

### Post by Mark76 on 2024-06-06
To 24.04,  Happened yesterday.

---

### Post by #&amp;thj^% on 2024-06-06
Mark76, I got so tired of breakage with it I simply removed it and installed "kpat".
Full Card Solitaire suite, but you may not be as happy with it as I am.

Pysolfc is dependent on python3 and what I've seen currently you will need to downgrade to python3.9. 9 and pillow. and we are on 
```
python3 --version
Python 3.12.3

```
I wish Debian would just pull it from the repos, they don't maintain it well at all.

---

