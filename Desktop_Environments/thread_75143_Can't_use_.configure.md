---
title: "Can't use ./configure ??"
date: 2005-10-13
forum: Desktop Environments
---

### Post by SilverTab on 2005-10-13
I'm trying to install a theme...I installed gcc and the build-essentials, but I get the following error when running ./configure (from the theme folder)

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!


I tried several themes and apps, I always get this error...

---

### Post by Dromio on 2005-10-13
I think you need to install the X development libraries, maybe libX11-dev.

---

### Post by SilverTab on 2005-10-13
still the same error :(

thanks for the suggestion though!

---

### Post by kassetra on 2005-10-13
[QUOTE=SilverTab]still the same error :(

thanks for the suggestion though![/QUOTE]

Do you have build-tools (I think that is the correct name) and gcc installed?

---

### Post by SilverTab on 2005-10-13
[QUOTE=kassetra]Do you have build-tools (I think that is the correct name) and gcc installed?[/QUOTE]


The name is build-essentials, and yes I installed both :confused: 

I think the problem is really the path...since the error is saying
checking for X... configure: error: Can't find X includes. **Please check your installation and add the correct paths!**

---

### Post by kassetra on 2005-10-13
[QUOTE=SilverTab]The name is build-essentials, and yes I installed both :confused: 

I think the problem is really the path...since the error is saying
checking for X... configure: error: Can't find X includes. **Please check your installation and add the correct paths!**[/QUOTE]
Whenever I get that error - it is because I have not installed all of the -dev files needed.

Do you have all of the xorg dev files installed?

The "path" it is looking for is in the package config - which it will not find unless you have the -dev installed.

---

### Post by SilverTab on 2005-10-13
[QUOTE=kassetra]Whenever I get that error - it is because I have not installed all of the -dev files needed.

Do you have all of the xorg dev files installed?

The "path" it is looking for is in the package config - which it will not find unless you have the -dev installed.[/QUOTE]


mmm not sure... what would be the package name??

I have pretty much all the xorg packages installed except xorg-fglrx which is for ATI drivers...

---

### Post by kassetra on 2005-10-13
[QUOTE=SilverTab]mmm not sure... what would be the package name??

I have pretty much all the xorg packages installed except xorg-fglrx which is for ATI drivers...[/QUOTE]

x-window-system-dev  ... I believe (not at my desktop.)

... you're not running this on a PPC/Mac are you?

---

### Post by SilverTab on 2005-10-13
[QUOTE=kassetra]x-window-system-dev  ... I believe (not at my desktop.)

... you're not running this on a PPC/Mac are you?[/QUOTE]


nope, on a P4.... ok let me try to find the package! :)

---

### Post by GeneralZod on 2005-10-13
Very odd; what is the result of 

```

ls /usr/X11R6/include/X11

```

?

---

### Post by SilverTab on 2005-10-13
[QUOTE=GeneralZod]Very odd; what is the result of 

```

ls /usr/X11R6/include/X11

```

?[/QUOTE]


ok I got it to work by installing x-window-system-dev 

now I got another problem..apparently I don't have Qt3 installed LOL
(I checked, libqt3-mt is installed)
checking for Qt... configure: error: Qt (>= Qt 3.1 (20021021)) (headers and libraries) not found. Please check your installation!

wow...installing a simple theme turned out to be harder than I expected...

---

### Post by GeneralZod on 2005-10-13
This is one of my major annoyances with the standard "configure" script - it gives completely the wrong error messages!

It should really be complaining about the lack of qt3 *headers*.  Search  for 

qt *dev*

(I don't know the exact package name, I'm afraid :() and install anything that looks promising! :D

---

### Post by SilverTab on 2005-10-13
[QUOTE=GeneralZod]This is one of my major annoyances with the standard "configure" script - it gives completely the wrong error messages!

It should really be complaining about the lack of qt3 *headers*.  Search  for 

qt *dev*

(I don't know the exact package name, I'm afraid :() and install anything that looks promising! :D[/QUOTE]

hehe thanks for the tip, it worked, now im getting:
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


:confused:

---

### Post by kassetra on 2005-10-13
[quote=SilverTab]hehe thanks for the tip, it worked, now im getting:
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!


:confused:[/quote]

.... oi.  guess what -dev files you have to install now?  yep.  kde ones.  *sigh* 

once you get all these devs installed though, you'll be able to compile nearly anything you want to from now on!

---

### Post by SilverTab on 2005-10-13
LOL ok im trying it...

sorry if i'm that clueless...im a gnome guy usually, but there are some programs that I need in KDE, and I cant run'em from gnome since I upgraded to breezy so I decided to give kde a try...

---

### Post by kassetra on 2005-10-13
[quote=SilverTab]LOL ok im trying it...

sorry if i'm that clueless...im a gnome guy usually, but there are some programs that I need in KDE, and I cant run'em from gnome since I upgraded to breezy so I decided to give kde a try...[/quote]

LOL it's cool.  You're not clueless.  How the heck are you supposed to know what all that means?  -dev doesn't say "I have header files in here!  Install me!"  ... it's unfortunately something you have to learn - and first you have to learn that when it can't find the "path" it can't find the header files.

It's all good.  You're doing great for doing this on your own.  When I first tried doing compiles in 97, my neighbors couldn't figure out why glass items were coming out of my second story window at amazing speed and distance.

---

### Post by kaktusztea on 2005-10-22
sudo apt-get install kdelibs-dev

---

### Post by gimfred on 2008-02-20
If any other newbies like myself come here searching for the original error, the new packages to be installed are based on xorg, rather than x-windows. So the files talked about should be one of the xorg-<may be relevant>-dev packages. 

This is because x11 went through a name/?licence? change in ?2003 or 2004? which eventually lead to a re-designation of the x libraries for compatibilities sake I am to understand. I believe the qt libraries mentioned went through a similar name change, however I haven't found them.


Hope this helps someone. I could have used it.

---

