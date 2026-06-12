---
title: "Issues w/ splash screen? want to get rid of the brown..."
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by pjones0404 on 2007-10-30
hey everybody. i have a question about the splash screen that shows after i log in but before the desktop loads. 

i have added a new gdm theme that i use when i log in. after i login it shows a brown screen for a few seconds while the desktop loads. i would like to either load a separate splash here or just have a black screen. i tried to add a splash but it still had the brown background around the image. i have added the splash manager to select diferent splashes but they all have this brown background, how can i change this?

thanks.

---

### Post by Forlong on 2007-10-30
```
sudo gedit /etc/gdm/PreSession/Default
```
look for
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi  
```
and change it to
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="x"  
      fi  
```

---

### Post by pjones0404 on 2007-10-31
thanks. that worked like a charm. 

:guitar:

---

### Post by dgrafix on 2007-11-07
THANK YOU!!!

That was driving me crazy and really didnt fit with my theme.

---

### Post by jimerickso on 2007-11-07
thanks forlong i was really bugged by that tan screen. completely ruined the theme for me. now all is well.

---

### Post by joouni on 2007-11-09
> **Forlong said:**
> ```
sudo gedit /etc/gdm/PreSession/Default
```
look for
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi  
```
and change it to
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="x"  
      fi  
```



Worked nicley.. Thx!

---

### Post by rodrigovb-cl on 2007-11-09
Por fin algo que funciona!!

Gracias,

Tranks!!

---

### Post by chimerazz on 2007-11-10
Thanks MAn i was very much fiddling with the soln for this problem
Now i have a cool color to go with
Kudos!!!

---

### Post by dweebs0r on 2007-11-19
Just wanted to add my thanks as well.  This worked perfectly for me.  Now to get rid of the brown that appears at the login screen.

-D

---

### Post by olivero1 on 2007-11-20
Thanks! Worked like a charm on all my 7.10 machines!!!

:guitar:

---

### Post by Arthur Archnix on 2007-11-22
Forlong's tip did the trick.

---

### Post by Sorivenul on 2007-11-22
I've been looking for a way to do this for a long time.  Thanks!  Worked perfectly.

---

### Post by carlos1992 on 2007-11-26
Nice trick i use to change it with startup manager but isn't like this;
is much more cooler cuz it doesn't change back xD

---

### Post by martinarg on 2007-11-27
Excelent! Thanks very much!

---

### Post by BDNiner on 2007-11-27
Nice job, works like a charm

---

### Post by apothecaryaaron on 2007-11-30
Thanks! Worked well.

---

### Post by erm27 on 2007-12-01
With this:KS I've finished my first "working" instal(sound, vid card, powermgmt, samba,& webservers) running and now to back up. . . . .:KS

---

### Post by Steve Fisher on 2007-12-14
Great! But what I *really* want to do is display a picture rather than a blank canvas.

For example... I want to design a login screen which uses the same wallpaper as my desktop. Then this screen pops up (instead of a flat colour), then my desktop loads. It would (in theory) look seamless, rather than have, in effect, 3 different screens flash before you as you login.

---

### Post by gupta_sumesh63 on 2007-12-15
Can we have some other colour instead of Brown or black. Can anyone suggest some hex values for other colours like steel Grey or violet or lemon yellow etc? Is teher also a way to have the flash screen for the complete duration before the desktop loads?(Compiz takes a long time to load and the splach screen stays only for a short time)
Thanks in advance

---

### Post by techstop on 2007-12-15
> **gupta_sumesh63 said:**
> Can we have some other colour instead of Brown or black. Can anyone suggest some hex values for other colours like steel Grey or violet or lemon yellow etc? Is teher also a way to have the flash screen for the complete duration before the desktop loads?(Compiz takes a long time to load and the splach screen stays only for a short time)
Thanks in advance

There are *plenty* of online hex colour pickers. Here is one;

[http://www.colorschemer.com/online.html](http://www.colorschemer.com/online.html)

Thanks forlong for the tip!

---

### Post by metaknecht on 2007-12-16
> **Steve Fisher said:**
> Great! But what I *really* want to do is display a picture rather than a blank canvas.

For example... I want to design a login screen which uses the same wallpaper as my desktop. Then this screen pops up (instead of a flat colour), then my desktop loads. It would (in theory) look seamless, rather than have, in effect, 3 different screens flash before you as you login.
install gnome-splashscreen-manager from synaptics

---

### Post by Prisma on 2007-12-16
Wow that fixed the problem , thank you man. I hove there could be a simple GUI option to change it instead of editing a file.

---

### Post by steve.t on 2008-03-02
Hey gupta_sumesh63,

I don't know if you tried the hex color pickers suggested by techstop, but try this:

You will notice that when you boot up, you will see the tan or orange screen before your login screen; then once you've loged in, you'll see the tan screen again before your desktop loads.  You can change the colour of the transition between boot-up and login screen by going to System -> Administration -> Login Widow -> Local (tab).  Under the themes panel you will see a "Background colour:" option.  This is for the transition colour between boot-up and the login screen.
Change that to whatever you like by clicking on the coloured box, which gives you a "Pick Background Colour" dialog. The "Colour name:" field shows the hex value of the colour you have chosen.  Mine is a dark green, "#023500".
Take note of that colour code, and then in the file in Forlong's tip, put that colour code in instead of "x" to replace the tan colour. And voila, you are starting to get some consistency across your theme.

Hope this helps you and some others looking for the answer.
Cheers,
Steve

---

### Post by trig on 2008-03-04
> **dweebs0r said:**
> Just wanted to add my thanks as well.  This worked perfectly for me.  Now to get rid of the brown that appears at the login screen.

-D

you can change that in the system, admin, login window, look at pic attached.

---

### Post by cosmin1086 on 2008-03-11
Is there any way to have a themed login that uses the wallpaper directly after login instead of a colour?

---

### Post by Dragoth82 on 2008-03-13
i was just wondering about this issue this morning.  thanks for the fix!

---

### Post by Herrakles on 2008-03-14
Anyone know how to show the splash longer in gusty gnome?

Cause i see the splash a few seconds and 
after that i see a longer time the blackscreen.

Is there any way to hide the splash after the desktop
is shown?

---

### Post by fredbird67 on 2008-03-21
Forlong, thanx for posting that -- you sir, are a genius.  I've changed my login background color from that sand color, which doesn't go very well with a theme that's something like blue or green, to solid black, which looks much better, no matter what wallpaper or theme I happen to have on my desktop.

Fred in St. Louis

---

### Post by misterhead on 2008-03-28
As everyone else has stated..."Works Perfectly. Thank You"

---

### Post by clanky on 2008-03-30
As everyone else has said, thankyou very much, that is so much nicer now.

Could the OP or a mod possibly mark this as solved?

---

### Post by Stroisblaeter on 2008-03-30
:) It's been a while... nevertheless; Thanks!

