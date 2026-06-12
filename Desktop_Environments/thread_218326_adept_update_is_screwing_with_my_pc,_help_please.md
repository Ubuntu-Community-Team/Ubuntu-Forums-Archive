---
title: "adept update is screwing with my pc, help please"
date: 2006-07-18
forum: Desktop Environments
---

### Post by maddbaron on 2006-07-18
I had for upgrades showing so I tried to upgrade two i think were linux images and 2 were for my kernal. as soon as i started the process my klamav went insane and my pc kept forcefully shutting down on its own. i rebooted about 3 times and same thing happened. I only get up to about 40percent on the update then shutdown on its own. now I am trying to install avast so i can get rid of klamav and i am told that adept, or one of my other update managers is running and to shut them down.

how can do this please? it wont let me install anything.

and if my upgrades keep shutting down my pc what can I do?

---

### Post by briguy on 2006-07-18
First thing to try would be to do the update from a terminal.  Enter the following:

```
sudo apt-get update
sudo apt-get upgrade
```

And that *should* fix your problems.  If it doesn't, post the error message and we can work from there.

---

### Post by maddbaron on 2006-07-18
thank you, i got no error messages and finally got to install avast so i just removed klamav and clamav but when i did get upgrade i was told there were none. my pc shutdown before the previous upgrade was complete i believe is there anyway to check?

and with avast now is there any way for me to add it to my quick launch and my startup when the pc starts and do u know how i can set its settings incase it finds anything?

---

### Post by briguy on 2006-07-18
If apt said there were no updates available, then you're ok.  Adept should work now as well.

If you want avast (or any program for that matter) to start up under KDE, there are a few ways to do it.  I like to save a session to start up (I like to have Kerry search and Yakuake running when I login, for example).  Under your K start menu, there is a "Save Session" option.  From a clean login, start up the programs you want to have running, then click the Save Session option.  Next, go to the Control Panel and click on KDE Components, then Session Manager.  Select the "Restore manually saved session" option, and KDE will load the saved programs everytime you login.

The other way to do it is to put a script in your ~/.kde/Autostart/ directory.  Save a text file with the name of the executable in it, chmod +x the text file and it will run the script when you login.  If you don't know what I'm talking about, go with the first option ;).

It's interesting that you're running Avast - I didn't know they had a linux version!

---

