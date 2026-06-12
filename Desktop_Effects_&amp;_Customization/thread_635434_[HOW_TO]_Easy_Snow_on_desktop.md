---
title: "[HOW TO] Easy Snow on desktop"
date: 2007-12-08
forum: Desktop Effects &amp; Customization
---

### Post by jryprt on 2007-12-08
1st credit go to Espreon for posting the script.
2nd credit go to Ankara23 for posting the snowflake .png
3rd credit go to Roofie for posting the extra snowflakes on Post #4

Make sure you have compizconfig-settings-manager installed.

#1 Download the attached script into your home folder, be sure (save to disk) is used .
#2 Code in Terminal " sh snowscript.sh " after its done close the Terminal .
 Now you have snow But it is Square snowflakes . Now lets get snowflakes.
#3 Click on the attached (3) snow.png a new window with the snowflake will come up right click(if a new box does not open right click the .png & save as) will come up right click & save page as a new box should say.
#4 Name the snow.png & Save in folder (your user name) should be there.
#5 Now open Home Folder look for snow.png & leave it alone for now.
#6 Now in the Terminal code " sudo nautilus " do your password hit enter Then the root file will open.
#7 Then double click on file system.
#8 Then double click on home 
#9 Then double click on (your user name) when you are in your user file
 click on view & click on show hidden files or Ctrl+h 
#10 Then double click on .compiz file after it opens copy the (3) snow.png to the .compiz file
 or grab the (3) snow.png & do drag & drop to the .compiz file thats what I did close the files & close the Terminal.
#11 Now go to System>Preferences>Advanced Desktop Effects Setting & click.
#12 Go to Extras & find snow click on it,then click on Enable Snow
#13 Then click on the Textures tab, click add , a Edit Snow Textures box opens. 
#14 On the right side of the box click on the file icon , a open file box comes up.
#15 Click on .compiz hit open (if you cannot find .compiz file then hit Ctrl + h to show hidden files) 
#16 Now click on snow.png hit open, now we are back to Edit Snow Textures box hit OK. 
 Repete steps 13-14-15-16 to get more snowflakes. Now close all boxes & files .
 Now restart your pc (I had too to get it to work)
 Super key + F3 turns in on & off
 I Hope It Works For You let us know

 EDIT: Here is some .png for Halloween remove snow .png put it Halloween .png on Post #20
 EDIT: just right click on the Attached Images of the snowflake than save page as.

---

### Post by Roofie on 2007-12-09
Works great !!
Thank you \\:D/

---

### Post by jryprt on 2007-12-09
Thanks for letting me know it works.

The only thing I see I need to add is just right on the Attached Images of the snowflake than save page as.

---

### Post by Roofie on 2007-12-09
My wife like the pluggin so much i added some more snow flake pics.
So with different looking flakes coming down it looks more real.
I figure i cant help with much here on the forum with fixxing things,so
I can offer some more snow flake pics to add for the pluggin.
To use the snow flake pics just right click save as.
Here is a pic from my desktop 

[center][IMG]http://i108.photobucket.com/albums/n38/CanadianWarez/Screenshot.png[/IMG][/center]

---

### Post by jryprt on 2007-12-09
Thanks they do look nice. You can help me how did you get the screenshot 
in your post without it being an  attachment ? I have the screenshot know I would like to show it , it to big for attachment.

---

### Post by Roofie on 2007-12-09
I use photobucket for hosting pictures.
Does not take long to register and they have a free account.
I find host sites are better they dont leach bandwith off the forums :)

---

### Post by jryprt on 2007-12-09
> **Roofie said:**
> I use photobucket for hosting pictures.
Does not take long to register and they have a free account.
I find host sites are better they dont leach bandwith off the forums :)
Will I got photobucket account I still can not get it to upload its to big or not the right URL standards for the forum.

---

### Post by jryprt on 2007-12-09
Mine at my home

---

### Post by jryprt on 2007-12-09
[IMG]http://i267.photobucket.com/albums/ii305/jryprt/home.png[/IMG]

---

