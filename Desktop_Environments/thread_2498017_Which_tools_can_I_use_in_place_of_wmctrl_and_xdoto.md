---
title: "Which tools can I use in place of wmctrl and xdotool in Wayland? Revived"
date: 2024-05-26
forum: Desktop Environments
---

### Post by josephj on 2024-05-26
This closed [thread]("https://ubuntuforums.org/showthread.php?t=2475972") was somewhat hopeful.

It's been two years since then. Are things any better?

I work on the  [AutoKey]("https://github.com/autokey/autokey") project (mostly in support).

AutoKey is a desktop automation tool which allows the user to expand phrases and run arbitrarily complex Python scripts at the press of a hotkey (shortcut) sequence. It emits keyboard and mouse events and manipulates application windows in a way that makes most applications behave  as if the user had done these actions.

AutoKey only works on X11 and now that X11 support is fading away, I (and  lot of users) would hate to see it die.

We did some exploratory work using uinput for keyboard and mouse actions with some success, but also need to work with application windows.

I have seen some references to Wayfire, but have no experience with it.

Any help or insights would be appreciated as well as better topic tags.

---

### Post by TheFu on 2024-05-27
ydotool does many things that xdotool did, but not all of them.
KDE has some specific capabilities that Gnome-based DEs don't provide, but the ones in KDE are impressive.

I've never used AutoKey.  Been using **xdotool** scripts and **cnee** for automation that couldn't be handled by **Selenium IDE**.  Selenium (the non-IDE version) is too hard.  Of course, most of my automation is either bash or perl scripts.  The CLI will never die.  I took simple Selenium IDE scripts and created some perl code to create those scripts that can be maintained outside the point-n-click world (which is prone to human error) so that inside a webpage, specific CSS items could be clicked, not just specific locations on the screen.

Does AutoKey send events to specific widgets and not to specific X,Y locations?

---

### Post by josephj on 2024-05-28
Thanks for the reply.

TL;DR: No, neither.

AutoKey does the same sorts of things your scripts do and can even call such scripts. The difference is that you have to invoke your scripts yourself and AutoKey does it for you on demand at the press of a hotkey...

AutoKey's claim to fame is that it allows you to press a hotkey and then it does things as if it were you doing them, so it has no special knowledge of the active web page or application window. This is a double-edged sword. The good part is that it just works with almost anything. The bad part is the same thing. By default, it marches ahead even if its events are going to the wrong fields... It depends on the user to assure that initial conditions are as expected - the text cursor is where it is expected to be... before an action is invoked. Since AutoKey scripts are written in full Python3, the user can handle some of these problems on their own if they are sufficiently skilled.

To make things a bit better, AutoKey supports optional window filters. If the filter regex for the action that the hotkey would invoke doesn't match the active window title or class, then AutoKey does nothing and the application receives the hotkey...
This is one of things we don't know how to do in Wayland.

----

There is also an option to call out to visgrep, part of Xautomation, which can search the screen for a small image (e.g. a button) and then move the mouse there or click there. This great feature doesn't really get used though and it doesn't look like the Xautomation project has been maintained for quite a while, so this capability will most likely have to be dropped.

----

I took a brief look at cnee and the Selenium IDE. They both appear to address automated testing of websites. AutoKey works primarily at the application window level and doesn't care (or even know) if the application is a browser, a text editor, or an interactive game.

---

### Post by TheFu on 2024-05-28
cnee/xnee doesn't care about the app - or even if there is an app under it.  It can be a browser or not.   Sounds just like AutoKey.

As for scripts - WMs almost always have a capability of assigning keyboard chords to invoke anything.  Call them "hot keys" if you like. Same thing, just without running yet another app.  This has been part of X/Windows 35+ yrs - perhaps since the mid-1980s.  My WM is **fvwm**.  In the config file for it, I have
```
Key f   A  4  Exec /usr/bin/firefox.sh
Key t   A  4  Exec /usr/bin/thunderbird.sh
```
which sets up 4th level keys to launch programs.  fvwm has been around since just after mwm.
**openbox** has an XML file for stuff like this. Almost all WMs do - I say almost because I haven't looked at every possible WM, but I've looked at 20+ of them and they all have a method.  

