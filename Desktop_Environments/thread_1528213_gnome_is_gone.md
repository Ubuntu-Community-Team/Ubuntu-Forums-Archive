---
title: "gnome is gone"
date: 2010-07-10
forum: Desktop Environments
---

### Post by kroiz on 2010-07-10
when I login to my user I get this screen:

[ATTACH]162990[/ATTACH]
[IMG]http://yfrog.com/1q19052010sj[/IMG]

not sure you can see it in the picture (which I took using a external camera, of course ,cause I cannot screenshots) but the white rectangle has actually a bash prompt but it is not really a window just a white rectangle that cannot be moved.

the mouse is working but I have nothing to click cause gnome is not there.

I am still able to login to other account like the kids's account and they work fine.

not sure what could have caused that....

---

### Post by bobcollard on 2010-07-10
> **kroiz said:**
> when I login to my user I get this screen:

[ATTACH]162990[/ATTACH]
[IMG]http://yfrog.com/1q19052010sj[/IMG]

not sure you can see it in the picture (which I took using a external camera, of course ,cause I cannot screenshots) but the white rectangle has actually a bash prompt but it is not really a window just a white rectangle that cannot be moved.

the mouse is working but I have nothing to click cause gnome is not there.

I am still able to login to other account like the kids's account and they work fine.

not sure what could have caused that....
try this command:
```
sudo startx
```

---

### Post by kroiz on 2010-07-11
I wrote what I did and the out put cause I cannot copy paste
> 
sudo startx
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again

please consult The X.Org Foundation support
    at [http://wiki.x.org](http://wiki.x.org)
for help.
ddSigGiveUp: Closing log


so then I tried
deleting that file but I got a similar error that the server is still running and a socket cannot be opened to it.

is there a way to somehow reset the X configurations or maybe create a new user and copy the home directory and stuff?

---

### Post by exodus_ on 2010-07-11
Well, when you click on your user name can you look at the bottom of your screen for "Session" and next to it it might say failsafe.

You need to click the drop down box and then make sure that Gnome is selected

What you are logging into now as an Xorg failsafe.  Basically it has nothing but Xorg and a terminal running.  The above should fix this for you

---

### Post by kroiz on 2010-07-11
> **exodus_ said:**
> Well, when you click on your user name can you look at the bottom of your screen for "Session" and next to it it might say failsafe.

You need to click the drop down box and then make sure that Gnome is selected

What you are logging into now as an Xorg failsafe.  Basically it has nothing but Xorg and a terminal running.  The above should fix this for you


UN-BE-LIEV-ABLE
A million thanks exodus_! :D
for the record it was saying "xterm" and not failsafe. 

yeepee I am so happy!

---

### Post by exodus_ on 2010-07-11
So glad it helped!  just so you know though, you can have any number of desktop environments and window managers installed and select which one to use when you log in this way.

It's really neat! You may want to check it out.  Just look around for window managers or desktop environments online.

---

### Post by kroiz on 2010-07-11
I guess that what happens when you create a user account on your computer for your kids....

---

### Post by exodus_ on 2010-07-11
> **kroiz said:**
> I guess that what happens when you create a user account on your computer for your kids....

No,

Generally you need to specify what session you want to use when you log in.  It will remember what you used last time, so that's why you were stuck going to xterm.

---

### Post by ov3rcl0ck on 2010-07-11
The new GDM allows you to boot a default WM for each user, so your kids accounts are probably set to a default Session of Gnome, whereas you are set to boot into xterm(that lil white square).

When you are about to type in your password look on the bottom and make sure the "Session" is set to Gnome.

---

### Post by kroiz on 2010-07-12
1. anyone (including randomly clicking users) has access to the user selection screen.
2.almost nobody notices those settings in the bottom of the screen. the user does not spend time there - only the miliseconds it takes him/her enter the password.
3. the other problem is that it persist to future sessions.

I think It is not a good design.

---

