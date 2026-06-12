---
title: "Right click to go back in nautilus."
date: 2016-07-20
forum: Desktop Environments
---

### Post by psyoma on 2016-07-20
In Firefox and Chrome you can right click and choose to go back to the previous page/directory.
 It is convenient as I don't have to move my mouse all the way to the corner to navigate. Is there a way to add this feature to Nautilus? 
[IMG]http://i.imgur.com/uuZZuUg.png[/IMG][IMG]http://i.imgur.com/Ze0vUK9.png[/IMG]

---

### Post by CantankRus on 2016-07-21
You could use alt +left/right to go back and forward in all three applications mentioned.
But as you seem to prefer to use the mouse, have a look at **easystroke** mouse gestures.
Set up gestures to run the alt+left/right key combos and you will have a universal way to navigate using the mouse.
If you do use, change the gesture button to 3 which feels more natural.
[**_[COLOR="#B22222"]Youtube: EasyStroke Mouse Gestures[/COLOR]_**]("https://www.youtube.com/watch?v=sOWXAyOde18")

You can set gestures or mouse buttons to run commands or keystrokes.
These are some of the commands I use with easytroke utilizing wmctrl and xdotool.
[LIST]
[*]maximize/unmaximize........... wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz
[*]minimize......... xdotool windowminimize $(xdotool getactivewindow)
[*]Resize and centre window......... wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz && wmctrl -r :ACTIVE: -e 0,485,250,818,485
[/LIST]

---

### Post by psyoma on 2016-07-23
Thanks [[COLOR=#000000]@CantankRus, [/COLOR]]("https://ubuntuforums.org/member.php?u=1938181")that looks like a possible solution. I'm a big fan of keyboard shortcuts and use them all the time, but when I'm browsing with a mouse, it's nice to save on repetitive motions. I'll be downloading easystroke and checking it out today. Thanks again.

---

