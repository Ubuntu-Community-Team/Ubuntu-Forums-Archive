---
title: "How to &quot;downgrade&quot; Firefox from 4 to 3.6.17?"
date: 2011-05-20
forum: Desktop Environments
---

### Post by Krupski on 2011-05-20
Hi all,

Does anyone know how to "downgrade" Firefox 4.x in Ubuntu 11.04 back to 3.6.17?

Yes, I've searched here, everywhere else and Google. I found a few "procedures", none of which work.

I tried to download the tar.gz file from Mozilla, unpack it and run it... doesn't work. I tried adding the "PPA" stuff to the APT sources and then trying to do an install... doesn't work.

Currently, I have reverted back to Ubuntu 10.10 so that I can use Firefox 3.6.x, but of course this is not the solution since it means I can never upgrade again.

Anyone have any ideas...hints... procedures that ACTUALLY work (i.e. you've already done it and it works)?

Google links will be of no help to me - been there, done that. I need something that ACTUALLY works.

Thanks!

-- Roger

---

### Post by Joe of loath on 2011-05-20
Out of interest -

Why?

With 5 minutes of work you can make them look the same, 99% of addons are compatible with FF4, and FF4 is faster, lighter and more secure.

---

### Post by Mbhiza on 2011-05-20
1. go here:  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2)
2. Extract the file to your home folder.
3. Open the folder and double click on the file named firefox with no extantion
4. Done and be sure to set it to default browser when it prompts you ;)

---

### Post by lovinglinux on 2011-05-20
> **Mbhiza said:**
> 1. go here:  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2)
2. Extract the file to your home folder.
3. Open the folder and double click on the file named firefox with no extantion
4. Done and be sure to set it to default browser when it prompts you ;)

Keep in mind that is the 32bit version of Firefox. If you are running a 64bit system, you need to get the 64bit version from the [nightly repository]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/").

@Krupski

Please specify why you want to downgrade. Perhaps we can help tune your Firefox 4.

---

### Post by Krupski on 2011-05-21
> **Joe of loath said:**
> Out of interest -

Why?

With 5 minutes of work you can make them look the same, 99% of addons are compatible with FF4, and FF4 is faster, lighter and more secure.

Two reasons: 

(1) It's laid out differently

(2) Noia extreme (theme) doesn't work with it.

---

### Post by Krupski on 2011-05-21
> **lovinglinux said:**
> Keep in mind that is the 32bit version of Firefox. If you are running a 64bit system, you need to get the 64bit version from the [nightly repository]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/").

@Krupski

Please specify why you want to downgrade. Perhaps we can help tune your Firefox 4.

Thank you for the link. I'll try it.

As for the reason I want to go back to 3.6... see above.

---

### Post by Larkspur on 2011-05-21
> **Krupski said:**
> Two reasons: 

(1) It's laid out differently

(2) Noia extreme (theme) doesn't work with it.

For (1), if you right-click on one of the bars and choose "customize" you can rejig FF to the older appearance.  There's also an Add-on called [Status 4 evar]("https://addons.mozilla.org/en-US/firefox/addon/status-4-evar/"), which brings back the status bar.

For (2), there is [Noia 4]("https://addons.mozilla.org/en-US/firefox/addon/noia-4/"), which says it is the new version of Noia Extreme for FF4.

---

### Post by Krupski on 2011-05-24
> **lovinglinux said:**
> Keep in mind that is the 32bit version of Firefox. If you are running a 64bit system, you need to get the 64bit version from the [nightly repository]("http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-firefox-3.6.x/").


I run 64 bit Linux... and Firefox 4.0.1 is 32 bit... so why can't I run the 32 bit version of 3.6.17?

---

### Post by lovinglinux on 2011-05-24
> **Krupski said:**
> I run 64 bit Linux... and Firefox 4.0.1 is 32 bit... so why can't I run the 32 bit version of 3.6.17?

Because your plugins won't work.

If you are using Firefox 4 from the repositories, it is 64bit.

To find out, type **about:support** in the address bar and look for the user Agent info.

---

### Post by iokhahon on 2011-05-28
> **Mbhiza said:**
> 1. go here:  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2)
2. Extract the file to your home folder.
3. Open the folder and double click on the file named firefox with no extantion
4. Done and be sure to set it to default browser when it prompts you ;)