---

### Post by AlistairH on 2008-03-30
> **Steve Fisher said:**
> Great! But what I *really* want to do is display a picture rather than a blank canvas.

For example... I want to design a login screen which uses the same wallpaper as my desktop. Then this screen pops up (instead of a flat colour), then my desktop loads. It would (in theory) look seamless, rather than have, in effect, 3 different screens flash before you as you login.

Here's my solution as first detailed in the thread [http://ubuntuforums.org/showthread.php?t=739731](http://ubuntuforums.org/showthread.php?t=739731)

Do what I did... rename the /etc/gdm/PreSession/Default file to /etc/gdm/PreSession/Default.sample for example. The original file won't be found and the instructions it contains won't be applied.

If your gdm background is the same as your desktop background you'll go straight to your desktop in a beautifully smooth transition.

---

### Post by Lantesh on 2008-03-31
Like the others said THANKS FORLONG!!!!!!!!!!!!!!!!!!!!!

---

### Post by misterhead on 2008-04-01
> **AlistairH said:**
> Here's my solution as first detailed in the thread [http://ubuntuforums.org/showthread.php?t=739731](http://ubuntuforums.org/showthread.php?t=739731)

Do what I did... rename the /etc/gdm/PreSession/Default file to /etc/gdm/PreSession/Default.sample for example. The original file won't be found and the instructions it contains won't be applied.

If your gdm background is the same as your desktop background you'll go straight to your desktop in a beautifully smooth transition.

I just tried that, but believe it or not, it it took longer to display my wallpaper than before. Since I already followed previous instructions on changing that default color to black, it's actually a smoother transition leaving the PreSession/Default file as is. (at least on my machine) Not discrediting your advice, by any means, just commenting on how it worked with my setup.
I did figure out that if I take a GDM theme I like, Copy the background jpg or png, I can not only make it my wallpaper but also Make it into a Usplash them with TheeMann's Usplash Maker, so all 3 are identical. Looks pretty sweet.

---

### Post by AlistairH on 2008-04-02
> **misterhead said:**
> I just tried that, but believe it or not, it it took longer to display my wallpaper than before. Since I already followed previous instructions on changing that default color to black, it's actually a smoother transition leaving the PreSession/Default file as is. (at least on my machine) Not discrediting your advice, by any means, just commenting on how it worked with my setup.
I did figure out that if I take a GDM theme I like, Copy the background jpg or png, I can not only make it my wallpaper but also Make it into a Usplash them with TheeMann's Usplash Maker, so all 3 are identical. Looks pretty sweet.

Funny you should say that....

My wallpaper is the same as the background I use for the logon screen, but I have noticed the time taken from logon to my full desktop appearing varies from day to day. The wallpaper remains on screen all the time, so it's only the panels I'm waiting on as it were. However, after my last post, I changed things in that I made a backup of the original default file then I erased the contents of the original. So the default file is still there, it simple doesn't contain any code.

This 'seemed' to speed things up a bit, though I haven't sat down and timed it so it may very well be a perception thing.

Still, good to hear you found another solution, one which I shall investigate this weekend.

---

### Post by New2Linux0319 on 2008-04-02
> **Forlong said:**
> ```
sudo gedit /etc/gdm/PreSession/Default
```
look for
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="#dab082"  
      fi  
```
and change it to
```
# Default value  
      if [ "x$BACKCOLOR" = "x" ]; then  
              BACKCOLOR="x"  
      fi  
```


QUESTION:
so changing from backcolor ="#dab082"    to   "x"     

#dab082  is tan background?
x               is blank (black)  or 
x               is the new background (whatever you choose it to be)?

i tried to put in a splash screen using splash screen manager but its not working as hoped.

the login screen is plain tan ---(  i would like to change this to something else that i downloaded -  example: tan background but with penguin sitting next to the block where i sign in )

then after i login it goes to a tan screen and then flashes just for a second my picture from the splash screen manager and then instantly to the regular desktop.  so as it is now,  the splash screen only just appears for a seocnd -  is this how it is supposed to be?

perhaps i have my screens mixed up?
i 'd like the play with different  login screens  and also page loading screens


desktop computer, pentium4 2.6, nvidia7300GT, 2G ram, Ubuntu 7:10
thanks

---

### Post by zir0n on 2008-04-29
Hi all, i think they fixed this with Hardy 8.04. If you change the color in login window configuration window it changes all of the color of the screen before and after the login pops up.

---

### Post by erginemr on 2008-04-30
Good to hear that! 

I think the dev's have also fixed the issue regarding the usplash having too high a resolution setting, which gave quite a few laptop users "out of range" errors at boot.

---

