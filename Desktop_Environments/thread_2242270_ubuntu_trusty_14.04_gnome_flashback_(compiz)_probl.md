---
title: "ubuntu trusty 14.04 gnome flashback (compiz) problems-solutions"
date: 2014-08-31
forum: Desktop Environments
---

### Post by Claus7 on 2014-08-31
Hello,

I'm creating this thread in order to post the configurations I did while transferring from maverick meerkat 10.10 to ubuntu trusty 14.04 due to a hard drive failure.

Maverick was a really good distribution and I was able to configure many things to my liking. I wanted to do exactly the same thing with ubuntu trusty which supports the flashback desktop environments, and which are close to what maverick used as DE.

In [this]("http://ubuntuforums.org/showthread.php?t=2220264") thread I had posted some questions I had about the new OS, yet the OP of this thread is using metacity, whereas I would like to use compiz. I will continue here my "tweakings", since these will mess with the ones of the metacity flashback thread. 

Now, I will start one by one the problems I faced and, if applicable, with the solutions I was able to find.

1) One of the biggest problems -in order for me to use gnome flashback compiz- was the **blurry screen** I came across. Also, the same thing happened with unity desktop as well, but not with metacity, which led me to the fact that it was a compiz issue and not a graphics card one.

In order to solve this issue, I opened CompizConfig Settings Manager and I tried to uncheck one by one the options that were already selected. At the moment that I unchecked the OpenGL option under the General tab, the entire screen showed only my desktop background and the mouse. Nothing else. I pressed Ctrl+Alt+F1, I entered text mode and I safely shut down my system. When I entered back again my compiz environment, everything was ok. Yet, I will have to check how this will behave, since there were some conflicts under the compiz settings.

graphics card: ati hd 5670 
I had the problem in question both with the driver installed via synaptic and the one from amd's website.

2) Another problem that I had was that I was **not able to see any mounted device on my desktop**. In order to unmount them I had to go via Applications->Accessories->Disks and then I had to power them down.

Solution: from applications->system tools->preferences->tweak tool and then the option desktop on the left, I clicked the option Mounted Volumes. And the problem was solved: I was able to see the mounted volumes, and I was able to eject them while right clicking on them.

3) **Changing icon in the Applications menu**: I wanted to change some icons from the applications menu, without changing in general the theme I had and the set of icons I was using. The options that were to my liking were radiance for window and gtk+, and ubuntu-mono-light for icons.

The ubuntu-mono-light does not include all the icons that is using, which means that some are borrowed from another theme.
The majority (if not all) the themes that are installed and have to do with these type of icons will be found under /usr/share/icons
Now the main "tank" of icons that are used if a theme does not include them is the one with the name Humanity. The applications icons will be found under:
/usr/share/icons/Humanity/categories/24/

For example I wanted to change the applications-games file, which is an svg one. I had to find which icon I wanted (should be a 24 size one), if png it has to be converted to svg using inkscape, and then to be placed under the folder in question. Trying to change the file from Applications->right click->edit menus did not work for me, yet only once. I do not know why. In order for the change to take effect I had to log out and back in. It is a nice idea to back up your original file first.

With the themes that I had installed, I was able to find that there were more themes that were borrowing some of the icons of Humanity: Human, gnome-colors-common.

EDIT: the applications icon is found now under: /usr/share/icons/*title_of_theme*/apps/22/
with the name: start-here.svg

4) I had a **blinking effect**, while I had an opened window full sized and I was placing my cursor on the left hand size of the top panel (Applications). I do not face such and issue in compiz flashback, yet I do not know if it persists on metacity. It is really minor if light themes were used.

5) I **cannot right click on a file and send it to my mobile** phone via bluetooth. I can send files to my mobile, yet I have to open bluetooth, find the file and then send it.

EDIT: see after a couple of posts

6) The **bottom panel bar becomes black**, while set to transparent, on its own.
I have not found any solution to this issue. I will try and see if changing the transparency makes any difference.

7) **Firefox cannot handle flash player videos** as it used to (version 31 - ubuntu trusty). If I use the HTML5 option then in some websites I cannot see videos, and in you tube I cannot set the quality of the video higher than 360.
Opera uses the same adobe flash player as firefox and it plays really nice. Chromium has no problem as well.

