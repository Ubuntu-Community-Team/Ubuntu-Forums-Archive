---
title: "Installs from CD but won't play from CD"
date: 2006-02-01
forum: Desktop Environments
---

### Post by Gritz on 2006-02-01
Ok ... gave up on trying to upgrade Firefox to ver 1.5 until I do some more research .... but now, just a simple problem maybe?? If I try to play an audio CD I get the following message:

Error playing CD:
Reason: Could not open CD device /dev/hdc for reading

Now ... I installed ubuntu from the cd ... I can see data and audio files on the cd .... but, they won't play.

Simple? or complicated?  Help for a squeaky newbie?  Or just point me ...:confused:

---

### Post by mycroft on 2006-02-01
What application are you using for playing the CD?

Have you made certain you are a member of the audio user group?

---

### Post by Gritz on 2006-02-02
Just the "CD Player" that is installed on the initial setup. Yes, the user (Jim) is a member of the Audio Group.  I'm thinking it may be the onboard audio. It seems others have overcome using the old "Soundblaster Live" soundcard. That may be my only option.

---

### Post by Gritz on 2006-02-03
Well .... changing to Creative SoundBlaster failed to solve the audio problem. Guess I'll come back in 6 months to see if they've got the bugs worked out yet.

---

### Post by christhemonkey on 2006-02-03
If it cant read the files from the cd, this is not an audio problem, it is more likely an incorrect setup of your fstab.  Post the contents of your fstab here!
(located in /etc/fstab)
((to open do: > nano /etc/fstab  in a terminal))

---

