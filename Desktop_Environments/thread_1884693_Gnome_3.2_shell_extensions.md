---
title: "Gnome 3.2 shell extensions"
date: 2011-11-21
forum: Desktop Environments
---

### Post by cbowman57 on 2011-11-21
We need a place to share extensions that we find, create or modify.

This looks like a good place to start.

Anyhow, a simple mod to the Panel_Favorites extension from the frippery collection.

1. Places panel favorites on the right.
2. Resizes icons to more closely match the status icon size.

Additionally, any tips or tricks involving java scripting is welcome.

---

### Post by Copper Bezel on 2011-11-21
Hey, good idea! So I take it you know some Javascript, then? (Or are you just sort of working backwards from the extension scripts?) I wish I could make heads or tails of them - there are a number of little things I'd like to tweak.

---

### Post by cbowman57 on 2011-11-21
Just working backwards, look for the obvious and try a little trial & error.

I just know we have a lot of talent that visit the forum and now that Gnome shell is mainstream I expect that a lot of java savvy Ubuntu users will start writing code.

So, we could expand this to discussion of the code?

---

### Post by Copper Bezel on 2011-11-21
Yeah, I like that idea. It seems unlikely that we're going to learn Javascript just from dinking around with these extension files, but if we can poke at things and see what they do and hope for the occasional pro tip, we might be able to marginally improve the functionality of some of these extensions.

---

### Post by cbowman57 on 2011-11-21
Good, I hope it takes off and we get some cool stuff going on in here.

---

### Post by aeronutt on 2011-11-21
Excellent thread!

---

### Post by werewolves on 2011-11-21
Autohide Top Panel

Use the attached file, or install from PPA.
> 
sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-extensions-autohidetopbar


---

### Post by cbowman57 on 2011-11-21
For the most part I like installing them manually, thanks for attaching that werewolves.

---

### Post by aeronutt on 2011-11-21
Agreed, I like 'em in .local rather than owned by root. I have installed them from webupd8team/gnome3 then copied them over to .local and edited. Seems to work well.

---

### Post by cbowman57 on 2011-11-22
Yeah, I do that too.

---

### Post by furiat on 2011-11-23
Documentation on writing Gnome Shell extensions is so poor that motivated me to learn Java Script and digg into /usr/share/gnome-shell/js/ui. It is not like I am going to write amazing extension tomorrow but so far I do enjoy learning this. I would really like to be master of my OS interface not the other way around ;).

