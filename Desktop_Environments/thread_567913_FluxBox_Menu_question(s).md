---
title: "FluxBox Menu question(s)"
date: 2007-10-05
forum: Desktop Environments
---

### Post by ghandi69_ on 2007-10-05
Hey guys, been running with fluxbox for about a month now, and I'm not sure if I'll ever go back!

Anyway, I was trying to add a new program to the menu, and with most programs... my menu entry always looked like this...

[exec] (xmms) {usr/bin/xmms} <>

and some jazz like that. I only learned that because that is what the menu looked like before I started messing with it, and up until now, that worked for everything.

However, I just installed the game Astromenace ( I love it!!).  But as of now, the only way i can play it, is to move to /usr/share/astromenace/ and then type ./Astromenace

having to do the ./ is giving me troubles I think, because I first tried...

[exec] (Astromenace) {usr/share/astromenace/Astromenace} <>

and that didn't work so I tried..

[exec] (Astromenace) {usr/share/astromenace/./Astromenace} <>, and that didn't work either.

My other question regards to the use of the gdm.  I have the server edition installed, and I usually just start up that way, login, and then say 'startx' to get in.  I dont have a problem with this, however, I have heard that using gdm instead and help save a lot of headaches, is this true?

---

### Post by RedSquirrel on 2007-10-05
> **ghandi69_ said:**
> Hey guys, been running with fluxbox for about a month now, and I'm not sure if I'll ever go back!

Anyway, I was trying to add a new program to the menu, and with most programs... my menu entry always looked like this...

[exec] (xmms) {usr/bin/xmms} <>

and some jazz like that. I only learned that because that is what the menu looked like before I started messing with it, and up until now, that worked for everything.

However, I just installed the game Astromenace ( I love it!!).  But as of now, the only way i can play it, is to move to /usr/share/astromenace/ and then type ./Astromenace

having to do the ./ is giving me troubles I think, because I first tried...

[exec] (Astromenace) {usr/share/astromenace/Astromenace} <>

and that didn't work so I tried..

[exec] (Astromenace) {usr/share/astromenace/./Astromenace} <>, and that didn't work either.

The path should begin with root, that is /, so the path is /usr/share/astromenace/Astromenace.

```
 [exec] (Astromenace) {/usr/share/astromenace/Astromenace} <>

```On the command line, you should be able to run it the same way, just by running /usr/share/astromenace/Astromenace. You could also create an alias for the command in your ~/.bashrc or ~/.bash_aliases:

```
alias astromenace='/usr/share/astromenace/Astromenace'
```That game looks pretty cool, but I see it requires a 1 GHz CPU. I might give it a shot anyway. 


> **ghandi69_ said:**
> My other question regards to the use of the gdm.  I have the server edition installed, and I usually just start up that way, login, and then say 'startx' to get in.  I dont have a problem with this, however, I have heard that using gdm instead and help save a lot of headaches, is this true?

In some ways, yes. When you use gdm, your computer will finish booting with a nice login screen and all you have to do is login and it will run your default window manager or desktop environment. The other advantage is that it will have everything setup for you automatically. Let's say for instance you have Fluxbox installed, but you want to try out IceWM. Well, all you have to do is install icewm and it will appear in your sessions list at the gdm login screen. When you use startx, you might have to do some work yourself to set things up. There are defaults that the system sets up and you can use scripts to make things easier, but when you use gdm, it handles all of that for you so that you don't have to put any thought into it.

gdm doesn't consume much in terms of system resources either. 

Oh, and you get to theme the login screen! I was using the Tropic theme for a while. It's in the repositories. 

I have used gdm quite a bit in the past, but these days I prefer to login on the console. It's really about personal preferences.

---

### Post by mojoman on 2007-10-05
You could try out slim login manager as well. I use on my Debian partition and it's quite good. It's in the Gutsy repositories and is available as .deb-file as well. It does the job though if you use several WM it has some limitations (but as you seem to have gotten bitten by flux that might not be a problem :wink: )

If you just want to not have to write startx every time you log in you could just add a short start-up script in your .bashrc-file. Basically does the same job as slim does but without the graphics.

/mojoman

---

### Post by ghandi69_ on 2007-10-05
Oh No!!

I installed gdm, and now nothing works!!..

Ok it works, but it just starts fluxbox, not through "startfluxbox" command, so none of my startup programs work, my text and theme has all been changed, and everything just looks real ugly now.

I'm looking into why this happened, but in the mean time, feel free to point me in the wrong direction.

