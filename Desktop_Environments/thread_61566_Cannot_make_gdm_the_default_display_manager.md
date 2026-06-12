---
title: "Cannot make gdm the default display manager"
date: 2005-09-01
forum: Desktop Environments
---

### Post by thundertoad on 2005-09-01
Hey, 

Have a bit of a problem.. I kinda sorta messed with my system a few days back and now gnome wont load as the default display manager. On boot up once the check list reaches gnome **it displays a Red star and says cannot run gnome it is not the default display manager**... I had.. well not accidently .. but definitly n00bly changed my default display manager to X ... just to check it out. After that gnome wouldnt load ... and I would get a funky debian log in box with red text on top stating that this is not a secure session.

Now to solve the loading in x problem I did a few things... including going into /etc/X11 and editing the file default-display-manager from xdm to gdm... problem is it doesnt work... it still doesnt load gnome and gives me the same error... so I uninstalled x from synaptic and now it doesnt load either gnome or X ... even though I tried to make gdm the default manager.

So no my machine boots into Command line... and I have to su then initiate gdm... after which gnome runs perfectly...

What do I need to do to switch between say KDE and GDM if I decide to install KDE as an alternate display manager?

can someone shed any light on this? and I apologize if this has been addressed in an older post.

Thanks.
ThunderToad

---

### Post by az on 2005-09-01
sudo dpkg-reconfigure gdm

It will ask you if you want to make gdm the default display manager.  You can do this with kdm as well.  In either of them, you can change the default session to be gnome or kde.

So, you have a choice.

If you are running gnome more often than kde, make gdm your default.  If you want to log into kde, log out and log back into gdm, but pick the kde session.

---

### Post by thundertoad on 2005-09-01
Thank you kindly,

I will try this the moment I get back home to my 'buntu box.
I have browsed a whole lot of posts today and none had mentioned that... hopefully that will do the trick... 

I'll fill you in with what happens .....
again muchos gracias

ThunderToad

---

### Post by az on 2005-09-02
You answered me in a personal message, but I think it is more helpful to take this back to the thread, here, so that others can bebefit.

What error do you get when you tyr to reconfigure gdm?

Perhaps you are using kdm, and do not have gdm installed.  I do not know.  You can also try to reconfigure kdm.

It would be really halpful to know what theerror is.  Betcha it's a thirty-second fix!

---

### Post by thundertoad on 2005-09-02
You're absolutely right... it was a thirty second fix... that took about half an hour with the help of a friend of mine who is a little more familiar with linux than I am.

Believe it or not your fix did the trick... but for some reason it didnt work the first time... I got my friend to do everything else he can possibly do ... then as a last resort got him to look up your post and then run your command again... he ran it ... it worked.

The thing is that there was two places that ubuntu was getting instructions about what the default display manager was... it was in startup item 13 (thats where I was getting that red star error that gdm is not the default display manager) and then after the boot up sequance finished starting I was getting command line prompt. I dont know where the second one was ... but it caused a conflict. or so I believe.

So I installed KDE and so kdm became the default display manager... problem is it was still showing me the display error at line 13 of the boot up sequance. and GDM was refusing to be the default display manager...
so again I re-installed X (dude I am n00bie to the core) and so I had three display managers to choose from.

But still I could not get gnome to be the default one... KDM worked fine but it was still bothering me that I couldnt get gnome to be default... so we ran your command again and it worked this time... maybe after KDE was installed that fixed (or didnt) something. The point is now I get gnome to boot up as default but I have an error at Start line 22 or something that says KDM cannot start... it is not the default display manager... but since GDM is start line 13 and start before the system gets to boot line 22 I dont see that error... but I know its there cause we saw it while my friend was switching between the ttys.

Confused yet? hehe sorry I cant get any more technical be you can rest assured that your instructions did the trick... just not the first time for some reason.

what I want to know now is how can I get that extra line out of the boot sequance... the one that tells it to boot kdm... number 22 ... is there a way to edit that so I dont get the error.

and sorry if sending you the private message was the wrong thing to do... I didnt think that my problem might be happening to someone else. like I said... n00bie to the core.

ThunderToad
~~~~~~~~~~~
Beware the Undertoad

---

