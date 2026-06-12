---
title: "Updates available..."
date: 2006-04-02
forum: Desktop Environments
---

### Post by Martjc on 2006-04-02
...I am new to Linux, [no, newer than that] and want to learn more. I have installed version 5.10 and there is a big red splodge on top right, telling me that there are 75 updates available.
I clicked it, input my password, as asked and tried to download the updates.  Nothing happened!  On subsequent attempts to access, I was not even asked for a password.
I dearly want to understand what is happening here and appreciate any help.  I can be reached at [email]mjchristy@hotmail.com[/email].

Thanks]

---

### Post by anodizer on 2006-04-02
Open your terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
```

And see what happens. Probably it will give you an error, or wrong IP resolving, like [10.0.0.1]
Also when you type your password, you will not be asked again for 15 minutes, so thats normal.

---

### Post by eriefisher on 2006-04-02
You can also use Synaptic. Open it up, enter your password, click reload, once thats done click on "mark all upgrades" then click apply. This will download all the updates and install them. Hope this helps.

eriefisher

---

### Post by Martjc on 2006-04-04
[QUOTE=anodizer]Open your terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
```

And see what happens. Probably it will give you an error, or wrong IP resolving, like [10.0.0.1]
Also when you type your password, you will not be asked again for 15 minutes, so thats normal.[/QUOTE]

Can't find Terminal!  I said I was new!!

---

### Post by Martjc on 2006-04-04
[QUOTE=eriefisher]You can also use Synaptic. Open it up, enter your password, click reload, once thats done click on "mark all upgrades" then click apply. This will download all the updates and install them. Hope this helps.

eriefisher[/QUOTE]

Found Synaptic in [system], [administration]
Clicked on it - heard a drumbeat but nothing else happens.  I'm stumped!!!

---

### Post by Tosa on 2006-04-04
The same thing was happening to me to... Then it stopped, I don't know why.
It happened with all the apps that needed password to run. Actually they worked, but with a big lag. As you said nothing would happen, but after several minutes the app, that I've forgotten of in the mean time, would pop up...

---

### Post by Martjc on 2006-04-05
Thanks Anodizer - found the terminal and tried your code - nothing!

Erifisher - Synaptic does not work either!

Thanks Tosa, will try just waiting there - who knows?  Still stumped!

---

### Post by nocturn on 2006-04-05
Moved to the ubuntu forum, I think it is better suited here.

---

### Post by Edward The Bonobo on 2006-04-05
To answer the original question (maybe):

What I didn't know when I was a newbie was that Ubuntu is very clever in the way that it installs software - whether new or upgrades.  It keeps 'Repositories' of all the packages you need.  You get updates or new stuff by connecting to these over the internet, via the update manager, Synaptic, or a package called apt-get which you run by typing in a terminal window.

There's stuff you'll need to know about, like how to get Ubuntu to look at the right Repositories on the web.  With what I've told you so far...you may now be able to make sense of the Starter Guide's info. on installing applications: [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

I hope I'm not being patronising here.  I went through the same experience myself.  It can be difficult to remember what new concepts users don't know - often we don't even know what questions to ask!  I believe that what Ubuntu really needs is some kind of conceptual, high-level guide for the real newbie...and maybe with a bit more experience I'll be able to write one!

---

### Post by Nordoelum on 2006-04-05
[quote=Martjc]...I am new to Linux, [no, newer than that] and want to learn more. I have installed version 5.10 and there is a big red splodge on top right, telling me that there are 75 updates available.
I clicked it, input my password, as asked and tried to download the updates. Nothing happened! On subsequent attempts to access, I was not even asked for a password.
I dearly want to understand what is happening here and appreciate any help. I can be reached at [EMAIL="mjchristy@hotmail.com"]mjchristy@hotmail.com[/EMAIL].
 
Thanks][/quote]
Could you run:
```
 
$ sudo gedit /etc/apt/sources.list

```
and post it on the forum?

---

### Post by Martjc on 2006-04-05
[QUOTE=Edward The Bonobo]To answer the original question (maybe):

What I didn't know when I was a newbie was that Ubuntu is very clever in the way that it installs software - whether new or upgrades.  It keeps 'Repositories' of all the packages you need.  You get updates or new stuff by connecting to these over the internet, via the update manager, Synaptic, or a package called apt-get which you run by typing in a terminal window.

There's stuff you'll need to know about, like how to get Ubuntu to look at the right Repositories on the web.  With what I've told you so far...you may now be able to make sense of the Starter Guide's info. on installing applications: [http://help.ubuntu.com/starterguide/C/index.html](http://help.ubuntu.com/starterguide/C/index.html)

I hope I'm not being patronising here.  I went through the same experience myself.  It can be difficult to remember what new concepts users don't know - often we don't even know what questions to ask!  I believe that what Ubuntu really needs is some kind of conceptual, high-level guide for the real newbie...and maybe with a bit more experience I'll be able to write one![/QUOTE]
Thanks Edward, I thought I understood what you've just said - must read that guide!  Surely, one would think, the upgrade manager should be able to handle those repositories itself on a look-up basis - otherwise what's it managing?  Nothing except confusion!

I'll try the guide.

---