---

### Post by yabbadabbadont on 2007-10-05
Edit /usr/share/xsessions/fluxbox.desktop and make sure that the Exec line is starting startfluxbox and not just fluxbox.

---

### Post by yabbadabbadont on 2007-10-05
As an example, here is the contents of the one I saved a while back:
```
/backup/Various/config $ cat fluxbox.desktop 
[Desktop Entry]
Encoding=UTF-8
Name=Fluxbox
Comment=Highly configurable and low resource X11 Window manager
Exec=/usr/bin/startfluxbox
Terminal=False
TryExec=/usr/bin/startfluxbox
Type=Application

[Window Manager]
SessionManaged=true

```

---

### Post by ghandi69_ on 2007-10-06
My file looks exactly like yours, and more importanlty, it has the startfluxbox already in there.  So that is not the issue.

Where does gdm look when it decides to start a window manager?

---

### Post by kerry_s on 2007-10-06
> **ghandi69_ said:**
> My file looks exactly like yours, and more importanlty, it has the startfluxbox already in there.  So that is not the issue.

Where does gdm look when it decides to start a window manager?

did you select fluxbox in the gdm session menu before you logged in.

---

### Post by ghandi69_ on 2007-10-06
That worked, all I had to do was tell it to pick fluxbox in the gdm screen.

However, I'm trying to change the gdm theme.. it can't find the "human" one it keeps trying to reference, so I downloaded another theme, and moved it to the /usr/share/gdm/themes/

directory, and modified the /etc/X11/gdm.gdm.conf file to reference to the new theme, but I cannot seem to stop it from referencing the human theme.

Any ideas?

---

### Post by ghandi69_ on 2007-10-06
> **RedSquirrel said:**
> The path should begin with root, that is /, so the path is /usr/share/astromenace/Astromenace.

```
 [exec] (Astromenace) {/usr/share/astromenace/Astromenace} <>

```On the command line, you should be able to run it the same way, just by running /usr/share/astromenace/Astromenace. You could also create an alias for the command in your ~/.bashrc or ~/.bash_aliases:

```
alias astromenace='/usr/share/astromenace/Astromenace'
```That game looks pretty cool, but I see it requires a 1 GHz CPU. I might give it a shot anyway. 




In some ways, yes. When you use gdm, your computer will finish booting with a nice login screen and all you have to do is login and it will run your default window manager or desktop environment. The other advantage is that it will have everything setup for you automatically. Let's say for instance you have Fluxbox installed, but you want to try out IceWM. Well, all you have to do is install icewm and it will appear in your sessions list at the gdm login screen. When you use startx, you might have to do some work yourself to set things up. There are defaults that the system sets up and you can use scripts to make things easier, but when you use gdm, it handles all of that for you so that you don't have to put any thought into it.

gdm doesn't consume much in terms of system resources either. 

Oh, and you get to theme the login screen! I was using the Tropic theme for a while. It's in the repositories. 

I have used gdm quite a bit in the past, but these days I prefer to login on the console. It's really about personal preferences.

My bad, I had a typeo in my original post... I indeed already had the path to work like /usr/share/astromenace, like it should be, but it still doesn't work.

I think it has something to do that even when i'm in that directory, I have to type ./Astromenace instead of just Astromenace in order to get it to run.

---

### Post by RedSquirrel on 2007-10-06
> **ghandi69_ said:**
> My bad, I had a typeo in my original post... I indeed already had the path to work like /usr/share/astromenace, like it should be, but it still doesn't work.

Maybe this would work:

```
[exec] (Astromenace) {cd /usr/share/astromenace && Astromenace} <>
```

---

### Post by RedSquirrel on 2007-10-06
> **ghandi69_ said:**
> ... I'm trying to change the gdm theme.. it can't find the "human" one it keeps trying to reference, so I downloaded another theme, and moved it to the /usr/share/gdm/themes/

directory, and modified the /etc/X11/gdm.gdm.conf file to reference to the new theme, but I cannot seem to stop it from referencing the human theme.

Any ideas?

You can use gdmsetup to browse to the location of the gdm theme (tarball) and then you just click **Install**. I'm not running gdm right now so I can't give you really precise instructions nor a screenshot. 

You don't even have to extract the tarball. You just run gdmsetup, install the theme, select the theme, and you're done. By the way, you don't even have to use a theme if you don't want to. You'll see what I mean when you run gdmsetup...

```
gksudo gdmsetup
```

---

