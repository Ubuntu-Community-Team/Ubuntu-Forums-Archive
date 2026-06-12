---
title: "CD Burning with Abuntu"
date: 2005-03-05
forum: Desktop Environments
---

### Post by Mark7805 on 2005-03-05
Hi I'm using Ubuntu live cd so I can just restore my files I used on Windows XP.Does any1 know how to burn cd's on Ubuntu easliy.Like I said I come from Using Windows XP so I have know clue how to use terminal or anything.If some1 can help it would be very apperciated

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]Hi I'm using Ubuntu live cd so I can just restore my files I used on Windows XP.Does any1 know how to burn cd's on Ubuntu easliy.Like I said I come from Using Windows XP so I have know clue how to use terminal or anything.If some1 can help it would be very apperciated[/QUOTE]


GnomeBaker is probably the best Gnome based burner.
K3B is good, but we wanna stay GNOME.

be sure to apt-get install cdda2wav first [might be in universe repository]
[http://www.ubuntulinux.org/wiki/GnomeBaker](http://www.ubuntulinux.org/wiki/GnomeBaker)

Loos a bit like Nero eh ;-) ?
[IMG]http://gnomebaker.sourceforge.net/wp-content/gnomebaker1.png[/IMG] 
[IMG]http://gnomebaker.sourceforge.net/wp-content/gnomebaker3.png[/IMG] 

and this is [K3B](http://k3b.plainblack.com/index.pl/screenshots) 
its KDE Based, ur on Gnome so ull hav to download quite some MBs from KDE part :s

G-Baker is about 500k and blends in nicely with whatever u theme ur ubuntu

---

### Post by Mark7805 on 2005-03-05
So I get the Gnobe baker bianary?Then what?

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]So I get the Gnobe baker bianary?Then what?[/QUOTE]

U would download [this](http://people.debian.org/~goedson/packages/ubuntu/warty/gnomebaker/releases/i386/gnomebaker_0.3-1ubuntu1_i386.deb)  file, then in a terminal do this :

> $sudo dpkg -i gnomebaker_0.3-1ubuntu1_i386.deb 
u just write gnom]and press TAB to complete the name[

it will install , if it doesnt install, i told u to get cdda2wav

go to synaptic package manager , settings > repositories , check EVERY single one there, hit ok, the press RELOAD then search for cdda2wav right clic  > install

---

### Post by Mark7805 on 2005-03-05
When I go to termanal I use requires superuser privilges

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]When I go to termanal I use requires superuser privilges[/QUOTE]


> $sudo su 
enter your password, 
then make the process


I know this sounds like a hassle, but i REALLY recommend to every1 starting linux/ubuntu to read [**THIS**](http://ubuntuguide.org/)  guide; or at LEAST bookmark it, and if u have a problem, look over the topics.


There it explains the basic on everything u would need for an everyday ubuntu usage .

---

### Post by Mark7805 on 2005-03-05
when I go to type my password in nothing shows up.Meaning I can't even type my password in

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]when I go to type my password in nothing shows up.Meaning I can't even type my password in[/QUOTE]


newsflash : this aint XP

it doesnt show as a security measure so that some1 near by cant even know how many characters


haha funny but ok, type it, it is typing itself trust us

---

### Post by Mark7805 on 2005-03-05
ok last question.What is the Default warty password.I try to change it but it always goes back to the default password.

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]ok last question.What is the Default warty password.I try to change it but it always goes back to the default password.[/QUOTE]


Dont worry dude we can help u for as long as u need us .

There is no default passwd
here is the thing

When u installed u created a passwd, the one u login thru.
ur a user , just like Xp

Ubuntu does not allow u to conect directly as Administrator or Root [linux name], it creates a fake root environment. its safer for n00bs, and u only hav to know 1 passwd instead of multiple.

so everytime ur asked for a passwd input the one u login with


if u want to hav a personal root password, wich i dont see why u would need it, type
> sudo passwd 
and create a passwd


hav in mind, should u screw things from root environment, ull most likely need a fresh reinstall.



and NEVER login to gnome/ubuntu as root !!its a "sacred" rule!!

---

### Post by bored2k on 2005-03-05
if u would give in a read the topics,u wouldve found

