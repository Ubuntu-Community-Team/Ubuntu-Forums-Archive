---
title: "Applications Menu Editor broken"
date: 2006-03-14
forum: Desktop Environments
---

### Post by OMRebel on 2006-03-14
Whenever I try to run the Applications Menu Editor, I see it pop up on the bottom bar saying that it's starting, but then it goes away and nothing loads.  Do I uninstall it and reinstall it?  Not real sure how to fix this.  Thanks.

---

### Post by Ramses de Norre on 2006-03-14
Can you run it from terminal? Type in smeg and see if it gives any output.

---

### Post by OMRebel on 2006-03-14
I got the following when typing it in at a terminal:

Traceback (most recent call last):
  File "/usr/bin/smeg", line 562, in ?
    main()
  File "/usr/bin/smeg", line 558, in main
    smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
    self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 56, in __init__
    xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 28, in __init__
    self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 42, in parse
    self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 524, in parse
    __genmenuNotOnlyAllocated(tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 850, in __genmenuNotOnlyAllocated
    __genmenuNotOnlyAllocated(submenu)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 853, in __genmenuNotOnlyAllocated
    tmp["cache"].addMenuEntries(menu.AppDirs)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1016, in addMenuEntries
    self.__addFiles(dir, "", prefix, legacy)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 1022, in __addFiles
    menuentry = MenuEntry(os.path.join(subdir,item), dir, prefix)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 382, in __init__
    self.DesktopEntry = DesktopEntry(os.path.join(dir,filename))
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 25, in __init__
    self.parse(filename)
  File "/usr/lib/python2.4/site-packages/xdg/DesktopEntry.py", line 36, in parse    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.4/site-packages/xdg/IniFile.py", line 30, in parse
    for line in file(filename,'r'):
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'

---

### Post by OMRebel on 2006-03-14
"sudo smeg" will run though.

---

### Post by Ramses de Norre on 2006-03-14
Strange.. it runs perfectly as normal user here..

---

### Post by justaguynpc on 2006-03-14
I think your idea of removing / re-installing would be my next step.  You may also want to make note of when the symptoms started to occur should you have installed anything else which may have affected (smeg) applications menu editor.

Correct me if I am wrong, but the applications menu editor is essentially a front end to smeg.  Follow up on that, too.

Try thinking out of the box, like package dependencies to your mal-fuctioning application.

justaguy

---

### Post by Sutekh on 2006-03-14
[QUOTE=OMRebel]
IOError: [Errno 13] Permission denied: '/usr/share/applications/dvdrip.desktop'[/QUOTE]
The rest of the error is garbage to me.

Could you check the permissions of that file?
```
ls -l /usr/share/applications/dvdrip.desktop
```
It may be that the Menu Editor is unable to read the file.

---

### Post by OMRebel on 2006-03-14
justaguynpc - I tried reinstalling it, but that didn't correct it.  I'm still in the process of learning Linux, so thinking outside of the box is a bit difficult for now.  But, this forum has been awesome with helping me out, and I'm learning more and more everyday.  I'm not sure when it first broke, because that was the first time I tried running it.  I originally installed Hoary on this laptop, and upgraded Hoary to Breezy.  Today is the first day I used smeg (Opera wasn't showing up under Internet, so I needed to add it).  I'm thinking that it's possible that upgrading from Hoary to Breezy could have been the cause, and it was a permission that didn't get changed during that process?

Sutekh - When I checked the permissions, it gave me the following:
-rwx------  1 root root 170 2006-03-07 21:04 /usr/share/applications/dvdrip.desktop

I'm assuming that means that it belongs to root, and that would be what the problem is.  How can I go about changing the permission on that file?

Thanks.

---

### Post by Sutekh on 2006-03-14
[QUOTE=OMRebel]
Sutekh - When I checked the permissions, it gave me the following:
-rwx------  1 root root 170 2006-03-07 21:04 /usr/share/applications/dvdrip.desktop[/QUOTE]

```
sudo chmod 755 /usr/share/applications/dvdrip.desktop
```
This will allow non-root users the ability to read the file.  [Linux CHMOD calculator]("http://www.onlineconversion.com/html_chmod_calculator.htm") - for some insight on [B]chmod 755
[/B]
Could you also post the permissions for another random .desktop file
```
ls -l /usr/share/applications/totem.desktop
```or whatever, just so i know 755 permissions are okay.




Hey check it out, your problem is a bug.

[https://launchpad.net/distros/ubuntu/+source/pyxdg/+bug/32762]("https://launchpad.net/distros/ubuntu/+source/pyxdg/+bug/32762")

---

### Post by skymt on 2006-03-14
I had this problem also, only with Opera, not dvdrip. Perhaps the chmod workaround should be in the wiki, at least until the developers come up with some clever fix?

---

### Post by OMRebel on 2006-03-14
Sutekh - thanks for your help.  For totem, I get:
-rw-r--r--  1 root root 6240 2005-12-13 14:56 /usr/share/applications/totem.desktop

I'm glad to know that others have reported this and it's not that I'm just doing something wrong.

skymt - I'm getting it on opera as well.  I'm just gonna through each one till it's working. 

Thanks for helping everyone.  I got it working now.  Only had to change the rights on opera.desktop, and it's working now.

---

### Post by Sutekh on 2006-03-14
[QUOTE=OMRebel]Sutekh - thanks for your help.  For totem, I get:
-rw-r--r--  1 root root 6240 2005-12-13 14:56 /usr/share/applications/totem.desktop[/QUOTE]

Okay so thats 644 permissions, so use that for any offending .desktop files

---

