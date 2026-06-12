---
title: "Installing KDE - Will it upgrade apps?"
date: 2009-06-14
forum: Desktop Environments
---

### Post by PureLoneWolf on 2009-06-14
Hi all

This is something I can't seem to find anywhere.  I am on gnome at present and want to try the new KDE, but I actually run Amarok 1.4.  If I were to install the Kubuntu-Desktop package, would it attempt to upgrade me to Amarok 2?

Obviously I am happy to goto Amarok 2 in the future when they add some of the features that I need, but right now I need 1.4.

I guess I could just remove 2 and re-install 1.4 if absolutely necessary, but I would rather not have to.

Cheers

---

### Post by briguy47 on 2009-06-14
> **PureLoneWolf said:**
> Hi all

This is something I can't seem to find anywhere.  I am on gnome at present and want to try the new KDE, but I actually run Amarok 1.4.  If I were to install the Kubuntu-Desktop package, would it attempt to upgrade me to Amarok 2?

Obviously I am happy to goto Amarok 2 in the future when they add some of the features that I need, but right now I need 1.4.

I guess I could just remove 2 and re-install 1.4 if absolutely necessary, but I would rather not have to.

Cheers


I just went into Synaptic and selected the Kubuntu-Desktop metapackage.  One of it's dependencies is Amarok, which in the updated repositories is the updated 2.0.2 version.  However, I then unmarked Amarok and Amarok-common and it didn't require me to unmark any of the packages installed with Kubuntu-Desktop.

So, based on that, I think you can select Kubuntu-desktop and just unselect Amarok and be okay.  I don't know for sure though, because I didn't go through with the install all the way, but it looks pretty safe.

I hope that helps.  Let me know if you have any questions!  :D

---

### Post by PureLoneWolf on 2009-06-14
Thanks - I didn't think about doing it that way in Synaptic - Will give it a try later :)

---

### Post by briguy47 on 2009-06-14
Sweet.  Post how it goes, if you don't mind.  I'm curious to know.  Good Luck!  :)

---

### Post by uberlube on 2009-06-14
I ran into issues installing a second DE ontop  of the one i was using, but that was back in 2007 so hopefully its been improved. Hope it works out for you!

---

### Post by PureLoneWolf on 2009-06-14
Ok - It seemed to go ok, I deselected Amarok 1.4 and it left it alone (thankfully).

That said, my desktop is blank and I am unable to right click on it anywhere.  I have tried looking through as many settings as I can find through the menus, nothing doing.

Any ideas?

---

### Post by briguy47 on 2009-06-14
Are you in KDE now?  If you are and can get to a terminal or if there is a run command option (sorry, I don't have too much experience in KDE) then try to run:

```
kdewm
```and see if that helps.  I know I've had a similar situation in Gnome and reloading Nautilus helped.

---

### Post by PureLoneWolf on 2009-06-14
lol - typically I refreshed this page, then decided to head back to gnome.  I will try that later as I need to head out now... Sunday is giant steak day :D

Thanks for the help, will update more when I get back

---

### Post by briguy47 on 2009-06-14
Giant Steak!  Who can resist that?! lol

Also, I just found a page saying that explicitly setting KDE as the environment from the login screen (as opposed to "Default") might also help.  :)

---

### Post by PureLoneWolf on 2009-06-14
Hi again

Steaks downed, now time to investigate the issue - 

Got to a terminal (all menus/applications are fine) ran kdewm and nothing - Command not found.

Incidentally, I am using Compiz as I like wobbly windows (go figure)

Any other ideas?  I am looking around aswell..

Thanks

---

### Post by PureLoneWolf on 2009-06-14
Sorted it - Had to go to the Desktop Settings and change it from Desktop to Folder view - Then underneath that, I had to specify Desktop in the Name field.

Then all my icons sprung into life - Now I just need to shrink them from the default mahoosive setting.

---

### Post by briguy47 on 2009-06-14
Glad you got it figured out!

BTW:  Nice specs!  *drools*

---

### Post by PureLoneWolf on 2009-06-15
Thanks..as I don't game these days they are quite modest really :)

I had other issues though, but created a new thread if you are interested..

[http://ubuntuforums.org/showthread.php?t=1187468](http://ubuntuforums.org/showthread.php?t=1187468)

---

