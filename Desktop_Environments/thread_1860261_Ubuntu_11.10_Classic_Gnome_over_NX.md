---
title: "Ubuntu 11.10 Classic Gnome over NX"
date: 2011-10-14
forum: Desktop Environments
---

### Post by nstong on 2011-10-14
So I have classic gnome set up, I even have it as the default, no login.  However when I connect over NX (and I always connect over NX), I still have Unity.  Anyone have some idea of how I can have it load gnome classic?

---

### Post by nstong on 2011-10-14
Nevermind, if you go into the NX client setting you set up custom, with options to start new desktop and run the command 
gnome-session-fallbackIt completely looks like **** though.  Not sure why, but as I understood it there were big differences between this fallback and what there was in 11.04?  Anyone have ideas about what to install to make up those deficiencies?  Will probably just try KDE

---

### Post by hannes_a on 2011-10-15
[http://www.nomachine.com/fr/view.php?id=FR06I02466](http://www.nomachine.com/fr/view.php?id=FR06I02466)

actually, it's a feature request.
if everyone ask [http://www.nomachine.com/contactus.php](http://www.nomachine.com/contactus.php) they will see the urgent need of it

---

### Post by venik212 on 2011-10-15
I have the same problem and request, but was unable to petition NoMachine on the website you provided-- could not get through their Gotcha.....
Has anyone tried WinLive32?  
Gnomeless Unity might drive me away from Ubuntu...

---

### Post by nstong on 2011-10-17
I was pretty happy with what I had set up on 11.04, which I guess was the gnome 2 fall back when the unity did not work over NX.  Using the custom with command gnome-session-fallback, I can get a working gnome environment, however its just really slow and had stuff missing.  It looks better now that I installed gnome 3 (useless as it is over NX).  Is there any other gnome stuff I could install or tweak?  Or is the deficiency due to using the custom NX and missing settings that are part of selecting GNOME?

---

### Post by edvar on 2011-10-17
I'm having the exact same problem. Any ideas?

---

### Post by nstong on 2011-10-18
I have been using KDE, but that is still not as responsive as before.  Does anyone have an idea how to speed up NX on KDE?

---

### Post by edvar on 2011-10-20
KDE sucks on NX. Too slow...

I found a workaround. I copied the file gnome-terminal.desktop  from /usr/share/applications to the Desktop folder and gave it execute rights. After that I ran gnome-session-properties from the terminal and added an entry to get the command "metacity --replace" to run at startup.

After that it was just a matter of copying some other shortcuts I needed to the Desktop from /usr/share/applications like firefox, logout, etc. It's not perfect as the gnome panel doesn't work but at least I can launch some applications I need.

Another option is this: [http://www.linux-archive.org/ubuntu-user/588481-remote-nx-sessions-11-10-work.html](http://www.linux-archive.org/ubuntu-user/588481-remote-nx-sessions-11-10-work.html) . However it's not the best as it opens the panel, unity launcher and the desktop on different windows and you have to manually kill the process to terminate the session.

**_UPDATE_**: Nevermind my workaround... It seems the second option works perfectly with Unity 2D if you use the NX Player 4.0. The old NX Client 3.5 opens different windows for each element for some reason.

---

