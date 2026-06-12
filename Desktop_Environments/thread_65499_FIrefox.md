---
title: "FIrefox"
date: 2005-09-14
forum: Desktop Environments
---

### Post by x__dark on 2005-09-14
I'm having problems installing firefox and gtk+. I keep getting errors and shit.

&I would post them here, but it doesn't seem to want to let me past. Basically the FIrefox 1.0.6 install said I needed libgtk-x11-2.0.so.0, so I get GTK+ and when I go to install it, it says I need a C Compiler, so I get Gcc, installs just fine via apt-get. Then I go to install GTK+ again and it says I need pkg-config, which I get and it wont install. . . it says "lib/cpp/" fails sanity check. 

what do i do? i'm new to linux. lol help me! O:)

---

### Post by ltmon on 2005-09-14
Hi,

Best not to use the firefox installer from the Mozilla site, unless you really need to for some reason.  The Ubuntu devs have already made a nice packaged version for you.

Quickest way:

- Open a terminal
- type:

sudo apt-get install mozilla-firefox

- type your password
- wait for download and install to complete

Slightly harder, but prettier, way:

- Open "Kynaptic" (Kmenu -> System -> Package Manager (kynaptic)
- In the menu bar: Edit -> Find
- Type "mozilla-firefox"
- Right click on the package, and select "Install"
- Click on the "Commit Changes" button (that's the one on the far right of the toolbar)
- Wait for download and install to complete.

Hope that helps :)

L.

---

### Post by x__dark on 2005-09-14
[QUOTE=ltmon]Hi,

Best not to use the firefox installer from the Mozilla site, unless you really need to for some reason.  The Ubuntu devs have already made a nice packaged version for you.

Quickest way:

- Open a terminal
- type:

sudo apt-get install mozilla-firefox

- type your password
- wait for download and install to complete

Slightly harder, but prettier, way:

- Open "Kynaptic" (Kmenu -> System -> Package Manager (kynaptic)
- In the menu bar: Edit -> Find
- Type "mozilla-firefox"
- Right click on the package, and select "Install"
- Click on the "Commit Changes" button (that's the one on the far right of the toolbar)
- Wait for download and install to complete.

Hope that helps :)

L.[/QUOTE]
 Mine doesn't seem to have the  mozilla-firefox package when i search in kynaptic.

---

### Post by x__dark on 2005-09-14
[QUOTE=ltmon]Hi,

Best not to use the firefox installer from the Mozilla site, unless you really need to for some reason.  The Ubuntu devs have already made a nice packaged version for you.

Quickest way:

- Open a terminal
- type:

sudo apt-get install mozilla-firefox

- type your password
- wait for download and install to complete

Slightly harder, but prettier, way:

- Open "Kynaptic" (Kmenu -> System -> Package Manager (kynaptic)
- In the menu bar: Edit -> Find
- Type "mozilla-firefox"
- Right click on the package, and select "Install"
- Click on the "Commit Changes" button (that's the one on the far right of the toolbar)
- Wait for download and install to complete.

Hope that helps :)

L.[/QUOTE]
 Mine doesn't seem to have the  mozilla-firefox package when i search in kynaptic.

jeremiah@Dark:~$ sudo apt-get install mozilla-firefox
Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate

THat's what it reads from konsole.

---

### Post by f1dave on 2005-09-14
Try sudo apt-get firefox then

---

### Post by treris on 2005-09-14
Are you sure you have all the repositories you need? Correct me if I'm wrong but I believe that the latest versions of firefox arent in the 'normal' repositories, have you tried the backport repositories yet?

with the help of those I had no trouble whatsoever installing firefox 1.0.6

hope that helps

---

### Post by Slackitude on 2005-09-14
The first thing I'd do is 
sudo apt-get update
sudo apt-get install synaptic
Kynaptic is an interesting effort but much as I like the KDE desktop synaptic blows it away. Than open synaptic (I'm assuming you're more comfortable with a gui, if not you can do all this from the command line) and look under "settings" "repositories" and enable most if not all of them, sorry but I'm not sure which one has FireFox. Than hit "reload" and after that you ought to be able to find and install FireFox. Don't be startled if it wants to install half of the Gnome desktop along with it though, I know on mine it seemed to have a ridiculous amount of stuff that wanted to tag along for the ride. Hope that helps.

---

### Post by x__dark on 2005-09-14
I get the same error as when I apt-get firefox.

jeremiah@Dark:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate

---

### Post by treris on 2005-09-14
That is weird, so you can't even get synaptic installed?? could you maybe list your etc/apt/sources.list file?? 
I see you're using the command line for installing stuff, have you tried installing anything with kynaptic? I remember that when I first installed kubuntu I used kynaptic to install synaptic and then started installing all the proggies that make computing more fun.

---

### Post by OBnascar on 2005-09-17
x__dark, I have been following this post but looks like it is dead now. I can not get Firefox installed either, no matter what method I try. It is almost worth switching to ububtu 5.04, I installed that on a different computer and that has Firefox installed as the default browser. I HATE Konqueror !

Have you got it installed since this post ? 

I don't understand what treris is saying in the quote below, do you ?


[COLOR=Blue]treris wrote: 

Are you sure you have all the repositories you need? Correct me if I'm wrong but I believe that the latest versions of firefox arent in the 'normal' repositories, have you tried the backport repositories yet?

with the help of those I had no trouble whatsoever installing firefox 1.0.6

hope that helps[/COLOR]

---

