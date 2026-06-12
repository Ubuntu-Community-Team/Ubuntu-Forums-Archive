---
title: "Just installed FVWM-Crystal on feisty server edition, having questions..."
date: 2007-06-10
forum: Desktop Environments
---

### Post by smartboyathome on 2007-06-10
The title pretty much says everything except the questions. The questions are:

What command is used to get the ubuntu network manager (default on desktop)? is it installed by default on the server edition?

I would like a battery moniter (I am on a laptop), and do not want to install the one with the other GNOME modules (as I don't need them). Is there anything else I could use?

I would like to use synaptic, but I cannot because there is nothing installed to give me a dialog box asking for the root password. What packages are used to do this in *buntu?

Thanks to anyone who helps! :KS

---

### Post by ugm6hr on 2007-06-10
> **smartboyathome said:**
> The title pretty much says everything except the questions. The questions are:

What command is used to get the ubuntu network manager (default on desktop)? is it installed by default on the server edition?

I would like a battery moniter (I am on a laptop), and do not want to install the one with the other GNOME modules (as I don't need them). Is there anything else I could use?

I would like to use synaptic, but I cannot because there is nothing installed to give me a dialog box asking for the root password. What packages are used to do this in *buntu?

Thanks to anyone who helps! :KS

If you're looking for a lightweight wifi manager - Wicd might be a better choice (Network Manager is GNOME-based): 
[http://wicd.sourceforge.net/pages/features.php](http://wicd.sourceforge.net/pages/features.php)
I'd recommend the 1.2.9 testing version for Feisty

As for synaptic - does *gksudo synaptic* work from Terminal?

PS: out of interest - what hardware have you got this running on?

---

### Post by smartboyathome on 2007-06-10
> **ugm6hr said:**
> If you're looking for a lightweight wifi manager - Wicd might be a better choice (Network Manager is GNOME-based): 
[http://wicd.sourceforge.net/pages/features.php](http://wicd.sourceforge.net/pages/features.php)
I'd recommend the 1.2.9 testing version for Feisty

As for synaptic - does *gksudo synaptic* work from Terminal?

PS: out of interest - what hardware have you got this running on?

Thanks for your quick reply. I will try out Wicd. gksudo synaptic does work in the terminal, and now I can access synaptic from the menu. Thanks! :)

And I don't know what I run, as I have not looked in a while. All I do know is it was a Toshiba that I got one of the last of about 1-1/2 years ago because it was taken off the market. I am using it to free some ram (also, I am hoping to create a distro to show off to my friends ;)).

---

### Post by smartboyathome on 2007-06-10
I have another problem. I installed Seamonkey in fvwm-crystal (using ubuntuzilla), but it won't show up on the applications list. Would anyone be able to tell me how I could get it to work? :( also, is there any script for rox-filer which auto-mounts drives?

btw, sorry for the double post...

---

### Post by ThomasAdam on 2007-06-10
> **smartboyathome said:**
> I have another problem. I installed Seamonkey in fvwm-crystal (using ubuntuzilla), but it won't show up on the applications list. Would anyone be able to tell me how I could get it to work? :( also, is there any script for rox-filer which auto-mounts drives?

btw, sorry for the double post...

God you're posting all over the place on differebt forums but your questions have a similar theme.  It's really annoying.

There's a script within fvwm-crystal which generates the main fvwm-crystal menu.  You can look at how it does this by reading the README file in the fvwm-crystal repository.  And no, that's not me being flippant, it really does explain the application database fvwm-crystal uses.

-- Thomas Adam

---

