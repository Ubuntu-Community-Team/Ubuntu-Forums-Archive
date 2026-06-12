---
title: "Auto Wallpaper changer of ubuntu"
date: 2008-05-18
forum: Desktop Environments
---

### Post by carfield on 2008-05-18
I am using GNOME, in the old day I can use an application call chbg to change wallpaper, but now it doesn't work, is that any similar application for me to do that?

---

### Post by Superevil on 2008-05-18
I used Desktop Drapes and Wallpapoz both of which are available through the add/remove apps. Personally I'd like something like OS X has where you can change the wallpapers every 5 seconds or so and they blend from one to the other.

---

### Post by esteckis on 2008-05-18
What I am using under the screenelts program is called Gnome wallpaper. You can have it change wallpapers from your folder, or download wallpaper Gnome art and change wallpapers that way. It's nice to have some refreshing wallpapers from Gnome art.

---

### Post by angry_johnnie on 2008-05-19
There is a really nice app available in the repos, called **wallpaper-tray**.

It stays on the system tray, and looks for images in any directory of your choice, and then changes them at certain user-specified intervals (the minimum interval being 1 minute).

There is another one, called gbackground, which does the same, but can be set to change the background image at a faster rate (any given number of seconds --even 1 second).  It is also available in the repositories.

A, perhaps, "geekier" approach, would be to write an xml file to set the background and then change it after some time, with --even-- a nice fade in/out transition.  Then you could just go to **system > preferences > appearance > background > add > all files**, and select your xml script.

It would look something like this:

```
<background>
	<static>
		<duration>1.0</duration>
		<file>/background/image/one</file>
	</static>	
	<transition>
		<duration>2.0</duration>
		<from>/background/image/one</from>
		<to>/background/image/two</to>
	</transition>
	<static>
		<duration>2.0</duration>
		<file>/background/image/two</file>
	</static>
	<transition>
		<duration>2.0</duration>
		<from>/background/image/two</from>
		<to>/background/image/one</to>
	</transition>
	<static>
		<duration>1.0</duration>
		<file>/background/image/one</file>
	</static>
</background>
```

where **duration** is measured in seconds.

But then, if you ask me, I'd say wallpaper-tray. :-)
It's a lot easier.

---

### Post by carfield on 2008-05-20
Wallpaper_tray look great, but where does the config file put in home directory?

---

### Post by angry_johnnie on 2008-05-21
> **carfield said:**
> Wallpaper_tray look great, but where does the config file put in home directory?

:o It's either not there, or it's called something completely random, but you can change anything in its configuration just by right-clicking on the tray icon.

---

### Post by carfield on 2008-05-21
My issue is I would like to have a hidden directory to be added, like "/home/user/.friends" How can I do that for Wallpaper_tray??

---

### Post by angry_johnnie on 2008-05-22
I'm not sure about that... I'm not currently using wallpaper-tray, but it doesn't show hidden directories, does it?

What happens if you type in the entire path to the directory of your choice?

you know, like /home/you/.friends

If it works, well... it works :-)... if not, then I don't think it will let you add hidden directories.

---

### Post by carfield on 2008-05-22
cool, it work

---

### Post by dage on 2008-05-23
i'm using wallpaper-tray, it's really an user-friendly program. Thanks.

---

### Post by stinger30au on 2008-05-24
thanks for the info.
i was feeling kinda dumb for a while as i searched first of via applicatoins > add remove and could not find wallpaper changer.

duh!!!!

system > administration > synaptic

searched on wallpaper and installed.

Thanks!

---

### Post by carfield on 2008-05-24
> **stinger30au said:**
> thanks for the info.
i was feeling kinda dumb for a while as i searched first of via applicatoins > add remove and could not find wallpaper changer.

duh!!!!

system > administration > synaptic

searched on wallpaper and installed.

Thanks!
a lot of application do like this, at least all applications mentioned in this thread

---

### Post by guywithcable on 2008-08-20
For anyone interested in this. I wrote a shell script to generate an XML file which will give you the fading transition effect like in Mac OS X.

Thanks to angry_johnnie for pointing out how to do this.

Run the script in a directory full of all your wallpapers, then go to **system > preferences > appearance > background > add > all files**, and select wallpaper-set.xml.

---

### Post by angry_johnnie on 2008-08-21
> **guywithcable said:**
> For anyone interested in this. I wrote a shell script to generate an XML file which will give you the fading transition effect like in Mac OS X.

That is way cool. :-)

---

### Post by tweak on 2008-08-21
> **guywithcable said:**
> For anyone interested in this. I wrote a shell script to generate an XML file which will give you the fading transition effect like in Mac OS X.

Thanks to angry_johnnie for pointing out how to do this.

