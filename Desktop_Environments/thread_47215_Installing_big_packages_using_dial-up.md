---
title: "Installing big packages using dial-up"
date: 2005-07-07
forum: Desktop Environments
---

### Post by Stag on 2005-07-07
Dear All,

How do other people install packages that are, for example K3B at 114MB across a dial-up connection?  It would take forever to download and install wouldn't it?  Are there any tricks to deal with this issue?

Any help gratefully appreciated.
Stag :???:

---

### Post by javiadip on 2005-07-07
no tricks, you would just have to leave your dialup on over night or something.

---

### Post by jasmuz on 2005-07-07
[QUOTE=Stag]Dear All,

How do other people install packages that are, for example K3B at 114MB across a dial-up connection?  It would take forever to download and install wouldn't it?  Are there any tricks to deal with this issue?

Any help gratefully appreciated.
Stag :???:[/QUOTE]
 Or start downloading everytime you get online, and it will resume were it left off. (Synaptic & apt-get do that, they keep a partial save of the download).

---

### Post by Stag on 2005-07-07
Thanks for the tips but to me they dont make sense.  Maybe being at the bottom end of the world has something to do with this (ie slow dial-up speed). I have never ever even considered trying to download anything more than about 15MB using dial-up, partly because it takes forever and partky becuase I have a limit of 100MB per month download. 

Does someone out there provide a service where they burn popular Linux software to CD which you can then refer Synaptic to?

Stag

---

### Post by jasmuz on 2005-07-08
[QUOTE=Stag]Thanks for the tips but to me they dont make sense.  Maybe being at the bottom end of the world has something to do with this (ie slow dial-up speed). I have never ever even considered trying to download anything more than about 15MB using dial-up, partly because it takes forever and partky becuase I have a limit of 100MB per month download. 

Does someone out there provide a service where they burn popular Linux software to CD which you can then refer Synaptic to?

Stag[/QUOTE]

Stag where do you live???

---

### Post by angkor on 2005-07-08
[QUOTE=Stag]I have a limit of 100MB per month download.[/QUOTE]

 8-[ 
 :wink: 

Don't you know anyone with a fast inet connection. You'll be able to download the desired packages (mind dependencies) burn em on cd and install them on your comp.

---

### Post by poptones on 2005-07-08
I go to the city with my $200 laptop and download stuff there. Every minute I spend at the cafe is (literally) more than an hour I save downloading from home. 

But even without that I do not find it so bad. I installed k3b from home, it took about five hours - not a big deal. I used to keep an active easynews account that had a 6GB a month download limit. Even just downloading on a dialup I managed to max out that account every single month, and some months I would even buy another 6GB. 

All on a 56k line.

---

### Post by maruchan on 2005-07-08
100 MB a *month*? Wow. I'm not on dialup anymore but when I was, I used Access4Less (in the US), and downloaded about 200 Megs a week :D

---

### Post by az on 2005-07-08
[QUOTE=Stag] 

Does someone out there provide a service where they burn popular Linux software to CD which you can then refer Synaptic to?

Stag[/QUOTE]


Yes, there are, but most of them cannot make a deb cd to save their life.  You would need to copy all the stuff into your /var/cache/apt/archives directory and apt-get update and hope that not a lot of packages have changed in the meantime.

You can always install k3b from the Kubuntu cd.

Send me your address and I'll burn off a copy for you

[email]ubuntuguy@yahoo.ca[/email]

With the cd, you just add the cd to your repositories in Synaptic and then install K3b.

I would suggest you remove your online repositories from your sources.list.  You do not want to be reloading 2 megs of a packages.gz file every other day with the update manager.

---

