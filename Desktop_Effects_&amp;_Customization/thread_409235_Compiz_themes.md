---
title: "Compiz themes"
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by Deviltongue on 2007-04-14
how do I install themes for compiz?

---

### Post by derrekito on 2007-04-21
> **Deviltongue said:**
> how do I install themes for compiz?


Bump, I'm trying to figure this out as well.

---

### Post by Happy_Man on 2007-04-21
Yeah, me too.

---

### Post by derrekito on 2007-04-21
> **Happy_Man said:**
> Yeah, me too.

Most of the pages I come to are broken links.  Also someone on the compiz forums suggested using emerald with compiz, however I cannot seem to be able to get that work either.

---

### Post by steveneddy on 2007-04-22
Anyone try using....um....Beryl?

---

### Post by Happy_Man on 2007-04-22
Beryl no work for me... plus I like Compiz settings. Beryl default sucks.

---

### Post by derrekito on 2007-04-22
> **steveneddy said:**
> Anyone try using....um....Beryl?

Beryl doesn't work for me either.  I get a nasty error.
```

** (beryl-manager:3043): CRITICAL **: can't execute beryl-xgl: Success

``` 


I posted this issue, but no replies yet. [http://ubuntuforums.org/showthread.php?t=416975](http://ubuntuforums.org/showthread.php?t=416975)

---

### Post by steveneddy on 2007-04-22
> **Happy_Man said:**
> Beryl no work for me... plus I like Compiz settings. Beryl default sucks.

So - the Beryl Manager is accessible immediately from the gem icon and you can't tweak a little on it to get it to your liking, and the Compiz settings aren't available, to me at least, so I can get the settings that I am used to in Beryl....hmmm...

I thought that the default Compiz setting that I viewed when I clicked Desktop Effects, as compared to Beryl, were slow and kind of beginner looking. There was no actual screen transparency, the cube rotated in a fashion that resembled the first weeks of Compiz. The window wobble is weak and there seems to be no place to change the settings in Compiz to get what one wants out of the software.

If Beryl settings are to wild for you out of the box, then tune them down. Or are you one of those who use software OOB and then won't/can't change the settings to his/her liking?

For whatever reason, Beryl is much more configurable at the moment, and since I have used Compiz since the beginning, then moved to Compiz-Quinn, then full on to Beryl, then I think that I have a fair amount of experience using this bit of software. Heck - I used Compiz when it would crash my PC if I used it for more than an hour.

Beryl Manager is easy to tweak if one just looks.....I just want to know where the settings are for Compiz.

Compiz and Beryl will be one in the same soon, so we may as well get used to setting up Compiz.

-SE

---

### Post by steveneddy on 2007-04-22
> **derrekito said:**
> Beryl doesn't work for me either.  I get a nasty error.
```

** (beryl-manager:3043): CRITICAL **: can't execute beryl-xgl: Success

``` 


I posted this issue, but no replies yet. [http://ubuntuforums.org/showthread.php?t=416975](http://ubuntuforums.org/showthread.php?t=416975)

There are specific settings to get these effects with an ATI vid card. I think that if you search for ATI beryl, there is a forum posting about the settings that you may need to add to the xorg.conf file to get everything working well with Beryl or Compiz.

Try looking [here]("http://ubuntuforums.org/showthread.php?t=272104") first.

There are postings about setting ATI cards for Beryl and Compiz.

-SE

---

### Post by derrekito on 2007-04-22
> **steveneddy said:**
> There are specific settings to get these effects with an ATI vid card. I think that if you search for ATI beryl, there is a forum posting about the settings that you may need to add to the xorg.conf file to get everything working well with Beryl or Compiz.

Try looking [here]("http://ubuntuforums.org/showthread.php?t=272104") first.

There are postings about setting ATI cards for Beryl and Compiz.

-SE

The thing is, I have compiz working.  and the error suggests that I NEED this binary beryl-xgl , but that doesn't seem to be in the repository for Ubuntu. Hmmmmm.

---

### Post by steveneddy on 2007-04-22
I was my understanding that one didn't have to have XGL when running Feisty. that was the big deal in the past, that everyone HAD to run XGL to get any compositing working. I guess either XGL or AIGLX. 

I use an nVidia card in all my stuff, so the ATI thing is beyond me. I believe there is a fix. Try going to the [Beryl ]("http://forum.beryl-project.org/")site and looking there, also.

-SE

---

### Post by steveneddy on 2007-04-22
> **Deviltongue said:**
> how do I install themes for compiz?

Back to the original question......

---

### Post by derrekito on 2007-04-22
Yeah see thats the thing!  ATI does not have any composite function at all.  So the work around is to run a XGL session.  It's the only way! :(  Bah I hate my laptop :p.

---

### Post by derrekito on 2007-04-22
> **steveneddy said:**
> Back to the original question......

yeah sorry for the hijack, bah still have no idea how to install a compiz theme.

---

### Post by qamelian on 2007-04-22
> **steveneddy said:**
> I was my understanding that one didn't have to have XGL when running Feisty. that was the big deal in the past, that everyone HAD to run XGL to get any compositing working. I guess either XGL or AIGLX. 

I use an nVidia card in all my stuff, so the ATI thing is beyond me. I believe there is a fix. Try going to the [Beryl ]("http://forum.beryl-project.org/")site and looking there, also.

-SE
You only ever had to run XGL if your card was not supported by AIGLX. I've been running AIGLX from day one one my laptop with an ATI Mobility Radeon 9000 IGP. My desktop PC has an Nvidia Geforex FX5600 which is not supported by AIGLX, so it needs XGL. 

It all depends on just which model of card you have.

---

### Post by qamelian on 2007-04-22
> **derrekito said:**
> Yeah see thats the thing!  ATI does not have any composite function at all.  So the work around is to run a XGL session.  It's the only way! :(  Bah I hate my laptop :p.

Depends on which ATI card you have. Mine runs perfectly under AIGLX but won't run under XGL at all.

---

### Post by derrekito on 2007-04-22
> **qamelian said:**
> Depends on which ATI card you have. Mine runs perfectly under AIGLX but won't run under XGL at all.

Well enabling the composite function breaks the driver.  ATI M300.

---

### Post by Tyltyl on 2007-04-23
When I first installed Compiz one year ago I was able to change themes, same with Beryl later and Emerald. But now I can't with the built in Compiz I found in Feisty. Even after I installed Emerald I couldn't change them...

---

### Post by rogeriovinhal on 2007-04-23
The fglrx drivers doesn't support Composite and, by consequence, AIGLX.

BUT, the opensource 'ati' driver does support Composite and AIGLX by default. If you can get direct rendering with the 'ati' driver, then you can have Effects with the 'ati' driver.

In Edgy I couldn't get direct rendering with 'ati', then I had to install XGL and run beryl on it, but now this isn't working in Feisty. I don't know why, I can't get direct rendering with fglrx AND XGL. But so far 'ati' opensource driver is working fine, so it may be better for me.

It is even easier to install. No need to install XGL, and make a new session.

---

### Post by derrekito on 2007-04-23
I was never able to get direct rending to function with the opensource driver either.  I didn't spend enough time with it in feisty however to even find out.

---

### Post by steveneddy on 2007-04-23
OK - figured it out. You have to install 

```
gnome-compiz-manager
```

from Synaptic.

Look under System -->Preferences -->GL Desktop and you will find all of the controls that the Compiz want you to have.

Beryl is a lot more fun and lets you tweak settings a lot farther than Compiz.

But it is fun to have another toy to play with.

Cheers - SE

---

### Post by derrekito on 2007-04-23
> **steveneddy said:**
> OK - figured it out. You have to install 

```
gnome-compiz-manager
```

from Synaptic.

Look under System -->Preferences -->GL Desktop and you will find all of the controls that the Compiz want you to have.

Beryl is a lot more fun and lets you tweak settings a lot farther than Compiz.

But it is fun to have another toy to play with.

Cheers - SE

doesn't seem to want to work with me.  I update to 0.5.0 is that a problem?

---

### Post by steveneddy on 2007-04-23
> **derrekito said:**
> doesn't seem to want to work with me.  I update to 0.5.0 is that a problem?

I don't know - I'm still on the stock version of Compiz.

**WARNING**

Do NOT turn on Desktop Effects while running Beryl!

Bad things happen......

Great - another $2000 door stop. I'm using this one to hold up the garage door.

---

### Post by derrekito on 2007-04-23
> **steveneddy said:**
> I don't know - I'm still on the stock version of Compiz.

**WARNING**

Do NOT turn on Desktop Effects while running Beryl!

Bad things happen......

Great - another $2000 door stop. I'm using this one to hold up the garage door.

yeah I get that error regardless of compiz running or not, like I said it seems to want to run a binary that doesn't exist.  beryl-xgl

---

### Post by frup on 2007-04-29
Back to the real question... The themes.
So you can untick using metacity themes, how do you enable the compiz theme? Do you have to place it somewhere, is there a theme package to enable/install it? Compiz a year ago had this feature and Beryl has awesome themes.

---

### Post by kaede on 2007-04-30
im using compiz, but can't find a way to install themes that i got from gnome-looks.
they said to install program named gcomiz themer. but can't find it on feisty repo. anyone know how to solve tis?

---

### Post by ayllu on 2007-04-30
I using feisty and i have compiz installed but i want to use beryl so i installed beryl but i get the beryl-manager but i cannot use it still compiz taking effect, how to make beryl take effect

---

### Post by derrekito on 2007-04-30
> **ayllu said:**
> I using feisty and i have compiz installed but i want to use beryl so i installed beryl but i get the beryl-manager but i cannot use it still compiz taking effect, how to make beryl take effect

in the beryl-config there should be a window manager option, select Beryl.  If this doesn't work, then welcome to the club! :)

---

### Post by kaede on 2007-05-01
> **kaede said:**
> im using compiz, but can't find a way to install themes that i got from gnome-looks.
they said to install program named gcomiz themer. but can't find it on feisty repo. anyone know how to solve tis?
need help pls, i need more effect on my screen :D

---

### Post by kpolice on 2007-05-01
compiz themes from gnome-look won't work with compiz from feisty.

The compiz themes you downloaded were made for compiz-quinn which then changed it's name to beryl.

---

### Post by kaede on 2007-05-01
well, actually from synaptic i've installed the thing called gnome-extra-plugin. any idea how to using it?

all i know is just some effect that configurable via compiz tray icon on the right top corner of the screen thats it. 

thanks

---

### Post by derrekito on 2007-05-01
> **kpolice said:**
> compiz themes from gnome-look won't work with compiz from feisty.

The compiz themes you downloaded were made for compiz-quinn which then changed it's name to beryl.



So these compiz themes we download from gnome-look.org will not work with compiz?  Now that does not make any sense.

---

### Post by kpolice on 2007-05-01
No they won't work.

As I told you it was for compiz-quinn which then was renamed as Beryl.

---

### Post by derrekito on 2007-05-01
> **kpolice said:**
> No they won't work.

As I told you it was for compiz-quinn which then was renamed as Beryl.

/confused  

lol now Beryl and Compiz are one... or will be... whatever.  Sigh, I'm not going to worry about it anymore, I'll wait until the program is more reliable, and maybe by then ATI will push out some drivers worth installing.

---

### Post by kaede on 2007-05-02
so ? compiz or beryl ?

heheheheh. seems like berly offering more various effect . am i rite?
but people said compiz more stable. :D

---

