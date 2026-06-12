---
title: "Taskbar that doesnt require compiz/core"
date: 2009-01-02
forum: General Help
---

### Post by josephcohen on 2009-01-02
Because of my computer i had to un-install compiz and compiz core (i think because of my video card) for ubuntu which was very unfortunate.

So i tried to install avant window navigator not reallizing in needed compiz core to work.

Does anyone know of a task bar/mac like bar thing that goes at the bottom of the screen that doesnt involve or require compiz or compiz core?!

---

### Post by PmDematagoda on 2009-01-02
Cairo Dock may do the trick, instructions on installing it can be found [here]("https://help.ubuntu.com/community/CairoDock").

---

### Post by josephcohen on 2009-01-02
I installed it using the first method and it it worked but something very odd is happening.

It has a black background behind the whole dock.
Im guessing it is again related to the fact that i dont have compiz or compiz core.

---

### Post by sigurnjak on 2009-01-02
I think you need to enable compositing for metacity to remove black background if you are not using compiz .

---

### Post by BLTicklemonster on 2009-01-02
> **sigurnjak said:**
> I think you need to enable compositing for metacity to remove black background if you are not using compiz .

How do you do that?

And Gdesklets has a nice taskbar app in it somewhere.

---

### Post by sigurnjak on 2009-01-02
Better explained than i would :
[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

---

### Post by Forlong on 2009-01-02
You might want to give **Simdock** a try, it's in the repos:
```
sudo apt-get install simdock
```

---

### Post by Shazaam on 2009-01-02
wbar is another one that doesn't need compiz...
[http://www.google.com/search?hl=en&as_q=&as_epq=wbar&as_oq=Ubuntu&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images](http://www.google.com/search?hl=en&as_q=&as_epq=wbar&as_oq=Ubuntu&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images)

---

### Post by Forlong on 2009-01-02
As far as I know wbar is a dead project. There hasn't been an update in two years.

But as I see now, Simdock is not much better off... but at least it's easily installable.

---

### Post by fabounet on 2009-01-02
if you don't run a compositor you can't have transparency, means you will have a black background.
activate the fake transparency in the Cairo-Dock's config to get rid of it (in the System tab).

---

### Post by josephcohen on 2009-01-02
I tried sim dock but Im having a problem.

I right click the dock and click add launcher but and then
when I put everything in it just says "error, could not load background image" 
So all it does is display open programs but I cant place programs there and
click on them when I want.

And I guess I could try gdesklets but I dont want desklets. Just the bar.

---

### Post by Forlong on 2009-01-03
I fiddled around with Simdock and it indeed seems to be broken, as it doesn't save the newly added icons.

A workaround is configuring the config file yourself. It is located in your home directory in a hidden folder called **.SimDock**

You can open it like this (on GNOME):
```
gedit ~/.SimDock/launchers.xml
```
There you have to add new launchers like this:
```
<Program>
  <SimDock>
    <path>/usr/bin/firefox</path>
    <icon>/usr/share/pixmaps/firefox-3.0.png</icon>
    <description>Firefox web browser</description>
    <name>Firefox</name>
  </SimDock>
  <SimDock>
    <path>/usr/bin/gedit</path>
    <icon>/usr/share/icons/gnome/32x32/apps/text-editor.png</icon>
  </SimDock>
  <SimDock>
    <path>gnome-terminal</path>
    <icon>/usr/share/icons/gnome/32x32/apps/gnome-terminal.png</icon>
  </SimDock>
</Program>
```
You see, a new launcher begins with the <SimDock> tag and ends with </SimDock>
All you need to add is the path to the application (in most cases in /usr/bin) but you do not have to give the exact path.
As you can see **gnome-terminal** is enough if it's in /usr/bin

It's vital to add an icon path, though. Nearly any image filetype will do (except for .svg, which is actually pretty unfortunate).
Many application icons are stored in /usr/share/pixmaps or under /usr/share/icons


Hope this helps.

---

### Post by BLTicklemonster on 2009-01-03
> **fabounet said:**
> if you don't run a compositor you can't have transparency, means you will have a black background.
activate the fake transparency in the Cairo-Dock's config to get rid of it (in the System tab).

On the contrary, in gdesklets, there is a taskbar that you can edit the background on to be transparent.

---

### Post by josephcohen on 2009-01-03
Very helpful forlong thank you!
Is there a way to add a launcher of go to desktop?

---

### Post by Forlong on 2009-01-04
> **josephcohen said:**
> Is there a way to add a launcher of go to desktop?
No, I'm afraid that's not possible.

---

### Post by zika on 2009-01-04
> **BLTicklemonster said:**
> How do you do that?

Alt-F2->gconf-editor->Run->apps->metacity->general->compositing_manager

---

