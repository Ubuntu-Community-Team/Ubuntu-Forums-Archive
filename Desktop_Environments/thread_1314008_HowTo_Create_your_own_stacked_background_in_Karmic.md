---
title: "HowTo: Create your own stacked background in Karmic"
date: 2009-11-04
forum: Desktop Environments
---

### Post by ackey on 2009-11-04
I absolutely love the effect of the "stacked background" space theme in Karmic.  I couldn't find a description anywhere of how to do it, so I thought I'd share what I've figured out.

I don't know if this will work in any version of Ubuntu before Karmic.

When you go to System->Preferences->Appearance and click on the background tab, you see a panel of available backgrounds.  A default one on Karmic is a space background, which has a different type of icon than the other ones.  If you select it an arrow appears and you can see all of the pictures in the stack.  I was happily surprised when a bit after selecting the background I saw my wallpaper change.

This affect is done through an xml configuration file.  If you try to "drag" the icon for the space wallpaper to your desktop, it appears as an xml file.  You can modify this with your own pictures.

The beginning of the file looks like:
```

<background>
  <starttime>
   <year>2009</year>
   <month>08</month>
   <day>04</day>
   <hour>00</hour>
   <minute>00</minute>
   <second>00</second>
  </starttime>
  <!-- This animation will start at midnight. -->
  <static>
   <duration>1795.0</duration>
   <file>/usr/share/backgrounds/cosmos/cloud.jpg</file>
  </static>
  <transition>
   <duration>5.0</duration>
   <from>/usr/share/backgrounds/cosmos/cloud.jpg</from>
   <to>/usr/share/backgrounds/cosmos/comet.jpg</to>
  </transition>

```

I think you can ignore the first part about start time - I just left it as it is.  The important part is the static and transition tags.  Each <static> tag defines one of the pictures that will show.  Insert the location of the file you want to use in the <file> tags.  The <transition> tag then defines the transition that occurs as one image rotates to another.  On my system I didn't see a change in behaviour due to changing the duration length.  Taking out the transition tag seemed to make it not change at all.  The last <transition> should come back to the first image, like so:

```

 <static>
  <duration>1795.0</duration>
  <file>/usr/share/backgrounds/cosmos/whirlpool.jpg</file>
 </static>
 <transition>
  <duration>5.0</duration>
  <from>/usr/share/backgrounds/cosmos/whirlpool.jpg</from>
  <to>/usr/share/backgrounds/cosmos/cloud.jpg</to>
 </transition>
</background>

```

Make sure you close the tags out at the end.  I've attached a version I've modified that should be a good starting point.  

Now, to add it as a background, go to the appearance preferences where the backgrounds are listed.  Near the bottom is a button labeled "Add..." and go to the location where you have saved the xml file.  You won't be able to see it initially - you need to look for all files.  Above the "open" button is a drop down menu that is set to images as a default.  Select "All files" and now you should be able to see the xml file.

Select the xml file and now your stack should be available as a background.

I'd imagine that there are more things that can be done in the xml file, but all I know is what I saw in the file to define the space background.  If anyone else has knowledge on this, I'd love input!

---

### Post by avdzm on 2009-11-07
I am also trying to find a program that creates the xml file.
Although I can't find anything,
I am thinking of creating my own app to do.

Select the pictures, sort the order and vula.

Although I am looking...

---

### Post by ackey on 2009-11-07
It looks like [someone just did it.]("http://ubuntuforums.org/showthread.php?p=8264624#post8264624")

I've found some further discussion on the wallpaper at at 
[http://ubuntuforums.org/showthread.php?t=845693](http://ubuntuforums.org/showthread.php?t=845693)  [http://jkwarren.info/blogs/index.php/2009/10/28/slick-wallpaper-rotation-in-ubuntu](http://jkwarren.info/blogs/index.php/2009/10/28/slick-wallpaper-rotation-in-ubuntu) [http://www.mail-archive.com/ubuntu-art@lists.ubuntu.com/msg05440.html](http://www.mail-archive.com/ubuntu-art@lists.ubuntu.com/msg05440.html)

---

### Post by SebbyT on 2009-11-20
Thank you - I was tearing my hair out trying to figure out how to do this. That stacked icon is just so enticing I figured I was missing some obvious piece of functionality. Guess not!

---

### Post by decrow06 on 2009-12-18
Does anybody know why my cosmos background won't switch?

---

### Post by tomturtle18 on 2009-12-18
My background wouldn't change unless I saved the backgrounds-1.xml file. There's a patch for it at [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753)

I think I ran ```
sudo apt-get source libgnome-desktop-dev
sudo apt-get build-dep gnome-desktop
```

Then applied the patch and ran configure, make and make install.

And now it works for me.

---

### Post by LuisGMarine on 2009-12-18
I've done this myself, but I noticed that after I restart my machine, the first picture is defaulted to a solid color.  I don't know if it's me or what, but can someone else try and restart their computer and see if they experience the same problem?

---

### Post by decrow06 on 2009-12-18
tomturtle, i'm kind of a newbie, can you be a little more specific

---

### Post by decrow06 on 2009-12-18
More specifically, could anybody elaborate on how to install the patch etc.

---

### Post by LuisGMarine on 2009-12-18
nvm on my post.  When I was editing the code I forgot to have it loop again.  As in I forgot to tell the script to go back to the first image after the last one is played, so that is what was causing my screen to go to a solid.

That would be cool to turn this into a script, or even a python gui program.  Could be a project of mine, but it would take to long since I"m in the process of learning and I"m sure someone can make one in a heartbeat.

---

### Post by tomturtle18 on 2009-12-18
Decrow, run the two commands I have before to get the source code for gnome-desktop and the dependencies to build it.  After that, in the command terminal, cd into the source directory. Assuming you ran those commands while in your home directory it will be ~/gnome-desktop-2.28.1.  Download the patch from [https://bugzilla.gnome.org/show_bug.cgi?id=601753](https://bugzilla.gnome.org/show_bug.cgi?id=601753) named gnome-desktop.patch.  While in the gnome-desktop-2.28.1 directory run the following command (may need to apt-get patch):
```
patch -p1 < ~/gnome-desktop.patch
```
assuming gnome-desktop.patch is in your home directory.
If that is successful, then run```
./configure
make
sudo make install
```
I then rebooted, you may just need to logout but I'm not sure.

I think these are the steps I took to get it to work.  I'm sure if something doesn't work when you try, someone will be able to figure it out.

Good luck.

---

### Post by coffeeandlinux on 2009-12-18
Thank you ackey! Much appreciated! I had tried before but was unsuccessful now I got it to work!

---

### Post by decrow06 on 2009-12-19
I get the following when I try to start: 

```

dcrow@dcrow-laptop ~ $ sudo apt-get source libgnome-desktop-dev
[sudo] password for dcrow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

```

What do I do now?

Thanks for all of your help

---

### Post by LuisGMarine on 2009-12-19
> **decrow06 said:**
> I get the following when I try to start: 

```

dcrow@dcrow-laptop ~ $ sudo apt-get source libgnome-desktop-dev
[sudo] password for dcrow: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: You must put some 'source' URIs in your sources.list

```

What do I do now?

Thanks for all of your help

Try following this thread to fix that problem:

[http://ubuntuforums.org/showthread.php?t=516003]("http://ubuntuforums.org/showthread.php?t=516003")

---

