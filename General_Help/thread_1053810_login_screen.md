---
title: "login screen"
date: 2009-01-29
forum: General Help
---

### Post by nealien on 2009-01-29
hello everyone!

this is my first post, although i've been to this site many many many times. this is the first time i've had a problem that wasn't already solved on these forums (as far as i know).  

i've been using ubuntu for about 4 months so i'm still relatively new.  i have dozens of windows certifications but linux is a whole different ballgame.  i've had to reinstall windows on my brothers computer 4 times in two months, so a few days ago i installed ubuntu 8.10 on his comp.  today he decided to change his login screen.  i'm not sure what he did wrong, but he didn't do it the way i did.  i won't be able to be in front of his computer till tomorrow evening but i think (tho i'm not sure) that he set his login screen incorrectly (resolution?).  when he boots his computer, instead of getting the login screen he gets NOTHING!  i've tried to have him login with the command prompt, which worked, but then he got a few random errors and his mouse didn't work.  i don't wanna have to reinstall if i don't have to.  so how do i fix this?  i believe that his gnome desktop is totally screwed up.  HELP??

---

### Post by Yashiro on 2009-01-29
You have no idea what he's done. As he seems intent on breaking stuff I wouldn't have given him the root password.
i.e. after installing, make another account for him and do not give him your install password.

If this doesn't go down too well then you will need to find an app to *image the install* so it's easier to fix when he trashes it after playing with sudo.


> If you dont have access to your graphical (GUI) desktop or you're stuck at the login screen, drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

This will remove the folders needed to reset Ubuntu/Gnome back to its defaults.

Get back to your GUI desktop by hitting CTRL + ALT + F7.

Keep in mind that this will only reset your Gnome-specific settings. If you are having problems with your video card, display, x-server, etc., this will not fix your problems..

Also, install the ssh server when you get a chance and set it up so you can remote log in.
You can do it all from home as long as the system boots and has a web connection.

---

### Post by nealien on 2009-01-29
that didn't work.  it just does what it was doing before.  it just sits and "thinks."  it's a blank screen with the mouse cursor in the middle of the screen with the ubuntu equivalent of the windows hourglass.  the hard drive isn't searching for anything, it just sits.  any other ideas?

---

### Post by xtifr on 2009-01-29
If he messed up the login screen (aka "gdm"), then the settings he messed up won't be in his home directory, because gdm isn't a per-user program.

You might find some clues in /var/log/gdm.

You *might* be able to straighten things out by simply running gdmsetup and choosing some rational settings.

Without more details about what actually happened, it's hard to suggest more than that.

---

### Post by Yashiro on 2009-01-29
Not really. Not a great deal of information to go on.

Is it gdm he broke, or the screen resolution in general?

---

### Post by nealien on 2009-01-29
Ok This is his brother. im going to explain exactly what i did. i downloaded this GDM screen: 

[http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883](http://www.gnome-look.org/content/show.php/nUbuntu+GDM+Logins?content=73883) 

and i saved it in .../pictures/background images/GDM Themes/ (package name)

i then went to login window preferences, i then clicked the Local tab. once there i clicked +Add and clicked to open the package in the above location. 

The package opened and i saw my new GDM Theme in the Theme selector box. i then clicked my newly added theme, and closed the window. 

I Used my computer as normal for a little bit. then restarted it to see my new login screen. it restarted fine, but when it got to the login screen it loaded up to the default plain background color (Tan/brown) and the mouse searches for something, and it does nothing.

What did i do wrong?

---

### Post by nealien on 2009-01-29
i also wonder if i may have saved it in the wrong location? if so i left you the exact location i saved it at. when i get to the console what is the command to move a file, and where do i save it at?

---

### Post by Yashiro on 2009-01-29
Log into a terminal.
> sudo nano /etc/gdm/gdm.conf-custom

Find the 'GraphicalTheme' lines and change them to look like this:
> GraphicalTheme=Human
GraphicalThemes=happygnome/:Human
(Control O to save, Control X to exit)

Reboot.

---

### Post by nealien on 2009-01-29
that worked!

thank you sooo much guys!:D  u've saved us reinstall.

---

### Post by Yashiro on 2009-01-30
Remember for the future: If things ask you for the admin password there is a risk you could render the machine unusable.

Send the cheque in the post. :D

---

