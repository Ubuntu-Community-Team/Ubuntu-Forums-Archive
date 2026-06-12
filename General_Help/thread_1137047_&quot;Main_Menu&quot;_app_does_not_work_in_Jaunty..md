---
title: "&quot;Main Menu&quot; app does not work in Jaunty..."
date: 2009-04-25
forum: General Help
---

### Post by b@sh_n3rd on 2009-04-25
Hi, i installed Jaunty Jackalope BETA some time ago and at the time, before the official release, i came across the known bug where when u select "Main Menu" in the "Preferences" menu it returns an error. Currently, i've updated Jaunty up to the 24th but when i try this app, i have no feedback whatsoever and the "Main Menu" dialog box doesn't open. Any help on this please?

---

### Post by b@sh_n3rd on 2009-04-26
any help pls? :(

---

### Post by spiderbatdad on 2009-04-26
hmm. was unaware of this issue. I upgraded via update-manager and have not had this problem.
What happens if you open a terminal and run:```
alacarte
```

---

### Post by b@sh_n3rd on 2009-04-27
Hey, thanks for your reply but i had a few other problems which tend to occur with my tinkering (especially on a beta system!...shouldn't do that on beta..) so i reinstalled Jaunty final release. Thanks alot dude...:D

---

### Post by shane2peru on 2009-04-29
I too had this problem with the RC version of Jaunty, and then I re-installed with the official release, and my edit menus still doesn't work.  Any ideas???  

Shane

---

### Post by capt_carl on 2009-05-26
Hi all,

I'm having this problem too.  I'm currently working on a fresh install of Jaunty.  I tried running alacart in a terminal, and I got this:
```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/captcarl/.config/menus/applications.menu'

```It runs fine if I put sudo in front of it.

---

### Post by b@sh_n3rd on 2009-05-27
> **capt_carl said:**
> Hi all,

I'm having this problem too.  I'm currently working on a fresh install of Jaunty.  I tried running alacart in a terminal, and I got this:
```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/captcarl/.config/menus/applications.menu'

```It runs fine if I put sudo in front of it.

Try this, Goto: System > Administration > Users and Groups, click "Unlock", type your password when requested, select your user from the list and click properties. In the next dialog-box that appears, click the "User Priviledges" tab and check all the items on the list (If you're the only user, I suggest you select all, or select the ones you want [this has solved some similar issues for me before]) :D...hope this helps... Oh yeah, and Welcome to the Community and Ubuntu! :D

---

### Post by capt_carl on 2009-05-27
Thanks for the welcome. :)  I've been a lurker for a while, reading for troubleshooting issues, but I never got around to signing up until now.  Been using Ubuntu for about a year now, started on Hardy.

I tried your suggestion.  I already had everything checked from my own fooling around at a previous time.  I asked a friend and he suggested I check the permissions of the file.  That came back as the following:
```
-rw-r--r-- 1 root root 233 2009-05-26 23:43 /home/captcarl/.config/menus/
```Again, I had to run ls with sudo, as it wouldn't even let me view the permissions.  I changed the permissions for the file from root to me(captcarl).  I still get the same "permission denied" when trying to run alacart from terminal without sudo.  I also still cannot view the permissions without sudo, even though the app comes back with me as the owner.

It's not a huge deal, just annoying, ya know?

---

### Post by Menthu_Rae on 2009-08-14
**EDIT2:** Got it working now... edited below to match my "fix"...

[COLOR="Silver"]**EDIT:** Hrmmm it seems whilst now I can open the edit menus/alacarte - I can't actually change anything! Rargh... Will post back if I fix this.[/COLOR]


I just had this issue in Jaunty final 2.6.28-14 on my EeePC 1000HE... I fixed it by doing this:

```
cd /home/**username**/.config/menus/
```

```
ls -ltra
```

You should see that the files *settings.menu* and *applications.menu* are owned by **username** but belong to the group **root**...

I then did...

```
sudo chown **username:username** *.menu
```
```
sudo chown -R **username:username** /home/**username**/.local/
``` ***from EDIT2**

And the permissiions now showed that they belonged to **username** and group **username**... I can now edit my menus and run alacarte from terminal without sudo. :)

---