Selenium IDE and Selenium are most definitely for automating browsers.  Selenium IDE is limited to inside the browser area.  For example, it cannot Save As .... from the browser menu to grab a complex webpage that is full of javascript and requires getting to it through multiple other javascript webpages first.

AutoKey using Python3 is fantastic, if you know or like Python.  I could never get used to the mandated indentation methods python requires. Too many decades programming in languages that don't use whitespace as important aspects for decisions.  OTOH, all the new kids learn python and it is a great language if you can un-learn habits.

Anyway, this isn't helping you to find 100% replacements for to use.  I don't see X/Windows going away as quickly as claimed.  There are too many features still lacking in Wayland.  It breaks many of my most important automation workflows, so I suspect it breaks workflows for others as well.  Nearly everything I do is running programs on other computers, not the one I happen to be sitting behind at the moment.  Additionally, I seldom use any remote-desktops, unless I'm 100% using them from a different country where I didn't want to bring any data at all.  When I travel to those places, I bring a very lite Linux that only has VPN client, ssh-keys, and a remote desktop client on it.  If I need to run any automation, it will happen inside the remote desktop.  I tend to use x2go, which is NX based for this, if any internet connectivity is possible.

Google found this project: [https://git.sr.ht/~geb/dotool](https://git.sr.ht/~geb/dotool)  written in Go.  You've probably seen it.

---

### Post by vanadium on 2024-05-30
Not a lot has changed since then. For simulation of keyboard events and mouse clicking, ydotool does a good job, but there is also dotool to which TheFu linked, which I currently use instead. These can be used for automated typing and clicking, with all the caveats of a keyboard macro approach outlined in your post #3.

With respect to window manipulation, thinks are a lot more difficult because this is handled at the level of the Wayland compositor. That means that methods to do so are different and specific between Gnome Shell, Plasma, Hyprland, ... For Gnome Shell, there are Gnome Shell extensions that expose dbus interfaces, allowing to obtain information and manipulate windows through dbus commands.

For text expansion, I since long rely on a script inspired by Dmitri Popov's snippy ([https://www.linux-magazine.com/index.php/layout/set/print/Issues/2014/162/Workspace-Text-Expander/(tagID)/92)](https://www.linux-magazine.com/index.php/layout/set/print/Issues/2014/162/Workspace-Text-Expander/(tagID)/92)). I migrated it to Wayland using ydotool (now dotool) instead of xdotool, and wl-clipboard
instead of xclip.

I posted a basic version here: [https://askubuntu.com/a/1514090/558158](https://askubuntu.com/a/1514090/558158). Essentially you type an abbreviation, e.g. "br" for "Best regards...". When hitting the shortcut key for the script, the script will 1) select the word before the cursor 2) retrieve the snippet with the corresponding file name and place that on the clipboard and 3) paste the clipboard contents, i.e., the text snippet. Retrieving text and pasting it through the clipboard is much faster and more reliable for larger snippets than having it typed out using dotool. Such script can be expanded to save and restore existing text on the clipboard, and I documented such attempt [here](https://askubuntu.com/a/1510281/558158).

In brief, your work at the level of window manipulation will be rather problematic, because of the fragmentation in implementation that Wayland introduced.

---

### Post by josephj on 2024-05-30
@TheFu
Thanks. I have a couple of keys bound to scripts in Ubuntu. AutoKey just makes it a lot easier and has some supporting features. It also does phrases which are somewhat like a very powerful auto-correct feature.

I had not seen dotool. It looks interesting. I bookmarked it.

@Vanadium
Thanks for your input. Sounds like we would have to do something like window manager specific plugins and that would be a lot of work, especially since app and, most likely window manager developers never consider automation when they update their offerings, so their changes frequently break  automation.

One of these days we'll have AIs that can replace all these tools with agents that just do what we want them to. Until then, I think we need a rewrite of Xautomation for Wayland (if possible). Then our tools can just "look at the screen" and figure out what to do based on what they "see" without a deep knowledge of window managers, etc.

---

