---
title: "Can I show someone a screensaver remotely?"
date: 2008-01-30
forum: Desktop Environments
---

### Post by rubbsdecvik on 2008-01-30
I'm in a Linear Algebra class and we were talking about 4 dimensional objects, and I remembered that I have a Regular 4D Prototypes screensaver.  I want to just show him the screensaver without having to go through all the screensaver preferences.  The catch... I want to do this remotely if possible.

Here's the set up.  I have a desktop computer in my room running Ubuntu.  I have a laptop that I bring to class that has Windows (I know it sucks, but it's the schools laptop and I can't install Linux on it.).  I have putty and Xming installed on the Windows machine and I have lots of success forwarding X11 through ssh.  But what I want to do is log on to the desktop computer in my room (I can do that part) run a command and then see this particular screensaver, preferably in a window.  

If I can't do this I'll get over it.  But I just thought it would be cool to try, but I don't know how to envoke a screensaver through the commandline.

---

### Post by Dark Hornet on 2008-01-31
Well, I would recommend using VNC, but the issue you are going to run into is rendering 3d movement, etc.  Any screen saver that moves, or watching movies, etc....over a connection like VNC, or ssh, etc will not look very good, and this is simply because of bandwidth issues...usually.

---

### Post by rubbsdecvik on 2008-01-31
Thats what I was afraid of.  I guess I'll have to see if I can't just boot off a liveCD and show him then.

Thanks

---

