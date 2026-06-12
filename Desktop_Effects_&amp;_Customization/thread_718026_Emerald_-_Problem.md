---
title: "Emerald - Problem"
date: 2008-03-07
forum: Desktop Effects &amp; Customization
---

### Post by jinxes on 2008-03-07
Hi,

I'am aware that there are many threads regarding emerald, however my question is same and long one and i would appericiate it, if you could help me out.

The trouble I' am having is that, i have installed emerald, as well as compiz and enabled the window effects option. Emerald does not seem to change the theme whatsoever. I have been trying the command "emerald --replace" but still no use and I have ran out of ideas. 

Any suggestions? 

Kind regards

---

### Post by joshuachad on 2008-03-07
Do you get an error message. Also fire up ccsm and click on Window Decorator. In there there is whitespace next to command where you can type in there emerald --replace. Make sure its check first of all. Just curios what kind of vid card do you have? If its like me and its Nvidia you may have to alter your xorg.conf with a command "sudo nvidia-xconfig --add-argb-glx-visuals" assume you have the drivers installed.

---

### Post by Tomana on 2008-03-07
Since you have the Visual Effects working you have the right graphics drivers (good suggestion though)
so try the following ...

make sure you have ran all of these in Terminal

sudo apt-get install emerald
sudo apt-get install libemeraldengine0
sudo apt-get install compizconfig-settings-manager
sudo apt-get install compizconfig-settings-manager python-compizconfig
sudo apt-get install xserver-xgl

just run them all, can't hurt to do so. If you find you need to boot the
computer using safe mode after installing all that stuff then run the following ...

( to remove xgl ) sudo apt-get remove xserver-xgl

To set up Emerald Themes open Emerald Themes Manager,
click on the Theme you want (highlight it) and then use
ALT + F2 and type     emerald --replace    (use two dashes before the word " replace ") 
then click the RUN button

to switch to other Themes immediately, open Emerald Themes Manager
and place the mouse cursor on the window Title Bar and leave it there
then use the keyboard up/down arrows and the Themes should change 
right away

I don't know why I have to place the cursor on the title bar and leave it there, I just know it works

there's some high quality Themes at [http://www.gnome-look.org/index.php?xsortmode=new&xcontentmode=103&page=6]("http://www.gnome-look.org/index.php?xsortmode=new&xcontentmode=103&page=6")

You can also mix and match using the standard Ubuntu Themes (right-click Desktop > Change Desktop Background > Theme
When doing this, the title bar/frame will be from Emerald and the rest will be from the Theme - pretty neat I must say.

---

### Post by joshuachad on 2008-03-07
If he has the right driver why use Xgl?

---

### Post by Tomana on 2008-03-07
Honestly? I don't know.

Oh, I've been wanting to ask, how do you leave a thankyou on someone's account?

---

### Post by BooBooNTZU on 2008-03-08
Here is the funny part about the 'emerald --replace' command.

If you log in as root  , you don't have to type any emerald --replace commands anymore because as soon as you click on a theme it gets applied . That's how it's supposed to work in the first place.

---

### Post by Baelari on 2008-03-08
the 'thank you' button is the little gold star ribbon next to 'quote'

---

### Post by jinxes on 2008-03-08
Hi,

I have ATI RADEON x1950 Series

OpenGL version 2.1.7412

Someone have told me that i shouldn't be installing xserver-xgl, should i still proceed with the following codes that has been provided?

Thanks for all the replies by the way, sorry i could not reply any sooner :)

Kind Regards


/edit

I found out that compiz was the issue, i have played around a bit, removed all the components and after the re-installation, everything worked well. Thanks for all your help, and hope this thread would also help many others.

Regards

---

