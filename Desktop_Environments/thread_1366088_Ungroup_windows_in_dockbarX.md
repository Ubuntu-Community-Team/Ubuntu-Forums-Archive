---
title: "Ungroup windows in dockbarX ??"
date: 2009-12-28
forum: Desktop Environments
---

### Post by chinmaya_n on 2009-12-28
HI,

I tried to ungroup  windows in dockbarX ....
But failed! Can anyone help me!
I didnt like that grouping behaviour!

Thanx!

---

### Post by M7S on 2009-12-28
Sorry, grouping is in the very core of DockbarX. I have no plans at including that feature, it would be way too much work for something that actually makes no sense at all to me. But if you (or someone else) want to fork dockbarx and make a non-grouping version (which probably would be much easier than supporting both grouping and non-grouping at the same time), I'll give you all support you need.


M7S,
DockbarX developer

---

### Post by chinmaya_n on 2009-12-28
> I'll give you all support you need.

Thanx M7S, I would like to do that! :popcorn:
Can you direct me to first understand the construction of this dockbar.... I mean, you might already documented it!

Thanx again :)

---

### Post by M7S on 2009-12-28
I won't give you a full documentation now, I don't have the time.

What I will give you is a dirty hack that will do what you want, hopefully (It's not throughly tested and migh not work as expected at all time) :). Two easy steps:
1) Pull the last last commit from the experimental bransh from launchpad. [https://code.launchpad.net/dockbar](https://code.launchpad.net/dockbar) (Yes, that last commit is made simply to make your hacking easier, you're welcome :P).

2) Replace line 4019 and 4020 in dockbarx.py with
```
            self.groups[class_group_name].add_window(window)
            return
```with
```
            if not self.groups[class_group_name].windows:
                self.groups[class_group_name].add_window(window)
                return
            else:
                class_group_name = "%s-%s"%(class_group_name, time())
                self.windows[window]=class_group_name
```This is a really ugly hack! If one would like to do this the right way the classes Group Button and window button should be merged to one class, since every class now is a window. If you're up for that and need help, I'm still willing to offer you that, but not until next year or so. ;)

---

### Post by pibach on 2010-01-29
I would like to second ungrouping, as the grouping requires an extra click or mouse move and makes thinks more complicated than it helps.

---

### Post by chinmaya_n on 2010-01-31
> **pibach said:**
> I would like to second ungrouping, as the grouping requires an extra click or mouse move and makes thinks more complicated than it helps.

Hey thankyou!
I didnt had time, so I did not sit to solve it... Hope I may get some time in following few weeks!

---

### Post by #Peter on 2010-01-31
I would also like to see ungrouping very much, bugs the hell out of me with grouping... Makes no sense at all, much more complicated than having seperate icons...

---

### Post by M7S on 2010-02-01
I still don't understand why you want dockbarx to do this. If all you want is icons instead of icons+name, just use talika.

---

### Post by #Peter on 2010-02-03
I did not know about talika, it suited all my needs. Thank you very much!

---

### Post by floopy1962 on 2010-09-30
i've been use talika before, its great but with talika 0.49 icons are smaller and with 0.50 icons are OK but don't have buttons...
so i see dockbarx have option "ignor windows on other workspaces" 
and have buttons even better have themes. but pibach is right.... its more complicated with grouping. so i can't find "dockbarx.py" anywhere, in /usr/bin i have "dockbarx_factory.py" and there is only 76 lines... where is this "dockbarx.py" i can't find it with gnome-search-tool or catfish.
i have big and clear panel, 2 workspaces... i don't need grouping pls tell me how to do it :(
sry.. i found dockbarx.py in /usr/share/pyshared/dockbarx but i can't find lines 4019-            self.groups[class_group_name].add_window(window) and 4020-return i have only 1144 lines..

---

### Post by M7S on 2010-09-30
Much has happened with dockbarx since I posted that hack. I could make some new instructions if you want later this week (I have to prioritize releasing a new version of dockbarx first). Don't expect a perfect bugfree experience, though. The hack will be ugly.

---

### Post by floopy1962 on 2010-09-30
> **M7S said:**
> Much has happened with dockbarx since I posted that hack. I could make some new instructions if you want later this week (I have to prioritize releasing a new version of dockbarx first). Don't expect a perfect bugfree experience, though. The hack will be ugly.

Thank you very much... i will be grateful :P i will wait 8)

---

### Post by M7S on 2010-10-04
Ok, haven't tried this so I don't know if it works but replace line 443 (in Dockbarx 0.39.8, it might be some other line if you still use 0.39.7) 
```
self.groups[identifier].add_window(window)
```

