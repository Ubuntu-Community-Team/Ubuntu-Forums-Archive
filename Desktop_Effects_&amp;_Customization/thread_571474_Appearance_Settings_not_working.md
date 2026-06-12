---
title: "Appearance Settings not working"
date: 2007-10-09
forum: Desktop Effects &amp; Customization
---

### Post by Koziasty on 2007-10-09
OK, here goes.

I use Gutsy, with Gnome. Just now i tried going to System->Preferences->Appearance.

The window loads just fine, but I can click ONLY ONCE (i can choose a different theme). Then only the cross and the close buttons are working. Clicking on tabs results in what is shown on the screen - a white box with nothing inside.

Any suggestions?

Oh, by the way - I tried removing qt3-qtconfig ( i need that for another application ) but that didn't work. I also tried logging off and on, reseting Xs. Nothing worked.

Thank you in anticipation of your future help, lol :D
---------------------------------------------------------------------------------
Having run 
koza@laptop:~$ gnome-appearance-properties 
sh: kde-config: not found
sh: kde-config: not found

I googled it, it turned out to be a BUG in gtk-qt-engine. I installed that, cos I was told it would help kadu's (an application written in qt) appearance.
Removing gtk-qt-engine solved the issue.
Hope that helps anybody.

---

### Post by Koziasty on 2007-10-09
Bumping it, cos its solved now, maybe will help anybody

---

### Post by hopfrog238 on 2007-10-21
It helped me, and I would have never fixed the problem without your post.  Many Thanks!

~hf

---

### Post by John Bennett on 2007-10-22
> **Koziasty said:**
> 
I use Gutsy, with Gnome. Just now i tried going to System->Preferences->Appearance.
The window loads just fine, but I can click ONLY ONCE (i can choose a different theme). Then only the cross and the close buttons are working. Clicking on tabs results in what is shown on the screen - a white box with nothing inside.

I had almost the same behavior.

In the System -> Preferences -> Appearance dialog, only the "close" button would work.

Running "gnome-appearance-properties" at the command prompt resulted in...

```
X Error: BadDevice, invalid or uninitialized input device 156
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(gnome-appearance-properties:5967): Gtk-CRITICAL **: gtk_widget_map: assertion `GTK_WIDGET_VISIBLE (widget)' failed
```

Per your experience, I used System > Administration > Synaptic Package Manager to uninstall **gtk-qt-engine**.

Now doing System -> Preferences -> Appearance, or running "gnome-appearance-properties" at the command prompt gives me a functional "appearance" dialog and does not result in any errors.

Thanks Koziasty!!

I don't know what gtk-qt-engine is for, but hopefully I won't need it. 8-)

---

### Post by jagrav on 2007-10-22
Thanks Koziasty. I thought I would have to reinstall gutsy.

---

### Post by hrpr on 2007-10-24
Had same problem same symptoms.  Thanks for posting the solution.:)

---

### Post by Me_Titus on 2007-10-27
Thanks a ton mate...;)

---

### Post by Useff on 2007-11-02
This solved my problem. Thanks!

---

### Post by pritamps on 2007-11-26
Thanks from me too!

---

### Post by ArdentLonging on 2007-11-29
I could solve this problem thanks to the above posts.

Thanks!!!

---

### Post by Grantium on 2007-12-03
Thanks again

---

### Post by Seji.Kenja on 2007-12-07
Hey there..

ok I install the compiz fusion all fine and dandy besides the cube effect working.. I dont know went wrong there..

but later on in the day I installed a few more things that was to help my video codecs.. 

doing updates and stuff.. the computer asks me to reset the computer for the settings to take effect..

so I do

but I lose all my desktop effects.. and I have to keep my visual effects on  "none" I dont know why :S

I tried to reinstall like I never had it on the computer.. but that didnt work.. unless I did something wrong.. can some one help me :)

...:::Seji.Kenja:::...

---

### Post by MOPAULY on 2007-12-24
thanks, I had the same issue and this resolved it.

---

### Post by lonesomecrow on 2008-02-18
thanks this helped me a lot too!!!!!!!!!!!!!

---

