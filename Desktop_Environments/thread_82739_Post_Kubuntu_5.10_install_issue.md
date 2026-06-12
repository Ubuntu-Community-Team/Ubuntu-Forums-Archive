---
title: "Post Kubuntu 5.10 install issue"
date: 2005-10-27
forum: Desktop Environments
---

### Post by Sankukai Monkey on 2005-10-27
Complete newbie to this world but determined tinkerer :D 

Have clean-installed Kunbuntu 5.10 onto a Shuttle SV24 256Mb ram and Via 733 Samuel. I only managed to get the install to complete and reboot into Kubuntu after 4 days dicking about with re-burnt discs, swapping out old drives etc etc.

Even the final stage of the install didn't load all the selected packages and I was given that onscreen prompt saying some of them wouldn't work. :???: 

I'm now looking at the desktop and pretty much everything I try to us is working but when I try to start Synaptic I get asked for su password which I don't have. 

Do I need to assign my user to the SU group or something ? I've read some posts in here aready about sudo and followed those suggestions and it kind of worked but like I say I'm a virgin !!

Can anyone simply explain to me what I need to do to 
[LIST]
[*]get Synaptic to load [I've no su password] ?
[*]make apt-get work from the Kconsole to update the packages that failed from the base install ?
[/LIST]

MTIA
Scott

---

### Post by thumper on 2005-10-27
You can get apt-get working from the console using```
sudo apt-get update
```when prompted for a password, it is your users password.  There is a big talk on sudo somewhere, so if you are interested, then search for it (maybe on the wiki).

Ditto for starting synaptic, although if you are using Kubuntu, why not use adept?

---

### Post by GeneralZod on 2005-10-27
[QUOTE=thumper]
Ditto for starting synaptic, although if you are using Kubuntu, why not use adept?[/QUOTE]

At its current stage of development, Adept is not as feature-packed as Synaptic, although I like the way it's going - the multi-threaded search behaviour, for instance, is great!

Hopefully it will be a more even match come Dapper.

---

### Post by Sankukai Monkey on 2005-10-27
[QUOTE=thumper]You can get apt-get working from the console using```
sudo apt-get update
```when prompted for a password, it is your users password.  There is a big talk on sudo somewhere, so if you are interested, then search for it (maybe on the wiki).

Ditto for starting synaptic, although if you are using Kubuntu, why not use adept?[/QUOTE]

Ok Thumper...I'll try with sudo and have a good ferret around for relevant posts on it's use.
Goddamn I love the interface Kubuntu though !:KS

---

### Post by Sankukai Monkey on 2005-10-27
Gutted...just booted my PC this evening to find that instead of loading KDE it's just giving me the command line login :confused: :confused: :confused: :confused: :confused: :confused: 

WTF ?! Where do I go from here...just reinstall ?
I should of course mention that I've just run my inputs to the Kubuntu box through a Belkin Omni KVM....is this bad ?

Ha hah ! Can now get the desktop up but she's a damned ugly 640 x 480 res ! More soon !

---

### Post by thomax on 2005-10-28
to get into synaptic you need to do this trough command line 

sudo synaptic (it will prompt for a pw just give your userpw (if you are the admin otherwise it will NOT work))

for the X problem restore /etc/X11/xorg.conf which will probably be called xorg.conf.back rename it to xorg.conf

---