Run the script in a directory full of all your wallpapers, then go to **system > preferences > appearance > background > add > all files**, and select wallpaper-set.xml.

Any way to increase the smoothness of the transition? I'm loading 1600x1200 images and they chunk the system quite heavily when performing anything other than a very fast transition, defeating the beauty of it!

---

### Post by guywithcable on 2008-08-21
> **tweak said:**
> Any way to increase the smoothness of the transition? I'm loading 1600x1200 images and they chunk the system quite heavily when performing anything other than a very fast transition, defeating the beauty of it!

You could tweak the time for the transition to give you your desired effect. I found that smaller transition times give me smoother transitions, but it could be different for you. Just open up the script in gedit and find and change the value in bold below:

```
                echo "    </static>" >> wallpaper-set.temp
                echo "    <transition>" >> wallpaper-set.temp
                echo "        <duration>**1.0**</duration>" >> wallpaper-set.temp
                echo "        <from>$f</from>" >> wallpaper-set.temp
```

---

### Post by guywithcable on 2008-08-21
I forgot to post that if you want a different duration for your wallpapers, you can give it the duration as a command line argument:

Usage: ./Wallpaper-Transition-XML-Generator.sh [duration]

It is duration in seconds and the default is 300 (5 minutes).

---

### Post by tweak on 2008-08-21
yeah I've fiddled the various transition times without luck. I suspect that the sheer size of the images vs the relatively low cpu speed is just the nature of the beast.

cheers!

---

### Post by guywithcable on 2008-08-21
> **tweak said:**
> yeah I've fiddled the various transition times without luck. I suspect that the sheer size of the images vs the relatively low cpu speed is just the nature of the beast.

cheers!

Do they have to be that big? Have you tried decreasing their size or quality? It would help them load faster.

---

### Post by tweak on 2008-08-21
the hell with that, screen real estate is more important to me :)

---

### Post by guywithcable on 2008-08-21
> **tweak said:**
> the hell with that, screen real estate is more important to me :)

Haha. Yeah. It's too bad though, cause Mac OS X pulls it off pretty nicely even with huge pictures.

---

### Post by tweak on 2008-08-21
> **guywithcable said:**
> Haha. Yeah. It's too bad though, cause Mac OS X pulls it off pretty nicely even with huge pictures.

Yeah I'm the token linux user in an office full of mac zealots. Gotta admit some things are done well on osx, and they seize every opportunity to make mention of those things and rub it in.....the ******* :P

---

### Post by guywithcable on 2008-08-21
> **tweak said:**
> Yeah I'm the token linux user in an office full of mac zealots. Gotta admit some things are done well on osx, and they seize every opportunity to make mention of those things and rub it in.....the ******* :P
There's always one thing they'll never, ever beat... the price. :)


not to mention, the filesystem support, compiz fusion, the package managers, the community, the customization, the various distributions, the free learning resources, etc.

---

### Post by tweak on 2008-08-21
haha preaching to the choir bro! :D

---

### Post by angry_johnnie on 2008-08-22
> **guywithcable said:**
> There's always one thing they'll never, ever beat... the price. :)


not to mention, the filesystem support, compiz fusion, the package managers, the community, the customization, the various distributions, the free learning resources, etc.

Speaking of the "free learning resources..."

I have taken the liberty to borrow your script...
and then I took the liberty to re write it...
and finally I took the liberty to make a debian package out of it...

I kept your name in there, although I didn't include your email... but you can add that later (and then we can call that version 1.02 :p).

I can still think of a few things to add to it... but then I'm moving to another town... like... right now... (I shouldn't even be here, really), so that means I won't have time to sit down and think about it for at least another three or four days.  So, why don't you try it and see what you can make of it.

I have also attached a compressed folder with all the included files. I would have written a changelog... but then I'm lazy like that :p... no... really I have to get going.

If you install it, you'll find it under **System > Preferences > XML Wall**.

Cheers :-)



P.S.  I just came back to warn you:  Don't you dare make fun of my silly icon... it's a work of aht! :p

---

### Post by guywithcable on 2008-08-24
Very nice! I made a few modifications and fixed a bug when you give it a folder path with a space. I also wrote error protection for it. I drew a new icon that is a little more relevant to its name. (BTW I like the name) Also included my email. :)  Here is version 1.02 and source.

PS: The icon you have isn't bad, it's just not relevant. ;)

---

### Post by guywithcable on 2008-09-05
So how difficult would it be to get XML Wall included in an Ubuntu repository?

---

### Post by lovinglinux on 2008-09-07
> **guywithcable said:**
> Very nice! I made a few modifications and fixed a bug when you give it a folder path with a space. I also wrote error protection for it. I drew a new icon that is a little more relevant to its name. (BTW I like the name) Also included my email. :)  Here is version 1.02 and source.

