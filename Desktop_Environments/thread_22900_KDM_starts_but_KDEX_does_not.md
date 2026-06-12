---
title: "KDM starts but KDE/X does not"
date: 2005-03-30
forum: Desktop Environments
---

### Post by Kinema on 2005-03-30
I just installed Kubuntu via a 'server' install from a Kubuntu CD from 2005/03/25 then did an 'apt-get upgrade' against the Ubuntu proper and Universe archives and finally did an 'apt-get install kubuntu-desktop kubuntu-default-settings'.

Now when I start my box I get a Kubuntu themed KDM but when I try to log-in the screen blanks for five or so seconds and I'm returned to KDM.

Any thoughts?

--adam

---

### Post by apokryphos on 2005-03-30
It is unlikely, but you might have been upgrading just when they were making changes, and might have got broken packages. Try doing:
sudo apt-get dist-upgrade

p.s. You needn't do apt-get install kubuntu-desktop *and* kubuntu-default-settings -- the former pulls in the latter.

---

### Post by odrop on 2005-03-30
To help your problem a bit more, if updating didnt help.  Get out of KDM, so you're in a normal terminal login, log in, then try starting KDE from the command line (startx or startkde should do the trick.)

Always remember your /var/log too for help with figuring out these problems, though not every error is usually logged there.

---

### Post by Kinema on 2005-03-30
I took a closer look at my logs today (being sober helps) and the only errors I can find are:

```
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
``` 

I'm working on an upgrade but it's going to take a few hours as I'm connected via dial-up :mad:.

--adam

---

### Post by alexs99 on 2005-04-27
Hi,

I installed kubuntu yesterday for the first time.
The install process seemed to work correct, but now I'm getting this error too:

[QUOTE=Kinema]Now when I start my box I get a Kubuntu themed KDM but when I try to log-in the screen blanks for five or so seconds and I'm returned to KDM.
[/QUOTE]

I was not able to log in to kde. It's not possible to log in to console too. After I select this option my box tries to statr console but gets interrupted by sth. like 'stop kdm' followed by 'start kdm'. This brings me back to the login screen everytime.

I believe that this problem has sth. to do with graphics drivers because on the first try the login screen is not rendered correct. The displayed box is way smaller then my screen. Text is not rendered correct. After the first 'stop kdm' 'start kdm' cycle this problem is fixed and the login screen gets rendered correctly.

I'm using an nforce2 board and a nvidia ti4200 graphics card.

Could anybody please help me out, 'cause I really want to try my new kubuntu installation.  :neutral:

Greets,
Alex

P.S.: First post on this board, seems to be a great community here...  :razz:

---

### Post by Disorder2 on 2005-04-27
Oops. Didn't see this post.
I had the same problem and the answer (well, the answer for me) is here:

[http://www.ubuntuforums.org/showthread.php?t=30093](http://www.ubuntuforums.org/showthread.php?t=30093)

---

### Post by alexs99 on 2005-04-27
@Disorder2: Thx for the link, I didn't see your post when searching the forum. I think I'll give it a try as soon as I get back to my box. I'll update this thread then.

---

### Post by alexs99 on 2005-04-29
Just for the record: As I had trouble starting a shell because of the described problems I decided to start from scratch.

I did a new clean install from cd and my problems are gone.  :razz:

Thx for the help...
Regards,
Alex

---

