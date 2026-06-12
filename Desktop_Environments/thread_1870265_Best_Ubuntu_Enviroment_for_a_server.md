---
title: "Best Ubuntu Enviroment for a server?"
date: 2011-10-27
forum: Desktop Environments
---

### Post by Huntereb on 2011-10-27
Hello, I just got finished with a post regarding making my server run faster on Ubuntu. Now I would like to know this, what is the best Ubuntu Enviroment that uses as little memory as possible? I still want a GUI, so I can navigate easier, but just a GUI that isn't so detailed it takes up 75% of your memory (not being literal) like regular Ubuntu. I have heard of enviroments called Kubuntu and Xubuntu, but are there any others that would suit my needs? If not, then which of those two are better?
 
I do not want to use Ubuntu Server, like I said, I need a GUI that is at least navigatable.
 
Thank you!
 
[SIZE=1]P.S. My server is an SRCDS server running a Garry's Mod game, it is executed in a terminal. I also use another small program that automatically sets the NICE. So I need to be able to run 2 terminal windows, and use as little memory as possible with a GUI.[/SIZE]

---

### Post by Bucky Ball on 2011-10-27
Always go with the LTS (long-term support) releases. 10.04 LTS is current and the server version is supported until 2015.

Not sure what the confusion is with Ubuntu Server. It has everything you need to setup a server. You just need to install the desktop environment if you want one. That easy. 

```
sudo apt-get xfce4
```Will install the Xfce4 desktop environment, used by Xubuntu, but none of the apps, just the DE. Fully navigable. That is how I would go. That is the lightest of those you mentioned (don't go anywhere near Kubuntu for what you are after - uses KDE DE incidentally).

Have no idea what an SRCDS server is so have no idea whether you can install any of these DEs. The fastest you are going to get is to do a CLI install and just install the packages you need for your server, nothing else, and you do this manually (you would obviously need to put in some time researching this option). I did an install like this on one of my partitions and was getting to the login screen in 12 seconds.

Lxde is apparently lighter again. Good luck.

---

### Post by gsmanners on 2011-10-27
If you want your server to not use much memory, but you still want to be able to have a graphical environment, I think starting out with openbox or fluxbox is a good idea. I mean, why install a whole desktop on your server? Then, if you want a panel, install fbpanel or lxpanel or tint2 (whatever gets the job done).

---

### Post by Huntereb on 2011-10-27
So if I install Ubuntu Server, and then install Xfce4 from the command line, I just reboot and it will have and interface? I see that it is able to install packages, so I can install all of the things I need for making my browsing simpler. But is that all? Afetr Getting Ubuntu Server, typing that, and then rebooting I would have an interface?
 
I am hoping that the interface will have a built in internet browser, a Terminal program, and I'm guessing it also has USB support. I've never even looked into using Ubuntu Server because I thought it was just a terminal, but if it has all of that after installing Xubuntu interface then i'm all in for this. Please just tell me now that it will be able to do those things before I wipe my hard drive and restart on everything...
 
Also, SRCDS is a program used to run a Source Dedicated Server. Such as the ones you are able to connect to in games like "Team Fortress 2", and "Counter Strike Source". So basically it's just a game server.

---

### Post by fullmoonguru on 2011-10-27
I beleive the answer to your last post is yes.  The only thing I'm not sure about is the resident browser, but I think it's there.  if it's not there when you get to the desktop, just install Chromium (or whatever your preference).

---

### Post by Lars Noodén on 2011-10-27
You can use a plain Window Manager instead of a full-blown Desktop Environment.  Openbox and FVWM-Crystal come to mind.  That way fewer resources will be wasted on the GUI.

In the long run it pays to learn your way around the shell as soon as you can.  That makes your work very much easier and more powerful once you've learned how.  See this thread about [beginner's resources for the shell](http://ubuntuforums.org/showthread.php?t=1869906) for starting points.

---

### Post by haqking on 2011-10-27
Ubuntu Server comes without a GUI for a reason, leave it that way and administer it using ssh, if you want the graphical tools then ssh -X

IMHO

You say in your OP "you do not want to use Ubuntu Server" what does that mean ?

Why not just use a desktop edition with whatever services you need instead.

A server is not defined by the fact it is server edition, a server is defined by the fact it is providing server services

---

### Post by Huntereb on 2011-10-27
So how would I install Openbox or FVWM-Crystal when I start Ubuntu Server? And which one is better in preference?
 
And ok I see, the gui will have a terminal, but no browser. But I can install a browser using the "apt get", cool.
 
So lemme get this striaght, if I do this it will install a gui that includes a Terminal, has the ability to install Applications from the command line (the Terminal), and uses as little memory as possible. If that's what it does then that's all I need.

---

### Post by collisionystm on 2011-10-27
> **Huntereb said:**
> Hello, I just got finished with a post regarding making my server run faster on Ubuntu. Now I would like to know this, what is the best Ubuntu Enviroment that uses as little memory as possible? I still want a GUI, so I can navigate easier, but just a GUI that isn't so detailed it takes up 75% of your memory (not being literal) like regular Ubuntu. I have heard of enviroments called Kubuntu and Xubuntu, but are there any others that would suit my needs? If not, then which of those two are better?
 
I do not want to use Ubuntu Server, like I said, I need a GUI that is at least navigatable.
 
Thank you!
 
[SIZE=1]P.S. My server is an SRCDS server running a Garry's Mod game, it is executed in a terminal. I also use another small program that automatically sets the NICE. So I need to be able to run 2 terminal windows, and use as little memory as possible with a GUI.[/SIZE]


Install lxde. It is extremely light and only about 50mb to download

```
sudo apt-get install lxde
```

restart your server

I am sure you will find this is your best choice.

---

### Post by docbop on 2011-10-27
IS there a way to not load a GUI on the server, but ssh -X in and run a GUI on remote sessions?

---

### Post by haqking on 2011-10-27
> **docbop said:**
> IS there a way to not load a GUI on the server, but ssh -X in and run a GUI on remote sessions?

yes, dont install one ;-)