PS: The icon you have isn't bad, it's just not relevant. ;)
[I]
It isn't working for me. I get an error message during the xml file creation. There is "wallpaper-set.temp" file in the xml-wall directory, but it is empty.[/I]

[COLOR="Red"]**Edit: Apparently you cannot specify a name with spaces. That is why it wasn't working. Works perfectly now.**[/COLOR]

How difficult would be to create several xml files and schedule a different file for each day of the week? I want to load a different set of images each day.

---

### Post by lovinglinux on 2008-09-07
> **lovinglinux said:**
> How difficult would be to create several xml files and schedule a different file for each day of the week? I want to load a different set of images each day.

After some research, here it is how to load different xml-wall sets on a daily basis:

1 - Run System > Preferences > XML Wall and create one set of images for each day with the following names  (without quotes):

"mon", "tue", "wed", "thu", "fri", "sat" and "sun"

2 - Type the following command in the Terminal to create a file named .change.cron

```
gedit .change.cron
```

3 - Add the following lines to the file, replacing "/home/me/" with your user path

```
01 00 * * 0 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/sun.xml
01 00 * * 1 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/mon.xml
01 00 * * 2 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/tue.xml
01 00 * * 3 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/wed.xml
01 00 * * 4 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/thu.xml
01 00 * * 5 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/fri.xml
01 00 * * 6 gconftool -t string -s /desktop/gnome/background/picture_filename /home/me/.xml-wall/sat.xml
```

You can tweak the exact time the wallpaper set will be changed by replacing the first four values on each line above. 

This is how a cron job is layed out:

minute (0-59), hour (0-23, 0 = midnight), day (1-31), month (1-12), weekday (0-6, 0 = Sunday), command

In this example the cron job will change the wallpaper set every day at the first minute after midnight. I'm not sure if the machine needs to be turned on to work if you set a specific hour and minute, but if you set the second value to "*" it will run the script every hour.

4 - Run System > Preferences > Sessions and add a startup program like the one below. Don't forget to replace "/home/me" with your user path.

Name: XML Wall Daily Cron
Command: crontab /home/me/.change.cron
Comment: XML Wall cron job for daily xml file

That's it. There is probably a more elegant way of doing this, but this is the best I could do.

---

### Post by guywithcable on 2008-09-08
> **lovinglinux said:**
> [I]
It isn't working for me. I get an error message during the xml file creation. There is "wallpaper-set.temp" file in the xml-wall directory, but it is empty.[/I]

[COLOR=Red]**Edit: Apparently you cannot specify a name with spaces. That is why it wasn't working. Works perfectly now.**[/COLOR]

How difficult would be to create several xml files and schedule a different file for each day of the week? I want to load a different set of images each day.

Thanks for telling me about that error. I've fixed it and released 1.02.1 (Attached) which will let you specify a file name with spaces. Now there should be no problem with spaces anywhere. :)

The daily set feature would be pretty cool. I could try to expand the script to automate that process as well.

---

### Post by lovinglinux on 2008-09-08
> **guywithcable said:**
> Thanks for telling me about that error. I've fixed it and released 1.02.1 (Attached) which will let you specify a file name with spaces. Now there should be no problem with spaces anywhere. :)

The daily set feature would be pretty cool. I could try to expand the script to automate that process as well.

I'm glad to help with my limited knowledge about Linux :biggrin:

It would be awesome if you could expand the script to automate the daily feature. It's working pretty fine here and it's very cool. I have 7 different wallpaper sets with posters of TV shows that I like to watch, so my desktop presents me the Primetime schedule of the day.

---

### Post by guywithcable on 2008-09-08
To everyone who has downloaded XML-Wall, you can either look for updates here, or when I am done migrating from Mambo to Joomla on my website, it will be available there. I'm going to make an official home for it on [SciActive.com]("http://www.sciactive.com"). It will be my first maintained Linux program on SciActive. :)

---

### Post by Dragonbite on 2008-09-08
KDE allows you to change the wallpaper at any increment (*from 1 minute to 1 day ... I usually use 1 hour*) and Xfce allows you to change every time you bootup, why has Gnome not implemented this feature built in?

---

### Post by guywithcable on 2008-09-08
> **Dragonbite said:**
> KDE allows you to change the wallpaper at any increment (*from 1 minute to 1 day ... I usually use 1 hour*) and Xfce allows you to change every time you bootup, why has Gnome not implemented this feature built in?

It has, it just hasn't a GUI to set it up. That is what XML-Wall is for. XML-Wall doesn't provide any new feature to Gnome, it just helps you take advantage of it, without having to write the complicated XML script yourself.

