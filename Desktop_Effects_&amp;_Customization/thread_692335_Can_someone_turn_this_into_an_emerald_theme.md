---
title: "Can someone turn this into an emerald theme?"
date: 2008-02-09
forum: Desktop Effects &amp; Customization
---

### Post by Redrazor39 on 2008-02-09
Ok. Right now I have this theme: [White?!]("http://www.gnome-look.org/content/show.php/White%3F%21?content=62968")

And I can't get the titlebars working right without losing my compiz fusion effects, so then I found this theme: [Skimmed Milk]("http://www.gnome-look.org/content/show.php/Skimmed+Milk?content=28142") 
and I LOVE the titlebars! I love how it just flows with the rest of the window instead of being completely separated. I would probably edit the buttons a bit, but w/e.

I need someone who can do it to turn "Skimmed Milk" (the second link) into an emerald theme and attach it or post it online or something so I can download it and install the .emerald file easily and have White?! control and stuff, Skimmed Milk titlebars, and all my Compiz Fusion effects. I know this is possible because I've seen it done with other themes, but I don't know how to do it or who can do it. Will someone please help?:confused::confused::confused:

Many thanks,

Me.

---

### Post by Redrazor39 on 2008-02-09
any help at all would be greatly appreciated...

---

### Post by Redrazor39 on 2008-02-16
See, I would like to be able to change the buttons to simple triangles (not those Apple circle things) and I love how the titlebar blends into the window.

Can't anyone do this?

---

### Post by blueshift9 on 2008-02-17
Looks like someone doesn't get the Linux mentality........Why don't you figure out how for yourself?

---

### Post by CarpKing on 2008-02-18
If you set that as your Metacity theme and then switch from Emerald to GTK-Window-Decorator (I'm not sure how to do the latter once you've installed Emerald, but try putting "gtk-window-decorator" in the "Window Decorator Command" field in the decoration plugin in CCSM), you'll be using that theme.

---

### Post by Redrazor39 on 2008-02-18
I'm an extreme noob and i love learning about linux, but I learn from things like this.

and sorry, but I don't really understand what the above poster means...

---

### Post by tedt on 2008-02-20
I think what the post was trying to say is as follows:

Download the metacity file.

Open up System>Preferences> Appearance 

Drag the metacity theme (28142-Skimmed-Milk.tar.gz) in to the Appearance window

A dialog box will then pop up asking "Would you like to apply it now, or keep your current theme?"

Click on "Apply New Theme"

Then hit the alt key and F2.

The "Run Application" dialog box will pop up.

Enter into the "Run Application" dialog box -> gtk-window-decorator --replace


The Skimmed Milk theme should now load.  Basically what this will do is switch the winodw decoration from Emerald to Metacity

---

### Post by CarpKing on 2008-02-20
Yes, that's exactly what I meant.  I can be hard to understand sometimes.

---

### Post by Redrazor39 on 2008-02-21
Thanks, but I tried something like this and my compiz effects wouldn't work. Is there a way to go back, just in case? I'll try this, but I need a way to get it back, just in case.


Also, I wanted to change the close/max/min buttons to simple black triangles (down for minimize, up for maximize, and right arrow for close

---

### Post by tedt on 2008-02-21
with the Alt F2 bit from above use emerald --replace instead of gtk-window-decorator --replace

Metacity doesn't support changing buttons like emerald does so you will have to open up the downloaded archive and change the image files inside the archive that relates to the buttons

Sorry it doesn't work for you but on my Gutsy it does so I guess YMMV

---

### Post by rainwalker on 2008-02-21
> **blueshift9 said:**
> Looks like someone doesn't get the Linux mentality........Why don't you figure out how for yourself?

No, *you* don't understand. Obviously they *are* trying to figure it out by asking the community, which is at the core of the "Linux mentality".

---

### Post by Redrazor39 on 2008-02-21
Thank you. This is what I thought the Linux mentality was and I'm glad it is. I love the community-ness and how active the community really is. This is the great philosophy of Linux I love!

---

### Post by Redrazor39 on 2008-02-21
Thanks, everyone! This worked perfectly! Now I have all my compiz fusion effects AND I can use metacity for titlebars! yay!

Now I just need to try to change the buttons because I don't like these mac ones. Should I extract the tar.gz and edit the buttons there or should I just open the tar.gz in archive manager and save my new buttons there?

Thanks for all your help!

---

### Post by Redrazor39 on 2008-02-22
YES!!! My awesome new theme is atched

---

