---
title: "[SOLVED] unable to open any terminals in gnome as user X."
date: 2007-10-03
forum: Desktop Environments
---

### Post by RandB on 2007-10-03
Am unable to open any terminal in my user account when running the gnome desktop, not xterm, aterm, rxvt, or gnome-terminal. It was working correctly when I left for a short vacation but as of my return the terminal programs do not open. Sometimes they flash momentarily on the screen before disappearing, but mostly not even that much.

I am able to open up terminals without problems on a second user account that I just created, so I am wondering which config file in my /home directory might have been mucked up last week that now prevents me from opening terminals in my user account?

---

### Post by RandB on 2007-10-03
I suspect the problem is related to my attempt to setup xterm to run screen automatically when it is opened.   Was unsuccessful at this before the vacation, however screen now opens automatically on the virtual consoles. Terminals in gnome still close as soon as they open so I do not know if they are running screen or not. Is there a simple ( or complex) method of tracking what happens when xterm and other terminal programs are opened in gnome? 
 
I realize that I could create a new account and transfer files, settings and permissions to it, but fixing the problem would be better. Would appreciate any clues or guesses or leads. Thanx.

---

### Post by RandB on 2007-10-04
hmmm, maybe I should have posted this question in the complete noob section. Suspect it has a simple answer. Probably should have mentioned that am using 6.06. Am rather missing the use of the command line.  :confused:  Will post the solution when I finally find it. Will be smarter then.  :)

---

### Post by RandB on 2007-10-05
Solution was simple -> change default shell back to bash  ie [ chsh -s /path/to/shell {user} ].  I had it setup as /usr/bin/screen which worked fine initially until the power failure.

Am very happy to have the terminals programs working again. Thank you to all who took some time to consider the problem.

---

