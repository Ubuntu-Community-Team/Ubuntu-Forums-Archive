---
title: "Do these window border features exist?"
date: 2010-05-03
forum: Desktop Environments
---

### Post by theLured on 2010-05-03
I want to control my windows without the normal buttons like close minimize and maximise.
I have a clean lucid install.

I want to use my mouse buttons to control the windows.
On the title bar
Middle click: close(i already use this with cairo-dock. It's great.)
Scroll up: restore/maximize
Scroll down: minimize
Double left click: make always on top
Double right click: make sticky

I'm probably asking for something that doesn't exist. I thought of it whilst reading about Esfera and someone said it should turn the whole title bar into a control area.

---

### Post by sanderd17 on 2010-05-03
I don't think this exists. But there exist mouse gestures for linux. see [http://www.makeuseof.com/tag/enable-mouse-gestures-linux-easystroke/]("http://www.makeuseof.com/tag/enable-mouse-gestures-linux-easystroke/") Or anotherone: gestikk but I don't know if it's still active.

Maybe you can contact a developer to ask if this would be possible or if it exists. I think I wouldn't use this type of gestures but I wouldn't use Esfera to.

---

### Post by stinkeye on 2010-05-03
Easystroke is good.
You can also use easystroke to map mouse buttons to any command or keyboard shortcut.

---

### Post by zlatkart on 2010-05-03
with openbox you can have all of this (I think)

---

### Post by theLured on 2010-05-04
Thanks for all the suggestions. I am now using easystrokes because I don't have to go all the way to the top of the window to do the action. Plus it's easier.

Here's how I set it up. I also installed wmctrl as it helps with setting windows to "always on top" and "on all workspaces"

1. install easystroke and wmctrl
2. load it up and click on the icon in the system tray

3. Click add action and set them like this

To add the stroke click "record stroke" after entering the details
```
Stroke           Name              Type      Details
Down             Minimize          Key       Alt+F9
Up               Maximize/Restore  Key       Alt+F10
Diagonal Up      Close             Key       Alt+F4
Diagonal Up      Close             Key       Alt+F4
Diagonal Down    Close             Key       Alt+F4
Diagonal Down    Close             Key       Alt+F4

You will need to install wmctrl for these 2 commands.
Sticky means to show on all of the workspaces.
Circle or curve	 Sticky            Command   wmctrl -r :ACTIVE: -b toggle,sticky
Up curve	 Above all         Command   wmctrl -r :ACTIVE: -b toggle,above
```


These next steps are for audacious the audio player. Might be useful if you want gestures for only 1 program.

4. Click Add group. Name the group Audacious
5. Click add application and then selected the player.
6 .Click application again and selected the playlist.
7. Click on the Audacious group that you made. This will make sure it add's the gesture to both the player and playlist.

8. add these commands.
```
Stroke              Name        Type        Details
Line to the left    Previous    Command     audtool2 playlist-reverse
Line to the right   Next        Command     audtool2 playlist-advance
```


Once again. Thanks for the suggestions. Linux rules.

---

### Post by stinkeye on 2010-05-04
> **theLured said:**
> Here's how I set it up. I also installed wmctrl as it helps with setting windows to "always on top" and "on all workspaces"

Seeing as you installed wmctrl, you might like this command.
```
wmctrl -r :ACTIVE: -e 0,400,250,800,500
```

From man wmctrl
```
A  move  and  resize  argument  has  the  format
              'g,x,y,w,h'.   All five components are integers.
              The first  value,  g,  is  the  gravity  of  the
              window,  with 0 being the most common value (the
              default value for the window).  Please  see  the
              EWMH specification for other values.

              The   four   remaining  values  are  a  standard
              geometry specification: x,y is the  position  of
              the  top  left  corner of the window, and w,h is
              the width and height of  the  window,  with  the
              exception  that  the value of -1 in any position
              is interpreted to mean that the current geometry
              value should not be modified.

```

I use this a lot because  I only like a fullscreen window when web browsing.It resizes and centres the window to my 1680x1050 screen.

---

### Post by theLured on 2010-05-04
Thanks. That was really helpful. I don't use windows in the center of the screen much.
I do use them at the four corners though, so I've changed it to


# top left
wmctrl -r :ACTIVE: -e 0,0,0,800,500
# bottom left
wmctrl -r :ACTIVE: -e 0,0,550,800,500
# top right
wmctrl -r :ACTIVE: -e 0,880,0,800,500
# bottom right
wmctrl -r :ACTIVE: -e 0,880,550,800,500

My gestures are a line up and to the right, means top right. A line going down and to the left, is for the bottom left.
And a circle for center.

---