This method worked perfectly for me, thanks!
My reason for down leveling? I finally convinced my wife to try Ubuntu (she is currently using Windows 7), one of her regular games is Zuma Blitz on fb and it does not play smoothly in firefox 4 (there is a hesitation between the time you fire and the time you see the ball move). I tried every version of flash available then finally tried another browser (Google Chrome) which worked perfectly (didn't even have to download the Flash plug in).

---

### Post by nullified_nostalgia on 2011-06-08
> **Mbhiza said:**
> 1. go here:  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.6.17/linux-i686/en-US/firefox-3.6.17.tar.bz2)
2. Extract the file to your home folder.
3. Open the folder and double click on the file named firefox with no extantion
4. Done and be sure to set it to default browser when it prompts you ;)
I'm brand new to using linux and I've got a couple of questions about this.  I followed these instructions (had to uninstall firefox 4.x before it would work) and was able to use firefox 3.6.17.  However, I'm having some trouble with it.

First, this doesn't seem to actually install firefox 3.6.17.  I can only run it by clicking on the file named firefox and every time I do that it acts like it's a completely brand new install of firefox, asking me if I want to make it the default browser, and it doesn't show up in the applications menu.  Is there a way to get this to actually install so it will quit asking me to make it the default browser and so it will show up in the applications menu?

Second, this doesn't seem to have a firefox icon that I can put on the menu at the top of the desktop.  How would I accomplish this?  I'm assuming it has to do with my first question.

And just for the record, the reasons I don't want firefox 4.0 are that many of the addons I use aren't compatible with 4.0 and I don't like some of the changes in the interface - primarily that the interface seems bulky and cartoony to me instead of streamlined and minimal like 3.x.

Thanks for any help anybody can give me.

---

### Post by lovinglinux on 2011-06-08
> **nullified_nostalgia said:**
> I'm brand new to using linux and I've got a couple of questions about this.  I followed these instructions (had to uninstall firefox 4.x before it would work) and was able to use firefox 3.6.17.  However, I'm having some trouble with it.

First, this doesn't seem to actually install firefox 3.6.17.  I can only run it by clicking on the file named firefox and every time I do that it acts like it's a completely brand new install of firefox, asking me if I want to make it the default browser, and it doesn't show up in the applications menu.  Is there a way to get this to actually install so it will quit asking me to make it the default browser and so it will show up in the applications menu?

Second, this doesn't seem to have a firefox icon that I can put on the menu at the top of the desktop.  How would I accomplish this?  I'm assuming it has to do with my first question.

And just for the record, the reasons I don't want firefox 4.0 are that many of the addons I use aren't compatible with 4.0 and I don't like some of the changes in the interface - primarily that the interface seems bulky and cartoony to me instead of streamlined and minimal like 3.x.

Thanks for any help anybody can give me.

First I would like to say that downgrading is just a temporary solution. Mozilla is already preparing to release Firefox 5 and versions 6 and 7 are already under way. Firefox 3.6 will soon no longer be supported. If your extensions are not compatible with Firefox 4 yet, then most likely they are abandoned. However, If you are using extensions installed via repository, then remove them and get the latest versions from [Mozilla]("https://addons.mozilla.org") site.

There are several add-ons that can bring some Firefox 3 features to Firefox 4. Not to mention Firefox 3.x is a lot slower.

If you have any difficulties with some extensions, please provide their names so we can take a look and find a solution. Also, if are more specific about which features you don't like in Firefox 4 we can help you customize it.

That being said, you can tell your system to use your Firefox installed manually as default Firefox. You can do that by diverting the /usr/bin/firefox. Keep in mind that could cause some issues when you upgrade your system and get Firefox updates. The Ubuntu developers don't like this solution very much, because people tend to report as bug when the problems occur. However I have been using this for a long time without issues.

Assuming your Firefox is extracted to your home directory and you start it using **~/firefox/firefox**, then do this (save these commands for future reference):

```
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox && sudo ln -s **~/firefox/firefox** /usr/bin/firefox
```

If you ever want to revert to the original Firefox installed from the repositories, you will need to do this:

```
sudo unlink /usr/bin/firefox && sudo dpkg-divert --rename --remove /usr/bin/firefox
```

