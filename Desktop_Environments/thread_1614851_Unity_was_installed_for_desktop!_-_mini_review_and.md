---
title: "Unity was installed for desktop?! - mini review and a question"
date: 2010-11-06
forum: Desktop Environments
---

### Post by slidingClouds on 2010-11-06
Hi all,
I'm really desperate here.

Some intro: I have a  desktop machine. I moved from Win7 to Ubuntu about a year ago, started  with 9.10. I liked Ubuntu for it's simplicity and the power to customize  the OS to what I needed and how I liked it. Although I'm familiar with  the terminal (executing commands only, not reading man pages or editing  files), I prefer GUI.
In that year I've run Ubuntu without a hiccup. And that's why I didn't have a user name up until now.

Yesterday I've upgraded Ubuntu 10.04 to 10.10 and it installed the Unity interface.
Excuse me my "french" but..... OMG! It's a piece of ****!

Let's  put the technical difficulties off to the side right now (not rendering  the icons on the left pane, left pane disappears all together, etc.) --  there's a more serious issue: the UI.

There's no "settings" - if  I want bigger icons for images for example; or if I want to see a list  view of my files instead of icons - I couldn't find any way to customize  it.

File Management - I needed to copy a file from one folder to  another folder (a file from Downloads folder to Downloads\Photos  folder), how difficult should it be?
Well, let's see: 
click Files&Folders
click Downloads - ah, here's the file and the Photos folder
drag the file to the folder - no, no dragging
hmmm, ok... right-click the file to copy - no, no right-clicking
OK.... click Applications
search  for "file" - oh, good there's an application called "File Browser" it  seems that I've been using it with knowing it (always though it was part  of the OS...).
again, click Applications
again search for "file" and open another window of File Browser
now I can move the files
(and a little tid-bit: on the left pane "File Browser" is becoming "File Manager" - all I have to say is: What? How? Why?)

It's  S.L.O.W - when I restart the machine and click on "Application" in the  left pane it takes about 134 seconds (!!!) on average to show the icons.

The  general UI of Unity - long names of applications are trimmed without  tool tips so you get something like "OpenOffic...readsheet" and in  combination with the previous point  - finding the application you want  to run isn't so easy.

Sorry for the long bashing, but I'm really frustrated with the Unity desktop. At least it turned out to be a mini review.
_For the developers of 10.10_  - why, at the installation process, nobody asked me if I want to move  to Unity? I'd say "no" or cancel the upgrade if I knew I'd get Unity (I  never install v1.0... especially on the machine intended for my parents)

_For the community_ - how do I move back to Gnome? Or, at least, are there any tutorials or any other resources to understand Unity?
Because right now, I'm contemplating reformatting the machine and installing win7....

TIA,
Eli

---

### Post by arnavk007 on 2010-11-06
yup you can move back to gnome
type in the terminal
sudo apt-get install ubuntu-desktop

or

you may download ubuntu 10.04 and install it again

---

### Post by slidingClouds on 2010-11-06
> **arnavk007 said:**
> yup you can move back to gnome
type in the terminal
sudo apt-get install ubuntu-desktop

or

you may download ubuntu 10.04 and install it again

Thank you for fast reply.
I've tried  sudo apt-get install ubuntu-desktop as you recommended but it just says "ubuntu-desktop is already the newest version"

How can I re-install ubuntu to replace the current installation?

Eli

---

### Post by DogMatix on 2010-11-06
If ubuntu-desktop is already installed you can switch to it from the login screen.

---

### Post by arnavk007 on 2010-11-06
then you need to type
sudo apt-get install gnome gdm
if still some problem then ask

---

### Post by ajgreeny on 2010-11-06
Bottom right of the login screen there is a Session menu button with a dropdown (actually throwup, I suppose) option. Choose the gnome desktop there.

Done!

PS:  I presume this was the UNR version, as I don't think the desktop version has changed to unity; that is coming in 11.04.  Certainly my install of 10.10 does not have unity.

I also think perhaps your upgrade to 10.10 did not go well, if the system has suddenly become so slow.  Another try may be worth doing with a clean install this time.

---

### Post by slidingClouds on 2010-11-06
Yay!!!

Thank you all so very much!

Indeed, in the log in screen it was set to open the netbook edition for all user (don't know why that was the default). I've changed it to Desktop and normality recommenced once again (@ajgreeny - now the system is back up to speed, so I guess the slow preformance something in Unity - maybe my GPU is not supported as it's not a netbook GPU and that is causing the slow-down).

Anyway, while fixing the desktop issue, I noticed that grub is loading version 23 of the kernel. When I tried to load version 25 it loaded 10.04 version of Ubuntu.
Should I be concerned? Should I just leave it as it is? Should I open another thread for this question?

Again, thanks a lot everyone,
Eli

---

### Post by arnavk007 on 2010-11-06
Don't worry about the kernel unless you have some need which would be fixed by updating the kernel
enjoy gnome
also mark the thread as solved
oh this is my hundredth post

---

### Post by NagWolf on 2010-12-03
Unity = Mixed Emotions

Firstly - I'm holding thumbs for the Ubuntu developers... moving full-on over to Unity as the Primary DE on 11.04 onwards is a brave move, for one reason only, seems there's a lot of work that still needs to be done on this DE. Hardware support for different Touch Screens, Bugs like the mentioned tool tips and Long Application names that gets trimmed off and for instance in my case, after installing Unity (Netbook Edition) onto my Intel chipset laptop to give it a test drive, I only see my Wallpaper, Conky setup and Pidgin that Auto opens on login... nothing further, no R-Click mouse menus nothing.
I'm all for this move to unity, seeing everybody nowadays are getting used to SmartPhones and iPods and all the other Apple inspired devices, moving to a more "Touchscreen-esque" DE will make Ubuntu a familiar environment for anyone that owns a Cellphone or iPod.
I like the idea of using my any of my Desktops and laptops as if I'm Tom Cruise in Minority Report... Touch touch wipe etc... and years before any other mainstream OS will do it for their Drones :D

Good luck guys and to all the Doom Prophets: Keep with the times guys

---

