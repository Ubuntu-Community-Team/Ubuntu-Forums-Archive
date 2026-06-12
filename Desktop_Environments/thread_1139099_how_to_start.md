---
title: "how to start"
date: 2009-04-26
forum: Desktop Environments
---

### Post by num on 2009-04-26
how to start up a command line program in terminal such as tightvnc?

---

### Post by pastalavista on 2009-04-26
It depends on how and where it was installed. Mostly you should cd to the directory the executable .bin or .sh or whatever it is and use some variation of ```
./tightvnc
```I'm a relative newb to Linux but I have figured a few things out like that.

---

### Post by ljerabek on 2009-04-26
To find where it is installed from the command prompt run the following:

sudo find /* -name "tightvnc"

or

sudo find /* -name "*tightvnc*"

This should show you the path to that file if it's on your system.

---

### Post by num on 2009-04-28
once i know the path how i start it?

---

### Post by cariboo on 2009-04-28
You should have to type the complete path to start the application. there are to different tightvnc pprograms, the server and the viewer. to start the server in a terminal type:

```
tightvncserver
```

to start the viewer:

```
xtightvncviewer
```

---

### Post by SharkSpace on 2009-04-28
It depends which application your are running.  If you are trying to start the server the command 

[PHP]vncserver :1 -geometry 1024x768 -depth 16 -pixelformat rgb565 			 		[/PHP]

Should work for you.  Just configure to your needs.  No path would be required.

---

