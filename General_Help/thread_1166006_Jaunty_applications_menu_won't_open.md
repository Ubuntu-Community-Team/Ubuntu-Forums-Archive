---
title: "Jaunty applications menu won't open"
date: 2009-05-21
forum: General Help
---

### Post by dskyracer on 2009-05-21
I upgraded to Jaunty about a week ago. Things were going great but today I find the applications menu doesn't drop down or open. I've rebooted, removed the menu from the panel and put it back again but when I click on it nothing happens. I've looked in preferences to see if something was able to get the menu to open but so far no luck. Also how can I access the command line without the use of this menu? Thanks ahead of time..

---

### Post by dskyracer on 2009-05-21
Also when I right click on the application menu icon to edit the menu nothing happens. I googled this problem and editing the menu was mentioned.. no luck in editing it either..

---

### Post by Paresh on 2009-05-21
try pressing alt-f2 and entering gnome-terminal, or try ctrl-alt-f1 to get into a full screen shell (ctrl-alt-f7 to return to gui)

no idea what's happened to your menus tho :(

---

### Post by Paresh on 2009-05-21
alt-f2 and enter gmenu-simple-editor to load the menu editor

---

### Post by dskyracer on 2009-05-21
tried alt f2 nothing happened. Tried ctr-alt-f7, no joy either..

---

### Post by dskyracer on 2009-05-21
I've gone  into the systems, preferences, main menu, click on it and nothing happens.. this must have something to do with the problem.

---

### Post by dskyracer on 2009-05-21
Ok I forgot I had a shortcut to the terminal on my desktop so I have access to it for any sort of commands that may help me edit my main applications menu or any other magic the CLI can do.

---

### Post by Paresh on 2009-05-21
Try this
> gedit ~/.config/menus/applications.menu to get to your menu file.

if gedit doesn't work, use nano instead.

---

### Post by dskyracer on 2009-05-21
did that command and here is it's output:

<!DOCTYPE Menu PUBLIC "-//freedesktop//DTD Menu 1.0//EN"
 "http://www.freedesktop.org/standards/menu-spec/menu-1.0.dtd">

<Menu>
  <Name>Applications</Name>
  <MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
  <Menu>
    <Name>Internet</Name>
    <Exclude>
      <Filename>openjdk-6-javaws.desktop</Filename>
      <Filename>pidgin.desktop</Filename>
      <Filename>ia32-sun-java6-javaws.desktop</Filename>
      <Filename>tsclient.desktop</Filename>
    </Exclude>
  </Menu>
  <Menu>
    <Name>Other</Name>
    <Exclude>
      <Filename>wine-Programs-Microsoft Streets & Trips.desktop</Filename>
    </Exclude>
  </Menu>
</Menu>


Now what?

---

### Post by dskyracer on 2009-05-21
I have no idea how to edit the text in the  applications menu that the terminal has brought up. I've done a reboot into older kernels, system check, installed a new program to see if it would turn up in the applications menu.. nothing has worked. I've gone to the url listed in the output from the terminal in the last post and I see there might be a solution there some day, some way, I guess I will have to open apps with the terminal for now until I can get a way to get the edit menu feature working again.. and bring back a drop down menu. Life goes on.. acceptance is key ..

---

### Post by Paresh on 2009-05-21
Have a look in the ~/.config/menus/ for previous copies of applications.menu and compare then to see what's changed.  if you have anything, you could try renaming one of them as applications.menu and see if that makes things better.

I have had a quick look and found [ this link]("http://ubuntuforums.org/showthread.php?t=1081979"):

The suggested 'worst case' solution is to delete ~/.config/menus/applications.menu and ~/.config/menus/setting.menu
to reset the entire menu.

This should then re-create the standard menus and then you can configure to taste with the main menu app.

Hope it works

---

### Post by dskyracer on 2009-05-22
This is where my ignorance of the command line interface is hampering my abilities to even open the files you mention. I tried opening them by clicking on them only to get a message telling my I don't have permission to open such files.. I feel like such a newb because I should readily be able to open these files using sudo or some other way with root authority. Forgive me please for my lack of understanding or knowledge in the CLI. Obviously I need to study these things deeper. I've been running Ubuntu  for over a year now and love it's stability, secure features, and ease of use. However when problems like these arise it surely pays to have a better understanding of the terminal's power and usefulness. I need more practice or time on it, there is no doubt about that. 

Thanks for the link and also your help Paresh. I believe it's just a matter of time for me to be able to overcome this issue, especially when people like you in the community come forward with the help and assistance that I hope I can return someday to others who would benefit from my input.

---

### Post by dskyracer on 2009-05-22
Looking into my system files using nautilus shows me that the  /.config folder has zero items in it. I have no idea if this is even normal. Other folders show a question mark for items. It's all amazing if not mysterious to newbs like me.. 

One possible solution I considered was building a live disc of Ubuntu 9.04 and using that to possibly compare files or copy them out of the system or root in the live disc and then to paste them later into my current seemingly crippled  system to restore editing menus. 

Of course all this takes time.. and when we have lives to lead outside of the computer it can take a lot of time. I'm ok with that. Time is irrelevant in many ways, Sometimes I think it's something we created to drive us insane or stress us out. Thanks for your time in considering this problem.

---

### Post by Paresh on 2009-05-23
I haven't had time to get an answer for you, but I'm looking [here]("http://www.yolinux.com/TUTORIALS/GNOME.html#MENUS") to find out how the menu's work (I'm learning too :D)

---

### Post by mc4man on 2009-05-23
Open up a terminal like you did to run gedit or go 
Alt+F2, in the run box popup enter gnome-terminal -> run and you'll get a terminal

Then use this command
 ```
mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak
```

Alternately go Places -> home folder -> and under the view tab enable 'show hidden files'
Then browse to .config/menus and delete the applications.menu file

---

### Post by dskyracer on 2009-05-27
I just did what Mc5man advised to do with the terminal copying and pasting this command into the terminal 

mv ~/.config/menus/applications.menu ~/.config/menus/applications.menu.bak

and Vwella! I have my apps menu back in place.. Amazing!!!My main menu icon works again in the preferences choices too. Many thanks to Mc5man and Parish for taking the time to give me aid.. I had faith the Ubuntu community would come through for me and it did. You guys and gals are the best! Now I need to learn how to tag this solved and give Mc5man an official thanks

---

### Post by windyrij on 2009-07-20
> **Paresh said:**
> Have a look in the ~/.config/menus/ for previous copies of applications.menu and compare then to see what's changed.  if you have anything, you could try renaming one of them as applications.menu and see if that makes things better.

I have had a quick look and found [ this link]("http://ubuntuforums.org/showthread.php?t=1081979"):

The suggested 'worst case' solution is to delete ~/.config/menus/applications.menu and ~/.config/menus/setting.menu
to reset the entire menu.

This should then re-create the standard menus and then you can configure to taste with the main menu app.

Hope it works
---------------------
Hardy Heron:
I had exactly the same problem, don't know what I did, but the applications menu and Sytem|Prefernces|Main menu had disappeared..

I followed the worst case solution suggested above, and the applications menus and the menu editor in ~|Preferences returned.  :P

I hope this helps someone else.

windyrij

---