Here is a great attempt for documentation: [http://mail.gnome.org/archives/gnome-shell-list/2009-March/msg00001.html](http://mail.gnome.org/archives/gnome-shell-list/2009-March/msg00001.html)

---

### Post by ShodanjoDM on 2011-11-23
Just a tweak to reduce menu icon size with apps-menu extension.

```
gksudo gedit /usr/share/gnome-shell/extensions/apps-menu@gnome-shell-extensions.gnome.org/extension.js
```

Find and change this:

```
const ICON_SIZE = 28;
```

To something smaller, like 20 or 16.

```
const ICON_SIZE = 16;
```

------------------------------------

Anyway, I'm hoping that someday someone will make a globalmenu extension for gnome-shell like the one in Gnome 2. A more functional bottom panel and movable notification area extensions will be great as well...

---

### Post by cbowman57 on 2011-11-26
> **ShodanjoDM said:**
> 
Anyway, I'm hoping that someday someone will make a globalmenu extension for gnome-shell like the one in Gnome 2. A more functional bottom panel and movable notification area extensions will be great as well...

I see that Webupd8 has a global menu extension in their ppa.

Anyway, here's a modification for the extended places menu extension giving you more flexibility in locating the icon if you use it on the right end of the panel.

*12/05/2011 Some extensions require that you follow their installation procedure, this is one of them.  After it's installed you can replace the contents of the extension directory with these files.

---

### Post by Copper Bezel on 2011-11-26
[QUOTE=cbowman57]I see that Webupd8 has a global menu extension in their ppa.[/QUOTE]
It wasn't bad, but it stopped working for me after a regular system update, and I haven't been able to get it working again. It's different from Unity's, of course - it just adds the normal GTK menus as sections in the Appmenu, which added some extra clicks to get to anything (so it was more useful as a way to hide the menus than as a way to access them.) I'm looking forward to the point at which Shell has its menus sorted, so that application-level menus are in the Appmenu and document-level ones are in the individual windows, but I know that's all at the mockup stage still.

---

### Post by cbowman57 on 2011-11-26
He did say it was buggy on the website, but I thought some people might get lucky.

Apparently you weren't one of the lucky ones. :)

---

### Post by cbowman57 on 2011-11-27
The option to eliminate one more icon from your top panel.

This is an extension to hide the network icon.
(Sourced from the noa11y extension)

I'm on a wired connection & came to the conclusion recently that I never need instant access to those settings so why look at the icon.

---

### Post by ShodanjoDM on 2011-12-01
> **cbowman57 said:**
> I see that Webupd8 has a global menu extension in their ppa.

Anyway, here's a modification for the extended places menu extension giving you more flexibility in locating the icon if you use it on the right end of the panel.

Thank you. I never used extended places menu extension myself since I have icons on the desktop and XFCE4-panel's directory menu which is still far better IMHO, but I'll give it a try.

If you don't mind and have the time, can you look at the bottom panel extension? I really want to have it able to use the top panel's theme or gradient and being able to switch between opened windows with mouse scroll wheel.

---

### Post by cbowman57 on 2011-12-02
I need some help with the weather extension if anybody can dissect it. I want it to display just the degree sign, not C or F, just the degree symbol.  Seems like that should be easy enough but I can't figure it out.  :)

---

### Post by cortman on 2011-12-02
I'm still looking in vain for an extension that would either

a) remove the message tray
b) move the message tray to the top or side
c) move the notifications that appear in the message tray to a gnome panel applet and do away with the message tray.

I use Docky and LOVE it, and it's quite annoying to have the message tray bar pop up every time I do something, and block it.
I'm about to start learning Javascript, and if anyone here who has more experience would like to work on such a project that would be pretty cool too.

---

### Post by Frogs Hair on 2011-12-02
I can't get the weather extension find my location after entering the code from the RSS per the instructions @ Web Upd8 . I'll be using indicator-weather until I can get it to work .

---

### Post by xircon on 2011-12-03
> **Frogs Hair said:**
> I can't get the weather extension find my location after entering the code from the RSS per the instructions @ Web Upd8 . I'll be using indicator-weather until I can get it to work .

Same problem here, Chuck and GeneC (from the LMDE forum) have been trying to help me, but I got nowhere.

The Clear weather screenlet works for me, just create an entry in .config/autostart:
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Name=ClearWeatherScreenlet
Encoding=UTF-8
Version=1.0
Type=Application
Exec= python -u /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py
X-GNOME-Autostart-enabled=true

```

Then right click to set it up.

---

### Post by cbowman57 on 2011-12-03
xircon, is it the LMDE installation that this is happening on?

I ran LMDE & Debian with gnome shell and it seemed they were always playing catch up, I finally got tired of waiting on their schedule.

That's not to say that we're giving up though, I ran into a theme problem on my Precise installation today and had to switch out the user-themes-extension before I could activate a shell theme.  For LMDE I used to use the gnome extensions common & the user themes extension from Ubuntu 11.10, they were pretty reliable.

---

### Post by xircon on 2011-12-03
Yes, LMDE, should of made that clearer sorry.

---

### Post by iamnotthemessiah on 2011-12-03
does anyone know if its possible to load an extension from the terminal? or if theres some other way to load an extension after a certain time delay.

the reason i ask is that my network connection doesent work until a few seconds after gnome is loaded so the weather extension isnt able to connect out right away and just sits there looking stupid. if i load it manually after im logged in it works just fine

---

### Post by cbowman57 on 2011-12-03
> **iamnotthemessiah said:**
> does anyone know if its possible to load an extension from the terminal? or if theres some other way to load an extension after a certain time delay.

the reason i ask is that my network connection doesent work until a few seconds after gnome is loaded so the weather extension isnt able to connect out right away and just sits there looking stupid. if i load it manually after im logged in it works just fine

I really don't know, but this looks like the location in the extension.js where you can increase the timeout, not sure what that will do if anything but it's where I'd start.

```
        // Show weather
        Mainloop.timeout_add_seconds(3, Lang.bind(this, function() {
            this.refreshWeather(true);
        }));
