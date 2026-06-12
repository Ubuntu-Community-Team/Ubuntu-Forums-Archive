---
title: "Problem right clicking the top panel"
date: 2009-06-06
forum: General Help
---

### Post by colau on 2009-06-06
Hi,
Right clicking the top panel>then selecting properties
the result is attached.
:)

---

### Post by QIII on 2009-06-06
Could you post a screenshot of your top panel before you right click on it?

Have you installed/uninstalled/updated Evince recently?

---

### Post by colau on 2009-06-06
Sorry,it is right click the top panel > then properties.

---

### Post by colau on 2009-06-06
> **QIII said:**
> Could you post a screenshot of your top panel before you right click on it?

Have you installed/uninstalled/updated Evince recently?

aptitude remove evince
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
The following packages are BROKEN:
  ubuntu-desktop 
The following packages will be REMOVED:
  evince 

```

---

### Post by QIII on 2009-06-06
Did you type "y" or did you bail out of the terminal?

I think there are dependencies between Evince and ubuntu-desktop, which is why I was asking if you had done anything with Evince.

Not to worry if you have.  You should be able to fix that with Synaptic.

Wife just got home from night out with the girls, and it's time for me to hit the rack.

I'll try to get back on this in the morning.

Or someone else will chime in.

---

### Post by colau on 2009-06-06
> **QIII said:**
> Did you type "y" or did you bail out of the terminal?

I think there are dependencies between Evince and ubuntu-desktop, which is why I was asking if you had done anything with Evince.
evince --version
```

GNOME Document Viewer 2.26.1

```
What can be done with evince?

---

### Post by QIII on 2009-06-06
Evince is a pdf viewer.

---

### Post by colau on 2009-06-06
> **QIII said:**
> Evince is a pdf viewer.
I know this.
dpkg -l | grep ubuntu-desktop
```

ii  ubuntu-desktop                             1.140                                The Ubuntu desktop system

```
How can I get rid of that message?

---

### Post by QIII on 2009-06-06
OK.  Got you.

I'm still thinking about this.  

Obviously I'm concerned about the message that ubuntu-desktop is broken, and I know that there are dependencies between ubuntu-desktop and Evince.

Have you done an update lately, say just before you started having this problem?

---

### Post by colau on 2009-06-06
> **QIII said:**
> OK.  Got you.

I'm still thinking about this.  

Obviously I'm concerned about the message that ubuntu-desktop is broken, and I know that there are dependencies between ubuntu-desktop and Evince.

Have you done an update lately, say just before you started having this problem?
Do you mean this?;)
```

aptitude dist-upgrade

```

---

### Post by QIII on 2009-06-06
Actually, I was wondering about through the Update Manager that pops up inconveniently when you are in the middle of something (which can be fixed, of course.)

---

### Post by colau on 2009-06-06
> **QIII said:**
> Actually, I was wondering about through the Update Manager that pops up inconveniently when you are in the middle of something (which can be fixed, of course.)
Ok.
How to solve it?

---

### Post by QIII on 2009-06-06
Well.  Give this a whirl.

Go to Synaptic.  Under the "Edit" in the toolbar, there is a "Fix Broken Packages" option.

(Or were you talking about how to get rid of the annoying Update popup?)

---

### Post by colau on 2009-06-07
> **QIII said:**
> Well.  Give this a whirl.

Go to Synaptic.  Under the "Edit" in the toolbar, there is a "Fix Broken Packages" option.

(Or were you talking about how to get rid of the annoying Update popup?)
I did this
```

aptitude dist-upgrade

```
During setting up
```

 * Loading AppArmor module...                                            [fail] 
invoke-rc.d: initscript apparmor, action "force-reload" failed.

