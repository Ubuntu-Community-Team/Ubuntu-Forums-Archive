---
title: "Indicator and notification area applets issues"
date: 2010-06-12
forum: Desktop Environments
---

### Post by Cfhs_1 on 2010-06-12
Hello ubuntu forums,

I am having issues with the indicator applet and notification area applet under ubuntu 10.04 32-bit. I'm using a Dell Latitude E6400 and every time I boot into ubuntu (I dual boot ubuntu and windows 7 ultimate) The indicator applet and the notification applet are all jumbled up and completely unusable. I have to remove both applets from the panel and re-add the to correct this. I have to do this every single time I boot into ubuntu. It's starting to get really annoying, and I have looked everywhere for a solution to no avail. If someone could please provide a fix, or some advice for fixing this annoyance, that would be awesome! 

                                                         Thanks,
                                                         Nicholas C. Brown

P.S. I'll post pictures ASAP.

---

### Post by Cfhs_1 on 2010-06-12
In this screenshot it's not as bad as it usually is, but as you can see the "mail" icon on the indicator applet is missing. I'll post more pictures as soon as I have time.

---

### Post by Cfhs_1 on 2010-06-12
Here is a great example of what usually happens.

---

### Post by hansdown on 2010-06-12
Hi Cfhs_1.

I've had the same issues, and also, sometimes an applet will double itself, making two identical applets.

A restart usually corrects it, but it would be neat to find out what is causing this.

---

### Post by Cfhs_1 on 2010-06-12
> **hansdown said:**
> Hi Cfhs_1.

I've had the same issues, and also, sometimes an applet will double itself, making two identical applets.

A restart usually corrects it, but it would be neat to find out what is causing this.

Yes, I agree. It's getting very annoying, We need to find a way to fix this.

---

### Post by teachop on 2010-06-12
I was able to mostly stop this by sequestering certain panel icons to one side of the panel.  Now it almost always comes up reasonable.  The only stuff I have on the top right is exactly the way Lucid ships.  The user configured stuff is all moved to the right.  There are two different sortings that come up now, but both are usable.

However, two of the icons on the left sometimes come up the wrong size.  Right now the System Monitor panel applet icon is about 2 pixels high, but it still works (in a useless sort of way).  I frequently have the Show Desktop icon come up strange sizes, and it was a pixel or two wide one time, still worked.

---

### Post by Cfhs_1 on 2010-06-13
After some recent updates this problem seems to have completely disappeared!:popcorn:

---

### Post by sderrick on 2010-06-14
This issue is not solved. 

I'm using Lucid on a INspiron Laptop, system is up to date and this morning the NM is missing and the power icon is doubled. Usually its much worse.

I've attached a picture.

Scott

---

### Post by Cfhs_1 on 2010-07-10
> **sderrick said:**
> This issue is not solved. 

I'm using Lucid on a INspiron Laptop, system is up to date and this morning the NM is missing and the power icon is doubled. Usually its much worse.

I've attached a picture.

Scott

Hmm, it seems to still happen to me sometimes too, though not as bad... Now a simple restart usually corrects things, also it seems to happen more often when resuming from hibernation, or standby...

---

### Post by sderrick on 2010-07-10
> **Cfhs_1 said:**
> Hmm, it seems to still happen to me sometimes too, though not as bad... Now a simple restart usually corrects things, also it seems to happen more often when resuming from hibernation, or standby...

I never Hibernate.  Always happens on a fresh boot.

Using the Killall gnome-panel always seems to restore things. I think it has to do with the timing of things starting.  If the applets are not all done and running happily when the panel populates things get screwed up.

---

### Post by Cfhs_1 on 2010-07-15
> **sderrick said:**
> I never Hibernate.  Always happens on a fresh boot.

Using the Killall gnome-panel always seems to restore things. I think it has to do with the timing of things starting.  If the applets are not all done and running happily when the panel populates things get screwed up.

hmmm, there must be some file we can edit to make the applets load first, then the panels populate... that would help. Unfortunately I have no clue what file that would be, and what part of it to edit...

---

### Post by hubertofliege on 2010-07-17
I just upgraded, and I've noticed that there is an applet that lets me know which keyboard layout I'm in.  I don't like this.  Its an eyesore, and I have an LED that lets me know.  How can I remove applets?

---

### Post by gavdari on 2010-07-17
I have almost same problem. I guess the panel is a mess in 10.04. although restarting or killall gnome-applet doesn't change anything for me. Two of my icons are disappeared (xfardic and checkgmail) but the respected programs are running. any solution?

---

### Post by Cfhs_1 on 2010-07-17
I don't know if this will fix things for everyone else, but I moved all my applets to one panel, and deleted the other, the changed my panel size to 40PX, and all the problems have gone away completely. This isn't a true fix of course, but until a fix is found this will make things functional. 


P.S. I don't know what fixed it, changing the panel size, or moving all the applets to one panel and deleting the other, but it sure worked.:popcorn:

---

### Post by NeverSage on 2010-09-05
If anyone figures out a solution for this, please post it here.  Thanks!

---

