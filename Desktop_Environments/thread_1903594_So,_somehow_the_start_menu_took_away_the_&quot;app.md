---
title: "So, somehow the start menu took away the &quot;apps&quot; button..."
date: 2012-01-02
forum: Desktop Environments
---

### Post by Artic_princess on 2012-01-02
I'm using Ubuntu 11.10 in my netbook and so far, I've been happy with it. However, just a few minutes ago, I restarted and somehow the start menu took away the "apps" button. Instead of 4 buttons for "shorcuts" "apps" "files" and "music", there are only three, and apps is gone!

How do I fix this? :( I installed all the updates btw and everything was working right out of the box when installed a few days ago.

---

### Post by syerges on 2012-01-02
was the "apps" on your dock?

---

### Post by Artic_princess on 2012-01-02
Nope... Like, when you hit the start button and you're supposed to see the 4 options... but the apps button is gone and I can't access my apps.

Sorry, I'm a noob with Linux :(

---

### Post by syerges on 2012-01-02
Start button? If you read this already, I was confused... you mean the dash home?

---

### Post by Artic_princess on 2012-01-02
Uhm... Like I said, I'm a newbie with Ubuntu... there's no need to be rude >:( I want to learn this thing and if I'm gonna be treated as if I was a fool, then I'd rather re-install windows in this thing instead of trying something new, which I REALLY want to do, please! /rant

Ok, when the bar shows up, at the top of it, there's a button with the ubuntu logo, when I scroll the mouse pointer to it, it says "start" (inicio, in spanish, I'm not American). That's why I called it the "Start button", isn't that a bit uhm... obvious? 

Anyway, when you hit that button, it shows 4 options at the bottom: shortcuts, apps, files and music, kinda like a smartphone or whatever. 

Either way, I need to access those apps (firefox, liberoffice and others) and fix the "start menu" or whatever you call it in Ubuntu so I can re-access those apps and have a "smooth" experience.

How do I do this?

---

### Post by syerges on 2012-01-02
You could try installing the CompizConfig Settings Manager from the Ubuntu Software Center... it's suppose to help edit your dash home

---

### Post by Artic_princess on 2012-01-02
How exactly? I mean, like I said, I can't access the software installer 'cause that part of the start menu is GONE! o_o

Seriously, though...

---

### Post by syerges on 2012-01-02
type "Ubuntu Software Center" when you click the start button... you can still access apps that way until you can get it fixed...

:confused:Sorry about my confusion earlier... I'm going to bed soon. Didn't mean to be rude.:(

---

### Post by syerges on 2012-01-02
also, under 'shortcuts' if you click on 'more apps' it bounces you to the 'apps' you are talking about... does it still move you there even though it doesn't show it?

---

### Post by Artic_princess on 2012-01-02
Nope...

I'm showing a screenshot since it seems like we're not getting each other

[IMG]http://img803.imageshack.us/img803/2606/pantallazodel2012010221.png[/IMG]

Can you see that there's an icon missing in the lower part? The "Apps" icon?

I NEED it back! :(

---

### Post by syerges on 2012-01-02
try: alt + f2[FONT=Verdana]
then run in the terminal

[/FONT]sudo apt-get install unity-lens-files unity-lens-music unity-lens-applications

---

### Post by Artic_princess on 2012-01-02
Done... but what does that do? I ask 'cause it didn't change anything. Do I have to reboot or something?

---

### Post by syerges on 2012-01-02
each one of those things on the bottom is called a lens... it installs them... 2 of which were already installed but I copied/pasted it from my commands I use.

---

### Post by syerges on 2012-01-02
quite new myself... reinstall is

sudo apt-get install --reinstall unity-lens-applications

---

### Post by Artic_princess on 2012-01-02
Well, it said it didn't install, eliminate or update anything and the problem still remains :(

EDIT: Testing the 2nd command...

Well, doesn't seems to change anything... Do I restart? What do I do?

---

### Post by ridetheteapot on 2012-01-02
Just fyi you can not *sudo* from the 'Run Application' (the alt f2 thing) dialog, you must use *gksudo*.

I'm still on gnome2 so forgive me if this has changed, but I just thought it might be the easy answer to why nothing was happening.

---

### Post by Artic_princess on 2012-01-02
Dude, I have no idea what you're talking about...

I just wanna be able to access my apps again. I downloaded Ubuntu from the official website and installed it via USB flashdrive, vanilla, as it was.

---

### Post by syerges on 2012-01-02
ok... same thing but you need to do it as like an "administrator" as windows is... that's where the gk comes from so here's the right code and I hope it works ...

gksudo apt-get install --reinstall unity-lens-applications

---

### Post by Artic_princess on 2012-01-02
it says something like "impossible to find the themes engine in pixmap" or something like that... :(

Gosh this IS frustrating!

---

### Post by ridetheteapot on 2012-01-02
sorry i should have said type 'gnome-terminal' into the box you get when you press "alt+f2". Then you can go along and use the apt-get command to reinstall those packages. ie 'sudo apt-get install --reinstall unity-lens-applications' that syerges suggested.

---

### Post by Artic_princess on 2012-01-02
Nope... still nothing! /Angry D:

---

### Post by Artic_princess on 2012-01-02
I just want to know: Is there ANY way to restore the OS to a previous state or to "factory stock" settings? I'm not really in the mood to deal with all this command stuff right now. I've had a TERRIBLE day so far :( This is the cherry of the cake, I swear! D:

---

### Post by ridetheteapot on 2012-01-02
Well I haven't got any experience with the dash or unity so i can't really help but i see unity can be reset with the 'unity --reset' command.
that command you could enter directly into the 'alt f2' prompt. maybe try loging out and back in after. see [http://ubuntuforums.org/showthread.php?p=11581752](http://ubuntuforums.org/showthread.php?p=11581752)
it seemed to *kind of* work there.

-----
restore to factory? just do a fresh install if you want to really keep it simple. because only more commands are involved otherwise.

---

### Post by syerges on 2012-01-02
reinstall it with this

sudo apt-get install --reinstall ubuntu-desktop

this should reinstall your whole start menu not just the part missing

---

### Post by syerges on 2012-01-02
or you have to use the gk so


gksudo apt-get install --reinstall ubuntu-desktop

---

### Post by Artic_princess on 2012-01-02
Sigh... what a "great" day! -_-" It's like somehow karma wanted to play me a VERY bad joke today!

The last command didn't work. So my only real option is to do a clean install? This means I'll have to delete all the data in my hard drive (music, pics and whatnot)?

This morning the HDD in my desktop crapped out, I have backups of all that but... Is there a way to re-install ubuntu without losing those files? :(

---

### Post by ridetheteapot on 2012-01-03
kk bro i feel you. You need to have a terminal open to use the command 'apt-get anything' it cant be run from the alt f2 prompt (it fail when it sees there is no terminal. there are ways to get around this, we will not discuss them).

1. press alt f2
2. enter 'gnome-terminal' into that prompt without the quotes
3. enter the last apt-get command syerges told you there. the ubuntu-desktop one.

---

### Post by Artic_princess on 2012-01-03
BTW alt+f2 opens the "start menu" or whatever you call it in Ubuntu. Instead, I have to hit ctrl+alt+T to open a terminal.

BTW2, it's sis ;)

And, the steps didn't work at all :( Sigh... I'm tired as hell. I'll reinstall everything tomorrow morning, but not now. Is there a way to reinstall everything without losing my music, pics and whatnot? Kinda like fixing the OS or whatever.

---

