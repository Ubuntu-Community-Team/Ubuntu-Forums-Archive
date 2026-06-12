---
title: "Ubuntu 11.04 Errors .ICEauthority, configuration server, Nautilus"
date: 2011-09-10
forum: Desktop Environments
---

### Post by mintberry_crunch on 2011-09-10
Hey guys, i really need your help on this one.
When i booted ubuntu today, i received some error messages after i logged in.

First of all there is a window: Could not update ICEauthority file/home/USER/.ICEauthority

when i close that, the next window pops up: There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

and finally there is a message stating: Nautilus could not create the following required folders:/home/USER/Desktop,/home/USER/.nautilus

after having closed all the windows the screen remains blank.

I already tried to solve the .ICEauthority error using
sudo chown USER:USER /home/USER/.ICEauthority
however i had no sucess as it always says: "Cannot acces /home/USER/.ICEauthority: No such file or directory


The only thing i remember doing yesterday that could somehow be related to that problem is installing Veetle

I have no clue how i may solve that problem so please help me

---

### Post by Krytarik on 2011-09-10
May it be that you have an encrypted home directory and enabled auto login now?

If so, disable it again.

Greetings.

---

### Post by BushyIII on 2011-09-10
I have the identical problem. 
I disabled Autologin, rebooted and am presented with the same experience, i.e. Could not update ICEauthority file/home/USER/.ICEauthority, There is a problem with the configuration server, Cannot acces /home/USER/.ICEauthority

Any other suggests?

---

### Post by Krytarik on 2011-09-10
BushyIII, while also pointing to your [own thread]("http://ubuntuforums.org/showthread.php?t=1841419"), try this (just for a test, not as the solution):

1. At the login screen, press Ctrl+Alt+F1 to get to the console.

2. Log in there.

3. Check if you can access the files in your home directory, incl. ".ICEauthority".

4. If yes, switch back to the login screen by pressing Ctrl+Alt+F7 or F8 and try again to log in.

5. If no, meh!

---

### Post by BushyIII on 2011-09-11
Tried your suggestion but get a response that the files does not exist.  I have an encrypted file system.  Oddly, when I log in at the terminal I get a response that I do not own the encrypted directory.  I am using my normal login credentials.  What gives, does it think I am someone or that there is a different owner?  IF so I do I find out who the new owner is and change it back to me?

---

### Post by Krytarik on 2011-09-11
Did you change your login password lately, maybe through root? If yes, see this bug report:

[https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/579876](https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/579876)

This guide outlines that changing the login password in the usual way would update the password for the encryption as well:

[http://bodhizazen.net/Tutorials/Ecryptfs#Password](http://bodhizazen.net/Tutorials/Ecryptfs#Password)

---

### Post by BushyIII on 2011-09-11
Before I try anything else, is there a way I can determine what the owner's name is for the encrypted directory since it doesn't think it is me?
I can use the terminal or I can use the gui from a different user login.

---

### Post by BushyIII on 2011-09-11
Sorry, I didn't answer your original question.  I didn't change my password.  I tried typing"ecryptfs-mount-private " and the response was that the encrypted directory wasn't set up correctly.  Hope the additional information may help find a solution.

---

### Post by Krytarik on 2011-09-11
> **BushyIII said:**
> Before I try anything else, is there a way I can determine what the owner's name is for the encrypted directory since it doesn't think it is me?
Yeah, sure, check it with:
```
ls -al /home/.ecryptfs
```This should turn up a directory with your username, and those should be owned by you. If it isn't, change it:
```
sudo chown USERNAME:USERNAME -R /home/.ecryptfs/USERNAME
```> **BushyIII said:**
> I can use the terminal or I can use the gui from a different user login.
Yeah, you can use the GUI from within the desktop of another user, but I would just use the terminal.

---

### Post by BushyIII on 2011-09-11
Well running the command shows that I am in fact the owner,  and again if I run ecryptfs-mount-private it reports that it wasn't setup correctly.  Am I dead in the water?

---

### Post by Krytarik on 2011-09-11
> **BushyIII said:**
> Am I dead in the water?
Well, I'm not really experienced in those encryption stuff, so you have to do a bit of research on your own - I list my bookmarked guides below -, and/or wait for someone with more experience in this.

[http://bodhizazen.net/Tutorials/Ecryptfs](http://bodhizazen.net/Tutorials/Ecryptfs)
[http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html](http://blog.dustinkirkland.com/2009/03/mounting-your-encrypted-home-from.html)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

Good luck!

---

### Post by BushyIII on 2011-09-11
OK, thanks for all your effort.

---

