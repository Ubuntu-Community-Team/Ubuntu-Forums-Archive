---
title: "Prism and Alltray not cooperating."
date: 2009-01-17
forum: General Help
---

### Post by Dirjel on 2009-01-17
I have GMail running through Prism using Alltray, so it doesn't eat up space in my window list.  I have it set to start at login automatically.  This works fine.  The command is as follows:
```
alltray prism-google-mail -na -st
```

I also have Pandora set up through Prism/Alltray.  I have a launcher for this one on my Gnome Panel, so it doesn't eat up resources unless I'm actually listening to music.  The command on this one is:
```
alltray xulrunner-1.9 /usr/share/prism/application.ini -webapp pandora.radio@prism.app -na
```

Independently, these work fine.  However, if I try and run them both simultaneously, I have problems.  Whichever one I open SECOND won't show up in the notification area.  I also have totem living in the tray, but the GMail/Pandora won't both appear simultaneously regardless of whether or not Totem is open.  I haven't tried another Prism/Alltray combo, mostly because I don't have another one set up.

If anyone knows how to fix this, let me know.  I'm gonna' do some more experimenting on my own.  Thanks.

EDIT:  Made a new prism, and tried to alltray it.  Worked fine by itself, but wouldn't co-exist with another Prism in the tray.

---

### Post by Dirjel on 2009-01-24
So, is this a problem with my computer, or with the applications?  Has anyone else tried this before?

---

### Post by Loco Ulysses on 2009-10-14
I realize this thread's a bit old, but I have the exact same problem. I can start one prism app with alltray (ie "alltray prism-google-mail") and it will go straight in the tray, and if I try to do so with a second (ie "alltray prism-google-calendar") it just appears as a prism window, with no icon in the tray. However, I can open prism, then call alltray and select the window with my mouse, and it will be added to the tray no problem.

Even a horrible kludge would be fine with me. So far I've looked into:

* Using "alltray -p <pid>" style command to capture prism after the fact, but this is still in development, and the newest versions don't support -g,-na,-st switches. Otherwise works okay. BUT, if yet a third prism app is opened, it has the same PID as the second one (that of (xulrunner-bin), and they will be captured together.
* Copying xulrunner-1.9, so I could run 2 separate processes. However, it is actually a script and copying it or changing it's name in any way seems to break it. Can't figure that one out...

So, if anyone has an idea. I just want the functionality I had with Fluid under OSX.

---

