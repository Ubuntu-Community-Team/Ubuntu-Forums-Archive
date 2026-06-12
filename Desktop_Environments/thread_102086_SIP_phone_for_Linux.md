---
title: "SIP phone for Linux"
date: 2005-12-11
forum: Desktop Environments
---

### Post by Jingo on 2005-12-11
Where do I find a decent SIP phone for linux?

Linphone does not work great, can't get it to register with my Voip provider.

kPhone works.. but the audio and the interface is bad.

minisip.org seems to provide a good one... dependency problem!!!
Anyone tried minisip?

Finally I found X-Lite for linux. But this is a beta version, and I don't know if it is still maintained!? [http://support.xten.net/](http://support.xten.net/)
And it is not open source :(

Anybody using SIP voip??

---

### Post by ominolore on 2005-12-11
I'm using X-Lite too. I think it has a very bad interface (i mean the way to use it) but it seems to work fine, at least, for me..

---

### Post by anil_robo on 2005-12-11
I guess you could try GIZMO. It's at [www.gizmoproject.com](www.gizmoproject.com)

---

### Post by Jingo on 2005-12-12
Can Gizmo connect to other SIP providers than GIZMO?

I need to connect to my current Voip provider!

---

### Post by anil_robo on 2005-12-12
Yes it does! I just looked it up for you on gizmoproject website. Here's the link: [http://support.gizmoproject.com/?_a=knowledgebase&_j=questiondetails&_i=7]("http://support.gizmoproject.com/?_a=knowledgebase&_j=questiondetails&_i=7")
In summary, it says:
> [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]Gizmo Project is an open standards based implementation. You can call too and from other sip networks. You can call hardware / software clients around the world. You can manage an addressbook, talk to other users via Instant Message. All using open standards so you can use other clients and communicate with other services seemlessly. All at no cost![/SIZE][/FONT][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]

Look at this screenshot of my Gizmo:
[IMG]http://img394.imageshack.us/img394/3417/gizmosip0ls.jpg[/IMG]
Hope it helps! :)
[/SIZE][/FONT]

---

### Post by doboy007 on 2005-12-12
I suppose you could try Stanaphone. I haven't used it but its worth checking out.

---

### Post by mcrosmar on 2005-12-13
I installed Gizmo, but it hangs on "Agent started..." at login. Any ideas?

Thanks.

---

### Post by Chris Tucker on 2005-12-13
Skype! Skype! Skype! Skype! Skype! 
skype is awesome, pc-to-pc  very popular, very cheap pc-to-phone, and reasonable phone-to-pc!

---

### Post by Brynster on 2005-12-13
Skype is not a Sip phone service. Skype is a peer to peer VOIP application kind of an enhanced msn or yahoo messenger service.

Skype cannot be configured to connect to other Sip phone services since it is a propriety peice of software and is not open source. Infact it is the scourge of the Sip phone world.

That said its an excellent application that works wonderfully, but the interface for Linux needs a work over as it looks like something from 1992 imo.

---

### Post by Chris Tucker on 2005-12-13
well, i have no idea what an SIP phone is then

BTW, the skype interface for linux does not look like something from 1992, thats just your QT theme. change your theme and it looks great. i'll post some screenshots later when im finished upgradeing from my old version, having some sound device issues.

---

### Post by leech on 2005-12-13
A SIP phone is any phone that uses SIP (Session Initiation Protocol)  They are adding SIP to Gnomemeeting as well, I believe you can get cvs packages for Debian (not sure if they work under Ubuntu).  Asterisk aslo uses SIP (which is why SIP phones rock, you can get VOIP phones that use SIP and connect them throughout your house/business and have everyone set up on their own extensions.)  Something like Linphone though is considered a soft phone.

Leech

---

### Post by clayton on 2005-12-14
I just installed  gnomemeeting-opal-cvs, which I believe contains the features of gnomemeeting 2 (SIP and H.323). The installation went flawlessly, and I registered on sip.gnomemeeting.net. I believe that right now you can only call others in the sip.gnomemeeting.net directory (with SIP protocol). You need to add these lines to your sources.list file:

deb [http://snapshots.gnomemeeting.net/ubuntu/](http://snapshots.gnomemeeting.net/ubuntu/) breezy main
deb [http://snapshots.voxgratia.org/ubuntu/](http://snapshots.voxgratia.org/ubuntu/) breezy main

Also, see here:

[http://snapshots.gnomemeeting.net/](http://snapshots.gnomemeeting.net/)

I'm also going to try out Gizmo tonight.

Clayton
sip:anderc@gnomemeeting.net

---

### Post by anil_robo on 2005-12-14
I've followed directions on qt configuration somewhere from this forum and skype looks alright now. But some other applications still look ugly - VLC media player for example. How do I fix that?

---

### Post by Chris Tucker on 2005-12-15
vlc uses its own theme system... i havent figured it out yet...but it doesnt use Qt so your Qt themes dont apply to it

---

### Post by Brynster on 2005-12-15
[QUOTE=Chris Tucker]BTW, the skype interface for linux does not look like something from 1992, thats just your QT theme. change your theme and it looks great. i'll post some screenshots later when im finished upgradeing from my old version, having some sound device issues.[/QUOTE]

Ok I will play but it looked awful as well in another disty which was KDE based.

---

### Post by Typhoon on 2005-12-15
Gizmo is not bad, but it will not register with other SIP providers (such as Free World Dialup). X-Ten Lite has the advantage of being able to register with multiple providers.

SJphone is a very good SIP phone for Linux. It is not Open Source. It registers with only one service at a time, but has multiple "profiles" that lets you switch quickly from one to another.

If you don't mind the rather steep learning curve for Asterisk, then the way to go is to use X-Ten or SJphone to connect to an asterisk server. Asterisk registers with all your providers and the soft-phone registers with Asterisk.

If you do that, then you could also use an IAX phone to register with Asterisk. Kiax is a good one that will work with Ubuntu. IaxComm will as well (although as I recall, you need to make a symbolic link to one of the libraries).

HTH,
Typhoon

---

### Post by Brynster on 2005-12-16
Gizmo an be used with any sip phone provider. Or at least thats the theory. If you go into settings you can change the provider in there. (sorry for the vagueness i am away from a PC with gizmo installed)

---

### Post by Typhoon on 2005-12-16
"Gizmo an be used with any sip phone provider. Or at least thats the theory. If you go into settings you can change the provider in there. (sorry for the vagueness i am away from a PC with gizmo installed)"

Don't think so. In the Settings you can add Gizmo accounts, but not register with other providers.

Typhoon

---

### Post by frobroj on 2006-12-27
Be aware that Gizmo will send an email to everyone in your contacts list if you import it... YUK! Here is a free open source sip phone that is video capable.. 
[http://www.kapanga.net/IP/home.cfm](http://www.kapanga.net/IP/home.cfm)
I personally use the xten Eyebeam. Its worth the dough. Its incredible!
Thats my 2 cents worth.

---

