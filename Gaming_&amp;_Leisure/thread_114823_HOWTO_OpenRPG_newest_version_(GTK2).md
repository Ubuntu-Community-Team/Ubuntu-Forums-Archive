---
title: "HOWTO: OpenRPG newest version (GTK2)"
date: 2006-01-09
forum: Gaming &amp; Leisure
---

### Post by leech on 2006-01-09
Here's what I did;

1 ) sudo apt-get install openrpg
2 ) sudo -s (this will basically put you as root user, you could probably just use sudo)
3 ) /usr/games/openrpg-client (you have to use the full path, since /usr/games is not in the root user's path).
4 ) Upgrade the client by using /update get (on their forum it says to change the URL, but I didn't have to)
5 ) sudo apt-get install python-wxgtk2.6
6 ) Download [http://openrpg.wrathof.com/OpenRPGd.zip](http://openrpg.wrathof.com/OpenRPGd.zip) and exctract it to /tmp or whevever you want.
7 ) (with still being sudo, from a terminal just run cp -r /tmp/openrpg1/* /usr/share/openrpg/
8 ) chmod -R 777 /usr/share/openrpg/myfiles
9 ) exit sudo -s by using control+D or exit.
10 ) now run openrpg-client from the terminal.

When you run the client, the splash screen will show, and sit there... you need to click on the spash screen and then the program will load.  Even after you close the program, python is still loaded, so you may want to kill that too, though I don't think it hurts anything.  

Leech

---

### Post by nalmeth on 2006-01-09
cool, thanks for posting this howto. I've never heard of it though. I think I will try it.

---

### Post by meborc on 2006-01-10
got it running now... under breezy... :D ... lets try it out

---

### Post by psoleko on 2006-03-29
Thanks very much for this howto leech. I can confirm it works under Dapper. I just searched for anything on OpenRPG, glad to see some others using it. Until I found this I had been painfully using the Windows version, as I could not figure out the python shenanigans. Thanks again for keeping me from rebooting.

---

### Post by yarri on 2006-09-07
Hi!

I have a problem with OpenRPG. I have installed it from repositories together with python-wxgtk2.6. Unfortunatelly when it starts I see only splash screen and output in the console is:

openrpg-client
/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wxPython/lib/splashscreen.py:5: DeprecationWarning: \

#####################################################\
# THIS MODULE IS NOW DEPRECATED                      |
#                                                    |
# The core wx library now contains an implementation |
# of the 'real' wx.SpashScreen.                      |
#####################################################/


  import wx.lib.splashscreen
/usr/lib/python2.4/whrandom.py:38: DeprecationWarning: the whrandom module is deprecated; please use the random module
  DeprecationWarning)

Traceback (most recent call last):
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py", line 111, in OnMouseClick
    self.timer.Notify()
  File "/usr/share/openrpg/orpg/main.py", line 1037, in AfterSplash
    self.frame = orpgFrame(NULL, -1, "OpenRPG v"+VERSION)
  File "/usr/share/openrpg/orpg/main.py", line 255, in __init__
    self.settings = orpg.tools.orpg_settings.settings()
  File "/usr/share/openrpg/orpg/tools/orpg_settings.py", line 265, in __init__
    while(index<len(sys.argv)-1):
NameError: global name 'sys' is not defined

Program in not starting with sudo as well.
Do you have any idea what could be the reason? 

Best regards
               Yarri

---

### Post by SilasleCake on 2006-12-06
I am having a problem every time I try to run "openrpg-client".

Here is the error code:
```
root@VZ-E-laptop:/usr/share/openrpg# /usr/games/openrpg-client
Rooting OpenRPG at: /usr/share/openrpg
Traceback (most recent call last):
  File "/usr/share/openrpg/start.py", line 8, in ?
    import orpg.main
  File "/usr/share/openrpg/orpg/main.py", line 44, in ?
    import orpg.tools.PyAUI
  File "/usr/share/openrpg/orpg/tools/PyAUI.py", line 224, in ?
    raise "\nSorry: I Still Don't Know How To Work On GTK/MAC Platforms... " \

Sorry: I Still Don't Know How To Work On GTK/MAC Platforms... Please Download The Latest wxPython Version.
```

Hope you can help.

By the way, I have python-wxgtk2.6 installed.

---

### Post by da Wookiee on 2007-05-22
> **leech said:**
> Here's what I did;


4 ) Upgrade the client by using /update get (on their forum it says to change the URL, but I didn't have to)

Leech

I don't understand what I'm supposed to do on this step.  

If it helps when I run openrpg-client I get:



/usr/share/openrpg/orpg/plugins.py:1: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
Rooting OpenRPG at: /usr/share/openrpg
[WARNING] Could not create approot file.
[WARNING] Automatic directory resolution not configured.
Traceback (most recent call last):
  File "./start.py", line 6, in <module>
    import orpg.main
  File "/usr/share/openrpg/orpg/main.py", line 35, in <module>
    from orpg.orpg_windows import *
  File "/usr/share/openrpg/orpg/orpg_windows.py", line 43, in <module>
    from wxPython.html import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/html.py", line 151, in <module>
    wxHtmlWindowEvent = wx.html.HtmlWindowEvent
AttributeError: 'module' object has no attribute 'HtmlWindowEvent'

---

### Post by basotl on 2007-12-19
I am having a similar issue.

```
/usr/share/openrpg/orpg/plugins.py:1: DeprecationWarning: The wxPython compatibility package is no longer automatically generated or actively maintained.  Please switch to the wx package as soon as possible.
  from wxPython.wx import *
Rooting OpenRPG at: /usr/share/openrpg
Traceback (most recent call last):
  File "./start.py", line 6, in <module>
    import orpg.main
  File "/usr/share/openrpg/orpg/main.py", line 35, in <module>
    from orpg.orpg_windows import *
  File "/usr/share/openrpg/orpg/orpg_windows.py", line 43, in <module>
    from wxPython.html import *
  File "/usr/lib/python2.5/site-packages/wx-2.8-gtk2-unicode/wxPython/html.py", line 151, in <module>
    wxHtmlWindowEvent = wx.html.HtmlWindowEvent
AttributeError: 'module' object has no attribute 'HtmlWindowEvent'

```

Has anyone found a way to fix this? I've been trying at it and I know I must be missing something simple.

---

### Post by basotl on 2007-12-19
I just had to use the more up to date package from the [unofficial download site]("http://openrpg.digitalxero.net/wiki/").

I guess the issue was addressed but the package at Sourceforge hasn't been updated.

---

### Post by opakedragon on 2008-01-15
So I've installed OpenRPG it works fine but thats only when I use sudo and this is the output that the terminal gives (since you need to run it from terminal) if I don't use sudo:
```
Rooting OpenRPG at: /usr/share/openrpg
[WARNING] Could not create approot file.
[WARNING] Automatic directory resolution not configured.
/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wxPython/lib/splashscreen.py:5: DeprecationWarning: \

#####################################################\
# THIS MODULE IS NOW DEPRECATED                      |
#                                                    |
# The core wx library now contains an implementation |
# of the 'real' wx.SpashScreen.                      |
#####################################################/


  import wx.lib.splashscreen
```

Splash screen comes up, I click it but then I get this in the terminal:
```
/usr/share/openrpg/orpg/orpg_windows.py:985: DeprecationWarning: wx.MaskColour is deprecated, use `wx.Mask` instead.
  mask = wxMaskColour( gif, mask_color )
Reading Gametree file: /home/opakedragon/.openrpg/tree.xml... done.
Parsing Gametree Nodes  . done
[Errno 13] Permission denied: '/home/opakedragon/.openrpg/lastgood.xml'
Current image cache size is set at 32 images, using random purge.
```

Then this pops up in a window:
```
Corrupt Tree!
Your game tree is being regenerated. To
salvage a recent version of your gametree
exit OpenRPG and copy the lastgood.xml
file in your myfiles directory
to /home/opakedragon/.openrpg/tree.xml
in your myfiles directory.
lastgood.xml WILL BE OVERWRITTEN NEXT TIME YOU RUN OPENRPG.
```

It closes out when I click ok, and then this is the resultant output in the terminal:
```
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/wx-2.6-gtk2-unicode/wx/lib/splashscreen.py", line 111, in OnMouseClick
    self.timer.Notify()
  File "/usr/share/openrpg/orpg/main.py", line 1087, in AfterSplash
    self.frame = orpgFrame(NULL, -1, "OpenRPG v"+VERSION)
  File "/usr/share/openrpg/orpg/main.py", line 293, in __init__
    self.tree.load_tree(self.settings.get_setting("gametree"))
  File "/usr/share/openrpg/orpg/gametree/gametree.py", line 306, in load_tree
    os.rename(filename,filename+".corrupt")
OSError: [Errno 13] Permission denied
```

And then I need to Ctrl+C to close the code.

I would like to be able to run openrpg without having to use root.

---

### Post by sirebral on 2009-06-06
Wow.  You guys are way off.  Some people helped me with these instructions a long time ago.

[http://www.assembla.com/wiki/show/openrpg/InstallUbuntu_Hardy](http://www.assembla.com/wiki/show/openrpg/InstallUbuntu_Hardy)

---

### Post by Sef on 2009-06-06
Closed. necromancing.

---

