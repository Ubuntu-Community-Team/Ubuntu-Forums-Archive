---
title: "Transparent Konsole in Feisty?"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by miggols99 on 2007-04-12
I looked on the Beryl website and it said you can get a transparent Konsole in Edgy. I'm not using Edgy though! How do I do this in Feisty?

---

### Post by bashologist on 2007-04-12
I've noticed that if I start beryl with the option "--replace", e.g. "beryl --replace" it makes my transparent terminal background look real. Maybe this is what you're looking for?

---

### Post by blazercist on 2007-04-12
You don't need beryl to have a transparent console in edgy or feisty.  Look at the 
Edit > Current Profile
menu there should be something in there.

You could also use beryl/emerald for that though if you wanted to but thats alot more complicated.

---

### Post by miggols99 on 2007-04-12
>   You don't need beryl to have a transparent console in edgy or feisty. Look at the 
 Edit > Current Profile
 menu there should be something in there.
 
 You could also use beryl/emerald for that though if you wanted to but thats alot more complicated.
When I change to transparent, it just shows the background image. I want real transparency.

EDIT:
> I've noticed that if I start beryl with the option "--replace", e.g. "beryl --replace" it makes my transparent terminal background look real. Maybe this is what you're looking for?
This doesn't do anything :(

---

### Post by blazercist on 2007-04-12
Real transparency?  I don't understand.   There is a slider bar where you can set the degree of transparency, if you have it set to 100% then it will just appear to be your desktop background.

---

### Post by miggols99 on 2007-04-12
Real transparency is when you see the windows behind it not just the background.

Have a look at this page:

[http://www.beryl-project.org/userguide.php]("http://www.beryl-project.org/userguide.php")

---

### Post by Ptero-4 on 2007-04-12
To get real transparency (It works for me in gnome-terminal, don`t know if konsole does it too) use the fake transparency option while you have a compositing wm running (kwin is one of those) with it`s compositor enabled and with both the libxcomposite package installed and the Composite line in your xorg.conf

---

### Post by blazercist on 2007-04-12
Well, I see what you mean, I am under the impression that you need Beryl or Compiz for that... do you have either of those installed and running?  If so then its probably an option under one of the plugins.

---

### Post by miggols99 on 2007-04-12
Yes, I have Beryl working fine. Do I have to download a new plugin or is there already one built in?

EDIT: >  
To get real transparency (It works for me in gnome-terminal, don`t know if konsole does it too) use the fake transparency option while you have a compositing wm running (kwin is one of those) with it`s compositor enabled and with both the libxcomposite package installed and the Composite line in your xorg.conf
I tried this but it did nothing.

---

### Post by blazercist on 2007-04-12
Well right now I'm at work so I can't really check, but I think beryl comes with that functionality, no extra plugins required.  Unfortunately I can't check where that option is in the manager so you'll  have to poke around and find it for yourself.  Good luck I know its in there somewhere.

Also! I just remembered that Compiz has an option that when you move a window it goes transparent, perhaps that is what it is, maybe Beryl has some equivalent?  Maybe if you look closely at those pics the windows are being moved?

---

### Post by DJ_Peng on 2007-04-13
Just checked my Feisty/Beryl (AIXGL) comp installation and was able to use the Alt-scroll wheel to activate the transparency. It works as before, making the entire window (except the title bar) transparent to see behind it. Is this what you are looking for?

---

### Post by miggols99 on 2007-04-13
Well, that's almost what I want. Can I make it so it starts up transparent and only the black part transparent?

Look at the screenshot to see what I'm getting.

---

### Post by DJ_Peng on 2007-04-13
I think I see what you're looking for. Check my screenshot. I got that in Terminal by selecting View > Profiles... Edit > Effects and making the transparency to about 50%. When I close Terminal and reopen it the transparency is remembered.

---

### Post by miggols99 on 2007-04-13
I'm using Konsole (KDE) so it's different. When I go to settings >> configure konsole then schema, I can change the transparency, but it still isn't real.

---

### Post by DJ_Peng on 2007-04-13
Sorry, I can't help with KDE. Maybe someone can help soon.

---

### Post by n8bounds on 2007-04-13
I <3 KDE, but use gnome-terminal instead of Konsole b/c I can't seem to figure this out either.

---

### Post by KubuntuKilledMe on 2007-04-20
I kinda followed the guide here: [http://wiki.beryl-project.org/wiki/Konsole-alpha](http://wiki.beryl-project.org/wiki/Konsole-alpha)

I am running feisty, but i added that edgy line to sources.list:

 deb [http://download.tuxfamily.org/3v1deb](http://download.tuxfamily.org/3v1deb) edgy beryl-svn

then i did apt-get update, apt-get install konsole-alpha, then i reverted the change in sources.list and i had it working with no apparent problems.

Cheers.

---

### Post by smac4president on 2007-04-27
Try this:
Alt+F2 and type Beryl-settings
Go to Window Management panel
Check the box on "Set Window Attribs by various criteria"
Drop down the Opacity menu
Hit the Add (+) button and select "Window Class" from the drop down menu
type Konsole in the box and set the transparency to the level you want.

Alternatively you can have a terminal open and use the "grab" feature by clicking the open terminal window (or any other type of program you want to open with a set transparency).

I've seen answers about "Beryl Settings Manager -> Window Management -> Window-Specific Settings", but there was no "window-specific settings" tab for me.  This, though, appears to work for me at least.

---

### Post by miggols99 on 2007-04-28
That worked! Thanks :)

---

### Post by AngelSeph on 2008-07-13
Perhaps this can help:

Starting feisty, you can just start konsole with the argument --real-transparency as so:

konsole --real-transparency

You can just modify the K menu and add it so it would start any time you click on the icon instead of starting a foreground job for the konsole.

Hope it helps!

---

