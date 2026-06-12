---
title: "Does khotkeys work on your KDE 4.1?"
date: 2008-07-29
forum: Desktop Environments
---

### Post by boom2k1 on 2008-07-29
I don't know if it is my installation (sudo apt-get install kubuntu-desktop from Ubuntu 8.04), or if it is a general Kubuntu 8.04 problem, or if it is a KDE 4.1 problem, but none of the khotkeys work(from System Settings -> Keyboard and Mouse -> Keyboard Shortcuts)

All I want at this moment is to have a keyboard shortcut for print screen and Run Konsole.

[I can get the konsole shortcut working using xbindkey, if I really want.]

Does everybody else have similar experience?

Overall, I am quite happy with KDE 4.1, except for some little things like this I find annoying, but I am really glad I tried it.

Thanks!

---

### Post by 34.50 on 2008-07-29
Yep, they work for me, and I'm usin a laptop

---

### Post by kuja on 2008-07-29
No, I can't get khotkeys to work either - I'm using KDE4 RC1 myself ... 

Note to 34.50: having your normal hotkeys working and having the program khotkeys working are two different matters entirely ... khotkeys is a mouse guesture/key binding/etc program.

---

### Post by bda on 2008-07-30
I have the same problem with kde 4.1, installed from the kubuntu launchpad apt sources. Hotkeys work fine in 3.5.

---

### Post by flying_icarus on 2008-08-01
Well, I got them to work somehow, the trick needed was the following:

1) Start menu editor, assign a shortcut to an application (i.e. for Firefox, I chose "Meta+F")

2) Open system settings applet, go into keyboard & mouse under computer administration, choose Keyboard shortcuts and in the fall-down menu instead of "kmix" or something chosen by default select "khotkeys"

An entry "K Menu - firefox.desktop" should now be present. Now, it can happen that it doesn't appear instantly, or at all untill you start menu editor again and save the configuration again (even if it wasn't altered), I'm not sure exactly when it appeared.  ~/.kde4/share/config/khotkeysrc is instantly updated with the new commands and shortcuts, but it takes some trial & error to get the entries to appear in khotkeys configuration. It may also help to terminate any running khotkeys process and start it again (i.e. from konsole with "pkill -15 khotkeys; khotkeys &" without the quotes and definitely without any sudo prepended).

Essentially, you fiddle with alternatly starting menu editor and system settings untill it appears.

3) The new "K Menu - firefox.desktop" has preselected the custom shortcut which is "none", but the default shortcut is "Meta+F" as set in the menu editor in step 1). Now you need to select the default shortcut for this item and confirm to "reassign from menu editor". After this the shortcut should start working.

So, the basic functionality seems to be there, only burried under unfinished user inteface.

Hope this helps. :)

One last bit of info - after restarting KDE the hotkeys didn't work again, apparently the khotkeys process doesnt get saved with the session. Just put it in autostart or start it manually and the shortcuts should keep on working.

---

### Post by rumburak on 2008-08-04
I suffer the same problem that my custom shortcuts don't work.

There must be something wrong with the KHotKeys since a custom shortcut I defined in "main surface" (dunno the english translation since I use german localization - the german term is "Oberfläche zur Ausführung von Befehlen") for locking a session (WINDOWS+L) works out fine.

@flying_icarus
I tried your workflow but that does not help. Furthermore I have multiple entries for apps in my KHotKeys settings. See attached screenshot.
Additionally I can no longer start apps from the K-Menu. Starting by ALT+F2 works fine, but clicking the entry in the K-Menu has no effect (paths are correct/unchanged).

So in fact that are 2 problems, but they may depend on each other. Nevertheless the shortcuts didn't already work when I COULD start the apps in the K-Menu then.

---

### Post by kuja on 2008-08-04
> **rumburak said:**
> I suffer the same problem that my custom shortcuts don't work.

There must be something wrong with the KHotKeys since a custom shortcut I defined in "main surface" (dunno the english translation since I use german localization - the german term is "Oberfläche zur Ausführung von Befehlen") for locking a session (WINDOWS+L) works out fine.

