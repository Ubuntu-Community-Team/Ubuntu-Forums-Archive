---
title: "Natty starts in Ubuntu Classic.  Unity available after logout/login"
date: 2011-05-25
forum: Desktop Environments
---

### Post by jdholman on 2011-05-25
Hello:

I upgraded to Natty at the beginning of May and Unity has been working fine until about 4 days ago.  Around then, then I cold boot and log in, Ubuntu starts in "Ubuntu Classic" desktop.  If I log out then back in, Unity starts as expected.

In both cases of my logging in, Ubuntu Classic is not selected - Ubuntu is, which should start the UI under Unity.

Anyone seen this before?

Regards,

Jim

---

### Post by Krytarik on 2011-05-25
Please see if this guide helps:
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Also try setting the default session option in the "Login Screen" settings to "Ubuntu" if it isn't already.

Greetings.

---

### Post by jdholman on 2011-05-26
Hello Krytarik:

Thank you for your reply.  I did consult the link you provided and confirmed my settings.

I passed the tests in these commands:

/usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test -p --compiz

I then added "FORCE START" as shown here:

Add "UNITY_FORCE_START=1" to "/etc/environment":

gksu gedit /etc/environment

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
UNITY_FORCE_START=1

Finally, I confirmed that my default session option was "Ubuntu" rather than "Classic" or similar and it was.  After rebooting, and logging in with the "Ubuntu" session, I still had Ubuntu Classic!  Even with UNITY_FORCE_START set to 1.  I logged out and logged back in and once again, I had Unity as I requested.

I have no idea when I don;t get Unity on first log in after a restart or cold boot.  Any suggestions?

Thanks,

Jim

---

### Post by Krytarik on 2011-05-26
Try removing the fallback section from Unity's session settings:
```

sudo cp /usr/share/gnome-session/sessions/ubuntu.session /usr/share/gnome-session/sessions/ubuntu.session.bak
gksudo gedit /usr/share/gnome-session/sessions/ubuntu.session
```
Remove the [COLOR=Red]**red marked**[/COLOR] entries:
```
[GNOME Session]
Name=Ubuntu
Required=windowmanager;panel;filemanager;
Required-windowmanager=compiz
Required-panel=compiz
Required-filemanager=nautilus
DefaultApps=gnome-settings-daemon;
[COLOR=Red][B]IsRunnableHelper=/usr/lib/nux/unity_support_test
FallbackSessionsID=FallbackUnity2d;FallbackClassicGnome
FallbackUnity2d=2d-ubuntu
FallbackClassicGnome=classic-gnome
FallbackClassicGnomeMessage=It seems that you do not have the hardware required to run Unity. Please choose Ubuntu Classic at the login screen and you will be using the traditional environment.[/B][/COLOR]
```

---

### Post by jdholman on 2011-05-26
Hi Krytarik:

After removing those lines, would you believe that I still need to boot, log in, log out, and log in again to get to Unity?  I don;t understand how Natty falls back or otherwise selects Ubuntu Classic when I am not selecting it at login and we have disabled it as a fall back.

I don't know how it is doing what it is doing.

Jim

---

