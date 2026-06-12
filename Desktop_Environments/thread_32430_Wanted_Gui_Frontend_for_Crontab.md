---
title: "Wanted: Gui Frontend for Crontab"
date: 2005-05-07
forum: Desktop Environments
---

### Post by jimcooncat on 2005-05-07
I don't know where to post this, if it's Ubuntu forums or if I have to find a gnome support forum.

I like crontabs and would like for my users to have an easy way to set up their own. When I select "Run Application ..." from the Application menu, a "Run at Intervals" button would be added to the dialog box. This would pop up a crontab editor with a new entry with the application path filled in. 

Maybe another button on the dialog could be "Run Later", which would present an "at" command entry form.

Especially nice would be the ability to limit the resources a user takes for their crontab use, preventing runaway scripts from hogging the system. Any ideas for this piece; maybe could be done with bash or djb's daemontools?

---

### Post by mlmurray on 2005-05-07
I'm sure there are others, but I've always used Webmin.  Do a search for "webmin" in synaptic.  I think the cron module comes with the base installation, but I may be wrong.  Apt has many other modules that are good for other administrative tasks as well.

---

### Post by mirek on 2005-05-07
[QUOTE=jimcooncat]I don't know where to post this, if it's Ubuntu forums or if I have to find a gnome support forum.

I like crontabs and would like for my users to have an easy way to set up their own. When I select "Run Application ..." from the Application menu, a "Run at Intervals" button would be added to the dialog box. This would pop up a crontab editor with a new entry with the application path filled in. 

Maybe another button on the dialog could be "Run Later", which would present an "at" command entry form.

Especially nice would be the ability to limit the resources a user takes for their crontab use, preventing runaway scripts from hogging the system. Any ideas for this piece; maybe could be done with bash or djb's daemontools?[/QUOTE]
 what about the tasche project? take a look at: [http://www.gnomefiles.org/app.php?soft_id=756](http://www.gnomefiles.org/app.php?soft_id=756) it is written in pygtk and also runs at console.

---

### Post by JonahRowley on 2005-05-08
I know this doesn't help you as a Gnome user, but I use KCron on KDE, and it's great.  You could conceivably run this on Gnome, if you don't mind loading all the KDE libs and daemons in the background.

---

### Post by jimcooncat on 2005-05-08
Thanks much, folks. The office system I'm planning will have light (not thin) clients and most apps running from a central computer. So I'm keeping away from having too much running (KDE tools), a desktop that needs a lot of attention (KDE), or a second interface for folks to learn (Webmin or Usermin).

Tasche looks like the dialog I'd like to have! Thanks for pointing that out, I'd probably never found it. Wish I had more time, the author could probably use some help to get this out of beta. [http://komo.mizu.sk/projects/tasche/index.php](http://komo.mizu.sk/projects/tasche/index.php) 

Kcron looks nice too, but the interface could stand a few tweaks from a new user's perspective. I hadn't thought about the environment management this provides, it's got me curious if this is something I should be looking at including.

I tried gcrontab, and with apologies to its author and fans, would rather use a text editor instead!

So I'm still curious about creating a button on the "Run Application ..." dialog. Who would be in charge of this part of the interface?

---

### Post by mirek on 2005-05-10
[QUOTE=jimcooncat]Thanks much, folks. The office system I'm planning will have light (not thin) clients and most apps running from a central computer. So I'm keeping away from having too much running (KDE tools), a desktop that needs a lot of attention (KDE), or a second interface for folks to learn (Webmin or Usermin).

Tasche looks like the dialog I'd like to have! Thanks for pointing that out, I'd probably never found it. Wish I had more time, the author could probably use some help to get this out of beta. [http://komo.mizu.sk/projects/tasche/index.php](http://komo.mizu.sk/projects/tasche/index.php) 

Kcron looks nice too, but the interface could stand a few tweaks from a new user's perspective. I hadn't thought about the environment management this provides, it's got me curious if this is something I should be looking at including.

I tried gcrontab, and with apologies to its author and fans, would rather use a text editor instead!

So I'm still curious about creating a button on the "Run Application ..." dialog. Who would be in charge of this part of the interface?[/QUOTE]
 about tasche - i know the author personaly. we developed this soft together (he was programming, i helped him with ideas and howtos how to do it - so some consulting). so - maybe, if there will be some interest in, we (or he ;) ) can continue developing this program. it works already, but also - there is still some work to do ;)

---

### Post by fackamato on 2005-05-11
[QUOTE=mirek]about tasche - i know the author personaly. we developed this soft together (he was programming, i helped him with ideas and howtos how to do it - so some consulting). so - maybe, if there will be some interest in, we (or he ;) ) can continue developing this program. it works already, but also - there is still some work to do ;)[/QUOTE]

Please do, it would be grrrreat! ;)

---

### Post by mirek on 2005-05-11
[QUOTE=fackamato]Please do, it would be grrrreat! ;)[/QUOTE]
 yes - i already talked with him, so - the plan is continue developing this soft, but during summer holiday, because he has to finish semester succesfully ;) so - now we can maybe gain ideas for the program, so if you have some, what to do better in this state of application, lets talk about.

---

### Post by newen on 2005-11-25
It would be great if this program could be further developed

---

### Post by frodon on 2005-11-25
[QUOTE=jimcooncat]I don't know where to post this, if it's Ubuntu forums or if I have to find a gnome support forum.

I like crontabs and would like for my users to have an easy way to set up their own. When I select "Run Application ..." from the Application menu, a "Run at Intervals" button would be added to the dialog box. This would pop up a crontab editor with a new entry with the application path filled in. 

Maybe another button on the dialog could be "Run Later", which would present an "at" command entry form.

Especially nice would be the ability to limit the resources a user takes for their crontab use, preventing runaway scripts from hogging the system. Any ideas for this piece; maybe could be done with bash or djb's daemontools?[/QUOTE]I think a nautilus bash script using zenity could do the the job for non-root crontabs.
If you only want to right click on a exe files and have a small GUI to set a crontab line, it shouldn't be so difficult. If you don't find anybody to do it send me a PM or post here if it's really what you want and i will do it when i will have the time.

---

### Post by ph3ar on 2008-04-23
Hello, the download links for tasche 1.0.8 are down.

---

### Post by martinw89 on 2008-06-08
I apologize for the late reply, this was the first Google result and I was hoping the following program would help further Google searchers.

I personally recommend *gnome-schedule*.  It's a very gnome-like GUI frontend to crontab that is really easy to use.  Hope that helps :)

---