a server comes without a GUI in the first place.

---

### Post by Huntereb on 2011-10-27
I think I'm gonna go against you and install one. I'm a noob to Ubuntu, and I don't want to make this harder for me then it has to be. I guess I will try lxde, it looks really easy to use, undetailed, and it has everything I need.
 
It has a Terminal, and many file browsing utilities! Exactly what I wanted!
 
Thank you, I will definatly try this when I can get to my computer on Tuesday.

---

### Post by WasMeHere on 2011-10-27
Hello again Huntereb,

It is good that you plan to wait for a few days until you start installing a new system. That gives you a chance to consider the pros and cons of the different solutions that are suggested in this thread.

Good luck and have fun :-)
Olle

---

### Post by Lars Noodén on 2011-10-27
> **docbop said:**
> IS there a way to not load a GUI on the server, but ssh -X in and run a GUI on remote sessions?

Yes.  That way you can still run a lot of graphical tools like file managers and browsers.  Best it works towards making SSH the main way of interacting with the server.  In the long run that is by far the best.

---

### Post by Huntereb on 2011-10-27
> **Olle Wiklund said:**
> Hello again Huntereb,
 
It is good that you plan to wait for a few days until you start installing a new system. That gives you a chance to consider the pros and cons of the different solutions that are suggested in this thread.
 
Good luck and have fun :-)
Olle
 
Oh hello! And thank you again for your help on my last topic. Yes I will be looking into the options that where said on this forum before doing so, I want to be sure it will be as simple and lightweight as possible. So far the ones posted look very good, and very simple to use.

---

### Post by Huntereb on 2011-11-02
> **collisionystm said:**
> Install lxde. It is extremely light and only about 50mb to download
 
```
sudo apt-get install lxde
```
 
restart your server
 
I am sure you will find this is your best choice.
 
I did this last night, and I am VERY pleased with the results! In fact, the system starts up in almost 30 seconds! Every application I used on Ubuntu works exactly the same on LXDE, and even start faster than before!
 
This is exactly what I wanted, an operating sytem that barley uses any memory, but lets me navigate easily. I was having some problems with the server not being loaded because of something with the OS being 64 bit, but I think I have gotten that resolved.
 
Anyway, thank you! It's perfect!

---

