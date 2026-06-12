---
title: "GUI login problem - Terminal instead of desktop"
date: 2010-07-22
forum: Desktop Environments
---

### Post by pasan1 on 2010-07-22
Hi,

I have been running 10.04 since the launch after upgrading from 9.10. Today when I logged in as normal, instead of taking me to the desktop I get a white console on the top left corner with the normal login background. I typed 'sudo X' but it says the server is already active for display 0. 

Please advise what I can do. I am reasonably new to Linux so apologies if this has been discussed before (but I couldn't find any info here or on google).

---

### Post by pasan1 on 2010-07-22
I forgot that I had uninstalled compiz yesterday. I had a problem with the close/minimize buttons disappearing from my opened windows. I think this is probably the cause. Tried to install compiz by running sudo apt-get commands but says it's already installed.:(

Any suggestions to resolve this through a terminal command?

---

### Post by mcduck on 2010-07-22
Check that your desktop session is set to Gnome (in the login screen click the Session-button and select "Gnome").

---

### Post by Bhamid on 2010-07-22
Try using 'sudo aptitude purge [compiz package name]' and then reinstalling it.

Also try Atl + F7 on the command line screen you are getting.

---

