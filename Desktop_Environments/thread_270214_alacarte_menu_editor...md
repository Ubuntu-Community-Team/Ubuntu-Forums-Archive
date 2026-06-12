---
title: "alacarte menu editor.."
date: 2006-10-02
forum: Desktop Environments
---

### Post by markster23 on 2006-10-02
hey.. im a bit of a newb, and i don't know why but my alacarte menu editor won't open... i tried logging out of gnome, and back in and no cigar... i'm just wondering what the cause could possibly be.. like i said im a newb and i dont know much about debugging it.. anyone help ??

mark ](*,)

---

### Post by pay on 2006-10-02
Open up the terminal and type in alacarte and tell us what errors occur so we can help you. Besides Alacarte isn't essential as you can and applications to the Gnome menu by hand. Eg ```
gksudo gedit /usr/share/applications/dvdrip.desktop

```and then type```
[Desktop Entry]
Name=dvd::rip 
Comment=dvd::rip
Exec=dvdrip
Icon=/usr/share/perl5/Video/DVDRip/icon.xpm
Terminal=false
Type=Application
Categories=Application;AudioVideo;
```which would then add the app dvd::rip

---

### Post by markster23 on 2006-10-02
hey, this is what comes up when i try to run it from console...

```
    __parseTheme(os.path.join(dir,theme, "index.theme"))
  File "/usr/lib/python2.4/site-packages/xdg/IconTheme.py", line 315, in __parseTheme
    __addTheme(subtheme)
  File "/usr/lib/python2.4/site-packages/xdg/IconTheme.py", line 301, in __addTheme
    __parseTheme(os.path.join(dir,theme, "index.theme"))
  File "/usr/lib/python2.4/site-packages/xdg/IconTheme.py", line 314, in __parseTheme
    for subtheme in theme.getInherits():
  File "/usr/lib/python2.4/site-packages/xdg/IconTheme.py", line 36, in getInherits
    return self.get('Inherits', list=True)
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 108, in get
    values = self.getList(value)
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 143, in getList
    if re.search(r"(?<!\\)\;", string):
  File "/usr/lib/python2.4/sre.py", line 134, in search
    return _compile(pattern, flags).search(string)
  File "/usr/lib/python2.4/sre.py", line 222, in _compile
    if not sre_compile.isstring(pattern):
RuntimeError: maximum recursion depth exceeded
root@molly-desktop:~#

```

---

### Post by JamesVeDe on 2006-10-02
I gave all the Google available threads a shot.

Latest : 
sudo apt-get remove clvm -f 

Yields:
E: could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)

---

### Post by markster23 on 2006-10-04
anybody ??

---

