---
title: "How to prevent Ubuntu 10.04 from blanking the screen when idle?"
date: 2010-08-12
forum: Desktop Environments
---

### Post by fivebells on 2010-08-12
I have removed gnome-screensaver, and to the best of my knowledge, it has not been replaced it with any other screensaver application.  I have set System->Preferences->Power Management to never blank the screen.  However, Ubuntu still blanks the screen if there has been no user interaction for a while.  Is there anything else I should do to prevent this?  [These instructions]("http://www.liberiangeek.net/2010/07/prevent-ubuntu-10-04-lucid-lynx-display-turning-blank/") suggest that there is nothing else which could be blanking the screen, so I am confused.

---

### Post by wojox on 2010-08-12
Install [Caffeine]("https://launchpad.net/~caffeine-developers/+archive/ppa") and your troubles will be solved.

---

### Post by fivebells on 2010-08-13
Thanks, that seems to be what I need.

---

### Post by wojox on 2010-08-13
Your welcome :)

---

### Post by fivebells on 2011-03-17
I finally got around to digging in to caffeine to see how it works.  (Not hard; it's a simply python script.)  The key idea is to run "xset -dpms" and "xset s off"

---

