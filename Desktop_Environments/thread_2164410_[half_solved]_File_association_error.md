---
title: "[half solved] File association error"
date: 2013-07-31
forum: Desktop Environments
---

### Post by Pyov. on 2013-07-31
Hi,
I'm using 13.04. Python3.2 and IDLE work find.
First, i want to associate Python file (ex: file.py) with IDLE. Right click on the file, then "Open with" and "Other application".
Recommended application are: "Run Software" and "gedit". "Run Software" do nothing, but no error message…
-Trying "Show other application" do not list IDLE
-Trying "Find applications online" stop with message:

Failed to look for applications online
GDBus.Error:org.freedesktop.DBus.Python.xdg.Exceptions.ParsingError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/sessioninstaller/core.py", line 1030, in _install_mime_types
    path))
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 33, in __init__
    self.parse(filename)
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 42, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.7/dist-packages/xdg/IniFile.py", line 81, in parse
    raise ParsingError("Invalid line: " + line, filename)
ParsingError: ParsingError in file '/usr/share/app-install/desktop/workrave:workrave.desktop', Invalid line: - RSI (Repetitive Strain Injury) oraz wspomaga rekonwalescencj\u0119

Well… Trying same thing with other files give the same result.

Is someone has an simple idea to solve that problem?
Thanks in advance! :-)

Pyov

---

### Post by Morbius1 on 2013-07-31
If you do a lot of file asociations you might want to go back to the future and install XFCE's file manager:
```
sudo apt-get install thunar
```
Open thunar and go to a *.py file then Right Click > Open With Other Application and you will get something like this:
[ATTACH=CONFIG]244946[/ATTACH]
At the bottom you will notice the "Use a custom command" box. I don't know if that is the correct path for IDLE so change it to the correct one. Check the "Use as default for this kind of file" if you want it to launch with a double click. 

You don't have to use thunar after this is done it should work with Nautilus or anywhere else as well.

---

### Post by Pyov. on 2013-07-31
Hi,
Very easy to do and it works well (and on Nautilus)!
Have you got any idea about the Nautilus problem (i let the thread unsolve for that)?

Thank you very much Morbius1!! 
Pyo

---

### Post by mc4man on 2013-07-31
Pretty simple to fix, just package maintainer negligence. 
For apps to show in the context  open with menus the Exec= line in the app's .desktop must end in %<a letter>
Common letters are f, F, u & U
Generally I either use f or U
(this is nothing new, you'd think maintainers would catch on..

So to fix open /usr/share/applications/idle.desktop or /usr/share/applications/idle3.desktop in a root text editor & add - Ex.
```
Exec=/usr/bin/idle %f
```
See screens

---

### Post by Morbius1 on 2013-08-01
The "use a custom command" option can be used to fix all sorts of problems. For example, ever wonder why the system insists that a jar file be marked as executable before it will run? It's because of something called cautious-launcher that Ubuntu uses as a roadblock to not only *.jar but *.exe files for those who use Wine. You can fix it for jar files by using a custom command ( java -jar ).

The "use a custom command" option was removed from Gnome since it appears anytime the Gnome developers touch code they tend to remove function. I don't know if it's because of high levels of lead or mercury in the water where they work or because they all buy into Gnome's Orwellian motto: "If we reduce function the desktop becomes more functional"

---

### Post by Pyov. on 2013-08-02
Hi,
@mc4man: I've try your solution and it works fine! (In fact "Exec=/usr/bin/idle" was already there, I just add "%f"! Thank you for your solution!!!
@Morbius: Nice! :-)
But the problem's still there! I mean that the crash and message are still there for other applications, no?
Well, in fact, not a big problem with your solutions!
Thank you very much for your solutions!!
Pyo

---