EDIT: Firefox version 32.0, flash player 11.2.202.400, plugin ubuntu integration disabled: firefox is working as it should!

And I think that's all. I hope that these will provide some help to those that will switch to ubuntu trusty flashback sessions.

Regards!

---

### Post by grahammechanical on 2014-08-31
You might be interested in Ubuntu Mate. It is being built on Utopic Unicorn (14.10 under development) by one of the main Mate developers. A request has been made for Ubuntu Mate to be officially recognised as a Ubuntu flavour. The word is that the request will be favourably received. I have installed it and although it is beta code it is stable and it is starting to look nice.

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

[https://ubuntu-mate.org/blog/](https://ubuntu-mate.org/blog/)

Regards.

---

### Post by Claus7 on 2014-09-01
Hello,

> **grahammechanical said:**
> You might be interested in Ubuntu Mate.... 

thank you very much for the information. For the time being, things are starting to look the way they used to be with ubuntu flashback, so I'm not thinking to switch distro. Almost always new systems provide some impediments, and I hope that soon enough the vast majority of them will belong to the past.

Regards!

---

### Post by Claus7 on 2014-09-02
Hello,

> **Claus7 said:**
> Hello,

...

5) I **cannot right click on a file and send it to my mobile** phone via bluetooth. I can send files to my mobile, yet I have to open bluetooth, find the file and then send it.

...


In order to solve this issue I tried two things. The one which was successful is the 2nd one of this post. In between I will describe my 1st approach to the problem which led me to know how to handle nautilus scripts for ubuntu trusty.

_Approach 1_

I followed this [link]("http://ubuntuhandbook.org/index.php/2014/04/ubuntu-14-04-add-open-as-rootadministrator-to-context-menu/") and I copied a script about nautilus there.
First I had made it executable:
```
chmod 755 name_of_script
```

Unfortunately, using this way, I was not able to find a working script which will enable the send to bluetooth function.

_Approach 2_

I installed from synaptic the package [COLOR="#0000CD"]nautilus-actions[/COLOR].
Then under Applications->System Tools I chose Nautilus-Actions Configuration Tool

There I clicked File->New Action

The tabs on the right hand side became selectable and I will explain what I chose for each one of them:

**Action**
Ticked only the 1st choice and both context label and Tooltip had the name: Send with bluetooth
with these options you define how you name your action both on the right click menu and on this program. As far as the icon is concerned is completely optional.

Command ([COLOR="#FF0000"]important one[/COLOR])
Label: Default profile
Path: /usr/bin/bluetooth-sendto
Parameters: %f (which means the file selected, if you leave it empty then while executing the command from the nautilus right click menu you will find out that it opens the folder that the file in question belongs to)
working directory: %d

**Execution**
I chose display output in case there is an error to be printed on screen.

Basenames
Basename filter: *
selected the must much one
and the match case on the bottom checked

**Mimetypes**
as before without the option match case

**Folders**
/  
must match one of (if you select the other option, then the command disappears from the nautilus right click menu, because that way you say that no file under root should be taken into consideration)

**Schemes**
*
must match one

**Capabilities**
leave it empty

**Environment**
do not change anything (which means: strictly greater than 0, Always appears, and the rest empty)

**Properties**
Enabled checked

In the end, if you are done, click: File->save
Close the manager and pick up any file you like. It should be sent to your mobile. You do not have to log out and back in.

All the above will work taking into account that your bluetooth configuration is working.

While searching I came across [this post]("http://ubuntuforums.org/showthread.php?t=903213&p=5679606#post5679606"), yet the option %M did not work for me.

Regards!

---

### Post by Claus7 on 2014-09-02
Hello,

> **Claus7 said:**
> Hello,

...
6) The **bottom panel bar becomes black**, while set to transparent, on its own.
I have not found any solution to this issue. I will try and see if changing the transparency makes any difference.

...


I have not tested it a lot, yet it seems that compiz can do some work here. 
(under accessibility: opacity, brightness and saturation)
Just changing directly the transparency of the panels did not work.

Regards!

---