```

---

### Post by cbowman57 on 2011-12-03
> **xircon said:**
> Yes, LMDE, should of made that clearer sorry.

No problem, it just helps to know since it seems each distro has it's own little quirks.

I liked using Debian, it was just hard to keep the shell in sync with development, they just don't move as fast as some others.

Pardon if I already asked, but when you pop into looking glass does it report any errors?

---

### Post by xircon on 2011-12-03
No it didn't, but have deleted it all now.

There is a bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=665452](https://bugzilla.gnome.org/show_bug.cgi?id=665452)

So I am not the only one.

---

### Post by cbowman57 on 2011-12-03
> **cortman said:**
> I'm still looking in vain for an extension that would either

a) remove the message tray
b) move the message tray to the top or side
c) move the notifications that appear in the message tray to a gnome panel applet and do away with the message tray.

I use Docky and LOVE it, and it's quite annoying to have the message tray bar pop up every time I do something, and block it.
I'm about to start learning Javascript, and if anyone here who has more experience would like to work on such a project that would be pretty cool too.

I was looking at the code in the messageTray.js & did manage to get notifications popping up in the middle of the screen, but it caused a crash.

So, pretty sure it's possible, I don't have the skills to do it unfortunately.  Would be nice if it were an extension so the shell itself wouldn't need to be edited.

If I stumble across one that can do it I'll be sure to post about it here.

---

### Post by cbowman57 on 2011-12-03
> **Frogs Hair said:**
> I can't get the weather extension find my location after entering the code from the RSS per the instructions @ Web Upd8 . I'll be using indicator-weather until I can get it to work .

Check your dates on the one you got off Webupd8, you might want to compare it against the git [https://github.com/simon04/gnome-shell-extension-weather](https://github.com/simon04/gnome-shell-extension-weather)

---

### Post by Frogs Hair on 2011-12-03
I'm using the PPA and not installing the individual extension packages manually . I will check a code for a city close by . The RSS code provided with the extension worked fine and the local RSS code works in my browser but not in the extension preferences .

---

### Post by vanlong441 on 2011-12-04
[http://forum.pinguyos.com/Thread-Gnome-Shell-suggestions-and-solutions](http://forum.pinguyos.com/Thread-Gnome-Shell-suggestions-and-solutions)

my thread over PinguyOS forum.
To reply to that thread or make a copy of it content, you must at least quote the above link in your post. Thanks :)

---

### Post by cbowman57 on 2011-12-05
Really liking the [QuickLaunch extension]("https://extensions.gnome.org/extension/37/quicklaunch/") but if anyone is having a problem with it the directions on the git page are currently incorrect.  The correct location for the .desktop files is ~/.local/user/apps

[IMG]https://extensions.gnome.org/static/extension-data/screenshots/screenshot_37.png[/IMG]

---

### Post by cbowman57 on 2011-12-05
Another one I like is [NetMonitor Lite]("https://extensions.gnome.org/extension/52/netmonitor/")

[IMG]https://extensions.gnome.org/static/extension-data/screenshots/screenshot_52.png[/IMG]

If you find that it's something you like combine it with my no-network-icon extension and it's pretty clean.  Let me know if you want to reposition it in the panel, &/or change font size & style, I can point you in the right direction.

---

### Post by Frogs Hair on 2011-12-05
No luck getting local data with the weather extension . Indicator-weather and the extension both use Yahoo as their source and indicator weather provides local data and extension does not . I have checked the feed ID many times ? Maybe I will try again a few months .

---

### Post by cbowman57 on 2011-12-05
> **Frogs Hair said:**
> No luck getting local data with the weather extension . Indicator-weather and the extension both use Yahoo as their source and indicator weather provides local data and extension does not . I have checked the feed ID many times ? Maybe I will try again a few months .

Can you forward the WOEID code you're using to me, I'd like to give it a try.

---

### Post by MBybee on 2011-12-05
I'm using both the weather one and the gtk menu one - both are working ok. The only quirk I had was that the weather defaulted to being in the center (by the date) instead of where I wanted it (off to the right).

It was a bit of a pain to get the right WOEID.

---

### Post by cbowman57 on 2011-12-05
> **MBybee said:**
> I'm using both the weather one and the gtk menu one - both are working ok. The only quirk I had was that the weather defaulted to being in the center (by the date) instead of where I wanted it (off to the right).

It was a bit of a pain to get the right WOEID.

This is probably the best instructions I can find for determining the WOEID.

> 
This is what i did:
  
[LIST=1]
[*]go to [http://weather.yahoo.com]("http://weather.yahoo.com/") and enter your location
[*]klick on "**RSS**" (on the right side)
[*]your location code is shown in the address-bar  (eg. weather.yahooapis.com/forecastrss?p=**GMXX0087**&u=f)
[*]copy your code (**GMXX0087** in my case) and open a terminal
[*]set location and city with
  gsettings set org.gnome.shell.extensions.weather woeid "'**GMXX00187**'"
  gsettings set org.gnome.shell.extensions.weather city **YOURCITY**
[*]logout & login again
[/LIST]


Source [Ask Ubuntu]("http://askubuntu.com/questions/72224/gnome-shell-weather-extension-is-not-showing-correct-weather-information")

---

### Post by Frogs Hair on 2011-12-05
> **cbowman57 said:**
> Can you forward the WOEID code you're using to me, I'd like to give it a try.

This is the closest large city with relevant information . [http://weather.yahooapis.com/forecastrss?p=USWI0771&u=f](http://weather.yahooapis.com/forecastrss?p=USWI0771&u=f)

---

### Post by MBybee on 2011-12-05
That works for me - and dang it's cold there!!

---

### Post by cbowman57 on 2011-12-05
> **Frogs Hair said:**
> This is the closest large city with relevant information . [http://weather.yahooapis.com/forecastrss?p=USWI0771&u=f](http://weather.yahooapis.com/forecastrss?p=USWI0771&u=f)

Works or me, no problem. (Don't you love it when people say that) :)

I entered the code using dconf-editor.

[ATTACH]208571[/ATTACH]

---

### Post by cbowman57 on 2011-12-05
> **MBybee said:**
> That works for me - and dang it's cold there!!

I know, I'm getting chilled just looking at it, I thought 50 was cold today with the winds coming in from the north.

---

### Post by Frogs Hair on 2011-12-05
> **MBybee said:**
> That works for me - and dang it's cold there!!

In a month this will be a nice day ! :P

---

### Post by MBybee on 2011-12-05
> **cbowman57 said:**
> Works or me, no problem. (Don't you love it when people say that) :)

I entered the code using dconf-editor.

[ATTACH]208571[/ATTACH]

I just typed it in via preferences (in the GUI menu)

Are you just using the USWI0771 part? That's all I put in to get it to work.

---

### Post by Frogs Hair on 2011-12-05
> **cbowman57 said:**
> Works or me, no problem. (Don't you love it when people say that) :)

I entered the code using dconf-editor.

[ATTACH]208571[/ATTACH]

I will reinstall and use the dconf-editor , that was not supposed to be needed anymore according to the web Upd8 instructions.

---

### Post by cbowman57 on 2011-12-05
> **Frogs Hair said:**
> In a month this will be a nice day ! :P

:lol:  I grew up in Rockford, IL.  Those northern winters were the deciding factor when I decided to move down to the Texas coast last year, well that and getting my son located so he could get a job.

---

### Post by MBybee on 2011-12-05
> **cbowman57 said:**
> :lol:  I grew up in Rockford, IL.  Those northern winters were the deciding factor when I decided to move down to the Texas coast last year, well that and getting my son located so he could get a job.

I bet - I like snow best when I can visit it :)

---

### Post by cbowman57 on 2011-12-05
> **Frogs Hair said:**
> I will reinstall and use the dconf-editor , that was not supposed to be needed anymore according to the web Upd8 instructions.

I think it depends on a couple things I don't understand.  On a couple of my Ubuntu setups it worked via preferences, a couple others the settings wouldn't stick, would default back to whatever the default is.  On my Arch installations the Preferences don't even show up so I've always had to resort to the dconf-editor.

With any luck, by the time you read this it will be working.

---

### Post by cbowman57 on 2011-12-05
> **MBybee said:**
> I bet - I like snow best when I can visit it :)

I have no compulsion  to do even that. :)

I do love Autumn though, just not the same down here.  Spent most of my career in the south & always missed Fall.  Oh well, life is full of little compromises.

---

### Post by xircon on 2011-12-05
Chuck, can you try UKXX1002 (Sheffield, Attercliffe) I still can't get the extension to run.

Cheers

Steve

---

### Post by cbowman57 on 2011-12-05
> **xircon said:**
> Chuck, can you try UKXX1002 (Sheffield, Attercliffe) I still can't get the extension to run.

Cheers

Steve

Works fine Steve, it's apparently 36 degrees partly cloudy with a  chance of showers today & tomorrow.

---

### Post by xircon on 2011-12-05
Well its 1.5 deg C so thats about right, with snow showers, 3 miles away from home there is 8-9cm of standing snow (2.5-3 inches).  

I updated to 3.2.1-7 (LMDE Sid) today, still no joy, activating weather logs me out to the extensions on/off screen. I officially give up and have deleted.

[[IMG]http://thumbnails64.imagebam.com/16296/6fdb6a162953464.jpg[/IMG]](http://www.imagebam.com/image/6fdb6a162953464)

---

### Post by Frogs Hair on 2011-12-05
> **cbowman57 said:**
> I think it depends on a couple things I don't understand.  On a couple of my Ubuntu setups it worked via preferences, a couple others the settings wouldn't stick, would default back to whatever the default is.  On my Arch installations the Preferences don't even show up so I've always had to resort to the dconf-editor.

With any luck, by the time you read this it will be working.

Weather extension now working ! . Instead of using the WOEID from Yahoo I used my zip-code .

---

### Post by cbowman57 on 2011-12-05
> **Frogs Hair said:**
> Weather extension now working ! . Instead of using the WOEID from Yahoo I used my zip-code .

Worked for me too, that's way too easy.  ](*,)

@Steve, do you have the equivalen of a zipcode?  Gnome shell on Debian is an ongoing struggle right now, and probably the foreseeable future.  You must be  a glutton for punishment. :)

---

### Post by xircon on 2011-12-05
True, postcode is s6 2sa, but if I turn the extension on it crashes so can't test (and I have deleted doh) I give up.  Does my postcode work for you?

---

### Post by cbowman57 on 2011-12-05
> **xircon said:**
> True, postcode is s6 2sa, but if I turn the extension on it crashes so can't test (and I have deleted doh) I give up.  Does my postcode work for you?

No, it  sure doesn't.

---

### Post by xircon on 2011-12-05
Probably only works for US codes as Yahoo are American.

---

### Post by cecilpierce on 2011-12-06
@xircon

If you really want a weather forecast you could install 'indicator-weather' from synaptic, it not in the top panel though, it comes up in the bottom, Ive had a lot of probs with the weather thing to  :(

---

### Post by malspa on 2011-12-06
Or just go with something like ForecastFox, right in the browser.

---

### Post by xircon on 2011-12-06
> **cecilpierce said:**
> @xircon

If you really want a weather forecast you could install 'indicator-weather' from synaptic, it not in the top panel though, it comes up in the bottom, Ive had a lot of probs with the weather thing to  :(

I have installed screenlets clearweather, works well but thanks for the tip:
[[IMG]http://thumbnails64.imagebam.com/16221/309cdb162203483.jpg[/IMG]](http://www.imagebam.com/image/309cdb162203483)

---

### Post by cecilpierce on 2011-12-06
Yep, that looks a lot better then my idea and the top one.

---

### Post by cecilpierce on 2011-12-06
Hmmm! just noticed the temp are different   :confused:

---

### Post by Frogs Hair on 2011-12-06
The widgets / indicators probably get data from different places or the refresh rate is different .

---

### Post by r_mano on 2011-12-06
Hi, I have "arranged" a little extension to make the text on the top bar smaller (useful for netbooks). It's an hack, but it works for me, and I would like to share it with you. 

[http://rlog.rgtti.com/2011/12/06/a-gnome-shell-extension-to-change-the-top-panel-look/](http://rlog.rgtti.com/2011/12/06/a-gnome-shell-extension-to-change-the-top-panel-look/)

The good thing is that you can use it to modify a lot of things, and test them just disabling/enabling the extension through the gnome-tweak-tool shell extension interfaces. 

All the merit is to be given to Finnar B. Murphy, and all the bad things and the horrible coding style to myself.

---

### Post by cbowman57 on 2011-12-06
> **r_mano said:**
> Hi, I have "arranged" a little extension to make the text on the top bar smaller (useful for netbooks). It's an hack, but it works for me, and I would like to share it with you. 

[http://rlog.rgtti.com/2011/12/06/a-gnome-shell-extension-to-change-the-top-panel-look/](http://rlog.rgtti.com/2011/12/06/a-gnome-shell-extension-to-change-the-top-panel-look/)

The good thing is that you can use it to modify a lot of things, and test them just disabling/enabling the extension through the gnome-tweak-tool shell extension interfaces. 

All the merit is to be given to Finnar B. Murphy, and all the bad things and the horrible coding style to myself.

Thanks r_mano, I played with it a bit.  Your website mentioned having to add it with dconf-editor?  Not sure what that's about, there was a missing url, I corrected that.

Commented the style sheet so that it doesn't override the gnome-shell theme (might not be necessary unless using theme other than Adwaita).  

Instead of fixed font-size as a point, I changed it to adjust by a percentage with em instead of pt.

Changed font-size to normal & added a hover effect changing it to bold (something I like for my old tired eyes).

Also reduced padding a bit to keep the icons a little more condensed.

Hope you didn't mind me tweaking on it. :)

Also, I didn't do this in the archive but if you want the panel to "come alive" when you hover over an icon you can edit the stylesheet.css portion 

```
.panel-button:hover {
    color: white;
    font-weight: bold;
    font-size: .90em;  << -- something like this
    
}
```

---

### Post by r_mano on 2011-12-07
> **cbowman57 said:**
> 

Hope you didn't mind me tweaking on it. :)



The other way around, I like it --- that was the idea, to share a trick to "hack" a bit on the shell. I will check your changes asap (I cannot use gnome shell at work, due to ATI rendering bugs) and, if you don't mind, I will put your version on my web page, with the due attribution. Ok? 

By the way, I have a bit of problem of inter-relation between my extension, auto-hide top bar and classic-systray... but the worst one is between the autohide and "looking glass", which can hard-lock the shell --- anyone tested that?

---

### Post by cbowman57 on 2011-12-07
> **r_mano said:**
> The other way around, I like it --- that was the idea, to share a trick to "hack" a bit on the shell. I will check your changes asap (I cannot use gnome shell at work, due to ATI rendering bugs) and, if you don't mind, I will put your version on my web page, with the due attribution. Ok? 

By the way, I have a bit of problem of inter-relation between my extension, auto-hide top bar and classic-systray... but the worst one is between the autohide and "looking glass", which can hard-lock the shell --- anyone tested that?

Good, I share that philosophy. :)

---

### Post by cbowman57 on 2011-12-31
> **ShodanjoDM said:**
> Thank you. I never used extended places menu extension myself since I have icons on the desktop and XFCE4-panel's directory menu which is still far better IMHO, but I'll give it a try.

If you don't mind and have the time, can you look at the bottom panel extension? I really want to have it able to use the top panel's theme or gradient and being able to switch between opened windows with mouse scroll wheel.

Don't have a solution on the mouse wheel scroll but did you ever manage to theme your bottom panel?  If not I think I've got the fix for it.

---

### Post by cbowman57 on 2012-01-03
The [Disable Window Animations extension]("https://extensions.gnome.org/extension/119/disable-window-animations/") is pretty cool, adds even more snap than my hacks on the shell.

---

### Post by xircon on 2012-01-03
Something for the brave (or foolhardy ;)):
[http://www.techdrivein.com/2012/01/install-latest-gnome-shell-332-in.html](http://www.techdrivein.com/2012/01/install-latest-gnome-shell-332-in.html)

Shell 3.3.2 in PPA.

---

### Post by cbowman57 on 2012-01-04
> **xircon said:**
> Something for the brave (or foolhardy ;)):
[http://www.techdrivein.com/2012/01/install-latest-gnome-shell-332-in.html](http://www.techdrivein.com/2012/01/install-latest-gnome-shell-332-in.html)

Shell 3.3.2 in PPA.

Call me foolhardy then, just had to try it.

Feels faster & after updating metadata.json to proper shell version all of my extensions seem to work.

My alternate activities overview shortcut doesn't work though, that's the only "bug" I've encountered.  Think I'll ride the  bleeding edge for awhile. :)

Also seems I've lost my startup apps in the notification area of the message tray.

---

### Post by xircon on 2012-01-04
Can't get it to run on my main Debian install :( (and I use a lot of PPAs coz I am bad lad).

Vbox not running on sandybridge chipsets (bug since April!!).

So tried Wubi, can't get the $%^&!"£ to run, something to do with BCD store, so TBH I just gave up :)

3.2.1 for me then.

---

### Post by cbowman57 on 2012-01-04
> **xircon said:**
> Can't get it to run on my main Debian install :( (and I use a lot of PPAs coz I am bad lad).

Vbox not running on sandybridge chipsets (bug since April!!).

So tried Wubi, can't get the $%^&!"£ to run, something to do with BCD store, so TBH I just gave up :)

3.2.1 for me then.

Yeah, I ran gnome shell on Debian for awhile, it's an ongoing struggle.

---

### Post by sanderd17 on 2012-01-04
> **cbowman57 said:**
> Call me foolhardy then, just had to try it.

Feels faster & after updating metadata.json to proper shell version all of my extensions seem to work.

This is great, it looks promising for the future

---

### Post by cbowman57 on 2012-01-04
Who was it looking for a way to disable the message tray?

[http://sourceforge.net/projects/removebottombar/](http://sourceforge.net/projects/removebottombar/)

---

### Post by werewolves on 2012-01-04
> **cbowman57 said:**
> Feels faster & after updating metadata.json to proper shell version all of my extensions seem to work.

Did you have the "partial upgrade" problem described in the post?

---

### Post by cbowman57 on 2012-01-04
> **werewolves said:**
> Did you have the "partial upgrade" problem described in the post?

I didn't have any problems but I almost always substitute aptitude safe-upgrade for apt-get upgrade to help insure my system doesn't get broken by an update.

---

### Post by werewolves on 2012-01-05
> **cbowman57 said:**
> I didn't have any problems but I almost always substitute aptitude safe-upgrade for apt-get upgrade to help insure my system doesn't get broken by an update.

Unfortunately, I've had a few problems since installing this PPA.  My biggest issue is that my keyboard shortcuts for changing desktops no longer function.  I had set Win+F1-F5 to jump to a particular desktop, and they no longer function.  Very annoying.  Anyone have thoughts?

---

### Post by cbowman57 on 2012-01-05
> **werewolves said:**
> Unfortunately, I've had a few problems since installing this PPA.  My biggest issue is that my keyboard shortcuts for changing desktops no longer function.  I had set Win+F1-F5 to jump to a particular desktop, and they no longer function.  Very annoying.  Anyone have thoughts?

Yeah, I discovered a bug with shortcuts too, it works but it's pretty raw.

---

### Post by werewolves on 2012-01-05
> **cbowman57 said:**
> Yeah, I discovered a bug with shortcuts too, it works but it's pretty raw.

Apparently you can set them with dconf-editor at "org.gnome.desktop.wm.keybindings"

---

### Post by werewolves on 2012-01-05
Now if I could just get shellshape ([http://gfxmonk.net/shellshape/](http://gfxmonk.net/shellshape/)) to work!

---

### Post by sanderd17 on 2012-01-06
I made an extension: [https://gitorious.org/gnome-shell-extension-application-installer](https://gitorious.org/gnome-shell-extension-application-installer)

(just copy the files to .local/share/gnome-shell/extensions/installer@sanderd17.gmail.com )

It depends on packageKit, so please install that first.

I know there's a lack of feedback for the moment (it doesn't tell you if your program is installed, or if the installation crashed), and the theming is not very attractive yet, but it should work.

So please test it, and report if you have issues. You can report directly to me at sanderd17[AT]gmail[DOT]com.

I would consider this to be at alpha stage, so be careful with it.

---

### Post by cbowman57 on 2012-01-06
@Sanderd

Haven't tried the packagekit version yet, on  my Arch installation I don't want to change what you did yesterday, works perfectly with packer.

---

### Post by sanderd17 on 2012-01-07
> **cbowman57 said:**
> @Sanderd

Haven't tried the packagekit version yet, on  my Arch installation I don't want to change what you did yesterday, works perfectly with packer.

The information about installing the Extension I made is changed. 

This is because the AUR support file and the other one are merged, but now you have to disable the AUR support flag at the top of the JS file if you don't want AUR support.

So for Ubuntu, it will just crash when you don't disable that flag (maybe it will give you an error log).

---

### Post by bookcrazy on 2012-01-23
Hello everyone,

I've looked and looked but I haven't been able to find an extension for the clock that allows you to have multiple times listed. For example, on my machine running 10.04 I'm able to list my local time (China) as well as other places around the world so I can check whether or not it's too late to call someone. Does anyone know if there's an extension like that available for 11.10 yet?

Cheers!

---

### Post by cbowman57 on 2012-01-23
Don't believe there is one.

---

### Post by markbl on 2012-01-23
> **bookcrazy said:**
> 
I've looked and looked but I haven't been able to find an extension for the clock that allows you to have multiple times listed. For example, on my machine running 10.04 I'm able to list my local time (China) as well as other places around the world so I can check whether or not it's too late to call someone,
I just use [http://www.timeanddate.com/worldclock/meeting.html](http://www.timeanddate.com/worldclock/meeting.html).

---

### Post by sanderd17 on 2012-01-23
> **bookcrazy said:**
> Hello everyone,

I've looked and looked but I haven't been able to find an extension for the clock that allows you to have multiple times listed. For example, on my machine running 10.04 I'm able to list my local time (China) as well as other places around the world so I can check whether or not it's too late to call someone. Does anyone know if there's an extension like that available for 11.10 yet?

Cheers!

It doesn't look too difficult to create one, but I think you will get in space problems. 

The space on the top bar is limited, and a clock asks a lot of space, certainly if you want to display the name of the time zone next to it.

Do you have an idea where it could be added instead?

---

### Post by bookcrazy on 2012-01-23
I was thinking that it would work much the same way as it does in 10.04 on the gnome desktop where you click on the time, and then it expands to show you additional time zones. 

What do you think?

> **sanderd17 said:**
> It doesn't look too difficult to create one, but I think you will get in space problems. 

The space on the top bar is limited, and a clock asks a lot of space, certainly if you want to display the name of the time zone next to it.

Do you have an idea where it could be added instead?

---

### Post by cbowman57 on 2012-01-23
> **bookcrazy said:**
> I was thinking that it would work much the same way as it does in 10.04 on the gnome desktop where you click on the time, and then it expands to show you additional time zones. 

What do you think?

Not an extension I normally have a use for but that makes sense.  Would look good as an added panel on the calendar popup, or even incorporated into the userMenu.

---

### Post by bookcrazy on 2012-01-23
> **cbowman57 said:**
> not an extension i normally have a use for but that makes sense.  Would look good as an added panel on the calendar popup, or even incorporated into the usermenu.

Exactly!

---

### Post by krippa on 2012-02-27
Myself and several other people I know really miss this feature. I think putting it below the calendar really makes sense. Is it possible to make an extension that adds functionality to existing indicators?

---

### Post by omegadestroy on 2012-03-18
got a question guys, is there any shell extension for Ubuntu One indicator in the top panel?

---

### Post by Frogs Hair on 2012-03-18
If it can't be found at the link it probably doesn't exist yet .

[https://extensions.gnome.org/](https://extensions.gnome.org/)

---

