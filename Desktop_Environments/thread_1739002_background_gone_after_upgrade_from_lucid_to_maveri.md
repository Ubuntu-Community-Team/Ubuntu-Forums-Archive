---
title: "background gone after upgrade from lucid to maverick"
date: 2011-04-25
forum: Desktop Environments
---

### Post by rizos on 2011-04-25
background now is gone (just a gray area) if i tick off show background in gconf-editor-->preferences--> show desktop (off) the wallpaper appears but desktop icons and volumes are gone.

i can't find what can be wrong.


any idea?.


thanx

---

### Post by Krytarik on 2011-04-25
I guess you mean "/apps/nautilus/preferences/show_desktop". It seems like Nautilus doesn't handle the desktop properly.

Are the icons there if you enable "show_desktop"?

Do you have any other issues with Nautilus?

---

### Post by rizos on 2011-04-25
yes you are rigth i mean that.


also yes,there are icons in the desktop when the wallpaper is gone and gray (when "show_desktop" is enabled) .

volumes and folders

other wise i dont have any problem with nautilus.

---

### Post by Krytarik on 2011-04-25
Please check if that also occurs with a new user, go to "System -> Administration -> Users and Groups" to create one.

---

### Post by rizos on 2011-04-25
done: created a new account and same problem.


no wallpaper and if i change the picture it goes black instead of gray.

---

### Post by Krytarik on 2011-04-25
What version of Nautilus are you using, plain/official Nautilus, provided the official repos, or Nautilus Elementary?
To check that, go to "Help -> About".

Try reinstalling "nautilus" and "nautilus-data":
```
sudo apt-get install --reinstall nautilus nautilus-data
```

---

### Post by rizos on 2011-04-25
done: reinstall nautilus by the command in terminal and nothing change, something new is that in every restart my theme changes and when i click the appereance button from system it comes back to normal.:shock:


 im using Nautilus 2.32.0 version and i guess in the one in the official repos cause i just upgrade to maverick straigth simple upgrade.

---

