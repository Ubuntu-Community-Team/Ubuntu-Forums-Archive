---
title: "Katrain 1.9.3, Terminal not responding to commands to compile"
date: 2023-08-22
forum: Gaming &amp; Leisure
---

### Post by SciGuy1872 on 2023-08-22
Hi.  I have Katrain 1.14 installed but want to replace it with 1.9 because there are no sounds in the current program.  If others have an idea I can try with 1.14 to get the sound working, I'd be glad to know it; I haven't had sound since upgrading the OS from 20.04--I currently have 22.04.  The following output is from the pip3 list command.

```
Package                 Version
----------------------- --------------
apt-xapian-index        0.49
apturl                  0.5.2
ayatana-settings        21.1.28
bcrypt                  3.2.0
beautifulsoup4          4.10.0
blinker                 1.4
Brlapi                  0.8.3
cajarename              21.11.24
certifi                 2020.6.20
chardet                 4.0.0
click                   8.0.3
colorama                0.4.4
command-not-found       0.3
configobj               5.0.6
cryptography            3.4.8
cupshelpers             1.0
dbus-python             1.2.18
defer                   1.0.6
distro                  1.7.0
distro-info             1.1build1
docutils                0.19
duplicity               0.8.21
fasteners               0.14.1
ffpyplayer              4.5.0
folder-color-caja       0.0.86
folder-color-common     0.0.86
future                  0.18.2
gpg                     1.16.0-unknown
httplib2                0.20.2
idna                    3.3
importlib-metadata      4.6.4
jeepney                 0.7.1
KaTrain                 1.12.3
keyring                 23.5.0
Kivy                    2.1.0
Kivy-Garden             0.1.5
kivymd                  0.104.1
language-selector       0.1
launchpadlib            1.10.16
lazr.restfulclient      0.14.4
lazr.uri                1.0.6
lockfile                0.12.2
louis                   3.20.0
lxml                    4.8.0
Magnus                  1.0.3
mate-hud                22.4.4
mate-menu               22.4.1
mate-tweak              22.4.8
meteo_qt                2.1
monotonic               1.6
more-itertools          8.10.0
netifaces               0.11.0
oauthlib                3.2.0
olefile                 0.46
onboard                 1.4.1
paramiko                2.9.3
pexpect                 4.8.0
Pillow                  9.0.1
pip                     22.0.2
psutil                  5.9.0
ptyprocess              0.7.0
pulsemixer              1.5.1
pycairo                 1.20.1
pycryptodomex           3.11.0
pycups                  2.0.1
Pygments                2.14.0
PyGObject               3.42.1
PyJWT                   2.3.0
PyNaCl                  1.5.0
pyparsing               2.4.7
PyQt5                   5.15.6
PyQt5-sip               12.9.1
python-apt              2.4.0+ubuntu1
python-dateutil         2.8.1
python-debian           0.1.43ubuntu1
python-xlib             0.29
pyxattr                 0.7.2
pyxdg                   0.27
PyYAML                  5.4.1
reportlab               3.6.8
requests                2.25.1
screen-resolution-extra 0.0.0
screeninfo              0.8.1
SecretStorage           3.3.1
setproctitle            1.2.2
setuptools              59.6.0
six                     1.16.0
soupsieve               2.3.1
systemd-python          234
ubuntu-advantage-tools  8001
ubuntu-drivers-common   0.0.0
ufw                     0.36.1
unattended-upgrades     0.1
urllib3                 1.26.5
variety                 0.8.5
vboxapi                 1.0
wadllib                 1.3.6
wheel                   0.37.1
xdg                     5
xkit                    0.0.0
youtube-dl              2021.12.17
zipp                    1.0.0
```

From Github I can download a tarball and a zip, and I have tried to install the file, but I tried to enter the command ./configure, but it didn't work for some reason.  Everything with Katrain is good--it's just the sound.  I have speakers through my screen, using an hdmi connection that shows two audio streams name "main _.py audio stream", with a slider that is light color to show it is active for Katrain.

---

### Post by Xian on 2023-08-22
Can you perhaps mention at what step from the install file you have an issue?

