---
title: "updates removed kde?"
date: 2009-04-09
forum: General Help
---

### Post by Symbiote on 2009-04-09
hello there, 
yesterday something funny happened to me... I installed the latest updates via adept updater, rebooted my system and it looks like the update removed my kde 4 desktop... 

I can only boot to terminal, when I try to run apt-get update I only get repositories errors, also when I tried to run apt-get install kubuntu-desktop it just gave me an error message that packages are broken... 

I'm still beginner in linux a little so I don't know which information should I provide here but I would really appreciate if you could help me with this because if I wasn't using dual boot with XP, I would be screwed

---

### Post by westyonfire on 2009-04-09
That exact thing happened to me. I too am new so I didnt know how to fix it. I had to reinstall from disc. Sounds like someone at Canonical messed up big time...

---

### Post by anapob on 2009-04-19
hmm...the same thing happened to me, Desperately wanted to try the new KDE 4.2, went for the Adept updates :( 

Now I cannot login to my KDE desktop , cause it is giving me a "/usr/bin/startkde" cannot be found error and defaults back to GNOME

Back in Gnome i found that kubuntu-desktop is unticked,i cannot install kubuntu-desktop from synaptic either.
 
It gives me the following error 

"The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences."

---

### Post by abn91c on 2009-04-19
try again 
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get check
sudo apt-get update
sudo apt-get install -f

---

### Post by anapob on 2009-04-19
Nope, nothing has changed, i seem to be getting the error again, however after running the last command , i got a message

"The following packages were automatically installed and are no longer required:"
which includes some of the kde components, which of course is useless because kubuntu-desktop is not installed. But at the end i got an option to remove all of them "apt-get autoremove". Should i go for it and do another fresh install of KDE, or is there another workaround.

---

### Post by abn91c on 2009-04-19
run the sudo apt-get autoremove, then logout>login then sudo apt-get install kubuntu-desktop, if you get a message about kubuntu already installed, then sudo aptitude reinstall kubuntu-desktop

---

### Post by anapob on 2009-04-20
Yep, Problem solved.....thanx mate.

---

