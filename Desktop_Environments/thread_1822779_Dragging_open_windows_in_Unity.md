---
title: "Dragging open windows in Unity?"
date: 2011-08-11
forum: Desktop Environments
---

### Post by HiFlight on 2011-08-11
I can only reposition (drag)  opened windows within the workspace switcher, but not in an opened desktop.  Is this normal for Natty Unity???

---

### Post by sikander3786 on 2011-08-11
You should be able to drag those on the desktop too. Try holding down <Alt> key and then you should be able to grab the window from anywhere and not just the title bar and move it.

---

### Post by mcduck on 2011-08-11
Make sure you have the "Move" plugin enabled in Compiz settings. (You can use Compizconfig Settings Mananger to do that, or alternatively running "unity --reset" in a terminal might do the trick as well.)

---

### Post by HiFlight on 2011-08-11
> **sikander3786 said:**
> You should be able to drag those on the desktop too. Try holding down <Alt> key and then you should be able to grab the window from anywhere and not just the title bar and move it.


"Move" is enabled, holding down the "ALT" key will allow me to drag, but there is no title bar on any of the open child windows to grab for dragging.  Also, I don't find any means of resizing an open window.   Other than these niggles, Unity seems to be working fine.  I would like to find a means of overcoming these minor annoyances, however.  

Thanks for the suggestions!

---

### Post by HiFlight on 2011-08-11
> **HiFlight said:**
> "Move" is enabled, holding down the "ALT" key will allow me to drag, but there is no title bar on any of the open child windows to grab for dragging.  Also, I don't find any means of resizing an open window.   Other than these niggles, Unity seems to be working fine.  I would like to find a means of overcoming these minor annoyances, however.  

Thanks for the suggestions!

Well, I did find an almost invisible grab handle in the lower right corner of an open window for resizing, and found that ALT F10 will maximize a window once again when reduced, as the sizing symbols are missing in the top panel after reducing the size from maximized.  

There are still no title bars showing to grab for moving a window except the global bar in the top panel, which does not work for grabbing and moving.  Only the ALT key or Workspace Switcher seems to work for dragging a window.

---

### Post by mcduck on 2011-08-11
> **HiFlight said:**
> "Move" is enabled, holding down the "ALT" key will allow me to drag, but there is no title bar on any of the open child windows to grab for dragging.  Also, I don't find any means of resizing an open window.   Other than these niggles, Unity seems to be working fine.  I would like to find a means of overcoming these minor annoyances, however.  

Thanks for the suggestions!

Ah, so actually moving windows works just fine, but your problem is that you are missing the title bars? It's definitely not apparent for you first post...

What happens if you open a terminal and run "gtk-window-decorator --replace"?

---

### Post by HiFlight on 2011-08-11
> **mcduck said:**
> Ah, so actually moving windows works just fine, but your problem is that you are missing the title bars? It's definitely not apparent for you first post...

What happens if you open a terminal and run "gtk-window-decorator --replace"?

When I try to run that command in terminal, it never completes the process and shows a continuously blinking cursor.    Perhaps that command can be executed via a menu setting in Ubuntu Tweaks or CompizConfig Manager to make the change permanent?

While the process is running in Terminal, the title bars show on the child windows just fine, but whenever I close terminal, they again disappear.  Is there a way to make this permanent and be able to close Terminal without reverting back to the lack of title bars?

---

### Post by mcduck on 2011-08-11
It's not supposed to complete, it's supposed to keep on until you stop it or close the terminal. (I didn't ask you to run the command so that it would fix the problem, which it doesn't do, only to check if the decorator works and the problem disappears when it's started manually)

Anyway, since that fixes the problem you should check that the Window Decoration-plugin is enabled in CompizConfig Settings Manager, and that the "command" field in that plugin's settings is set to "/usr/bin/compiz-decorator".

---

### Post by HiFlight on 2011-08-11
> **mcduck said:**
> It's not supposed to complete, it's supposed to keep on until you stop it or close the terminal. (I didn't ask you to run the command so that it would fix the problem, which it doesn't do, only to check if the decorator works and the problem disappears when it's started manually)

Anyway, since that fixes the problem you should check that the Window Decoration-plugin is enabled in CompizConfig Settings Manager, and that the "command" field in that plugin's settings is set to "/usr/bin/compiz-decorator".


I did check those settings in CCSettings Manager and they were correct, but I unchecked and rechecked the WD pluging box and now the title bars are present on all child windows.   Hopefully, this will permanently solve this aggravating niggle!     My Unity now seems like it is working very well with no apparent problems.  Now that the problems have been fixed, I prefer Unity to Classic. 

Thanks much for all the useful help, mcduck, it is very much appreciated!

---

