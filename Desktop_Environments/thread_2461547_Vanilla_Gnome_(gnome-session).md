---
title: "Vanilla Gnome (gnome-session)"
date: 2021-05-02
forum: Desktop Environments
---

### Post by dddman on 2021-05-02
I'm trying to run the Vanilla Gnome desktop with instructions from here.

[https://linuxconfig.org/how-to-install-minimal-gnome-on-ubuntu-20-04-focal-fossa-linux](https://linuxconfig.org/how-to-install-minimal-gnome-on-ubuntu-20-04-focal-fossa-linux)

When I enter the command to install the gnome-session and gnome-terminal it comes back with a already installed message.  OK, where is it? I haven't found it.

Googling tells me the command "gnome-session" should open it if there is a bin file.  Running the command "gnome-session" sends me back to the login screen but no option to run vanilla gnome.

Edit
This link says gdm3 needs to be installed, but again I get the already installed message.
[https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa)

I do have a option to switch to "Gnome Classic" at login, but this has never worked and only leads to a useless black screen.  Could it be the one?

---

### Post by dddman on 2021-05-02
Edit#2
Gnome Classis needs the gnome-shell-extensions which again show already installed.  
[http://linuxhalwa.blogspot.com/2020/04/install-gnome-classic-desktop-on-ubuntu.html](http://linuxhalwa.blogspot.com/2020/04/install-gnome-classic-desktop-on-ubuntu.html)

Its would also be nice to get this working.

Thats it for tonight.

---

### Post by grahammechanical on 2021-05-03
There is a misunderstanding here and it is the authors of that web site that do not understand.

They say this for step 2 to install the full Gnome desktop on Ubuntu 20.04

> Next, use the tasksel command to install GNOME desktop: $ sudo tasksel install ubuntu-desktop

How can the "full," "Vanilla" Gnome desktop be installed by running a command that installs the Ubuntu Desktop?

Ubuntu 20.04 is built on the Gnome 3 desktop environment and it runs the Gnome 3 shell as a user interface. That is why you are getting the already installed message. The terminal in Ubuntu is Gnome terminal.

If the Gnome shell extensions are already installed then please confirm that when you get to the log in screen and press enter to allow you to type in your user password, that you do not see the cog icon in the bottom right hand corner?

The cog icon on Ubuntu 20.04 should give us an option to load Ubuntu with Wayland, Ubuntu on the X server and Gnome and Gnome classic.

Regards

---

### Post by dddman on 2021-05-03
Hello

Yes I do have that.  Old pic, disregard the arrow.

[ATTACH=CONFIG]288420[/ATTACH]

Gnome classic is nothing but a black screen; no gnome vanilla.

---

### Post by deadflowr on 2021-05-03
For vanilla gnome it's the vanilla-gnome-desktop package.
For minimal gnome it's gnome-core.

vanilla-gnome-desktop is built to be like the older Ubuntu Gnome flavor's desktop, which was a pure gnome experience.
gnome-core is gnome stripped down to the very basics.

Sidenote: I think many users would find this quote 
> It is ideal for servers with minimal GUI applications requirement.
from the link to be quite comical.
As not many users who run servers (outside of Ubuntu developers maybe) would ever run it as an alternative desktop.
Instead they would use much lighter desktops, or window managers (like i3 or fvwm or openbox or fluxbox or other)
As no matter how it's installed gnome is always very heavy, regardless of what apps are installed.

---

### Post by dddman on 2021-05-03
Not running any servers here, just playing with different desktops.

I ran across a redit post that said to install the package vanilla-gnome-desktop.  So I did and am currently on Gnome Classic desktop.  It works now!  No dead black screen.  It's  similar in layout, but puts a different twist on things.  Has a pull down menu that I already don't like.  

For me, that ends the hunt for Vanilla Gnome.

Thank you both for the input.

---

