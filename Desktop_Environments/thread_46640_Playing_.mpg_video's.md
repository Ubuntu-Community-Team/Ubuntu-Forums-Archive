---
title: "Playing .mpg video's"
date: 2005-07-05
forum: Desktop Environments
---

### Post by larued on 2005-07-05
I have Warty right now and a shipment of Hoary on the way hopefully. So until then Im stuck with Warty. Id like to be able to watch video's on my computer but Totem keeps rejecting the files and saying that they are incompatible. I can play them on my lower end windows system but they run all sketchy. Any way to fix the problem with Ubuntu? Or any other programs besides Totem that plays .mpg files for linux?

---

### Post by grim42 on 2005-07-05
[QUOTE=larued]I have Warty right now and a shipment of Hoary on the way hopefully. So until then Im stuck with Warty. Id like to be able to watch video's on my computer but Totem keeps rejecting the files and saying that they are incompatible. I can play them on my lower end windows system but they run all sketchy. Any way to fix the problem with Ubuntu? Or any other programs besides Totem that plays .mpg files for linux?[/QUOTE]
 Getting various video formats to play, even with Hoary, requires installing a few extra packages.

Try having a look at the Ubuntu Guide for Warty ([http://ubuntuguide.org/4.10](http://ubuntuguide.org/4.10)) which describes how to install various media players and codecs.

You'll probably want to install the following at least:
w32codecs
gstreamer0.8-plugins

I find that the totem-xine package also works a lot better for video playback than totem's standard setup.

---

### Post by larued on 2005-07-05
as far as i can see this would require me to be online to get the codecs, is there anyway that i can get the things that i need in binary form so i can burn them to diska nd then put them of my ubuntu system? Or any way that someone can provide links for me to download them and then where to put them? Im more of a front end linux user. I don't know all this advanced stuff with linux yet. Thnx for the help  :smile:

oh and incase you didn't get my drift my ubuntu system is not hooked up to the net. Ive got to downlaod everything i need on my windows system and then burn to disk and put it on my ubuntu system.

---

### Post by larued on 2005-07-07
[QUOTE=larued]as far as i can see this would require me to be online to get the codecs, is there anyway that i can get the things that i need in binary form so i can burn them to diska nd then put them of my ubuntu system? Or any way that someone can provide links for me to download them and then where to put them? Im more of a front end linux user. I don't know all this advanced stuff with linux yet. Thnx for the help  :smile:

oh and incase you didn't get my drift my ubuntu system is not hooked up to the net. Ive got to downlaod everything i need on my windows system and then burn to disk and put it on my ubuntu system.[/QUOTE]
 any help? anyone

---

### Post by larued on 2005-07-13
[QUOTE=larued]any help? anyone[/QUOTE]
 does anyone know the defualt player dormat for Totem?

---

### Post by ubuntp on 2005-07-13
There is no default player format, although it's a good question what totem can actually play out of the box.

About your problem, you must download the .deb files for w32codecs and probably also totem-xine. Or it may be just enough to download the codecs directly from here: [http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2](http://www1.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2) and extract the files into /usr/lib/win32 (create if it doesn't exist).

---

### Post by larued on 2005-07-13
Thanks, ill try this out and let you know what happens

---

### Post by larued on 2005-07-14
[QUOTE=larued]Thanks, ill try this out and let you know what happens[/QUOTE]
 didn't work, i still havn't figured out how to login as root so i can't create the folder :P n00balicious right here

---

### Post by poptones on 2005-07-14
In spite of the wiki folks saying "don' do that" I am gonna refer you to [http://ubuntuguide.org](http://ubuntuguide.org) 

This is a cookbook. Do things *exactly* as it says and you should be able to get up and running.

---

### Post by larued on 2005-07-15
[QUOTE=poptones]In spite of the wiki folks saying "don' do that" I am gonna refer you to [http://ubuntuguide.org](http://ubuntuguide.org) 

This is a cookbook. Do things *exactly* as it says and you should be able to get up and running.[/QUOTE]
 yeah, its says use the sudo command to download the files, which i understnad ill need to do. On my linux system though, i only have dailup access. There is a Gone PPP dialer thinger, but it also uses sudo to get it. Anyone know where i can get Gnome PPP so I can download the codecs and crap i need for Totem? Or how to log in as root?

---

### Post by poptones on 2005-07-15
You do not "log in as root." You simply type **exactly what it says** in the guide. When it says "sudo" *you type sudo*. If you type "sudo nautilus" for example and press enter it will then ask you for **your** password and when you enter that password it will complete the command and open nautilus with "root" prviledges. 

Read the guide. When it says "read this part first" that is not an option - read that part first.

---

### Post by thenonymous on 2005-07-21
sudo allows a user to run a command as a different user. In cases when the user is not specified, as in "sudo nautilus", the superuser (the default user that "sudo" uses) is used.

So basically, what "sudo nautilus" does is 'do nautilus as superuser' or 'run nautilus as superuser'. A friend who taught me what "sudo" does told me before that it simply meant 'do as SuperUser'. Makes lots of sense.

You wouldn't have to log in as root. Literally speaking. :)

Anyway, sorry, I don't know how to set up a dial-up connection in Linux.

---