---

### Post by nullified_nostalgia on 2011-06-08
> **lovinglinux said:**
> First I would like to say that downgrading is just a temporary solution. Mozilla is already preparing to release Firefox 5 and versions 6 and 7 are already under way. Firefox 3.6 will soon no longer be supported. If your extensions are not compatible with Firefox 4 yet, then most likely they are abandoned. However, If you are using extensions installed via repository, then remove them and get the latest versions from [Mozilla]("https://addons.mozilla.org") site.

There are several add-ons that can bring some Firefox 3 features to Firefox 4. Not to mention Firefox 3.x is a lot slower.

If you have any difficulties with some extensions, please provide their names so we can take a look and find a solution. Also, if are more specific about which features you don't like in Firefox 4 we can help you customize it.

I've got several people presenting good arguments to me on why I should upgrade to firefox 4 so I would like to do it if I can get a few things customized about it.  Maybe you or someone else could tell me how to do these things.

1 - The + symbol for opening a new tab is around 4 times the size it was in 3.x.  Is there a way to make it small like it was in 3.x?

2 - I have a lot of addons but I only want a tool button for two of them to be visible, right next to the address bar (the adblock plus button and the noscript button).  The only way I've found thus far to have these visible is to have the addon toolbar visible, which has buttons running all the way across the screen making it look junky.

3 - This relates to 2:  I love my 3.x status bar, primarily just because I want the noscript button down there, but also because I use a theme and the status bar allows me to make the theme cover firefox from top to bottom.  I installed the addon to add the status bar to 4.x, but the organize status bar addon doesn't work with 4.x so just like the addon toolbar it's got buttons running all along it making it look junky.

As for addons that aren't compatible:
1. Any Color (maybe firefox 4.x has a way to customize all the colors of the components like this addon does for 3.x?)
2. Organize Status Bar (See number 3 above for the explanation of this one)

