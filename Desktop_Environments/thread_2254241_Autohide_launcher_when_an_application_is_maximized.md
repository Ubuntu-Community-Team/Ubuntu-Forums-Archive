---
title: "Autohide launcher when an application is maximized"
date: 2014-11-25
forum: Desktop Environments
---

### Post by vasa1 on 2014-11-25
I don't use (or need) launchers but here's an interesting question about the Unity launcher: [How can I auto-hide the launcher via a script, when I maximize the browser?]("http://askubuntu.com/questions/553539/how-can-i-auto-hide-the-launcher-via-a-script-when-i-maximize-the-browser")

The code presented in the **body** of the question has reference to Unity 2D and doesn't work now but apparently it did at one time. But I don't see anything in the code that would indicate whether a window is maximized or not. How was that information obtained?

---

### Post by coldcritter64 on 2014-11-25
> But I don't see anything in the code that would indicate whether a window is maximized or not.I can't either, only seems to check for the presence of a browser open.

wmctrl usage : > -l     List  the windows being managed by the window manager. One line
              is output for each window, with the line broken up  into  space
              separated columns.  The first column always contains the window
              identity as a hexadecimal integer, and the second column always
              contains  the desktop number (a -1 is used to identify a sticky
              window). If the -p option is specified  the  next  column  will
              contain  the PID for the window as a decimal integer. If the -G
              option is specified then  four  integer  columns  will  follow:
              x-offset,  y-offset,  width  and height. The next column always
              contains the client machine name. The  remainder  of  the  line
              contains the window title (possibly with multiple spaces in the
              title).

except in the first answer .... wmctrl -l**G**, note the > If the -G
              option is specified then  four  integer  columns  will  follow:
              x-offset,  y-offset,  width  and height.
So dimensions are considered within the first answer where the question itself is not using that switch, it may be possible with some scripting to determine if a window is full or close to full size and then activate the hide launcher code using that sort of output, though I am missing how it is done myself reading that.
Even reading the following comments doesn't look good ....

> Very nice! only thing is that it also hides  the launcher on workspaces where there is no maximaized window (if there  is one one of the workspaces.and > --- and it works unpredictably sometimes, I have it running, nowhere a maximized window, in workspace 2/4 it autohides? may still need some work by the looks.

---

### Post by papibe on 2014-11-25
Moved to **Desktop Environments**.

---

### Post by vasa1 on 2014-11-25
Is there any command then to determine if a window is maximized? Or maybe to force a window to be maximized and then use some code to autohide a launcher?

**man wmctrl** has this but I don't have time to look at it right now:```
      -b  ( add | remove | toggle),prop1 [,prop2 ]
              Add, remove, or toggle up to two window properties simultaneously. The window that is being modified must be identified with a -r action. The property
              change  is  achived  by  using  the  EWMH _NET_WM_STATE request. The supported property names (for prop1 and prop2) are modal, sticky, **maximized_vert**,
              **maximized_horz**, shaded, skip_taskbar, skip_pager, hidden, fullscreen, above and below.  Two properties are supported to allow operations like maximiz&#8208;
              ing a window to full screen mode. Note that this action is made up of exactly two shell command line arguments.
```

This does it:```
$ wmctrl -r geany -b add,maximized_horz,maximized_vert
```

---

### Post by user1397 on 2014-11-27
I don't get why you don't just set the launcher to autohide in settings?

---

### Post by vasa1 on 2014-11-27
> **ubuntuman001 said:**
> I don't get why you don't just set the launcher to autohide in settings?Not me :)
I don't use any launcher. The question was raised by someone at Ask Ubuntu (linked to in the first post). My question was about the codes that were being discussed and it related to how those codes detected whether a window was maximized or not.

---

### Post by user1397 on 2014-11-27
> **vasa1 said:**
> Not me :)
I don't use any launcher. The question was raised by someone at Ask Ubuntu (linked to in the first post). My question was about the codes that were being discussed and it related to how those codes detected whether a window was maximized or not.
Ah I see.  So they want to have the launcher NOT on autohide, but when a window is maximized, it hides automatically? And then when the windows is not maximized the launcher reveals itself again?

---

