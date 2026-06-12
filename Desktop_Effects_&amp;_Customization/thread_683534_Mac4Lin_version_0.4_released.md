---
title: "Mac4Lin version 0.4 released"
date: 2008-01-31
forum: Desktop Effects &amp; Customization
---

### Post by ciscoder on 2008-01-31
[SIZE="6"][COLOR="LightBlue"][B]Mac4Lin version 0.4 released[/SIZE]
[/B][/COLOR]
_the link_

Part1:  [http://downloads.sourceforge.net/mac4lin/Mac4Lin_Part1_v0.4.tar.gz?modtime=1198003589&big_mirror=0&filesize=15418558](http://downloads.sourceforge.net/mac4lin/Mac4Lin_Part1_v0.4.tar.gz?modtime=1198003589&big_mirror=0&filesize=15418558)
Part2:  [http://downloads.sourceforge.net/mac4lin/Mac4Lin_Icons_Part2_v0.4.tar.gz?modtime=1198005665&big_mirror=0&filesize=14406146](http://downloads.sourceforge.net/mac4lin/Mac4Lin_Icons_Part2_v0.4.tar.gz?modtime=1198005665&big_mirror=0&filesize=14406146)
Part3:  [http://downloads.sourceforge.net/mac4lin/Mac4Lin_Wallpapers_Part3_v0.4.tar.gz?modtime=1198007584&big_mirror=0&filesize=12555519](http://downloads.sourceforge.net/mac4lin/Mac4Lin_Wallpapers_Part3_v0.4.tar.gz?modtime=1198007584&big_mirror=0&filesize=12555519)
Documentation :  [http://downloads.sourceforge.net/mac4lin/Mac4Lin_Documentation_2.pdf?modtime=1198008186&big_mirror=0&filesize=4590352](http://downloads.sourceforge.net/mac4lin/Mac4Lin_Documentation_2.pdf?modtime=1198008186&big_mirror=0&filesize=4590352)


Thank's To The Developer : Anirudh Acharya (a.k.a infra_red_dude)

Good luck For All :)

---

### Post by Evelyn on 2008-02-08
While extracting the Mac4Lin_Wallpapers_Part3_v0.4.tar.gz I received an error "An error occurred while extracting files." I have copied and pasted the Command Line Output below. 
 
 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk2 [[]blue[]].jpg: Not found in archive 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk2 [[]grey[]].jpg: Not found in archive 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk3 [[]blue[]].jpg: Not found in archive 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk [[]blue[]].jpg: Not found in archive 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk [[]grey[]].jpg: Not found in archive 
tar: Pattern matching characters used in file names. Please, 
tar: use --wildcards to enable pattern matching, or --no-wildcards to 
tar: suppress this warning. 
tar: Wallpapers/ipodesk3 [[]grey[]].jpg: Not found in archive 
tar: Error exit delayed from previous errors

---

### Post by Evelyn on 2008-02-08
The documentation that comes with Mac4Lin is for Gnome 2.0 and 2.18. I have the latter, however cannot figure out how to install the icons. In the document it says, "GNOME 2.18 
Goto System > Preferences > Theme > Customize > Icons. Click Install. Choose the Mac4Lin 
GTK Icon Theme .tar.gz file (wherever its extracted). Select to Apply." My problem is that in my directory I have Mac4Lin_Icons_v0.4 and in that there is no Mac4Lin GTK Icon Theme .tar.gz file

---

### Post by Evelyn on 2008-02-08
According to the document that came with the download it says: "After installation, copy all splash images files from /GTK Splash to /usr/share/pixmaps/splash/ as root." I can open the /usr/share/pixmaps/splash/ folder and the /GTK Splash folder but when I try to copy and paste or drag and drop it comes up with this error message "Error while copying to "/usr/share/...aps/splash". You do not have permissions to write to this folder." Can someone please help me? How do I copy all splash images files from /GTK Splash to /usr/share/pixmaps/splash/ as root?

---

### Post by denham2010 on 2008-02-09
Hi,

For those who are wanting to use the LastFM AWN applet with the Mac4Lin themes.......

I had the problem of the Play, Skip, Love and Ban buttons not being displayed while using Mac4Lin as my GTK theme.

The reason for this is that the Mac4Lin theme defaults to not showing icons on gtk buttons.

To get the icons to show, open up the folder:

```
~/.themes/Mac4Lin_GTK_v0.4/gtk-2.0
```

and edit the file gtkrc

Right near the top of the file you will see the following:

```
# Do not show images on buttons (Set to 1 if you want icons to be displayed)
gtk-button-images = 0
```

Just change the 0 to a 1 and save the file.

You will now have icons on gtk buttons. Of course, now you can see why it defaults to off. The shape of the button in the Mac4Lin theme being rounded means some icons will be larger than the button itself - LastFM applet is a good example of this.

If anyone knows a way to scale the icons on the gtk buttons to prevent this, I'm all ears!

Thanks, and enjoy!

---

### Post by af01 on 2008-07-21
Hey guys!!!
I just recently got Mac4lin 0.4, I must say I really enjoy the work done there... I have friends I've been trying to convince to switch over to ubuntu, and only ubuntu with mac4lin made it interesting enough for them to try! So thank you!!!

Now, my problem...

If I use the mac4lin theme for the controls, it makes Nautilus freeze while browsing some folders... especially if they have images or music in them.

I tried removing the theme just from controls, and leaving all the rest... and it works great. Anyone know what I should do? I'm running Hardy.


Thanks!

---

