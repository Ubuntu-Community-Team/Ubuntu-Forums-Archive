---
title: "gdm problems"
date: 2007-08-29
forum: Desktop Environments
---

### Post by leegwebb on 2007-08-29
Hi.  I have been using Linux for a few months and run Ubuntu on one machine and Mepis on another.  The problem I am having actually relates to the Mepis machine, but is Ubuntu-related and the solution will help me customize my Ubuntu machine as well.

FYI, the reason I chose Mepis for this particular machine is that it auto-detected and configured the Wifi card, something I wish Ubuntu could also do.

Mepis by default uses the K environment, but this is my daughter's computer and she likes gnome better.  Truthfully, she likes Windows better, so gnome is kind of a compromise.  I know her machine will work better with Linux, and gnome is more familiar.

Anyway, I used Synaptic to install the "gnome desktop environment"  and it works, but with a couple of minor issues I am hoping someone might be able to help with.  Upon startup, gdm initializes and I get an error message "could not find the theme Human."  All I have to do is click OK and startup proceed, but this is annoying.  I know Human is the default Ubuntu theme, but it is not present on my Mepis computer.  Can anyone tell me which config file to edit to point it to a different theme?  I would like to change this in my Ubuntu machine as well.  I know how to change the user theme, but at startup it still goes through Human before starting the user accounts 

Second, when I do get to the login screen, the login box is greyed out at first.  I have to click OK with the box blank, prompting another error message, but then I can sign in as usual.  Any ideas why?  It was suggested that I change the default display manager to kdm; that is, to use kdm as the login manager even though it will be set to boot into gnome by default.  I edited /etc/X11/default-display-manager to point to kdm, which resulted in neither graphical environment loading at reboot.  Is there another config file that I also need to edit? 

Third, I find that I cannot run root apps in gnome, even with the root password.  I have to sign out and sign back into KDE.  Any ideas about this one?

Thanks for any help.

---

