---
title: "Menu's application name first?"
date: 2006-04-03
forum: Desktop Environments
---

### Post by Gowator on 2006-04-03
I have been trying to work out how to get rid of the annoying tag that goes in front of all the menu items in Ubuntu...Help me start using the GUI please!!!!
e.g. 
Package Manager (Add applications)
Package Manager (Adept)
Package Manager (Kpackage)
Package Manager (Synaptic)
Package Manager etc. etc. etc.

This makes it really frustrating trying to find a menu item for you want and often causes me to select the wrong one, especially on my laptop and touch pad!  

Also the packages are put in random places that ignore the normal Deb packaging so I just installed a whole load of odbc stuff today and of course it doesn't even appear on a menu yet I wasted however long just trying to find it?  

In the end I have ended up spending more time at the console than using the GUI because the GUI is counter intuitive if you know what you are looking for... why force me to scroll through 10 media players or 5 browsers when I know which one I want to use?  

Is there is a simple way to just get rid of all these additions to the menu system, I haven't used pure debian for a while, are these part of KDE now or part of Ubuntu because if I can get rid of them by going back to Debian that sounds ideal... ( it will also fix amarok and 20 other issues I have to put up with daily on Kubuntu).

---

### Post by Sboulema on 2006-04-03
To get rid of unwanted entries use kmenuedit

To change they way the entries are shown System Settings->Panel->Menus

---

### Post by gingermark on 2006-04-03
Right-click on the Panel and select "Configure Panel".
Select "Menus", and from here you can change how your programs are shown. (EDIT: looks like Sboulema beat me to that one).

"sudo apt-get install menu" should install a Debian menu entry in your K-Menu, which you can use to launch apps if you prefer the Debian menu system. I'm not sure if you can switch totally though. Guess you could play around in kmenuedit when you've got the Debian menu installed, but I wouldn't recommend it.

And, yes, it's my experience that sometimes apps take a little while to get added to the menu, not so sure why.

Any OS usually takes time to set up to your liking, and that's all I put the menu-naming excentricity down to. I guess it's designed for Linux converts who don't know what each program does.

Apart from that, I quite like the Kubuntu menu system, but each to their own :)

---

### Post by GeneralZod on 2006-04-03
I've pretty much ditched the kmenu in favour of katapult, nowadays :)

---

### Post by Gowator on 2006-04-03
Thanks everyone....
> 
Any OS usually takes time to set up to your liking, and that's all I put the menu-naming excentricity down to. I guess it's designed for Linux converts who don't know what each program does.
I understand that point and I see how its useful to new converts but IMHO its more useful the first time they are looking for a program.  Once you have tried the options and know which program you want it becomes more of an annoyance, at least for me!  Personally I think it makes more sense overall in reverse ... Name **then** description?  
Even for new converts I can see the present system is confusing because they choose image editor for instance and get gimp but forget the name and next time launch a different application but that's just my 2c....

I did install the Debian menu but it seems incomplete and Im not sure if that is because the kubuntu menu system is interfering or because I installed it after a lot of apps were aleady installed or a mix of the two?  

I would prefer deleting all the Kubuntu entries and going back to something more familiar but Im a bit worried what might happen if I do this.  

Also something weird happens with kappfinder... that is I know stuff is installed and should be found BUT its not so I end up adding it by hand.  

I like playing about a bit and add apps I see others using to try them out but often I select a set and only half seem to ever appear on the menu's, more than once I have searched for an app and then found its already installed and done an apt-get install --reinstall to find it is then on the menu's?  I have to say this is a rather heavy way to do it but ??

I used to use Mandrake (when it was mandrake) and they had a utility to back out the Mandrake menu's and revert to KDE ones... (it was a bit hidden but it worked after a fashion) so Im wondering if its possible in Kubuntu too?  
I'm presuming the .deb contains the dpkg info for this and there might be a logical entry in some apt config file allows me to use the KDE/Debian one because presumably its still around because it partially seems to work with the Debian menu?  

Any further tips please keep em coming...  especially what the consequences of deleting the whole Kubuntu tree might be from kmenuedit!  

@GeneralZod
As I said above Im pretty weak with myself for expermenting ... you have wet my appetite so here goes katapult :D

edits:  Guess what it was already installed!  LOL

---

### Post by gingermark on 2006-04-03
Yep, I also use Katapult the majority of the time.

[QUOTE=Gowator]Personally I think it makes more sense overall in reverse ... Name **then** description[/QUOTE]

This is how it used to be in Hoary I believe. And I totally agree with you. Not sure why it changed.

---

### Post by Parkotron on 2006-04-05
I agree that 'Name (Description)' is by far a better default. I think 'Description (Name)' is somewhat offensive to the intelligence of any user, even beginners. It's also kind of disrespectful to application developers; users should learn the names of the programs they use.

Anyway, one of the first things I do after a fresh install is turn off the descriptions altogether. But I feel that anyone who's "advanced" enough to be bothered by the descriptions, should be able to easily find the option to turn them off, so I think descriptions on by default is all in all a good idea, so long as they don't take precedence over the application names.

---

