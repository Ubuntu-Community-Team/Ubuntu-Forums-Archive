---
title: "Makin it snazzy"
date: 2005-12-10
forum: Desktop Environments
---

### Post by jabb0 on 2005-12-10
Heya,
I have been messing around icons and themes and stuff.
I have got some nice configurations now, but there is a few things i could do with a hand on.

Nearly all of the icon sets i download dont have matching icons, for example some sets would have an icon for say a .doc file and others for a .odt file.  I havent found one yet that will cover all the icons i need.  I realise the chances of getting that in one iconset are a lil low but is there some way i could create my own iconset madeup from several iconsets in an attempt to do this?

Another icon thing is, the little icon on the main menu is always a Ubuntu icon, how can i change this to a foot, i much rather have the Gnome foot?

Oh yeah it prolly worth mentioning i am on Gnome :razz:

I remember when i first started out a fe wmonths back on my Ubuntu expidition into linux an i seen some pretty cool screenshots of some folks desktops and they looked mad, with things like cool analogue clocks and dynamic displays (thats the best way i could describe it, it was only a screenshot but they must have been changing) of thier gmail showing a lil report of new mails and stuff.  Now i have looked and i cannot get back to this page for the life of me... so would any of you guys know where i could find out about this kinda stuff?

Any other stuff i can get goin to jazz thangs up a bit would be greatly appreciated :D

---

### Post by taurus on 2005-12-10
I think you are talking about the eye-candy thing!!!  You can use gdesklets, gdeskcal, gkrellm, conky/torsmo, adesklets, superkaramba (for KDE), etc...  Perhaps we should have a new threat where people post their screenshots!!!

---

### Post by jabb0 on 2005-12-10
I have no idea what all that means but i like the sound of it, and yes plz post screenshots.

Ill go google some of that stuff see wot i get.  

I have to say i got a rather cool set of semi transparent icons that do the business, however they do fall short of completing a full set :(

---

### Post by taurus on 2005-12-10
gDesklets...
[http://gdesklets.gnomedesktop.org/](http://gdesklets.gnomedesktop.org/)

gDeskcal...
[http://www.pycage.de/software_gdeskcal.html](http://www.pycage.de/software_gdeskcal.html)

Gkrellm...
[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

Conky...
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

aDesklet...
[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

Superkaramba...
[http://www.superkaramba.com/index.php?SourceWell_Session=20b57b95ba5a0a291aa915fe890fd921](http://www.superkaramba.com/index.php?SourceWell_Session=20b57b95ba5a0a291aa915fe890fd921)

     Those should keep you busy for a while!!!  :)

---

### Post by jabb0 on 2005-12-11
I have slowly made my way through gDesklets and got some fine results, however there seems to be some kin of issue with the latest version being wierd with sensors which means i cant use alot of them, but ill be keeping an eye here defo for new cools stuff.

Now for the rest... ill post a screenie when im done... ur not alowed to see it until its finished :P

---

### Post by taurus on 2005-12-11
Can't wait for your screenshots to see what kind of a monster I have created!!!  :smile:

---

### Post by jabb0 on 2005-12-11
there is a link to to my latest screenie, its a works in progrss but its looks so much better than it used to
[http://www.jabb0.cunningdesigns.com/files/vault/jabb0//images/gdesklets1_scrnsht.png]("http://www.jabb0.cunningdesigns.com/files/vault/jabb0//images/gdesklets1_scrnsht.png")

Adesklets
I have ot it downloaded and installed and every command i type doesnt seem to break it, i have downloaded and installed some actual desklets and executed the .py file, but i cant get nuttin else to happen, here look the website says :

 > To add a new desklet script, simply:    [LIST=1]
[*]Download its tarball and unpack it somewhere in your home     directory
[*]Look at the included README file; special requirements or     instructions will be given. Usually, all you have to do is to     get adesklets installed, your X server running, then launch the     executable script file from the base directory. [/LIST]Im guessing the base directory is where it was installed, the only place it exists on my compo is in my /home dir (whether thats a good decision or not i dunno, but i hope i can leave that one for another day).
But im not sure what it is i run from the "base dir"?

When i run adesklets in the command console it starts a comman line program, i have read all 160 commands from --help and i dont think there is one thats gonna make something happen on the screen.
[LIST=1]
[*] [/LIST]

---

### Post by taurus on 2005-12-11
That looks real nice there, jabb0.  If you want to use adesklets, you need to download those applets (or modules) and unpack them somewhere in your $HOME.  I put mine in ~/adeskets_modules.  Now, change to the directory that you just unpack and run the file with py extension,

./package.py

Then, run adesklets from a prompt and see if the applet/module starts or not...

---

### Post by jabb0 on 2005-12-11
Heya,

Ok i have done wot u said already and have gotten as far as to find out the bad news i have the "filcker Problem", like the thing has even got a name :eek: any who i have tried running adesklets under nautilus fake root thingy ie 
**$ adesklets --nautilus**
I tried all the others too, just for the hell of it, but nothing makes it go.
it just "flickers".... nice!!!

Wot ya think?

---

### Post by Hairy_Palms on 2005-12-11
one thing to make it snazzyer is use sidepanels for extra menus, like this screenshot.

[http://photobucket.com/albums/b264/Hairy_Palms/?action=view&current=Screenshot-1.jpg](http://photobucket.com/albums/b264/Hairy_Palms/?action=view&current=Screenshot-1.jpg)

or you can Xpify it, check out winbuntu in my signature :)

---

### Post by maruchan on 2005-12-11
jabb0,

As for the incomplete icon sets, I would recommend tracking down the author (on either gnome-art or gnome-look) and dropping them an email like:

> Hi,
I am new to Linux and enjoy using your icon set. Thank you very much for your hard work. I wonder if you might find it in your heart to create an icon for .odt and .psd files? These are the only icons I find missing from the total [icon set name] experience, so if you do have a moment to whip something up, please let me know. Again, thank you for your work, and kind regards,

Jabb0rw0cki Jorg Jalewskeyi
Petropavlovsk, Delaware

That should help get you most icons you need. ;)

---

### Post by taurus on 2005-12-11
The reason for the flickering is because of the nautilus thing!!!  I run either Xfce4 or Fluxbox and don't have any problem with it.

---

### Post by jabb0 on 2006-01-17
I didnt think i had a choice - ill have to look them up.

so i have
- xserver / xorg
- gnome / kde
- gtk
- nautilus / Xfce4 / Fluxbox
All working happily to give me my desktop and i have only a vague idea at best as to what they all actually are... i need to do some reading!!!!

Know any good places to start? (start being the most important word there, i am 6 months in with ubuntu/linux but ive obviously got a long way to go yet!!!)

---

