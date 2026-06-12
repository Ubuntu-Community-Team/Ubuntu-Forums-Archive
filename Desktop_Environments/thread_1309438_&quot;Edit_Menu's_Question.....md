---
title: "&quot;Edit Menu's Question...."
date: 2009-11-01
forum: Desktop Environments
---

### Post by wbee on 2009-11-01
Hello,

I have VLC set up as my default media player.

I took the http mp3 file from a radio station,put it in a text editor,and saved it to my music file.

When I double left click it,the VLC opens and the station starts playing.

Now,the problem. I opened (right click)applications>Edit Menus>(left column)Sound and Video>New Item.

When Create Launcher came up,I Browsed to the correct file,opened it,added the name,and clicked OK.

When I click the link from Sound and Vision,I get one of those wrong way road signs and it won't play.

What am I doing wrong?

How do I set this up correctly?

----------

Thank you

---

### Post by Turtle.net on 2009-11-01
you need to type the name (that's the name of the menu item) and then type the command line.
What did you typed for the command line ?
You can test the command line to enter by launching your application from a terminal first :)

---

### Post by wbee on 2009-11-01
Turtle.net,

When I "browsed" from "Create Launcher" and opened the file,it added this to the "command" box:

/home/wbee/Music/WCPE-FM

WCPE-FM is what I typed into the name box.(Which is what I named the file,which was a hypertext protocol mp3 file.)

When I typed it into the terminal,it returned "permission denied".

---

### Post by Turtle.net on 2009-11-01
If you cannot launch it from the terminal then it's normal that you can't launch it through a launcher.
Make sure that your file is executable ```
chmod +x WCPE-FM
``` and then try to launch it through the terminal.
But, if you type on the terminal ```
vlc http://xxxxx.mp3
``` does it work ?
If yes, then instead of creating a file just to say that, put this line in the command line box of the launcher. Should be the right way to do it.

---

### Post by wbee on 2009-11-01
Thank you.

The later solution worked perfectly.:-)

---