@flying_icarus
I tried your workflow but that does not help. Furthermore I have multiple entries for apps in my KHotKeys settings. See attached screenshot.
Additionally I can no longer start apps from the K-Menu. Starting by ALT+F2 works fine, but clicking the entry in the K-Menu has no effect (paths are correct/unchanged).

So in fact that are 2 problems, but they may depend on each other. Nevertheless the shortcuts didn't already work when I COULD start the apps in the K-Menu then.

My K-menu hasn't been working either. I think I got a crash at some point or another saying something about a corrupt k-menu list or something ... I wonder if that's related.

---

### Post by kuja on 2008-08-05
There were updates released earlier today that fix the kmenu not launching apps problem.

---

### Post by flying_icarus on 2008-08-07
> **rumburak said:**
> I suffer the same problem that my custom shortcuts don't work.

There must be something wrong with the KHotKeys since a custom shortcut I defined in "main surface" (dunno the english translation since I use german localization - the german term is "Oberfläche zur Ausführung von Befehlen") for locking a session (WINDOWS+L) works out fine.

@flying_icarus
I tried your workflow but that does not help. Furthermore I have multiple entries for apps in my KHotKeys settings. See attached screenshot.
Additionally I can no longer start apps from the K-Menu. Starting by ALT+F2 works fine, but clicking the entry in the K-Menu has no effect (paths are correct/unchanged).

Ok, I will for now assume that the kmenu started working again, and concentrate ond khotkeys. ;)

I have also noticed the duplicate entries, and found their source:
```
~/.kde4/share/config/kglobalshortcutsrc
```

They look something like this:
```
{6dad625b-0000-4000-be05-ed3e3cf362c3}=Meta+F,Meta+F,K Menu - firefox.desktop
```

If you delete such lines from kglobalshortcutsrc file and logout & login, they should be gone from the configuration gui. But apparently their appearance in there does not guarantee that the shortcut will work, the same key must be present in the ```
~/.kde4/share/config/khotkeysrc
``` as well, which in my case got created like this:

```
[Data_4_3]
Comment=
Enabled=true
Name=K Menu - firefox.desktop
Type=MENUENTRY_SHORTCUT_ACTION_DATA

[Data_4_3Actions]
ActionsCount=1

[Data_4_3Actions0]
CommandURL=firefox.desktop
Type=MENUENTRY

[Data_4_3Conditions]
Comment=
ConditionsCount=0

[Data_4_3Triggers]
Comment=Simple_action
TriggersCount=1

[Data_4_3Triggers0]
Key=Meta+F
Type=SHORTCUT
Uuid={6dad625b-0000-4000-be05-ed3e3cf362c3}
```

The Uuid in this case is the same for both, and if khotkeysrc process is not running, or if the khotkeysrc config file doesn't have the correct entry the shortcut again will not work.

So, try the following:

I have attached my khotkeysrc and kglobalshortcutsrc, go into .kde4/share/config in your home folder, rename your original files to something (i.e. add .bak at the end) and put my config files in their stead. Since they're default-generated apart from firefox, thunderbird and konsole additions, they should work on your system as well. 

Now log out and back in so the kglobalshortcutsrc gets re-read.

Then open konsole and issue 
```
# ps aux |grep khotkeys
```
If you see 2 lines (one will be from the "grep khotkeys" command above), and one of them just has "khotkeys" at the end, then you got khotkeys running, but maybe we should kill & restart it just to make sure it re-reads the configuration:
```
# pkill -15 khotkeys; pkill -9 khotkeys
```
After this the first command should list only "grep khotkeys" - that is our searching for the khotkeys process
Lastly, still in the command prompt, run the khotkeys again:
```
# khotkeys &
```
Hopefully you should see something like this while khotkeys starts up:
```
[icarus@andelain config]$ khotkeys &
[1] 11918                           
[icarus@andelain config]$ khotkeys(11919) KHotKeys::ShortcutsHandler::ShortcutsHandler: Initializing shortcuts_handler                                                                              
khotkeys(11919) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{f36ee83f-0000-4000-8102-831412ef66c6}"  -  "PrintScreen" : QKeySequence("Print")                                      
khotkeys(11919) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{f36ee83f-0000-4000-8102-831412ef66c6}"  -  "PrintScreen" : QKeySequence("Print") QKeySequence("")            
khotkeys(11919) KHotKeys::ShortcutsHandler::addAction: Creating action for  "{338b434f-0000-4000-ab55-5675442f8f9a}"  -  "K Menu - thunderbird.desktop" : QKeySequence("Meta+T")                    
khotkeys(11919) KHotKeys::ShortcutsHandler::addAction: Finished creating action for  "{338b434f-0000-4000-ab55-5675442f8f9a}"  -  "K Menu - thunderbird.desktop" : QKeySequence("Meta+T") QKeySequence("") 
((...and so on...))
```

