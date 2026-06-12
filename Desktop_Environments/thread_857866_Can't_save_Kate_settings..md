---
title: "Can't save Kate settings."
date: 2008-07-12
forum: Desktop Environments
---

### Post by KhipuX on 2008-07-12
Evening all.

Been all over KDE's website with no luck on this one. When I use Kate I like to use line numbers, get rid of the terminal line and hide the Documents column. Every time I set these preferences and restart Kate my preferences have been changed back to the default setup.

How do I make Kate remember these settings?

Many thanks.

---

### Post by p_quarles on 2008-07-13
I thought this bug had been fixed in KDE 3.5.9. Are you using Ubuntu 7.10 by any chance? 

In any case, the workaround was to edit ~/.kde/share/config/katerc directly. For some reason, it wasn't saving changes to that file, but changing it manually (of course) would save them.

---

### Post by KhipuX on 2008-07-13
I'm definately on 8.04.1 with KDE 3.5.9. I've been through option after option and still can't get it to save any settings. Katerc has helped me out though so thank you. Looks like another bug report. Having said that, I can't get Konsole to save my settings either and that was supposed to be fixed in 3.5.9 too. Maybe there is a problem with my permissions.....

---

### Post by sigfrido on 2008-08-01
Hi there. I'm tryin to edit katerc myself, as I have a problem with my shortcuts. The thing is I don't know how to edit specific entries. I tried the most intuitive ways, but it doesn't work.

Do anyone know how to edit the Shortcuts section in katerc?

Better, is there any handout to do the editing of katerc?

Thanks.

---

### Post by KhipuX on 2008-08-05
I'm just trying to drag out the guide that I used. Can't find it on the net now though and the page I got the link from has disappeared.

If you can wait I'm sure I'll find it again.

---

### Post by automaton26 on 2008-11-22
I'm on Kubuntu 8.10, and Kate still doesn't persist the "Window...Tool Views..." settings.

I can't find any changes to the "katerc" file that fix this either.

---

### Post by Ubangi on 2009-01-21
I am using Ubuntu 8.10 and I cannot save the Kate settings either.
I thought Kate was a decent editor until now.
Now I regret installing such rubbishware....

---

### Post by Ubangi on 2009-01-27
Has anyone found a solution to this please? All I can find is lots of people reporting the same problem but no solutions.....

---

### Post by Ubangi on 2009-02-08
hmmmm, silence, as usual....

---

