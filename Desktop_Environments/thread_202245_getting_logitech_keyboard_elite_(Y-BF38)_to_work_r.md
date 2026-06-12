---
title: "getting logitech keyboard elite (Y-BF38) to work right"
date: 2006-06-23
forum: Desktop Environments
---

### Post by dantx24 on 2006-06-23
I bought a logitech keyboard elite model number (Y-BF38) at Wal-Mart a while back, and have never been able to get all of the special keys to work (from what i read its a kernel problem, extra scan codes have to be mapped or something), best explanation i found was here: [https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/46586](https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/46586) , this fix was for a different model of logtiech elite, some scan codes are different. I tried to implement it, but ran into a hangup when it came to editing the rules files.

My keyboard is supported under lineak, BUT, this still doesn't work because it still runs into the kernel limitation. 

I am a complete moron when it comes to anything behind the GUI ](*,) 

I know you need more detail, please let me know how i can provide more useful information, its irritating that I can't provide scancodes via xev, becuase it reports most of them as having the same code, 230 
(now i need to restore my config files, screwed things up worse trying to use that bugfix)

sorry for being semi-coherant, but I have no idea what I'm doing.

I'd appreciate any help, or comments (other than "go back to windows".) 
thanks

---

### Post by lastdeadmouse on 2006-12-16
I have exactly the same problem.  Anyone?

---

### Post by B00R4dL3y on 2007-02-26
I found that you can use Banshee Music Player to configure some of the keys.

Once you have Banshee open, go to the Edit > Plugins... menu.  Then check/click Multimedia Keys option, then Configuration tab on the right.  Then click on Configure Keyboard Shortcuts.  A window will open and you can set the keys for what actions are available.  I was able to set most of the keys.

I wanted to set the Shopping button to open the calculator, but it didn't work.  Maybe I don't have the right calculator program installed that it wants to open?

Anyways, hope this helped someone.


Oops... this is the same thing as going to the System > Preferences > Keyboard Shortcuts.

Just ignore my post.

---

### Post by RedSquirrel on 2007-02-26
Is the "logielite" model specified in your /etc/xorg.conf?

Save a backup of your xorg.conf file:

```
sudo cp /etc/xorg.conf /etc/xorg.conf.bak
```Then have a look in /etc/xorg.conf.

There should be section something like this:

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

```Comment out the generic model (pc105 or similar) and add the "logielite" model.

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
#       Option          "XkbModel"      "pc105"
        Option          "XkbModel"      "[COLOR=DarkOrange]**logielite**[/COLOR]"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

```What does xev tell you with that keyboard model?

---

### Post by Mana82 on 2007-04-13
i dont know if this helps but i found this really easy... i just went into keyboard shortcuts, added the multimedia keys to what i wanted, and then went into amarok and did the same thing in there.  i guess i got lucky cos i dont use the other buttons like favs shopping etc. just the music control buttons.

---

