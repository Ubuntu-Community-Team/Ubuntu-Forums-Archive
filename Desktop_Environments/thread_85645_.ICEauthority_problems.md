---
title: ".ICEauthority problems"
date: 2005-11-03
forum: Desktop Environments
---

### Post by Karahana on 2005-11-03
Something weird is happening... After installing xfce and whole bunch of other software i saved my session and rebooted. Then I started getting an error message on login. It said that my session lasted less then 10 seconds and the log said that there was an error accesing the .ICEauthority file. Nothing would boot. Not xface, not GNOME, not the failsafe GNOME... 

I fixed it by changing the CHMOD of the file to 777 (lol) from the console. Now my system boots normal, but when I try to run Krusader i get a dcopserver error. If I run dcopserver it says that there was a problem with a .DCOPserver file that i can't find in my home directory... I need Krusader cause I'm used to the totalCMD UI...

What I think caused the problem is smb4k. I ran it as root so I could mount a windoze share and saved it with the session thinking that it will mount it automatically... Changing the CHMOD of the file back to default (644?) also didn't help.. :( 

I am still a big noob in nix so I don't have any more ideas...

Pls help I need my Krusader! :)

Tnx

---

### Post by Biased turkey on 2005-11-03
I have the same problem when running KDE applications with gnome, mostly Kdevelop and Smb4k.
What I did was just delete .ICEauthority, reboot, select KDE in the display manager and KDE will recreate the .ICEauthority on startup.
The only reason why I keep KDE is because of Kdevelop

---

### Post by az on 2005-11-03
This was a problem in Warty when you would install k3b or something.  KDE changed the permissions of .ICEAuthority.  It was fixed in Hoary.

It would appear that non-main kde apps still cause that to happen.  Perhaps file a bug report about his?


launchpad.net (Universe packages use Malone for bug reports)

---

### Post by Karahana on 2005-11-03
Biased turkey I'll try that as soon as I get home! It didn't even occur to me that I can simply delete the file...  :D 

Azz I have Breezy... I'll try posting a bug report, but it's hard to do since I'm not sure what exactly caused the error.

Tnx for the answers! :)

EDIT:

Just occured to me that i don't have KDE... Crossing my fingers for it to work with GNOME of xface!

---

### Post by jonny on 2005-11-03
I had this problem under Hoary whenever I ran a KDE app.  Haven't tried it with Breezy.

---

