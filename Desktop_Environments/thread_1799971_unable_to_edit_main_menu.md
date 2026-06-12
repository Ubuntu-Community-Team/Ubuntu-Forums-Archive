---
title: "unable to edit main menu???"
date: 2011-07-08
forum: Desktop Environments
---

### Post by lalitha niharika on 2011-07-08
When I am right clicking on menu or clicking on main menu (system<preferences) nothing is opening.I tried reinstalling gnome desktop, python..and there is no use.What should I do now??I want to edit my menu.:(

---

### Post by adit on 2011-07-08
Which version of ubuntu are you using?
What happens when you type into terminal
```
alacarte
```

---

### Post by lalitha niharika on 2011-07-08
I am using 10.10 , gnome.
I typed in terminal.got this
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 37, in <module>
    main()
  File "/usr/bin/alacarte", line 33, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/share/alacarte/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 63, in __loadMenus
    self.save(True)
  File "/usr/share/alacarte/Alacarte/MenuEditor.py", line 67, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/lalitha/.config/menus/applications.menu'

---

### Post by e79 on 2011-07-08
Does right-clicking the top menu in Gnome (Applications, Places, System) and choosing 'Edit Menus' work by any chances ?
 
Or does this works :
 
```
sudo alacarte
``` 
(as you have a permission denied)

---

### Post by lalitha niharika on 2011-07-08
yes!! this is working...sudo alacarte...thanks!! but can I do something to get it on right clicking??

---

### Post by adit on 2011-07-08
Actually sudo not required.  There are problems with permissions in your home directory.  Check the owner and permissions in your home directory.
```
ls -al
```

---

### Post by adit on 2011-07-08
> can I do something to get it on right clicking?
The python script /usr/bin/alacarte can be called in one of the following three ways
1) Type alacarte in terminal
2) Click System -> Preferences -> Main Menu
3) Right Click -> Edit Menus
The result is same.  If one way works *without errors*, the other ways also will work.

---

### Post by e79 on 2011-07-08
> **lalitha niharika said:**
> yes!! this is working...sudo alacarte...thanks!! but can I do something to get it on right clicking??
 
I'm glad to see it work at least with Sudo, we're getting there !
 
> **adit said:**
> Actually sudo not required. There are problems with permissions in your home directory. Check the owner and permissions in your home directory.
```
ls -al
```
 
Yup, more precisely :
 
```
ls -alh /home/lalitha/.config/menus/applications.menu
```
(since it seems to be the file not having the proper permission)

---