### Post by JabaDisa on 2009-05-01
I have the same problem changing the font-size.
It has something to do with kate settings for root (since I've run kate as root a couple of times). When I deleted the files for my user's kate settings and root's kate settings, changing the font size was permanent.
Can't say the same for other settings such as line numbering...
I'll post again if I find a solution...

Using Kubuntu Interpid & KDE 4.1.4

---

### Post by inobe on 2009-05-01
welcome to the ubuntu forums

kde 4.2.2 is out and it's pretty stable, it fixes a lot of past bugs.

if your running kubuntu 8.10 or later' try to upgrade your desktop.


[http://www.kubuntu.org/news/kde-4.2](http://www.kubuntu.org/news/kde-4.2)

---

### Post by JabaDisa on 2009-05-01
It seems that the font size isn't kept in katerc, perhaps I got the wrong trail anyway. I think I'll be upgrading to Jaunty and hope things get fixed :)

---

### Post by inobe on 2009-05-01
you don't have to upgrade to jaunty.

if your running 8.10 you can upgrade your desktop only.

---

### Post by guyburke on 2009-05-29
editing ~/.kde/share/config/katerc seems to do the trick, but...

here's something interesting...
i did notice that at least some of the settings are being saved. it's the reading of the settings that seems to be the issue.

try this:
Open Kate, Settings > Configure Kate.
Select Application > Plugins and enable every plugin listed in the Plugin Manager. Click Apply and OK.
Now open ~/.kde/share/config/katerc and look under [Kate Plugins]. You'll see that each plugin setting is set to true--saving of the settings worked.
Now close Kate and reload Kate. Go again to Settings > Configure Kate > Application > Plugins. You'll see that the settings are not being read as each plugin is not enabled.

What's happening, is the saved settings are not correctly being read and if the settings are again updated, all of the previous settings are being overwritten (with what was not read correctly).

Who's wants to submit this bug?

---

### Post by guyburke on 2009-05-30
SOLUTION:
a combination of Sessions > Save and Sessions > Save As Default.

Also, open ~/.kde/share/config/katerc and verify:
[General]
Last Session=mysession.katesession
Restore Window Configuration=true
Session Exit=save

Here's my **working configuration** that i ended up with:
```

[General]
Days Meta Infos=30
Last Session=mysession.katesession
Modified Notification=false
Restore Window Configuration=true
Save Meta Infos=true
Session Exit=save
Show Full Path in Title=true
Show Status Bar=true
Startup Session=manual

[KTEXTEDITOR:]
DEVELOPER_INFO=NEVER TRY TO USE VALUES FROM THAT GROUP, THEY ARE SUBJECT TO CHANGES

[Kate Document Defaults]
Allow End of Line Detection=true
Allow Simple Mode=true
Backup Config Flags=0
Backup Prefix=
Backup Suffix=~
Basic Config Flags=8912928
Encoding=UTF-8
End of Line=0
Indentation Mode=normal
Indentation Width=4
PageUp/PageDown Moves Cursor=true
ProberType for Encoding Autodetection=0
Search Dir Config Depth=3
Tab Handling=2
Tab Width=4
Word Wrap=false
Word Wrap Column=80

[Kate Plugins]
katebacktracebrowserplugin=true
katebuildplugin=true
katectagsplugin=true
kateexternaltoolsplugin=true
katefilebrowserplugin=true
katefiletemplates=true
katefindinfilesplugin=true
katekonsoleplugin=true
katemailfilesplugin=true
kateopenheaderplugin=true
katequickdocumentswitcherplugin=true
katesnippetsplugin=false
katesymbolviewerplugin=true
katetabbarextensionplugin=true
katetextfilterplugin=true

[Kate Renderer Defaults]
Schema=kate - Normal
Show Indentation Lines=true
Show Whole Bracket Expression=true
Word Wrap Marker=false

[Kate View Defaults]
Auto Center Lines=0
Auto Completion=true
Bookmark Menu Sorting=0
Default Mark Type=1
Dynamic Word Wrap=false
Dynamic Word Wrap Align Indent=80
Dynamic Word Wrap Indicators=1
Folding Bar=true
Icon Bar=false
Line Numbers=true
Persistent Selection=false
Replacement Text History=
Scroll Bar Marks=true
Search Pattern History=
Search/Replace Flags=140
Vi Input Mode=false
Vi Input Mode Hide Status Bar=false
Vi Input Mode Steal Keys=false

[Konsole]
AutoSyncronize=true

[MainWindow]
Height 1050=736
Width 1680=1022

[MainWindow][Toolbar mainToolBar]
Hidden=true
Index=0

[Notification Messages]
Kate hide sidebars notification message=false

[Plugin:katefindinfilesplugin::find-in-files]
CaseSensitive=true
LastSearchFiles=*,*.h\\,*.hxx\\,*.cpp\\,*.cc\\,*.C\\,*.cxx\\,*.idl\\,*.c,*.cpp\\,*.cc\\,*.C\\,*.cxx\\,*.c,*.h\\,*.hxx\\,*.idl
LastSearchItems=
LastSearchPaths=
Recursive=true
RegExp=false

[PluginSymbolViewer]
ExpandTree=false
ViewTypes=false

[TipOfDay]
RunOnStart=false

[fileselector]
AutoSyncEvents=0
filter history=
filter history len=9
pathcombo history len=9
restore last filter=true
restore location=true
toolbar actions=up,back,forward,home,short view,detailed view,tree view,bookmarks,sync_dir

```

---

### Post by ASCHYIEL on 2009-07-17
=(

---

### Post by dyingsun on 2009-10-20
Bumping this thread rather than starting a new one.

I'm using Kate on the Jaunty system, it was brilliant on 8.04, but having these config issues now. I have the templates plugin installed, but it won't stay enabled in Configure Kate. It also wasn't remembering the line numbers, but that is fixed by editing the katerc file. In katerc, it says katefiletemplates=true, but I have no option in the File menu to create a new file from a template. Is there something else I need to do/enable to get this option?

Cheers!
Damien

---

### Post by Morientes on 2009-11-02
I am having this problem with Kate on Kubuntu 9.10. I am just trying to enlarge the font but it simply refuses to remember my settings.
Any solution?
If anyone could just tell me how to edit the config file manually that would also be fine...

---

### Post by rCXer on 2009-11-02
These problems may be related to [this bug](https://bugs.launchpad.net/ubuntu/+source/kdesdk/+bug/206176), in case anyone is interested...

---

### Post by Morientes on 2009-11-05
Any news on this? It's a pretty big problem in my opinion for the reasons I stated here: [http://ubuntuforums.org/showthread.php?t=1315332&highlight=kate](http://ubuntuforums.org/showthread.php?t=1315332&highlight=kate) .

I actually forgot about this thread and started a new one. But we might as well keep it here.

---

### Post by Morientes on 2009-12-09
And another bump!
This problem is soooo annoying! I have to increase my font size every time I open kate (and kile which uses Kate).

WOuld be really great with some fix if someone know it?

---

### Post by Ms_Angel_D on 2009-12-17
I fixed this issue by doing the following:

```
sudo chown -R angel:angel /home/angel/.kde
```

of course replace my name with your username

it seems some of the files we're owned by root instead of me, now all my settings save properly.

---

### Post by linucks42 on 2009-12-29
I'm still hitting this problem on Karmic.

I've filled a bug report here:

[http://bugs.kde.org/show_bug.cgi?id=220591](http://bugs.kde.org/show_bug.cgi?id=220591)

Here's hoping someone's able to work out what's going on.

---

### Post by linucks42 on 2009-12-30
Just found out this isn't a bug, but rather a feature of Kate.

Kate has the concept of "sessions" and by default, it always starts with a new one.

In order to get Kate to start up with the same settings as you closed her down, you need to go to "Settings", and then in the "Sessions" section, select the "Load last-used session" and also select the "save session" in the "Behaviour on Application Exit or Session Switch" section.

Bleedin' obvious when you know how...

---

### Post by Morientes on 2010-01-11
> **Ms_Angel_D said:**
> I fixed this issue by doing the following:

```
sudo chown -R angel:angel /home/angel/.kde
```

of course replace my name with your username

it seems some of the files we're owned by root instead of me, now all my settings save properly.

That fixed it for me too! Thanks a lot!

---

### Post by Kyril on 2010-01-11
Since KDE 4.3.90 it works for me with a simple:

1. Open Kate and make your changes

2. Session > Save As Default

3. Done :D

---

### Post by leiavoia on 2010-01-25
chown worked for me too!

---

### Post by navets on 2010-05-20
thanks for the session save as default it really worked and helped me .. :)

---

### Post by yanike on 2010-10-30
> **guyburke said:**
> SOLUTION:
a combination of Sessions > Save and Sessions > Save As Default.

Also, open ~/.kde/share/config/katerc and verify:
[General]
Last Session=mysession.katesession
Restore Window Configuration=true
Session Exit=save

Here's my **working configuration** that i ended up with:
```

[General]
Days Meta Infos=30
Last Session=mysession.katesession
Modified Notification=false
Restore Window Configuration=true
Save Meta Infos=true
Session Exit=save
Show Full Path in Title=true
Show Status Bar=true
Startup Session=manual

[KTEXTEDITOR:]
DEVELOPER_INFO=NEVER TRY TO USE VALUES FROM THAT GROUP, THEY ARE SUBJECT TO CHANGES

[Kate Document Defaults]
Allow End of Line Detection=true
Allow Simple Mode=true
Backup Config Flags=0
Backup Prefix=
Backup Suffix=~
Basic Config Flags=8912928
Encoding=UTF-8
End of Line=0
Indentation Mode=normal
Indentation Width=4
PageUp/PageDown Moves Cursor=true
ProberType for Encoding Autodetection=0
Search Dir Config Depth=3
Tab Handling=2
Tab Width=4
Word Wrap=false
Word Wrap Column=80

[Kate Plugins]
katebacktracebrowserplugin=true
katebuildplugin=true
katectagsplugin=true
kateexternaltoolsplugin=true
katefilebrowserplugin=true
katefiletemplates=true
katefindinfilesplugin=true
katekonsoleplugin=true
katemailfilesplugin=true
kateopenheaderplugin=true
katequickdocumentswitcherplugin=true
katesnippetsplugin=false
katesymbolviewerplugin=true
katetabbarextensionplugin=true
katetextfilterplugin=true

[Kate Renderer Defaults]
Schema=kate - Normal
Show Indentation Lines=true
Show Whole Bracket Expression=true
Word Wrap Marker=false

[Kate View Defaults]
Auto Center Lines=0
Auto Completion=true
Bookmark Menu Sorting=0
Default Mark Type=1
Dynamic Word Wrap=false
Dynamic Word Wrap Align Indent=80
Dynamic Word Wrap Indicators=1
Folding Bar=true
Icon Bar=false
Line Numbers=true
Persistent Selection=false
Replacement Text History=
Scroll Bar Marks=true
Search Pattern History=
Search/Replace Flags=140
Vi Input Mode=false
Vi Input Mode Hide Status Bar=false
Vi Input Mode Steal Keys=false

[Konsole]
AutoSyncronize=true

[MainWindow]
Height 1050=736
Width 1680=1022

[MainWindow][Toolbar mainToolBar]
Hidden=true
Index=0

[Notification Messages]
Kate hide sidebars notification message=false

[Plugin:katefindinfilesplugin::find-in-files]
CaseSensitive=true
LastSearchFiles=*,*.h\\,*.hxx\\,*.cpp\\,*.cc\\,*.C\\,*.cxx\\,*.idl\\,*.c,*.cpp\\,*.cc\\,*.C\\,*.cxx\\,*.c,*.h\\,*.hxx\\,*.idl
LastSearchItems=
LastSearchPaths=
Recursive=true
RegExp=false

[PluginSymbolViewer]
ExpandTree=false
ViewTypes=false

[TipOfDay]
RunOnStart=false

[fileselector]
AutoSyncEvents=0
filter history=
filter history len=9
pathcombo history len=9
restore last filter=true
restore location=true
toolbar actions=up,back,forward,home,short view,detailed view,tree view,bookmarks,sync_dir

```

THANK YOU THANK YOU THANK YOU!!!!!

I can now go back to coding with a :)

---

### Post by techexpert on 2011-01-17
> **Ms_Angel_D said:**
> I fixed this issue by doing the following:

```
sudo chown -R angel:angel /home/angel/.kde
```

of course replace my name with your username

it seems some of the files we're owned by root instead of me, now all my settings save properly.

Ms_Angel_D, you are the best!
 I've seen this problem in Fedora and CentOS and it was just very annoying of not having my settings right everytime.
 Now switched to Ubuntu and the problem was still the same. I've tried to "chown" several times using the Nautilus, but that didn't fix it. After I did it as you said in the command line, everything works!!! Kate rocks!!! (when it works..):p:P

---

