---
title: "Can't switch user, log off, restart, or shut down PC"
date: 2009-05-02
forum: General Help
---

### Post by Mister LinOx on 2009-05-02
Okay. I don't really like hard booting my computer all the time, so instead, I shut it down/log off/restart all from the user switcher panel app or one of the others. The problem is when I do any of these, I just get a dark purple/black screen, and the PC doesn't really turn off. If I log off, I know it takes me to the login screen, because if I type another user name and their password, I hear the successful login sound, but the visual part is not working. So I am thinking it might have to do with my video card. I don't know what the problem would be with shutting down or restarting. 

I use Ubuntu 9.04(but I'm pretty sure it happened in 8.10,also) and my video card is an Intel 82845G graphics controller. I believe it is integrated, also. 

So, if you do know what I can do to fix it, please help. Thank you in advanced. :D

---

### Post by cariboo on 2009-05-02
What happens when you open an Applications-->Accessoreis-->Terminal and type:

```
sudo shutdown -h now
```

to shut down or:

```
sudo shutdown -r now
```

to restart?

---

### Post by Mister LinOx on 2009-05-02
> **cariboo907 said:**
> What happens when you open an Applications-->Accessoreis-->Terminal and type:

```
sudo shutdown -h now
```

to shut down or:

```
sudo shutdown -r now
```

to restart?

The same thing happens. Oh, and sorry for the belated response. I was at a wake.

---

### Post by Mister LinOx on 2009-05-03
Oh, and if I select another user to switch to, it does it then, which is really annoying as I usually have to switch users when others use the PC.

---

### Post by Mister LinOx on 2009-05-06
Well, I hate doing this, but I guess I'm going to bump as I can't seem to find anyone with a similar problem.

---

### Post by cholericfun on 2009-05-06
i've seen some very strange login/shutdown behaviour, including everything working fine after a reinstall.

maybe if the graphics arent working maybe try ctrl-alt-F3 to drop to a simple command line without graphics and go through the login, sudo shutdown...

see if it works at least

---

### Post by Mister LinOx on 2009-05-06
> **cholericfun said:**
> i've seen some very strange login/shutdown behaviour, including everything working fine after a reinstall.

maybe if the graphics arent working maybe try ctrl-alt-F3 to drop to a simple command line without graphics and go through the login, sudo shutdown...

see if it works at least

When I logged off, the dark screen came up. When I entered Ctrl-alt-F3, a full screen terminal came up. I entered my username and password since it said to login. Once that happened, well, I didn't know how to get out of the terminal. So I rebooted.

---

### Post by cholericfun on 2009-05-07
did you reboot by using ```
sudo shutdown -r now
``` ?

because that was the point of the excercise... ;)

other than that you can go back to your desktop on ctr-alt-F7


this ctr-alt-F3 thing wasnt meant as a fix but a quick solution...

---

### Post by Mister LinOx on 2009-05-07
> **cholericfun said:**
> did you reboot by using ```
sudo shutdown -r now
``` ?

because that was the point of the excercise... ;)

other than that you can go back to your desktop on ctr-alt-F7


this ctr-alt-F3 thing wasnt meant as a fix but a quick solution...

Yes.

---

### Post by cholericfun on 2009-05-07
OK,

great

i've seen some useless and strange behaviour of the log off/shutdown right after installing a fresh system (e.g. not beeing able to just click "shutdown).
i ended up installing again, from the SAME CD and everything was fine (including beeing able to click "shutdown")

so maybe theres some way to reinstall/fix the whole login/shutdown procedure although i have no idea even what to search for...
good luck!

---

### Post by Mister LinOx on 2009-05-07
> **cholericfun said:**
> OK,

great

i've seen some useless and strange behaviour of the log off/shutdown right after installing a fresh system (e.g. not beeing able to just click "shutdown).
i ended up installing again, from the SAME CD and everything was fine (including beeing able to click "shutdown")

so maybe theres some way to reinstall/fix the whole login/shutdown procedure although i have no idea even what to search for...
good luck!

Thank you. If I end up HAVING to do a reinstall, I have a /home partition holding most of my information. Also, if I do HAVE to, that would give me the chance to try out the EXT4 system on my / partition. So I don't know. I'm still going to try to search for some fixes. If you find one, let me know. =D

---

### Post by cholericfun on 2009-05-10
hi,
this is unlikely to work since you had problems shutting down from command line

but try this anyway...

right click on the desktop
create new launcher

type command:
```
gksudo shutdown -hP now
```

for a shutdown button

also check out this thread...
[http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999)

---

