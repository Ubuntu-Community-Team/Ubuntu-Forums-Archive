---
title: "Changing the home folder name"
date: 2007-09-01
forum: Desktop Environments
---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-01
I posted this awhile ago but it was a sub-concern of three and I've had enough trouble with it for it to warrant a thread.

I want to change the name of my home folder without compromising everything else on my PC? For example, if my home folder's name was "goku" and my current login is "kakarot", I would currently want my home folder to be "kakarot" as well.

I was given these instructions:

> **aquavitae said:**
> 
b) At the [GRUB] login, give the username as 'root'(without quotes) and give your user password when it prompts for password (Note that it won't show anything as you type your password.)  I'm not certain of the way ubuntu handles the root user, so it might not accept that.  If it doesn't, just log in to your normal user.

c) Type the following (if you logged in as root, don't type the 'sudo' part), replacing *home-folder* with the name of your new home folder, and *username* with your user name ```

sudo usermod -d /home/*home-folder* -m *username*

```

d) Reboot by typing ```
sudo reboot
```

I selected the latest generic kernel's recovery mode, and it automatically logged in as root. (I don't know if that's a bad thing, but oh well, it's not my concern right now.) I then typed the equivalent of "usermod -d /home/goku -m kakarot" and then "usermod -d /home/kakarot -m kakarot" just to make sure that I did it correctly.

When I rebooted, it told me that the username "kakarot" pointed to "home/kakarot" but there was nothing in it (or something similar to that, I can't recall the exact error message) and that it wouldn't be able to log in. It then offered me to log in with root as my home folder, which I did, and it promptly logged out to the title screen.

I then went back into the GRUB menu, changed it back to /home/goku and now everything is working again.

Am I doing something wrong, or is there a better way to do this?

---

### Post by lloyd_b on 2007-09-01
You're only doing *half* the job.  

First, log in in recovery mode as you did before, and run the commands you were provided.  This correctly changes the account's pointer to the home folder
.
(You could potentially do this without recovery mode by prefacing those commands with "sudo", but you'll need to do this from another account.  Trying to reconfigure the "kakarot" account while logged in a "kakarot" could lead to bizarre results).

But this command does NOT create a new home folder, nor does it move the existing folder to a new location.  It just changes the pointers.  That was why you had problems logging in - your account was pointing to "/home/kakarot", but that directory didn't exist!

So you need to move your existing home folder "/home/goku" to "/home/kakarot".  While still in recovery mode:
```
mv /home/goku /home/kakarot
```

Then reboot, and your normal account should be accessible.  

Be advised - there may be other problems with this change.  For instance, some programs may have remembered that "/home/goku" was your home folder the last time you ran them, and get confused because of the change.  This ideally shouldn't happen (well written programs use "~" to reference your home folder, rather than the explicit "/home/goku"), but there *are* poorly written programs out there... 

Lloyd B.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
Hm. When I used "mv /home/goku /home/kakarot", it caused this error:

> User's $HOME/.dmrc file is being ignored. this prevents the default session and language from being saved. File should be owned by the user and have 644 permissions. User's $HOME directory must be owned by the user and not writable by other users.

Evidently "/home/goku" was moved to "home/kakarot/goku", though that was fixed by moving it back to "/home/goku". I'm probably doing this incorrectly..

---

### Post by Happy_Man on 2007-09-03
If you have already created this account "karkarot", then there should be a folder named "karkarot" in you /home folder. So just log in to the karkarot account, and everything should be setup with the defaults.

---

### Post by lloyd_b on 2007-09-03
> **boiiinnnnnnnnnnnnnnnnggg said:**
> Hm. When I used "mv /home/goku /home/kakarot", it caused this error:



Evidently "/home/goku" was moved to "home/kakarot/goku", though that was fixed by moving it back to "/home/goku". I'm probably doing this incorrectly..

Okay - I was making an assumption.  Specifically, I was assuming that "/home/kakarot" did not already exist.

"mv /home/goku /home/kakarot" will, if there is no "/home/kakarot", simply rename the directory "goku" to "kakarot" (well, it's a little more complex than that, but that's the result).

On the other hand, if "/home/kakarot" already exists, then that same command will move "goku" into a *subdirectory* of "/home/kakarot".  This is what happened to you.

If you "rm -r /home/kakarot" first, to remove any existing "/home/kakarot" directory, then do the "mv /home/goku /home/kakarot", you'll get the desired results.

Lloyd B.

---

### Post by boiiinnnnnnnnnnnnnnnnggg on 2007-09-03
I should have mentioned this earlier, but forgot to, sorry.

"home/kakarot" actually didn't exist. I got an error that the folder didn't exist when typing "mv /home/goku /home/kakarot" so I typed "mkdir /home/kakarot" to quell that error.

---

### Post by lloyd_b on 2007-09-03
> **boiiinnnnnnnnnnnnnnnnggg said:**
> I should have mentioned this earlier, but forgot to, sorry.

"home/kakarot" actually didn't exist. I got an error that the folder didn't exist when typing "mv /home/goku /home/kakarot" so I typed "mkdir /home/kakarot" to quell that error.

:confused: As stated in the previous message - if "/home/kakarot" didn't already exist, it *should* have simply renamed "/home/goku" to "/home/kakarot".

Could you provide the exact error message from the "mv"?  

Lloyd B.

---

### Post by Happy_Man on 2007-09-04
Like I said, man: if you just log in as your karkarot user, then it should make a /home directory for you. If you want all your settings in there, you can copy them over from /home/goku at the same time you are logged in as karkarot. 

Now, if you are having problems logging in or this is just part of some bigger issue, please post that issue, and we can kill more birds with one stone.

---