[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)
Q: How to set/change/enable root user password?

---

### Post by landotter on 2005-03-05
CD Burning with Ubuntu out of the box: 

Open file manager, places, Cd creator. Drag files into window. Burn.

to burn an ISO:
right click, burn.

Now wasn't that easy?

---

### Post by bored2k on 2005-03-05
[QUOTE=landotter]CD Burning with Ubuntu out of the box: 

Open file manager, places, Cd creator. Drag files into window. Burn.

to burn an ISO:
right click, burn.

Now wasn't that easy?[/QUOTE]
 lol

i automatically understood as if he had already gone thru that lol

---

### Post by landotter on 2005-03-05
[QUOTE=bored2k]lol

i automatically understood as if he had already gone thru that lol[/QUOTE]
 I made no such assumption, grasshopper.

:P

---

### Post by Mark7805 on 2005-03-05
Ok when I do everything after typing my password in it says root@ubuntu:/home/warty # 

What do I type here.Oh shit I should of mentioned this before.I'm using the live cd of unbuntu.can I still use it or do I need to get the whole thing installed?

gnomebaker is on my desktop right now so make sure you give me the right things to say in terminal remeber

---

### Post by bored2k on 2005-03-05
there are some underage kiddies here ; try avoiding funky w0rdz.

---

### Post by Mark7805 on 2005-03-05
what yah mean.can you help me?

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]what yah mean.[/QUOTE]
i meant try avoiding words like sh!@T 

[QUOTE=Mark7805]can you help me?[/QUOTE]
ubuntu live aint my territory


i couldve tried but i just had dinner ... i.e. lazy-mode

---

### Post by Mark7805 on 2005-03-05
alright I'll watch my languages [-X  if any1 can help me out there plz come and do so

---

### Post by bored2k on 2005-03-05
By the way has anyone here besides Mark7805 ever used **A**buntu ? how is it like ?

lol

---

### Post by bored2k on 2005-03-05
did u try landotter's post ?

that burner app should run in a live disc. .. as long as u dont try 2 burn from the same disc the live is reading lol

---

### Post by Mark7805 on 2005-03-05
I don't see places.I go to file management then I can't see places.where is it?

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]I don't see places.I go to file management then I can't see places.where is it?[/QUOTE]
 open nautilus

go > cd creator

or 
> nautilus burn:///


hes using hoary thats why he sees places

---

### Post by Mark7805 on 2005-03-05
finnaly!Thanks for all those who helped me on here.I can take it all from here.But just one last thing.How do I make it so I can burn more file on to the cd after I already burned using the same cd?

---

### Post by bored2k on 2005-03-05
[QUOTE=Mark7805]finnaly!Thanks for all those who helped me on here.I can take it all from here[/QUOTE]finally ;  :-({|= 
 10 posts just to burn a disc 

wao XP really does enslave ppl :P

---

### Post by ericsp on 2005-03-06
Hi,

not that the guy is on Ubuntu**Live** so he probably cannot install gnomebaker. If you need a password, it is probable "ubuntu" or "Ubuntu". You'd beter partition your HD and install HD next to your windows. If you are satisfied, you can delete the windows partition later.

Eric

---

### Post by occy8 on 2005-03-23
I just got Gnomebaker installed and try to burn an audio cd.
It locks up at the message "converting wav to cd audio"

---

### Post by occy8 on 2005-03-23
this is an interesting one 
the files I wanted to burn were on the windows partition.
One file was called **blabla.WAV** and gnomebaker got stuck while graveman couldn't find it. ( thats how I found out )
renamed it to **blabla.wav** and everything worked fine

---

### Post by TravisNewman on 2005-03-24
bored2k, sorry, gonna correct a few things
[QUOTE=bored2k]
if u want to hav a personal root password, wich i dont see why u would need it, type
 sudo passwd
and create a passwd
[/QUOTE]
"sudo passwd root" is the safe way to do this. I tried just "sudo passwd" when the root account was disabled, and it just changed my user password. I know this is supposed to work in most cases, but I think it is dependent on some config files. "sudo passwd root" specifies root.

and about "sudo su" followed by dpkg -i whatever:
not needed
all you have to do is "sudo command -args"
su isn't needed at all.

---

