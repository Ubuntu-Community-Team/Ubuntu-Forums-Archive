---
title: "Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)"
date: 2009-05-18
forum: General Help
---

### Post by ProgressionMurph on 2009-05-18
Hey Everyone,

    When I try to open synaptic Package manager, I click on the icon it asks for my password and then it doesn't open.  I've searched around the forums a bit and to no avail I still can't manage to get it to work.

  What led up to this problem was me trying to get fprint_demo to work however It wouldn't detect my biometric fingerprint sensor.

  I had troubles trying to uninstall that and finally managed to do it through terminal.  However, I believe when I installed it it altered some password files.  Now when I log in I have to type in my password twice.  When I type something into the terminal it requires me to type my password in twice.
 
  I've tried to reinstall update manager and synaptic package manager through add/remove however it says reinstall it through synaptic.. Go figure..

  Hmm..
Does anyone have any suggestions?

  I've tried sudo apt-get update and sudo apt-get upgrade along with the two previous without the sudo..  I end up an error in the terminal that says Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)?

Any help is much appreciated,

Sincerely,
Alex

P.S. I don't know if it's of any use but I am usuing 64bit Jaunty.

---

### Post by cariboo on 2009-05-18
Have you tried removing the look file? I would also help us diagnose your problem, if you tried to open synaptic in a termenal and paste the output in your next post.

---

### Post by ProgressionMurph on 2009-05-18
Sorry, what is the look file?

---

### Post by ProgressionMurph on 2009-05-19
I typed gksudo nautilus in terminal went to /var/lib/apt/lists/lock and deleted the lock file.  Still no luck.

I type apt-get update in the terminal and I get: 

alex@alex-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

sudo apt-get update works.

apt-get upgrade doesn't:

alex@alex-laptop:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


sudo apt-get uprade works:
alex@alex-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Hmm.  Unsure what to do from here.

---

### Post by ProgressionMurph on 2009-05-19
Fixed the problem.
 	Code:
 	sudo gedit /etc/pam.d/common-auth 
and commented out this line

 	Code:
 	#auth   sufficient      pam_fprint.so

---

