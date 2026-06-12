---
title: "How do I change beard man icon? Xfce No Gnome"
date: 2005-12-01
forum: Desktop Environments
---

### Post by videodrome on 2005-12-01
Hello.

How do I change the bearded man icon that is there when you log back in, after, say a screensaver?

I need to know what package to install to allow me to change the picture, or be told where the icon is so I can delete it.

I am NOT running Gnome. Just a server install & Xubuntu. Thanks

---

### Post by aysiu on 2005-12-01
The beard man?
I'm not sure if this'll solve your problem, but for splash screen (after the regular login... I don't have a login after returning from the screensaver), you can change it to Balou and then change this icon:

/usr/share/themes/Defaults/Balou/logo.png

I'm going based off memory, but it's a path like that.

---

### Post by psychicdragon on 2005-12-01
That's not it. It's the icon shown in the log-in dialog, this guy:
[IMG]http://planet.gnome.org/heads/nobody.png[/IMG]

run xscreensaver and lock the screen to see him.

It doesn't use the user_icon supplied by my icon theme. So, the only way to change it would be to find the .png and replace it with something you prefer.

---

### Post by videodrome on 2005-12-06
Yes that's the guy. I hate that guy! Any idea which/where that icon is so I can terminate it? Thanks

---

### Post by bunty on 2005-12-06
Call that a beard?! 

I quite agree , makes me want to puke , thanks for "sharing" that with us.

Try using APM in your bios to power the screen off . Screensavers dont save screens.:cool:

---

### Post by videodrome on 2005-12-06
I have to use the screensaver for work, so that login prompt has to stay. But the little goatee dude has got to go. Somehow.

---

### Post by ranf on 2005-12-07
[QUOTE=psychicdragon]That's not it. It's the icon shown in the log-in dialog, this guy:
[/QUOTE]
I found him several times under `/usr/share/icons' as `stock_person.png'.

---

### Post by MaX on 2005-12-07
what do you have against him anyhow... :confused:

---

### Post by matthew on 2005-12-07
System->Preferences->About Me

Click on the icon.

Either direct it to use another picture or click on "no icon."

Personally, I use the attached...

---

### Post by videodrome on 2005-12-07
I don't have the >about "me portion" as stated, because I don't have Gnome installed. I will however look for those "stock_person" icons.

Max: Women want women icons.

---

### Post by aysiu on 2005-12-07
[QUOTE=videodrome]I will however look for those "stock_person" icons.[/QUOTE] ```
 locate stock_person
/usr/share/icons/hicolor/48x48/stock/generic/stock_person.png
/usr/share/icons/hicolor/32x32/stock/generic/stock_person.png
/usr/share/icons/hicolor/16x16/stock/generic/stock_person.png
/usr/share/icons/hicolor/24x24/stock/generic/stock_person.png
```

---

### Post by matthew on 2005-12-07
[quote=videodrome]I don't have the >about "me portion" as stated, because I don't have Gnome installed.[/quote]Oops! I read that the first time and promptly forgot it. Sorry. It looks like aysiu has found where the icons are, though.

---

### Post by IdolizingStewie on 2005-12-08
That little guy has always kind of bugged me too, and for the same reason. I'm not a guy. You actually couldn't get much farther from my appearance. At any rate, I am not much of an artist, but I have gone into the GIMP and edited him. The idea was to make him look like me, but I decided the black hair went better with the black outline than brown. If you want, you can rename the current stock_person.pngs and replace them with these.

---

### Post by IdolizingStewie on 2005-12-08
Well hell. I went to all four places aysiu found, renamed the dude stock_person_old.png, and copied in my pics as stock_person.png, and the guy's still there when I lock the screen. I don't get it.

---

### Post by videodrome on 2005-12-08
I was all excited and was about to go and rename all of those pics that Aysiu found. Now I hear that it doesn't work. Crap!

---

### Post by taurus on 2005-12-08
Maybe log out and back in could cure the problem!!!

---

### Post by IdolizingStewie on 2005-12-08
No, I have since rebooted and it still doesn't change that guy. It changes the default login photo in gnome that people thought she was talking about earlier.

---

### Post by aysiu on 2005-12-08
So stock_person isn't the right icon, then. I'll dig around and see if I can find the right one...

---

### Post by aysiu on 2005-12-09
I did a search for every single image in /usr and /etc, and I couldn't find a single other image besides stock_person.png that looks like that. It's got to be that icon.

How do we get it to refresh, though? That's the question. A reboot doesn't do it. Logging out and logging back in doesn't do it. Any other ideas?

**Edit**: I'm totally baffled. I looked all over the entire filesystem for *.png, *.jpg, *.gif, *.svg, and *.xpm. I couldn't find it. It's not the stock_person icon. I just looked at it again, and it's a very low-res icon.

---

### Post by matthew on 2005-12-09
[quote=aysiu]I did a search for every single image in /usr and /etc, and I couldn't find a single other image besides stock_person.png that looks like that. It's got to be that icon.

How do we get it to refresh, though? That's the question. A reboot doesn't do it. Logging out and logging back in doesn't do it. Any other ideas?

**Edit**: I'm totally baffled. I looked all over the entire filesystem for *.png, *.jpg, *.gif, *.svg, and *.xpm. I couldn't find it. It's not the stock_person icon. I just looked at it again, and it's a very low-res icon.[/quote]I'm guessing that is where the original icon is stored but that whichever graphic is in use currently is copied to another location using a different name. I will also do some searching and see if I can uncover the mystery of the bearded man.

** Edit:** That or there is just a link created to whichever file is chosen...which would be even more difficult to find than an actual graphics file. Now to try to find where a link for that could be stored.

** Edit2**: I found something that seems probable, give it a try. There's a hidden graphics file in /home that doesn't have a graphics filename extension, but I think it's what we are looking for. Copy the file you want as your face to this location with this name:

/home/.face

and see if that works for you. 

Note to self: got to remember that in *nix everything is a file...configurations, settings, everything. If this isn't the solution, the solution will still probably be contained in a file of some sort...maybe .xml, but almost certainly a hidden file in /home or a subfolder.

---

### Post by missmoondog on 2005-12-09
searched and found this thread. same issue here. the about me or login photo options don't do a thing for me either.

---

### Post by matthew on 2005-12-09
[quote=missmoondog]searched and found this thread. same issue here. the about me or login photo options don't do a thing for me either.[/quote]See my previous post that I was editing while you were commenting. I think it will work.

---

### Post by aysiu on 2005-12-09
On my own computer, I don't need to change this, as I never switch users (my wife has her computer; I have mine).

I really want to get to the bottom of this, though, for three reasons:

1. I'm just curious.
2. I want to help out other users, and this seems to be an annoyance for some people.
3. I don't like the idea of not being able to customize something--I thought that was the whole idea behind Linux... it's all transparent.

I'll do some more searching later.

---

### Post by matthew on 2005-12-09
[quote=aysiu]I really want to get to the bottom of this, though, [/quote]Me too, for similar reasons. I may have a lead, see post #20 above.

---

### Post by d1337 on 2005-12-09
The hidden file, /home/.face is the file that is changed when you add the pic to the about me part of prefs...but that doesn't fix the guy either.  I've been wanting to do this for awhile myself and glad to see that I'm not the only one wanting to customize this icon.

d1337

---

### Post by matthew on 2005-12-09
[quote=d1337]The hidden file, /home/.face is the file that is changed when you add the pic to the about me part of prefs...but that doesn't fix the guy either. I've been wanting to do this for awhile myself and glad to see that I'm not the only one wanting to customize this icon.

d1337[/quote]
BTW, the way I mentioned in post #9 does work to change the icon, but only if you are using Gnome as your desktop.

Hmm... I just looked. Yep, the hidden file changes if I use the method I just referred to, but changing the hidden file directly does NOT change the icon being used. There must be another file (I'm leaning toward a text file or xml) that holds the saved configuration...I'm off to look some more.

---

### Post by d1337 on 2005-12-09
As sad as this will sound, I scrolled through all 12,750 (no joke) of .png files and only located him 4 times all in /usr/share/icons/hicolor/ under various sizes/generic.  Changed him in all four instances, shutdown/rebooted for grins and had no changes made.  I'm leaning towards text or xml as well...but I'll keep looking.

d1337

---

### Post by matthew on 2005-12-09
I've looked through just about everything in /home and I'm not finding anything. I know lots of configuration files are kept in /etc so I'm going to look there next.

Edit: nope. not there

---

### Post by devnulljp on 2005-12-09
This doesn't work for me - I did that already, but the beardedweirdie remains in the lock screen/screensaver login screen.


[QUOTE=matthew]System->Preferences->About Me
Click on the icon.
Either direct it to use another picture or click on "no icon."
Personally, I use the attached...[/QUOTE]

---

### Post by matthew on 2005-12-09
[quote=devnulljp]This doesn't work for me - I did that already, but the beardedweirdie remains in the lock screen/screensaver login screen.[/quote]Hmm... <blushing> I just noticed it doesn't for me either. I didn't actually test that but I had just looked at System->Preferences->About Me and it was changed there.

As I am looking at the lock screen login I am beginning to wonder if that image is just a part of the login screen and not actually changable?

...man, I really need to stop posting when I'm tired and just *think* I understand what I am writing about.

---

### Post by d1337 on 2005-12-09
I agree...that image is not an icon or a .png anywhere that I can see.  But if it is just a file, it seems that it could be edited or replaced.  I rely on my screen locking at work...and sometimes at home.  This would be just another hack/customization...like setting up a grub splash image.  IMHO, though, it'd be cool at least for those of us that use it.  I'll keep looking around a bit.

d1337

---

### Post by d1337 on 2005-12-09
Maybe I'll stop now.  Came across this page regarding [XScreenSaver]("http://www.jwz.org/xscreensaver/toolkits.html") and it appears that this may be far beyond my scope.  The author makes very valid points regarding security and the tweaking of the unlock dialog.  I'm just gonna leave the bearded guy be bearded for now.

d1337

---

### Post by matthew on 2005-12-09
[quote=d1337]Maybe I'll stop now.  Came across this page regarding [XScreenSaver]("http://www.jwz.org/xscreensaver/toolkits.html") and it appears that this may be far beyond my scope. The author makes very valid points regarding security and the tweaking of the unlock dialog. I'm just gonna leave the bearded guy be bearded for now.[/quote]Hmm... Sounds like a good idea. I hate it when I encounter something I can't solve. :(

---

### Post by IdolizingStewie on 2005-12-10
[QUOTE=matthew]I hate it when I encounter something I can't solve. :([/QUOTE]
I know the feeling. I got much more interested in changing him once I realized I couldn't with my current knowledge. Wasn't expecting to find that nobody could. That's most of the reason I came to Linux, lol. Thanks for trying, though, guys.

---

### Post by videodrome on 2005-12-10
What a shame. The icon is not female-friendly and with a server install + xubuntu (no gnome) there is apparently no way to change it. Bummer.

---

### Post by missmoondog on 2005-12-11
[QUOTE=d1337]Maybe I'll stop now.  Came across this page regarding [XScreenSaver]("http://www.jwz.org/xscreensaver/toolkits.html") and it appears that this may be far beyond my scope.  The author makes very valid points regarding security and the tweaking of the unlock dialog.  I'm just gonna leave the bearded guy be bearded for now.

d1337[/QUOTE]

same here. hate it when i can't fix something that isn't broke!!

even with all this fine help.

thanks for all the effort.

---

### Post by matthew on 2005-12-11
[quote=missmoondog]same here. hate it when i can't fix something that isn't broke!![/quote]LOL. My computer motto (on non-production machines) is "if it ain't broke, you haven't played with it enough lately." :)

---

### Post by DonPachi on 2005-12-11
Is there no one who can save us from Goatee Man!?

---

### Post by aysiu on 2005-12-11
[QUOTE=DonPachi]Is there no one who can save us from Goatee Man!?[/QUOTE] It seems that way...

---

### Post by ranf on 2005-12-12
[QUOTE=DonPachi]Is there no one who can save us from Goatee Man!?[/QUOTE]
Look here: [http://bugzilla.ubuntu.com/show_bug.cgi?id=14571](http://bugzilla.ubuntu.com/show_bug.cgi?id=14571)
Make a nice picture and send it to Oliver. Maybe he takes it. Maybe not.

---

### Post by shekhark on 2006-02-08
It's frankly absurd that this image is fixed and cannot be changed. Someone needs to fix this in the next release. At least for GNOME, the image should come from the user-specified one in the 'Login Photo' or 'About Me' preference panels (and the fact that there are two separate sets of preferences for this function is also anomalous). 

The bearded man must die!

---

### Post by videodrome on 2006-09-24
Has this been fixed for Edgy? Hope so!

---

