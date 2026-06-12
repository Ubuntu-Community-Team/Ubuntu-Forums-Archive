---
title: "System -- Preferences -- Sessions dialog won't load"
date: 2005-04-19
forum: Desktop Environments
---

### Post by shakin on 2005-04-19
I'm trying to add a program to my startup. I know this was working before, but I haven't used it in a few weeks so tracing which update or config change broke it would be hard.

When I click the 'Configure your sessions' launcher it begins to load and the window shows up in the window list bar saying "Starting Sessions", but then it disappears. I never see an actualy window for the app.

I tried running gnome-session from the terminal, but I don't know if that's the right command. It gave an error about not being able to read my .ICEAuthority file. I have noticed that I've been needing to delete my .ICEAuthority file quite often because otherwise I can't login. Not sure if that's related.

---

### Post by shakin on 2005-04-19
I solved my own problem after searching the forums for .ICEAuthority. I believe the Sessions problem is related to running K3B while I'm in Gnome because K3B somehow interacts badly with the .ICEAuthority file.

I chmodded 600 my .ICEAuthority file, restarted X and haven't touched K3B and now I can get into Sessions.

---