Now try one of the shortcuts (in my config those are win+f, win+t and win+a) and see if it works.

If it does (as I hope it will), now we just need to make khotkeys run every time you log in, since it's not remembered in the session.

Create a file named i.e. khotkeys.sh in ~/.kde4/Autostart with the following contents:
```
#!/bin/bash
khotkeys &
```
and make it executable ("chmod +x ~/.kde4/Autostart/khotkeys.sh" in konsole or right click, properties, permissions, check "is executable"). This should make it start every time when you login.

Although this made it work for me in the end, it's definitely not as straightforward as it used to be. ;) Hopefully it will improove in one of the 4.1.x releases so more people can begin using it.

---

### Post by rumburak on 2008-08-08
Thx. I'll try this.
Meanwhile I got pretty used to ALT+F2 ;)

> **flying_icarus said:**
> 
```
# ps aux |grep khotkeys
```
```
# pkill -15 khotkeys; pkill -9 khotkeys
```


You can shorten this to
```

# pgrep khot

```
or
```

pkill -SIGKILL $(pgrep khot)
```

---

### Post by QCompson on 2008-08-09
Is this a kubuntu problem or a KDE4 problem?

Not being able to use a shortcut to quickly access a terminal is a complete show-stopper for me.

---

### Post by kuja on 2008-08-09
My approach to khotkeys as of late is to use xbindkeys ...

---

### Post by rumburak on 2008-08-09
> **QCompson said:**
> Is this a kubuntu problem or a KDE4 problem?

Not being able to use a shortcut to quickly access a terminal is a complete show-stopper for me.

Definitely a problem with KDE4.1. KDE3 runs perfectly.

For whom it may concern:
Btw. Unless the last library update, I cannot start some programs through the K-Menu. Some work, some others don't. I couldn't figure out the reason yet. At first I thought that there's a connection between starting apps with ALT+F2 and K-Menu not working, but that's not true.
Anyway - that's not a major problem to me now since I got used to ALt+F2, but it seems there's a little mess in some KDE4 libs..

---

### Post by QCompson on 2008-08-09
> **rumburak said:**
> Definitely a problem with KDE4.1. KDE3 runs perfectly.

Sorry, I didn't make myself clear.  I was wondering whether this was an issue with KDE4.1 specific to Ubuntu, or do all KDE4 distros (suse, fedora) have the same problem.  From a quick google search it seems like everyone looking for a solution to this problem is running Ubuntu.

Keyboard shortcuts seem like such a fundamental desktop usability tool.  I will be very discouraged if the KDE team has put off fixing this until 4.2.

---

### Post by GeneralZod on 2008-08-10
I've just asked mjansen, the current shortcut guru, and apparently KHotKeys does indeed not work correctly in 4.1.x.

He has a re-designed version in trunk and *hopes* that it will be released for 4.2, but has limited free time on his hands, unfortunately :/

---

### Post by QCompson on 2008-08-10
> **GeneralZod said:**
> I've just asked mjansen, the current shortcut guru, and apparently KHotKeys does indeed not work correctly in 4.1.x.

He has a re-designed version in trunk and *hopes* that it will be released for 4.2, but has limited free time on his hands, unfortunately :/

*Hopes* that it will be released for 4.2?  Stick with gnome it is then.  Am I the only one that constantly uses a keyboard shortcut to get to a terminal?  The KDE team has some strange priorities.

Thanks for the info GeneralZod.

---

