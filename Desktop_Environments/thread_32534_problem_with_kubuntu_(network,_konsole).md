---
title: "problem with kubuntu (network, konsole)"
date: 2005-05-08
forum: Desktop Environments
---

### Post by konan on 2005-05-08
Hi!

I have a two problems... First is, that when I try to configure my network in Control center I can't. If I want to go in administrator mode, it asks me for password, I type it in, and than nothing happens... It theows me back in main menu of Internet & Network menu...
What's wrong? I cant't configure my network!!

The second "problem" is, that my konsole is changeing it's background!!
Yesterday I have black background, but today is white...
It's preety strange!!!

Any help?

THANX


P.s.: I installed  Kubuntu four times, but this happens always after some time of useing it!

---

### Post by mindspin on 2005-05-08
Hi, you have to enable root login. Your question is asked and answered in several threads here in the forum. You'll find the solutions by searching the forum yourself.

happy sunday, mindspin

---

### Post by wwwolf on 2005-05-08
[QUOTE=mindspin]Hi, you have to enable root login. Your question is asked and answered in several threads here in the forum. You'll find the solutions by searching the forum yourself.

happy sunday, mindspin[/QUOTE]

Boy, that post sure was helpful. I did a search and I couldn't find this info. If it was so easy to find you could have provided the link.

anyway:

1. you can run the control center as root by going in the konsole and running 'sudo kcontrol' the control window will then pop up and you should be able to configure your network.

2. It could be that you were running the konsole on different virtual desktops. I have 4 and the konsole seems to remember what the settings are for each particular desktop I called it up on.

HTH,

wwwolf

---

### Post by konan on 2005-05-08
I searched the forums and I try different things

1. reinstal kcontrol
2. modify "/etc/sudoers" with adding "system_username ALL=(ALL) ALL"
3. deleting everything in /var/tmp/kdecache (the one with your username in it)
4.Checking the /etc/kde3/kdm/kdmrc file and change "RootLogin -  true".

but nothing helped... Some times it works (admin mode in kcontrol), and sometime it doesn't... Pretty strange!!

Don't know what else to do...

I tryed "sudo kcontrol" and it works fine, but I would like it works like it should...

If anybody knows what else I could do, please tell me...


Thanx for advise!

---

### Post by mindspin on 2005-05-08
Ok guys, I found it just by reading a bit in this forum....

try this thread and the included link, it solved my probs, but to suspect useres to read isn't harsh, I just didn't want to do the basics for you.

have  a look here [kadmin/sudo et al.](http://www.ubuntuforums.org/showthread.php?t=30893)  

mindspin

---

### Post by konan on 2005-05-09
Yeah, I have found all these posts, but none of them make my kcontrol worked...
Maybe my laptop si a bit strange?

 ;-)

---

### Post by mindspin on 2005-05-09
Hi, I don't think its your hardware,
on my machines
Kcontrol works sometimes and sometimes not, that's not real cool,but

"sudo kcontrol" works always.

For me it's not so important, coz I always used su for administrational purposes, so sudo kcontrol doesn't make any difference for me in usability......

I would call it a "minor" bug, but that's IMHO.

mindspin

---

### Post by konan on 2005-05-09
Yes, that's right...

I respect your opinion, but for me it's very disturbing when something doesn't work like it should...

I switched back to Ubuntu and Gnome and that's it...

Maybe later developers of Kde will fix this bug and I'll switch to Kde, but for now eventhough I like Kde more, I'll stick wit Gnome...

Why do you prefer Kde to Gnome? (If it's not disturbing question...)  O:)

---

### Post by mindspin on 2005-05-09
This decision is reasonable.
I prefer KDE, cause I use it since kde1 (suse6.0) the look and feel is IMHO great. And I get my daily work done without any trouble. The parts I dislike (konqueror as filemanager and browser, koffice, kmail) re not used by me and thats it.

It makes no sense to teach an old donkey to dance.... ( german proverb)
So there are no ideological/technological reasons.

Before I switched to Kubuntu, I used knoppix HD install on my Notebook for two years, but I was looking for a Distro that is not overloaded with stuff I never need. Actually I would like to install just what I need (like a debian server Installation, starting with "nothing" but the OS), but desktop and server are two different stories. 
My daily work does not allow me to play around with Distros on my working tools. And I do not want to waste my time "learning" a new Windowmanager although there might be a thousand of reasons for using Gnome.

mindspin

---