```
Why is this?

---

### Post by QIII on 2009-06-07
Hmmm.

Don't know exactly.

Do you have the Universe repository clicked in your Software Sources?

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)

---

### Post by colau on 2009-06-07
> **QIII said:**
> Hmmm.

Don't know exactly.

Do you have the Universe repository clicked in your Software Sources?

[https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)
Yes.
Attached.

---

### Post by QIII on 2009-06-07
Did you try Fix Broken Packages in Synaptic?

---

### Post by colau on 2009-06-07
> **QIII said:**
> Did you try Fix Broken Packages in Synaptic?
Which packages would I search in Synaptic?

---

### Post by QIII on 2009-06-07
In Synaptic, the top toolbar has an "Edit" button.

In the drop-down is a "Fix Broken Packages" option.

---

### Post by colau on 2009-06-07
> **QIII said:**
> In Synaptic, the top toolbar has an "Edit" button.

In the drop-down is a "Fix Broken Packages" option.
If I click broken packages from Edit tab nothing happens.

---

### Post by QIII on 2009-06-07
If you still have it open, look at the lower left corner.  It should say "Succesfully fixed dependency problems".

---

### Post by colau on 2009-06-07
> **QIII said:**
> If you still have it open, look at the lower left corner.  It should say "Succesfully fixed dependency problems".
Yes,Got this message at bottom.

---

### Post by QIII on 2009-06-07
Right click the panel you were having problems with.

If you still get the same error, we'll try reinstalling Evince from the Synaptic.

---

### Post by colau on 2009-06-07
> **QIII said:**
> Right click the panel you were having problems with.

If you still get the same error, we'll try reinstalling Evince from the Synaptic.
Right Click on the top panel>Properties
Same problem.
uname -r
```

2.6.29-020629-generic

```
;)

---

### Post by QIII on 2009-06-07
You've updated your kernel...

Still, let's try this.

In Synaptic, search for Evince.  Select Evince and then Mark for Reinstallation.

When you click Apply, you should get a pop-up that says Apply the following changes.

Click Show Details, and you'll notice ubuntu-desktop is listed.  That is because of the dependency.

Click apply.

---

### Post by colau on 2009-06-07
> **QIII said:**
> You've updated your kernel...

Still, let's try this.

In Synaptic, search for Evince.  Select Evince and then Mark for Reinstallation.

When you click Apply, you should get a pop-up that says Apply the following changes.

Click Show Details, and you'll notice ubuntu-desktop is listed.  That is because of the dependency.

Click apply.
Reinstalled evince, same result.
Is there any command to reinstall gnome-panel.
After apt-get install ubuntu-desktop
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  ubuntu-desktop 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 29.1kB of archives. After unpacking 57.3kB will be used.
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  ubuntu-desktop 

Do you want to ignore this warning and proceed anyway?

```
NB:If I create a New panel from right clicking the above gnome panel then there appears a new panel at right.
Then if I Right Click>Properties to the newly created panel, no problem.

---

### Post by QIII on 2009-06-07
Interesting that ubuntu-desktop is untrusted...

Can you drag all of your icons to the new panel?  Do they work from there?

As for installing gnome-panel, I would assume so.

sudo apt-get install gnome-panel.  

I'm going to try that on my dev machine.  Hang on for a moment.

---

### Post by QIII on 2009-06-07
sudo apt-get install gnome-panel  works, but since I have the latest, nothing was installed.

---

### Post by colau on 2009-06-07
> **QIII said:**
> sudo apt-get install gnome-panel  works, but since I have the latest, nothing was installed.
Thanks for your reply.
I had to restore my backup ubuntu 9.04.:D

---

### Post by theozzlives on 2009-06-07
Move all your icons, system tray, & Menu Bar to the side panel. Delete the top one, and drag the side panel to the top.

---

### Post by QIII on 2009-06-07
Ooof.

I wish you had tried moving all of your icons.

Then we could have said we had found a solution, more or less...

A restore of the OS is disaster recovery.

Oh, well.

As long as you are up and running again!

---

### Post by colau on 2009-06-07
> **QIII said:**
> Ooof.

I wish you had tried moving all of your icons.

Then we could have said we had found a solution, more or less...

A restore of the OS is disaster recovery.

Oh, well.

As long as you are up and running again!
I could have dragged the icons.
But how could I add the 
```

Applications
Places
System

```
menus?

---

### Post by QIII on 2009-06-07
Deselect "Lock to Panel" and use Move.

I just did it on my dev machine.

No matter.  The thing that really matters is that you are up and running.

---

### Post by colau on 2009-06-07
> **QIII said:**
> Deselect "Lock to Panel" and use Move.

I just did it on my dev machine.

No matter.  The thing that really matters is that you are up and running.
What do you mean by "Lock to Panel"?

---