---

### Post by FokkerCharlie on 2008-09-23
Cool!

I love XML-Wall.  Are you going to be further advancing the project?  If so, a feature request.  Could we have a GUI that allows us to modify the settings without going through the whole setup (not that it's really long, but you know...) every time?

This is a great script- cheers!

Charlie

---

### Post by guywithcable on 2008-09-23
> **FokkerCharlie said:**
> Cool!

I love XML-Wall.  Are you going to be further advancing the project?  If so, a feature request.  Could we have a GUI that allows us to modify the settings without going through the whole setup (not that it's really long, but you know...) every time?

This is a great script- cheers!

Charlie

Thanks for the compliments. Yes, I will be working on it in the future, but right now I have very little time. I'm in college and have two jobs. When I have more time I'll put it up on SciActive and work on it there. I'll also try to include it in one of the repositories.

---

### Post by boingboing on 2008-10-15
Hello, the fade effect doesn't work for me, even if the wallpaper switch every 20 seconds as I asked.

So no fade transition...can you help me? I have Ubuntu 8.04 and an ATI HD 2600 Pro with latest EnvyNG drivers.

Thanx !! ):P

---

### Post by I wanted to leave on 2008-10-16
This works great, though no transition effects for me either...

For future revisions, would it be difficult to include a day/night transition option, using the same wallpaper but in varying shades according to the time of day?

---

### Post by MR.UNOWEN on 2008-10-30
This is really good, but it's just a little buggy. Is the processing done in real time or does it do some calculations in advance? Could a setting for frame rate be added? The only issue I have with it is the choppy frame rate.

---

### Post by guywithcable on 2008-10-30
> **MR.UNOWEN said:**
> This is really good, but it's just a little buggy. Is the processing done in real time or does it do some calculations in advance? Could a setting for frame rate be added? The only issue I have with it is the choppy frame rate.

Unfortunately I can't do anything about the frame rate. It's Gnome that produces the effect. You could submit something to Gnome to try and get it improved.

---

### Post by MR.UNOWEN on 2008-10-30
Where do I post a request for it to be improved???

---

### Post by guywithcable on 2008-10-30
> **MR.UNOWEN said:**
> Where do I post a request for it to be improved???

That's a good question. You could use the Ubuntu Brainstorm. You might also try Gnome's launchpad at [https://launchpad.net/gnome](https://launchpad.net/gnome).

---

### Post by weezerisrock on 2008-11-08
Brilliant!  I've been looking for something that would do fades between desktop changes!  However for some reason my fades are not working atm.  Is there something I should look at? 

 Also,  if There is anyway I can help please let me know.  I don't really know scripting of anykind but I would be willing to do just about anything I can for this project, including learning the scripting you guys are using.

And now for my recommendations for future releases.  During the setup process it has sliders for seconds between fades and fade times.  If you move that slider on the seconds its practically impossible to get the exact number you want after that.  Could there be a way to make it to where you could type your numbers in as well as the sliders?

Same thing with the transistions, it would be nice to be able to put something in other than a whole second like.  1.25 or 1.5 seconds.

This is awesome!  (as soon as I get this dadgum fade to work) and please let me know if there is something I can do to help!

---

### Post by jnewm on 2009-02-05
This really is a fantastic little program!  Thank you all so much. 
-Jesse
:KS

---

### Post by euchrid33 on 2009-02-13
Yeah, wallpaper tray is great.

---

### Post by tsoumt1123 on 2009-03-17
> **lovinglinux said:**
> After some research, ....

......
......

4 - Run System > Preferences > Sessions and add a startup program like the one below. Don't forget to replace "/home/me" with your user path.

Name: XML Wall Daily Cron
Command: crontab /home/me/.change.cron
Comment: XML Wall cron job for daily xml file

That's it. There is probably a more elegant way of doing this, but this is the best I could do.


Thank you Guywithcable, your script helped me a lot, and the transition effect on my box acted perfectly, though I still spent hours to fix a bug that seemed to happen with two pipeline commands in the script. And I'd like to contribute a little more about 'autostart' of this method to those who are new to Linux or Ubuntu and whose computers do not run all the time. Instead of utilizing crontab in the autostart, I suggest simply putting the following command into it:
```
 
gconftool -t string -s /desktop/gnome/background/picture_filename /home/yourname/.xml-wall/`date +%a`.xml  
```
As a consequence, one has to follow the strict naming pattern such as "Mon.xml", "Tue.xml", "Wed.xml", ..., etc. for the command to work flawlessly. In this way, your wallpaper will keep in pace with the date whenever gnome desktop environment starts. I now have a pleasant desktop that changes its background periodically and automatically. Thank you very much for inspiring me, Guywithcable!

---

### Post by guywithcable on 2009-03-17
> **tsoumt1123 said:**
> Thank you very much for inspiring me, Guywithcable!

Glad I could help. :)

I'll be posting XML-Wall on [SciActive.com]("http://www.sciactive.com") and opening it up for more development in a few days. I'm probably going to start a forum on SciActive, and will create a forum for XML-Wall. :D

---

### Post by amirage on 2009-03-27
Hi there..

Nice xml. But a doubt - Why is the transition very choppy? I have send the wallpaper to change every 10 secs and the transition delay to stay at 5 seconds. When the wallpaper changes, it's quite choppy. Any idea why?

I'm running Ubuntu 8.10 with compiz and emerald in full blow.

Looking forward to your comments.

Amit

---

### Post by Ryan Yo on 2009-04-01
FYI: 

Jaunty has a nice visual effect for changing wallpapers which works really well with the 'wallpaper-tray' app in synaptic.

It looks great.

---

### Post by tbone7 on 2009-04-02
What's special with this visual effect you are describing?

---

### Post by Naz_Farooq on 2009-04-02
> **guywithcable said:**
> It has, it just hasn't a GUI to set it up. That is what XML-Wall is for. XML-Wall doesn't provide any new feature to Gnome, it just helps you take advantage of it, without having to write the complicated XML script yourself.

How can I find XML wallpapers. I have tried but could not find anything that changes wallpapers with the day passes.
Thanks a lot if you tell me how to do that.

---

### Post by lovinglinux on 2009-04-02
> **Naz_Farooq said:**
> How can I find XML wallpapers. I have tried but could not find anything that changes wallpapers with the day passes.
Thanks a lot if you tell me how to do that.

Follow these posts:

[http://ubuntuforums.org/showpost.php?p=5743890&postcount=29](http://ubuntuforums.org/showpost.php?p=5743890&postcount=29)

[http://ubuntuforums.org/showpost.php?p=6911741&postcount=46](http://ubuntuforums.org/showpost.php?p=6911741&postcount=46)

---

### Post by Naz_Farooq on 2009-04-02
> **lovinglinux said:**
> Follow these posts:

[http://ubuntuforums.org/showpost.php?p=5743890&postcount=29](http://ubuntuforums.org/showpost.php?p=5743890&postcount=29)

[http://ubuntuforums.org/showpost.php?p=6911741&postcount=46](http://ubuntuforums.org/showpost.php?p=6911741&postcount=46)

Thanks a lot.
I will try them in the evening.

---

### Post by Dragonbite on 2009-04-02
> **Ryan Yo said:**
> FYI: 

Jaunty has a nice visual effect for changing wallpapers which works really well with the 'wallpaper-tray' app in synaptic.

It looks great.

Is that GUI, or text-based?

I have a demonstration this coming Monday on Desktop Linux at the computer club and was thinking this could be a fun app to demonstrate finding, downloading and installing if it has an GUI so they could see it work AND see the feature of changing wallpapers.

---

### Post by Ryan Yo on 2009-04-03
> **Dragonbite said:**
> Is that GUI, or text-based?

It's GUI based. It took me forever to realize it wasn't really a stand-alone app, but an applet that you stick onto the Gnome panels (right-click -> "Add to Panel...").

This is where I put mine:
[IMG]http://api.photoshop.com/home_8da66861f94140c38484d29fbd4d20bb/adobe-px-assets/890191cf24954529b6c3f7f97fb80e1c[/IMG]

---

### Post by Ryan Yo on 2009-04-03
> **tbone7 said:**
> What's special with this visual effect you are describing?

It's at the very last part of the Gnome 2.26 changelog:

     "*New visual effects, such as the panels sliding in and out at login and logout, and **crossfading desktop backgrounds**.*"

It adds a slick fade when you change desktop backgrounds.

---

### Post by Giblet5 on 2009-04-03
> **Superevil said:**
> I used Desktop Drapes and Wallpapoz both of which are available through the add/remove apps. Personally I'd like something like OS X has where you can change the wallpapers every 5 seconds or so and they blend from one to the other.


Why stop there? You can use xwinwrap to play movies on your root window (aka background), in addition to throwing images up with any degree of opacity you choose.

I have a Qt3 GUI for xwinwrap sitting around somewhere, or you can find the GUI with a search for "qxwinwrap". I think xwinwrap is in the same tarball.

Here's the [tarball]("http://www.byteshuffler.com/qxwinwrap.tar.bz2") with binaries.

```
tar xjf qxwinwrap.tar.bz2
cd qxwinwrap
sudo cp qxwinwrap xwinwrap /usr/bin
qxwinwrap

```

You may want to turn off ARGB visuals, and you need to have a compositing manager running (eg, compiz).

Note: You're better off compiling it...

---

### Post by vaserlan on 2009-04-04
I'd like a different desktop background for each workspace. is this possible? Any help would be much appreciated. :)

---

### Post by lovinglinux on 2009-04-04
> **vaserlan said:**
> I'd like a different desktop background for each workspace. is this possible? Any help would be much appreciated. :)

There are a lot of threads about this:

[http://www.google.com/search?q=different+wallpaper+workspace+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=different+wallpaper+workspace+site%3Aubuntuforums.org&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by deekshlap on 2009-04-19
Ty so much for creating XML WALL, I've been looking for a wp-changer that has transition effects for over two days. Keep up the good work, hoping to see smoother fade effect on the next update, but this is good enough as it is :D.

Update: I would like to report a bug, when I reboot my laptop the XML WALL is working however the transition fade effect does not, the wallpaper just change normally. But after about 5-10 minutes it starts to work again.

Also Is there a GUI to configure XML WALL settings, currently when i click on the XML WALL in System-->Preferences-->XML WALL it only lets me choose a new directory of pictures.

---

### Post by guywithcable on 2009-04-20
> **deekshlap said:**
> Ty so much for creating XML WALL, I've been looking for a wp-changer that has transition effects for over two days. Keep up the good work, hoping to see smoother fade effect on the next update, but this is good enough as it is :D.

Update: I would like to report a bug, when I reboot my laptop the XML WALL is working however the transition fade effect does not, the wallpaper just change normally. But after about 5-10 minutes it starts to work again.

Also Is there a GUI to configure XML WALL settings, currently when i click on the XML WALL in System-->Preferences-->XML WALL it only lets me choose a new directory of pictures.

Well, as of now, there is no GUI for settings. However, most of the settings you'd want to change are Gnome's settings, so you can try gconf-editor. As for those bugs, unfortunately they are Gnome bugs, so I can't fix them. You can report them to Gnome though.

---

### Post by deekshlap on 2009-04-20
Where should I go to in gconf-editor to configure transitional effects?

---

### Post by guywithcable on 2009-04-20
> **deekshlap said:**
> Where should I go to in gconf-editor to configure transitional effects?

/desktop/gnome/background/

Not a lot there. :(

---

### Post by deekshlap on 2009-04-20
> **guywithcable said:**
> /desktop/gnome/background/

Not a lot there. :(

Looool hopefully next version will have more eye candies to satisfy my sweet-tooth. :P

---

### Post by deekshlap on 2009-04-25
Ack, bad news XML Wall seems to have stop working in 9.04. The fade doesn't work any more and even the wallpaper doesn't change. :(

---

### Post by tbone7 on 2009-04-25
It works for me in Jaunty..

---

### Post by Bob63 on 2009-04-25
> **deekshlap said:**
> Ack, bad news XML Wall seems to have stop working in 9.04. The fade doesn't work any more and even the wallpaper doesn't change. :(
For me, the wallpaper changes, but no transitions. I'm going to run XML Wall again and see if rebuilding the settings will fix it and report back.

EDIT: Re-running XML Wall did NOT fix the transition issues. I'll check and see if it might be something with Compiz or maybe even the NVIDIA driver.

---

### Post by guywithcable on 2009-04-25
It's working for me on 9.04, partially. The transitions are not working for me either. :( Can you paste the output from:
```
lspci
```and
```
lshw -c video
```

---

### Post by Bob63 on 2009-04-26
> **guywithcable said:**
> It's working for me on 9.04, partially. The transitions are not working for me either. :( Can you paste the output from:
```
lspci
```and
```
lshw -c video
```

Here's mine: From lspci:

```
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Quadro NVS 210S/GeForce 6150LE] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
04:07.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
04:09.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 61)
04:09.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 63)
```From: lshw -c video:

```
 *-display               
       description: VGA compatible controller
       product: C51 [Quadro NVS 210S/GeForce 6150LE]
       vendor: nVidia Corporation
       physical id: 6
       bus info: pci@0000:00:05.0
       version: a2
       width: 64 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

---

### Post by zero7404 on 2009-04-26
i downloaded this for 8.10, but i can't find it in add/remove programs and can't find it in the last when i click add to panel....

uninstalled it and reinstalled it and it's still nowhere.

---

### Post by tbone7 on 2009-04-26
Try System --> Preferences.

---

### Post by zero7404 on 2009-04-26
it finally appeared after a few restarts, found it in Applications/Graphics

---

### Post by deekshlap on 2009-04-27
I tried wallpaper-tray again and now there is a fade transition. It seems that it automatically comes with 9.04 :P.

---

### Post by matairangi on 2009-05-28
The hint that wallpaper-tray settings are in Gnome was a lifesaver.
 I'd put a change time of 0.3 minutes into wallpaper-tray which it had read as 0 and then taken over processor time completely, changing as fast as possible. Oops!!

Fortunately I was able to change user to root and found the errant time inthe  /home/<user>/.gconf/apps/wp_tray .xml file

Now back to enjoying the changes

---

### Post by guywithcable on 2009-05-30
Well, it seems that the new version of Gnome broke the slideshow support for slideshows based on intervals rather than times of day, so for now, XML-Wall is no more. All is not lost though, as the new version of Gnome has blessed us with background transitions on *all* changes, so XML-Wall is mostly unnecessary now anyway.

---

### Post by Nixie Pixel on 2009-06-06
Can wallpaper-tray also handle different wallpapers for different desktops in Compiz?

---

### Post by guywithcable on 2009-06-06
> **Nixie Pixel said:**
> Can wallpaper-tray also handle different wallpapers for different desktops in Compiz?

I'm not sure. I don't use it. :(

If you find out, could you post it here?

---

### Post by hekar on 2009-06-06
I've made a little python script if don't wish to install a program just to change your wallpapers.

You just have to set your folder of images (by default ~/Pictures/) then give it an interval in seconds (ie. --time 50).

run with nohup ./ScreenChanger --time 50 &

---

### Post by dailyacts56 on 2009-07-06
Hi,
I need some help finding a wallpaper changer. I tried to use Drapes and Wallpaper-tray, but I cannot find the icon under graphics after I installed them. I would like something which would fade. I also need a little instructions about how to install it. Sorry if I maybe repeating this post. But I tired AutoWallpaper 2.0.4.2 and it worked really good for a couple of days. Then when I writing on Scribus, the changer crashed and I got an error message. No need to tell you what the error message was because I got rid of it. I tried to reinstall the wallpaper changer program, but it would not do it. Anyway, I would greatly appreciate the help.

---

### Post by carfield on 2009-07-06
Wallpaper-tray is now a gnome-applet. From the taskbar, click "Add to panel", you can find it

---

### Post by sandeepraj on 2009-07-26
i used **wallpaper_tray** but i made some changes in it's preferences and the wall papers change very raipdly( like each every sec) and it is not even allowing me to open preferences or to do right click on it.. how can i reset preferences in any other way.. i'm newbie to linux so can any 1 explain clearly procedure.. :confused::confused:

---

### Post by guywithcable on 2009-07-26
> **sandeepraj said:**
> i used **wallpaper_tray** but i made some changes in it's preferences and the wall papers change very raipdly( like each every sec) and it is not even allowing me to open preferences or to do right click on it.. how can i reset preferences in any other way.. i'm newbie to linux so can any 1 explain clearly procedure.. :confused::confused:

I'm not that familiar with wallpaper_tray, but the two ways programs usually store their preferences is in dot folders in your home directory, or in gconf. Go to your home folder and go View -> Show Hidden Files. Look for something like ".wallpapertray". Also check the .config and the .gnome2 folders. If you find it, delete it, then restart wallpaper tray (ie, logout and login). If you don't find anything, run "gconf-editor" (Alt+F2) and search around in there for its settings.

---

### Post by sandeepraj on 2009-07-27
wow.. thanx guywithcabel.. gconf-editor worked.
  jst want to clarify do all preferences of ubuntu programs changed from gconf-editor? and what else can we do in it?

---

### Post by guywithcable on 2009-07-27
> **sandeepraj said:**
> wow.. thanx guywithcabel.. gconf-editor worked.
  jst want to clarify do all preferences of ubuntu programs changed from gconf-editor? and what else can we do in it?

Not all of them. In fact, most don't use it. Gnome programs will use it, but most other programs use a dot directory in your home folder. Also, system stuff, like servers, store their settings in the /etc directory.

---

### Post by ttilberg on 2009-11-08
This is becoming frustrating.
I was first introduced to the XML wallpaper slideshows when I noticed the Cosmos wallpaper after doing a fresh install of Karmic. I was intrigued and amazed. The pictures were horrible, but the idea was beautiful.

Since then, I've been looking for more information on the XML wallpaper concept, and the best I've been able to find is the Day of Ubuntu stuff (which is fantastic).

Why are there no resources describing how to fully utilize the XML file? And why isn't this a more prominent feature? I got so excited when I saw the XML-Wall app here, only to find out it doesn't work.
I'd use wallpaper-tray but I can't stand how it has to be visible on a panel.

Does anyone know where we can find better resources on this? And how to elongate the transition effects? I'm sad the best answer people have is to set a cron-tab and use .py scripts. While I am not opposed to using such actions, this should be a prominent and easy-to-access feature, especially being that it is already inherent within Gnome. 
As the fellow above mentioned doing a Desktop Linux presentation, wouldn't it be a great attraction to... make this easy?

---

### Post by Dullstar on 2009-11-08
> **angry_johnnie said:**
> There is a really nice app available in the repos, called **wallpaper-tray**.

It stays on the system tray, and looks for images in any directory of your choice, and then changes them at certain user-specified intervals (the minimum interval being 1 minute).

There is another one, called gbackground, which does the same, but can be set to change the background image at a faster rate (any given number of seconds --even 1 second).  It is also available in the repositories.

A, perhaps, "geekier" approach, would be to write an xml file to set the background and then change it after some time, with --even-- a nice fade in/out transition.  Then you could just go to **system > preferences > appearance > background > add > all files**, and select your xml script.

It would look something like this:

```
<background>
    <static>
        <duration>1.0</duration>
        <file>/background/image/one</file>
    </static>    
    <transition>
        <duration>2.0</duration>
        <from>/background/image/one</from>
        <to>/background/image/two</to>
    </transition>
    <static>
        <duration>2.0</duration>
        <file>/background/image/two</file>
    </static>
    <transition>
        <duration>2.0</duration>
        <from>/background/image/two</from>
        <to>/background/image/one</to>
    </transition>
    <static>
        <duration>1.0</duration>
        <file>/background/image/one</file>
    </static>
</background>
```where **duration** is measured in seconds.

But then, if you ask me, I'd say wallpaper-tray. :-)
It's a lot easier.

I should try that script....

---

### Post by b1uesm4n on 2010-06-24
That script works nice! But i'm lazy... I've automated the process writing a python script though it's a very simple command-line script.

I've uploaded it to sourceforge so you can download it if you want.

[https://sourceforge.net/projects/pyslidemaker/](https://sourceforge.net/projects/pyslidemaker/)

---

### Post by marsters256 on 2010-09-04
> **angry_johnnie said:**
> There is a really nice app available in the repos, called **wallpaper-tray**.

It stays on the system tray, and looks for images in any directory of your choice, and then changes them at certain user-specified intervals (the minimum interval being 1 minute).

There is another one, called gbackground, which does the same, but can be set to change the background image at a faster rate (any given number of seconds --even 1 second).  It is also available in the repositories.

A, perhaps, "geekier" approach, would be to write an xml file to set the background and then change it after some time, with --even-- a nice fade in/out transition.  Then you could just go to **system > preferences > appearance > background > add > all files**, and select your xml script.

It would look something like this:

```
<background>
    <static>
        <duration>1.0</duration>
        <file>/background/image/one</file>
    </static>    
    <transition>
        <duration>2.0</duration>
        <from>/background/image/one</from>
        <to>/background/image/two</to>
    </transition>
    <static>
        <duration>2.0</duration>
        <file>/background/image/two</file>
    </static>
    <transition>
        <duration>2.0</duration>
        <from>/background/image/two</from>
        <to>/background/image/one</to>
    </transition>
    <static>
        <duration>1.0</duration>
        <file>/background/image/one</file>
    </static>
</background>
```where **duration** is measured in seconds.

But then, if you ask me, I'd say wallpaper-tray. :-)
It's a lot easier.


Erm... how would that xml file tell the wallpaper app or whatever it is to change the background image i just don't understand. could you explain how it works a bit please?

---

### Post by Bob63 on 2010-09-04
The XML code is just a skeleton (I think), and not actually meant to run.

---

### Post by alexds9 on 2010-09-25
I built a small C program that does what we need. In other words, from given folder with pictures it creates 2 xml files in folders:[INDENT]1) "/usr/share/backgrounds/"
2) "/usr/share/gnome-background-properties/"
[/INDENT]Which specify pictures in random order, time of showing and transition time, given by user.
It also can delete      existing collections(xml files) of pictures with command-line switch: "-r".
You can read help info ```
./wallpapers --help
```.
**Instructions:**[INDENT]1) Extract it from archive. 
2) Compile it for your system with ```
make
```.
3) Use example
```
sudo ./wallpapers -cn \"wallpapers 4.9.2010\" -cp \"/media/D/Wallpapers/4.9.2010\" -vt 45 -tt 0
```4) Choose the collection in "Appearance Preferences".
[/INDENT]I plan to make it    possible combining few folders to one collection. 
For bug reports and suggestions, contact me: [EMAIL="alexds9@gmail.com"]alexds9@gmail.com[/EMAIL].

---

