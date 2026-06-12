---
title: "Cedega has a 14 day trial"
date: 2005-12-19
forum: Gaming &amp; Leisure
---

### Post by GQed76 on 2005-12-19
but i dont know how to install it.  I have the file...its a shell installer..any one know how?

---

### Post by newuser111 on 2005-12-19
just type ./filename in console

or if its a .deb file sudo dpkg -i filename

---

### Post by GQed76 on 2005-12-19
gqed76@gqubuntu:~/Desktop$ ./cedega_timedemo_installer
bash: ./cedega_timedemo_installer: Permission denied

---

### Post by Sutekh on 2005-12-19
How about

```
chmod +x ./cedega_timedemo_installer
sh ./cedega_timedemo_installer
```

---

### Post by GQed76 on 2005-12-19
thanks! that worked like a champ

---

### Post by Des33 on 2005-12-19
isnt the timedemo finished? sometime in november it ended did it not?

---

### Post by GQed76 on 2005-12-19
no its 14 days from the time you download it.

and by the way, anyone ever use it.. I have NO idea where i isnatlled my game too..cant find it anywhere in the filesystem

---

### Post by patrick295767 on 2005-12-19
[QUOTE=GQed76]no its 14 days from the time you download it.

and by the way, anyone ever use it.. I have NO idea where i isnatlled my game too..cant find it anywhere in the filesystem[/QUOTE]
  
```
xterm
rox
(if u have rox-filer  or use nautilus)
show hidden files
then 
have  a look in :
.transgaming/c_drive/program files
```
(+ or -)
  
Enjoy gaming under Linux !
& also, dont hesitate to let us know the programs workign and also not workign !!
  
Kind regards, 

Pat'

---

### Post by patrick295767 on 2005-12-19
(/home/user_name/.transgaming ... )

---

### Post by GQed76 on 2005-12-19
Thanks Patrick, Ill look there when I get home.

Im still very new to Ubuntu and Linux :)

---

### Post by Jaygo333 on 2006-02-10
Hey, Just one question. How Do I now Unistall It?
?sh Unistall?

:h34r: Jaygo333 :h34r:

---

### Post by RonJohnson on 2006-02-11
That's my question too. I installed the TimeDemo and IMO for them wanting a monthly subscription it better be flawless and its far from that. I get better results with wine and those results leave a lot to be desired. So how do we uninstall?

---

### Post by handy on 2006-02-11
[QUOTE=Sutekh]How about

```
chmod +x ./cedega_timedemo_installer
sh ./cedega_timedemo_installer
```[/QUOTE]

Ahh  Sutekh...

You love those permissions...:KS

---

### Post by handy on 2006-02-11
[QUOTE=RonJohnson]That's my question too. I installed the TimeDemo and IMO for them wanting a monthly subscription it better be flawless and its far from that. I get better results with wine and those results leave a lot to be desired. So how do we uninstall?[/QUOTE]

Cedega, won't work perfectly with many games.  It will work & be very playable with some games.  Some have the experience of a game playing better under cedega than under windoze!

I have got Guild Wars to function really well...  I have no need to ever boot to windoze to play GW...:KS 

Quite a lot of detail in the following thread:

[http://ubuntuforums.org/showthread.php?t=123715](http://ubuntuforums.org/showthread.php?t=123715)

Re; the subscription:  You can quit after 3 months I believe.  So, if you have got the games that you want running on the various versions available, (which are really easy to install & manage with the Point2Play GUI front end), you can get out of it for $15- US.

I thought that was good value - now that I don't have to boot to windoze to play GW!  :KS

---

### Post by RonJohnson on 2006-02-11
Maybe I was a little harsh on Cedega, but now it's really not an issue as I was able to get wine to work with the only game I actively care about playing. I may start to pull some others out just to see what I can get going on with wine. But for now I'm happy with the setup I'm running.

---

### Post by Sutekh on 2006-02-11
[QUOTE=handy]Ahh  Sutekh...

You love those permissions...:KS[/QUOTE]

Haha that I do!  I like to stick to what I know!

I used some **chmod +s**'s the other day too! ;)

---

