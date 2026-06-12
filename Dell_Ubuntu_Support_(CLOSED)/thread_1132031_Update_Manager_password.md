---
title: "Update Manager password"
date: 2009-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by andreMini9 on 2009-04-21
I bought a Dell Mini 9 with Ubuntu 8.04 around Christmas for my wife.  As I was helping her with something I noticed there are 188 updates available, so I tried to install them.  I get prompted for an Update Manager Password to install them.  I have no idea what the pwd is - all I've done since I got the computer is setup a couple of shortcuts for her on the desktop.  Dell was of course worthless.  Can anyone tell me what the Update Manager password might be?

Thanks, Andre

---

### Post by _Purple_ on 2009-04-21
Use the password of the first user you have created.

---

### Post by andreMini9 on 2009-04-21
Unfortunately, I can't remember what it is - honestly I don't remember setting one up.  I tried to go to the user properties and changing it but it asks for a password to modify the user.  Am I screwed?  I really don't want to re-install - especially cuz I'm a ubuntu rookie.

---

### Post by _Purple_ on 2009-04-21
Then how do you login? How many users are there?

---

### Post by andreMini9 on 2009-04-21
There is only 1 user, and she never has to login.  I turn it on and it goes straight to Dell's modified desktop.

---

### Post by sir_nasty on 2009-04-21
reset it ;)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

esc timing is critical here if grub is set to 0 seconds... might take a few tries

---

### Post by andreMini9 on 2009-04-21
Thanks very much - that worked and now my updates are installed!  You're correct about hitting the esc key - tricky.  Is it possible to set the grub to something other then 0?

---

### Post by gbrainin on 2009-04-21
> **andreMini9 said:**
> Thanks very much - that worked and now my updates are installed!  You're correct about hitting the esc key - tricky.  Is it possible to set the grub to something other then 0?

Absolutely!  There should be a file called menu.lst; it is usually in /boot/grub.  Somewhere in that file should be a line that reads:

timeout     0

Change the 0 to some other number of seconds (2 or 3 is usually sufficient).

Of course, you'll need to have super-user privileges to edit the file, so something like:

```
gksudo gedit /boot/grub/menu.lst
```

should do the trick.

---

### Post by sir_nasty on 2009-04-21
as was stated you can easily change that to something other than 0, I didn't suggest that to start because you would have needed the admin password to do it!:lolflag:

and just as a side note (not sure if it matters) for your mini 9 just a simple 
sudo gedit /boot/grub/menu.lst

should work, enter your password, change timeout to 2 or 3 (just like gbrainin said), save and exit.

then for added fun drop into a terminal again and type 'dmesg' and check out the list of hardware in your mini 9, and get comfy with typing ;)

---

### Post by gbrainin on 2009-04-22
> **sir_nasty said:**
> and just as a side note (not sure if it matters) for your mini 9 just a simple 
sudo gedit /boot/grub/menu.lst

I remember reading that when using a window-y program (like gedit), it is preferable to use gksudo over sudo.  Honestly, I don't recall why this is the case.

---

### Post by Hanzomon on 2009-04-23
i am having same problem with my password. However, when i press ESC is doesn't do anything?

---

### Post by gbrainin on 2009-04-24
If your timeout is set to 0 (as the mini 9's are by default), you have less than a one-second window to hit the ESC key.  The timing is, reportedly, tricky.  Keep trying, and eventually you should hit it.

---

### Post by evilcydnar on 2009-05-03
> **sir_nasty said:**
> reset it ;)

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

esc timing is critical here if grub is set to 0 seconds... might take a few tries
I have same problem but when I press Esc I get MBR 2FA: 
That's it no menu. So the instructions on this link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) can't be followed. Any other suggestions please. I'm a complete newbie to Ubuntu and need to reset password because like other guy after accepting  and installing 188 updates, my password was no longer recognized and I hadn't forgotten it as I had it wriiten down and had used it many times before downloading the 188 updates!

---

### Post by Rabnes on 2009-11-01
Hi guys

Am trying to reboot my ubuntu 8.04 on my mini dell laptop. Everytime grub is about to load, the system starts up. [grub loading flashes up for a millisecond]. How do i stop this happening? 

much appreciated

---

### Post by Rabnes on 2009-11-03
Rite guys!!

Need help with the reseting of my password like many on here.
got a dell mini9. Everytime i press escape at the boot screen i get the message MBR :2FA.
Then `grub loading` flashes up for a millisecond before ubuntu starts up. What the feck can i do? have tried downloading the startup manager so i can access the options to change the grub loading time but of course i need a password to download this. V frustrating:mad: **

help!!

Thanks!

---

