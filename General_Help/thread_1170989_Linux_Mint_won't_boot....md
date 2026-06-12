---
title: "Linux Mint won't boot..."
date: 2009-05-26
forum: General Help
---

### Post by cjmabry25 on 2009-05-26
Hi guys. Thanks for the support you guys have given me so far in the past.

Anyways, I installed Linux Mint, and then installed the ATI drivers from the ATI website (Catalyst Control Center). I restarted my computer, it booted fine, and then I went to play a game. I was playing fullscreen, and all of a sudden my game minimizes to a window and I cant move the mouse or do anything, (I've heard this was something to do with the screensaver) so I had to hold the power button to turn off. Now Mint won't start. It goes through the loading screen and then goes to a black screen with some weird colors at the top.

I'll post specs, but couldn't find the terminal command I needed to get my PC's Specs, so here they are off of the top of my head -

AMD Athlon 3200+
Ati Radeon x1300
512mb RAM

I'm relatively new to Linux. I've tried Ubuntu and then Mint but always wound up with a problem and had to resort back to windows.

Thanks

---

### Post by cjmabry25 on 2009-05-26
Does anyone know what I could do? Linux Mint is almost identical to Ubuntu so any commands I could do in the terminal of the recovery console that would work in Ubuntu should work here.

Thanks

---

### Post by pbpersson on 2009-05-26
First of all, tell us about this black screen with the weird colors on top.  Is this a console screen or what?

There is a command you can type at the command console to reconfigure your XServer, it will basically start you over again with the Open Source video driver.

The command is:  dpkg-reconfigure xserver-xorg

This assumes that you are in recovery mode with root access.

---

### Post by cjmabry25 on 2009-05-26
Thanks for the reply.

The black screen is not a console, it's just where the login screen should be.

As for getting into a console to type that, I'm lost. Can I do it from the live CD? Because I tried accessing the recovery console, but it said I needed a root password. I typed in my password and nothing. 

Thanks

---

### Post by pbpersson on 2009-05-26
If you mean can you enter those commands from a console in the Live CD, no - because you are in the Live CD session.

If you are asking "is there a way to enter the recovery console using a menu choice on the Live CD" then I have no idea.

---

### Post by cjmabry25 on 2009-05-26
Well I just need to know how to enter the Console and get in... I can get into recovery where it lists run root console, xfix, etc. but when I go to root console and type in my password it says password incorrect.

---

### Post by pbpersson on 2009-05-26
I just booted into recovery mode in Jaunty.  There were several choices - root mode with networking, root mode without networking, xfix which was to fix XServer problems.

I did root mode without networking and it never did ask for a password

---

### Post by cjmabry25 on 2009-05-26
Hmmm... I think it's just a mint problem with the password...

Anyways thanks

---

### Post by blacklocist on 2009-05-27
Here is something to try, when you boot up and get the weird colors usually X server is hung or something weird. Thanks ATI :)

Try Ctrl+Shift+F2 to get into another terminal. There you should be able to log in. Something to keep in mind that bailed me out while trying to get my ATI drivers working correctly.

---

### Post by brntoki on 2009-05-27
Additionally, you may consider typing your user-name and password as you normally would if the login screen had appeared correctly.  It may just be the screen is messed up, but you are able to login anyway.  From there, however, you'd have to know what else to do, i.e. start the console from key commands, etc.  Alt+F2 would give you the ability to type whatever command is necessary to get where you needed to be, but I can't remember a lot of that stuff.  I'd guess that Ctrl+Shift+F2 would do it?

---

