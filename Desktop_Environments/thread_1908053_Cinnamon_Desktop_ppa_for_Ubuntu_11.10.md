---
title: "Cinnamon Desktop ppa for Ubuntu 11.10"
date: 2012-01-12
forum: Desktop Environments
---

### Post by recluce on 2012-01-12
This went faster than I thought. Thanks to "merlwiz79" there is now a ppa for the new Cinnamon desktop. Cinnamon is a fork of Gnome 3 and can coexist with Gnome 3 and Unity. Basically, Cinnamon gives you (most) of the look and feel of the classic Gnome 2 desktop, but with the speed of Gnome 3.

If you don't like Unity, this is for you. Be aware that Cinnamon currently lacks a lot of the configuration options that are planned and while Cinnamon is very stable for me, it is still considered in its alpha stage.

To add the Cinnamon desktop in Oneric or Precise:

```

sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon

```

Now log out, select "Cinnamon" as your session on the log-in page and log in again. 

Known issue: Ubuntu Software Center is not on the Cinnamon menu. If you need it, you can manually add a launcher.

---

### Post by jhoo on 2012-01-14
this Ubuntu noob says: I detest Unity so I thought I'd give Cinnamon a whirl, but something seems to have gone amiss.

The installation appeared to go fine, no errors reported.  I logged out, logged back in on a Cinnamon session but .. no Cinnamon desktop.  I think what I've got is some Gnome default: top bar, bottom bar (no "Menu" item on the left), etc. :(

I've looked in the Software Center and it does say I've got the latest (1.1.3) installed.

FWIW, I'm running on an old Pentium 4 system with Matrox G550 graphics.  Maybe I'd defaulting back to some baseline because my system can't handle Cinnamon?  That would be a bummer.  :sad:

Later:

At some point I had installed the new "minty" theme for Cinnamon but couldn't find a way to activate or select it.  Then went into Applications > Other > Advanced Settings and found this, thought it might be relevant:

---

### Post by mhenriday on 2012-01-14
> **recluce said:**
> This went faster than I thought. Thanks to "merlwiz79" there is now a ppa for the new Cinnamon desktop. Cinnamon is a fork of Gnome 3 and can coexist with Gnome 3 and Unity. Basically, Cinnamon gives you (most) of the look and feel of the classic Gnome 2 desktop, but with the speed of Gnome 3.

If you don't like Unity, this is for you. Be aware that Cinnamon currently lacks a lot of the configuration options that are planned and while Cinnamon is very stable for me, it is still considered in its alpha stage.

To add the Cinnamon desktop in Oneric:

```

sudo apt-add-repository ppa:merlwiz79/cinnamon-ppa

sudo aptitude update

sudo aptitude install cinnamon cinnamon-session

sudo aptitude install cinnamon-settings gnome-tweak-tool

```

The last line is for optional components that are recommended. 

Now log out, select "Cinnamon" as your session on the log-in page and log in again. 

Known issue: Ubuntu Software Center is not on the Cinnamon menu. If you need it, you can manually add a launcher.

**Recluce**, might I inquire as to just how one goes about manually adding that Ubuntu Software Centre launcher to the Cinnamon menu ? I've attempted to do it by right-clicking on a Software-Centre window, but the option to add it to the panel doesn't appear....

Henri

---

### Post by recluce on 2012-01-14
> **mhenriday said:**
> **Recluce**, might I inquire as to just how one goes about manually adding that Ubuntu Software Centre launcher to the Cinnamon menu ? I've attempted to do it by right-clicking on a Software-Centre window, but the option to add it to the panel doesn't appear....


Detailed installation instructions (including adding a launcher for the software-center) can be found here:

[http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/](http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/)

---

### Post by recluce on 2012-01-14
> **jhoo said:**
> this Ubuntu noob says: I detest Unity so I thought I'd give Cinnamon a whirl, but something seems to have gone amiss.

The installation appeared to go fine, no errors reported.  I logged out, logged back in on a Cinnamon session but .. no Cinnamon desktop.  I think what I've got is some Gnome default: top bar, bottom bar (no "Menu" item on the left), etc. :(