### Post by lalitha niharika on 2011-07-08
tab is opening using that command but I am unable to edit anything in that:(.Plz tell me someway in which I can modify it??

---

### Post by adit on 2011-07-09
> tab is opening using that command but I am unable to edit anything in that
Type into terminal```

ls -alh /home/Your_User_Name/.config/menus/applications.menu
```
and post the output of the above command

---

### Post by adit on 2011-07-09
> tab is opening using that command but I am unable to edit anything in that
I guess exactly what happened.  You tried to select the output with mouse and accidentally right clicked the mouse.  See screenshot.  That is why a new tab opened.
Try again.

---

### Post by sikander3786 on 2011-07-10
Yeah, definitely sounds like a permissions problem. We definitely need to see the output of this command:

```
ls -alh ~/.config/menus/applications.menu
```

Just copy/paste this command into your Terminal and there should be some output rather than opening up of a new Tab. Highlight that output as you'd simply do in any other application like Firefox or Word Processor and copy/paste the output here by right clicking it.

Or if that doesn't work for you, run this command instead:

```
ls -alh ~/.config/menus/applications.menu | tee ~/output
```

It would show the output and also, it would generate a new file in your /home directory named 'output'. You can copy/paste the text from that file onto the forums.

**Added:** BTW, almost all the configuration files in the home directory are simply recreated upon removal. Just tested changing the permission on my ~/.config/menus/applications.menu and then removing it. It solved the issue, so the simplest thing for you to do would probably be simply renaming the existing file. Run this command:

```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bad
```

And again try to edit the menus.

---

### Post by lalitha niharika on 2011-07-11
no tab is opening after typing this.What I meant in previous post is, edit menu tab is opening after using sudo alacatre command, but I am unable to edit anything in that.


output of command ls -alh ~/.config/menus/applications.menu
ls: cannot access /home/lalitha/.config/menus/applications.menu: Permission denied

---

### Post by adit on 2011-07-11
> What I meant in previous post is, edit menu tab is opening
That is not "tab", that should be called "window".
> but I am unable to edit anything in that.
Again permission problem.  The output shows you are not the owner of the above file.  In a default installation of ubuntu this should not happen.
What did you do? (to lose the ownership of the above file)
What is the output of
```
sudo ls -alh ~/.config/menus/applications.menu
```

---

### Post by lalitha niharika on 2011-07-11
your command didnt solve the prob:(

output
sudo ls -alh ~/.config/menus/applications.menu
ls: cannot access /home/lalitha/.config/menus/applications.menu: No such file or directory

I don't know the reason..I didn't do anything to loose ownership:confused:what would be the reason??is there any way of correcting it??

---

### Post by lalitha niharika on 2011-07-11
My installation is manual, I selected partitions.Can that effect ownership??

---

### Post by sikander3786 on 2011-07-11
I wonder if you are missing the whole .config directory. Please post the output of these commands:

```
ls -alh ~ | grep .config
```

```
sudo ls -alh ~ | grep .config
```

If the output is still the same i.e. 'ls: cannot access ...', open your home directory in File Browser and press Ctrl + H to see the hidden files. Can you see the .config directory?

---

### Post by adit on 2011-07-11
> My installation is manual, I selected partitions.Can that effect ownership?? 
No, That is not the cause of your problem

From your first post
> I tried reinstalling gnome desktop, python
Why did you reinstall gnome desktop and python.  I think this is the cause of your problem.  The basic problem is you do not have permissions to access your own home directory.
To display owners and permissions of any directory
```
ls -al
```
In case you do not know, read the following tutorials to get a basic understanding of permissions, owner etc.
_[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)_
_[http://www.tuxfiles.org/linuxhelp/fileowner.html](http://www.tuxfiles.org/linuxhelp/fileowner.html)_

---

### Post by lalitha niharika on 2011-07-11
lalitha@lalitha-desktop:~$ ls -alh ~ | grep .config
drwxr-xr-x 26 lalitha lalitha 4.0K 2011-07-11 13:36 .config
drwxr-xr-x  2 lalitha lalitha 4.0K 2011-07-08 09:19 .fontconfig

lalitha@lalitha-desktop:~$ sudo ls -alh ~ | grep .config
[sudo] password for lalitha: 
ls: cannot access /home/lalitha/.gvfs: Permission denied
drwxr-xr-x 26 lalitha lalitha 4.0K 2011-07-11 13:36 .config
drwxr-xr-x  2 lalitha lalitha 4.0K 2011-07-08 09:19 .fontconfig
lalitha@lalitha-desktop:~$ 



adit: no,that is not the reason.first I got problem, then to solve it I reinstalled.I read that solution in one of the forum threads.

---

### Post by lalitha niharika on 2011-07-11
I already tried that, I opened .conf folder.It is saying that I am not the owner.I saw in properties<permissions.

---

### Post by adit on 2011-07-11
The following command lists all the files in the home directory not owned by you.
```
find ~ ! -user lalitha
```
For your privacy:
The output of above command usually will not contain the names of your personal files created by you.  Anyway verify the output carefully.  If it contains the names of any of your personal files, delete those lines and post the rest of the output.
Edit: If the output is very large, don't post in the forum directly.  Save the output in a text file and attach the file.

---

### Post by lalitha niharika on 2011-07-11
lalitha@lalitha-desktop:~$ find ~ ! -user lalitha
/home/lalitha/.mozilla/plugins
/home/lalitha/.config/menus
find: `/home/lalitha/.config/menus': Permission denied
lalitha@lalitha-desktop:~$ 

I upgraded my system just before one month.Then I didn't like 11.04.so I formatted and newly installed 10.10.Its just before 1 weak!!

can I solve my problem by upgrading????

---

### Post by rushikesh988 on 2011-07-11
> **adit said:**
> The following command lists all the files in the home directory not owned by you.
```
find ~ ! -user lalitha
```
For your privacy:
The output of above command usually will not contain the names of your personal files created by you.  Anyway verify the output carefully.  If it contains the names of any of your personal files, delete those lines and post the rest of the output.
Edit: If the output is very large, don't post in the forum directly.  Save the output in a text file and attach the file.
nice command...

---

### Post by rushikesh988 on 2011-07-11
Check out This Site .. may be links of pages on this site will help you [http://www.timelordz.com/wiki/Gnome_Menus]("http://www.timelordz.com/wiki/Gnome_Menus")

---

### Post by lalitha niharika on 2011-07-12
Thanks to all!!Problem got solved..I simply created anther account, deleted this account.:popcorn:

---

