---
title: "Error installing theme"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by lsutiger on 2007-04-04
Everytime I try to install a new theme from gnomelook I get "File is in invalid format" All of the files that I have tried with are tar.gz files, which, in the help section, stated what type of file it needed to be.
Why am I getting this error?

---

### Post by renzokuken on 2007-04-04
have you opened up the tar.gz file to see what is inside. sometimes there are tar.gz's contained in the original tar.gz which are actually the files you want. if its just a few folders in the tar.gz it should work.

which themes in particular are u using?

if the wizard isnt recognising the tar.gz files you could just extract the contents directly to /home/user/.themes ....... thats all the wizard is doing

---

### Post by lsutiger on 2007-04-04
I will give you links when I get home. I d/l all of them from gnomelook.org. The wizard stated that it did install, I think it is called Clearlooks-Luna, but it isnn't listed. I'll probably have more for ya by lunch.
Thanx for the help!

---

### Post by renzokuken on 2007-04-04
it may not listed in the main page.....it may not be a ful theme but instead a Controls (GTK) or Windows Border (Metacity)

open the theme manager and click on theme details then search for it in the "Controls" or "window Border" tabs

---

### Post by lsutiger on 2007-04-04
ok [this one]("http://gnome-look.org/content/show.php/Doe+GDM?content=52791") give an error, and [this one]("http://gnome-look.org/content/show.php/Avio-GDM?content=37395"), to mention just a couple.
I put the folder Avio-GDM under the .themes folder but it does not show up in the wizard.
Thanx

---

### Post by mcduck on 2007-04-05
> **lsutiger said:**
> ok [this one]("http://gnome-look.org/content/show.php/Doe+GDM?content=52791") give an error, and [this one]("http://gnome-look.org/content/show.php/Avio-GDM?content=37395"), to mention just a couple.
I put the folder Avio-GDM under the .themes folder but it does not show up in the wizard.
Thanx

Those are GDM themes, for your login screen, not for your desktop. They should be installed with System/Administration/Login Screen

---

### Post by quentinludwig on 2007-04-05
I'm having the same problem!  Invalid format!  What's the deal?

---

### Post by lsutiger on 2007-04-05
Doe! I learn something new every day!
But I am having an odd problem. When I go to System/Administration/Login Window,I get nothing,nada, not even a security/password prompt.
What would cause this? Any idea?
Thanx!

PS- Also,Could someone give me some definitions to the difference between GDM ( is tis only for loging?) and other themes?

---

### Post by lsutiger on 2007-04-06
Bump

---

### Post by mcduck on 2007-04-07
What happens if you try running 'gksudo gdmsetup' from a terminal? Do you get any errors?

---

### Post by lsutiger on 2007-04-07
Thanx for the reply! This is what I get:
```
 Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 2 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 3 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 4 of 5.
  Failed to connect to socket, sleep 1 second and retry
  Trying failed command again.  Try 5 of 5.
  Command failed 5 times, aborting.
Could not access GDM configuration file.

```
Also, I do have KDE installed, but I am using the Gnome Desktop. The login screen is KDE. I switched back to Gnome after having some glitches in KDE

---