[https://github.com/sanderland/katrain/blob/master/INSTALL.md](https://github.com/sanderland/katrain/blob/master/INSTALL.md)

---

### Post by SciGuy1872 on 2023-08-23
I'm entering commands according to an article about installing from either a [zip]("https://ubiq.co/tech-blog/install-zip-file-linux/") or [tar.gz]("https://www.itprotoday.com/development-techniques-and-management/how-install-targz-file-ubuntu-linux"). I can't use the "pip3 install -u katrain" because I just want version 1.9 (or however I can get the sound working), instead of the newest. The screenshots show one entry for both the zip and the tar.gz (I figured if one didn't work, the other, following separate directions, would (the unzip command versus the gui).  As you can see, I'm not having luck with the first step--the ./configure command; I navigated into the directory created by the uncompressing.

---

### Post by SciGuy1872 on 2023-08-23
Here is the info from the Readme file--I don't think it helps me much.

---

### Post by SciGuy1872 on 2023-08-23
I clicked on the link provided and saw the commands to try to fix the no sound issue, but now katrain does not start. 
> In case the sound is not working, or there is no available wheel for your OS or Python version, try building kivy locally using:

 pip3 uninstall kivy
pip3 install kivy --no-binary kivy     

You can now start KaTrain by running python3 -m katrain

  

Here is the log with the debugging option activated. 

```
[INFO   ] Logger: Record log in /home/anthony/.kivy/logs/kivy_23-08-23_14.txt
[INFO   ] Kivy: v2.2.1
[INFO   ] Kivy: Installed at "/home/anthony/.local/lib/python3.10/site-packages/kivy/__init__.py"
[INFO   ] Python: v3.10.12 (main, Jun 11 2023, 05:26:28) [GCC 11.4.0]
[INFO   ] Python: Interpreter at "/usr/bin/python3"
[INFO   ] Logger: Purge log fired. Processing...
[INFO   ] Logger: Purge finished!
[INFO   ] Factory: 190 symbols loaded
[DEBUG  ] Cache: register <kv.resourcefind> with limit=None, timeout=60
[DEBUG  ] Cache: register <kv.lang> with limit=None, timeout=None
[DEBUG  ] Cache: register <kv.image> with limit=None, timeout=60
[DEBUG  ] Cache: register <kv.atlas> with limit=None, timeout=None
[INFO   ] ImageLoaderFFPy: Using ffpyplayer 4.5.0
[INFO   ] Image: Providers: img_tex, img_dds, img_pil, img_ffpyplayer (img_pygame ignored)
[DEBUG  ] Cache: register <kv.texture> with limit=1000, timeout=60
[DEBUG  ] Cache: register <kv.shader> with limit=1000, timeout=3600
[DEBUG  ] Cache: register <kv.graphics.texture> with limit=None, timeout=None
[INFO   ] Clipboard: Provider: gtk3(['clipboard_xclip', 'clipboard_xsel', 'clipboard_dbusklipper'] ignored)
[CRITICAL] Cutbuffer: Unable to find any valuable Cutbuffer provider. Please enable debug logging (e.g. add -d if running from the command line, or change the log level in the config) and re-run your app to identify potential causes
xclip - FileNotFoundError: [Errno 2] No such file or directory: 'xclip'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1006, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 688, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 883, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/clipboard/clipboard_xclip.py", line 17, in <module>
    p = subprocess.Popen(['xclip', '-version'], stdout=subprocess.PIPE,
  File "/usr/lib/python3.10/subprocess.py", line 971, in __init__
    self._execute_child(args, executable, preexec_fn, close_fds,
  File "/usr/lib/python3.10/subprocess.py", line 1863, in _execute_child
    raise child_exception_type(errno_num, err_msg, err_filename)

xsel - FileNotFoundError: [Errno 2] No such file or directory: 'xsel'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1006, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 688, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 883, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/clipboard/clipboard_xsel.py", line 16, in <module>
    p = subprocess.Popen(['xsel'], stdout=subprocess.PIPE)
  File "/usr/lib/python3.10/subprocess.py", line 971, in __init__
    self._execute_child(args, executable, preexec_fn, close_fds,
  File "/usr/lib/python3.10/subprocess.py", line 1863, in _execute_child
    raise child_exception_type(errno_num, err_msg, err_filename)

[DEBUG  ] Text: Ignored <pygame> (import error)
[DEBUG  ] STREAM b'IHDR' 16 13
[DEBUG  ] STREAM b'IDAT' 41 1216
[INFO   ] Text: Provider: pil(['text_pygame'] ignored)
[DEBUG  ] Window: Ignored <pygame> (import error)
[DEBUG  ] Window: Ignored <x11> (import error)
[CRITICAL] Window: Unable to find any valuable Window provider. Please enable debug logging (e.g. add -d if running from the command line, or change the log level in the config) and re-run your app to identify potential causes
pygame - ModuleNotFoundError: No module named 'pygame'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1006, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 688, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 883, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/window/window_pygame.py", line 13, in <module>
    import pygame

x11 - ModuleNotFoundError: No module named 'kivy.core.window.window_x11'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1004, in _find_and_load_unlocked

[INFO   ] KivyMD: v0.104.1
[CRITICAL] App: Unable to get a Window, abort.
```

---

### Post by Xian on 2023-08-23
A user's similar error report:: [https://stackoverflow.com/questions/45529794/x11-importerror-no-module-named-kivy-core-window-window-x11/61448189#61448189](https://stackoverflow.com/questions/45529794/x11-importerror-no-module-named-kivy-core-window-window-x11/61448189#61448189)

---

### Post by SciGuy1872 on 2023-08-23
I followed the steps from the linked page and have copied the debug file contents; I am unsure what to do to get the game working.  Is there a way to erase it so that I just have to type "pip3 install -U katrain" as the Github page says?

```
INFO   ] Logger: Record log in /home/anthony/.kivy/logs/kivy_23-08-23_8.txt
[INFO   ] Kivy: v2.2.1
[INFO   ] Kivy: Installed at "/home/anthony/.local/lib/python3.10/site-packages/kivy/__init__.py"
[INFO   ] Python: v3.10.12 (main, Jun 11 2023, 05:26:28) [GCC 11.4.0]
[INFO   ] Python: Interpreter at "/usr/bin/python3"
[INFO   ] Logger: Purge log fired. Processing...
[INFO   ] Logger: Purge finished!
[INFO   ] Factory: 190 symbols loaded
[DEBUG  ] Cache: register <kv.resourcefind> with limit=None, timeout=60
[DEBUG  ] Cache: register <kv.lang> with limit=None, timeout=None
[DEBUG  ] Cache: register <kv.image> with limit=None, timeout=60
[DEBUG  ] Cache: register <kv.atlas> with limit=None, timeout=None
[INFO   ] ImageLoaderFFPy: Using ffpyplayer 4.5.0
[INFO   ] Image: Providers: img_tex, img_dds, img_pil, img_ffpyplayer (img_pygame ignored)
[DEBUG  ] Cache: register <kv.texture> with limit=1000, timeout=60
[DEBUG  ] Cache: register <kv.shader> with limit=1000, timeout=3600
[DEBUG  ] Cache: register <kv.graphics.texture> with limit=None, timeout=None
[INFO   ] Clipboard: Provider: xclip
[INFO   ] CutBuffer: cut buffer support enabled
[DEBUG  ] Text: Ignored <pygame> (import error)
[DEBUG  ] STREAM b'IHDR' 16 13
[DEBUG  ] STREAM b'IDAT' 41 1216
[INFO   ] Text: Provider: pil(['text_pygame'] ignored)
[DEBUG  ] Window: Ignored <pygame> (import error)
[CRITICAL] Window: Unable to find any valuable Window provider. Please enable debug logging (e.g. add -d if running from the command line, or change the log level in the config) and re-run your app to identify potential causes
pygame - ModuleNotFoundError: No module named 'pygame'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1006, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 688, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 883, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/window/window_pygame.py", line 13, in <module>
    import pygame

x11 - AttributeError: module 'kivy.core.window.window_info' has no attribute 'WindowInfoX11'
  File "/home/anthony/.local/lib/python3.10/site-packages/kivy/core/__init__.py", line 59, in core_select_lib
    mod = importlib.__import__(name='{2}.{0}.{1}'.format(
  File "<frozen importlib._bootstrap>", line 1129, in __import__
  File "<frozen importlib._bootstrap>", line 1050, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1027, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1006, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 688, in _load_unlocked
  File "<frozen importlib._bootstrap_external>", line 1184, in exec_module
  File "<frozen importlib._bootstrap>", line 241, in _call_with_frames_removed
  File "kivy/core/window/window_x11.pyx", line 1, in init kivy.core.window.window_x11

[INFO   ] KivyMD: v0.104.1
[CRITICAL] App: Unable to get a Window, abort.


```

---

### Post by SciGuy1872 on 2023-08-24
I got the game working.  What worked for me were the commands "pip install pygame" and then uninstalling and reinstalling kivy with "pip uninstall kivy", then "pip install kivy"

---