### Post by Krytarik on 2011-04-25
> **rizos said:**
> something new is that in every restart my theme changes and when i click the appereance button from system it comes back to normal.
This one is a common bug of Maverick (and onwards?), see here:
[http://ubuntuforums.org/showthread.php?t=1575703](http://ubuntuforums.org/showthread.php?t=1575703)

Recent threads with summed-up workarounds:
[http://ubuntuforums.org/showthread.php?t=1722179](http://ubuntuforums.org/showthread.php?t=1722179)
[http://ubuntuforums.org/showthread.php?t=1724702](http://ubuntuforums.org/showthread.php?t=1724702)

That may also be the reason for your original issue, and those may as well get solved by applying one of these workarounds.

---

### Post by rizos on 2011-04-25
WOW now something got pretty bad.


i cannot log in into ubuntu any more, i delete the new account i created then log out when login again put my password the login page keep reloading and i cant get into ubuntu any more.

admin account and guest account... there is no way to get in.


how can i solved this, please help!

---

### Post by Krytarik on 2011-04-25
Are you getting any error messages?

Login at a console and check "~/.xsession-errors" for related error messages:
- press Ctrl+Alt+F1
- login there
- run:
```
cat .xsession-errors
```
Did you something more before, aside from removing the newly created user?

---

### Post by rizos on 2011-04-25
i cannot login into ubuntu no terminal...no nothing.



i should reinstall ubuntu and see if this helps...


but how?

---

### Post by Krytarik on 2011-04-25
Without following exactly my instructions and/or providing more information I cannot help.

---

### Post by rizos on 2011-04-26
this is what exactly happens i deleted the user account i created for testing then i uninstall nautilus via synaptic and re install.

logout and everything was ok...till login page keeps reloading over and over again i couldn't login in any of both accounts i had admin and guest.

nothing i could do.


insert passwrod and then bring me back to the login screen.


didn't knew how to access terminal to get xsessions-errors

i use puppy linux and my whole data was safe and sound but couldn't log in.


next i reinstall ubuntu 10.10 form a live cd.


now i can login as i created a new admin account same name and password.

all my info is there in home even the guest account and files is there but i cant access that info.


i have to reinstall all the applications so they can work.

opera, skype, dejadup etc...


but they are a LOT...


now the wallpaper issue it's solved but the theme keeps changing on login and i cant recover the guest account...


but all applications are there.


wish i could bring this back to normal even go back to lucid (hahaha)


any ideas what to do now?

---

### Post by Krytarik on 2011-04-26
So, do I understand correctly that you have a separate home partition and the home directory of each user is encrypted?

If so, I don't have much of experience with encrypted home directories, but these guides may help:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
[http://bodhizazen.net/Tutorials/Ecryptfs/#Live](http://bodhizazen.net/Tutorials/Ecryptfs/#Live)

Also, make sure that the settings of the guest user are exactly the same as before, especially the UID and GID.

As for the gnome-settings-daemon bug, did you try the mentioned workarounds?

---

### Post by rizos on 2011-04-26
i reinstall ubuntu on the same partition of the old ubuntu.


it went pretty normal...


i still have all my files (music, vids, pix) but applications arent showing in the applications menu but they are in home folder.

if i install them like opera (browser) now they work normal with all my old settings.

the guest account is gone from the login screen but it shows up in home folder i wonder if i create an account with same name and no password to log in will bring it back?



im kind of very lost at the moment trying to recover my system... bit hard to focus on the work arounds of nautilus.


creepy nautilus...:D


cheers for your help maite!...

---

### Post by Krytarik on 2011-04-26
> **rizos said:**
> 
the guest account is gone from the login screen but it shows up in home folder i wonder if i create an account with same name and no password to log in will bring it back?
Ok, I thought you did that already. Then do it now, but possibly with the same password as before, at least if the home directory is indeed encrypted, which you didn't answer. Do you see the content of its home directory then, if you access it as root?

---

### Post by rizos on 2011-04-26
the guest account works the same passwordless and i can access the home folder of the new admin account and guest account...

i can access all files... what i ddi is replace the whole OS on the same old partition so now all files and settings are there but when i try to launch some appl like skype it says no process child found and then cant use that appl unitl i donwloaded again then all setting are as i had them.

so far my system is back and working all files can be access in both accounts.


but it is a huge process to reinstall all my appl...is there a way to solve this issue?.

now im working in thew work arounds of this post...

---

### Post by Krytarik on 2011-04-26
> **rizos said:**
> so now all files and settings are there but when i try to launch some appl like skype it says no process child found and then cant use that appl unitl i donwloaded again then all setting are as i had them.
It's because you apparently had set up custom launchers, or modified the menus in their aspect, and those are still there because the user profiles were preserved, but the actual apps aren't.

---

### Post by rizos on 2011-04-27
back on topic and now that my system is back to "nomral"...


i try the work arounds on the post and didnt work out.


i change the time to 15 even 20 and nothing...

then i try this fix for [bug#574296]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296") and nothing...


it's a bug and now that my background is back i still have the issue that theme changes back to the 80's...


any other ideas?...

---

### Post by Krytarik on 2011-04-27
When you get the 80's look right after login, run these commands and report if they restore your theme, run them slowly after each other, to give them time to finish:
```
killall gnome-settings-daemon
gnome-settings-daemon
killall nautilus
```

---

### Post by rizos on 2011-04-27
ok this is the out put of the first command 

killall gnome-settings-daemon
gnome-settings-daemon: no process found


then the second which actually fix the theme bringing it to the present...

** (gnome-settings-daemon:1881): WARNING **: Key binding (custom0) is invalid
rizos@rizos-G31D-M7:~$ Unable to find a synaptics device.


and killing nautilus finally fix the folder look to the normal one.

---

### Post by Krytarik on 2011-04-27
Ok, fine. Now we only need to find a working set of startup commands.

- How long does your system precisely take to load your desktop, after pressing the 'Log In' button at the login screen?

- Check if "gnome-settings-daemon" is running (but crashed) after login:
```
ps ax |grep -v grep |grep gnome-settings-daemon
```

---

### Post by rizos on 2011-04-27
it takes 33 seconds to show the desktop...


the code wont bring any output in terminal after running it.

---

### Post by Krytarik on 2011-04-27
I just yet noticed that you already confirmed earlier that "gnome-settings-daemon" isn't running after login:
> **rizos said:**
> 
killall gnome-settings-daemon
gnome-settings-daemon: no process found

So, sorry for the unnecessary check.

Then try setting at least a delay of 25 secs, add this command to "Startup Applications":
```
sh -c "sleep 25; gnome-settings-daemon; killall nautilus"
```

---

### Post by rizos on 2011-04-27
i try before and now this work around with 30 and 35 seconds and no luck.


theme still changes then i have to open appereance menu to have it fix and then killall nautilus in terminal to fix the view of folders.


so basically is not working...

---

### Post by Krytarik on 2011-04-27
Basically, these commands, if put properly into "Startup Applications", do exactly the same as you did in a terminal. Maybe try an even longer delay.

---

### Post by rizos on 2011-04-27
finally...


setting to 55 seconds did the trick...


i hope this nasty bug is killed for natty release...

---

### Post by Krytarik on 2011-04-27
That's fairly long, maybe it's still running after login, but in a crashed state.
So, try setting the command like this:
```
sh -c "sleep 25; killall gnome-settings-daemon; gnome-settings-daemon; killall nautilus"
```As for Natty, I didn't hear about much issues with those bug in the beta so far. The only report of those issue in Natty I remember is more than three weeks ago, in the bug's megathread, I just yet checked it:
[http://ubuntuforums.org/showthread.php?p=10630903#post10630903](http://ubuntuforums.org/showthread.php?p=10630903#post10630903)

---

