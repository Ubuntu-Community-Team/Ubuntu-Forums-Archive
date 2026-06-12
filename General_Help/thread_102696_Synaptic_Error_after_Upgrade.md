---
title: "Synaptic Error after Upgrade"
date: 2005-12-12
forum: General Help
---

### Post by taecha on 2005-12-12
I have upgraded from 5.04 to 5.10. Ever since I am unable to start Synaptic. Calling Synaptic from the menu just results in no action after entering the sudo pw. Starting synaptic from the shell results in a "Segmentation fault"? Any suggestions?

Thanks in advance.

---

### Post by NotJustANewbie on 2005-12-12
I have read many articles about this problem... and unfortunatly most of the solutions given were to install breezy from scratch :(

My first Ubuntu verison was/is breezy... I will face all your troubles too when I upgrade to dapper when the time comes. Oh Joy! ;)

---

### Post by taecha on 2005-12-13
Not very encouraging :( Any other suggestions out there?

---

### Post by earobinson on 2005-12-13
apt-get remove synaptic (not sure its remove but you can man apt-get to figure it out, not on linux:()
apt-get install synaptic

that might work, let us know. I have also been told that it is a bumpy upgrade for some reason.

---

### Post by taecha on 2005-12-13
would have been nice ... but doen't work either.

---

### Post by earobinson on 2005-12-13
as in the soultion did not work or you cant us apt-get?

---

### Post by taecha on 2005-12-15
solution does not work ... no change. apt-get works.

---

### Post by earobinson on 2005-12-15
In theroy you can install anything you need via apt-get (I understand this is not a soultion only a workaround)

They Did release an updeate to synaptic the othe day did you install that, If so what where the results?

---

### Post by taecha on 2005-12-15
Since I have removed and re-installed synaptic via apt-get I guess I have the latest version, havn't I. Well, synaptic still doesn't work.

---

### Post by earobinson on 2005-12-15
[QUOTE=taecha]Since I have removed and re-installed synaptic via apt-get I guess I have the latest version, havn't I. Well, synaptic still doesn't work.[/QUOTE]
lol, well the update came betteen my post recomending removal and the recomendation of an update

been searching the forums fro (synaptic Segmentation fault) found you some reading
[http://www.ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+Segmentation+fault](http://www.ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+Segmentation+fault)
[http://www.ubuntuforums.org/showthread.php?t=90028&highlight=synaptic+Segmentation+fault](http://www.ubuntuforums.org/showthread.php?t=90028&highlight=synaptic+Segmentation+fault)

---

### Post by taecha on 2005-12-16
[QUOTE=earobinson]lol, well the update came betteen my post recomending removal and the recomendation of an update[/QUOTE]

Have done a second round of removes and reinstalls and it seems to work now. :) Thanks earobinson!

---

### Post by earobinson on 2005-12-16
Im going to assume sw bug then.

---

