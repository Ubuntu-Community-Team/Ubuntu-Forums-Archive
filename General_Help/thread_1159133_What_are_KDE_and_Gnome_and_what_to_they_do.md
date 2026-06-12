---
title: "What are KDE and Gnome and what to they do?"
date: 2009-05-14
forum: General Help
---

### Post by mahela007 on 2009-05-14
I've been using ubuntu for about a year now and I'm almost embarrassed to ask this question.
What is a desktop environment and what does it do? BTW I'd also like to know what a kernel is... Thanks

---

### Post by WatchingThePain on 2009-05-14
Hi,


In my own words I will explain..

If you want you can use Linux without a desktop environment (Gnome and KDE are not the only ones) but you would be using command line.

The Kernel is the core of the operating system. It allocates memory and deals with hardware interrupts and stuff like that.
Kernels can be standard, custom or development.
In software terms your operating system is like an onion with lots of layers with the kernel at the center and the outermost layer being your desktop environment.
(I think the Windows equivalent is a squashed banana afaik lol)

In a way you manipulate the Kernel indirectly when you are using your gui (graphical user interface) i.e. desktop environment.

This is a little surprising (and I'm not sure whether it's good or bad) that someone got through a year without knowing that, from which one could make certain deductions about Ubuntu.

---

### Post by baseface on 2009-05-14
ubuntu: the demise of the linux community.

---

### Post by technotitclan on 2009-05-14
A desktop environment is basically the appearance and layout of your windows, menus and buttons. there a bunch of different ones for Linux and there are different distros of Ubuntu that are built with different enviroments as there default enviroment. like for example Ubuntu - Gnome, Kubuntu - KDE, Xubuntu - Xfce. Those are the major ones. heres a link to a Wikipedia page w/ examples of linux desktop environments.  [http://en.wikipedia.org/wiki/Desktop_environment#Examples_of_desktop_environments]("http://en.wikipedia.org/wiki/Desktop_environment#Examples_of_desktop_environments")

---

### Post by DeMus on 2009-05-14
> **mahela007 said:**
> I've been using ubuntu for about a year now and I'm almost embarrassed to ask this question.
What is a desktop environment and what does it do? BTW I'd also like to know what a kernel is... Thanks

Are you familiar with Dos and Windows?
Well, a kernel is nothing else than the old operating system DOS which handles everything in your computer. When you hit a key on the keyboard it would take care of it, make sure the right program would receive it, show the letter on the monitor by transferring it to the graphical card, send info to a printer when you want to print something, making sure all disc activities are handled the right way, etc.
Nowadays Microsoft claims there is no DOS in Win**DO**w**S**, but that is nonsense. Each operating system needs it, in Linux it is called the kernel.

A desktop environment is like the old Windows 3.1, a graphical shell build on top of DOS. It takes care of the windows, the buttons, the famous mouse. It's a way to make life a lot easier, although here in the Linux world some people hate it. They only want the command line and type instructions like:
cd (change directory)
ls (list contents of directory)
cp a b (copy file a to file b)
Just like in the 80's when we were still using DOS.

In windows you have the right to use one desktop environment, given to you by the man himself. In Linux you can choose if you want Gnome, KDE, XFCE, or any of the others. Each D.E. has its own programs to do things for you, like burn a cd. KDE has K3B, Gnome has Brasero.
It's what you want, what suits you best, what fits best for you.

Does this make it more clear for you?

---

### Post by druhboruch on 2009-05-14
Kernel and desktop environments are computer programs.
The only difference is that kernel is essential and desktop environment is completely obsolete.
:D

---

### Post by uupreti on 2009-05-14
> **druhboruch said:**
> Kernel and desktop environments are computer programs.
The only difference is that kernel is essential and desktop environment is completely obsolete.
:D

I like this one. Short and sweet. In addition I will say kernel is essential core system program. I will say gnome as a application program which may not be crucial thing to have. We can use bash shell which interacts with kernel to make sure everything we hit through the keyword is going to right programs.

---

### Post by trpnblies7 on 2009-05-14
> **baseface said:**
> ubuntu: the demise of the linux community.

On the contrary, I think that if more people are able to use Ubuntu and other Linux distros without having to worry about what a kernel or desktop environment is, the better Linux as a whole will fare in the marketplace. 

Your average Windows user knows how to work his computer, but probably doesn't know a thing about what the Windows registry does. Then there are experts who use Windows and can tweak the registry to their liking.

I don't see anything wrong with having that same type of situation with Linux.

---

### Post by uupreti on 2009-05-14
> **trpnblies7 said:**
> On the contrary, I think that if more people are able to use Ubuntu and other Linux distros without having to worry about what a kernel or desktop environment is, the better Linux as a whole will fare in the marketplace. 

Your average Windows user knows how to work his computer, but probably doesn't know a thing about what the Windows registry does. Then there are experts who use Windows and can tweak the registry to their liking.

I don't see anything wrong with having that same type of situation with Linux.


Exactly I agree with you. But previously almost all Linux distros came with the concept of server administration. That's why people think of using Linux only in server side which has this black and white command prompt rather than nice GUI. But now since couple of years most of the distros are going toward GUI. It's not bad at all coz it's free overall and free things are always good. 

But keep in mind: Using Ubuntu and administrating ubuntu are two different things ( at least in these days). ;)

---

### Post by WatchingThePain on 2009-05-14
> **druhboruch said:**
> Kernel and desktop environments are computer programs.
The only difference is that kernel is essential and desktop environment is completely obsolete.
:D

Nice.
Your explanation is perfect.
I want that in the dictionary.

---

### Post by hyperdude111 on 2009-05-14
The DE is the GUI
The kernel is the core of the system, in charge of compatibility and program installs.

A DE is installed on top of the kernel

---

