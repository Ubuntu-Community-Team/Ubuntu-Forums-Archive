---
title: "iPodder loads and immediately unloads"
date: 2006-08-29
forum: Desktop Environments
---

### Post by kBQ on 2006-08-29
iPodder 2.1.9-4 has worked but now the program will start and then it exits after the splash screen. I tried reinstalling and rebooting (windows habit). I'm a n00b so break it down simple, please.
I checked and it is not running as a process.
I'm running Kubuntu 6.10

---

### Post by meng on 2006-08-29
Did you launch it from the command line? Then there may be a message on program exit.

---

### Post by kBQ on 2006-08-29
I think Kubuntu 6.06 is more accurate...
Ah. Ok. More info - I would only be guessing as to what it means.

[<class 'ipodder.players.XMMSPlayer'>, <class 'ipodder.players.NoPlayer'>]
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
USING XMMS
Traceback (most recent call last):
  File "/usr/share/ipodder/iPodderGui.py", line 3531, in ?
    main()
  File "/usr/share/ipodder/iPodderGui.py", line 3525, in main
    myApp = iPodderGui(ipodder)
  File "/usr/share/ipodder/iPodderGui.py", line 590, in __init__
    wx.App.__init__(self, False, None)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7473, in __init__
    self._BootstrapApp()
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_core.py", line 7125, in _BootstrapApp
    return _core_.PyApp__BootstrapApp(*args, **kwargs)
  File "/usr/share/ipodder/iPodderGui.py", line 1460, in OnInit
    self.PopulateDownloadsTab()
  File "/usr/share/ipodder/iPodderGui.py", line 3233, in PopulateDownloadsTab
    self.DownloadTabLog(encinfo,prune=False)
  File "/usr/share/ipodder/iPodderGui.py", line 3143, in DownloadTabLog
    index = self.downloads.InsertStringItem(0,encinfo.item_title)
  File "/usr/lib/python2.4/site-packages/wx-2.6-gtk2-unicode/wx/_controls.py", line 4764, in InsertStringItem
    return _controls_.ListCtrl_InsertStringItem(*args, **kwargs)
UnicodeDecodeError: 'utf8' codec can't decode byte 0xb2 in position 2: unexpected code byte

---

