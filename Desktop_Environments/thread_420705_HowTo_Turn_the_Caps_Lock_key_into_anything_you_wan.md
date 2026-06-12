---
title: "HowTo: Turn the Caps Lock key into anything you want!"
date: 2007-04-23
forum: Desktop Environments
---

### Post by kwilliam on 2007-04-23
There's several tutorials on "How to disable the Caps Lock key" and both Gnome and KDE have settings somewhere to "Make the Caps Lock key act like a Ctrl key".  But the caps lock key is very conveniently positioned; what about making it do something *really* useful, like switch between windows?  This howto shows how to turn the Caps_Lock key into an F13 key that you can map however you like. (If you already have F13, choose a different name.) I used Kubuntu, but something similar ought to be achievable in Gnome.

1. Find out what the keycode of your caps lock key is by running xev and pressing the key. xev outputs a lot of jumbo, so to make it easy we can pipe its output to grep and search for "Caps_Lock". Open a terminal and type:

```
$ xev | grep Caps_Lock
```

Hit the caps lock key. You should end up with something like:
(colored for emphasis)
```
state 0x10, keycode [COLOR="Red"]66[/COLOR] (keysym 0xffe5, [COLOR="#ff0000"]Caps_Lock[/COLOR]), same_screen YES,
```
My keycode for Caps Lock is 66.
when you're done, you can close the window xev opened to end xev.

2. Now make a file called capslock.sh containing the lines:
```
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "keycode [COLOR="#ff0000"]66[/COLOR] = F13"
```

where [COLOR="#ff0000"]66[/COLOR] is the keycode you just found. Make it executable and test it.
```
$ chmod +x capslock.sh
$ ./capslock.sh
```

now run xev (without piping to grep) and hit the caps lock key. It should say it's F13 instead of Caps_Lock.

3. Now that we know the shell script works, make sure it's called automatically each time you log in. In KDE, do this my placing it in the ~/.kde/Autostart directory. In Gnome, I think there is a GUI that let's you add commands to run on login.

4. Now the fun part is making your new F13 key do something useful! You could give it different meanings in different programs, or assign it a global action. I decided to make it emulate Alt+Tab by switching to the previously focussed window. (Useful if you are switching between two programs a lot.) I only know how to assign global shortcuts in KDE, so Gnome people will have to add that info below I suppose.

*KDE Method 1: Make Caps_Lock perform an already defined action.*
Go to Control Center --> Regional & Accessibility --> Keyboard Shortcuts. Find the action you want ( "Walk Through Windows" in my case) and add "F13" as a primary or alternate shortcut. I had already assigned Ctrl+\ as an alternate Alt+Tab, so that I could walk through windows with my right hand as well. So I used KDE Method 2.

*KDE Method 2: Make Caps_Lock run a command.*
In Control Center --> Regional & Accessibility --> Input Actions create a Keyboard Shortcut that executes the command you want. I looked through the kwin dcop interface but didn't find the "Walk Through Windows" command, so I choose to run "xsendkeys Alt+Tab" when F13 is pressed. (xsendkeys lets you simulate keystrokes to the X window system. If you don't have the xsendkeys program installed it is in the lineakd package, at least in Feisty.)

Hope this is useful to someone!

---

### Post by YourSurrogateGod on 2007-04-23
Nevermind, stupid question.

---

### Post by bran on 2007-04-24
Many thanks!  given that the times i hit capslock on my laptop are 100% accedental this is a boon... for me I turned it into Shift_L... very useful.

---