I've looked in the Software Center and it does say I've got the latest (1.1.3) installed.

FWIW, I'm running on an old Pentium 4 system with Matrox G550 graphics.  Maybe I'd defaulting back to some baseline because my system can't handle Cinnamon?  That would be a bummer.  :sad:



Cinnamon, like Gnome Shell, requires 3D acceleration, which is not available for your graphics card, so you got "Gnome Fallback Mode". Sorry...

---

### Post by jhoo on 2012-01-14
> **recluce said:**
> Cinnamon, like Gnome Shell, requires 3D acceleration, which is not available for your graphics card, so you got "Gnome Fallback Mode". Sorry...

Yup, eventually found something to that effect over at the Mint forums.

Thanks for the reply.

---

### Post by mhenriday on 2012-01-15
> **recluce said:**
> Detailed installation instructions (including adding a launcher for the software-center) can be found here:

[http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/](http://www.linuxbsdos.com/2012/01/05/how-to-install-cinnamon-in-ubuntu-11-10/)

Thanks, **recluce** ; those instructions worked like a charm ! However, the launcher icon that appears on the panel after applying the procedure is the default rhombus ; do you know any simple way to replace it with a more appealing alternative ? In Gnome2, of course, when adding a new launcher to a list, one could right-click the default launcher icon and replace it with an image stored on one's computer ; does there exist a similar option for Cinnamon ?...

Now if only I could move the panel from the bottom to the top - I am told this option is in the works, but when will it be incorporated in the PPA (I'm currently running version *1.1.3-0ubuntu1~oneiric*) ?...

Henri

---

### Post by recluce on 2012-01-15
> **mhenriday said:**
> Thanks, **recluce** ; those instructions worked like a charm ! However, the launcher icon that appears on the panel after applying the procedure is the default rhombus ; do you know any simple way to replace it with a more appealing alternative ? In Gnome2, of course, when adding a new launcher to a list, one could right-click the default launcher icon and replace it with an image stored on one's computer ; does there exist a similar option for Cinnamon ?...

Now if only I could move the panel from the bottom to the top - I am told this option is in the works, but when will it be incorporated in the PPA (I'm currently running version *1.1.3-0ubuntu1~oneiric*) ?...

Henri

As I mentioned, Cinnamon is considered "alpha" or even "early alpha", with the first public release a little over a month ago. For that, it is amazingly stable, but it shows in the configuration options and some rough edges.

Sorry, I do not know how to change the icon - but you could ask in the Cinnamon board over at forums.linuxmint.com with a very good chance for an answer.

As mentioned over at linuxmint: configuration options for the panel are in the works and should not be that far of. I assume that new releases of Cinnamon will be in the ppa a couple of days after they are published, but I don't have a crystal ball :rolleyes:

---

### Post by recluce on 2012-01-15
> **jhoo said:**
> Yup, eventually found something to that effect over at the Mint forums.

Thanks for the reply.

Would there be any chance to get a Nvidia card for your system (assuming it has PCI or AGP slots)? A used card for these slots should not be too expensive.

---

### Post by gentracer on 2012-01-27
I'm hoping someone can help me - I've installed 11.10 and cinnamon on a Dell 1710.  When typing in a terminal screen, it seems that some key sequences cause menus to pop-up - extremely annoying. :( I thought perhaps my palm was hovering over the touchpad, but I have disabled it and the pop-ups continue.  It seems most prevalent with the 'u' key, for example starting to type sudo - after the 'u' the menu opens.  'l' seems to be another popular one.

This happens with Ubuntu, Mint12, cinnamon.  

Any ideas would be appreciated.

Thanks in advance!

---

### Post by tenach on 2012-02-06
> **recluce said:**
> As I mentioned, Cinnamon is considered "alpha" or even "early alpha", with the first public release a little over a month ago. For that, it is amazingly stable, but it shows in the configuration options and some rough edges.

Sorry, I do not know how to change the icon - but you could ask in the Cinnamon board over at forums.linuxmint.com with a very good chance for an answer.

As mentioned over at linuxmint: configuration options for the panel are in the works and should not be that far of. I assume that new releases of Cinnamon will be in the ppa a couple of days after they are published, but I don't have a crystal ball :rolleyes:

Aw, no crystal ball? ;)

As said above, I'd definitely look through the Linux Mint forums. While Cinnamon is great and all, I don't think it's stable enough (nor is it configurable enough) to be much good for me at this point. However, it is showing some amazing promise!

---

### Post by recluce on 2012-02-14
> **tenach said:**
> Aw, no crystal ball? ;)

As said above, I'd definitely look through the Linux Mint forums. While Cinnamon is great and all, I don't think it's stable enough (nor is it configurable enough) to be much good for me at this point. However, it is showing some amazing promise!

For me it is very stable. I agree about the lack of customization options - this is where the "alpha" is visible. I also agree that Cinnamon is very promising, especially if you look at the progress between 1.1.2 and 1.2 in about a month or so.

---

### Post by recluce on 2012-03-15
I updated my first post due to the fact that there is a new PPA now. Also, Precise is now supported. 

Fresh release of Cinnamon: version 1.4, see more about it, including a video, here:

[http://www.webupd8.org/2012/03/cinnamon-14-released-with-new-hot.html](http://www.webupd8.org/2012/03/cinnamon-14-released-with-new-hot.html)

---

### Post by mhenriday on 2012-03-15
**Cinnamon** is getting better and better - more powerful and easier to configure - with every release. Kudos to developer Clement Lefebvre !...

Henri

---

### Post by Inkknife on 2012-03-18
I really like **Cinnamon and want the new version. I ran the aptget commands in the blog linked in **[recluce]("http://ubuntuforums.org/member.php?u=601834")'s post above and the terminal told me I already have the latest version but I know I don't because I have none of the new stuff.
Kind of a noob, what should I do.

---

### Post by recluce on 2012-03-19
> **Inkknife said:**
> I really like **Cinnamon and want the new version. I ran the aptget commands in the blog linked in **[recluce]("http://ubuntuforums.org/member.php?u=601834")'s post above and the terminal told me I already have the latest version but I know I don't because I have none of the new stuff.
Kind of a noob, what should I do.

If you follow this link, you will see that the new 1.4 packages are in the ppa: [http://ubuntuforums.org/showthread.php?t=1908053](http://ubuntuforums.org/showthread.php?t=1908053)

Did you run aptitude update to renew your cache? 
Did you add the new ppa to your sources?

---

### Post by Inkknife on 2012-03-19
> **recluce said:**
> If you follow this link, you will see that the new 1.4 packages are in the ppa: [http://ubuntuforums.org/showthread.php?t=1908053](http://ubuntuforums.org/showthread.php?t=1908053)

Did you run aptitude update to renew your cache? 
Did you add the new ppa to your sources?
  Evidently I did have the right PPA in my list as I did not get any sort of error to that effect and I watched some version check interaction in terminal.
I would appreciate it is you explained how to run aptitude update. Like I said, noob here, climbing the learning curve. :)

---

### Post by Inkknife on 2012-03-19
I worked around the whole problem by remembering I could just go get the .deb at github. Installed smooth as glass, when I was back to my desktop I was pleased to see my theme was 1.4 compatible.
I only poked around a few minutes but all the changes I saw seemed to be improvements.
So far I really like the direction the Cinnamon teams is going.

---

### Post by luisvpikus on 2012-03-22
I installed Cinnamon Desktop, the away it shows in this thread... logged off and chose Cinnamon as new desktop environment and i get graphical bugs on "task bar" and all over the place! :| I really love to try this desktop environment cause i don't like Unity (and don't like the gnome classic either)...

I have installed graphic drivers from ATI (correctly installed)... It works fine with all desktop environments that i have installed, but with cinnamon, it gets very buggy! :S

Any help??

(Sorry for bad english)

---

### Post by Inkknife on 2012-03-22
Does anyone know if it is possible to edit the color of a Cinnamon "menu" background. I installed *New Elements* and really like it except the menu background is very dark and does not match or contrast well with the rest of the theme.
I am no coder by any means but I know how to use GIMP pretty well and am up for editing files.
Any guidance?

---

