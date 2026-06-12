---
title: "Keybinding to move window between screens"
date: 2009-04-26
forum: General Help
---

### Post by epic_fail on 2009-04-26
Hi everybody,

So today I decided to switch from Arch Linux back again to Ubuntu, and installed 9.04 on my PC. I have currently a dual screen setup working using the open source Radeon driver, even without messing with xorg.conf. It was the first time actually that the screen configuration tool really worked, so that is a big plus.

In Windows, I always used ultramon which featured custom keybindings to, for example, move windows between screens. So after I loaded an application, I used to use the keybindings to move to the correct screen. Now since I run just only Ubuntu and not dual-boot Arch / Windows XP, every time I have to move the window using the mouse to the correct screen. This works not very efficient I think, since I do most things using the keyboard.

So what my question is: is there a solution for Ubuntu so I can set a keybinding to move a window between screens? The default keybindings tool that comes with Ubuntu doesn't have that option, and I also checked the gconf-editor but found no entries that may do that.

I appreciate if anybody could help me on this, since I already smashed Windows through my window (:twisted:) and would like to configure Ubuntu to fit my needs.

[SIZE=1]By the way, a quick question: is it move windows **between** or **across** screens in [/SIZE][SIZE=1]English? :P[/SIZE]

---

### Post by lukjad on 2009-04-26
Now, I'm not entirely sure about this, since I have never used two screens, but what you are proabably looking for is Keyboard Shortcuts. They can be found in *System->Preferences->Keyboard Shortcuts*. The setting you are looking for it probably under the **Window Management** section.

---

### Post by epic_fail on 2009-04-26
> **lukjad007 said:**
> Now, I'm not entirely sure about this, since I have never used two screens, but what you are proabably looking for is Keyboard Shortcuts. They can be found in *System->Preferences->Keyboard Shortcuts*. The setting you are looking for it probably under the **Window Management** section.
As I said in my first post, I already looked there. Unfortunately there is no such option there :(.

---

### Post by geirha on 2009-04-26
In gconf-editor: /apps/metacity/window_keybindings/move_to_workspace_*

And by default you can move to the left or right workspace with ctrl+shift+alt+ arrow left or right

---

### Post by epic_fail on 2009-04-26
> **geirha said:**
> In gconf-editor: /apps/metacity/window_keybindings/move_to_workspace_*

And by default you can move to the left or right workspace with ctrl+shift+alt+ arrow left or right
No, that didn't work too :(. But guess what, I think I've found the solution!

In gconf-editor the following options:
/apps/metacity/window_keybindings/move_to_side_w
and
/apps/metacity/window_keybindings/move_to_side_e

Fixed! It behaves exactly right now how it did in Windows, cool!

---

### Post by epic_fail on 2009-04-26
Hmm, it seems like this works for all applications but Firefox. Luckily, since I use Opera that isn't really a problem.

---

### Post by lukjad on 2009-04-26
> **epic_fail said:**
> As I said in my first post, I already looked there. Unfortunately there is no such option there :(.
Well, I wasn't sure what you meant, so I decided to cover the obvious part first. :)

Anyway, glad you found the answer.

---

### Post by geirha on 2009-04-27
> **epic_fail said:**
> Hmm, it seems like this works for all applications but Firefox. Luckily, since I use Opera that isn't really a problem.

My best guess is that firefox also has the same keybindings bound to something else, and that firefox's keybindings override the window manager's.

---