### Post by GeneralZod on 2008-08-10
> **QCompson said:**
> *Hopes* that it will be released for 4.2?  Stick with gnome it is then.  Am I the only one that constantly uses a keyboard shortcut to get to a terminal?  The KDE team has some strange priorities.

Thanks for the info GeneralZod.

No problem, though like most volunteer-driven projects, the question of "priorities" often goes out the window: I'm sure that everyone would have liked it for 4.0.0, but unless someone with the necessary skills steps up (and the area of KDE's keyboard shortcuts seems to be unusually demanding, technically) and does the work, it won't happen, unfortunately.

---

### Post by QCompson on 2008-08-10
So I tried adding a shortcut for konsole through the advanced options -> input actions dialogue.  No luck.

Then I tried adding it through kmenuedit.  No luck.

Finally I set up xbindkeys, and that works, but now when I go to the keyboard settings dialogue in KDE's control center (I wanted to set F11 as full-screen), it instantly crashes.  Sigh.

---

### Post by rumburak on 2008-08-12
Indeed, it is unsatisfactory not to have properly working shortcuts. Anyway - using ALT+F2 and typing "kons" is almost as fast as a shortcut and I don't have to define any shortcuts at all. Not to be mistaken - I'd appreciate to have shortcuts working again but since it's not a "major" bug, I can live with the situation until then.

---

### Post by kuja on 2008-08-12
> **rumburak said:**
> Indeed, it is unsatisfactory not to have properly working shortcuts. Anyway - using ALT+F2 and typing "kons" is almost as fast as a shortcut and I don't have to define any shortcuts at all. Not to be mistaken - I'd appreciate to have shortcuts working again but since it's not a "major" bug, I can live with the situation until then.

You should try Yakuake.

---

