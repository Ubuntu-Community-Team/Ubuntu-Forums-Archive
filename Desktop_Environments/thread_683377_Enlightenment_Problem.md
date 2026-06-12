---
title: "Enlightenment Problem"
date: 2008-01-30
forum: Desktop Environments
---

### Post by Scott8855 on 2008-01-30
I have a fresh install of Gutsy, I installed enlightenment and was playing around with some themes and got stuck in one.  I was not able to center click or any click on the desktop to access any themes.  I went back in to regular gnome, rather then e-gnome and removed enlightenment, it was gone from the options, then i reinstalled it and went back into e-gnome and I was right back where I started.  I thought removing it would remove the bad theme but it didn't.  I can't access ~/.enlightenment/themes either so I have no idea how to get enlightenment back to a fresh install so I can screw it up again :)  Any ideas?

Scott

---

### Post by kiikkuja on 2008-01-31
You could try going back to Gnome and in there Synaptic. Remove the Enlightenment again using the remove completely option. After that you should have clean system without any of the enlightenment configs and such. 

BTW why haven't you able to access the enlightenment folder?

---

### Post by Scott8855 on 2008-01-31
That is what I did, went back in to gnome rather then e-gnome and removed enlightenment with the package manager.  Next I logged out of gnome, checked to make sure that enlightenment and e-gnome were no longer an option, they were not.  Then I proceeded to reinstall enlightenment, logged out of gnome, went into e-gnome and it was exactly like it was prior to removing it. 

As for ~/.enlightenment/themes goes, it appears to not exist anymore.  When i was playing with themes I would go to the shell and cd to ~/.enlightenment/themes and then untar the themes into that folder, then restart enlightenment, center click and load the theme.  After loading this particular theme I can not center click on the desktop to change themes or find the /.enlightenment/themes folder to remove the theme giving me the trouble.

Scott

---

### Post by jazzykay on 2008-01-31
Are you sure your e17 files are in ~/.enligtenment?
I just checked mine and my e17 files are in ~/.e/e/themes

Can you check to see if you have a .e folder in your home directory?

---

### Post by Scott8855 on 2008-02-01
I know they were in /.enlightenment, I put the themes i loaded there and they were working great, I may have e16, whatever Ubuntu loads from the package manager.  

How would it revert back to that theme after I remove enlightenment and reinstall it?

EDIT:  Hold on I may have this figured out, some how i managed to find a .enlightenment/themes folder so i removed it, now i'll re-install enlightenment and see what happens

---

### Post by kiikkuja on 2008-02-02
There is** two** options in the Synaptic package manager when removing packages. There is **remove** and **remove completely**. The latter option is supposed to remove the config files affiliated with said package. 

But it's nice if you solved your problem already...just wanted to make myself as clear as possible.

---

