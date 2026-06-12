---
title: "Installing Cinnamon on 12.04"
date: 2012-06-14
forum: Desktop Environments
---

### Post by piriton on 2012-06-14
[INDENT]I would like to install Cinnamon but run into these nasty errors.  How can I work around this ?

```

add-apt-repository ppa:merlwiz79/cinnamon-ppa
apt-get update
apt-get install cinnamon cinnamon-session cinnamon-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'cinnamon' instead of 'cinnamon-session'
Note, selecting 'cinnamon' instead of 'cinnamon-settings'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libcogl5 (>= 1.7.4) but it is not installable
            Depends: libmuffin0 (>= 1.0.0-0ubuntu1~precise) but it is not going to be installed
            Recommends: gnome-themes-standard but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```[/INDENT]

---

### Post by Frogs Hair on 2012-06-14
Try the following command.```
sudo apt-get -f install
```

---

### Post by piriton on 2012-06-14
Seriously ?

```

# apt-get install -f cinnamon cinnamon-session cinnamon-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'cinnamon' instead of 'cinnamon-session'
Note, selecting 'cinnamon' instead of 'cinnamon-settings'
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 cinnamon : Depends: gir1.2-muffin-3.0 but it is not going to be installed
            Depends: libcogl5 (>= 1.7.4) but it is not installable
            Depends: libmuffin0 (>= 1.0.0-0ubuntu1~precise) but it is not going to be installed
            Recommends: gnome-themes-standard but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

---

### Post by Frogs Hair on 2012-06-14
The command is intended to resolve broken package problems , but this is a 3rd PPA . ```
This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
``` 

You may want to purge the PPA using synaptic or a command provided by the PPA Author and try a different one.

[http://www.unixmen.com/howto-install-cinnamon-on-ubuntu-12-04-precise-pangolin/](http://www.unixmen.com/howto-install-cinnamon-on-ubuntu-12-04-precise-pangolin/)

---

### Post by Rifester on 2012-06-14
That is the old PPA...

---

### Post by piriton on 2012-06-14
I installed Cinnamon from the link below (is that the latest for 12.04 ?), however the menu us at the top of the screen and also the time.

It would be great to find a way to reset it, so that it's at the bottom.

[http://www.unixmen.com/howto-install...cise-pangolin/]("http://www.unixmen.com/howto-install-cinnamon-on-ubuntu-12-04-precise-pangolin/")

Also, how do I configure new themes ?

---

### Post by Frogs Hair on 2012-06-14
There has been no builds for this PPA in 20 weeks.  ppa:merlwiz79/cinnamon-ppa

---

### Post by piriton on 2012-06-14
So I should use this one ?

```
 [COLOR=red]
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable[/COLOR][COLOR=red]
sudo apt-get update[/COLOR][COLOR=red]
sudo apt-get install cinnamon[/COLOR]
```

---

### Post by Frogs Hair on 2012-06-14
When I searched the last one you posted shows up on all the major Linux blogs and was last updated 3 weeks ago. There may be a newer one but haven't found it yet.

---

### Post by piriton on 2012-06-14
Sounds like a yes, that's the best repository to use at present :-)

How do you add themes, and how do you flip over the menu so that it's from the bottom of the screen and not the top ?

[COLOR=red]ppa:gwendal-lebihan-dev/cinnamon-stable[/COLOR]

---

### Post by Frogs Hair on 2012-06-14
Install to file system usr/share/themes(gksudo-nautilus) and use the Cinnamon themes menu.

---

### Post by piriton on 2012-06-15
When I extract the new Cinnamon theme into /usr/share/themes I can see it listed in the "Cinnamon Settings" tool, however when I select the theme, it does not use that particular theme.  Any idea on why this could be ?  The background does not change...

---

### Post by drawkcab on 2012-06-15
I would wait for this:

[http://www.webupd8.org/2012/06/cinnamon-to-get-2d-session-more-new.html](http://www.webupd8.org/2012/06/cinnamon-to-get-2d-session-more-new.html)

---

### Post by BigSilly on 2012-06-15
> **piriton said:**
> When I extract the new Cinnamon theme into /usr/share/themes I can see it listed in the "Cinnamon Settings" tool, however when I select the theme, it does not use that particular theme.  Any idea on why this could be ?  The background does not change...

You need to hit alt-F2, then type r and enter. This resets Cinnamon and reveals the theme. However the background in the thumbnail picture is representative only. You don't get a new background with Cinnamon theme.

---

### Post by piriton on 2012-06-15
The beautiful background pictures in Cinnamon shown on the download webpage are misleading, because everyone assumes they are part of the themes.

With my setup I still dont have the task panel on the right hand side of my screen, and the menu's are at the top of the screen.

The r and at-f2 key combination didnt work for me.

Hmmm I don't think that Cinnamon is anything special, so I can't understand why so many people are raving about it.  Perhaps because the choice of well designed WM's isnt so great right now.

---

