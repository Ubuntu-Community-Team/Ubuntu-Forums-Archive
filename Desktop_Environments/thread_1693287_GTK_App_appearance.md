---
title: "GTK App appearance"
date: 2011-02-22
forum: Desktop Environments
---

### Post by jimbo99 on 2011-02-22
When looking for a solution to one problem I was instructed by a moderator at kde.org to remove some files, which in effect put KDE back to the defaults.  But what I noticed shortly after that was that the GTK application's appears has reverted back to the old X windows look.

Anyone know how to correct this issue and put it back to normal?

---

### Post by ankspo71 on 2011-02-23
Hi,
Did you only remove the hidden .kde folder inside your home directory? Or was there other files too, such as the .gtkrc-2.0-kde4 file? 

Step 1
Go to System Settings > Application Appearance > GTK+ Appearance...
Do you have any other option besides "Raleigh" in the drop down menu where it says "Widget Style:"? If you have one there that says oxygen, choose that one and click apply.

Step 2 
If the only option you have is "Raleigh", then it would be best to install Oxygen-GTK (*deb file) from here [http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216](http://kde-look.org/content/show.php/Oxygen+Gtk?content=136216) , OR install Oxygen-Molecule from your package manager (Kpackagekit, Synaptic, etc). After you install either one of those packages, go back and repeat Step 1.

The .gtkrc-2.0-kde4 (and/or .gtkrc-2.0) file in your home directory is your GTK application's theme settings. Also, make sure that you have ownership of these files... not root. If it is missing you can try reinstalling kubuntu-default-settings. If that doesn't work, let us know.

Hope this helps.

---

### Post by jimbo99 on 2011-04-06
Unfortunately I have to edit out all that I said because none of it actually solved the problem. In fact, the problem persists.  But, I do know how to on a session-by-session basis get back the more attractive look when using GTK apps.

I said in the post I'm editing that I had read a ton of other posts.  That I have.  I've tried what seems a never ending number of suggested changes.  Nothing solves the problem completely.

What apparently gives me back the more attractive appearance, albeit on a session-by-session basis, is that I load the gnome-control-panel and select appearance (with KDE as the desktop). If I reboot, everything goes back to the McUgly GTK look.

---

### Post by schnelle on 2011-04-06
Install gtk-chtheme. Run it and choose qtcurve and hit apply. If you want your root gtk applications to use qtcurve, run gtk-chtheme with kdesudo and then choose qtcurve and hit apply.

I hope this helps.

---

### Post by jimbo99 on 2011-04-13
Thought I'd give you an update since you were kind enough to respond.

I installed the program you suggested and it did allow me to bring up theme changer.  Unfortunately, after rebooting it did not resolve the issue.  The system went back to the old ugly look.

I began by listing out all the steps I took to test and resolve this once you gave me the suggestion to install that program.  Unfortunately it would have confused anyone reading it that had the same problem.

Suffice it to say that under the .kde folder are a series of folders, one of which deals with config.  In that folder was a config file that was supposed to handle how KDE handled the appearance of GTK apps.  At the top of the file there was a sentence that stated to uncheck the box in system settings under appearance and then under colors that told KDE to handle how KDE handled GTK app COLORS--unchecking it "disabled" KDE's control.

I unchecked that box. Ran the program you suggested to select the appearance, and then rebooted.

When I came back all the GTK apps looked nice.

I think this is a bug in KDE where it gets confused with certain settings.  BTW, after unchecking that box I went back to see if the config file was still there and it was missing.  I verified that the checkbox about KDE handling colors in GTK apps was still unchecked.  It was.

Anyway, it is good to have that awful awful look of GTK apps gone.  Thanks for your help.

---

