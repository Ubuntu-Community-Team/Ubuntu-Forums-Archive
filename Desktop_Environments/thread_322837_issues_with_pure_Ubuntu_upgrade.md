---
title: "issues with pure Ubuntu upgrade"
date: 2006-12-21
forum: Desktop Environments
---

### Post by tchoklat on 2006-12-21
Need advice and assistance please!

I had Kubuntu on my machine and decided to try Ubuntu instead so I followed the psychocats guide on getting pure Ubuntu.

What I have now is problematic.

On start up I still get the Kubuntu splash screen

Entering login and password I get a message "No exec line in the session file: kde. Running GNOME failsafe session instead"

Then I get the message " This is the GNOME failsafe ...."

Then "There was an error starting the GNOME settings daemon ..."


I am then logged into GNOME but fonts etc are dodgy and not as they should be.

I then log out and log in and receive a message, "Do you wish to make KDE-Desktop the default for future sessions"

I have three options and choose to just log in and all is fixed on the desktop.


What is this all about - it seems that KDE is still lingering about an the session tries to log in to KDE.


Tony

---

### Post by an.echte.trilingue on 2006-12-21
On the log in screen, go to the options menu, the sessions section, and select gnome as your default DE.  Then you should log on normally.

For the usplash thing, simply follow the [instructions on the wiki]("https://help.ubuntu.com/community/USplashCustomizationHowto") and you should be able to install anything you want for a splash screen.

Take care,
-mat

---

### Post by tchoklat on 2006-12-21
Hi, yes I thought that would be the way to go although I do not get an options menu at the log-on screen only a request for user name and then password - any other options?
 
Your other point will be followed through - thanks
 

Tony

---

### Post by darrenm on 2006-12-21
Have you changed System>Administration>Login Window to the correct Human one?

---

### Post by an.echte.trilingue on 2006-12-21
> **tchoklat said:**
> Hi, yes I thought that would be the way to go although I do not get an options menu at the log-on screen only a request for user name and then password - any other options?
 
Your other point will be followed through - thanks
 

Tony

Are you sure?  As opposed to the kdm log in screen, which puts that menu right under the password box, it is at the bottom left corner...

---

### Post by tchoklat on 2006-12-21
done - thanx guys!

---

