---
title: "XDMCP issues w/ certain apps and KDM"
date: 2007-10-27
forum: Desktop Environments
---

### Post by Defrector on 2007-10-27
Attempting to connect to Kubuntu (ubuntu 6.10) via XDMCP, I encountered some problems:

Attempting to see the login screen on my terminal when KDM was installed on my host was a 1 in 5 chance. Otherwise, X would either just hang with a black screen and "X" cursor, or if it got past that it would show the login, let me login and hang there after a few minutes of waiting.

The success rate seemed completely random; if I got through, KDE would eventually hang after a few minutes of work on my remote terminal and I would have to CTRL+ALT+BACKSPACE out of it. Suspecting it was the terminal I tried different distributions as X terminals such as kubuntu live CD, thinstation, and puppy linux and they all reported the same issues.

Replaced the KDM with GDM on the host machine and now the login screen comes up instantly every time. Could there be something funky between KDM and remote XDMCP?

There was another problem that did not get solved by switching to GDM. Certain programs would consistently crash when run in KDE from XDMCP. These were Firefox, Kopete, and Konsole  mainly. There were others but I can't remember. Their windows would show but they would be completely unresponsive and eventually return a message that it was not responding with a "force quit" option which didn't work. I think Synaptic ran reasonably stable. When these crashes happened there was a good probability that a minute later the whole desktop would stop responding and I would have to CTRL+ALT+BACKSPACE.

Generic Mozilla ran flawlessly in XDMCP. Others may have too; it was a long night and I don't remember.

I checked out the host's process list and at least firefox was hung and had to be killed manually through the shell.

Tried installing GNOME with lukewarm results (there were some configuration issues) but the problems running firefox and kopete in GNOME via XDMCP persisted the same.

When running X apps remotely through ssh, most everything worked fine. However XDMCP did not experience the same luck. I'd prefer XDMCP because of the straightforward terminal approach.

Bug or pilot error? Any explanations or ideas I should try?:confused:

thanx.

---

### Post by Defrector on 2007-11-09
I think I found a workaround involving having the remote terminal run xinit, then ssh to the host and run kdeinit. It seems to have the same effect, though without the pretty login screen.

---

