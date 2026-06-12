---
title: "edgy crash after login"
date: 2006-11-07
forum: Desktop Environments
---

### Post by xor.be on 2006-11-07
Hi all,

I have a weird issue.
I installed kde together with gnome, installed some customer themes and splash screens and so on.
Everything works fine,rebooted multiple times.

But then i tried to install kismet (that is the only relevant thing i can think of), then on the next reboot things go wrong.

After i log in,my screen goes weird (same i had when logging of before,but that was no problem), then it loads for like 5 seconds,and comes back to the login screen.

i switched between gdm and kdm,i get the appropriate custom login screen,but after that same problem.

I can only boot to the recovery desktop,and even there things like firefox don't open.

my guess is there is a problem with what happens when he boots (not with the custom splash screen,since they are different).

could somebody tell me how i can see/edit what loads upon desktop loading,maybe i'll see smth suspicous.

Thank you :)

---

### Post by taurus on 2006-11-07
Maybe there is a problem with permissions to your $HOME!  Boot into recovery mode and at the prompt, have a look at your $HOME/.dmrc!

```
ls -la /home/john/.dmrc
(assuming **john** is your username!!!)
```
User john should own .dmrc and the permissions should be either 

-rw------- john john .dmrc
-or-
-rw-r--r-- john john .dmrc

---

### Post by xor.be on 2006-11-07
Hi taurus

thx for ur swift reply,but everything in order there
-rw--... 1 xor xor 

i really think installing kismet etc did smth to the startup.
but i don't know where to look

also,i don't remember if i saw this before the problem or not,but i get a number of things like this in dmesg while under recovery =

[17181497.672000] SoftMAC : Authentication response receive fromed 00:12:bf:13:9a:81

this mac address doesn't correspond to anything i have, and i didn't install any spoofing programs (well,maybe some COULD,but it shouldn't spam this at boot)

thx again

---

### Post by taurus on 2006-11-07
What if you remove kismet with aptitude and see if that's the problem!

```
aptitude remove kismet
```
Also, look at the permissions of your account...

```
ls -la /home/xor
```

---

### Post by jhaquo on 2006-11-07
xor also has a Cannot read table of mounted file systems error when typing "df" too, dunno if it is related tough

---

### Post by xor.be on 2006-11-07
allright,i fixed that now :)
it seems there was idd some prob with mounting the drive

however, to make some room i uninstalled kde
put it back to gdm

but for some reason it starts the login screen with "kubuntu on .. "
and,for some other reason i can't open the login window manager,under administration.

is there a command that i can force a login windows /theme ? :)

thx

---

### Post by Erbium on 2006-12-01
I had the same problem.  After I would enter my login user name and password, edgy would crash, and put me back onto the log in screen.  I had to restart and go to the safe mode(command line).  I logged in and deleted some files I didn't need(had filled my hard drive up previously and assumed that this was the problems).  Then I restarted and logged in normally, and it worked fine.

---

