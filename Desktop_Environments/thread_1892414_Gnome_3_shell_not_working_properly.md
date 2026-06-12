---
title: "Gnome 3 shell not working properly"
date: 2011-12-07
forum: Desktop Environments
---

### Post by vat with tux on 2011-12-07
I have intalled gnome 3 shell on my ubuntu 11.10 system. It work working perfect but since last two days whenever i logs into gnome 3 it looks like classic gnome environment and not Gnome 3.  Same thing happens in case of unity means when i logs into unity it behaves like unity 2D. Means effects are not working properly. I'm not getting that exactly what is missing. Help me out.... thanking in advance...

---

### Post by vat with tux on 2011-12-08
bump.....

---

### Post by 23dornot23d on 2011-12-08
Its probably to do with your graphic driver ..... what graphics card do you use .... ?

---

### Post by vat with tux on 2011-12-08
I'm not having any additional graphic card. I'm having intel core 2 duo cpu.... and I as i said that before 2 days it was working perfect without any problems......

---

### Post by BC59 on 2011-12-08
If you logoff, can you logon on Unity (3d)?

---

### Post by BC59 on 2011-12-08
As I see you have problems with your Compiz which is crashing.

Try to reset Compiz:

```
gconftool-2 --recursive-unset /apps/compiz-1 && gconftool-2 --type=list --list-type=string --set /apps/compiz-1/general/screen0/options/active_plugins [core,bailer,detection,composite,opengl,compiztoolbox,decor,grid,move,resize,mousepoll,regex,snap,gnomecompat,place,imgpng,vpswitch,animation,wall,workarounds,fade,session,expo,ezoom,unityshell] && compiz --replace & disown
```

---

### Post by 23dornot23d on 2011-12-08
As my Dad always used to say to me ...... when my car stopped working ..... and it was ok
before I messed with it ......

Look at the last thing you did with it before it stopped working .... and often you will find
the cause ....

It takes 30 minutes to re-install ..... consider that ...... also try running it from a live CD .....

if it works ok from the live CD ..... then it may just be that by altering plymouth and your
boot up that somehow ...... you managed to disable the graphic acceleration needed to
run both UNITY 3D and GNOME SHELL

If you had said one works and the other does not ....... it would not lead me to believe its
a graphics driver related problem ...... but my guess is a clean install would solve your problems as you said it worked perfectly 2 days ago .....

What changed :confused: reading your previous posts ..... maybe somehow you altered something to cause this ...... I would either try retracing my steps ..... or start afresh .....

Your call though ..... 

I have seen people waste a week .... and not get sorted properly - and then re-install ... but
you will learn something along the way if you choose the path of greater enlightenment.

**Which computer do you have ?**

---

### Post by vat with tux on 2011-12-09
@23dornot23d yeah dude ... i was playing with plymouth and this happened......

---

### Post by 23dornot23d on 2011-12-09
You could try typing in 

[B]gnome-shell --replace
[/B]

in a terminal window and see what the output is .....

cut and paste it back in here ...... it may give someone a clue ...... just in case it is simple to fix.

---

### Post by vat with tux on 2011-12-11
here is the output of  **gnome-shell --replace** 


abcl@ubuntu:~$ gnome-shell --replace
gnome-shell: error while loading shared libraries: libclutter-1.0.so.0: cannot open shared object file: No such file or directory

---

### Post by lolpenguin on 2011-12-12
It doesn't have anything to do with Plymouth, that is animation while boot is happening.
It looks like your Clutter libraries aren't installed. Try reinstalling gnome-shell.

---

### Post by 23dornot23d on 2011-12-13
I agree .... that from that error .... you have things missing ..... but we have yet
to see if you have the graphics capability to run it yet ..... plymouth is not the cause
but in trying to set it up .... you may have inadvertently altered something else
that is yet to be seen ......... as Unity should run in 3D mode as it did before you
altered things. 

To install Gnome-Shell

Here is the long way of doing it ..... but it should check for dependencies and makes
sure you get the full install of gnome-shell and the advanced tweak tool too. 
*(gnome-tweak-tool alone pulls in everything .... but just to be sure - belts and braces ...... )

In a terminal do this .....

sudo apt-get update
sudo apt-get install aptitude
sudo aptitude update
sudo aptitude install gnome-tweak-tool
sudo aptitude install gnome-shell

gnome-shell --replace

and post the output again please ..... hopefully it will run ..... ;)

---

### Post by Frogs Hair on 2011-12-13
I'm not sure why libclutter is missing or not being found but it is a place to start as stated .

---

### Post by vat with tux on 2011-12-14
Thanks to all for trying hard....:) But finally I reinstalled system because many things were messed up ...:D So now every things working cool.... :D

---

### Post by 23dornot23d on 2011-12-15
Nice to hear you are up and running again .... :D 

Best of luck setting it up as you want it too .

---

### Post by jimmydean886-2 on 2011-12-15
You must've uninstalled the GNOME Shell libraries. Simple fix (so far as I know)
```
sudo apt-get install libclutter-1.0-0
```
Just for future reference

Hope this comes in handy to the wandering forums viewer with this problem!


:razz:

---

### Post by Arteymis on 2011-12-24
It might be local (only proper to the user). If so, that would necessarily that the issue is in the gnome 3 configuration files.

To verify if it's the case, run a guest session ; it's easy, lightGDM let you do that. If gnome 3 runs well in a guest session, then everything is fine your issue is only local to your user session. Otherwise, good luck my friend !

Solving bad config files is quite easy, you just have to delete them. They are hidden and probably in ./config

I have better stuff to do that looking in that, so I'll let you do so. Otherwise, if you're a lazy *** like me, just get the rid of ~/config and ~/local/share/gnome-shell, restart your session, let that big boy write back its stuff and enjoy !

EDIT : Just saw you've reinstalled your system.. lmao
By design, YOU CAN'T alter the libs and the executables as a normal user. Reinstalling the stuff is quite dumb as the chances you've messed them up is nearly 0. Most of my bad behiavior issues where related to the local config files and I believe it's the first place to look for when you're getting troubles... Anyway enjoy your day ! And also if you really want to dive into gnome 3, get Fedora ! Unity's getting anywhere :P

---