### Post by QCompson on 2008-08-12
> **rumburak said:**
> Indeed, it is unsatisfactory not to have properly working shortcuts. Anyway - using ALT+F2 and typing "kons" is almost as fast as a shortcut and I don't have to define any shortcuts at all. Not to be mistaken - I'd appreciate to have shortcuts working again but since it's not a "major" bug, I can live with the situation until then.
It's all about what you are used to.  I've been using "Ctrl+T" to access the terminal for years and it drives me insane not to be able to access konsole in this manner (besides the fact that I'm constantly hitting ctrl+t with no result).  To me it is a major bug, because without this shortcut the desktop environment is completely unusable for me.  I also think ctrl+t is significantly faster than Alt+F2+kons.

Other than this issue, I find KDE4 to be shaping up quite nicely.  I was impressed with the improvements made between 4.0 and 4.1.  Hopefully this issue will be resolved by 4.2; I look forward to trying KDE4 at that time.

---

### Post by moore.bryan on 2008-08-15
i think the solution is to enable the khotkeys daemon in system settings; i.e., system settings > advanced > input actions > general settings > uncheck "disable khotkeys daemon."

---

### Post by wd5gnr on 2008-08-15
I have found that if you are using Compiz instead of kwin that you need to set the hotkeys in Compiz which is a shame since Compiz only has 10 slots for keys that I am aware of.

---

### Post by QCompson on 2008-08-16
> **moore.bryan said:**
> i think the solution is to enable the khotkeys daemon in system settings; i.e., system settings > advanced > input actions > general settings > uncheck "disable khotkeys daemon."
Nah.  The whole thing is just broken.  Both khotkeys and the input actions options.  There's a few bug reports on it, and it *may* be fixed by 4.2.

---

### Post by moore.bryan on 2008-08-17
> **QCompson said:**
> Nah.  The whole thing is just broken.  Both khotkeys and the input actions options.  There's a few bug reports on it, and it *may* be fixed by 4.2.
yeah... strangely my "fix" worked for about two boots and then stopped suddenly; VERY strange. why the skepticism on it being fixed?

---

### Post by QCompson on 2008-08-17
> **moore.bryan said:**
> yeah... strangely my "fix" worked for about two boots and then stopped suddenly; VERY strange. why the skepticism on it being fixed?
Based on GeneralZod's info earlier in this thread and there was an open bug report on it which said basically the same thing (bugs.kde.org seems to be down atm).  Apparently the developers are aware that it is broken but there is only one chap who is working on it, and he is quite busy already.

The bug report was getting a little heated, with one group of critics saying they couldn't understand why this wasn't a top priority, and another group saying "fix it yourself then!"  

I think the KDE developers are very sensitive to criticism for the time being, given the hailstorm of complaints/trolling/attacks they've endured since the release of KDE4.  

In any case, I can't use a desktop environment which doesn't allow me to set a keyboard shortcut to a terminal, so I'll wait it out.

---

### Post by moore.bryan on 2008-08-17
unfortunate about things getting too heated... kde4 is just one of my testing desktops, so the inconvenience is trivial to me; however, i'm part of the camp surprised this hasn't been made a very high priority.

---

### Post by Tamacracker on 2008-08-20
I really hope there's a new update to make it as simple as KDE3. I don't like the idea that I need to spend 10 minutes just to setup 1 hotkey in kde4. 

Overall, so far so good... just needs to be a tad more user friendly.

---

### Post by QCompson on 2008-08-20
> **Tamacracker said:**
> I really hope there's a new update to make it as simple as KDE3. I don't like the idea that I need to spend 10 minutes just to setup 1 hotkey in kde4. 

Overall, so far so good... just needs to be a tad more user friendly.
I'd spend 10 minutes if it would actually work.  I don't think there is a way to link a shortcut key to the K-menu either.  

:confused:

---

### Post by moore.bryan on 2008-08-21
> **QCompson said:**
> I don't think there is a way to link a shortcut key to the K-menu either.  
i think that's because it isn't kmenu anymore... just a plasmoid in the taskbar area. i've been trying to figure-out the "command" to launch it without success. perhaps someone else has greater insight?

---

### Post by QCompson on 2008-08-22
> **moore.bryan said:**
> yeah... strangely my "fix" worked for about two boots and then stopped suddenly; VERY strange. why the skepticism on it being fixed?
bugs.kde.org is back up.  Here is the link to the bug report:

[http://bugs.kde.org/show_bug.cgi?id=160892]("http://bugs.kde.org/show_bug.cgi?id=160892")

Note what Michael Jansen, a KDE developer, says:

> OK. Once again. It's not that we somehow decided to kill khotkeys . Some decisions in kde4 unrelated to the khotkeys code broke it. It's stopped working. Since noone is/was willing to work on it nothing happened. Then i came along and decided to do a redesign because the changes to kde4 global shortcuts handling broke some assumptions khotkeys made so i had to do a fairly big change to make it working. That was my decision and since noone else worked on the code noone complained. Feel free to resurrect and fix the kde3 khotkeys code and noone will object to your version substitute mine. I won't. But in unrelated news someone decided complaining isn't the right way to go and start coding/contributing so let's see and wait how that turns out. I still plan to work on khotkeys but real life stuff keeps me away. serious stuff. I will however assist the volunteer as much as i can. I hope to have time for kde again in the near future (1month). To rephrase khotkeys will get better with 4.2 but most likely not with the full kde 3.5 functionality. [B]khotkeys with 4.1 is broke and will stay that way until some wonder happens. 
[/B]

It's a bummer.

---

### Post by moore.bryan on 2008-08-22
hmm... the end of the bug report is interesting because it suggests people are trying to use the windows key as a modifier, which is what kde4.1 seems to be doing. the opposite is true of what i'm trying to accomplish; namely, the windows key opens the new plasmoid main menu.

i'm always in awe of developers... they have such wonderful talent and such soft egos.
:-)

---

### Post by GeneralZod on 2008-09-18
Just FYI:

[http://michael-jansen.biz/blog/mike/2008-09-18/kmenuedit-support-application-shortcuts-again](http://michael-jansen.biz/blog/mike/2008-09-18/kmenuedit-support-application-shortcuts-again)

---

### Post by gozala on 2008-11-29
Fixed in KDE 4.2

Post how to get it in 8.10

[http://ubuntuforums.org/showthread.php?t=982726#2]("http://ubuntuforums.org/showthread.php?t=982726#2")

---