Those are really the only two addons I feel I can't live without, just simply because I like to keep firefox customized.  Here's a screenshot of what my 3.x looks like in windows.  I want 4.x to look as close to this as I can possibly get it:  [http://i53.tinypic.com/9itv29.jpg](http://i53.tinypic.com/9itv29.jpg)

---

### Post by Joe of loath on 2011-06-08
As a start, how's this? It has the noscript, adblock etc in the same place, and, err, not much else :p that is pretty much default, though.

[http://i274.photobucket.com/albums/jj269/joeofloath/Screenshot-11-1.png](http://i274.photobucket.com/albums/jj269/joeofloath/Screenshot-11-1.png)

---

### Post by nullified_nostalgia on 2011-06-08
> **Joe of loath said:**
> As a start, how's this? It has the noscript, adblock etc in the same place, and, err, not much else :p that is pretty much default, though.

[http://i274.photobucket.com/albums/jj269/joeofloath/Screenshot-11-1.png](http://i274.photobucket.com/albums/jj269/joeofloath/Screenshot-11-1.png)
Yeah that would work, I've just got to figure out how to put addon buttons on the toolbar like that.  They don't seem to be in the customize toolbar section like they are in 3.x (at least that I remember, I'm about to load ubuntu back up and check that.)  I've also got to figure out how to get the status bar back (and how to organize it) so my theme is showing at the bottom and how to edit the colors of the tabs and scroll bars and such without the any color addon.  I probably just haven't spent enough time tinkering with it.

---

### Post by Joe of loath on 2011-06-08
Well, to move the addon icons, open the addon toolbar (Or whatever it is they're displayed on by default), open the customise window, and drag them where you want them.

---

### Post by lovinglinux on 2011-06-08
> **nullified_nostalgia said:**
> 1 - The + symbol for opening a new tab is around 4 times the size it was in 3.x.  Is there a way to make it small like it was in 3.x?

The size of the icon haven't changed. All you need is to right-click on the toolbar, select "Customize" than tick the option to "Use Small Icons".

If that isn't enough for you, let me know so I can write a style sheet to make it smaller.

> **nullified_nostalgia said:**
> 2 - I have a lot of addons but I only want a tool button for two of them to be visible, right next to the address bar (the adblock plus button and the noscript button).  The only way I've found thus far to have these visible is to have the addon toolbar visible, which has buttons running all the way across the screen making it look junky.

> **nullified_nostalgia said:**
> Yeah that would work, I've just got to figure out how to put addon buttons on the toolbar like that.  They don't seem to be in the customize toolbar section like they are in 3.x (at least that I remember, I'm about to load ubuntu back up and check that.)

If your add-on icons are not visible in the Customize dialog, then hit the "Restore Default Set" button in the lower-right corner of the Customize dialog. This will reset your toolbars and bring back the icons that are missing. If that doesn't solve the problem, then close Firefox, open your profile located under ~/.mozilla/firefox/<profilename>/ and delete the file *localstore.rdf*.

You might also like [Barlesque]("https://addons.mozilla.org/en-US/firefox/addon/259879/") extension. It reduces the Add-on toolbar size according to the extension icons you have and add a small button so you can hide it when you don't need them. Alternatively, you can use [AIOS]("https://addons.mozilla.org/en-US/firefox/addon/1027/") extension. It adds an extra toolbar to the left of the sidebar, which can be collapsed automatically or when you click a small grip.

> **nullified_nostalgia said:**
> 
3 - This relates to 2:  I love my 3.x status bar, primarily just because I want the noscript button down there, but also because I use a theme and the status bar allows me to make the theme cover firefox from top to bottom.  I installed the addon to add the status bar to 4.x, but the organize status bar addon doesn't work with 4.x so just like the addon toolbar it's got buttons running all along it making it look junky.

Personally, I avoid add-ons with status bar icons. When Mozilla introduced the Add-ons bar, they have kept part of the status bar code, so that extensions that still use it will be displayed in the Add-ons bar. The problem is that instead of upgrading their extensions to use the new Add-ons bar, some developers are still using the old status bar placement, which cannot be customized. What you can do is to check if the add-on has an option to hide the status bar and add a regular launcher to the add-ons bar.

You could also tweak the status bar piece yourself, using [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") and [DOM Inspector]("https://addons.mozilla.org/en-US/firefox/addon/6622/"). For example to hide a status bar icon:

[LIST]
[*]Start DOM Inspector from "Firefox Menu >> Web Developer >> DOM Inspector"
[*]Click "File >> Inspect Chrome Document" and choose the first item, which is probably this page.
[*]Click the first icon on the upper left of DOM Inspector dialog. Is the one which the tooltip says "Find a node to inspect by clicking on it"
[*]Then click the status bar icon you want to change. The DOM Inspector will select the corresponding DOM element in the tree. Write the ID of the element somewhere. You will need it on the next step.
[/LIST]

With the ID of the element at hand, we will create a style sheet in Stylish. Click the Stylish button, select "Write new style >>> Blank Style...", give it a name and paste this in the code area:

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

#theidgoeshere {
	display: none !important;
}

```

Replace **#theidgoeshere** with the ID discovered by DOM Inspector.

To hide the close button use this:

```
#addonbar-closebutton {
	display: none !important;
}
```

To hide the status bar completely, use this:

```
#status-bar {
	display: none !important;
}

```

> **nullified_nostalgia said:**
> 1. Any Color (maybe firefox 4.x has a way to customize all the colors of the components like this addon does for 3.x?)


Any Color add-on has been discontinued. So, there is no point of using it anymore. Soon or later you won't be able to use it.

If you have the patience, you can use Stylish and DOM Inspector to change the color of any element.

For example, this is how to change the color of the Add-ons Bar:

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

/* add-ons bar */ 
#addon-bar {
	background-color: rgba(177, 179, 179, 1) !important;
}

/* status bar */
#status-bar {
	background-color: rgba(177, 179, 179, 1) !important;
}
```

> **nullified_nostalgia said:**
> 2. Organize Status Bar (See number 3 above for the explanation of this one)

I was a big fan of Organize Status Bar. However, with the end of the status bar, there is no point of keeping this add-on alive. It hasn't been updated since November and it unlikely that it will ever be updated again.

What I would do is to contact the developers of the add-ons that still use the status bar and don't have an alternative icon that can be placed on the add-ons bar, asking them to update their extensions.

> **nullified_nostalgia said:**
> 
Those are really the only two addons I feel I can't live without, just simply because I like to keep firefox customized.  Here's a screenshot of what my 3.x looks like in windows.  I want 4.x to look as close to this as I can possibly get it:  [http://i53.tinypic.com/9itv29.jpg](http://i53.tinypic.com/9itv29.jpg)

From what I can see, you only have Stylish add-on in the status bar. You can disable the status bar icon in Stylish preferences and place the regular icon in the add-ons bar. I use this way and it works like a charm.

I have compiled a collection of add-ons that bring some old features back to Firefox 4:

[https://addons.mozilla.org/en-US/firefox/collections/lovinglinux/firef/](https://addons.mozilla.org/en-US/firefox/collections/lovinglinux/firef/)

Let me know if you need further help.

---

### Post by nullified_nostalgia on 2011-06-08
> **lovinglinux said:**
> 
You could also tweak the status bar piece yourself, using [Stylish]("https://addons.mozilla.org/en-US/firefox/addon/2108/") and [DOM Inspector]("https://addons.mozilla.org/en-US/firefox/addon/6622/"). For example to hide a status bar icon:

[LIST]
[*]Start DOM Inspector from "Firefox Menu >> Web Developer >> DOM Inspector"
[*]Click "File >> Inspect Chrome Document" and choose the first item, which is probably this page.
[*]Click the first icon on the upper left of DOM Inspector dialog. Is the one which the tooltip says "Find a node to inspect by clicking on it"
[*]Then click the status bar icon you want to change. The DOM Inspector will select the corresponding DOM element in the tree. Write the ID of the element somewhere. You will need it on the next step.
[/LIST]

With the ID of the element at hand, we will create a style sheet in Stylish. Click the Stylish button, select "Write new style >>> Blank Style...", give it a name and paste this in the code area:

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

#theidgoeshere {
    display: none !important;
}

```Replace **#theidgoeshere** with the ID discovered by DOM Inspector.

Thank you so much, that helped me do exactly what I was wanting to do.

> **lovinglinux said:**
> 
Any Color add-on has been discontinued. So, there is no point of using it anymore. Soon or later you won't be able to use it.

If you have the patience, you can use Stylish and DOM Inspector to change the color of any element.

For example, this is how to change the color of the Add-ons Bar:

```
@namespace url(http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul);

/* add-ons bar */ 
#addon-bar {
    background-color: rgba(177, 179, 179, 1) !important;
}

/* status bar */
#status-bar {
    background-color: rgba(177, 179, 179, 1) !important;
}
```
I attempted doing this with the scroll bar but wasn't able to make it work like I did with the addon toolbar.  I was able to select the element but the scroll button, the bar behind it, and the arrows at the top and bottom of the bar don't seem to have ID's.  How would I go about finding IDs for those so I can change their colors?

---

### Post by lovinglinux on 2011-06-08
> **nullified_nostalgia said:**
> Thank you so much, that helped me do exactly what I was wanting to do.

You are welcome.

> **nullified_nostalgia said:**
> I attempted doing this with the scroll bar but wasn't able to make it work like I did with the addon toolbar.  I was able to select the element but the scroll button, the bar behind it, and the arrows at the top and bottom of the bar don't seem to have ID's.  How would I go about finding IDs for those so I can change their colors?

I think you can find the solution in the link below. However, the site seems to be down at the moment:

[http://www.google.com/url?sa=t&source=web&cd=1&ved=0CCAQrAIoATAA&url=http%3A%2F%2Fforum.userstyles.org%2Fdiscussion%2F24650%2Fhow-to-style-a-scrollbar%2Fp1&rct=j&q=Stylish%20scroll%20bar%20element&ei=SAHwTfvuD6H50gHUwYn0DA&usg=AFQjCNF_sjJXKuvT5XRO1HYFhtxijMLVtw&cad=rja](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CCAQrAIoATAA&url=http%3A%2F%2Fforum.userstyles.org%2Fdiscussion%2F24650%2Fhow-to-style-a-scrollbar%2Fp1&rct=j&q=Stylish%20scroll%20bar%20element&ei=SAHwTfvuD6H50gHUwYn0DA&usg=AFQjCNF_sjJXKuvT5XRO1HYFhtxijMLVtw&cad=rja)

---

### Post by malleeblue on 2011-06-09
I'd like to add to the mix if I may? My reason for downgrading is only this - I absolutely positively need Gmail available offline.

I live in Myanmar (Burma) where the Internet is on and off all the time. As Murphy would have it, I need it most when it's off. So offline Gmail is a must for me, and FF4, because of Google, won't give me what I want.

I love FF4 and am very happy with its speed, look, feel, etc, but no offline Gmail means I must have FF3. BTW, IMAP isn't an option from this country as it's been blocked (along with almost everything else).

If anyone knows how to get Gmail offline with FF4 then have at it.

Thanks,
malleeblue

---

### Post by lovinglinux on 2011-06-09
> **malleeblue said:**
> I'd like to add to the mix if I may? My reason for downgrading is only this - I absolutely positively need Gmail available offline.

I live in Myanmar (Burma) where the Internet is on and off all the time. As Murphy would have it, I need it most when it's off. So offline Gmail is a must for me, and FF4, because of Google, won't give me what I want.

I love FF4 and am very happy with its speed, look, feel, etc, but no offline Gmail means I must have FF3. BTW, IMAP isn't an option from this country as it's been blocked (along with almost everything else).

If anyone knows how to get Gmail offline with FF4 then have at it.

Thanks,
malleeblue

You could use FF 3.6 just for Gmail. You can manage/start multiple Firefox profiles and versions with the new [standalone profile manager]("https://developer.mozilla.org/en/Profile_Manager").

---

### Post by Krupski on 2011-06-09
> **lovinglinux said:**
> The size of the icon haven't changed. All you need is to right-click on the toolbar, select "Customize" than tick the option to "Use Small Icons".

If that isn't enough for you, let me know so I can write a style sheet to make it smaller.

That's really not the point. If I want a drink of water, all I need is the faucet, not the whole kitchen sink...

---

### Post by hhh on 2011-06-09
@Krupski, an option for using Firefox 3.6.* **with** support is to install Ubuntu 10.04. As the Desktop edition is a LTS (long-term support) release with an end of life date of April, 2013, it doesn't matter that Firefox might drop support, Canonical will provide security releases till then. When the end of life date arrives you will have to decide if you want to stay with what you have, unsupported, or upgrade to the next LTS release with whatever version of Firefox they include.

Yet another option that **won't** provide you with support is for you to install 11.04, remove Firefox 4 (via Synaptic, apt-get, etc...), temporarily change your sources.list to point to maverick, install Fx 3.6.* from there, pin it so it won't upgrade (again via Synaptic, dpkg, etc...), and revert your sources back to natty. I have no idea if you will run into dependency issues when trying this as I currently use Debian squeeze.

Cheers.

---

### Post by lovinglinux on 2011-06-09
> **hhh said:**
> @Krupski, an option for using Firefox 3.6.* **with** support is to install Ubuntu 10.04. As the Desktop edition is a LTS (long-term support) release with an end of life date of April, 2013, it doesn't matter that Firefox might drop support, Canonical will provide security releases till then. When the end of life date arrives you will have to decide if you want to stay with what you have, unsupported, or upgrade to the next LTS release with whatever version of Firefox they include.

Actually, once Mozilla drops support for Firefox 3.6, then Canonical will upgrade Firefox on all supported Ubuntu versions to the latest version available. They won't continue to provide security releases for Firefox 3.6 on their own. This already happened when Firefox 3 reached end-of-life. Canonical upgraded all Firefox versions to 3.6 at the time.

---

### Post by hhh on 2011-06-09
@lovinglinux, I didn't know that. Thanks for the info.

I suppose he could try installing Iceweasel from mozilla.debian.net?

---

### Post by lovinglinux on 2011-06-09
> **hhh said:**
> @lovinglinux, I didn't know that. Thanks for the info.

I suppose he could try installing Iceweasel from mozilla.debian.net?

Is the same thing, different name.

---

### Post by hhh on 2011-06-10
> **lovinglinux said:**
> Is the same thing, different name.
Right, but I meant I thought Debian releases security fixes for the versions in their repos. Squeeze is still using Firefox 3.5.

---

### Post by lovinglinux on 2011-06-10
> **hhh said:**
> Right, but I meant I thought Debian releases security fixes for the versions in their repos. Squeeze is still using Firefox 3.5.

Mozilla is still providing the security patches for Firefox 3.5 and 3.6. What they are not providing is for Firefox 3.0.

---