### Post by Krytarik on 2011-05-27
I just learned why GDM doesn't respect a user's "~/.dmrc" upon the first login, and where it instead pulls the session settings from:
[https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5](https://defect.opensolaris.org/bz/show_bug.cgi?id=14575#c5)

However, that seems not to be the cause in your case, since you said you are consciously logging into "Ubuntu" even at the first login, so you see that those session option is selected when you log in, right? And when you log out and click at your username, "Ubuntu" is also (still) selected?

---

### Post by jdholman on 2011-05-28
You are correct.  I coldbooted last night and it DID log into Unity, so I don't know why it does it sometimes and not others.

---

### Post by rtimai on 2011-06-05
Krytarik,

Here's additional anecdotal user information on the Unity issues.

I also upgraded to Ubuntu 11.04, have a Radeon video adapter on the open source driver, and was booting to a fully functional Unity desktop for several weeks. Then one day different parts of the desktop disappeared, and on restarting I had the wallpaper-only syndrome. I thought it might have been caused by my installing a couple of Gnome desktop themes, but other accounts suggest other reasons as well.

Most critical was that logging in to Ubuntu Classic resulted in BOTH Unity and Classic components visually overlapping one another. Yes, I had overlapping toolbars. 

"Ubuntu Classic (no effects)" appeared normal (don't know if hardware acceleration was turned off or not.)

The "unity --reset &" and "unity --reset-icons &" commands appeared to fix the symptoms -- until I closed the Terminal, and all reverted to wallpaper-only (to the best of my recollection.) 

I followed all the suggested remedies for no-toolbars-in-Unity without success. 

Resetting Compiz had no effect. (The terminal commands gconftool --recursive-unset /apps/compiz-1 and ... /apps/compizconfig-1) turns out to be wrong, I recently discovered.) Both storage locations are under /.config, not /apps. It seems there's a LOT of obsolete information out there for fixing Unity. I wonder if following them could confound other fixes.

Anyway, I reset (hopefully) Compiz using the graphical console.

I don't know if this is important, but I noticed that whenever I restarted GDM I found the active desktop on a different tty. It moved one over every time the desktop was restarted. I made certain that I pressed Ctrl-Alt-Bkspace and then used the icon at the lower right corner of the login screen to RESTART -- I avoided logging back in (no restart) to prevent the desktop from moving to a different terminal. I don't know if the tty affected where user settings were saved (probably not,) but I tried to keep it consistent, just in case. 

Logged on to Ubuntu Classic, from the Software Center I removed Unity, and I also removed all the Add-ons listed below it. Restarted, and my Ubuntu CLASSIC desktop was restored. And I stuck with it. That was then...


Since then, over the past month I saw several GTK and Compiz updates installed, and also noticed that the GConf and DConf editors showed a great reduction in the number of keys listed (hopefully to remove collisions of settings.) I decided to try Unity (with all the add-ons) again, installing from Software Center. 

SAME RESULTS.

So, once again, I removed Unity using Software Center. This time I checked Synaptic Package Manager, and found that a search for Unity revealed more items still installed. I selected them also for removal. 

I have looked at apt-get options, and will run --autoremove, hopefully it will remove any residual configuration settings that may cause collisions in the future. 

After removing what I believed to be all of the Unity elements (EXCEPT Compiz and CCSM) I rebooted. The "Ubuntu" login option REMAINS in the GDM login menu. Attempting to boot to it results in the wallpaper-only syndrome -- as one would expect -- except that the "Ubuntu" login option should not even be listed any longer. (Apparently the developers never expected that anyone would have to remove the Unity desktop.)

I understand that it is NOT the OS or Compiz that is the problem, but that it is the Unity desktop configuration settings used by Compiz that are causing the problem. I believe that incorrect, missing, or colliding settings are causing the Unity desktop to fail. 

Possible factors involved with Unity Misconfigurations:

1 - Canonical moving away from Gnome desktop may be causing a breakdown in critical communications -- some Gnome themes are apparently overwriting some settings required by Unity 3D. (Also, the art.gnome.org/themes, the default "Get more themes online" link in desktop Appearance shows duplication of several theme names. I seem to have gnome_alternative and gnome-alternative themes installed (possibly each using different methods.)

2 - Active desktop moving TTY on logout/in. Does it affect the login menu?

3 - When installing Unity components using different methods (e.g. apt-get commandline, Synaptic Package Manager, Software Center,) results are not the same. Removals may have to use the same technique as used for installation. Otherwise, why should I find still-installed Unity components in the Synaptic list after I expected to have removed them all in Software Center? This may result in residual settings that interfere with subsequent installations.

No response expected. I can wait till Oneiric, no problem.

---

