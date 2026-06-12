---
title: "Unreal Update"
date: 2008-10-05
forum: Gaming &amp; Leisure
---

### Post by Alasta on 2008-10-05
Hello everyone I have successfully installed My Unreal tournament 2004 game from the dvd. I have tried to update following the instructions Here :[http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd](http://gaming.gwos.org/doku.php/guides:32bit:ut2004dvd#unreal_tournament_2004_dvd).

and I get this Message :

cp: target `/usr/local/games/ut2004' is not a directory

---

### Post by Lovok on 2008-10-05
Did you install ut2004 in the default folder? Did you maybe change ut2004 to UT2004? 
I am not too familiar with Ubuntu yet, but all you have to do is find out where you install u2004 and put the update there.

Hope that helps.

---

### Post by AJB2K3 on 2008-10-05
What this line?
> sudo cp -r * /usr/local/games/ut2004
Just type it as is, don't alter anything.

BTW this only works on the old UT2004 not the midway one.

---

### Post by Alasta on 2008-10-05
Hi ajb thats the text thats on the guide which I copied and pasted the error it produces is :


cp: target `/usr/local/games/ut2004' is not a directory

---

### Post by Perfect Storm on 2008-10-05
Check if it's actually there.

```
ls -a /usr/local/games/ut2004
```

If it's not, you properly installed the game somewhere else.

---

### Post by Alasta on 2008-10-05
Thank you pumpkin

I think we have established the game isnt were i thought it was :)

does anyone know how to find it ? I have played the game , its working just fine , quicker than windoze I think

best regards

Alasta

---

### Post by Perfect Storm on 2008-10-05
```
locate ut2004
whereis ut2004
```

---

### Post by Alasta on 2008-10-06
Thanks for your patience :

alastair@LaburnumDesktop:~$ whereis ut2004
ut2004:

alastair@LaburnumDesktop:~$ locate ut2004
alastair@LaburnumDesktop:~$ 

does any one have a primer on using the Terminal? That seems to be my main prob

regards

Alasta

---

### Post by Perfect Storm on 2008-10-06
Try follow the guide and then post the in/output. It seems it isn't installed for some reason.

---

### Post by Alasta on 2008-10-07
well I am close to giving up on this . the game IS installed I played it for an hour last night 

BTW I have followed the instructions on the guide and this is where I got to...

Thanks for your patience

Alasta

---

### Post by ynell on 2008-10-07
If i'm understanding this right, you can't find where your ut2004 was installed.. so just do a search for ut2004.. or start the installer again, and just don't install it.. and see where it defaults to. 

I had to install mine to my /home/me/ because of osme dumb stuff that i forget now haha



I seem to be the only person ive seen so far who is having trouble with their ut2004 on linux.. i have a great gaming system but it seems choppy on linux.. its not the graphics or anything.. it seems almost like a mouse problem. it lags and jumps around and just seems weird..

---