with

```
identifier = identifier + str(len(self.groups[identifier].windows)+1)
self.windows[window] = identifier
```

---

### Post by floopy1962 on 2010-10-04
> **M7S said:**
> Ok, haven't tried this so I don't know if it works but replace line 443 (in Dockbarx 0.39.8, it might be some other line if you still use 0.39.7) 
```
self.groups[identifier].add_window(window)
```

with

```
identifier = identifier + str(len(self.groups[identifier].windows)+1)
self.windows[window] = identifier
```

i found "self.groups[identifier].add_window(window)" on line 439...
i replace it and dockbar wont run...
in terminal when i type "dockbarx_factory.py run-in-window"
i get this 
```
progname=dockbarx_factory.py; RGBA=on
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 26, in <module>
    import dockbarx.dockbar
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 440
    self.windows[window] = identifier
    ^
IndentationError: unexpected indent
```
this is with Dockbarx 0.39.8 
i also found other Dockbarx 0.39.8 tar.gz 
there "self.groups[identifier].add_window(window)" is exactly on 443 line and when raplace it i get this...
```
progname=dockbarx_factory.py; RGBA=on
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 26, in <module>
    import dockbarx.dockbar
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/dockbar.py", line 443
    identifier = identifier + str(len(self.groups[identifier].windows)+1)
             ^
IndentationError: expected an indented block

```
is there a chance for this to work... :( it's very difficult to me to work with gimp and inkscape...

---

### Post by M7S on 2010-10-05
The number of white spaces is very important in python. They need to unchanged from the code.

Edit: I have used normal spaces, not tabs in the code. That matters too. You should in other words have 12 spaces before each row.

---

### Post by M7S on 2010-10-05
Ok, I tested the code it doesn't work, but this should:

line 441 - 444
```
        if identifier in self.groups.get_identifiers():
            # This isn't the first open window of this group.
            self.groups[identifier].add_window(window)
            return
```should be replaced with these lines.
```
        if identifier in self.groups.get_identifiers():
            # This isn't the first open window of this group.
            if not self.groups[identifier].windows:
                self.groups[identifier].add_window(window)
                return
            n = 0
            while(True): 
                n += 1
                if not identifier + str(n) in self.groups.get_identifiers():
                    identifier = identifier + str(n)
                    self.windows[window] = identifier
                    break
```

The intendent should be correct if you just copy-paste over.

---

### Post by M7S on 2010-10-10
Did you get it to work?

---

### Post by floopy1962 on 2010-10-11
i'm sorry for wasting your time... it didn't work :( the whole dockbarx stop working until i delete every dockbarx file by heand and now i have fresh install... now i use dockbarx on AWN :) 
if you guessed some other way to do that... 
but thanks for trying to helping me :P :)

---

### Post by floopy1962 on 2010-10-11
hey wait i change some free space i dockbar.py and start working :) i love you man :KS:) i don't know why but the icon quality is little ugly... whateversize i made :d
[IMG]http://i53.tinypic.com/2iraiv6.png[/IMG]
 but however its work :P

---

### Post by M7S on 2010-10-12
Yes, the hack has that effect. What the hack does is that it adds a number to identifier for every new window so that every window has a unique identifier instead of the same for all windows of a program. The downside is that the identifier also is used for identifying the right icon in the theme and for pinning and stuff like that. As I said before it's an ugly hack.

---

### Post by floopy1962 on 2010-10-12
yea its happening only if two windows of one app is open... the pretty and the ugly :D however is not a big problem :P now i more easy to work with gimp for me :P tank you :)

---

### Post by Valery Kondakoff on 2010-11-23
There is 'Keep open office application separated' option. Can we have something like this for Chrome/Chromium windows, which were opened using application shortcuts?

Currently all of the Chrome/Chromium windows, which were opened using application shortcut are grouped with the main Chrome/Chromium window and all of them have the same icon - this seems wrong to me...

Thank you!..

---

### Post by M7S on 2010-11-24
Chrome/Chrominum apps could be separated and the same goes for firefox prism applications. Could you post a wishlist bug report at launchpad so that I won't forget it (I have a mile long todo list since the feature freeze ended after the 0.40 release)? [https://bugs.launchpad.net/dockbar/](https://bugs.launchpad.net/dockbar/)

---

### Post by Valery Kondakoff on 2010-11-25
Done! [https://bugs.launchpad.net/dockbar/+bug/681376](https://bugs.launchpad.net/dockbar/+bug/681376)

---

