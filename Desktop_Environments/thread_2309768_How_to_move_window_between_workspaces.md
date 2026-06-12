---
title: "How to move window between workspaces"
date: 2016-01-13
forum: Desktop Environments
---

### Post by andrei90 on 2016-01-13
In **Ubuntu** I assigned [COLOR=#0000ff][FONT=courier new]CTRL+ALT+SHIFT+ARROW_KEY[/FONT][/COLOR] to move window to different workspaces.

Is there a way to switch Workspaces with my window in **Lubuntu** and assign a *Keyboard shortcut* for that, other than installing some unknown package that could mess up my configs...?

I've already edited the [COLOR=#0000ff][FONT=courier new]~/.config/openbox/lubuntu-rc.xml[/FONT][/COLOR] with my Keyboard Shortcuts, I only want to add this **workspace switcher** shortcut in here.

There must be a command or way that I could add between the [COLOR=#0000ff][FONT=courier new]<command>[/FONT][/COLOR] tags.

Thank you in regards,
*Daniel*

---

### Post by vasa1 on 2016-01-13
Have you looked at ```
    <keybind key="S-A-Left">
      <action name="SendToDesktop">
        <to>left</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Right">
      <action name="SendToDesktop">
        <to>right</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Up">
      <action name="SendToDesktop">
        <to>up</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="S-A-Down">
      <action name="SendToDesktop">
        <to>down</to>
        <wrap>no</wrap>
      </action>
    </keybind>

```
and ```
    <!-- Keybindings for desktop switching -->
    <keybind key="A-C-Left">
      <action name="GoToDesktop">
        <to>left</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="A-C-Right">
      <action name="GoToDesktop">
        <to>right</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="A-C-Up">
      <action name="GoToDesktop">
        <to>up</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="A-C-Down">
      <action name="GoToDesktop">
        <to>down</to>
        <wrap>no</wrap>
      </action>
    </keybind>
    <keybind key="W-F1">
      <action name="GoToDesktop">
        <to>1</to>
      </action>
    </keybind>
    <keybind key="W-F2">
      <action name="GoToDesktop">
        <to>2</to>
      </action>
    </keybind>
    <keybind key="W-F3">
      <action name="GoToDesktop">
        <to>3</to>
      </action>
    </keybind>
    <keybind key="W-F4">
      <action name="GoToDesktop">
        <to>4</to>
      </action>
    </keybind>

```?

---

### Post by andrei90 on 2016-01-13
Omg, so that's were it was hiding! Thanks a billion times :D

**S-A-Left** and **S-A-Right** solved it :D

---

### Post by vasa1 on 2016-01-13
You're most welcome!

I found these references to be very helpful in understanding what lubuntu-rc.xml (or *rc.xml) is all about:
[http://pclosmag.com/html/Issues/201011/page09.html](http://pclosmag.com/html/Issues/201011/page09.html)
[http://pclosmag.com/html/Issues/201107/page08.html](http://pclosmag.com/html/Issues/201107/page08.html)

---

### Post by andrei90 on 2016-01-14
Wow, those are awesome. Thank you so much :)

Can't wait to hackety-hack my rc :D

---

### Post by vasa1 on 2016-01-14
> **andrei90 said:**
> Wow, those are awesome. Thank you so much :)

Can't wait to hackety-hack my rc :D
But please keep a back-up :)

---

### Post by andrei90 on 2016-01-14
Yes of course, got it under [Git]("https://github.com/dminca/dotfiles/blob/devel/lubuntu/lubuntu-rc.xml"), I never start without a backup :) learned my lesson in the past

---

### Post by vasa1 on 2016-01-14
> **andrei90 said:**
> ...
Can't wait to hackety-hack my rc :D
Well, if you come up with something nifty, do share!

You could also visit the [BunsenLabs forum]("https://forums.bunsenlabs.org/index.php") to meet more Openbox users.

---

### Post by andrei90 on 2016-01-14
Cool. Will do :)

Almost everything that's code related I share it on [Github]("https://github.com/dminca") :KS

---

### Post by vasa1 on 2016-01-15
> **andrei90 said:**
> Yes of course, got it under [Git]("https://github.com/dminca/dotfiles/blob/devel/lubuntu/lubuntu-rc.xml"), I never start without a backup :) learned my lesson in the past
For some reason, I get a 404 with the link above but this works: [https://github.com/dminca/dotfiles/blob/master/lubuntu/lubuntu-rc.xml](https://github.com/dminca/dotfiles/blob/master/lubuntu/lubuntu-rc.xml).

---

### Post by andrei90 on 2016-01-15
Yes, that's because I've drafted a new release of the *dotfiles project *and the dev branch has been merged with the master branch
It can be found now on
[https://github.com/dminca/dotfiles](https://github.com/dminca/dotfiles)
in /lubuntu/...xml

BTW in case you're interested, I've also created a [script]("https://github.com/dminca/dotfiles/blob/master/lubuntu/clearme.sh") that optimizes PC performace by moving Swap data to RAM (if RAM memory is available).
Tested on my localhost with runtime 1day and 7hrs and it moves flawless, no lag, no slow motion on windows or something. :)

The script is in /lubuntu/clearme.sh

---

