---
title: "New installation - Various failures"
date: 2005-12-20
forum: Desktop Environments
---

### Post by bobinski on 2005-12-20
Hello, I've just installed ubuntu 5.10 from CD but am having problems - I can log in as the user I set up and the desktop seems OK.  I get an icon in the top right which says there are 34 updates available, but when I right click and select show updates nothing happens after supplying the password.  Selecting System/Administration/Update Manager  does nothing at all.  I can't login as root at the initial prompt.  Does anyone have any ideas?:???:

---

### Post by stalefries on 2005-12-20
Open Applications>Accessories>Terminal.
Type the following```
sudo apt-get update && sudo apt-get upgrade
```
It will then ask for *your* password. when you are typing your password, it woll not show little asterisks (*) or any other symbols, but don't worry. That's standard. After doing this, and waiting several seconds to a minute, it will ask you a yes or no question about installing the updates. Press "y", and press enter. After waiting a couple of minutes, you updates should be installed. If this gives you any problems, please copy the output of the command I gave you. That should give us a starting point on figuring out the problem.

---

### Post by bobinski on 2005-12-21
Thank you very much for your reply.  I've just tried your suggestion and do get a Password: prompt but after sending the reply to it I get no output at all and it immediately outputs a new command prompt, I don't get any question at all!

---

### Post by bobinski on 2005-12-25
Hmm, I still don't have a fully working setup.  I think I'll try a re-install and if that doesn't work, I guess it's goodbye :-(

---

### Post by kaamos on 2005-12-25
Try this is terminal:
```
sudo rm /var/cache/apt/*.bin
```
And if it still does not work, could you please post the exact output of this
```
sudo echo "testing sudo"
```

---

### Post by bobinski on 2005-12-25
[QUOTE=kaamos]Try this is terminal:
```
sudo rm /var/cache/apt/*.bin
```
And if it still does not work, could you please post the exact output of this
```
sudo echo "testing sudo"
```[/QUOTE]

Thank you for your reply.  Unfortunately I had already started a re-installation when you posted.  I used the default installation and it is now working.  I have no idea why.

---

### Post by Mustard on 2005-12-25
Just out of curiousity, did you use the 'expert' install option the first time around?

If that was the case, then the first account would not have been set up with sudo privileges.  It would have asked you to input a root password during the setup, and then asked if you wanted to set up a normal user.

---

### Post by bobinski on 2006-01-04
[QUOTE=Mustard]Just out of curiousity, did you use the 'expert' install option the first time around?

If that was the case, then the first account would not have been set up with sudo privileges.  It would have asked you to input a root password during the setup, and then asked if you wanted to set up a normal user.[/QUOTE]

Yes, I did use expert, would a normal user not have had sudo privilege?

---

### Post by thekiller on 2006-01-04
it should have root privileges. However i created myself a separate root password to  avoid writing sudo everytime I wanna install something. If you wanna use it too just do

```

$ sudo su

```

Now it will ask for your current user password, enter that and now you will be root, and at the root prompt type :

```

# passwd

```

Enter your password twice, and your root password is set up. Next time you want to use it, just type "su" on the prompt and feed your root password in.

---