### Post by nikoPSK on 2007-12-09
thanks. but you could get it from git. (I am a terminal/ BASH freak... don't blame me:p)

---

### Post by apothecaryaaron on 2007-12-10
Wow.  That is beautiful.  Thanks for the how-to.  Worked well on the first try.

---

### Post by apothecaryaaron on 2007-12-10
Something else worth noting.  The snow stays animated and falls in the cube.  If you have transparency set at a decent level, it appears to be snowing from above and below the cube as well.  SWEET!

---

### Post by pointfivezero on 2007-12-10
It worked very well for me. Thank you!

---

### Post by mikeg113 on 2007-12-10
Ubuntu logo snow!

---

### Post by jryprt on 2007-12-15
[IMG]http://i267.photobucket.com/albums/ii305/jryprt/11-1.png[/IMG]

---

### Post by nmopal on 2007-12-15
I'm sorry if my first post is a cry for help, but I've looked at every website on how to get this to work with no help at all. I did everything you said step by step THREE TIMES and I keep getting errors.

Here is what I get:

```
nmopal@kevin-desktop:~$ sh snowscript.sh
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
--22:06:39--  http://gitweb.beryl-project.org/?p=fusion/plugins/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e0114569c8ad4e083;sf=tgz
           => `snow.tar.gz'
Resolving gitweb.beryl-project.org... 195.114.19.35
Connecting to gitweb.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [ <=>                                 ] 8,710         49.33K/s             

22:06:40 (49.11 KB/s) - `snow.tar.gz' saved [8710]

drwxrwxr-x root/root         0 2007-08-06 10:48 snow/
-rw-rw-r-- root/root     16338 2007-08-06 10:48 snow/Makefile
-rw-rw-r-- root/root        14 2007-08-06 10:48 snow/plugin.info
-rw-rw-r-- root/root     17013 2007-08-06 10:48 snow/snow.c
-rw-rw-r-- root/root      3757 2007-08-06 10:48 snow/snow.xml.in
convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h/bin/sh: --header=build/snow_options.h: not found
make: *** [build/snow_options.h] [COLOR="Red"]Error 127[/COLOR]
bcop'ing  : build/snow.xml -> build/snow_options.h/bin/sh: --header=build/snow_options.h: not found
make: *** [build/snow_options.h] [COLOR="Red"]Error 127[/COLOR]
```

I also tried manually installing xglsnow-0.2.0 but when I get to the "make" option in the terminal, I get attacked with errors. I managed to get most of the errors solved by installing packages for Beryl, but the last one "Package SM" has 400+ different programs Id have to download and it wont tell me individual ones I need. :/

I'm new to the Linux thing and I'm running Ubuntu 7.04 Feisty Fawn, any help would be gladly appreciated. I'll check this thread frequently. 

Thanks.

---

### Post by Brindled on 2007-12-16
sorry to hear that, nmopal. the OP is running gutsy 7.10. i'm not sure if that has any bearing on the outcome. all the other users that have posted that it's working are also.

it worked for me.

thanks jryprt for posting the How-to, and thanks to Roofie for posting the extra snowflakes.

---

### Post by jryprt on 2007-12-16
> **nmopal said:**
> I'm sorry if my first post is a cry for help, but I've looked at every website on how to get this to work with no help at all. I did everything you said step by step THREE TIMES and I keep getting errors.

Here is what I get:

```
nmopal@kevin-desktop:~$ sh snowscript.sh
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
--22:06:39--  http://gitweb.beryl-project.org/?p=fusion/plugins/snow;a=snapshot;h=01d0ff6ec71dae4699bc990e0114569c8ad4e083;sf=tgz
           => `snow.tar.gz'
Resolving gitweb.beryl-project.org... 195.114.19.35
Connecting to gitweb.beryl-project.org|195.114.19.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [application/x-gzip]

    [ <=>                                 ] 8,710         49.33K/s             

22:06:40 (49.11 KB/s) - `snow.tar.gz' saved [8710]

drwxrwxr-x root/root         0 2007-08-06 10:48 snow/
-rw-rw-r-- root/root     16338 2007-08-06 10:48 snow/Makefile
-rw-rw-r-- root/root        14 2007-08-06 10:48 snow/plugin.info
-rw-rw-r-- root/root     17013 2007-08-06 10:48 snow/snow.c
-rw-rw-r-- root/root      3757 2007-08-06 10:48 snow/snow.xml.in
convert   : snow.xml.in -> build/snow.xml
bcop'ing  : build/snow.xml -> build/snow_options.h/bin/sh: --header=build/snow_options.h: not found
make: *** [build/snow_options.h] [COLOR="Red"]Error 127[/COLOR]
bcop'ing  : build/snow.xml -> build/snow_options.h/bin/sh: --header=build/snow_options.h: not found
make: *** [build/snow_options.h] [COLOR="Red"]Error 127[/COLOR]
```

I also tried manually installing xglsnow-0.2.0 but when I get to the "make" option in the terminal, I get attacked with errors. I managed to get most of the errors solved by installing packages for Beryl, but the last one "Package SM" has 400+ different programs Id have to download and it wont tell me individual ones I need. :/

I'm new to the Linux thing and I'm running Ubuntu 7.04 Feisty Fawn, any help would be gladly appreciated. I'll check this thread frequently. 

Thanks.


Try posting in the  Absolute Beginner Talk someone mite know what  the error 
is , tell them what you are doing & what you did .

---

### Post by Nephron on 2007-12-16
No need to install beryl for their snow pngs, they have them on the interweb for your thieving pleasures:

[http://www.beryl-themes.org/content/show.php/Snowflakes+Pack+for+Snow+Plugin?content=50346&PHPSESSID=71a604f8ceb528ed4aeca926ff1d1b78]("http://www.beryl-themes.org/content/show.php/Snowflakes+Pack+for+Snow+Plugin?content=50346&PHPSESSID=71a604f8ceb528ed4aeca926ff1d1b78")

Enjoy.

---

### Post by jryprt on 2007-12-17
Here are some .png for Halloween  just remove snow .png put in Halloween .png

---

### Post by shifty2 on 2007-12-17
worked brilliantly. Nicely seasonal, cheers

---

### Post by jflaker on 2007-12-17
that is awesome!  Anyone have more snowflakes than were already posted?

---

### Post by jryprt on 2007-12-17
> **jflaker said:**
> that is awesome!  Anyone have more snowflakes than were already posted?

Here is some [http://graphicssoft.about.com/od/freedownloads/l/blfreepng05.htm?rd=1](http://graphicssoft.about.com/od/freedownloads/l/blfreepng05.htm?rd=1)

---

