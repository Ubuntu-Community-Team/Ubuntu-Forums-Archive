---
title: "beryl screensaver ????"
date: 2007-04-08
forum: Desktop Effects &amp; Customization
---

### Post by celticbhoy on 2007-04-08
I have got my Ubuntu & Beryl working just as I want it, but now I want to show it off. Is there such a thing as a screensaver that uses your desktop and shows a type of demo of Beryl's features ???

That way when I have friends round I can let the screensaver kick in and impress them, instead of having to out & out brag.

---

### Post by SargentFuzz on 2007-04-09
I recently had the same idea, how it would be nice for a screensaver to just rotate the desktop cube until mouse/keyboard activity, but I have not been able to find anything of the sort. Too bad, as it would make a pretty awesome screensaver.

---

### Post by Gallardo Spyder on 2007-04-10
The new 3.0 SVN release of Beryl has a new option...  Screen saver...  Replaces the standard Gnome Screen Saver.

You can set it up in Slow Motion, do negative, etc.  Very cool addition!  You can also set the idle time for it to kick off, etc.  Just like a normal SS...  But you get it from the beryl setting manager...

Here is the repository if you don't have it...

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

---

### Post by celticbhoy on 2007-04-10
Added the repo, but how do I update????

---

### Post by celticbhoy on 2007-04-10
its ok just remembered 'sudo apt-get upgate'

---

### Post by celticbhoy on 2007-04-10
Got the screen saver option on beryl now but cant seem to get it to cick in.

anyone know if you have to make any settings in gnome screensaver or anywhere else to get this to go ???

---

### Post by celticbhoy on 2007-04-10
Can get it to work with the hotkey, so maybee it doesn't start after a set time, but only when selected.

---

### Post by Gallardo Spyder on 2007-04-11
Mine worked fine - I disable the normal gnome SS under system/preferences - unclicked idle time.

Also - I do notice occasionally when restarting the system - Gnome, and now Beryl does not restart the SS.  I just get a blank screen instead of the SS I chose (or in this case the rotating cube).  Since I don't restart that often,  The fix I have found is if I just go into it (Gnome SS or Beryl SS) - just going into the app SS settings and it then works - until I restart again.  Odd.

---

### Post by celticbhoy on 2007-04-12
will give it a try - how do you set the delay time for beryl screen saver ???

---

### Post by celticbhoy on 2007-04-12
its ok found it

---

### Post by Gallardo Spyder on 2007-04-12
> **celticbhoy said:**
> will give it a try - how do you set the delay time for beryl screen saver ???

Similar to Gnome SS - when you are in Beryl Manager - got to Extras...  Click to enable the Screen Saver, to the right you will see options - you can set the time from 0 idle time - which means not active to 120 minutes...  However I think you actually have to set it for 60 minutes or less (I read in one of the posts on another forumn) - evidently it may not work if set to more than 60 minutes...  So put 45 minutes or something less than 60 minutes.

GSpyder

---

### Post by Fireblend on 2007-04-12
> **Gallardo Spyder said:**
> The new 3.0 SVN release of Beryl has a new option...  Screen saver...  Replaces the standard Gnome Screen Saver.

You can set it up in Slow Motion, do negative, etc.  Very cool addition!  You can also set the idle time for it to kick off, etc.  Just like a normal SS...  But you get it from the beryl setting manager...

Here is the repository if you don't have it...

deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

Where do I find the signature? it says its missing...

---

### Post by Gallardo Spyder on 2007-04-12
> **Fireblend said:**
> Where do I find the signature? it says its missing...

Go to a terminal and do:

wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O - | sudo apt-key add -

make sure you also do a:

sudo apt-get update

That should take care of it - if it doesn't let me know,,,

GSpyder

---

### Post by fatray on 2007-10-12
> **Gallardo Spyder said:**
> Go to a terminal and do:

wget [http://3v1n0.tuxfamily.org/DD800CD9.gpg](http://3v1n0.tuxfamily.org/DD800CD9.gpg) -O - | sudo apt-key add -

make sure you also do a:

sudo apt-get update

That should take care of it - if it doesn't let me know,,,

GSpyder

I did what you said above, looked like everything went the way it's supposed to.  I still don't see "Screen Saver" under the Beryl Manager Extra options.  Even after a restart.

---

### Post by alefnull on 2007-10-12
just a quick side question about the screensaver...

are there any other settings for the screensaver other than rotate cube? if there are, they aren't available to me... when i hover my mouse over the dropbox it says something (can't remember what) that implies there was at least one other one that is/was either available or under development...

---

### Post by celticbhoy on 2007-10-13
Screensaver only gives the rotate cube. You have a couple of settings but the cube is the only screensaver

---

### Post by KhaaL on 2007-10-14
> **celticbhoy said:**
> Screensaver only gives the rotate cube. You have a couple of settings but the cube is the only screensaver

This is incorrect. The screensaver plugin i had under CF gave flying windows aswell.

And in order to get it, i think you need to install the plugins-unofficial or plugins-unsupported package.

---

### Post by celticbhoy on 2007-10-14
can only comment on what I had available to me.

---