### Post by fballem on 2009-05-14
To the Original Poster (OP), you have clearly ignited a flamewar - quite accidental on your part.

In Windows, the equivalent of a kernel would be the programs that read and write data to your hard drive, your printer, your network, etc.

In normal circumstances these are in response to things you do with the keyboard and the mouse and are shown on your display in various ways. This is your desktop.

In Windows, the desktop and the kernel are tightly integrated. There are projects, like CygWin that attempt to provide a different desktop for Windows, but for all intents and purposes, Windows includes both the kernel and the desktop, which is why you don't really have a lot of choices in the actual desktop program.

Linux is the kernel. It is responsible for reading and  writing data to the hard drive, etc. In Linux itself, there are limited facilities to display and interact with the system. This is the command line interface - the commands that you type in the terminal. In Windows, the closest equivalent is when you open a Command Prompt and type commands into the Command Prompt.

There are different types of desktop systems - GNOME and KDE being two of the most common - that sits on top of Linux and provides the services to support the interaction with the display, mouse, and keyboard. The information generated by the desktop system is then passed to the kernel for action. The kernel performs the action and updates the desktop.

The key differences among the distributions includes the version of the Linux kernel that they use, the desktop that they use, packaging (used to manage the installation of application programs), and mix of application programs that they may include in the distribution.

For example, Fedora uses Linux, GNOME, RPM packaging, and they tend to use more recent - but potentially less stable - versions of the application programs. Ubuntu uses Linux, GNOME, deb packaging, and they tend to use recent, stable versions of the application programs. OpenSUSE uses Linux, KDE, and RPM packaging. OpenSolaris does not use Linux, but rather OpenSolaris, GNOME, and Image Packaging System (IPS).

You can often choose a different desktop within a distribution. For example, it is possible to install KDE on Fedora or ubuntu, and GNOME on OpenSUSE.

One of the advantages with Linux over Windows is the ability to use different desktop managers that each have specific strengths and challenges.

Hope this helps,

---

### Post by Bandit224 on 2009-05-14
Is it possible to install an rpm pre-compiled package in Ubuntu?

What is the default desktop manager of Ubuntu 9.04?  or did I blindly choose one when installing Ubuntu (which is possible).

---

### Post by mahela007 on 2009-05-14
Thanks for everyones replies... 
> **WatchingThePain said:**
> Hi,



This is a little surprising (and I'm not sure whether it's good or bad) that someone got through a year without knowing that, from which one could make certain deductions about Ubuntu.
  I had a general idea of what a DE MIGHT be but I wasn't certain.. I knew it was not something that was not essential to the PC because it could be changed without uninstalling the OS.. I didn't know if I was right so I posted this thread.

---

### Post by mahela007 on 2009-05-14
> **Bandit224 said:**
> Is it possible to install an rpm pre-compiled package in Ubuntu?

What is the default desktop manager of Ubuntu 9.04?  or did I blindly choose one when installing Ubuntu (which is possible).
Are desktop manager and desktop environment the same thing?

---

### Post by Bandit224 on 2009-05-14
> **mahela007 said:**
> Are desktop manager and desktop environment the same thing?

oops, I think I meant desktop environment.

---

### Post by mahela007 on 2009-05-15
Well, I don't know the answer to your RPM question but I do know that the default DE in ubuntu it's Gnome.. In Kubuntu it's KDE. 
(I'm going to be very hush-hush about which one I like because it seems to ignite threads faster than jet fuel.)
Of course you are free to install another one if you don't like the default DE. There are some guides on the web.

---

### Post by 3startuna on 2009-05-15
> **mahela007 said:**
> I've been using ubuntu for about a year now and I'm almost embarrassed to ask this question.
What is a desktop environment and what does it do? BTW I'd also like to know what a kernel is... Thanks

no offense but If you have to ask you havent been using linux :D

the desktoiop environment is the GUI or graphical user interface. Simular to how windows 98 was setup with dos as the text based and the GUi or windows as the graphical interface

---

### Post by mahela007 on 2009-05-15
You didn't read my previous post.. I said I had a rough idea about what a desktop env was but I wasn't sure if I was correct. Anyway thanks for replying to my initial question.

---

### Post by Keithhed on 2009-05-15
> **uupreti said:**
> Exactly I agree with you. But previously almost all Linux distros came with the concept of server administration. That's why people think of using Linux only in server side which has this black and white command prompt rather than nice GUI. But now since couple of years most of the distros are going toward GUI. It's not bad at all coz it's free overall and free things are always good. 

But keep in mind: Using Ubuntu and administrating ubuntu are two different things ( at least in these days). ;)

+1 to both of you.
nothing wrong with having willing converts to the Linux world.  The ones who don't like it usually run as fast as they can back to Windows

---

### Post by fballem on 2009-05-15
> **Bandit224 said:**
> Is it possible to install an rpm pre-compiled package in Ubuntu?

What is the default desktop manager of Ubuntu 9.04?  or did I blindly choose one when installing Ubuntu (which is possible).

Answers:
[LIST=1]
[*]There is a package called Alien that will allow you to install some programs from an .rpm. The challenge is that every program has specific dependencies, and the dependencies may differ since the package was not intended for ubuntu. In general, I will look first in the repositories, then look to see if there is a .deb repository with the project. I have never had to install a package from an RPM.
[*]The default manager for ubuntu 9.04 is GNOME. You can install KDE (or any of several other desktop managers) into an ubuntu installation, but ubuntu makes distributions where these are defaults. If you click some of the links on the left panel at this site: [http://www.ubuntu.com/products/whatisubuntu](http://www.ubuntu.com/products/whatisubuntu), you'll get an explanation of some of the other 'buntu distributions that are available. For example, KDE is the default desktop for kubuntu.
[/LIST]

Hope this helps,

---

