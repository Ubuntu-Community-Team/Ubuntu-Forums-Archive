---
title: "Desktop Info App With Html Support (gtk-desktop-info)"
date: 2008-12-14
forum: General Help
---

### Post by kaivalagi on 2008-12-14
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
__________________________________________________________________________________________________________________________________[/COLOR]

[COLOR="Green"][B]If you create any good custom templates and styles, please post them. I plan on adding a custom templates and styles folder in the long term....
Also, any developers out there that want to include a new plugin of thier own, just speak up...I'd always be happy to add functionality if it's any good[/B][/COLOR]

**_[SIZE="3"][COLOR="Blue"]Intro[/COLOR][/SIZE]_**

gtk-desktop-info is a python tool to display various pieces of information directly on the desktop, using plugins for html rendering, with html templates and css style sheets for formatting.

The application has been created off the back of existing python scripts used with Conky. The reason for it's creation is a simple one, Conky is great but formatting can suck sometimes...html seemed the obvious choice of formatting giving the user the ability to construct output in a variety of styles based on understood techniques.

Please, please, please, before asking any questions have a good read of the attached guide.

General points to note about the app are:
[LIST]
[*]Very lightweight and low cpu usage
[*]Creates cropped images of the background wallpaper and uses them for the generated html background, effectively making the window transparent.
[*]Utilises webkit html rendering engine and supports images, javascript and flash as you would expect in the browser
[*]Ability to customise any output within the boundaries of what can be done with html, and as it's html there are plenty of editors out there which can help with design
[*]All output content is scrollable, so the window size remains unchanged. Using the scroll wheel on a mouse will alway you to see the extra content
[*]Variety of plugins available and you also have the ability to use external scripts for rendering content too
[/LIST]

**_[SIZE="3"][COLOR="Blue"]Plugins[/COLOR][/SIZE]_**

All the plugins have come from my conky tinkering of the past, and have been adapted to output html based information, including weather/moon/wind icons for forecasts, and coverart for music. Plugins are defined using the –plugin option of the main application.

Below is a summary of each plugin.

[LIST]
[*]“deluge” – this plugin provides a breakdown of bit torrent information, when bit torrents are managed by Deluge. It can provide detailed and/or summary info.
[*]“email” - this plugin provides email account information, a count of unread emails and optionally details of the sender and subject of the emails.
[*]“exaile” - this plugin displays Exaile based song information, cover art, rating, progress etc
[*]“feedparser” - this plugin provides rss/atom feed information
[*]“forecast” - this plugin provides weather forecast information from weather.com for a given location. It includes weather, moon and wind images, detailing the weather.
[*]“googlecalendar” - this plugin provides Google Calendar event information.
[*]“null” - this plugin provides a means to use html, javascript and flash only content. By default is displays a javascript clock.
[*]“pidgin” - this plugin provides pidgin buddy information, telling you who is online and what their status is.
[*]“processinfo” - this plugin provides process information, telling you a processes id, cpu usage and memory usage. The information can be sorted by cpu or memory usage
[*]“rhythmbox”  - this plugin displays Rhythmbox based song information, cover art, rating, progress etc 
[*]“shell” - this plugin provides a means to execute scripts and commands from within a template. Whatever can be done on the command line can be done here too.
[*]“tomboy” - this plugin provides information on Tomboy based notes, keeping most formatting from the notes intact in the output.
[*]“twitter” - this plugin provides information on all your twitter friends, shown newest to oldest - note: to get running at the very least enter your username and password into the config file copied to ~/.config/gtk-desktop-info/plugin_twitter.config
[/LIST]

Note: The shell plugin will provide the equivalent functional to that used with exec/execi calls in Conky. The big difference however, is that it sources all the results from execs inside [] from within a template file, meaning that formatting of command line results is much simpler and neater. A lyrics scripts would work nicely in it for example ;)

**_[SIZE="3"][COLOR="Blue"]Current Limitations[/COLOR][/SIZE]_**

Compiz wallpaper settings are not supported yet, however gnome, xfce, kde3, and kde4 are.

If tiling or simple background colours are used, the application will no handle these well.

I am attempting to find a better way to handle system wallpaper, independently from the window manager type, so that the only thing this application will be dependant on is gtk, webkit and python libraries. However this may be some time off. If you have issues with wallpapers and the fake transparency is not working, I suggest you use the –wallpaper option, as described in the guide.


**_[SIZE="3"][COLOR="Blue"]Basic Install[/COLOR][/SIZE]_**

**[COLOR="Blue"]Method 1: Using apt[/COLOR]**

1) Create the necessary list file for access to the repository by running one of these:

Lucid Lynx:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
```

Karmic Koala:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-karmic.list -O /etc/apt/sources.list.d/conkyhardcore-karmic.list
```

Jaunty Jackalope:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-jaunty.list -O /etc/apt/sources.list.d/conkyhardcore-jaunty.list
```

Intrepid Ibex:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-intrepid.list -O /etc/apt/sources.list.d/conkyhardcore-intrepid.list
```

2) Add the gtk-desktop-info repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-key.gpg -O- | sudo apt-key add -
```

3) Now that is done simply run the following to install

```
sudo apt-get update && sudo apt-get install gtk-desktop-info

```

**[COLOR="Blue"]Method 2: Using tar.gz file[/COLOR]**

**Only go this route if you know what you're doing, you are not likely to get much help if you get stuck!**

1) Go to [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa") and download the latest tar.gz files for gtk-desktop-info and gtk-desktop-info-data packages.

2) Extract all the contents of the tar.gz files to an appropriate folder of your choice, the default location is /usr/share/gtk-desktop-info

3) Copy the gtk-desktop-info and gtk-desktop-info.guide script files to /usr/bin, edit them to point to the folder you extracted everything to, and make them executable

There are several dependencies for the app to run, these are:
[LIST]
[*]Python Google GData API
[*]Python PyWebKitGtk libraries
[*]Python Imaging library
[*]Python Xlib Libraries
[/LIST]
Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use the first method as all dependencies will be handled. You will not receive updates using this method either.

Any further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE="3"][COLOR="Blue"]Usage Help[/COLOR][/SIZE]_**

Refer to the attached guide for a detailed explanation of the application, along with information on the command line usage etc. The guide is also available within the install, it can be opened by running the following (evince is expected to be installed):

```
gtk-desktop-info.guide
```

You can also see the available options by running this in a terminal:

```
gtk-desktop-info -h
```


**_[SIZE="3"][COLOR="Blue"]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [https://code.launchpad.net/~m-buck/+junk/gtk-desktop-info](https://code.launchpad.net/~m-buck/+junk/gtk-desktop-info)

All packages available from me can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa](https://launchpad.net/~conkyhardcore/+archive/ppa)

---

### Post by kerry_s on 2008-12-14
what's the resource usage like?

---

### Post by martynp on 2008-12-14
I can confirm resource usage is low....... comparable to conky........

Kav has done a great job here.... this is a very versatile app already and I know it's gonna get even better.

Keep up the great work!

Martyn

---

### Post by kaivalagi on 2008-12-14
> **kerry_s said:**
> what's the resource usage like?

The plugins do the same amount of work as their equivalent scripts for conky. The main app only really has to render the html via a webkit view on a refresh call, so wont use more (if any) cpu than conky...Memory may be higher though, I am not sure.

On my system, I see zero cpu usage when the app is idle (in between intervals), with peaks when a refresh takes place of 2-3% maximum

I am running a quad code cpu though....

As the app runs instances for each plugin, and most plugins do not need a 1 second refresh rate, the hit on cpu usage for a whole desktop is low...

---

### Post by shadesofevil on 2008-12-14
my my my you've really outdone yourself! great-work!

---

### Post by Bruce M. on 2008-12-14
I'm going to be one of the:
> How did you do that? Please share config file.
guys here.

My HTML skills are ten years old and I was just beginning to "experiment" with stylesheets.

{sigh} Talk about feeling old ... even my second grandson didn't do this to me.

[B][CENTER][COLOR="Blue"][SIZE="6"]Job Well Done Award
&
Medal of Excellence[/SIZE][/COLOR][/CENTER][/B]

Absolutely great job!

Chimo!
Bruce

---

### Post by HippyRandall on 2008-12-14
> **Bruce M. said:**
> My HTML skills are ten years old and I was just beginning to "experiment" with stylesheets.
{sigh} Talk about feeling old ... even my second grandson didn't do this to me.
Chimo!
Bruce
:lolflag::lolflag::lolflag:

here's a shell.template I use:
```
<div id="wrapper">
    <div class="hugedark" align="right">[date +"%I<span class="hugelight">:</span>%M%p"]</div>
    <div class="mediumlight" align="right">[date +"%a, <span class="largedark">%d</span> %B"]</div>
    <div class="mediumdark" align="right">Core 0: <span class="mediumlight">[sensors |grep Core0 |cut -c15-16]&deg;C</span> <span class="mediumdark">| Core 1: <span class="mediumlight">[sensors |grep Core1 |cut -c15-16]&deg;C</span> | GPU: <span class="mediumlight">[nvidia-settings -q gpucoretemp |grep Attribute |cut -c47-48]&deg;C</span><br></div>
</div>
```nothing special other than liking to see my temps :)

---

### Post by kaivalagi on 2008-12-14
> **Bruce M. said:**
> My HTML skills are ten years old and I was just beginning to "experiment" with stylesheets.

{sigh} Talk about feeling old ... even my second grandson didn't do this to me.

Absolutely great job!

Chimo!
Bruce

Don't worry, Hippy and I will hone your skills again!

You can always use something like bluefish to get a html page sorted out, then edit that in gedit/mousepad to put in the details...

Thanks for the award, I am not very good at accepting compliments though :oops: Time will tell whether I deserve it or not...

I just hope people get something out of it

K

---

### Post by kaivalagi on 2008-12-14
> **shadesofevil said:**
> my my my you've really outdone yourself! great-work!

Thanks, glad you think so

I just hope it's not too complicated for most...I really don't want to be answering questions all day everyday...gonna need some support personnel I think!

---

### Post by ad_267 on 2008-12-15
Wow this looks great, good job!

---

### Post by Bruce M. on 2008-12-15
> **HippyRandall said:**
> :lolflag::lolflag::lolflag:

Laughing at an old man isn't nice you young whipper-snapper! :D

> **HippyRandall said:**
> here's a shell.template I use:
```
<div id="wrapper">
    <div class="hugedark" align="right">[date +"%I<span class="hugelight">:</span>%M%p"]</div>
    <div class="mediumlight" align="right">[date +"%a, <span class="largedark">%d</span> %B"]</div>
    <div class="mediumdark" align="right">Core 0: <span class="mediumlight">[sensors |grep Core0 |cut -c15-16]&deg;C</span> <span class="mediumdark">| Core 1: <span class="mediumlight">[sensors |grep Core1 |cut -c15-16]&deg;C</span> | GPU: <span class="mediumlight">[nvidia-settings -q gpucoretemp |grep Attribute |cut -c47-48]&deg;C</span><br></div>
</div>
```nothing special other than liking to see my temps :)

Thanks Hip, I'll give it a go.  :)
I just might create and "old" style html page, with depreciated code, and no css sheet. to start with.  :)

But I am going to play with this.  :)
CHIMO!
Bruce

---

### Post by Gnounc on 2008-12-16
Wow, I finally decided to find out what conky was all about YESTERDAY.
Talk about good timing. This is pretty amazing.
Good work. Keep it up!
*shoves nose back into manpages*

---

### Post by Bruce M. on 2008-12-16
> **kaivalagi said:**
> Don't worry, Hippy and I will hone your skills again!

No doubt in that, also my inner self that wants my layout to be "mine" will encourage re-learning an old subject.  :)

> **kaivalagi said:**
> You can always use something like bluefish to get a html page sorted out, then edit that in gedit/mousepad to put in the details...

Yup, have had bluefish for a while now, not a lot of time to play with it. To busy tweaking conky.  Of course now .... :lolflag:

> **kaivalagi said:**
> Thanks for the award, I am not very good at accepting compliments though :oops: Time will tell whether I deserve it or not...

From the other posts I see here I have one thing to say: Get use to it!

You've worked hard, people have noticed. Accept it! There are people that appreciate what you've done and will be here to help and improve it, via suggestions or code.  :)

> **kaivalagi said:**
> I just hope people get something out of it

K

Oh I'm sure they will. I know **I** will.

I tried three times yesterday to respond to this, and kept getting dropped carrier. :mad: I hope this time it works! =D>

Chimo!
Bruce

---

### Post by dksdk on 2008-12-17
~$ gtk-desktop-info
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 334, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 100, in __init__
    self.options.css = app_path+"/style/plugin_"+self.options.plugin+"_"+self.options.colour+".css"
TypeError: cannot concatenate 'str' and 'NoneType' objects

 hi this is what i get if i try runnuing this. Install was without a problem. What do i do. Thanks in advance.

---

### Post by kaivalagi on 2008-12-17
> **dksdk said:**
> ~$ gtk-desktop-info
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 334, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 100, in __init__
    self.options.css = app_path+"/style/plugin_"+self.options.plugin+"_"+self.options.colour+".css"
TypeError: cannot concatenate 'str' and 'NoneType' objects

 hi this is what i get if i try runnuing this. Install was without a problem. What do i do. Thanks in advance.

You are running the app with no options, take a look at the guide pdf to see example usage. Run this to view it:

```
gtk-desktop-info.guide

```

You should run it with the plugin option as a bare minimum:

```
gtk-desktop-info --plugin=shell
```

I'll update the app to have it run the shell plugin by default when no options are given...new release will have this. [COLOR="Blue"]Edit: 0.04 now has this feature[/COLOR]

---

### Post by vitorio on 2008-12-19
I've tried to install using the first method suggested, i.e. running this:
> ```
sudo apt-get update && sudo apt-get install gtk-desktop-info
```

And get the following in response:
```
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable
E: Broken packages

```

I'm running 8.04 LTS. The missing python-webkitgtk package is not in Synaptic. Universe, Multiverse, Restricted, and suggested [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) intrepid main are enabled. 

-First question is were to find the package?  
-Second-why it is claimed "not installable"?  Am I running a risk to break anything on my 8.04 LTS by installing it?

Thanks

---

### Post by kaivalagi on 2008-12-19
> **vitorio said:**
> I've tried to install using the first method suggested, i.e. running this:


And get the following in response:
```
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable
E: Broken packages

```

I'm running 8.04 LTS. The missing python-webkitgtk package is not in Synaptic. Universe, Multiverse, Restricted, and suggested [http://ppa.launchpad.net/m-buck/ubuntu](http://ppa.launchpad.net/m-buck/ubuntu) intrepid main are enabled. 

-First question is were to find the package?  
-Second-why it is claimed "not installable"?  Am I running a risk to break anything on my 8.04 LTS by installing it?

Thanks

gtk-desktop-info is made for intrepid (8.10), and it looks like unfortunately it wont work for older versions of Ubuntu such as hardy (8.04) because of dependencies.

If 8.04 does not have the python-webkitgtk package available, which seems to be the case, then gtk-desktop-info can't install either. Webkit is necessary for the working of gtk-desktop-info, without it html cannot be rendered on the desktop...have you tried the backports in case webkit is there?

Alternatively you may be able to find a deb package of webkit to download and install manually onto 8.04, then the install will have a better chance...but I have no idea where to look for it. Try googling for "deb" and "webkitgtk" and see what you can find...

Sorry I can't be of more help

---

### Post by HippyRandall on 2009-01-04
ok so not much has been going on in this thread since K started it. :( I have been thinking about implementing some stuff from: [http://jquery.com/](http://jquery.com/)
I also found:
[http://www.ndesign-studio.com/demo/css-dock-menu/css-dock.html](http://www.ndesign-studio.com/demo/css-dock-menu/css-dock.html) from
[http://www.ndesign-studio.com/blog/mac/css-dock-menu](http://www.ndesign-studio.com/blog/mac/css-dock-menu)
that might be some fun as a custom html launcher...if I can figure out how?! lol

Cheers all and let's see some customization already!!!

Hippy

---

### Post by stepper on 2009-01-05
Nice app again, K.

Request: I'm using the gtk-desktop-info exaile-plugin through conky and I'm enjoying it, one thing though... can you by any chance include playback controls like pause,forward and play on the plugin itself.

Nice work on all the scripts, keep it up!

---

### Post by kaivalagi on 2009-01-05
> **stepper said:**
> Nice app again, K.

Request: I'm using the gtk-desktop-info exaile-plugin through conky and I'm enjoying it, one thing though... can you by any chance include playback controls like pause,forward and play on the plugin itself.


Play back will be an issue, the app is essentially much the same as conky except it renders everything in html rather than plain text with fonts.

Because of this, the output is generally read only.

To get playback controls would require some clever javascript to talk to exaile from a browser window basically. If you can find some way to talk to exaile using javascript then I'd be happy to help you implement it in a template.

Food for thought.....how to render html but also have rich python gui content too.

Now if you used rhythmbox I could point you in the direction of the desktop-art plugin for it in my repos...;)

> **stepper said:**
> Nice work on all the scripts, keep it up!
Some thanks have to go to Hippy, he helped me with the templates and css, and went through the pain of testing it with me before it was put out there for everyone.

---

### Post by kaivalagi on 2009-01-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

The following changes have been made:

**gtk-desktop-info**
[LIST]
[*]Fixed sort order in email plugin
[*]Fixed cover art file path urlquote functionality for unicode characters
[*]Fixed limit function in google calendar plugin, was not outputting anything after hitting an imposed limit
[*]Added limit function to pidgin plugin, set in the config
[*]Added sortbylogactivity function to pidgin plugin, set in the config, useful used in conjunction with the limit option.
[/LIST]

**gtk-desktop-info-data**
[LIST]
[*]Renamed offline pidgin icon to support decent ordering of list, offline last...
[/LIST]

The changes to the packages are available by apt

---

### Post by kaivalagi on 2009-01-08
See changes above :)

Edit: still the new post doesn't register...something is not quite right with posts....nothing registering as new

---

### Post by kaivalagi on 2009-01-09
See changes above the above...

---

### Post by Gnounc on 2009-01-21
I was wondering if there is a way i could display the users buddy icons in gtk-desktop-info.

what i'd like to do is have a static list of 5 people on the desktop and they light up when online, and gray out when offline. just their buddy icons, no names nothin else.

i know i can do this with the ignore list options and the show offline options, 
so the last peice is using their buddy icons. 

thx

---

### Post by kaivalagi on 2009-01-21
> **Gnounc said:**
> I was wondering if there is a way i could display the users buddy icons in gtk-desktop-info.

what i'd like to do is have a static list of 5 people on the desktop and they light up when online, and gray out when offline. just their buddy icons, no names nothin else.

i know i can do this with the ignore list options and the show offline options, 
so the last peice is using their buddy icons. 

thx

Good call...there must be a way, although I have no idea at the moment

I'll take a look over the next few days or so and see what I come up with
[COLOR="Blue"]
Edit: easier than I thought, the new release (0.06) below has the feature :) read the bit at the bottom of the next post...it might be a good thing for what you want?[/COLOR]

---

### Post by kaivalagi on 2009-01-21
[COLOR="Red"][SIZE="5"]**UPDATE**[/SIZE][/COLOR]

An update has just gone out with the following changes. It should be available via apt soon(ish) - launchpad is quoting 1 hour before the build commences...

**gtk-desktop-info:**

[LIST]
[*]Added pragma no cache meta tag to html head of all output
[*]Fixed up rhythmbox plugin to work better with last.fm and CD based music info
[*]Updated rhythmbox coverart function to handle internet based art too for last.fm
[*]Added buddy icon to plugin_pidgin
[*]Updated plugin_pidgin.template to include buddy icon
[*]Updated guide to include new options available
[/LIST]

**gtk-desktop-info-data:**

[LIST]
[*]Added Polish translation for plugin_forecast
[*]Updated Romanian translation for plugin_forecast
[*]Included missing spacer.png file
[/LIST]

**Feedback please**

Currently all the plugins that display images do so with a IMAGESIZE setting in the config file for that plugin. I am thinking of removing this feature and instead updating the templates to suit. I would basically setup the templates <img> tags with a hard coded width and then feed the url for the image source from the plugin instead. In doing so the sizes of different images in a single plugin could be set independently from each other by tweaking the template text instead...

Any thoughts? Good? Bad?

If I don't here anything in the next few days I'll go ahead and make the changes to the plugin code and default template files.

[COLOR="Navy"]Edit: I've attached a screenshot demonstrating what varying image sizes can do for output for rhythmbox and forecast plugins...[/COLOR]

**Any other ideas - speak up! :)**

---

### Post by Gnounc on 2009-01-21
hahaha, I like the idea, I was just waiting for gtk-desktop update to hit the repos..
im getting the message "Window moved to 0,25" and my wallpaper in gtk-desktop-info is misalgned...presumably by 25. Where do you think the movements coming from, so I can set it to zero?

---

### Post by HippyRandall on 2009-01-21
> **Gnounc said:**
> hahaha, I like the idea, I was just waiting for gtk-desktop update to hit the repos..
im getting the message "Window moved to 0,25" and my wallpaper in gtk-desktop-info is misalgned...presumably by 25. Where do you think the movements coming from, so I can set it to zero?
it is likely getting pushed down by the top panel. try setting your y value to 25: ```
--y=25
```

Hippy

---

### Post by Gnounc on 2009-01-21
I went to just shut off gnome panel, and I'm finding it wont stay off.
Ive killed its process, and it just pops back up. Any thoughts.
Oh and how is that css navbar going? It looks sweet.

---

### Post by HippyRandall on 2009-01-21
> **Gnounc said:**
> I went to just shut off gnome panel, and I'm finding it wont stay off.
Ive killed its process, and it just pops back up. Any thoughts.
Oh and how is that css navbar going? It looks sweet.
I have not messed around with it actually. My sister is up from Texas till saturday and I doubt I will get to it before then.
As to the panel problem, I am not sure. Never had that problem before.

Hippy

---

### Post by Gnounc on 2009-01-21
Anybody have a good audioscrobbler for xmms2?
I have one...but it isnt exactly working, and I cant seem to find another option.

---

### Post by kaivalagi on 2009-01-22
> **Gnounc said:**
> Anybody have a good audioscrobbler for xmms2?
I have one...but it isnt exactly working, and I cant seem to find another option.

I used to use xmms2 and the xmms2-scrobbler package which I am assuming you are currently using? You setup the necessary config file in your ~/.xmms2/clients/xmms2-scrobbler directory for it to work right? I dont know of any other tool for the job, have you tried the xmms2 wiki? Or asked in IRC at #xmms2 on freenode?

I now use rhythmbox cause it is just much easier to setup everything like last.fm support etc...but there is a resource overhead...

P.S. I will apply the changes related to image sizing soon, it is working great and I see no reason not to do it...

---

### Post by Gnounc on 2009-01-22
yeah thats exactly what im using. i love the zero overhead, and that conky has built in support. ill check irc later haha, one project at a time (right now its moving conky into gtk-desktop-info. sweet, ill be waiting on the image sizes, Will that work on 
 [icon] for the pidgin plugin?

---

### Post by kaivalagi on 2009-01-22
> **Gnounc said:**
> yeah thats exactly what im using. i love the zero overhead, and that conky has built in support. ill check irc later haha, one project at a time (right now its moving conky into gtk-desktop-info. sweet, ill be waiting on the image sizes, Will that work on 
 [icon] for the pidgin plugin?

The new template for pidgin will look something like this (still playing with them all):

[PHP]<table class="contentbottom" border="0" cellspacing="0" cellpadding="0">
	<tr>
		<td width="28"><img src="[status]" width="24"/></td>
		<td width="68"><img src="[icon]" width="64"</td>
		<td>
			<div><span class="mediumdark"> [alias] </span><span class="mediumlight">([group])</span></div>
			<div class="mediumlight">[status_message]</div>
		</td>
	</tr>
	<tr><td>&nbsp;</td></tr>
</table>[/PHP]

So the source of the image is provided by the plugin rather than the whole image tag...

---

### Post by Gnounc on 2009-01-22
is there a way to set up a set of images in their place? (im not getting greedy haha just curious). like offline.img.src="www.flickr.com/3323.jpg"> ?

actually, after image sizes are done, what i want to do is easily done.

ps, glad to have such an accessable dev, and i've seen around the forums that so are a lot of other people. Thank you

---

### Post by kaivalagi on 2009-01-22
> **Gnounc said:**
> is there a way to set up a set of images in their place? (im not getting greedy haha just curious). like offline.img.src="www.flickr.com/3323.jpg"> ?

actually, after image sizes are done, what i want to do is easily done.

ps, glad to have such an accessable dev, and i've seen around the forums that so are a lot of other people. Thank you

It's just html, in this case html that is repeated for each buddy

Just remember this is a hobby and not a job for me...so things can take time...the wife sees to that :)

---

### Post by HippyRandall on 2009-01-25
> **HippyRandall said:**
> I have not messed around with it actually. My sister is up from Texas till saturday and I doubt I will get to it before then.
As to the panel problem, I am not sure. Never had that problem before.

Hippy

Had a look at this but can't figure out how to launch an app from the html. I am thinking that a new plugin is needed with some default options like [text] for text editor, [brower] for FF or web browser, etc etc etc.
If I can get this headache to quit I might have a go at the python code for shell and modify it for this purpose. It will be nothing but dirty hacks I am sure since my python skills are severely limited.

Hippy

---

### Post by kaivalagi on 2009-01-25
> **HippyRandall said:**
> Had a look at this but can't figure out how to launch an app from the html. I am thinking that a new plugin is needed with some default options like [text] for text editor, [brower] for FF or web browser, etc etc etc.
If I can get this headache to quit I might have a go at the python code for shell and modify it for this purpose. It will be nothing but dirty hacks I am sure since my python skills are severely limited.

Hippy

I may be missing the point, but here goes...

You'll have to bear in mind that all of the output is rendered in a web browser "view" / webkitview. I would presume this means there is no way of getting back to the code that created it from the html / javascript content displayed.

Essentially do you want to have html with javascript, executing app links? If so you'll need to find a way in pure javascript I think.

Although, this area is by no means a strong point of mine, so there may well be a way...I just don't know of one.

---

### Post by HippyRandall on 2009-01-27
> **kaivalagi said:**
> I may be missing the point, but here goes...

You'll have to bear in mind that all of the output is rendered in a web browser "view" / webkitview. I would presume this means there is no way of getting back to the code that created it from the html / javascript content displayed.

Essentially do you want to have html with javascript, executing app links? If so you'll need to find a way in pure javascript I think.

Although, this area is by no means a strong point of mine, so there may well be a way...I just don't know of one.

I had this convoluted idea of making an html app launcher that I could set to my widget layer in compiz and thereby have access to most often used apps without the need for gnome panel. I can't figure out how to make it work though so it is something of a moot point. ;)

Hippy

---

### Post by Bruce M. on 2009-02-02
Good morning K

I have the answer. What answer you say. A long time ago I asked about using the script with Xubuntu but I had to manually change what wallpaper I was using because we didn't know where Xubuntu "stored" the information. Well I found it:
```
~/.config/xfce4/mcs_settings/desktop.xml
```
Mine looks like this:
```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mcs-option SYSTEM "mcs-option.dtd">

<mcs-option>
	<option name="brightness_0_0" type="int" value="0"/>
	<option name="color1_0_0" type="color" value="           15104,           23296,           35072,           65535"/>
	<option name="color2_0_0" type="color" value="           15872,           26624,           40448,           65535"/>
	<option name="colorstyle_0_0" type="int" value="0"/>
	<option name="desktopiconstyle" type="int" value="2"/>
	<option name="icons_font_size" type="int" value="10"/>
	<option name="icons_icon_size" type="int" value="28"/>
	<option name="icons_use_system_font_size" type="int" value="0"/>
	<option name="imagepath_0_0" type="string" value="/home/bruloo/Wallpapers/Canuk-Arg.png"/>
	<option name="imagepath_0_1" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
	<option name="imagepath_1_0" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
	<option name="imagepath_1_1" type="string" value="/usr/share/xfce4/backdrops/xubuntu-jmak.png"/>
	<option name="imagestyle_0_0" type="int" value="1"/>
	<option name="showdm" type="int" value="0"/>
	<option name="showfilesystem" type="int" value="0"/>
	<option name="showhome" type="int" value="0"/>
	<option name="showimage_0_0" type="int" value="1"/>
	<option name="showimage_0_1" type="int" value="1"/>
	<option name="showimage_1_0" type="int" value="1"/>
	<option name="showimage_1_1" type="int" value="1"/>
	<option name="showremovable" type="int" value="0"/>
	<option name="showtrash" type="int" value="0"/>
	<option name="showwl" type="int" value="1"/>
</mcs-option>
```
Any chance of seeing this applied to the script?

CHIMO!
Bruce

---

### Post by kaivalagi on 2009-02-02
Bruce,

I started tinkering with this a while back and hit issues with the multiple screens...

I should be able to get it working with the first screen setting on all desktops...much like conky does (i.e. using imagepath_0_0), I'll take a look over the next week and maybe I'll have something this weekend (maybe)

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Red"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Red"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by kaivalagi on 2009-02-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

New versions will be available shortly via apt

**gtk-desktop-info** changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.08_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.08_source.changes)

**gtk-desktop-info-data** changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.04_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.04_source.changes)

---

### Post by Bruce M. on 2009-02-11
When it comes to this program that I want desperately to work for me I find out just how big a nOOb I am.

I can't for the life of me get it to work.
All I get is the image attached and that disappears when I close the terminal.

Can someone who has this working for weather show a screenie, and "all" your files that produced it.

Please - HELP!
Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-02-11
> **Bruce M. said:**
> When it comes to this program that I want desperately to work for me I find out just how big a nOOb I am.

I can't for the life of me get it to work.
All I get is the image attached and that disappears when I close the terminal.

Can someone who has this working for weather show a screenie, and "all" your files that produced it.

Please - HELP!
Have a nice day.
Bruce

Bruce,

Take a look at the guide, you can open it on your PC by running this command (assuming you have evince installed):

```
gtk-desktop-info.guide
```

Or you can get the PDF from the first post attachments

Glance through it to get an idea and then take a look at the last pages which have an example set of commands. The same script can be found in /usr/share/gtk-desktop-info/example/

If you've been through all that and still need help then fire away :)

P.S. you did get it working....you have the default system clock at the top right of the rectangle :)

---

### Post by Bruce M. on 2009-02-11
> **kaivalagi said:**
> Bruce,

P.S. you did get it working....you have the default system clock at the top right of the rectangle :)

Got it all, read it, but my brain must have been fried!
Anyway, I have more to post tomorrow ... errr later today.
Gotta get some shut eye.

More when I wake.
CHIMO!
Bruce

---

### Post by kerobaros on 2009-02-12
First off, love the program with all my heart and soul. It's lightyears beyond the amazingness that is conky, and can only get better.

That being said, here's my problem. (You knew I had one.) I've had gtk-desktop-info cranking along perfectly in the corner of my display, showing me current weather information for my area. Everything was great until I updated to 0.08, when it started displaying this upon relaunch:
[IMG]https://dl-web.getdropbox.com/get/Photos/gtk-desktop-info_images-what-images.png?w=e4138880[/IMG]
Yeah. Not so perfect anymore. Anyone got any ideas on what I screwed up? :p

Relevant software versions: Ubuntu Intrepid 8.10 (obviously), libwebkit-1.0-1 (1.0.1-2ubuntu0.1), python-webkitgtk (1.0.1-0ubuntu2), python-xlib (0.14-2), gtk-desktop-info-data (0.04), gtk-desktop-info (0.08).
The template I'm using for weather is (as far as I recall) the default, but tweaked for my location.

---

### Post by Bruce M. on 2009-02-12
OK, as promised here's what mine looks like. It's the straight out of the box config with LOCALE = es (Spanish)

Obviously I need to do some editing. But what is important is that one of the latest additions to the program allows for Xfce users to have the background match as it always was for Gnome users.

Here is what it looks like:
[CENTER][[IMG]http://img21.imageshack.us/img21/4342/desktopjg0.th.gif[/IMG]](http://img21.imageshack.us/my.php?image=desktopjg0.gif)


[[IMG]http://img502.imageshack.us/img502/4968/desktop2kg7.th.gif[/IMG]](http://img502.imageshack.us/my.php?image=desktop2kg7.gif)[/CENTER]

And the command to do that:
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=380 --x=10 --y=30 --windowmanager=xfce4 --plugin=forecast &
```

Now I have to practice my HTML skills again. They are really rusty.

Thanks kaivalagi for one super-duper-extra-special-fantastic-wonderful program.
{did I miss an adjective?}
Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-02-12
> **kerobaros said:**
> First off, love the program with all my heart and soul. It's lightyears beyond the amazingness that is conky, and can only get better.

That being said, here's my problem. (You knew I had one.) I've had gtk-desktop-info cranking along perfectly in the corner of my display, showing me current weather information for my area. Everything was great until I updated to 0.08, when it started displaying this upon relaunch:
[IMG]https://dl-web.getdropbox.com/get/Photos/gtk-desktop-info_images-what-images.png?w=e4138880[/IMG]
Yeah. Not so perfect anymore. Anyone got any ideas on what I screwed up? :p

Relevant software versions: Ubuntu Intrepid 8.10 (obviously), libwebkit-1.0-1 (1.0.1-2ubuntu0.1), python-webkitgtk (1.0.1-0ubuntu2), python-xlib (0.14-2), gtk-desktop-info-data (0.04), gtk-desktop-info (0.08).
The template I'm using for weather is (as far as I recall) the default, but tweaked for my location.

Dropbox image isn't coming through for me...can you post the screenshot on the thread itself?

I am guessing the issue relates to image output? If you have copied a template and are using --template to point to it, it might be because the template requirements for images have changed....if this is the case take a look at the new forecast template under /usr/share/gtk-desktop-info/templates

---

### Post by kaivalagi on 2009-02-12
> **Bruce M. said:**
> OK, as promised here's what mine looks like. It's the straight out of the box config with LOCALE = es (Spanish)

Obviously I need to do some editing. But what is important is that one of the latest additions to the program allows for Xfce users to have the background match as it always was for Gnome users.

Here is what it looks like:
[CENTER][[IMG]http://img21.imageshack.us/img21/4342/desktopjg0.th.gif[/IMG]](http://img21.imageshack.us/my.php?image=desktopjg0.gif)


[[IMG]http://img502.imageshack.us/img502/4968/desktop2kg7.th.gif[/IMG]](http://img502.imageshack.us/my.php?image=desktop2kg7.gif)[/CENTER]

And the command to do that:
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=380 --x=10 --y=30 --windowmanager=xfce4 --plugin=forecast &
```

Now I have to practice my HTML skills again. They are really rusty.

Thanks kaivalagi for one super-duper-extra-special-fantastic-wonderful program.
{did I miss an adjective?}
Have a nice day.
Bruce

Nice to see you are getting somewhere, you'll get the nack for it all soon enough...where there's a will there's a way as they say :)

**[COLOR="Red"]Quick note to all - this is using version 0.09 which isn't public yet....it will handle gnome/kde3/kde4 and xfce. I am just waiting on details on kerobaros's issue before releasing in case I need to fix a bug...[/COLOR]**

---

### Post by kerobaros on 2009-02-12
Here you go!

When you say 'the requirements for images changed'.. uh, I'll go look at the new template. :p

EDIT: yeah, I get it now. '[--datatype=WF]' used to spit out '<img src="image_url">', and now it spits out 'image_url'. Okay, rock on, that makes a lot of sense. Sorry to hold things up, as you were!

---

### Post by kaivalagi on 2009-02-12
> **kerobaros said:**
> Here you go!

When you say 'the requirements for images changed'.. uh, I'll go look at the new template. :p

EDIT: yeah, I get it now. '[--datatype=WF]' used to spit out '<img src="image_url">', and now it spits out 'image_url'. Okay, rock on, that makes a lot of sense. Sorry to hold things up, as you were!

I removed the IMAGE_SIZE option from the forecast config and image tags now need defining in the templates as the script only populates the actual image source now.

So the image part in a template has gone from a simple:

[--datatype=WF]

which will get replaced the the whole image tag, to:

<img src="[--datatype=WF]" width="64"/>

where only the image source is replaced

It means the the image sizes can be independently sized without one set size for all.

So if you are using the old template you'll get an image tag inside the image source...

Hope that makes sense

edit: I'll rollout the new version in a while as there is no bug to fix

---

### Post by Bruce M. on 2009-02-12
> **kaivalagi said:**
> Nice to see you are getting somewhere, you'll get the nack for it all soon enough...where there's a will there's a way as they say :)

Yup, just as soon as I brush up on HTML stuff, it wont take long.
Taking into account my wife and I share the computer, it might not be as fast as I'd like.

> **kaivalagi said:**
> **[COLOR="Red"]Quick note to all - this is using version 0.09 which isn't public yet....it will handle gnome/kde3/kde4 and xfce. I am just waiting on details on kerobaros's issue before releasing in case I need to fix a bug...[/COLOR]**

[CENTER]**[SIZE="7"][COLOR="DarkRed"]Oops![/COLOR][/SIZE]**
**So sorry, I didn't realize!**
Oh well, the cat's outta the bag now.:lolflag:

Now you have to make it work![/CENTER]

---

### Post by kaivalagi on 2009-02-12
> **Bruce M. said:**
> Yup, just as soon as I brush up on HTML stuff, it wont take long.
Taking into account my wife and I share the computer, it might not be as fast as I'd like.



[CENTER]**[SIZE="7"][COLOR="DarkRed"]Oops![/COLOR][/SIZE]**
**So sorry, I didn't realize!**
Oh well, the cat's outta the bag now.:lolflag:

Now you have to make it work![/CENTER]

Don't sweat it :) It will be available any time soon, now I know there isn't a bug to fix (yet)...

---

### Post by kaivalagi on 2009-02-12
**[COLOR="Orange"][SIZE="5"]UPDATE[/SIZE][/COLOR]**

I've updated the script, the first post has the new guide (forgot to add it to this release...whoops) and the apt package will be available shortly

Changes can be found here: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.09_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.09_source.changes)

---

### Post by paulus4605 on 2009-02-13
> **Bruce M. said:**
> 
Taking into account my wife and I share the computer, it might not be as fast as I'd like.
[/CENTER]

Bruce,

If I recall correctly from one of your posts on the conky threads you stated that your wife likes the forecasts and stuff like that too.

just tell her that you want to surprise her with a good brandnew conky for valentines day and that you need to work on the computer for that.

kaivalagi I see that your wife is also watching you to make sure that you have some family time and shut your computer down to.

mine is even worse she just gives me my 6 week old kid and tells me to change her and bath her.

so if I see it correctly we are all in the same boat :lolflag: ohhh well back to the guide and see if I can get my wife upset again lol 

at least I have 8 hours at work where I can play with conky otherwhise my behind is fried lol

---

### Post by kaivalagi on 2009-02-13
> **paulus4605 said:**
> kaivalagi I see that your wife is also watching you to make sure that you have some family time and shut your computer down to.

Tell me about it, she never stops....just like me :)

---

### Post by paulus4605 on 2009-02-13
kaivalagi:

1.where can I find the config/template files for the normal conky?
2.I noticed that for the general forecast template the windspeed isn't correctly translated in dutch I see in my example for today 4mph
3. where can I adapt the settings for my desktop to have the right resolution of 1280 by 800 


thanks again for the great work

---

### Post by kaivalagi on 2009-02-13
> **paulus4605 said:**
> 1.where can I find the config/template files for the normal conky?

Normal conky? This app doesn't go near conky. Normal conky config for forecast is at ~/.conkyForecast.config, templates are created by users, the only existing ones on the conky script installs are in the respective  example folder unser /usr/share. Not much use at all for this app though

> **paulus4605 said:**
> 2.I noticed that for the general forecast template the windspeed isn't correctly translated in dutch I see in my example for today 4mph

The translation code and po/mo files are the same for both conkyForecast and gtk-desktop-info forecast plugin, if you need to replace the gtk-desktop-info forecast translation files with what you have with the conkyForecast setup, you need to go to /usr/share/gtk-desktop-info/locale/nl/...notice the filename difference

I have your dutch translations in place in dev on my machine, they'll go out with both scripts next release

> **paulus4605 said:**
> 3. where can I adapt the settings for my desktop to have the right resolution of 1280 by 800 

This is down to messing with the --height, --width, --x and --y options on each call to gtk-desktop-info. A tip, if you run the app from the terminal, if you then use Alt-left mouse on the transparent window and drag it, you can reposition it and get feedback on where is has been moved to in the terminal. You can then take those x/y coords and update the script call with them for next time.

Hope that makes sense...although similar to conky in function the setup of the script is done slightly differently.

---

### Post by paulus4605 on 2009-02-13
hmmm I found the coordinates without a problem just trying to figure out where to put them, if I change the coordinats to this ones 36,454 I still get into the terminal moved to 0,24 :confused::confused::confused:  how do I get rid of this 0,24 ?


I also noticed that you have a complete weather map underneeth the 5 day weather prediction is that normal?

Paul

---

### Post by Bruce M. on 2009-02-13
> **paulus4605 said:**
> Bruce,

If I recall correctly from one of your posts on the conky threads you stated that your wife likes the forecasts and stuff like that too.

just tell her that you want to surprise her with a good brandnew conky for valentines day and that you need to work on the computer for that.

I cannot quote what she would say here, they'd ban me, but she would be sitting at the computer. For us Valentines Day is the other 364 days of the year that "others" don't celebrate it, and quite possibly ignore the meaning behind it.

> **paulus4605 said:**
> kaivalagi I see that your wife is also watching you to make sure that you have some family time and shut your computer down to.

Oh oh ... are our wives sisters K?

> **paulus4605 said:**
> mine is even worse she just gives me my 6 week old kid and tells me to change her and bath her.

You play the game you pay for the fame.  :)

> **paulus4605 said:**
> so if I see it correctly we are all in the same boat :lolflag: ohhh well back to the guide and see if I can get my wife upset again lol 

at least I have 8 hours at work where I can play with conky otherwhise my behind is fried lol

Maybe the same boat but I'm retired and my kids have kids that can change themselves. But all our wives must be kin of some type! :lolflag:

BTW, good to see you at "The Desktop"!
Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-02-13
Hi folks...

Well, I've been playing and have a couple of questions:

[LIST=1]
[*]Is there a way to support accented characters?
[*]I notice that *forecast.template* uses <div> and *forecastheader.template* uses <table> can tables be used in *forecast.template*?
[/LIST]

**mydesktop.sh**
```
#!/bin/sh
# example use of gtk-desktop-info, for a screen resolution of 1680x1050
# will display on all desktops, and log to a single logfile
# Note:	that if used on a smaller screen bad cropping of wallpaper can take play
#		causing unwanted side effects
################################################################################

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

# use the shell plugin to display the default output of date and time
# update every second
#gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1 --width=130 --height=50 --x=75 --y=250 --windowmanager=xfce4 --plugin=shell &

# use the forecast plugin to display weather info
# The default location is mine, the config file requires updating for custom locations (see guide for info), update every 30 minutes
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=400 --height=450 --x=0 --y=200 --windowmanager=xfce4 --template=/home/bruloo/gtk-desk/forecast.template --headertemplate=/home/bruloo/gtk-desk/forecastheader.template --plugin=forecast &
```
**forecastheader.template**
```
<table border="0" cellspacing="0" cellpadding="0">
	<tr>
		<td width="32"><img src="file:///home/bruloo/Images/Captain_Canuck/SgtCanuck_256_QS.png" border="0" width="32"/></td>
		<td valign="middle" class="largedarkitalic">&nbsp; Estado del Tiempo</td>
	</tr>
</table>
```
**forecast.template**
```
<!-- Forecast Template Options used in square brackets, datatype is a must! -->
<!-- --location : location code for weather data, use the following url to determine your location code by city name: http://xoap.weather.com/search/search?where=Norwich -->
<!-- --datatype : The data type options are: DW (Day of Week), WF (Weather Font output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CC (Conditions Text), PC (Precipitation Chance), HM (Humidity), VI (Visibility), WD (Wind Direction), WA (Wind Angle - in degrees), WS (Wind Speed), WG (Wind Gusts), BF (Bearing Font), BS (Bearing font with Speed), CN (City Name), CO (Country), OB (Observatory), SR (SunRise), SS (SunSet), DL (DayLight), MP (Moon Phase), MF (Moon Font), BR (Barometer Reading), BD (Barometer Description), UI (UV Index), UT (UV Text), DP (Dew Point), LU (Last Update at weather.com), LF (Last Fetch from weather.com), WM (weather map) -->
<!-- --startday : define the starting day number, if omitted current conditions are output. Not applicable at command line when using templates. -->
<!-- --endday : define the ending day number, if omitted only starting day data is output. Not applicable at command line when using templates. -->
<!-- --spaces : Define the number of spaces between ranged output. Not applicable at command line when using templates. -->
<!-- --locale : override the system locale for language output (en=english, es=spanish, fr=french, bg=bulgarian, cs=czech, more to come) -->
<!-- --imperial : request imperial units, if omitted output is in metric. -->
<!-- --beaufort : request beaufort scale for wind speeds, if omitted output is either metric/imperial. -->
<!-- --night : switch output to night data, if omitted day output will be output. -->
<!-- --shortweekday : Shorten the day of week data type to 3 characters. -->
<!-- --hideunits : Hide units such as mph or C, degree symbols (°) are still shown. -->
<!-- --hidedegreesymbol : Hide the degree symbol used with temperature output, this is only valid if used in conjunction with --hideunits. -->
<!-- --minuteshide : Works only with LU and LF. If present, hides the date part of the LU or LF timestamp if the day of the timestamp is today. The time part is also hidden, if the timestamp is older than minutes specified in this argument. If set to 0, the time part is always shown. If set to -1, the value EXPIRY_MINUTES from the config file is used. -->

<div id="wrapper">
	<div class="contenttop" align="center">
		<span class="hugelight">[--datatype=CC]</span>
	</div>
	<div>
		<div class="contentleft">
			<div class="current">
			<img src="[--datatype=WF]" width="80"/> 
			[--datatype=HT --hideunits] / [--datatype=LT --hideunits]
			</div>      
			<div class="moon"><br>
			<img src="[--datatype=MF]" width="60"/> 
			[--datatype=MP]
			</div>      
			<div class="wind"><br>
			<img src="[--datatype=BS]" width="60"/> 
			[--datatype=WD]<br>
			[--datatype=WS]
			</div>
		</div>
		<div class="contentright"><br><br>
		  <span class="mediumlight" align="left">UV: </span>[--datatype=UI] - [--datatype=UT]<br>
		  <span class="mediumlight" align="right">Humedad: </span>[--datatype=HM]<br>
		  <span class="mediumlight" align="right">Punto de Rosco: </span>[--datatype=DP --hideunits]<br>
		  <span class="mediumlight" align="right">Presión: </span>[--datatype=BR]<br><br>

		  <span class="mediumlight" align="right">Salida del Sol: </span>[--datatype=SR]<br>
		  <span class="mediumlight" align="right">Oscuro: </span>[--datatype=SS]
		</div>
	</div>
	<div class="contenttop"><br>
		<span class="mediumlight">los próximos días</span>
	</div>
	<div class="forecast">
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=1]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=1] - [--datatype=SS --startday=1]</span>
		  <span><img src="[--datatype=WF --startday=1 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=1 --hideunits] / [--datatype=LT --startday=1 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=1]</span><br><br>
		  <span class="mediumlight">[--startday=1 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=2]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=2] - [--datatype=SS --startday=2]</span>
		  <span><img src="[--datatype=WF --startday=2 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=2 --hideunits] / [--datatype=LT --startday=2 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=2]</span><br><br>
		  <span class="mediumlight">[--startday=2 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=3]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=3] - [--datatype=SS --startday=3]</span>
		  <span><img src="[--datatype=WF --startday=3 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=3 --hideunits] / [--datatype=LT --startday=3 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=3]</span><br><br>
		  <span class="mediumlight">[--startday=3 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=4]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=4] - [--datatype=SS --startday=4]</span>
		  <span><img src="[--datatype=WF --startday=4 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=4 --hideunits] / [--datatype=LT --startday=4 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=4]</span><br><br>
		  <span class="mediumlight">[--startday=4 --datatype=CC]</span>
		</div>
	</div>
	<div class="contentbottom" align="right"><br>
		<span class="smalllight">Fetched: </span><span class="smalldark">[--datatype=LF]</span>
	</div>
</div>
```

OH, and I took the "map" out because weather.com thinks Buenos Aires, Argentina is Caracas, Venezuela and the "Observatory" in Bs As is the same place as the Airport even though they are far enough apart that the temps are usually 3 - 5° different and wind speeds vary by 5 - 10k/hr and it could be raining at the airport and sunny here. Try to "contact" them and I get; "Thank you for contacting us but we can't respond to all the emails we get, if you are interested in receiving daily update in your email ... " Anda a la mie" - oh, wait, I can't say there here! Wednessday, I meant to say Wednesday! :lolflag:

And all that does this - look down.

Poor accented characters :cry:
Have a nice day
Bruce

---

### Post by Bruce M. on 2009-02-13
> **paulus4605 said:**
> hmmm I found the coordinates without a problem just trying to figure out where to put them, if I change the coordinats to this ones 36,454 I still get into the terminal moved to 0,24 :confused::confused::confused:  how do I get rid of this 0,24 ?


I also noticed that you have a complete weather map underneeth the 5 day weather prediction is that normal?

Paul

Paul,

The files you are looking for are in **/usr/share/gtk-desktop-info** I copied all of those to **~/gtk-desk/** and as you see in my setup (earlier post) I call them via my startup script: **mydesktop.sh**.  :)

That way I don't edit originals. :)
I always have a place to go back to if I **[COLOR="DarkRed"]"Oops!"[/COLOR]**

Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-02-13
> **paulus4605 said:**
> hmmm I found the coordinates without a problem just trying to figure out where to put them, if I change the coordinats to this ones 36,454 I still get into the terminal moved to 0,24 :confused::confused::confused:  how do I get rid of this 0,24 ?

Don't know why, I just ran this:

```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=3 --width=400 --height=300 **--x=2020 --y=25** --plugin=rhythmbox --css=/home/mark/.config/gtk-desktop-info/plugin_rhythmbox_green.css --template=/home/mark/.config/gtk-desktop-info/rhythmbox.template &
```

Then moved it about here and then and got this:
```

Window moved to 1750,199
Window moved to 1869,79
Window moved to 1766,169
Window moved to 2004,195
Window moved to 1804,85
```


> **paulus4605 said:**
> I also noticed that you have a complete weather map underneeth the 5 day weather prediction is that normal?

Paul

Yep, a satellite map at the bottom...you can scroll with the output, just hover the mouse pointer over the top and use the scroll wheel...

see the before.jpg and after.jpg for a scroll down with the mouse wheel...

---

### Post by kaivalagi on 2009-02-13
> **Bruce M. said:**
> 
Poor accented characters :cry:


:cry: indeed! accented characters have got to be the most awkward thing to support in python and html

I am not sure I'll get time to look into the issue this weekend, 6 nations rugby is on (no pumas sorry), tomorrow is my sisters birthday so I have to please two women, and I want to try and unwind after a rather stressful working week.

If there are any budding pythoners out there that want to try and produce better accented character support for the app then here is what gets html characters from unicode right now:

[PHP]#import needed: from htmlentitydefs import name2codepoint, codepoint2name

    def getHTMLText(self,text):
        try:
            htmlentities = []               
            for char in text:
                if ord(char) < 128:
                    htmlentities.append(char)
                else:
                    htmlentities.append('&%s;' % codepoint2name[ord(char)])
            html = "".join(htmlentities)
            
            html = html.replace("\n","<br>\n") # switch out new line for html breaks
            return html            
        except:
            return text[/PHP]

---

### Post by Bruce M. on 2009-02-13
> **kaivalagi said:**
> :cry: indeed! accented characters have got to be the most awkward thing to support in python and html

I am not sure I'll get time to look into the issue this weekend, 6 nations rugby is on (no pumas sorry), tomorrow is my sisters birthday so I have to please two women, and I want to try and unwind after a rather stressful working week.

> **kaivalagi said:**
> If there are any budding pythoners out there

Right there is where I stopped reading. :lolflag:

When it comes to python, I think: **snake - [SIZE="5"]BIG[/SIZE] snakes!** :lolflag:

---

### Post by Bruce M. on 2009-02-13
> **kaivalagi said:**
> :cry: indeed! accented characters have got to be the most awkward thing to support in python and html

Never mind, I'll change the words for now, grab your family and have a GREAT weekend!

> **kaivalagi said:**
> If there are any budding pythoners out there

Right there is where I stopped reading, you are obviously NOT talking to me!

When I hear python I think: **Snakes - [SIZE="5"]BIG[/SIZE] snakes!**

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-02-13
[CENTER]:guitar: **[COLOR="DarkRed"][SIZE="5"]Papa's got a brand new screen![/SIZE][/COLOR]** :guitar:

[[IMG]http://img7.imageshack.us/img7/2179/13feb09ix8.th.gif[/IMG]](http://img7.imageshack.us/my.php?image=13feb09ix8.gif)[/CENTER]

Take a look at the top left K!

**mydesktop.sh** - Note: *test.template* and *--noheader* I've put it in the test.template:
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=750 --height=240 --x=0 --y=750 --windowmanager=xfce4 --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```
and my: **test.template**
```
<div id="wrapper">
<table cellpadding="0" cellspacing="0" border="0">
<tr>
<td><table cellspacing="0" cellpadding="0" border="0">
	<tr>
		<td><img src="file:///home/bruloo/Images/Captain_Canuck/SgtCanuck_256_QS.png" border="0" width="50"/></td>
		<td valign="middle" class="largedarkitalic">&nbsp; Estado del Tiempo</td>
	</tr>
</table></td>
<td rowspan="2">	<div class="contenttop"><br>
		<span class="mediumlight">los próximos días</span>
	</div>
	<div class="forecast">
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=1]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=1] - [--datatype=SS --startday=1]</span>
		  <span><img src="[--datatype=WF --startday=1 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=1 --hideunits] / [--datatype=LT --startday=1 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=1]</span><br><br>
		  <span class="mediumlight">[--startday=1 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=2]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=2] - [--datatype=SS --startday=2]</span>
		  <span><img src="[--datatype=WF --startday=2 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=2 --hideunits] / [--datatype=LT --startday=2 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=2]</span><br><br>
		  <span class="mediumlight">[--startday=2 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=3]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=3] - [--datatype=SS --startday=3]</span>
		  <span><img src="[--datatype=WF --startday=3 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=3 --hideunits] / [--datatype=LT --startday=3 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=3]</span><br><br>
		  <span class="mediumlight">[--startday=3 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=4]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=4] - [--datatype=SS --startday=4]</span>
		  <span><img src="[--datatype=WF --startday=4 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=4 --hideunits] / [--datatype=LT --startday=4 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=4]</span><br><br>
		  <span class="mediumlight">[--startday=4 --datatype=CC]</span>
		</div>
	</div>
	<div class="contentbottom" align="right"><br>
		<span class="smalllight">Fetched: </span><span class="smalldark">[--datatype=LF]</span>
	</div></td>
</tr>
<tr>
<td valign="top">	<div class="contenttop" align="center">
		<span class="hugelight">[--datatype=CC]</span>
	</div>
	<div>
		<div class="contentleft">
			<div class="current">
			<img src="[--datatype=WF]" width="80"/> 
			[--datatype=HT --hideunits] / [--datatype=LT --hideunits]
			</div>      
			<div class="moon"><br>
			<img src="[--datatype=MF]" width="60"/> 
			[--datatype=MP]
			</div>      
			<div class="wind"><br>
			<img src="[--datatype=BS]" width="60"/> 
			[--datatype=WD]<br>
			[--datatype=WS]
			</div>
		</div>
		<div class="contentright"><br><br>
		  <span class="mediumlight" align="left">UV: </span>[--datatype=UI] - [--datatype=UT]<br>
		  <span class="mediumlight" align="right">Humedad: </span>[--datatype=HM]<br>
		  <span class="mediumlight" align="right">Punto de Rosco: </span>[--datatype=DP --hideunits]<br>
		  <span class="mediumlight" align="right">Presión: </span>[--datatype=BR]<br><br>

		  <span class="mediumlight" align="right">Salida del Sol: </span>[--datatype=SR]<br>
		  <span class="mediumlight" align="right">Oscuro: </span>[--datatype=SS]
		</div>
	</div></td>
</tr>
</table>
</div>
```
How sweet it is! :KS

Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-02-13
Bruce 

you did a great job as allways

Paul

---

### Post by Bruce M. on 2009-02-13
> **paulus4605 said:**
> Bruce 

you did a great job as allways

Paul

Thanks, but it's not finished yet. I want to make todays "temps" bigger and move the Moon and compass. Then I want to add some stuff to the 4 days as well.

It's a work in progress.

I'd like to see more setups. Foe now mine is only using the forcast, there are other options as well, but I'll get the weather working the way I like and then play with the other stuff.

Have a nice day.
Bruce

---

### Post by useResa on 2009-02-13
I justed learned about this app from Bruce and have not done any tweaking (yet).
Just like to inform that it also runs nicely on Xubuntu Jaunty. If I am correct this has not yet been posted and/or confirmed.

Attached a screenshot of the app running in Xubuntu Jaunty that I have installed on an old PIII (933 MHz) with 256 Mb memory. Amazing how little resources it uses.

Compliments to the dev.

---

### Post by Bruce M. on 2009-02-13
> **useResa said:**
> I justed learned about this app from Bruce and have not done any tweaking (yet).
Just like to inform that it also runs nicely on Xubuntu Jaunty. If I am correct this has not yet been posted and/or confirmed.

Attached a screenshot of the app running in Xubuntu Jaunty that I have installed on an old PIII (933 MHz) with 256 Mb memory. Amazing how little resources it uses.

Compliments to the dev.

Hi useResa, Fancy meeting you in a place like this.

WoW! Nice! Running on Xubu 9.04 - **YES! YES! YES!**
Time to tweak it.  :)

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-13
Well I did give it a go aswell 
however I am not that happy with the outlining but as Bruce is stating its a work in progress 

but here is my first atempt
hope you like it 

note: I didn't have time to adapt the translation files but that will be corrected later on

---

### Post by kaivalagi on 2009-02-13
> **paulus4605 said:**
> Well I did give it a go aswell 
however I am not that happy with the outlining but as Bruce is stating its a work in progress 

but here is my first atempt
hope you like it 

note: I didn't have time to adapt the translation files but that will be corrected later on

Are you running Compiz Paul? I am wondering if the outlining is in relation to shadows settings in the windows decorations...

If it is you can omit this app from the decoration using it's class name

[COLOR="Navy"]Edit:

Just realised there is already a mention of all of this in the pdf guide. You can open the guide by running:

```
gtk-desktop-info.guide
```

Then look for the "Gotchas" section towards the end...[/COLOR]

---

### Post by Bruce M. on 2009-02-14
> **kaivalagi said:**
> :cry: indeed! accented characters have got to be the most awkward thing to support in python and html


Forget I mentioned that **K**. The accented characters are working well in your coding.  :)

I see Wednesday as Miércoles :)

It was where I changed "next few days" to "los próximos días" - **[COLOR="DarkRed"]DUH![/COLOR]**

So I did what I "should have done" (it's been a LONG time for me and HTML) and changed it using the HTML Number:

los pr&**+**#**+**243**+**;ximos d&**+**#**+**237**+**;as

Oh that was fun, the forum translated it correctly as los próximos días, remove the + signs and you get the picture.

Sorry to have created an - **OH NO!**

Chimo
Bruce

---

### Post by useResa on 2009-02-14
> **Bruce M. said:**
> Hi useResa, Fancy meeting you in a place like this.
Well ... have been around a while, although been laying low a bit lately :)

> **Bruce M. said:**
> Time to tweak it.  :)I know. First I need to read the guide though. But I'll get to it and let you know what I achieved.

---

### Post by paulus4605 on 2009-02-14
I am back with a new version of my forecast

hope you like it 

this is the script I use 
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=740 --height=350 --x=0 --y=750 --template=/usr/share/gtk-desktop-info/templates/test.template --noheader --plugin=forecast &
```

and this is my template
```
<div id="wrapper">
<TABLE BORDER=0 cellspacing="0">
<TR>
<TD rowspan=2 valign="middle" class="largedarkitalic">&nbsp; Weersvoorspelling voor [--datatype=DW --startday=0]:<br>
<div class="contenttop" align="center"><pre>
		<span class="hugelight">[--datatype=CT]</span><br></div>
		<span class="mediumlight" align="left">Maximum Temp</span><span class="mediumlight" align="right">: [--datatype=HT]</span><span class="mediumlight" align="right">&nbsp;&nbsp;&nbsp;Minimum Temp</span><span class="mediumlight" align="right">: [--datatype=LT]</span><br>	
		<span class="mediumlight" align="left">Zonsopgang	:[--datatype=SR]</span><span class="mediumlight" align="right">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Zonsondergang: [--datatype=SS]</span><br>
		<span class="mediumlight" align="left">Uren Daglicht: [--datatype=DL]</span><br></pre>
<div class="contentleft"><pre>
			<div class="current" align="left">
	<img src="[--datatype=WF]" width="80"/>       <img src="[--datatype=MF]" width="60"/>
			[--datatype=MP]
			</div></div>
</div>
</TD>
<TD>
<div class="contenttop">
<div class="wind"><img src="[--datatype=BS]" width="60"/></div><br>
<span class="mediumlight" align="left">Wind:&nbsp;[--datatype=WS]/[--datatype=WD]</span><br>
<span class="mediumlight" align="right">UV&nbsp;&nbsp;:[--datatype=UI] - [--datatype=UT]</span><br>
<span class="mediumlight" align="right">Vochtigheid:&nbsp;[--datatype=HM]</span><br>
<span class="mediumlight" align="right">Dauwpunt:[--datatype=DP --hideunits] </span><br>
<span class="mediumlight" align="right">Barometer:[--datatype=BR]</span><br>
<span class="mediumdarkitalic" align="left">weersvoorspelling voor de volgende dagen:</span>
</TD>
</TR>
<TR>
<TD>
<div class="forecast">
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=1]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=1] - [--datatype=SS --startday=1]</span>
		  <span><img src="[--datatype=WF --startday=1 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=1 --hideunits] / [--datatype=LT --startday=1 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=1]</span><br><br>
		  <span class="mediumlight">[--startday=1 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=2]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=2] - [--datatype=SS --startday=2]</span>
		  <span><img src="[--datatype=WF --startday=2 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=2 --hideunits] / [--datatype=LT --startday=2 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=2]</span><br><br>
		  <span class="mediumlight">[--startday=2 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=3]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=3] - [--datatype=SS --startday=3]</span>
		  <span><img src="[--datatype=WF --startday=3 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=3 --hideunits] / [--datatype=LT --startday=3 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=3]</span><br><br>
		  <span class="mediumlight">[--startday=3 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=4]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=4] - [--datatype=SS --startday=4]</span>
		  <span><img src="[--datatype=WF --startday=4 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=4 --hideunits] / [--datatype=LT --startday=4 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=4]</span><br><br>
		  <span class="mediumlight">[--startday=4 --datatype=CC]</span>
		</div>
	</div>
			
		</div>
</TD>
</TABLE> 
</div>
```


only thing that I find a bit anoying the openspace between the right and the left side 
and for some reason I don't have my compass arrow... this also puzzles me 
if someone has an Idea to solve this please let me know 

thanks Paul

---

### Post by kaivalagi on 2009-02-14
> **paulus4605 said:**
> 
only thing that I find a bit anoying the openspace between the right and the left side 
if someone has an Idea to solve this please let me know 

thanks Paul

You'll need to look into the css option too, it will be the css settings that are causing the spacing. The css setting was geared up for the original template.

The css that is being used for your current settings is /usr/share/gtk-desktop-info/style/plugin_forecast_default.css

If you run the script in the terminal using the --verbose option it will output all of the html into the terminal window, so you get a good idea of the complete html output including the head of the document. Something you can copy and paste into a text doc, and open in a browser to play about with ;)

---

### Post by paulus4605 on 2009-02-14
kaivalagi
ok I will have a look at that when the wife lets me lol 

what do you think of my second attempt?

Paul

---

### Post by paulus4605 on 2009-02-14
kaivalagi,

I could be wrong but can it be that there isn't a translation for sunny in the dutch translation file?

if it isn't there the translation for sunny => Zonnig

I also found an error on the windspeed
I find the windspeed Rustig not the correct speed I rather see there 0 kpu (in dutch)
also the winddirection with status CALM doesn't seem to be correct to me 

Paul

---

### Post by kaivalagi on 2009-02-15
> **paulus4605 said:**
> kaivalagi,

I could be wrong but can it be that there isn't a translation for sunny in the dutch translation file?

if it isn't there the translation for sunny => Zonnig

I also found an error on the windspeed
I find the windspeed Rustig not the correct speed I rather see there 0 kpu (in dutch)
also the winddirection with status CALM doesn't seem to be correct to me 

Paul

There is an explanation for Sunny not being translated.

With weather.com there are 2 bits of data that the script can use to generate text output _like_ "Sunny". Straight text and condition codes. This means we have these two options:

[LIST=1]
[*]--datatype=CT  this is text straight from weather.com in the xml, it varies and is not a stable format. This is not translated.
[*]--datatype=CC  this is text set in the script which relates to the condition codes in the xml, therefore it is sourced from a known list of text. This is translated.
[/LIST]

The release of THIS script just gone has altered the default template to use CC rather than CT so language translations are thorough.

I am not going to attempt in getting all the text from the raw data into translation files that weather.com / met office / whomever dream up ....instead, if this proves much of a problem I shall just remove the CT option altogether.

Hope that makes sense.

P.S If the data is presented right but doesn't match the weather, that's not my fault ;) weather.com......
I had a look at your second attempt and it's okay, you've slotted in some new data nicely. Just need the css stuff to tighten up all the content a little, may be it's better to switch to tables in this scenario?...

---

### Post by paulus4605 on 2009-02-15
it makes sence,

and yes I use tables but I can't seem to get the left side of the screen tighten up for some reason perhaps you see a solution 
this is my template
```
<div id="wrapper">
<TABLE BORDER=0 cellspacing="0" cellpadding="0">
<TR>
<TD rowspan=2 valign="left" class="largedarkitalic">&nbsp; Weersvoorspelling voor [--datatype=DW --startday=0]:<br>
<div class="contenttop" align="left"><pre>
	<span class="hugelight">[--datatype=CT]</span><br></div>
		<span class="mediumlight" align="left">Maximum Temp</span><span class="mediumlight" align="right">: [--datatype=HT]</span><span class="mediumlight" align="right">&nbsp;&nbsp;&nbsp;Minimum Temp</span><span class="mediumlight" align="right">: [--datatype=LT]</span><br>	
		<span class="mediumlight" align="left">Zonsopgang	:[--datatype=SR]</span><span class="mediumlight" align="right">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Zonsondergang: [--datatype=SS]</span><br>
		<span class="mediumlight" align="left">Uren Daglicht: [--datatype=DL]</span><br></pre>
<div class="contentleft"><pre>
			<div class="current" align="left">
	<img src="[--datatype=WF]" width="80"/>       <img src="[--datatype=MF]" width="60"/>
			[--datatype=MP]
			</div></div>
</div>
</TD>
<TD>
<div class="contenttop">
<div class="wind"><img src="[--datatype=BS]" width="60"/></div><br>
<span class="mediumlight" align="left">Wind:&nbsp;[--datatype=WS]/[--datatype=WD]</span><br>
<span class="mediumlight" align="right">UV&nbsp;&nbsp;:[--datatype=UI] - [--datatype=UT]</span><br>
<span class="mediumlight" align="right">Vochtigheid:&nbsp;[--datatype=HM]</span><br>
<span class="mediumlight" align="right">Dauwpunt:[--datatype=DP --hideunits] </span><br>
<span class="mediumlight" align="right">Barometer:[--datatype=BR]</span><br>
<span class="mediumdarkitalic" align="left">weersvoorspelling voor de volgende dagen:</span>
</TD>
</TR>
<TR>
<TD>
<div class="forecast">
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=1 --shortweekday]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=1] - [--datatype=SS --startday=1]</span>
		  <span><img src="[--datatype=WF --startday=1 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=1 --hideunits] / [--datatype=LT --startday=1 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=1]</span><br><br>
		  <span class="mediumlight">[--startday=1 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=2 --shortweekday]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=2] - [--datatype=SS --startday=2]</span>
		  <span><img src="[--datatype=WF --startday=2 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=2 --hideunits] / [--datatype=LT --startday=2 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=2]</span><br><br>
		  <span class="mediumlight">[--startday=2 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=3 --shortweekday]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=3] - [--datatype=SS --startday=3]</span>
		  <span><img src="[--datatype=WF --startday=3 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=3 --hideunits] / [--datatype=LT --startday=3 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=3]</span><br><br>
		  <span class="mediumlight">[--startday=3 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=4 --shortweekday]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=4] - [--datatype=SS --startday=4]</span>
		  <span><img src="[--datatype=WF --startday=4 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=4 --hideunits] / [--datatype=LT --startday=4 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=4]</span><br><br>
		  <span class="mediumlight">[--startday=4 --datatype=CC]</span>
		</div>
	</div>
			
		</div>
</TD>
</TABLE> 
</div>
```


the general Idea that I had was a large left side window and the same side on the right but split in top and bottom, the last part is fitting like a charm. I checked this out by changing the value from the table border from 0 to 1.

its just the left side that is bugging me 


Paul

---

### Post by kaivalagi on 2009-02-15
> **paulus4605 said:**
> 

its just the left side that is bugging me 


Paul

Either remove the class= in all the tags or edit the css and repoint to a new version of it using the --css option

---

### Post by paulus4605 on 2009-02-15
made some modifications and this is my final version 

let me know what you think

---

### Post by useResa on 2009-02-15
> **paulus4605 said:**
> let me know what you thinkI am impressed!
I just started to try and get it looking the way I want. I am mostly struggling with getting everything in Dutch. Seem you have come a long way, well at least further than me :P

---

### Post by paulus4605 on 2009-02-15
> **useResa said:**
> I am impressed!
I just started to try and get it looking the way I want. I am mostly struggling with getting everything in Dutch. Seem you have come a long way, well at least further than me :P

well Dutch wasn't the problem since I was born there.
the problem I had was getting everything better organised and not like my very first attempt where there was a huge space between the left and the right column

Paul

---

### Post by useResa on 2009-02-15
> **paulus4605 said:**
> well Dutch wasn't the problem since I was born there.
:lolflag: 
I was also born in the Netherlands, so it is not the language itself that is my issue.
I currently still have a mixture of Dutch and English (see screenshot). 
That is what I meant when indicating I was having problems with Dutch

---

### Post by paulus4605 on 2009-02-15
> **useResa said:**
> :lolflag: 

I currently still have a mixture of Dutch and English (see screenshot). 
That is what I meant when indicating I was having problems with Dutch

Did you modify the config file and adapted the locale? if you have nothing mentioned there it will be in english by default

change this in the /usr/share/gtk-desktop-info/plugin_forecast.config

then you are set to go 

by the way you did a good job with the forecast 

Paul

---

### Post by Bruce M. on 2009-02-15
> **paulus4605 said:**
> made some modifications and this is my final version 

let me know what you think

[SIZE="7"][COLOR="DarkRed"]WOW![/COLOR][/SIZE]
Can I get your code, template whatever?

---

### Post by paulus4605 on 2009-02-15
Bruce 
sure you can 

you will find everything in attachment 

this is the commandline for the forecast 
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=740 --height=350 --x=0 --y=750 --template=/usr/share/gtk-desktop-info/templates/test.template --noheader --plugin=forecast &

```

Please note that I have been messing arround with the css file but didn't clean it up so you will find some abnormal things.

glad you like it 

Paul

---

### Post by Bruce M. on 2009-02-15
> **paulus4605 said:**
> well Dutch wasn't the problem since I was born there.

Paul

> **useResa said:**
> :lolflag: 
I was also born in the Netherlands, so it is not the language itself that is my issue.

Paul, meet my friend Resa, Resa, my friend Paul.
Now play nice guys.  :)

Probably neighbours and don't even know it. I mean on a map the Netherlands is smaller than my baby finger fingernail, now how many people could possibly live there!

{ducking, running, dodging}
HEY, Those are real eggs, no fair, two against one!!! :lolflag:

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-15
> **Bruce M. said:**
> 

Probably neighbours and don't even know it. I mean on a map the Netherlands is smaller than my baby finger fingernail, now how many people could possibly live there!


Well if I am not mistaken there would be around 16.5  million people in the Netherlands and since I live in Belgium where about 10 million people are situated. It could however that we neighbours but that chance would be very slim :-).

by the way I rather eat eggs then throw them arround:lolflag::lolflag:

Paul

---

### Post by paulus4605 on 2009-02-15
kaivalagi:
I have been thinking, I know with just 1 braincell its very hard :P 

would it be possible to do a conditional format on the positive temperatures?
for example if the temperature is between 0 and +10 then the colour would be blue between 10 and 20 it would be green and between 20 and 30 it would be orange and above 30 it would be red?

Paul

---

### Post by useResa on 2009-02-15
> **paulus4605 said:**
> Did you modify the config file and adapted the locale? if you have nothing mentioned there it will be in english by default
I have altered the line into
```
LOCALE = NL
```
which I assumed to be the code for the translation into Dutch.
Or would it be better to change it into
```
LOCALE = BE
```
:)

---

### Post by paulus4605 on 2009-02-15
[QUOTE=useResa]I have altered the line into
```
LOCALE = NL
```


just change it into nl 


Paul

---

### Post by useResa on 2009-02-15
> **paulus4605 said:**
> [quote=useResa]I have altered the line into
```
LOCALE = NL
```
just change it into nl 
[/quote]Still gives me English.
Do I need to have a language pack installed or so?
What I have installed is:

[LIST]
[*]language-pack-nl
[*]language-pack-nl-base
[*]myspell-nl
[/LIST]

---

### Post by Bruce M. on 2009-02-15
> **paulus4605 said:**
> Well if I am not mistaken there would be around 16.5  million people in the Netherlands and since I live in Belgium where about 10 million people are situated. It could however that we neighbours but that chance would be very slim :-).

by the way I rather eat eggs then throw them arround:lolflag::lolflag:

Paul

Shhhhhhhhh, I knew all that, I've been to the Netherlands and Belgium and I know where both of you are.

I was just having a bit of fun. :lolflag:

Me too, but at my age I have to watch my cholesterol, I can't eat as many as I'd like.  :(

Have a great day.
Bruce

---

### Post by Bruce M. on 2009-02-15
> **useResa said:**
> Still gives me English.
Do I need to have a language pack installed or so?
What I have installed is:

[LIST]
[*]language-pack-nl
[*]language-pack-nl-base
[*]myspell-nl
[/LIST]

That should be:```
LOCALE = nl
```(in lowercase)

And no, you don't need a language pack installed. I have yet to install the Spanish Language packs here (must do that soon), the app will get the Dutch language it needs from:
```
/usr/share/gtk-desktop-info/locale/nl/LC_MESSAGES/plugin_forecast.po
```

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-15
> **useResa said:**
> Still gives me English.
Do I need to have a language pack installed or so?
What I have installed is:

[LIST]
[*]language-pack-nl
[*]language-pack-nl-base
[*]myspell-nl
[/LIST]

no need to do that. did you put nl in caps? if so try in normal print.

did you do a refresh or did you closed weather down and started it up again?

when I was messing around with the css I had to close weather down in order to see the modifications.

if it still doesn't work I would ask kaivalagi  hes the master of the desktop universe :-)

Paul

---

### Post by Bruce M. on 2009-02-15
> **paulus4605 said:**
> Bruce 
sure you can 

you will find everything in attachment 

this is the commandline for the forecast 
```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=740 --height=350 --x=0 --y=750 --template=/usr/share/gtk-desktop-info/templates/test.template --noheader --plugin=forecast &

```

Please note that I have been messing arround with the css file but didn't clean it up so you will find some abnormal things.

glad you like it 

Paul

It's great, yours that is!

I see you are using SPAN & DIV ... I don't understand those and stuck to my 12 year old knowledge of HTML; TABLES because I wanted to modify it like - *Yesterday!*.

I'm a patient man, as long as patience is NOW! :lolflag:

I'll learn DIV and SPAN from yours.  :)

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-15
Bruce
patience my friend is a beautiful thing I have to admit that to you 
but I have to agree with you as long as I get what I want yesterday like you I am happy.

Well I am a self made man on span and div and I was just experimenting with your version modified it in about 3 versions to get what I wanted.
so in a way thats all the knowledge I have on span and div lol 


Paul

---

### Post by useResa on 2009-02-15
> **Bruce M. said:**
> That should be:```
LOCALE = nl
```(in lowercase)

And no, you don't need a language pack installed. I have yet to install the Spanish Language packs here (must do that soon), the app will get the Dutch language it needs from:
```
/usr/share/gtk-desktop-info/locale/nl/LC_MESSAGES/plugin_forecast.po
```
I have checked and this file does exist.
And I do lowercase now.

> **paulus4605 said:**
> no need to do that. did you put nl in caps? if so try in normal print.
did you do a refresh or did you closed weather down and started it up again?

As indicated above, I used lowercase now.
I use a script to restart gtk-desktop-info.
Just to be sure I have logged out and logged back in again.

Still I have the same issue. The screenshot shows -- AFAIK -- the important settings in the config file plus the result (still mixed English and Dutch) in my latest setup.

---

### Post by Bruce M. on 2009-02-15
> **useResa said:**
> I have checked and this file does exist.

When you got the "app", did you use Method #1 in the first post?
I know you're testing on J.J. but if you got the latest from I.I. and it installed those really should exist. See attached.

> **useResa said:**
> And I do lowercase now.

OK, that's a good thing.

> **useResa said:**
> As indicated above, I used lowercase now.
I use a script to restart gtk-desktop-info.
Just to be sure I have logged out and logged back in again.

Still I have the same issue. The screenshot shows -- AFAIK -- the important settings in the config file plus the result (still mixed English and Dutch) in my latest setup.

The Dutch comes from the template I believe you got from Paul, or the Dutch text you have put in there. The "output" is in English.

I'd reinstall the app and see if you get the language files as seen in the image attached.

Chimo!
Bruce

---

### Post by useResa on 2009-02-15
> **Bruce M. said:**
> I know you're testing on J.J. but if you got the latest from I.I. and it installed those really should exist. See attached.

> **Bruce M. said:**
> I'd reinstall the app and see if you get the language files as seen in the image attached.

I think you misread my previous post
> **useResa said:**
> I have checked and this file **does** exist.
Meaning: Files as indicated **are** available  :P

However, maybe it does have to do with the fact that I an running it on J.J.
Maybe this can be confirmed?

---

### Post by Bruce M. on 2009-02-15
> **paulus4605 said:**
> Bruce
patience my friend is a beautiful thing I have to admit that to you 
but I have to agree with you as long as I get what I want yesterday like you I am happy.

God grant me patience, and I mean right NOW!

Seriously: I really did want to play with it, it's a way to learn, and I simply applied what I do know, with an idea that if I put this stuff inside a table, it just might work, and ... SURPRISE! - it did. Colour me happy!

> **paulus4605 said:**
> Well I am a self made man on span and div and I was just experimenting with your version modified it in about 3 versions to get what I wanted.
so in a way thats all the knowledge I have on span and div lol 

Paul

**Hahahahahahahahahaha!** We is the same! (Don't tell my grammar teacher I said that.)
Oh I see, and all I did was trap those DIV and SPAN things inside a TABLE to see if they would work.

Then in my next test I did away with them entirely and just used "class=" in the <td> tags. That works too, which is a whole bunch easier on my one neuron that's at home. I have three but one got lost and the other one's out looking for him. :lolflag:

I'm beginning to play with different colours now in my CSS file.  :)

Chimo!
Bruce

---

### Post by useResa on 2009-02-15
> **Bruce M. said:**
> I'm beginning to play with different colours now in my CSS file. I am currently not on my Xubuntu box, but IIRC there were already different css files with different colors readily available in /usr/share/gtk-desktop-info/style. AFAIK the default version is used.

---

### Post by Bruce M. on 2009-02-15
> **useResa said:**
> I think you misread my previous post

Meaning: Files as indicated **are** available  :P

However, maybe it does have to do with the fact that I an running it on J.J.
Maybe this can be confirmed?

Oops!  You're right I did misread that.

Are you using any "custom" calls in getting the app to run?

For example I'm now using two custom calls:

```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=700 --height=240 --x=0 --y=755 --windowmanager=xfce4 --*css=/home/bruloo/gtk-desk/my_forecast.css* --*template=/home/bruloo/gtk-desk/test.template* --noheader --**plugin=forecast** &
```
I think that last one is a MUST.

Other then that maybe it is a J.J. Gotcha! for the moment.  :(

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-02-15
> **useResa said:**
> I am currently not on my Xubuntu box, but IIRC there were already different css files with different colors readily available in /usr/share/gtk-desktop-info/style. AFAIK the default version is used.

Yea, but each has only two colours in them, I want 3 or 4, or mauby more, colours in my display, not just two.  :)

CHIMO!
Bruce

---

### Post by xeddog on 2009-02-15
Hey guys,

This may not be the right thread to ask these questions, but you seem to know quite a bit about the data that comes from weather.com.  I have been playing around with conky for the last few days (I'm still a linux newbie), and I see that the same applies here.

When looking at "conkyForecast -h",  it says that for --datatype HT the value is (Forecast:High Temp,Current:Current Temp), and for datatype LT it says  (Forecast:Low Temp,Current:Feels Like Temp).  My question is, how would you get all 4 temps in one display?  

For example:

High/Low:
Current:
Feels Like:

I think I can handle the coding in my .conkyrc, but I don't know how to differentiate between a request for a forecast and a request for current conditions.

 
Second question - The biggest problem I have right now is that I cannot find a location code that is close enough.  When I go to weather.com and search for the location codes, If I search on my city (Oakley, CA) I get a code of USCA0792.  When I use this code in conky the "station" is identified as Livermore which is about 30 miles away to the south(ish).  If I use the adjoining city of Antioch, CA (USCA0034), the station is identified as Concord which is about 30 miles away to the West.  And if I use the location code for Stockton, CA (USCA1100) that one does identify itself correctly as Stockton, but it is 35 miles East.  The bottom line is that all of these other cities have their own micro climates and none of them match Oakley very well.  I have been using the one that has the closest match to my weather but still . . .

Anyway, do any of you know of another weather service that has all of this information like maybe the National Weather Service, or even Yahoo weather (both of which have localized weather for Oakley), and how to use them??

TIA,

xeddog

---

### Post by kaivalagi on 2009-02-15
> **xeddog said:**
> Hey guys,

This may not be the right thread to ask these questions, but you seem to know quite a bit about the data that comes from weather.com.  I have been playing around with conky for the last few days (I'm still a linux newbie), and I see that the same applies here.

Welcome xeddog,

Firstly, if you haven't already, take a look at the conkyForecast thread, you can find it through the "My Conky Scripts" link in my sig 

> **xeddog said:**
> When looking at "conkyForecast -h",  it says that for --datatype HT the value is (Forecast:High Temp,Current:Current Temp), and for datatype LT it says  (Forecast:Low Temp,Current:Feels Like Temp).  My question is, how would you get all 4 temps in one display?  

For example:

High/Low:
Current:
Feels Like:

I think I can handle the coding in my .conkyrc, but I don't know how to differentiate between a request for a forecast and a request for current conditions.

As "current" and "feels like" temps are only available for the current day, if you require both high/low and these for the current day the following will do it:

Current:    conkyForecast --datatype=HT --location=CODE
Feels Like: conkyForecast --datatype=LT --location=CODE
High:       conkyForecast --startday=0 --datatype=HT --location=CODE
Low:        conkyForecast --startday=0 --datatype=LT --location=CODE

> **xeddog said:**
> Anyway, do any of you know of another weather service that has all of this information like maybe the National Weather Service, or even Yahoo weather (both of which have localized weather for Oakley), and how to use them??

I am afraid if you have an issue with location code there's nothing much I can do. Bruce has had similar issues...

The NOAA do US only weather data which may be more accurate for you. There is a python-pymetar library in the repos for accessing this data but it's a bit more raw to use than this script...and wont provide fonts etc for icon output.

Be sure to raise any more question in the conkyForecast thread, you will get better support there as their are more subscribers using the script there.

Hope that helps

[COLOR="Blue"]Edit: corrected[/COLOR]

---

### Post by paulus4605 on 2009-02-16
> **Bruce M. said:**
> Yea, but each has only two colours in them, I want 3 or 4, or mauby more, colours in my display, not just two.  :)

CHIMO!
Bruce

Bruce we are alike :lolflag:  we are both colourfull men :lolflag::lolflag:  waiting patiently to the final version of bruce.


BRUCE BRUCE is it finished yet [COLOR="Blue"]**hahahahahahahahaha**[/COLOR]

---

### Post by Bruce M. on 2009-02-16
> **paulus4605 said:**
> BRUCE BRUCE is it finished yet [COLOR="Blue"]**hahahahahahahahaha**[/COLOR]

*No no no, not yet...* {tap tap tapping of keyboard} 

{mumbling to self} *close though close, oh so close ...*

{tap tap tapping of keyboard} *yes, yes, I' know I've been saying that for years ....*

{tap tap tapping of keyboard} *but this time I mean it! 1, 2 days at the most , well maybe a week!*

Seriously: ***finished?*** - my conky still isn't "finished",  I doubt this app will be any different. [My first question]("http://ubuntuforums.org/showthread.php?t=281865&page=116") was asking if something was conky - it was a desklet, that's how much I knew. :lolflag:

Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-02-16
> **Bruce M. said:**
> *No no no, not yet...* {tap tap tapping of keyboard} 

{mumbling to self} *close though close, oh so close ...*

{tap tap tapping of keyboard} *yes, yes, I' know I've been saying that for years ....*

{tap tap tapping of keyboard} *but this time I mean it! 1, 2 days at the most , well maybe a week!*
.
Bruce

Bruce STOP!!!  I see smoke signals coming out of your keyboard with the words *don't hit me so hard I get headaches from all these tapping fingers*:lolflag: 

kaivalagi: did you see the remark about the conditional formatting?


Paul

---

### Post by kaivalagi on 2009-02-16
> **paulus4605 said:**
> 
kaivalagi: did you see the remark about the conditional formatting?


I've not been keeping track of all the posts...can you explain?

---

### Post by paulus4605 on 2009-02-16
no problem 
is it possible to get a conditional formatting on the temperature 

for instance if the temperature is between 0 and 10 degrees the colour is blue between 10 and 20 green between 20 and 30 orange and higher then 30 red 

or is this not possible

---

### Post by kaivalagi on 2009-02-16
> **paulus4605 said:**
> no problem 
is it possible to get a conditional formatting on the temperature 

for instance if the temperature is between 0 and 10 degrees the colour is blue between 10 and 20 green between 20 and 30 orange and higher then 30 red 

or is this not possible

Sure it's possible, not straight forward though

How do I build into the script something that both supports the css stuff and also config entries detailing temp based colour settings

maybe a javascript/css solution is what's needed, a special css class used with javascript to colourize temps...?

need to ponder for a bit :)

---

### Post by useResa on 2009-02-16
> **kaivalagi said:**
> I've not been keeping track of all the posts...can you explain?Additional to the request for conditional formatting of temperatures by paulus4605.

I am running gtk-desktop-info on Xubuntu Jaunty and although I have set the LOCALE to nl in the forecast config file the displayed language remains English (for a screenshot see [post #102]("http://ubuntuforums.org/showpost.php?p=6740670&postcount=102")).
Could this be caused by the fact I am running Jaunty?

---

### Post by kaivalagi on 2009-02-16
> **useResa said:**
> Additional to the request for conditional formatting of temperatures by paulus4605.

I am running gtk-desktop-info on Xubuntu Jaunty and although I have set the LOCALE to nl in the forecast config file the displayed language remains English (for a screenshot see [post #102]("http://ubuntuforums.org/showpost.php?p=6740670&postcount=102")).
Could this be caused by the fact I am running Jaunty?

You updated the config file located in ~/.config/gtk-desktop-info right?

I can't see why Jaunty would cause any issues...

edit: can you run the script from a terminal with trhe additional --verbose option? I will detail config file use etc...might be helpful to post the output e.g.

```
gtk-desktop-info --verbose --plugin=forecast
```

will output a lot of details including:
```

2009-02-16 13:56:21,258 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/mark/.config/gtk-desktop-info/plugin_forecast.config"
```

---

### Post by Bruce M. on 2009-02-16
> **kaivalagi said:**
> Sure it's possible, not straight forward though

How do I build into the script something that both supports the css stuff and also config entries detailing temp based colour settings

maybe a javascript/css solution is what's needed, a special css class used with javascript to colourize temps...?

need to ponder for a bit :)

Maybe something like Crinos512's script for conky could be modified (adapted to python) and the **plugin_forecast.config** could be modified to add a section, so people can pick their temps: (obviously needed for the differences between F° and C°)

```

COOL=16
WARM=26

```

Anything 16 and below is COOL-COLD (C°)
Anything 17 to 25 is WARM
26 and up HOT

The script:
```
#!/bin/bash
# colorize.sh
# by: Crinos512

COOL=65
WARM=80

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```

Might be a start!

I use it in conky for: CPU, GPU, CORE, MB & HD's (copied to different names)

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-02-16
**[CENTER][COLOR="DarkRed"][SIZE="5"]Under Construction![/SIZE][/COLOR][/CENTER]**

And for that reason no template at this time. Sorry about that folks!

[CENTER][[IMG]http://img264.imageshack.us/img264/3771/underconstructionrw6.th.png[/IMG]](http://img264.imageshack.us/my.php?image=underconstructionrw6.png)[/CENTER]

):P useResa & Paul!

Have a nice day!
Bruce

---

### Post by paulus4605 on 2009-02-16
Bruce 
you little raskal :-)

you did it AGAIN great job again 

if you would share the template and other files you corrected I would be grateful 

Paul

---

### Post by Bruce M. on 2009-02-16
> **paulus4605 said:**
> Bruce 
you little raskal :-)

you did it AGAIN great job again 

if you would share the template and other files you corrected I would be grateful 

Paul

Hi Paul, tried all day but the forums were down. Late but here you are:

[center][[IMG]http://img511.imageshack.us/img511/2681/almostdonerx0.th.png[/img]](http://img511.imageshack.us/my.php?image=almostdonerx0.png)[/center]
and the **template**
```
<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
	 LT (Forecast:Low Temp,Current:Feels Like Temp),
	 HT (Forecast:High Temp,Current:Current Temp),
	 CC (Current Conditions),
	 CC (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->

<table cellpadding="0" cellspacing="5" border="0">
<tr>
	<td rowspan="3" align="center" valign="top"><img src="[--datatype=WF]" width="100"/></td>
	<td rowspan="3" align="center" class="hoy-cyan">[--datatype=HT --hideunits]</td>
	<td rowspan="3" align="right" valign="center">
<!-- High, Low, ST -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-red">High:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Low:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green"><br>ST:</td>
		</tr>
		</table>
<!-- END: High, Low, ST -->
	</td>
	<td rowspan="3" align="right" valign="middle">
<!-- high, low, st values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td class="ml-red">[--datatype=HT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-cyan">[--datatype=LT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-green"><br>[--datatype=LT --hideunits]</td>
		</tr>
		</table>
<!-- END: high, low, st values -->
	</td>
	<td colspan="3" rowspan="4" align="right" valign="top">
<!-- Todays info text -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Visibilidad:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Humedad</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Punto&nbsp;del&nbsp;Rosco:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Pres&#237;on:</td>
		</tr>
		</table>
<!-- END: Todays info text -->	
	</td>
	<td rowspan="4" valign="top">
<!-- Todays info data -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td class="ml-cyan">[--datatype=UI]&nbsp;~&nbsp;[--datatype=UT]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=VI]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=HM]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=DP]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=BR]<br>[--datatype=BD]</td>
		</tr>
		</table>
<!-- END: Todays info data -->
	</td>
	<td colspan="4" align="center" valign="bottom" class="ml-yellow">los pr&#243;ximos d&#237;as</td>
</tr>
<tr><!-- 4 weekday names -->
	<td align="center" class="ml-wkday">[--datatype=DW --startday=1]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=2]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=3]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=4]</td>
</tr>
<tr>
	<td><!-- Day 1 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=1]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=1 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=1 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=1]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 2 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=2]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=2 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=2 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=2]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 3 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=3]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=3 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=3 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=3]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 4 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=4]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=4 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=4 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=4]</td>
		</tr>
		</table>
	</td>
</tr>
<tr>
	<td colspan="4" class="hugelight">&nbsp;&nbsp;[--datatype=CC]</td>
	<td colspan="4" class="hugelight">&nbsp;</td>
</tr>
<tr>
	<td rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=BS]" width="50"/><br><br>[--datatype=WD] [--datatype=WS]</td>
	<td colspan="3" rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=MF]" width="50"/><br><br>[--datatype=MP]</td>
	<td colspan="3">
<!-- sunrise - sunset & daylight text -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-sr">Salida&nbsp;del&nbsp;Sol:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Oscuro:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>Luz&nbsp;del&nbsp;d&#237;a:</td>
		</tr>
		</table>
<!-- END: sunrise - sunset & daylight text -->
	</td>
	<td align="center">
<!-- Today: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL]</td>
		</tr>
		</table>
<!-- END: Today: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 1: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=1]</td>
		</tr>
		</table>
<!-- END: Day 1: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 2: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=2]</td>
		</tr>
		</table>
<!-- END: Day 2: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 3: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=3]</td>
		</tr>
		</table>
<!-- END: Day 3: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 4: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=4]</td>
		</tr>
		</table>
<!-- END: Day 4: sunrise - sunset & daylight values -->
	</td>
</tr>
<tr>
	<td colspan="5" valign="top" align="right" class="smalldark">Last Update: [datatype=LU]</td>
	<td colspan="3" valign="top" align="right" class="smalldark">Last Fetch: [datatype=LF]</td>
</tr>
</table>
```

and to the top of what ever CSS file you are using add these:
```
body{
  font-family: arial, verdana, "sans-serif";
}

.hoy-cyan {
  color: #A7D4FF;
  font-size: 40px;
  font-weight: bold;
  font-style: italic;
}

.ml-red {
  color: #FF7B7B;
  font-size: 12px;
  font-weight: bold;
}

.ml-cyan {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.ml-green {
  color: #00FF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-yellow {
  color: #FFFF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-wkday {
  color: #8EEA8E;
  font-size: 12px;
  font-weight: bold;
}

.ml-sr {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.md-ss {
  color: #DE5F00;
  font-size: 12px;
  font-weight: bold;
}

.ml-daylight {
  color: #FFFFFF;
  font-size: 12px;
  font-weight: bold;
}

```
I simply added them to my working copy of the default CSS that I'm using. 

Some of those are exact duplicates of original calls renamed (thinking of the future).

Have fun!

Have a nice day.
Bruce

---

### Post by xeddog on 2009-02-16
I have a (hopefully) simple question.  I added the info to my sources and installed the gtk-desktop-info package.  Looks like it all went well, but . . .  These are the last messages I got.  They show unpacking and installing (0.09), but the gtk-desktop-info --version command shows 0.07.

.
.
.
Unpacking gtk-desktop-info (from .../gtk-desktop-info_0.09_all.deb) ...
Setting up gtk-desktop-info (0.09) ...

twoblues@Stealth:~$ gtk-desktop-info --version
gnome-desktop-info v.0.07
twoblues@Stealth:~$ 


What the heck, over??

TIA,

xeddog

---

### Post by kaivalagi on 2009-02-17
> **xeddog said:**
> I have a (hopefully) simple question.  I added the info to my sources and installed the gtk-desktop-info package.  Looks like it all went well, but . . .  These are the last messages I got.  They show unpacking and installing (0.09), but the gtk-desktop-info --version command shows 0.07.

.
.
.
Unpacking gtk-desktop-info (from .../gtk-desktop-info_0.09_all.deb) ...
Setting up gtk-desktop-info (0.09) ...

twoblues@Stealth:~$ gtk-desktop-info --version
gnome-desktop-info v.0.07
twoblues@Stealth:~$ 


What the heck, over??

TIA,

xeddog

That's my fault, I neglected to increment the version number internally in the script...it is 0.09 though. Everyone will bwe getting the same...

0.10 will be 0.10

---

### Post by paulus4605 on 2009-02-17
kaivalagi goodmorning

I found a 1 typo in the dutch translation file on the moonphases

Last quarter is actually translated as Laatse Kwartier this should be Laats**t**e Kwartier

I also see that light Drizzle is not translated if its possible can you add this as well the translation for this would be lichte motregen.



thanks Paul

---

### Post by kaivalagi on 2009-02-17
> **paulus4605 said:**
> kaivalagi goodmorning

I found a 1 typo in the dutch translation file on the moonphases

Last quarter is actually translated as Laatse Kwartier this should be Laats**t**e Kwartier

I also see that light Drizzle is not translated if its possible can you add this as well the translation for this would be lichte motregen.



thanks Paul

Paul,

I think it best for you to keep the .po / .mo files updated locally, and pass them on later.

I'll try and remember to remind all translators to provide updated files before I rollout the next version of this script and the conkyForecast script.

Ideally I should setup translation checkins to launchpad but that involve users knowing their way around bazaar.

---

### Post by paulus4605 on 2009-02-17
> **kaivalagi said:**
> Paul,

I think it best for you to keep the .po / .mo files updated locally, and pass them on later.

I'll try and remember to remind all translators to provide updated files before I rollout the next version of this script and the conkyForecast script.

Ideally I should setup translation checkins to launchpad but that involve users knowing their way around bazaar.

no problem 

can you tell explain to me how to modify the files in order to add new translations

thanks Paul

---

### Post by paulus4605 on 2009-02-17
kaivalagi

I know I am difficult but is there a way to override the current config file?
reason for this is to be able to show 2 different forecasts 1 for the current location and 1 for instance for the holiday location?

it is possible in conkyforecast to do this so I was wondering if it was possible in Desktop info to

Paul

---

### Post by kaivalagi on 2009-02-17
> **paulus4605 said:**
> kaivalagi

I know I am difficult but is there a way to override the current config file?
reason for this is to be able to show 2 different forecasts 1 for the current location and 1 for instance for the holiday location?

it is possible in conkyforecast to do this so I was wondering if it was possible in Desktop info to

Paul

You can point to alternative config files using the --config option. It's all detailed in the guide :)

---

### Post by kaivalagi on 2009-02-17
> **paulus4605 said:**
> no problem 

can you tell explain to me how to modify the files in order to add new translations

thanks Paul

New translations really should be added by myself into the code, and then a new .pot file should be generated.

If you are talking about the text such as "sunny" then you should think about using the --datatype=CC rather than --datatype=CT option. Any text coming from the CT option is varied and not limited...the text is free text and therefore open to be what ever weather.com decide it should be.

---

### Post by xeddog on 2009-02-17
I have a few more questions, and I think I will try to figure out some of them myself.  But for now, I have one question that is beyond this newb.  I have most of the weather configured the way I want it, but I still have a problem with the background.

I don't know how much of the following is relevant, but I am running Ubuntu Intrepid 32-bit with an ATI Radeon 9600 graphics card, and dual monitors.  I have it set up in "big desktop" mode and it is working ok (not good, but ok).  I also use a script called XML-WALL that someone wrote (sorry that I don't remember who it was) that changes wallpaper for me, and right now I change every minute.  I have all of my wallpapers in ~/Pictures/Desktop Wallpapers.

Anyway, when I run gtk-desktop-info I get an error message:
gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...

and the background for my weather is white.  In your guide you say that the script only handles Nautilus based wallpapers but I don't know what that means.  I tried using the --wallpaper option and pointed it to my wallpapaer directory, but it changed nothing except the error message a little bit.  Doing this gives me:
gtk-desktop-info - ERROR - Invalid wallpaper, using nothing...

So if you would, please tell me how to get a transparent background.

TIA,

xeddog

P.S.  By now you probably realize that I am not a script or html coder.  Maybe someday, but not now.  I can hatchet scripts enough to change text, or perhaps move it around a little, but that is about all.

---

### Post by paulus4605 on 2009-02-17
Xeddog,

can you try the following to deactivate the script that you have running and seleect just the default background from ubuntu.

I had the same error when I changed my current background with solid black colour, when I changed it back to my background everything was working like it should

Paul

---

### Post by xeddog on 2009-02-17
. . .uh . . .the following??

xeddog

---

### Post by paulus4605 on 2009-02-17
Sorry for my english try to following = try this 

Paul

---

### Post by kaivalagi on 2009-02-17
> **xeddog said:**
> I have a few more questions, and I think I will try to figure out some of them myself.  But for now, I have one question that is beyond this newb.  I have most of the weather configured the way I want it, but I still have a problem with the background.

I don't know how much of the following is relevant, but I am running Ubuntu Intrepid 32-bit with an ATI Radeon 9600 graphics card, and dual monitors.  I have it set up in "big desktop" mode and it is working ok (not good, but ok).  I also use a script called XML-WALL that someone wrote (sorry that I don't remember who it was) that changes wallpaper for me, and right now I change every minute.  I have all of my wallpapers in ~/Pictures/Desktop Wallpapers.

Anyway, when I run gtk-desktop-info I get an error message:
gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...

and the background for my weather is white.  In your guide you say that the script only handles Nautilus based wallpapers but I don't know what that means.  I tried using the --wallpaper option and pointed it to my wallpapaer directory, but it changed nothing except the error message a little bit.  Doing this gives me:
gtk-desktop-info - ERROR - Invalid wallpaper, using nothing...

So if you would, please tell me how to get a transparent background.

TIA,

xeddog

P.S.  By now you probably realize that I am not a script or html coder.  Maybe someday, but not now.  I can hatchet scripts enough to change text, or perhaps move it around a little, but that is about all.

First off the --wallpaper option should point to an image file rather than a folder, pointing to the correct wallpaper image should get you going.

The nastier problem of changing wallpapers it not solvable right now. When the script runs it grabs the wallpaper (using --wallpaper if set) and crops it to size and uses it as the background for the window (fake transparency). It does this once and not again unless the app is closed and opened again. As it only does this once when your wallpaper changes it's background will not...causing unwanted affects.

You could start by creating a background image the size of your whole desktop and make it black in colour. Then point to this using the --wallpaper option to at least have a black background...

I really dont want the script regenerating a background image on each refresh as this will use considerable amounts of memory.

You could maybe have a script which kills the process and starts it again when your wallpaper is refreshed, but it wouldn't be pretty...

Not sure what can be done really...I'll think on it.

Anyone else with any suggestions?

---

### Post by Bruce M. on 2009-02-17
> **xeddog said:**
> . . .uh . . .the following??

xeddog

Paulus4506 is right.

Deactivate the script that calls up your wallpapers. This app defaults to the regular "gnome" wallpaper background.

I couldn't use it at first as it only worked with gnome.

Now there is an option for us xfce guys.  :)


Have a nice day
Bruce

---

### Post by paulus4605 on 2009-02-17
> **Bruce M. said:**
> Paulus4506 is right.


Bruce

glad you agree with me, I know that my knowledge to linux is limited however when I dare to make a statement about certain things is because I managed to get the same type of error somewhere along the configuration process.

hope you managed to solve it 

Paul

---

### Post by Bruce M. on 2009-02-17
> **paulus4605 said:**
> kaivalagi

I know I am difficult but is there a way to override the current config file?
reason for this is to be able to show 2 different forecasts 1 for the current location and 1 for instance for the holiday location?

it is possible in conkyforecast to do this so I was wondering if it was possible in Desktop info to

Paul

HEY! That gaves me an idea... Winnipeg, Manitoba, Canada on top and Buenos Aires Argentina on the bottom. Even made a template in English for this one. Makes for a busy screen though.  :)

I see weather(dot)com is up to their old tricks though. What we get in the RSS feed isn't tha same as what they display on the site. {shaking head}

Oh well, it does work.  :)

Have a nice day.
Bruce

---

### Post by Gnounc on 2009-02-17
Is there any way to stop gtk-desktop-info from being minimized when I hit
show desktop?

---

### Post by Bruce M. on 2009-02-17
> **Gnounc said:**
> Is there any way to stop gtk-desktop-info from being minimized when I hit
show desktop?

That's strange.  Mine doesn't, I have FF displaying full screen and when I hit the "Desktop" icon - it's still there. I'm using Xfce - no compiz

Just had a thought, are you using compiz?

---

### Post by xeddog on 2009-02-17
Sorry, but I wasn't sure that is what you meant.  I read what you wrote a couple more times and finally figured out what you meant.  It was one of those "DUH!" moments.  No need to apologize for your english.  You seem to speak it (or at least type it :-) ) better than many US natives.

I did try it anyway, and when I switched to the ugly brown coffee stained background, the gtk-desktop-info background was transparent.  For a while.  But the next time that I terminated the script, and restarted it, the background was white again.

Now this brings up another question.  The template I am using is the one that was submitted by BruceM in post #122.  The only changes I have made to it are to change the language to english, and added the "--imperial" operand to some of the datatypes.

In his post, BruceM also submitted some code to be added "to the top of what ever CSS file you are using".  Since I am clueless when it comes to html, I have no idea what that means.  I have just stashed the code for now, so naturally all of the text in my template is black.  Can you tell me where to put it, and how to invoke it, or anything that can help me out with that??

TIA,

xeddog

---

### Post by kaivalagi on 2009-02-17
> **Gnounc said:**
> Is there any way to stop gtk-desktop-info from being minimized when I hit
show desktop?

No idea, I had a quick look and I can monitor window state but can't stop the minimize (iconify) in code.....yet

---

### Post by xeddog on 2009-02-17
OK, skip my question regarding CSS files.  rtf'nm (Read The F'N Manual) again and it was in there.   Crap.  Don't know how I missed that one.

Sorry,

xeddog

---

### Post by Bruce M. on 2009-02-17
> **xeddog said:**
> In his post, BruceM also submitted some code to be added "to the top of what ever CSS file you are using".  Since I am clueless when it comes to html, I have no idea what that means.  I have just stashed the code for now, so naturally all of the text in my template is black.  Can you tell me where to put it, and how to invoke it, or anything that can help me out with that??

TIA,

xeddog

Hi xeddog,

I start my app with:
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=700 --height=240 --x=0 --y=758 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```

And as you see in there I am using **--css=/home/bruloo/gtk-desk/my_forecast.css** it is a copy of the default **CSS** found at:
~.config/gtk-desktop-info/**plugin_forecsat_default.css**.

So copy the original file to where you want, add the code to the top of it, NOT the first few lines that are the same, and then use the **--css=** option to point to it. To get the colour you NEED to use that code I gave.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-02-17
> **xeddog said:**
> OK, skip my question regarding CSS files.  rtf'nm (Read The F'N Manual) again and it was in there.   Crap.  Don't know how I missed that one.

Sorry,

xeddog

Oh sure, pop this in while I was responding. :lolflag:

Oh well, at least it is fixed.

Have a nice evening.
Bruce

---

### Post by xeddog on 2009-02-17
Sorry about that.  Been trying to jockey several things today, the most demanding (and the most fun), has been playing with my soon-to-be-5 year old grand daughter.  Just playing with this while my wife and I are tag teaming her, or is she tag teaming us???  :-)

At this point I am thinking that I would really like to find a different weather information supplier.  Weather.com seems to only be updated at 55 minutes past the hour.  I would like updated information more often than once per hour.  Probably not a big deal here in the fall, winter, and spring, but in the summer our temps can rise quite rapidly in the summer.  I think on some of our hottest days we probably have a 5-7 deg F increase per hour.  Also, our summer winds don't start until around 1:00PM but by around 4:00PM they are blowing around 20 kts so the wind speed rises quickly too.   I don't have a clue how I'm going to go about doing that.

The other thing is that the current days information seems to stop after a while.  For example, the predicted high starts reporting "N/A".  I also see a lot of "N/A"'s for wind gust info, and chance of rain on occasion.

Thanks again for you help.  I'm sure I'll be back but for now it's dinner time.

xeddog

---

### Post by xeddog on 2009-02-17
To Kaivalagi - I have tried coding the --wallpaper option and pointed to both a specific .jpg file (one that xml-wall actually uses), and to just the folder.  Background was still white in both cases and the error is one of the two I listed earlier.

Thanks,

xeddog

---

### Post by xeddog on 2009-02-17
I really gotta stop doing this.  I have looked at the --wallpaper option and looked at and looked at it and . . .

Well, as soon as I sent the last post I looked yet again and saw what was going on with the background.  I just had to change:

 --wallpaper=/home/twoblues/Pictures/Desktop Wallpapers/ph475971050.jpg

to

 --wallpaper=/home/twoblues/Pictures/"Desktop Wallpapers"/ph475971050.jpg

Sheez.  Picky little system ain't it?

xeddog

---

### Post by paulus4605 on 2009-02-17
Xeddog, yeah linux is stuborn when it comes down to details but when it works it works.

just a question that is popping into my mind how do you manage to tag this problem play with your kid and wife? I try to do the same with my 2 year old daughter and when I do this I am completely lost either in the game with my kid so she is winning again, and the forecast script looks even crappier.


{tapping foot on the floor}Bruce Why are you running with my ideas again grrrr:D:D

You got that part working however I wanted to be able to display it all in one overview. at least for the forecast part.


have a nice one guys

Paul

---

### Post by Gnounc on 2009-02-18
I am trying to have my buddy list based purely on 
buddy icons.
if it shows they are there, if it doesnt, they are not, but
many of the people I have online do not use a buddy icon.
I found in pidgin "set custom buddy icon", so I used that.
In pidgin I see the buddy icon, but it doesnt showup in gtk-desktop-info

any ideas?

also this would fulfill my previous request of replacement images for online status!

---

### Post by kaivalagi on 2009-02-18
> **Gnounc said:**
> I am trying to have my buddy list based purely on 
buddy icons.
if it shows they are there, if it doesnt, they are not, but
many of the people I have online do not use a buddy icon.
I found in pidgin "set custom buddy icon", so I used that.
In pidgin I see the buddy icon, but it doesnt showup in gtk-desktop-info

any ideas?

also this would fulfill my previous request of replacement images for online status!

Looks like the custom icon doesn't come through using standard api calls to the pidgin interfaces...when I get some time I'll look at the api again and see if there is a way to display them.

Alternatively, I could add an option to tell the script of an icon to use when none is available? It would mean one icon for all who have none though...

---

### Post by paulus4605 on 2009-02-18
I have been playing around a bit with desktop weather forecast and came out with the following result

it is a screen filling one but if you have a 22 inch screen you shouldn't have a problem 

here's the screenshot
if you have any comments I would be glad to hear them 

Paul.

---

### Post by Gnounc on 2009-02-18
custom icon support would be optimal but yes, I'd be happy with a standard
no icon icon.
Thanks for looking into it.

---

### Post by Bruce M. on 2009-02-18
> **xeddog said:**
> Sorry about that.  Been trying to jockey several things today, the most demanding (and the most fun), has been playing with my soon-to-be-5 year old grand daughter.  Just playing with this while my wife and I are tag teaming her, or is she tag teaming us???  :-)

Good morning Grampa xeddog,

Welcome to the club, I've got two grandsons. We need more grandparents here. :) And just so you know, we have a 5 year old niece that does the same thing.

> **xeddog said:**
> At this point I am thinking that I would really like to find a different weather information supplier.  Weather.com seems to only be updated at 55 minutes past the hour.  I would like updated information more often than once per hour.  Probably not a big deal here in the fall, winter, and spring, but in the summer our temps can rise quite rapidly in the summer.  I think on some of our hottest days we probably have a 5-7 deg F increase per hour.  Also, our summer winds don't start until around 1:00PM but by around 4:00PM they are blowing around 20 kts so the wind speed rises quickly too.   I don't have a clue how I'm going to go about doing that.

I hear you, personally I prefer:

[http://www.wunderground.com/](http://www.wunderground.com/)

This is the start, the same as weather.com uses:
[http://www.wunderground.com/global/stations/87582.html?bannertypeclick=sunandmoontransblack&MR=1](http://www.wunderground.com/global/stations/87582.html?bannertypeclick=sunandmoontransblack&MR=1)

Cruise down to: *Select a source for your current conditions:* and change it to "Instrumentalia S.A-BsAs" and you'll see the same weather as they show on the TV's here. {sigh} 

Quite the difference. I've used Underground Weather for years. And they do have an RSS feed. My problem is I couldn't program my way out of a wet paper bag if my life depended on it.

> **xeddog said:**
> The other thing is that the current days information seems to stop after a while.  For example, the predicted high starts reporting "N/A".  I also see a lot of "N/A"'s for wind gust info, and chance of rain on occasion.

Thanks again for you help.  I'm sure I'll be back but for now it's dinner time.

xeddog

Yea, I get that too. Oh well, we do what we can with what we have.  :)

> **xeddog said:**
> I really gotta stop doing this.  I have looked at the --wallpaper option and looked at and looked at it and . . .

Well, as soon as I sent the last post I looked yet again and saw what was going on with the background.  I just had to change:

 --wallpaper=/home/twoblues/Pictures/Desktop Wallpapers/ph475971050.jpg

to

 --wallpaper=/home/twoblues/Pictures/"Desktop Wallpapers"/ph475971050.jpg

Sheez.  Picky little system ain't it?

xeddog

Well, see I learned something new. I didn't know I could make a new folder with the **"** marks. Personally, I'd rename **"Desktop Wallpapers"** to **Desktop_Wallpapers** and change it in your command line.

**[COLOR="Blue"]REASON:[/COLOR]** Sometimes Linux does **[COLOR="Red"]NOT[/COLOR]** like file names (folders as well) with blanks in them. So I've learned to use underscores as a result. If that's true there might be a day you come up against an **Oops!** because of the quote marks.

> **paulus4605 said:**
> Xeddog, yeah linux is stuborn when it comes down to details but when it works it works.

No more so then other OS's I've found. But it is absolutely "case sensitive" in all it's commands. But now truer words were said:> when it works it works.

> **paulus4605 said:**
> just a question that is popping into my mind how do you manage to tag this problem play with your kid and wife? I try to do the same with my 2 year old daughter and when I do this I am completely lost either in the game with my kid so she is winning again, and the forecast script looks even crappier.


{tapping foot on the floor}Bruce Why are you running with my ideas again grrrr:D:D

WHO! ME! :-\" :mrgreen: Would **"I"** do that?

> **paulus4605 said:**
> You got that part working however I wanted to be able to display it all in one overview. at least for the forecast part.


have a nice one guys

Paul

You to Paul and xeddog
Bruce

---

### Post by paulus4605 on 2009-02-18
Grrr Bruce 

what do you think of my new template?


Paul


And since Bruce likes to see whats it about I send in the template to 

```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=500 --height=700 --x=0 --y=750 --template=/home/baskingshark/test2.template --css=/home/baskingshark/test2.css --noheader --plugin=forecast &

```
handing Bruce his jacket and send him out to his work :D:D

if the wife isn't there to throw her man out a friend needs to take over that job :lolflag:):P:-\":-\"

Paul

---

### Post by Bruce M. on 2009-02-18
> **paulus4605 said:**
> I have been playing around a bit with desktop weather forecast and came out with the following result

it is a screen filling one but if you have a 22 inch screen you shouldn't have a problem 

here's the screenshot
if you have any comments I would be glad to hear them 

Paul.

22" screen, why you capitalist you!
{looking at 17" screen - grumble grumble}

**Comments:** busy busy busy!
I like - share the template (in Dutch is OK) please! :D

Have a nice day.
Bruce

**EDIT: Oops! he did!**

---

### Post by Bruce M. on 2009-02-18
> **paulus4605 said:**
> handing Bruce his jacket and send him out to his work :D:D

if the wife isn't there to throw her man out a friend needs to take over that job :lolflag:):P:-\":-\"

Paul

We have a saying in English: With friends like you who needs enemies! ):P

OK, colour me gone ... will get it when I get back.

Thanks
Bruce

---

### Post by paulus4605 on 2009-02-18
I wish I had a 22 inch lol 
Its on my wishlist but my wife doesn't let me 
this template is done on a 13 inch screen of my laptop

Paul

---

### Post by paulus4605 on 2009-02-18
kaivalagi,

at this point the moon phase for my region is "waning Crescent" 

Normally you would see the dutch translation for this when you selected nl in your locale,

so I was taking a look at the current translation file and to my surprise I see the correct translation next to it.

is there a reason why this isn't shown in the template?

Paul

---

### Post by xeddog on 2009-02-18
To BruceM, Paulus4605, and all the other grandpa's out there, if you have a 4 or 5 year old grandchild, you just THINK the tag teaming is your idea.  You just need to admit that this is HER (or his) idea and that this little kid is already smarter than you.  She will be playing "camping" with me while grandma is recouping on the couch.  As soon as there is a lull, Ava (that's the grand daughter's name) will tag grandma to do something else.  When grandma is on, I try to sneak down to my "room" and play with this computer.  It won't be too long until I hear the pitter patter of little feet and a little voice saying (SAYing??   More like YELLing) "GRANDPA!!  Did you forget that we were playing camping?"  Tag - I'm it.  I go back upstairs and find grandma sprawled out on the couch exhausted (again).  :-)

As for Wunderground, I am familiar with them, and actually that is the resource that I would LOVE to use.  In your description when you said to select "Instrumentalia S.A-BsAs", I suppose you noticed that one of the tabs said "Personal Weather Stations"??  That is EXACTLY what I would like to do.  

I think they are partners with, or somehow joined at the hip with AmbientWeather.   They (AW) have a free download called Weather Exchange Desktop that will display data from any station in their database.  If this were available for linux I probably would not be in this thread.  Many of these stations are personal stations, and I have found several that are within a few miles of my house.  I think one is even less than a mile away.  Many of them are not the most accurate in the world, they may not have the most comprehensive data, and there is no forecasting, but they can be the most "fun" to watch.  Unfortunately, this app is windows only and is not compatible with Wine.  Crap!

I'm sure that programming would not be too difficult, but like you, I cannot program my way out of a wet paper bag either.  One of the things on my list of shoulda's. 

As for including spaces in my folder and file names, all I can say is blame it on Windows.  That's my excuse and I'm stickin to it.  I have only been using linux for a short while and am still trying to overcome some Windows habits.  Notice I did not say "bad" habits because I think many of them are not good or bad, just different.

Ah well.  It's a new day and Ava has just arrived.  I will probably have the morning "tag" since I have a lot of honeydo's this afternoon.  Not much time to play then.

xeddog

---

### Post by kaivalagi on 2009-02-18
> **paulus4605 said:**
> kaivalagi,

at this point the moon phase for my region is "waning Crescent" 

Normally you would see the dutch translation for this when you selected nl in your locale,

so I was taking a look at the current translation file and to my surprise I see the correct translation next to it.

is there a reason why this isn't shown in the template?

Paul

The "c" is missing from crescent again...not sure why, I thought we'd fixed that...

I've updated the .pot file for next time

Can you update your .po file in poedit, if that fixes it then once you've passed it my way it will go out in the next release, probably at the weekend

All the other translations need fixing up too, but I dont think there is an online translation package that will do a good enough job :(

---

### Post by paulus4605 on 2009-02-18
Just a slight correction on the grandpas thingy ;) I just became a proud father of my second daughter, she is 6 weeks now, so to me the grandpa thingy is far far away pfew. 

my first kid is getting 2 this sunday while her dad is becoming 41 the very same day.

in a way getting a daughter on your birthday is the greatest present you could wish for, on the other hand all the attention is going to the little brat and dad is happy with a small attention as his daughter is in the spotlight. No I am not complaining far from that.

I build my very first linux server last February and since about 6 months the linux microbe completely hit me.

and now I try to tackle everything that I want to learn.

I have done some programming in php ruby on rails and even a course in java for a blue monday.

although I mentioned the above languages I don't, (and I am sorry to say this) have the time to train myself on a daily base with these languages.

simply because my current job doesn't require any of these languages.

I also started a graduate informatica in the evening. I had to stop that simply because that lonely braincell that I have left couldn't keep up with the younger generation and regardless the modern time of computers the if and do whiles are thought on paper instead of a descent computer.

so that's briefly where I am coming from. 

oh yes before I started with the computer world I was chef in a kitchen and everything I learned about computers is mostly self thought.

Paul

---

### Post by kaivalagi on 2009-02-18
> **Gnounc said:**
> custom icon support would be optimal but yes, I'd be happy with a standard
no icon icon.
Thanks for looking into it.

No worries

A new config setting will be available for the pidgin plugin next release, called "DEFAULTBUDDYICON". If you set that to a filepath of an image you want it will be used where no icon is available for a buddy.

When I have more time to research the api I'll see whether I can output the buddy specific default which is set through the pidgin UI...

---

### Post by kaivalagi on 2009-02-18
> **paulus4605 said:**
> Just a slight correction on the grandpas thingy ;) I just became a proud father of my second daughter, she is 6 weeks now, so to me the grandpa thingy is far far away pfew. 

my first kid is getting 2 this sunday while her dad is becoming 41 the very same day.

in a way getting a daughter on your birthday is the greatest present you could wish for, on the other hand all the attention is going to the little brat and dad is happy with a small attention as his daughter is in the spotlight. No I am not complaining far from that.

I build my very first linux server last February and since about 6 months the linux microbe completely hit me.

and now I try to tackle everything that I want to learn.

I have done some programming in php ruby on rails and even a course in java for a blue monday.

although I mentioned the above languages I don't, (and I am sorry to say this) have the time to train myself on a daily base with these languages.

simply because my current job doesn't require any of these languages.

I also started a graduate informatica in the evening. I had to stop that simply because that lonely braincell that I have left couldn't keep up with the younger generation and regardless the modern time of computers the if and do whiles are thought on paper instead of a descent computer.

so that's briefly where I am coming from. 

oh yes before I started with the computer world I was chef in a kitchen and everything I learned about computers is mostly self thought.

Paul

Congratulations on your second one! Still trying for our second :)

You might want to think about setting up eclipse with pydev, so you can debug my python scripts...that's what I use when there is an issue...you may find a bit of hobbyist time here and there ;) I can attempt to take you through step by step if you want, time permitting anyway.

BTW, I do a mean Jambalaya!

---

### Post by xeddog on 2009-02-18
Ok then, just wait til your second one is having their second one.  Ya wanna feel old????  [excremental expletive deleted].

xeddog

---

### Post by paulus4605 on 2009-02-18
> **kaivalagi said:**
> 

All the other translations need fixing up too, but I dont think there is an online translation package that will do a good enough job :(

for which files do you need translations? on the dutch part its not a problem so if I can help you out there feel free to ask.

have to finish that up before sunday since its my birthday and I wont be spending much time on the computer 

if I would my wife would kill me slowly instead of celebrating my birthday :lolflag:

Paul

ps: I also modified the waxing crescent since it was missing a c to
in attachment you have the translation files

---

### Post by xeddog on 2009-02-18
I have another question.  How long does it take your weather to show up on your desktop?  From the time I run the command in a terminal window until the weather is displayed is probably over a minute and more likely closer to 2 minutes.

xeddog

---

### Post by paulus4605 on 2009-02-18
Xeddog,
I am not sure but my guess is that you have to adapt the interval time which is set to 1800 you can reduce it by entering 300 for example.

but again I am not sure


Paul

---

### Post by xeddog on 2009-02-18
I have already changed the interval to 300.  I'll probably increase it a little when I get it working the way I want.

Thanks,

xeddog

---

### Post by kaivalagi on 2009-02-18
> **xeddog said:**
> I have already changed the interval to 300.  I'll probably increase it a little when I get it working the way I want.

Thanks,

xeddog

You may also need to update the config file here:

```
~/.config/gtk-desktop-info/plugin_forecast.config
```

It has a default expiry setting of:

```
EXPIRY_MINUTES = 30
```

This is so cached data is used rather than refetching....it is a carry over from conky. I should remove the option at some point....

**Bruce can you see any reason why not?**

** **

---

### Post by xeddog on 2009-02-18
Thank you for that, but EXPIRY MINUTES was already reset to 1.  I also set REFETCH to true.  This isn't a major issue so I can live with it.

xeddog

---

### Post by paulus4605 on 2009-02-18
> **kaivalagi said:**
> Congratulations on your second one! Still trying for our second :)

You might want to think about setting up eclipse with pydev, so you can debug my python scripts...that's what I use when there is an issue...you may find a bit of hobbyist time here and there ;) I can attempt to take you through step by step if you want, time permitting anyway.

BTW, I do a mean Jambalaya!

Always interested in learning something new so I would appreciate it if you'd show me how.

{starting to nose into the repos to dig out eclipse} {not so fast almost got it ) :D:D:D:D

Paul

---

### Post by kaivalagi on 2009-02-18
> **paulus4605 said:**
> Always interested in learning something new so I would appreciate it if you'd show me how.

{starting to nose into the repos to dig out eclipse} {not so fast almost got it ) :D:D:D:D

Paul

Dont install eclipse from the repos, best downloading the tarball from eclipse and unpacking (no compile needed)

Start here [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

and look for "Eclipse IDE for Java EE Developers (162 MB)", then download the tarball for your arch

Once you have it running let me know and I'll look through my settings to let you know what to do to get pydev incorporated

Probably best doing it via PM's...it could take a little time and effort

---

### Post by paulus4605 on 2009-02-18
Darn I already installed it

---

### Post by Gnounc on 2009-02-18
Awesome thanks!

---

### Post by HippyRandall on 2009-02-18
> **xeddog said:**
> Thank you for that, but EXPIRY MINUTES was already reset to 1.  I also set REFETCH to true.  This isn't a major issue so I can live with it.

xeddog
I had this same issue when using the refetch option. this is what my starting command looks like:
```

gtk-desktop-info --width=420 --height=310 --plugin=forecast --y=30 --interval=900 --noheader --colour=white &
```
and in the config file in ~/.config/gtk-desktop-info/plugin_forecast.config:

```
REFETCH = False
```

Hope it helps,
Hippy Randall

---

### Post by Bruce M. on 2009-02-18
> **xeddog said:**
> To BruceM, Paulus4605, and all the other grandpa's out there, if you have a 4 or 5 year old grandchild, you just THINK the tag teaming is your idea.

OUCH! That could wear down a person faster then anything. At five energy recharges in minutes, at our age it's nore like days.  :)

> **xeddog said:**
> As for Wunderground, I am familiar with them, and actually that is the resource that I would LOVE to use.  In your description when you said to select "Instrumentalia S.A-BsAs", I suppose you noticed that one of the tabs said "Personal Weather Stations"??  That is EXACTLY what I would like to do.

Not given that option here. Guess there's no one feeding into it. Would be nice though.

> **xeddog said:**
> I think they are partners with, or somehow joined at the hip with AmbientWeather.   They (AW) have a free download called Weather Exchange Desktop that will display data from any station in their database.

Oh, gotta check that one out, maybe they have a "plugin" to be used on webpages. I have my own right here on my machine that I created as my "homepage" it has a little "script" from Wunderground on it but it's just the current temp and stuff with a link to their page.

> **xeddog said:**
> One of the things on my list of shoulda's.

hahaha, If you're like me, my list of "Shoulda's" is bigger than my list of "Todo's". I think it has to do with "to old to wise". If only I had listened to older people when I was younger and "knew" everything. {sigh}

> **xeddog said:**
> As for including spaces in my folder and file names, all I can say is blame it on Windows.  That's my excuse and I'm stickin to it.  I have only been using linux for a short while and am still trying to overcome some Windows habits.  Notice I did not say "bad" habits because I think many of them are not good or bad, just different.

What a GREAT attitude! I came to Linux with my mind wide open, I knew it was going to be "different". Didn't stop me from saying **"Oops!"** a lot though as I didn't "know" what all the differences were and learned a lot the hard way. Nice thing about Linux though, if one breaks it, it's a "snap" to repair.

> **xeddog said:**
> Ah well.  It's a new day and Ava has just arrived.  I will probably have the morning "tag" since I have a lot of honeydo's this afternoon.  Not much time to play then.

xeddog

Oh boy, have fun. :p

Tag your it! Lets play "Who can dream the most in the next hour!"

Have a great day!
Bruce

---

### Post by kaivalagi on 2009-02-18
Guys,

There is always the --url option ;)

Build a page with weather widgets and host it somewhere then point to it using this script

you wont have transparency though...

---

### Post by Bruce M. on 2009-02-18
> **xeddog said:**
> Ok then, just wait til your second one is having their second one.  Ya wanna feel old????  [excremental expletive deleted].

xeddog

Hmmmmmm, nope, not there yet, #1 son had a son, #2 son had a son, #3 son is too busy with computer graphics I think. His day will come.

So I'm close.  :)
Bruce

---

### Post by Bruce M. on 2009-02-18
> **kaivalagi said:**
> Guys,

There is always the --url option ;)

Build a page with weather widgets and host it somewhere then point to it using this script

you wont have transparency though...

Why? If I wanted widgets, I get them on my desktop.

I like "gtk", and I want the transparency.  :)

weather(dot)com's faults are not your faults, I've learned to live with it. But it's still a point of "GRRRRRRRR!" (at them, not you)

As for my personal on my machine page, I can have all the weather I want there, but I don't have to open FF to see gtk.  :)

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-02-18
> **kaivalagi said:**
> You may also need to update the config file here:

```
~/.config/gtk-desktop-info/plugin_forecast.config
```

It has a default expiry setting of:

```
EXPIRY_MINUTES = 30
```

This is so cached data is used rather than refetching....it is a carry over from conky. I should remove the option at some point....

**Bruce can you see any reason why not?**

** **

I have mine set to:
```
# How long before the cache is deemed out-of-date, so next refresh it will be updated from the weather.com website
EXPIRY_MINUTES = 10
```

But I notice that weather(dot)coms last update was 1 hours and 57 minutes ago, so it's really a mute point. I can fetch every 30 minutes, or every minute, doesn't matter if they don't update their stuff.

I just set:
```
# How long before the cache is deemed out-of-date, so next refresh it will be updated from the weather.com website
EXPIRY_MINUTES = 1
```

and:
```
# If set to true new weather data will retrieved each time the plugin runs
REFETCH = True
```

and restarted gtk ... took a while for get the info but the results are in, see second image (not good news)

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-19
Since its rather calm at the office I have some time to experiment with different templates

Here I used a conky template from Bruce now just wait if he remembers this one lol 


and yes Bruce I also added the templates :-)

Paul

---

### Post by Bruce M. on 2009-02-19
> **paulus4605 said:**
> Since its rather calm at the office I have some time to experiment with different templates

Here I used a conky template from Bruce now just wait if he remembers this one lol 


and yes Bruce I also added the templates :-)

Paul

Of course I remember that!  :)

Neat idea.  :)

Later.
Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-02-19
Bruce,

just wondering why you are so keen on Dutch translations? 
**thinking perhaps he is going to become a dutch prof too** #-o:-k

---

### Post by Bruce M. on 2009-02-19
> **paulus4605 said:**
> Bruce,

just wondering why you are so keen on Dutch translations? 
**thinking perhaps he is going to become a dutch prof too** #-o:-k

No! Can't speak a word ... but the "code" ie: [datatype=xx] will tell me what it is.  :)

CHIMO!
Bruce

---

### Post by paulus4605 on 2009-02-19
Bruce I see,

Now you make sense, you applied for a job at a Dutch weather station. Will tell them you are a very dedicated person willing to learn :lolflag::lolflag::lolflag:

a real gentlemen. 


but seriously if you need help with translations from Dutch to English will be glad to help you out


Paul

---

### Post by xeddog on 2009-02-20
I just noticed something.  When using conkyforecast, the current conditions graphic changes to a night time version at some point.  Maybe after sunset or something.   But the gtk-desktop-info graphic stays daytime.  Is there an easy way to fix this?

xeddog

---

### Post by yeleek on 2009-02-20
I'm currently using conky to bring in a number of security related feeds (via curl/grep/awk/sed) and have them displayed on my desktop.  The negative of conky is none of the links work, so web addresses have to be entered manually if something appears that catches your interest.

Does this app allow working urls to be clicked on from the desktop?

Thanks

---

### Post by kaivalagi on 2009-02-20
> **yeleek said:**
> I'm currently using conky to bring in a number of security related feeds (via curl/grep/awk/sed) and have them displayed on my desktop.  The negative of conky is none of the links work, so web addresses have to be entered manually if something appears that catches your interest.

Does this app allow working urls to be clicked on from the desktop?

Thanks

Give it a go, use the --url option to load a page in the app, then click on a link. Also no reason why some static html links can't be tried, ones which are generated from the shell plugin etc maybe

Not coded for it but it may work "out the box"....

---

### Post by kaivalagi on 2009-02-20
> **xeddog said:**
> I just noticed something.  When using conkyforecast, the current conditions graphic changes to a night time version at some point.  Maybe after sunset or something.   But the gtk-desktop-info graphic stays daytime.  Is there an easy way to fix this?

xeddog

The core of the forecast plugin is identical to conkyForecast, I just modified to fit with html generated content.

The icons displayed in this app are based on the weather.com SDK, so an icon number in the xml translates to an image with a number based filename. There are night time ones in there, take a look in /usr/share/gtk-desktop-info/images/weathericons...image numbers 27,29,31,33,45,46,47 are icons with the moon in them...

In theory the forecast plugin _should_ be more accurate than the conkyForecast output...

edit: see attached screenshot...night time icons working for me

---

### Post by Bruce M. on 2009-02-20
> **kaivalagi said:**
> In theory the forecast plugin _should_ be more accurate than the conkyForecast output...

edit: see attached screenshot...it is now 18:44 here in the UK

I was just going to say, it works for me too!

Hmmmmmmmmm!

Have a nice day.
Bruce

---

### Post by xeddog on 2009-02-20
Well [excrement]!!

xeddog

---

### Post by Sherbertlemon on 2009-02-20
Sorry to bother, but I'm new to Ubuntu and I need to open some rar files and I cant do it.. I was wondering if you could help me, I would open my own chat thingy if i could but I dont know how..	:tongue:

---

### Post by ad_267 on 2009-02-20
Never mind, it's too early here and I'm still half asleep.

---

### Post by kaivalagi on 2009-02-20
> **xeddog said:**
> Well [excrement]!!

xeddog

lol, that's one way of putting it :)

If you still have issues with it check your config file settings and make sure you have an --interval option in the app call to make sure it refreshes regularly

---

### Post by ad_267 on 2009-02-20
> **Sherbertlemon said:**
> Sorry to bother, but I'm new to Ubuntu and I need to open some rar files and I cant do it.. I was wondering if you could help me, I would open my own chat thingy if i could but I dont know how..	:tongue:

Install the rar and unrar packages from System - Administration - Package Manager and then you should be able to extract them as you would a zip file or any other archive.
To make a new thread you need to go to the forum you want to post in ([http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)) and click on New Thread.

---

### Post by Sherbertlemon on 2009-02-20
Thank you so much!

---

### Post by Bruce M. on 2009-02-20
> **xeddog said:**
> Well [excrement]!!

xeddog

The stuff that comes out of the **south** end of a cow heading **north**.

Had to get "something" about the weather in there. \\:D/

Hope you get it fixed xeddog.
Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-02-23
Parently its calm on the weather front 

I'm impatiently waiting till tomorrow **grin** I got some money for my bday and I am getting myself a 24 inch monitor 

Paul

---

### Post by Bruce M. on 2009-02-23
> **paulus4605 said:**
> Parently its calm on the weather front 

I'm impatiently waiting till tomorrow **grin** I got some money for my bday and I am getting myself a 24 inch monitor 

Paul

I think you'll need to wait another day, I see sever thunderstorms for tomorrow.

*OH! Wait! That's for here!*

Well, then in that case Happy Birthday and happy shopping!

Are you going to get a flat-screen-LCD?

Have a GREAT day.
Bruce

---

### Post by paulus4605 on 2009-02-23
Bruce 
so you are off from work tomorrow when you have such thunderstorms poor you.

this is the screen that I am going to buy a samsung 2429 hs 23,6 inch wide lcd screen :-)

---

### Post by xeddog on 2009-02-25
Hey guys,  I have been experimenting with a background (--wallpaper) and can't seem to get past:

> gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...

What I have done is try to use several different applications to create a very simple .gif file that is nothing more than a transparent image, or some short text on a transparent background, and then use that .gif in the --wallpaper parameter when running the script.  "Seemed" like it would be simple.  Am I chasing something that cant be done??

I remember in the initial post it says that only Nautilus based wallpapers are supported.  Not sure what that means, but I am assuming that it means that transparency is not supported in Nautilus wallpapers?????

Thanks.

xeddog

---

### Post by Bruce M. on 2009-02-25
> **paulus4605 said:**
> Bruce 
so you are off from work tomorrow when you have such thunderstorms poor you.

this is the screen that I am going to buy a samsung 2429 hs 23,6 inch wide lcd screen :-)

I'm Jealous!!!!  Guess you have it up and running now huh. :)

I have a 17" Samsung SyncMaster 713n I love it!

---

### Post by kaivalagi on 2009-02-25
> **xeddog said:**
> Hey guys,  I have been experimenting with a background (--wallpaper) and can't seem to get past:



What I have done is try to use several different applications to create a very simple .gif file that is nothing more than a transparent image, or some short text on a transparent background, and then use that .gif in the --wallpaper parameter when running the script.  "Seemed" like it would be simple.  Am I chasing something that cant be done??

I remember in the initial post it says that only Nautilus based wallpapers are supported.  Not sure what that means, but I am assuming that it means that transparency is not supported in Nautilus wallpapers?????

Thanks.

xeddog

The app now supports automatic wallpapers (in most cases!) of gnome, kde3, kde4 and xfce wallpapers. You just need to tell it which window manager you are using. See the guide for more info or type "gtk-desktop-info -h". It will not handle tiling though, as it will resize up the tile to the screen res...not a nice effect!

The error text you are getting isn't much help unfortunately, it has happened because an error occurred when trying to manipulate the wallpaper image you have provided.

If you can replace /usr/share/gtk-desktop-info/gtk_desktop_info.py with the attached file and run again we may get more information

If you could also post the gif image and the command line you are using I can try to reproduce the issue at my end. To be honest I have never tried gif images, always jpg or png for me...png's support transparency btw

---

### Post by kaivalagi on 2009-02-25
> **Bruce M. said:**
> I'm Jealous!!!!  Guess you have it up and running now huh. :)

I have a 17" Samsung SyncMaster 713n I love it!

I have 1 x 22" and 1 x 19" in twinview :p

Good for developing on one screen and reading reference guides/posting on the forums on the other, that's my excuse for it anyway.

I would love 2 x 24" though!

---

### Post by xeddog on 2009-02-25
Thanks for the reply, I'll try that tomorrow.  But just as a quick note, I have not specified the --windowmanager parameter at all.  Since it defaults to gnome, and I am using gnome without any enhancements at all, I didn't think it was necessary.  I am not even using the "Normal" visual effects and have that set to "None" (I tried a few of them, but found them more distracting than anything).  No Compiz, no nuthin.

I will also try a .png image first to see if there is any diff.  I might also try the "--verbose" command line option too if I get brave enough.

Thanks again,

xeddog

---

### Post by paulus4605 on 2009-02-26
> **kaivalagi said:**
> I have 1 x 22" and 1 x 19" in twinview :p

Good for developing on one screen and reading reference guides/posting on the forums on the other, that's my excuse for it anyway.

I would love 2 x 24" though!

Kaivalagi I would have like 2 times 24 inch however my wife wouldn't settle for that, but since this was by birthday gift she made an exception lol.  I used for excuse that my server needed a screen for when I need to do some modifications there ( is hardly needed) but she doesn't know that.

I couldn't have 2 24 inch since my computerdesk does not have enough space to do handle it.

but I will survive for now lol

---

### Post by kaivalagi on 2009-02-26
> **paulus4605 said:**
> Kaivalagi I would have like 2 times 24 inch however my wife wouldn't settle for that, but since this was by birthday gift she made an exception lol.  I used for excuse that my server needed a screen for when I need to do some modifications there ( is hardly needed) but she doesn't know that.

I couldn't have 2 24 inch since my computerdesk does not have enough space to do handle it.

but I will survive for now lol

I'm sure you will survive just fine with 24"'s of display

This is what I would love: [http://www.youtube.com/watch?v=1DWzuIreDGA](http://www.youtube.com/watch?v=1DWzuIreDGA)

---

### Post by paulus4605 on 2009-02-26
I would like that to but my wife will not agree with me, have then i have to play a few tricks to make this happen, perhaps when I am going to move to a new house??


Paul

---

### Post by Bruce M. on 2009-02-26
> **xeddog said:**
> I am not even using the "Normal" visual effects and have that set to "None" (I tried a few of them, but found them more distracting than anything).  No Compiz, no nuthin.

Hi xeddog,

I'm like you in that respect: **no nuthin'**

I tried a transparent gif & png last night with gtk, after reading your post! **No go**, it came up with a white background!

Also, as K said, if I make an image the same size as my "window" for gtk (--width=750 --height=245) it resizes it to my full screen value (1280x1024). How do you spell: ***UGLY!***

What I'm going to try next is take an image (Hardwood_w_Lights.jpg) that is 1280x1024 and resize it to a width of 750x245 and "Save as..." then insert the small image into the large image right where my gtk displays. Doing this just for fun mind you.  :)

And the results are:

[CENTER][[IMG]http://img413.imageshack.us/img413/4907/hardwoodlightstest1.th.gif[/IMG]](http://img413.imageshack.us/my.php?image=hardwoodlightstest1.gif)  [[IMG]http://img413.imageshack.us/img413/7023/hardwoodlightstest2.th.gif[/IMG]](http://img413.imageshack.us/my.php?image=hardwoodlightstest2.gif)[/CENTER]

Maybe we can talk K into adding and option "--resize_wallpaper=" that can be used if someone adds the --wallpaper option.

--resize_wallpaper=yes - automatically resizes wallpapers and acts like it does now.
--resize_wallpaper=no - calls a wallpaper for gtk use only (maybe different to the existing and uses it as is from x=0 & y=0 on it's own x-y axis) It will always grab ab image from the upper right corner and use it to the size you have specified in the startup command. So if you "make" an image the same size, it uses it in full.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2009-02-26
> **kaivalagi said:**
> I have 1 x 22" and 1 x 19" in twinview :p

I would love 2 x 24" though!

> **paulus4605 said:**
> Kaivalagi I would have like 2 times 24 inch

but I will survive for now lol

You guys are awaking the **"wannahave"** beast in me.  :lolflag:

{down boy, down!} {crack of whip}

Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-02-26
> **Bruce M. said:**
> You guys are awaking the **"wannahave"** beast in me.  :lolflag:

{down boy, down!} {crack of whip}

Have a nice day.
Bruce

Bruce you have to play a tactical game with your wife and tell her that you need a new screen because you can better arrange the work that you are preparing for your English courses. don't tell her that you need to have it because its beautiful but you have to proof de use of a bigger screen.

Perhaps you can tell her that you can't read the fine print anymore and when you enlarge the text you can read it better.
one of the benefits of getting old :evil::evil:


take care my friend

Paul

---

### Post by Bruce M. on 2009-02-26
> **paulus4605 said:**
> Perhaps you can tell her that you can't read the fine print anymore and when you enlarge the text you can read it better.
one of the benefits of getting old :evil::evil:

Hahahahaha, would not work.

If it did I'd have a stystem that would make "Warlock's Control Room", in the latest Die-Hard movie, look old!

It's my wallet that is laughing it's head off here.

:lolflag: <<--- wallet --->> :lolflag:
And I do mean tears of peeling laughter!

Seriously: I'm very satisfied with what I have. I have it because a benifactor, Willy Ratz, decided I shouldn't be running an old P-III and sent me, no strings attached, the parts to build this computer, the WRSSCC:

MSI K8N SLI-F 939 MB, AMD Athlon 64 +3500, 4 GIG RAM, nVidea GeForce 7300 GS - 256M, Creative SB Audigy 4, LG-DVD-RW-RAM and more.

Believe me, I'm always going to be in his debt.
Have a nice day.
Bruce

---

### Post by hpnc2 on 2009-02-26
Hi all,
in first sorry for my english...
i tried gtk-desktop-info on gnome-compiz-emerald, the result is that i can't get true transparency... :-(
i tuned compiz to remove the shadow and it look little better, but alwais visible the window.

also if i try to turn the cube the transparency is not!!
so, the question is: is me that missing somentingh in the thread, or really can't get trasparent with compiz??

thanks all
Ciao

---

### Post by HippyRandall on 2009-02-26
> **Bruce M. said:**
> "Warlock's Control Room", in the latest Die-Hard movie
All praise the genius that is Kevin Smith!!!:guitar:

---

### Post by kaivalagi on 2009-02-26
> **hpnc2 said:**
> Hi all,
in first sorry for my english...
i tried gtk-desktop-info on gnome-compiz-emerald, the result is that i can't get true transparency... :-(
i tuned compiz to remove the shadow and it look little better, but alwais visible the window.

also if i try to turn the cube the transparency is not!!
so, the question is: is me that missing somentingh in the thread, or really can't get trasparent with compiz??

thanks all
Ciao

I haven't got around to figuring out how to automatically handle compiz based wallpaper settings, so the wrong background will probably be used if at all.

I suggest you use the --wallpaper option for now to tell the app what wallpaper you are using, it should then make the output transparent (if the wallpaper is full screen res or if resized to full screen res will match your background)

---

### Post by kaivalagi on 2009-02-26
**[COLOR="Green"][SIZE="4"]WALLPAPER FUNCTIONALITY EXPLAINED[/SIZE][/COLOR]**

I though it may help to explain exactly how the _current_ wallpaper functionality works, step by step.

[LIST=1]
[*]if --wallpaper set, use this to get path to image
[*]if not set get the wallpaper path appropriately for window manager setting (compiz not supported yet, but standard gnome/kde3/kde4/xfce settings should be)
[*]check whether wallpaper image file present
[*]get image data into app
[*]determine screen res
[*]if image size less than screen res resize the image to it
[*]define the crop needed based on the position and size of gtk-desktop-info window
[*]crop the image
[*]define temp path for cropped image
[*]save image
[*]use temp path for background of html content in app
[/LIST]

**[COLOR="Blue"][SIZE="4"]WHAT NEXT?[/SIZE][/COLOR]**

If there are more suggestions on wallpaper handling please speak up, I think it would be best if we got all the ideas on the table first and then decided amongst us what would be best to cover off the requirements...

The option to stop resizing makes total sense, it will allow users to have an alternative background just for the app (good call). This I can do easily by only resizing if allowed by the options...I think the cropping should stay though just to make sure the image is the right size for the output...

So...any other ideas/thoughts?

[SIZE="4"]**[COLOR="Red"]SO FAR...[/COLOR]**[/SIZE]

I'm playing about with a --noresize option...

Using this command we get the attached output (some options are my default ones, only --noresize and --wallpaper are making the difference)

```
gtk-desktop-info --colour=green --allworkspaces --noheader --verbose --logfile=/tmp/gtk-desktop-info.log --width=400 --height=250 --x=500 --y=100 --plugin=rhythmbox  **--noresize** --wallpaper=/tmp/test.png
```

---

### Post by paulus4605 on 2009-02-26
> **Bruce M. said:**
> Hahahahaha, would not work.

If it did I'd have a stystem that would make "Warlock's Control Room", in the latest Die-Hard movie, look old!

It's my wallet that is laughing it's head off here.

:lolflag: <<--- wallet --->> :lolflag:
And I do mean tears of peeling laughter!

Bruce

I know what you mean if I would have a go to my perfect system I would be begging and more at the side of my wife and she will give in way to slow grrrr

just got a perfect system last year 

	CORSAIR Twinx Ddr2 2048mb Pc8500 Dominator Xms2 Epp (2x1024mb)
1x	CREATIVE Fatal1ty Champion X-fi Xtreme Gamer Retail
1x	ASUS Eah3850/g/htdi 512mb Ddr3 Pci Express
3x	WESTERN DIGITAL 500gb-ks 16mb Sata300 7200rpm
1x	LOGITECH X540 Speakers
1x	INTEL Core 2 Quad Q6600 2.40 Socket 775
1x	MICROSOFT Oem Nl Business 64bit Vista
1x	ASUS P5e-v Hdmi Socket 775 Intel G35


only bugger is that I can't get my soundcard to work under linux grrrr otherwhise it would have been  a perfect setup to work with the weather forecast

have a nice day my friend

Paul

---

### Post by paulus4605 on 2009-02-27
Kaivalagi:

I just found out about this tool that is used for the conky and conky forecast under windows [http://lifehacker.com/5087956/customize-your-own-killer-enigma-desktop](http://lifehacker.com/5087956/customize-your-own-killer-enigma-desktop)  

hope they didn't copy your work my friend.

Paul

---

### Post by kaivalagi on 2009-02-27
> **paulus4605 said:**
> Kaivalagi:

I just found out about this tool that is used for the conky and conky forecast under windows [http://lifehacker.com/5087956/customize-your-own-killer-enigma-desktop](http://lifehacker.com/5087956/customize-your-own-killer-enigma-desktop)  

hope they didn't copy your work my friend.

Paul

No, don't think it's ripped off. I can't download the source though...

---

### Post by hpnc2 on 2009-02-27
Hi kivalagi, thanks for the answer, i think that the program handle correctely the wallpaper, and in fact it look transparent now, tho only is that is not transparent when i "extrude" the cube to turn it....
i will try next day tuning up compiz, but seem same problem that occour in conky when i set own_window=no ....
thanks

> **kaivalagi said:**
> I haven't got around to figuring out how to automatically handle compiz based wallpaper settings, so the wrong background will probably be used if at all.

I suggest you use the --wallpaper option for now to tell the app what wallpaper you are using, it should then make the output transparent (if the wallpaper is full screen res or if resized to full screen res will match your background)

---

### Post by kaivalagi on 2009-02-27
> **hpnc2 said:**
> Hi kivalagi, thanks for the answer, i think that the program handle correctely the wallpaper, and in fact it look transparent now, tho only is that is not transparent when i "extrude" the cube to turn it....
i will try next day tuning up compiz, but seem same problem that occour in conky when i set own_window=no ....
thanks

It's not transparent on rotate because compiz only works with the background...the app fakes the transparency by cropping the background and using that...the app is really a gtk window with no borders running a webkit browser view with a background image set.

I dont think you'll ever get around this issue with compiz, unless widget layers help? not my speciality though!

---

### Post by Bruce M. on 2009-02-27
> **kaivalagi said:**
> **[COLOR="Green"][SIZE="4"]WALLPAPER FUNCTIONALITY EXPLAINED[/SIZE][/COLOR]**

So...any other ideas/thoughts?

Obvioiusly if using (--windowmanager=xfce4) it as it is today, grabbing a 1280x1024 background (for example) cropping is needed so the app gets what is really under it.

> **kaivalagi said:**
> [SIZE="4"]**[COLOR="Red"]SO FAR...[/COLOR]**[/SIZE]

I'm playing about with a --noresize option...

Using this command we get the attached output (some options are my default ones, only --noresize and --wallpaper are making the difference)

```
gtk-desktop-info --colour=green --allworkspaces --noheader --verbose --logfile=/tmp/gtk-desktop-info.log --width=400 --height=250 --x=500 --y=100 --plugin=rhythmbox  **--noresize** --wallpaper=/tmp/test.png
```

Yea, that's precicely what I was talking about. Most people, once the app is set up will leave it for a while. This way they can have a seperate background designed for it.

For example, mine looks best on a darker background, but if I change my background that is light I can create a background for the app and use a different command to call it.

Mine today is:
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```
I could create a second one:
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast --noresize --wallpaper=/Wallpapers/gtk/dark.png &
```
dancing between the two (or three or four) if my background isn't dark, or just to look different.

**Way to go K!**

CHIMO!
Bruce

---

### Post by kaivalagi on 2009-02-27
I'll give it until Sunday, if no more requirements surface I'll release 0.10 with the --noresize option

So far the changes for both packages are:

[LIST]
[*]Added DEFAULTBUDDYICON setting to pidgin plugin config, if set a default icon will be used for all buddies where one is not set
[*]Updated forecast plugin translation .pot file
[*]Altered the ordering of the deluge plugin output to include state as well as progress, states are listed in the order downloading, seeding, paused, unknown
[*]Added --noresize option to the main app to stop resizing the used/found wallpaper to the screen resolution
[*]Updated the pdf guide
[*]General update of translation .pot/.po/.mo files to include moon phase where it wasn't present (only english to english for now)
[/LIST]

---

### Post by paulus4605 on 2009-02-27
> **kaivalagi said:**
> I'll give it until Sunday, if no more requirements surface I'll release 0.10 with the --noresize option

So far the changes for both packages are:

[LIST]
[*]Added DEFAULTBUDDYICON setting to pidgin plugin config, if set a default icon will be used for all buddies where one is not set
[*]Updated forecast plugin translation .pot file
[*]Altered the ordering of the deluge plugin output to include state as well as progress, states are listed in the order downloading, seeding, paused, unknown
[*]Added --noresize option to the main app to stop resizing the used/found wallpaper to the screen resolution
[*]Updated the pdf guide
[*]General update of translation .pot/.po/.mo files to include moon phase where it wasn't present (only english to english for now)
[/LIST]

if you need help on the dutch translation just let me know I will translate them for you

Paul

---

### Post by kaivalagi on 2009-02-27
> **paulus4605 said:**
> if you need help on the dutch translation just let me know I will translate them for you

Paul

I think the Dutch translation is all good since your last update

These 2 entries are the ones that matter 'cause the crescent was spelt wrong before:

```
msgid "Waning Crescent"
msgstr "Afnemende Maan"

msgid "Waxing Crescent"
msgstr "Wassende Maan"
```

---

### Post by useResa on 2009-02-27
Today I dist-upgraded my Xubuntu Jaunty installation, followed by an autoclean and autoremove. The last resulted in the removal of **gtk-desktop-info** (plus related packages).

When I try to re-install I get the following result
```
rdrijsen@xubuntu-pIII:/$ sudo aptitude install gtk-desktop-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  python-webkitgtk 
The following NEW packages will be installed:
  gtk-desktop-info gtk-desktop-info-data{a} libwebkit-1.0-1{a} python-xlib{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7093kB of archives. After unpacking 15.6MB will be used.
The following packages have unmet dependencies:
  python-webkitgtk: Depends: python (< 2.6) but 2.6.1-0ubuntu1 is installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gtk-desktop-info [Not Installed]
python-webkitgtk [Not Installed]

Score is -9870

Accept this solution? [Y/n/q/?]
```
For now I will press **q** to Abort.

So for now I am without the Desktop Info App on my desktop.
Is there any information on when a Jaunty version will be available?

---

### Post by kaivalagi on 2009-02-27
> **useResa said:**
> Today I dist-upgraded my Xubuntu Jaunty installation, followed by an autoclean and autoremove. The last resulted in the removal of **gtk-desktop-info** (plus related packages).

When I try to re-install I get the following result
```
rdrijsen@xubuntu-pIII:/$ sudo aptitude install gtk-desktop-info
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  python-webkitgtk 
The following NEW packages will be installed:
  gtk-desktop-info gtk-desktop-info-data{a} libwebkit-1.0-1{a} python-xlib{a} 
0 packages upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 7093kB of archives. After unpacking 15.6MB will be used.
The following packages have unmet dependencies:
  python-webkitgtk: Depends: python (< 2.6) but 2.6.1-0ubuntu1 is installed.
The following actions will resolve these dependencies:

Keep the following packages at their current version:
gtk-desktop-info [Not Installed]
python-webkitgtk [Not Installed]

Score is -9870

Accept this solution? [Y/n/q/?]
```
For now I will press **q** to Abort.

So for now I am without the Desktop Info App on my desktop.
Is there any information on when a Jaunty version will be available?

Until I upgrade to Jaunty there will not be anything specific done. I don't upgrade until at least one week into the final release...

The python-webkitgtk package is the culprit needing python 2.5 by the looks of it. I would be tempted to install it anyway, python 2.6 should support 2.5 functionality, python 3.0 is the one coming that may cause issues. If you installed anyway worst case you should be able to remove the packages again...

Alternatively, as you are in beta still, you may just want to wait as this issue might get fixed - could just be a dependancy bug. I would assume my app is not the only one using python-webkitgtk

What packages are available in Jaunty with "webkit" in the name? Maybe thier is an equivalent package with a different name?

[COLOR="Navy"]Edit: I checked jaunty packages online and it does look like the python-webkitgtk package needs it's python dependency updated...it's probably just a case of testing it against python 2.6 to make sure all is good before allowing the newly required 2.6 version dependency in.[/COLOR]

---

### Post by Gnounc on 2009-02-27
Im not sure, but I think below, is the Pidgin API for 
telling if a buddy has a custom buddy icon set, 
and for finding that buddy icon.

Im not great at reading these things, and I dont know how to program.
I can't tell if that means they have set themselves an icon, of if you have set them a custom icon. But I thought I would post it in the hopes.



[http://developer.pidgin.im/doxygen/dev/html/buddyicon_8h.html#be51c2541393384df007a8576a139bc1](http://developer.pidgin.im/doxygen/dev/html/buddyicon_8h.html#be51c2541393384df007a8576a139bc1)



PurpleStoredImage* purple_buddy_icons_node_find_custom_icon  	(  	PurpleBlistNode *   	 node  	 )   	

Returns the custom buddy icon image for a blist node.

The caller owns a reference to the image in the store, and must dereference the image with purple_imgstore_unref() for it to be freed.

This function deals with loading the icon from the cache, if needed, so it should be called in any case where you want the appropriate icon.

Parameters:
    	node 	The node.

Returns:
    The custom buddy icon. 

Since:
    2.5.0 

gboolean purple_buddy_icons_node_has_custom_icon 	( 	PurpleBlistNode *  	node 	 )  	

Returns a boolean indicating if a given blist node has a custom buddy icon.

Parameters:
    	node 	The blist node.

Returns:
    A boolean indicating if node has a custom buddy icon. 

Since:
    2.5.0 

PurpleStoredImage* purple_buddy_icons_node_set_custom_icon 	( 	PurpleBlistNode *  	node,
		guchar *  	icon_data,
		size_t  	icon_len	 
	) 			

Sets a custom buddy icon for a blist node.

This function will deal with saving a record of the icon, caching the data, etc.

Parameters:
    	node 	The blist node for which to set a custom icon.
    	icon_data 	The image data of the icon, which the buddy icon code will free. Use NULL to unset the icon.
    	icon_len 	The length of the data in icon_data.

Returns:
    The icon that was set. The caller does NOT own a reference to this, and must call purple_imgstore_ref() if it wants one.

---

### Post by NuttyMonk on 2009-02-28
Hi,

Been having a look at the gtk-desktop-info app.

I can see how it could be easier to work with than conky, but there are a lot of pieces of info which i have no idea how to get into it.  e.g. hard disk space, memory, cpu usage, up/down internet usage etc.  I can't even manage to load an swf file into it  :-(

I know it's still in the beta, but i think i'll wait for a while to see how it develops before i decide to make a move over to it.

Thanks for letting me know about it though Kai.

Cheers

NM

---

### Post by kaivalagi on 2009-02-28
> **NuttyMonk said:**
> Hi,

Been having a look at the gtk-desktop-info app.

I can see how it could be easier to work with than conky, but there are a lot of pieces of info which i have no idea how to get into it.  e.g. hard disk space, memory, cpu usage, up/down internet usage etc.  I can't even manage to load an swf file into it  :-(

I know it's still in the beta, but i think i'll wait for a while to see how it develops before i decide to make a move over to it.

Thanks for letting me know about it though Kai.

Cheers

NM

Fair enough

loading an swf would require writing the html in a custom template and using it with the null plugin, not very intuitive I know :)

---

### Post by kaivalagi on 2009-02-28
@Gnounc

I had gone through all the api functions for custom buddy icons before now, and had a crack at getting the image but it didn't behave as expected.

At some point down later on I'll have another go...it's in my todo's

---

### Post by Gnounc on 2009-02-28
thankya

---

### Post by Bruce M. on 2009-02-28
OK, I was asked for my template. HONEST I WAS! I'm famous! :lolflag:

First I start gtk with: **mydesktop.sh** (call it whatever you want though)
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```
Next come the template - look at that It's still called **test.template**, I gotta change that some day.  :)
```
<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
	 LT (Forecast:Low Temp,Current:Feels Like Temp),
	 HT (Forecast:High Temp,Current:Current Temp),
	 CC (Current Conditions),
	 CC (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->

<table cellpadding="0" cellspacing="5" border="0">
<tr>
	<td rowspan="3" align="center" valign="top"><img src="[--datatype=WF]" width="100"/></td>
	<td rowspan="3" align="center" class="hoy-cyan">[--datatype=HT --hideunits]</td>
	<td rowspan="3" align="right" valign="center">
<!-- High, Low, ST -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-red">High:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Low:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green"><br>ST:</td>
		</tr>
		<tr>
			<td align="right" class="ml-wkday">PC:</td>
		</tr>
		</table>
<!-- END: High, Low, ST -->
	</td>
	<td rowspan="3" align="right" valign="middle">
<!-- high, low, st values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td class="ml-red">[--datatype=HT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-cyan">[--datatype=LT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-green"><br>[--datatype=LT --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-wkday">[--datatype=PC --startday=0]</td>
		</tr>
		</table>
<!-- END: high, low, st values -->
	</td>
	<td colspan="3" rowspan="4" align="right" valign="top">
<!-- Todays info text -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Visibilidad:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Humedad</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Punto&nbsp;del&nbsp;Roc&#237;o:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Pres&#237;on:</td>
		</tr>
		</table>
<!-- END: Todays info text -->	
	</td>
	<td rowspan="4" valign="top">
<!-- Todays info data -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td class="ml-cyan">[--datatype=UI]&nbsp;~&nbsp;[--datatype=UT]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=VI]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=HM]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=DP]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=BR]<br>[--datatype=BD]</td>
		</tr>
		</table>
<!-- END: Todays info data -->
	</td>
	<td colspan="4" align="center" valign="bottom" class="ml-yellow">los pr&#243;ximos d&#237;as</td>
</tr>
<tr><!-- 4 weekday names -->
	<td align="center" class="ml-wkday">[--datatype=DW --startday=1]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=2]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=3]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=4]</td>
</tr>
<tr>
	<td><!-- Day 1 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=1]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=1 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=1 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=1]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 2 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=2]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=2 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=2 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=2]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 3 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=3]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=3 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=3 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=3]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 4 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=4]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=4 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=4 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=4]</td>
		</tr>
		</table>
	</td>
</tr>
<tr>
	<td colspan="4" class="hugelight">&nbsp;&nbsp;[--datatype=CC]</td>
	<td colspan="4" class="hugelight">&nbsp;</td>
</tr>
<tr>
	<td rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=BS]" width="50"/><br><br>[--datatype=WD] [--datatype=WS]</td>
	<td colspan="3" rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=MF]" width="50"/><br><br>[--datatype=MP]</td>
	<td colspan="3">
<!-- sunrise - sunset & daylight text -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-sr">Salida&nbsp;del&nbsp;Sol:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Puesto del Sol:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>Horas de Luz:</td>
		</tr>
		</table>
<!-- END: sunrise - sunset & daylight text -->
	</td>
	<td align="center">
<!-- Today: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL]</td>
		</tr>
		</table>
<!-- END: Today: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 1: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=1]</td>
		</tr>
		</table>
<!-- END: Day 1: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 2: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=2]</td>
		</tr>
		</table>
<!-- END: Day 2: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 3: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=3]</td>
		</tr>
		</table>
<!-- END: Day 3: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 4: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=4]</td>
		</tr>
		</table>
<!-- END: Day 4: sunrise - sunset & daylight values -->
	</td>
</tr>
<tr>
	<td colspan="5" align="right" valign="bottom" class="smalldark">Last Update: [datatype=LU]</td>
	<td colspan="3" align="right" valign="bottom" class="smalldark">Last Fetch: [datatype=LF]</td>
</tr>
</table>
```
OK, one other thing, I'm using custom colours so in what ever **forecast.css** you use add these:
```
.hoy-cyan {
  color: #A7D4FF;
  font-size: 40px;
  font-weight: bold;
  font-style: italic;
}

.ml-red {
  color: #FF7B7B;
  font-size: 12px;
  font-weight: bold;
}

.ml-cyan {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.ml-green {
  color: #00FF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-yellow {
  color: #FFFF00;
  font-size: 12px;
  font-weight: bold;
}

.ml-wkday {
  color: #8EEA8E;
  font-size: 12px;
  font-weight: bold;
}

.ml-sr {
  color: #A7D4FF;
  font-size: 12px;
  font-weight: bold;
}

.md-ss {
  color: #DE5F00;
  font-size: 12px;
  font-weight: bold;
}

.ml-daylight {
  color: #FFFFFF;
  font-size: 12px;
  font-weight: bold;
}
```
and everything should work!

If you have questions just ask. As you see, mine is in Spanish
Have a nice day.
Bruce

**EDIT:** It was pointed out that I had a few "embarrassing" boo-boos with my Spanish. Nothing like "bad words" just bad translations of things like: "Hours of Daylight" and "Dew Point" **[COLOR="Red"]- hanging head in shame.[/COLOR]** None of the errors or changes I did today affect the operation of the app. :lolflag:

---

### Post by HippyRandall on 2009-02-28
as usual, Bruce, some stellar work there.:popcorn:

CHIMO
Hippy

---

### Post by paulus4605 on 2009-03-01
Bruce 
I have to agree with Hippy You did a great job again 
as usual

:popcorn::popcorn::popcorn:

{must get back to the drawing board}

Bruce 
another question how did you get that darn creative card working under ubuntu?

mine doesn't like me and tells me to create sound myself,
I can tell you that my wife doesn't like these sounds :lolflag:
and the little sandman even less since I get into bed way past my bedtime 

Paul

---

### Post by stepper on 2009-03-01
> **kaivalagi said:**
> Play back will be an issue, the app is essentially much the same as conky except it renders everything in html rather than plain text with fonts.

Because of this, the output is generally read only.

To get playback controls would require some clever javascript to talk to exaile from a browser window basically. If you can find some way to talk to exaile using javascript then I'd be happy to help you implement it in a template.

Food for thought.....how to render html but also have rich python gui content too.

K, I have managed to get both javascript and java to control exaile by using the methods below:

Java:
```
import java.io.*;
import javax.swing.JApplet;

public class exailenext extends JApplet {
     public static void main(String args[]) throws IOException         {
                Runtime rt = Runtime.getRuntime();
                Process proc = rt.exec("exaile -n");       }
{
```
Then in terminal: $javac exailenext.java, then $java exailenext... exaile plays next track

Javascript:
```

var jvclass = new java.lang.Runtime.getRuntime();
function back() {
jvclass.exec("exaile -p");
}
```
$java org.mozilla.javascript.tools.jsc.Main exaileback.js
$java exaileback...exaile plays previous track

But putting all together in my gtk-desktop-info exaile template like this:
```
<div id="wrapper">
	<div class="content">
		<div class="coverart"><img src="[--datatype=CA]" width="210"/></div>
               
		 <div class="largedark">[--datatype=TI --nounknownoutput]</div>
		<div class="mediumdark">[--datatype=AR --nounknownoutput]</div>	
		<div class="mediumdark">[--datatype=AL --nounknownoutput]</div>
		<div class="mediumdarkleft">[--datatype=PT --nounknownoutput] / [--datatype=LE --nounknownoutput]</div>         
		<div class="mediumdarkright">[--datatype=YR]</div>  
		<div class="rating"><img src="[--datatype=RT]" width="64"/></div>          
		<div class="barborder"><table width="[--datatype=PP]%" cellpadding="0" cellspacing="0"><tr><td class="bar">&nbsp;</td></tr></table>	
	   </div>

	</div>  
</div>
<script language="javascript" src="/home/stepper/exailecontrol.js">
</script>
<body>
<form>
<td align="center">
<font size="3" face="Buttons and Switches JL">
<input type="button" value="c" onclick="javascript:back()"><input type="button" value="d" onclick="javascript:stop()" ><input type="button" value="a" onclick="javascript:play()"><input type="button" value="f" onclick="javascript:pause()"><input type="button" value="b" onclick="javascript:next()" ></font>
</td>
</form>
</body>
```
my exailecontrol.js
```
var jvclass = new java.lang.Runtime.getRuntime();

function back() {
jvclass.exec("exaile -p");
}
function stop() {
jvclass.exec("exaile -s");
}
function next() {
jvclass.exec("exaile -n");
}
function play() {
jvclass.exec("exaile -a");
}
function pause() {
jvclass.exec("exaile -t");
}
function volup() {
jvclass.exec("exaile -i 1");  
}
function voldown() {
jvclass.exec("exaile -l 1");   
}
```
It doesn't work it keep giving this error:
*console message: /home/stepper/exailecontrol.js @1: ReferenceError: Can't find variable: java*
How can I fix this? Its my first time dabbling in html and java & javascripts.

---

### Post by kaivalagi on 2009-03-01
@stepper

Nice attempt, looking good :)

This is not my strong point...it's been a while since I did anything from the ground up with javascript

I didn't think you could call java functions from within javascript though...there are not the same thing...I am probably wrong though

This may help: [http://www.mozilla.org/rhino/shell.html](http://www.mozilla.org/rhino/shell.html) - have a look at the runCommand section.

Post back anything you find out and I'll try and help where I can

@Hippy - have you played around with this sort of thing yet?

---

### Post by kaivalagi on 2009-03-01
> **Gnounc said:**
> thankya

Just had another crack at getting the custom icons for buddies and hit a brick wall.

Techy explanation: I can retrieve the id for the custom image for the image store, but the image store doesn't have methods implemented on the dbus service...I would need to modify the dbus interface code in pidgin to get it working and apparently according to the guys on #pidgin that is a little bit messy.

Long and short of it, no custom buddy icon retrieval until the pidgin purplelibs are updated - whether I do the update or not. I going to take a look at the C code but no promises...

---

### Post by Bruce M. on 2009-03-01
> **HippyRandall said:**
> as usual, Bruce, some stellar work there.:popcorn:

CHIMO
Hippy

Why thank you Hippy. I try.
I'm finding this app like conky - it's just never done.  :)

And of course I have to check out the other options that I do use and just maybe start using some I don't as of yet.

> **paulus4605 said:**
> Bruce 
I have to agree with Hippy You did a great job again 
as usual

:popcorn::popcorn::popcorn:

{must get back to the drawing board}

And a thank you to you too.

I've seen some of your stuff and you're very creative as well.

> **paulus4605 said:**
> Bruce
another question how did you get that darn creative card working under ubuntu?

mine doesn't like me and tells me to create sound myself,
I can tell you that my wife doesn't like these sounds :lolflag:
and the little sandman even less since I get into bed way past my bedtime 

Paul

Shhhhhhhhhhhhh, don't tell anyone, it's here but I haven't plugged it in yet. I only have a cheapy set of speakers that wouldn't do the card justice. However I do have a birthday coming ... and my wife would benifit with it with all her flash games. I'll have to start feeding my wallet's secret section.  :)

CHIMO! guys ):P
Bruce

---

### Post by Gnounc on 2009-03-01
Sweet deal, thanks again.

I am trying to learn to make an applet for gnome panel for pidgin myself but I have no programming experience. Turns out I need to learn pidgins DBUS, Python, and then how to get it into the gnome panel im not sure?

It looks like I need to use glade maybe? The information is so spread out.

Anyways not my point, my point is I ran acrossed 

THIS  [http://unpythonic.blogspot.com/2007/11/desktop-widgets-with-pygtk-launchpad.html](http://unpythonic.blogspot.com/2007/11/desktop-widgets-with-pygtk-launchpad.html)

and I think it might help you with your desktop wallpaper
problems.

---

### Post by kaivalagi on 2009-03-01
> **Gnounc said:**
> Sweet deal, thanks again.

I am trying to learn to make an applet for gnome panel for pidgin myself but I have no programming experience. Turns out I need to learn pidgins DBUS, Python, and then how to get it into the gnome panel im not sure?

It looks like I need to use glade maybe? The information is so spread out.

Anyways not my point, my point is I ran acrossed 

THIS  [http://unpythonic.blogspot.com/2007/11/desktop-widgets-with-pygtk-launchpad.html](http://unpythonic.blogspot.com/2007/11/desktop-widgets-with-pygtk-launchpad.html)

and I think it might help you with your desktop wallpaper
problems.

Thanks for the link, I'll take a look

Take a look at the d-feet app in the repos, it shows all the methods available on dbus services in the system, very handy :)

---

### Post by xeddog on 2009-03-01
Hi there.

Been having a couple of Honey Do days so I haven't been able to do much.  I did manage to butcher the [excrement] out of BruceM's weather template.  I like to see all of the available info so I have just added all of the stuff that wasn't there before and rearranged some stuff.  Actually I made two templates.  I suppose I could have put all of this into a single template but it seemed easier this way.  

Anyway, the only thing I have left to do is figure out the transparent background stuff.  As I mentioned, I have had a couple of honey do days so I have not been able to try kaivalagi's suggestion yet.  I'll get to it soon.

xeddog

P.S.  This is the first time I have tried to include a screenshot so I hope it works.

---

### Post by paulus4605 on 2009-03-01
xeddog 

great job

Paul

---

### Post by Bruce M. on 2009-03-02
> **xeddog said:**
>  I did manage to butcher the [excrement] out of BruceM's weather template.

**Xeddog: YOU ROCK!**

Butcher away, my friend, butcher away.

But please; share the template.

Have a nice day.
Bruce

---

### Post by paulus4605 on 2009-03-02
Bruce

I Have another one for you 

{see Bruce running back to the drawingboard hanging out the "do not disturb" sign}

{WORK IN PROGRESS}


hope you like it

---

### Post by HippyRandall on 2009-03-02
> **kaivalagi said:**
> @Hippy - have you played around with this sort of thing yet?
no my lazy "point-and-click-and-it-should-just-work" attitude got the best of me and I never tried anything.
seeing some nice work on the templates guys. keep it up! I have an idea for a new layout, I just need to find the ambition to try coding it.

Hippy

---

### Post by paulus4605 on 2009-03-02
> **HippyRandall said:**
> no my lazy "point-and-click-and-it-should-just-work" attitude .
Hippy

Hippy Don't worry I try to do that to however sometimes I have to steel-click-copy-paste Whoops did I just day that :P   

but seriously I mean look at existing template figure out a new one template and modify it, so thats how the above template was born today.


so impatiently waiting till your template comes out in order to see how I copy-paste-mix-delete-modify your version into a newborn 

Paul

---

### Post by kaivalagi on 2009-03-02
**[SIZE="4"][COLOR="Green"]UPDATE[/COLOR][/SIZE]**

I've updated the app, it should be available via apt shortly.

gtk-desktop-info changes: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.10_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.10_source.changes)

gtk-desktop-info-data changes: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.06_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.06_source.changes)

I jumped one version with the data package by mistake, not that it really matters...(obviously vigorous internal testing required much more work and a newer version...)

---

### Post by xeddog on 2009-03-02
OK, the way my weather template works is that I have two of them and I run gtk-desktop-info twice.  Once for all of the weather data itself, and once for the weather map on the right.  I do that so I can easily stop displaying the weather map if I choose to.  And I probably will choose to because in the late spring, summer, and early fall it will never change.  BOOOOORING!

The attached file contains the commands, CSS, and the template.  My screen resolution is 2560x1024 (1280x1024 times two) so you may need to adjust your placement (among other things).  On my setup, it occupies the bottom part of the left screen only.


xeddog

---

### Post by kaivalagi on 2009-03-02
Thanks for the files xeddog :popcorn:

---

### Post by xeddog on 2009-03-02
Gotta stop rushing myself.  I forgot the weather map template, but it is simple enough.


```
<table cellpadding="0" cellspacing="0" border="0" bordercolor="white" >
<tr>	
		<td ><img src="[--datatype=WM]" width="500" /> </td>
</tr>
</table>
```


xeddog

---

### Post by paulus4605 on 2009-03-03
kaivalagi

thanks for the update 
we have again a translation problem with the moonphases the waxing crescent is not translated 

Paul

---

### Post by kaivalagi on 2009-03-03
> **paulus4605 said:**
> kaivalagi

thanks for the update 
we have again a translation problem with the moonphases the waxing crescent is not translated 

Paul

Send me the corrected mo and po file...I thought it was sorted...

---

### Post by paulus4605 on 2009-03-03
well thats the problem

when I check the files I see the correct translation 

I tried to open the mo file however it doesn't allow me to 

Paul

---

### Post by kaivalagi on 2009-03-03
> **paulus4605 said:**
> well thats the problem

when I check the files I see the correct translation 

I tried to open the mo file however it doesn't allow me to 

Paul

The mo file is a binary, you can't open it. It is created from the po file when you save it in poedit...if both datetimes almost match up then what the po file says is what should be happening...

---

### Post by paulus4605 on 2009-03-03
Ok 
does forecast lock the po file while its running or while the update is running in the background?

cause mine was running at this point 

Paul

---

### Post by kaivalagi on 2009-03-03
> **paulus4605 said:**
> Ok 
does forecast lock the po file while its running or while the update is running in the background?

cause mine was running at this point 

Paul

The files would have got updated.

The translations from a previous mo file may well be cached though. When the data gets refreshed (force it using --refetch) you should see the expected output.

---

### Post by paulus4605 on 2009-03-03
K
even removed and reinstalled everything no change 

Paul

---

### Post by kaivalagi on 2009-03-03
> **paulus4605 said:**
> K
even removed and reinstalled everything no change 

Paul

Paul,

Can you do me a favour please:

[LIST=1]
[*]copy the .po file in /usr/share/gtk-desktop-info/locale/nl/LC_MESSAGES/ to ~/
[*]open it in poedit then save
[*]copy both the .po and .mo from ~/ back into the original location
[*]run the app again
[/LIST]

I think the .mo file wasn't updated along with the .po...

If that is the case I'll go through all translations and make sure they're updated for the next release

edit: I am also certain this will resolve the issue, the dutch translation is the only one with a mis-matched po and mo file. Sorry, my bad...

---

### Post by paulus4605 on 2009-03-03
Kaivalagi

this solved the problem

another question When you have in the "CT" part things like AM fog/pm wind how is this translated or is it impossible to translate these since weather.com is pushing this differently then all the other weather texts?


Paul

---

### Post by kaivalagi on 2009-03-03
> **paulus4605 said:**
> Kaivalagi

this solved the problem

another question When you have in the "CT" part things like AM fog/pm wind how is this translated or is it impossible to translate these since weather.com is pushing this differently then all the other weather texts?


Paul

CT was never covered with the translations because we dont know what it will be all the time. If we started translating it, we would always be playing catch up IMHO

I have actually been thinking for some time that I should remove this option altogether from the forecast plugin/conkyForecast scripts as it is not that necessary and causes issues for translations.

I can confirm translations if there should convert the text for you, the below in red does that job:

```
            elif datatype == "CT":
                output = **[COLOR="Red"]_([/COLOR]**set.condition_text**[COLOR="Red"])[/COLOR]**
```

By all means update your own .po file for the translation of this data. If it works out then I might consider updating the .pot file for all translators to base new translations on or update existing ones (painfully). You may however get to the point where you are fed up needing to add more and more translations to handle it...or...you may get to a point where all is covered off (for now :) )

I am not so keen...personally I think we should remove the CT option and every one uses CC, I just haven't got to a clear decision on it yet...if you do want to try translating for CT then give me feedback on how it's going and we can make a sensible decision on keeping CT and new translations or removed CT altogether...maybe

---

### Post by xeddog on 2009-03-03
kaivalagi - regarding my transparent background problem, I finally got around to using the gtk-desktop-info.py program you provided.  The first time I used it, I looked at the log file and there were a few things in there, but they all ended with a message that said something like problems with interlaced .png files.   So I tried to re-create a new transparent png without interlace.  Now when I run the program there are NO messages at all either in the log file, or on the terminal window.  But the background is still black.  I think I might just be creating the png file incorrecly so maybe I will work on that.  

BruceM - I think I remember that you created one too, is that correct?  If so, could you make that available?

Just for ducks, I also tried simply removing the --wallpaper option from the command line and got this:

```
twoblues@Stealth:~/gtk-desk$ ./mydesktop.sh
twoblues@Stealth:~/gtk-desk$ 2009-03-03 13:55:27,472 - gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 195, in generateBackground
    img = Image.open(wallpaper)
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 1917, in open
    raise IOError("cannot identify image file")
IOError: cannot identify image file

twoblues@Stealth:~/gtk-desk$ Window moved to 900,674
```

So apparently gtk-desktop-info cannot find the wallpaper path??

Can't do much more today or tomorow.  I have a lot of the "g" words to do.  Words like garbage (collect it which includes yard waste this week, and take it out), groceries (go get them and get them all put away), garage (as in straightening up after the mess I made a few days ago), and Grand Daughter(5th birthday tomorrow).  And a few others too.

xeddog

---

### Post by kaivalagi on 2009-03-03
> **xeddog said:**
> kaivalagi - regarding my transparent background problem, I finally got around to using the gtk-desktop-info.py program you provided.  The first time I used it, I looked at the log file and there were a few things in there, but they all ended with a message that said something like problems with interlaced .png files.   So I tried to re-create a new transparent png without interlace.  Now when I run the program there are NO messages at all either in the log file, or on the terminal window.  But the background is still black.  I think I might just be creating the png file incorrecly so maybe I will work on that.  

BruceM - I think I remember that you created one too, is that correct?  If so, could you make that available?

Just for ducks, I also tried simply removing the --wallpaper option from the command line and got this:

```
twoblues@Stealth:~/gtk-desk$ ./mydesktop.sh
twoblues@Stealth:~/gtk-desk$ 2009-03-03 13:55:27,472 - gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 195, in generateBackground
    img = Image.open(wallpaper)
  File "/usr/lib/python2.5/site-packages/PIL/Image.py", line 1917, in open
    raise IOError("cannot identify image file")
IOError: cannot identify image file

twoblues@Stealth:~/gtk-desk$ Window moved to 900,674
```

So apparently gtk-desktop-info cannot find the wallpaper path??

Can't do much more today or tomorow.  I have a lot of the "g" words to do.  Words like garbage (collect it which includes yard waste this week, and take it out), groceries (go get them and get them all put away), garage (as in straightening up after the mess I made a few days ago), and Grand Daughter(5th birthday tomorrow).  And a few others too.

xeddog

The background by default is white, so getting black means something has happened I think

Looks like I need to tidy up error handling a little...

If you removed the --wallpaper option it will default to gnome based wallpaper, unless you define a --windowmanager option for something else.

Are you running gnome? And are you using gnomes wallpaper support?

I really shouldn't be this difficult, post some details on your screen res, window manager etc and we can get a test wallpaper together or direct you to use some other options. Either way if we get an example command line call for the app sorted and working on your PC that will be a beginning

[COLOR="Navy"]edit: noticed you have posted info on screen res etc, what window manager are you running? I am using jpg format images for the backgrounds right now...have you trying using that format yet?[/COLOR]

---

### Post by paulus4605 on 2009-03-04
Kaivalagi, 
if CT is depreciated I would vote to delete it from the coding and use CC instead. 

but thats just my humble opinion 

**Bruce what do you think?**

Paul

---

### Post by paulus4605 on 2009-03-04
Kaivalagi, 

little question how do you change the windspeed from kpu to Beaufort?

must be reading over it and can't figure it out

Paul

---

### Post by kaivalagi on 2009-03-04
> **paulus4605 said:**
> Kaivalagi, 

little question how do you change the windspeed from kpu to Beaufort?

must be reading over it and can't figure it out

Paul

Use the additional --beaufort option inside the template for your wind speed requests

---

### Post by paulus4605 on 2009-03-04
kaivalagi thanks I was trying things like --BF but that didn't work

---

### Post by Bruce M. on 2009-03-04
> **paulus4605 said:**
> Kaivalagi, 
if CT is depreciated I would vote to delete it from the coding and use CC instead. 

but thats just my humble opinion 

**Bruce what do you think?**

Paul

If CT is depreciated, and it causing headaches for translation - **ditch it!**

Like you, my humble opinion.

What say you K!

have a nice day.
Bruce

---

### Post by kaivalagi on 2009-03-04
> **Bruce M. said:**
> If CT is depreciated, and it causing headaches for translation - **ditch it!**

Like you, my humble opinion.

What say you K!

have a nice day.
Bruce

That's 3 votes (incl me) to ditch it so I will

I'll keep the CT datatype option though, and have it work as CC already does. That way no templates etc will break

---

### Post by Bruce M. on 2009-03-04
> **kaivalagi said:**
> That's 3 votes (incl me) to ditch it so I will

Yea - 3
Nea - 0
No vote: 22,486,157,512

The yea's have it.

> **kaivalagi said:**
> I'll keep the CT datatype option though, and have it work as CC already does. That way no templates etc will break

Oh good call. However may I suggest you strip it out of the "list" of datatype options available. That way new users will use CC automatically even though CT would work for them. You don't even need to have a new version for it, people will never notice.  :)

Unless of course we have crazy people like Paulus and myself that didn't read the instructions and try "CT" for something else, like we tried to use "BF". Yea, Paul, you read that right, I did the same when it was first implemented, as a test, in conkyforecast. :biggrin:

CHIMO!
Bruce

---

### Post by stepper on 2009-03-04
I'm trying to run the forecast plugin and all it gives me is this code...> Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 388, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 107, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 147, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1457, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1289, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1238, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1194, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1081, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 971, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

What am I doing wrong?

---

### Post by kaivalagi on 2009-03-04
> **stepper said:**
> I'm trying to run the forecast plugin and all it gives me is this code...
What am I doing wrong?

I dont know what you are doing wrong unless you tell me what you are doing to run the forecast plugin :) Can you tell me the command line you are executing?

Also can you run the app with the --verbose option added and paste the output from that please? That might help me understand what is wrong...

I am running python 2.5 like you so I am unsure why you have an issue and I don't...

---

### Post by xeddog on 2009-03-04
kaivalagi - 

Thanks for the reply.  regarding your questions, etc. :
> If you removed the --wallpaper option it will default to gnome based wallpaper, unless you define a --windowmanager option for something else.

Are you running gnome? And are you using gnomes wallpaper support?

I have tried both with and without the the --wallpaper option, and both with and without the --windowmanager option, and in all combinations.  For the windowmanager I have tried gnome, kde3, and kde4.  The reason that I tried the kdex options is because I remembered that at one point I was thinking it might be fun to be able to switch back and forth between gnome and kde, so I used apt and installed the kde desktop.  Never have used it though.  But none of the --windowmanager options seem to make any diff.

I am running gnome, and as for the gnome wallpaper support . . .uh . . .wut???  And the window manager being used is whatever the UBUNTU install put there (not Kubuntu or Xubuntu or ...).  There is one thing.  I am using xml-wall (obtained elsewhere on this forum) to change my desktop wallpaper.  This is a shell script that creates an xml file containing all of the info needed about each wallpaper that I want to use.  I do not know the method used to actually change the wallpaper.

My command line looks like this (for now):
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 2

gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=/home/twoblues/gtk-desk/green.css  --windowmanager=gnome --wallpaper=/home/twoblues/gtk-desk/TB6.png  --windowmanager=gnome --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/home/twoblues/gtk-desk/test3play.template --noheader  --plugin=forecast --config=/home/twoblues/gtk-desk/plugin_forecast.config &
```

this gives me a black background, but I  THINK TB6.png should be nothing more than a transparent background.  But it could easily be that I have not created it properly.  If I remember correctly, I used OpenOffice Draw (the 3.01 version on Winders) to create it.  I am using png at the moment, but I have also tried gif too.  I have used those two because I read on the Internet that gif supports transparent backgrounds and jpg does not.  When I read that, I tried a few different variations on creating a gif image.  Then I read on this thread (don't remember who said it.  You???) that png also supports transparent background so I tried a few png's.  I have not tried jpg but what have I got to lose?  :-(

Sorry to be such a pita on this, but if I can get a transparent background I'll be a REAL happy camper.  For a while.  :-)

TIA,

xeddog

---

### Post by akahige on 2009-03-04
So I've been catching up on all the gtk desktop goodness, having been teased about its rumored existence months back in the conky thread. Having read all 28 pages of this thread, and gone through the config doc referenced in the first post, I'm curious about something I haven't seen anyone do yet...

Can gtk dt do (or will it at some point be able to do) graphing functions like conky's cpugraph or downspeedgraph? The only thing that I've seen show up in any of the config screenshots is horizontal bar graphs.

Keep up the good work!

---

### Post by kaivalagi on 2009-03-05
> **xeddog said:**
> kaivalagi - 

Thanks for the reply.  regarding your questions, etc. :


I have tried both with and without the the --wallpaper option, and both with and without the --windowmanager option, and in all combinations.  For the windowmanager I have tried gnome, kde3, and kde4.  The reason that I tried the kdex options is because I remembered that at one point I was thinking it might be fun to be able to switch back and forth between gnome and kde, so I used apt and installed the kde desktop.  Never have used it though.  But none of the --windowmanager options seem to make any diff.

I am running gnome, and as for the gnome wallpaper support . . .uh . . .wut???  And the window manager being used is whatever the UBUNTU install put there (not Kubuntu or Xubuntu or ...).  There is one thing.  I am using xml-wall (obtained elsewhere on this forum) to change my desktop wallpaper.  This is a shell script that creates an xml file containing all of the info needed about each wallpaper that I want to use.  I do not know the method used to actually change the wallpaper.

My command line looks like this (for now):
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 2

gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=/home/twoblues/gtk-desk/green.css  --windowmanager=gnome --wallpaper=/home/twoblues/gtk-desk/TB6.png  --windowmanager=gnome --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/home/twoblues/gtk-desk/test3play.template --noheader  --plugin=forecast --config=/home/twoblues/gtk-desk/plugin_forecast.config &
```

this gives me a black background, but I  THINK TB6.png should be nothing more than a transparent background.  But it could easily be that I have not created it properly.  If I remember correctly, I used OpenOffice Draw (the 3.01 version on Winders) to create it.  I am using png at the moment, but I have also tried gif too.  I have used those two because I read on the Internet that gif supports transparent backgrounds and jpg does not.  When I read that, I tried a few different variations on creating a gif image.  Then I read on this thread (don't remember who said it.  You???) that png also supports transparent background so I tried a few png's.  I have not tried jpg but what have I got to lose?  :-(

Sorry to be such a pita on this, but if I can get a transparent background I'll be a REAL happy camper.  For a while.  :-)

TIA,

xeddog

What is the full resolution of your screen? I'll create a simple png background and post it for you to try. I use gimp for png creation, with default settings on save.

It does sound like that app you are using is causing the issues, as it will put the desktop wallpaper in place in it's own way and not define the setting in the normal gnome gconf config location.

Take a look at this wallpaper randomiser ([http://ubuntuforums.org/showthread.php?t=888746](http://ubuntuforums.org/showthread.php?t=888746)), this sets the wallpaper in the correct way so you shouldn't need to use the --wallpaper or --windowmanager options at all...the random function isn't working right now by default but I did post a quick solution to this problem on the thread...

---

### Post by kaivalagi on 2009-03-05
> **akahige said:**
> So I've been catching up on all the gtk desktop goodness, having been teased about its rumored existence months back in the conky thread. Having read all 28 pages of this thread, and gone through the config doc referenced in the first post, I'm curious about something I haven't seen anyone do yet...

Can gtk dt do (or will it at some point be able to do) graphing functions like conky's cpugraph or downspeedgraph? The only thing that I've seen show up in any of the config screenshots is horizontal bar graphs.

Keep up the good work!

No graphing functions sorry, I haven't come up with a solution for this at all yet. It is quite nasty to sort out especially via html...needs a javascript function and data history over the refresh interval which wont fit well with the current app structure.

I am open to suggestions on the technical front...

---

### Post by paulus4605 on 2009-03-05
> **kaivalagi said:**
> No graphing functions sorry, I haven't come up with a solution for this at all yet. It is quite nasty to sort out especially via html...needs a javascript function and data history over the refresh interval which wont fit well with the current app structure.

I am open to suggestions on the technical front...

should at this point php be an option to consider?

---

### Post by kaivalagi on 2009-03-05
> **paulus4605 said:**
> should at this point php be an option to consider?

Not really, the app is already a "server-side" thing which spits out html on a regular basis.

At the mo the app just gets new data per interval and replaces the existing data. What we need is a way for the app to keep state from previously so a graph based output can be achieved. Data in the app, drawing stuff in javascript maybe...

It's not going to happen any time soon, unless someone else wants to take on the challenge

---

### Post by sanus|art on 2009-03-05
Great addition to the desktop, really nice idea to parse HTML instead of custom markup, question though:
Does web-kit hates jQuery (or any functionality of it)?  

```
<div style="font:normal 18px 'verdana';color:#fff;border-bottom:1px dotted #ccc;letter-spacing:-2px;"><a href="" id="toggle_cal">CAL<b>ENDAR</b></a></div>
<div id="cal" style="font:normal 10px 'mono';color:#ccc;letter-spacing:0px;">[cal]</div>
<script type="text/javascript">
$("a#toggle_cal").click(function(){$("#cal").slideToggle(500); return false;});
</script>
```The slideToggle function seems to be "jumping" (sliding up, but sliding back down right away) upon triggering.

---

### Post by paulus4605 on 2009-03-05
kaivalagi,
I know I know I am a pain in the .....   

I have now beaufort as windspeed and that is working like a charm.

is it possible to give the text as well or is that over the top?

Paul

---

### Post by stepper on 2009-03-05
> **kaivalagi said:**
> I dont know what you are doing wrong unless you tell me what you are doing to run the forecast plugin :) Can you tell me the command line you are executing?

Also can you run the app with the --verbose option added and paste the output from that please? That might help me understand what is wrong...

I am running python 2.5 like you so I am unsure why you have an issue and I don't...
> stepper@desktop:~$ gtk-desktop-info --verbose --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=740 --height=350 --x=0 --y=750 --template=/home/stepper/forecasttemplate --noheader --plugin=forecast --css=/home/stepper/forecast.css & 
[2] 23574
[1]   Exit 1                  gtk-desktop-info --verbose --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=740 --height=350 --x=0 --y=750 --template=/home/stepper/forecasttemplate --noheader --plugin=forecast
stepper@desktop:~$ *** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: /home/stepper/forecast.css
    interval: 1800
    width: 740
    height: 350
    x: 0
    y: 750
    verbose: True
    logfile: /tmp/gtk-desktop-info.log
/usr/share/themes/MurrinaBleu/gtk-2.0/gtkrc:85: Murrine configuration option "hilight_ratio" will be deprecated in future releases. Please update this theme to get rid of this warning.
2009-03-05 17:33:24,872 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_f76dda3c-099a-11de-a238-0014852b516c.jpg
2009-03-05 17:33:24,992 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/stepper/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-05 17:33:24,994 - gtk-desktop-info.plugin_forecast - INFO - Locale set to en
2009-03-05 17:33:24,995 - gtk-desktop-info.plugin_forecast - INFO - Using custom header template file '/usr/share/gtk-desktop-info/templates/nullheader.template'
2009-03-05 17:33:24,996 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/home/stepper/forecasttemplate'
2009-03-05 17:33:24,997 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-UKXX0103.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 388, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 107, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 147, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1457, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1289, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1238, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1194, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1081, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 971, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

css and template files I got from this thread.

---

### Post by kaivalagi on 2009-03-05
Strange...can you tell me what this outputs in the terminal:

```
locale
```

Mine gives me:

```
LANG=en_GB.UTF-8
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC="en_GB.UTF-8"
LC_TIME="en_GB.UTF-8"
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY="en_GB.UTF-8"
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER="en_GB.UTF-8"
LC_NAME="en_GB.UTF-8"
LC_ADDRESS="en_GB.UTF-8"
LC_TELEPHONE="en_GB.UTF-8"
LC_MEASUREMENT="en_GB.UTF-8"
LC_IDENTIFICATION="en_GB.UTF-8"
LC_ALL=

```

I am wondering whether your system locales could be causing issues....

I am lost for answers, and I can't reproduce the problem ](*,)
[B]
Has anybody had this error before and knows the cause of it???[/B]

---

### Post by HippyRandall on 2009-03-06
> **sanus|art said:**
> Great addition to the desktop, really nice idea to parse HTML instead of custom markup, question though:
Does web-kit hates jQuery (or any functionality of it)?  

```
<div style="font:normal 18px 'verdana';color:#fff;border-bottom:1px dotted #ccc;letter-spacing:-2px;"><a href="" id="toggle_cal">CAL<b>ENDAR</b></a></div>
<div id="cal" style="font:normal 10px 'mono';color:#ccc;letter-spacing:0px;">[cal]</div>
<script type="text/javascript">
$("a#toggle_cal").click(function(){$("#cal").slideToggle(500); return false;});
</script>
```The slideToggle function seems to be "jumping" (sliding up, but sliding back down right away) upon triggering.
hmm crap I hope this isn't as fatal as it sounds. I have a couple ideas using JQuery I was hoping to implement. My laptop sorta crashed today so I can't promise to look into it right away but I am sure I will check it out before the end of the weekend

Hippy

[COLOR=Blue]Edit: I ran this: [http://jquery.com/test/](http://jquery.com/test/) in a gtk-desktop-info window and it did not throw any errors. More checking will be done soon.[/COLOR]

---

### Post by sanus|art on 2009-03-06
No, no worries, It is my fault - could've investigate the issue a bit more. The jumping is caused by the refresh rate "--interval=NUM" in the SH file, exam this by changing the default "--interval=1" to "--interval=20" for example. So all good.

---

### Post by zet120 on 2009-03-06
Hmmmm, I have the same error as **stepper**
```

zet120@zet120-desktop:~$ gtk-desktop-info --verbose --css=/home/zet120/Pulpit/cf/green.css  --wallpaper=/home/zet120/wallpaper/warriorz.jpg --logfile=/tmp/gtk-desktop-info1.log --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/home/zet120/Pulpit/cf/test3play.template --noheader  --plugin=forecast --config=/home/zet120/.config/gtk-desktop-info/plugin_forecast.config &
[2] 10877
[1]   Exit 1                  gtk-desktop-info --verbose --css=/home/zet120/Pulpit/cf/green.css --wallpaper=/home/zet120/wallpaper/warriorz.jpg --logfile=/tmp/gtk-desktop-info1.log --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/home/zet120/Pulpit/cf/test3play.template --noheader --plugin=forecast --config=/home/zet120/.config/gtk-desktop-info/plugin_forecast.config
zet120@zet120-desktop:~$ *** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: /home/zet120/Pulpit/cf/green.css
    interval: 300
    width: 905
    height: 350
    x: 0
    y: 674
    verbose: True
    logfile: /tmp/gtk-desktop-info1.log

2009-03-06 20:51:13,360 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_25c88952-0a88-11de-a3e0-00221591a554.jpg
2009-03-06 20:51:13,374 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/zet120/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-06 20:51:13,374 - gtk-desktop-info.plugin_forecast - INFO - Locale set to pl
2009-03-06 20:51:13,375 - gtk-desktop-info.plugin_forecast - INFO - Looking for translation file for 'pl' under /usr/share/gtk-desktop-info/locale
2009-03-06 20:51:13,375 - gtk-desktop-info.plugin_forecast - INFO - Translation file found for 'pl'
2009-03-06 20:51:13,376 - gtk-desktop-info.plugin_forecast - INFO - Translation installed for 'pl'
2009-03-06 20:51:13,376 - gtk-desktop-info.plugin_forecast - INFO - Using custom header template file '/usr/share/gtk-desktop-info/templates/nullheader.template'
2009-03-06 20:51:13,377 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/home/zet120/Pulpit/cf/test3play.template'
2009-03-06 20:51:13,377 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-PLXX0060.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 382, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 106, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 146, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1457, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1289, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1238, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1194, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1091, in getDatasetOutput
    self.logger.error("--startday set beyond forecast limit, reset to maximum of " + self.config.MAXIMUM_DAYS_FORECAST)
TypeError: cannot concatenate 'str' and 'int' objects


```

```

locale
```
```

zet120@zet120-desktop:~$ locale
LANG=pl_PL.UTF-8
LC_CTYPE="pl_PL.UTF-8"
LC_NUMERIC="pl_PL.UTF-8"
LC_TIME="pl_PL.UTF-8"
LC_COLLATE="pl_PL.UTF-8"
LC_MONETARY="pl_PL.UTF-8"
LC_MESSAGES="pl_PL.UTF-8"
LC_PAPER="pl_PL.UTF-8"
LC_NAME="pl_PL.UTF-8"
LC_ADDRESS="pl_PL.UTF-8"
LC_TELEPHONE="pl_PL.UTF-8"
LC_MEASUREMENT="pl_PL.UTF-8"
LC_IDENTIFICATION="pl_PL.UTF-8"
LC_ALL=

```
css and template files I got from **xeddog**, post NR:250

---

### Post by kaivalagi on 2009-03-06
You have a different error, you have tried to use more forecast days than are supported according to the error log.

The maximum forecast days available for a normal registration is 4, i.e. --startday or --endday can't be set higher than 4.

The error handling isn't quite right as it's erroring when trying to output the message, but the fact that the code is trying to output that message is enough to know.

I'll take a look at the template you are using...
[COLOR="Blue"]
Edit: Yep, xeddog is using a template which goes up to 7 days forecast, this isn't supported by default because of the standard registration only providing 4 days of forecast. I assume the forecast works if you use the default template and css (i.e. don't set them on the command line)? If you want to use xeddog's template you'll need to find a registration key which gives more forecast info...maybe PM xeddog as I assume it isn't something that should be made public?

@stepper, if you use the default template and css does the app work for you too? If so the template xeddog has provided is what is the issue and what I've mentioned above applies to you too[/COLOR]

---

### Post by xeddog on 2009-03-06
I am making progress with my transparent background "problem", but I think I might be screwed.  I was using xml-wall to change my wallpapers so I used synaptic and removed it.  Still did not get my transparent background.  Next, I went to a website that had a few trillion gnome wallpapers and downloaded one (and made it my wallpaper).  Walla.  Transparent background.  Sorta.

The problem is that the wallpapers are only as wide as one screen.  Both of my screens are running at 1280x1024, but with "bigdesktop" the workspace is 2560x1024.  That means that the wallpaper is plastered in the middle with 1/2 of the wallpaper on the left screen, and 1/2 on the right screen.  Then, there is a big border on the left side of the left screen, and the right side of the right screen.  So gtk-desktop-info crops a part of the wallpaper and uses it, but it starts at the left edge of the left screen and a good 1/3 of the display is over the large border on the left side of my wallpaper.  I was going to include a screenshot of the whole workspace but the file size was a tad to big.

So if I was going to make me a wallpaper image that was only a transparent background, it would have to be 2560x1024.  I didn't think I would need that much so I didn't try making one that big.  

That leads me to another question.  What makes a wallpaper gnome compatible?  Size?  Format?  Resolution?  All of the above???

TIA,

xeddog

---

### Post by kaivalagi on 2009-03-06
> **xeddog said:**
> I am making progress with my transparent background "problem", but I think I might be screwed.  I was using xml-wall to change my wallpapers so I used synaptic and removed it.  Still did not get my transparent background.  Next, I went to a website that had a few trillion gnome wallpapers and downloaded one (and made it my wallpaper).  Walla.  Transparent background.  Sorta.

The problem is that the wallpapers are only as wide as one screen.  Both of my screens are running at 1280x1024, but with "bigdesktop" the workspace is 2560x1024.  That means that the wallpaper is plastered in the middle with 1/2 of the wallpaper on the left screen, and 1/2 on the right screen.  Then, there is a big border on the left side of the left screen, and the right side of the right screen.  So gtk-desktop-info crops a part of the wallpaper and uses it, but it starts at the left edge of the left screen and a good 1/3 of the display is over the large border on the left side of my wallpaper.  I was going to include a screenshot of the whole workspace but the file size was a tad to big.

So if I was going to make me a wallpaper image that was only a transparent background, it would have to be 2560x1024.  I didn't think I would need that much so I didn't try making one that big.  

That leads me to another question.  What makes a wallpaper gnome compatible?  Size?  Format?  Resolution?  All of the above???

TIA,

xeddog

Either use a wallpaper the same size as the resolution or if not set it to fill the screen.

It is assumed that the wallpaper will either be the whole screen res or become stretched to cover the screen res.

I tried getting the screen captured however the settings as a full res wallpaper 'cause then all would be fine, however the xserver libs don't support this...

---

### Post by zet120 on 2009-03-07
Running default template and css :(
```

zet120@zet120-desktop:~$ gtk-desktop-info --verbose --plugin forecast
*** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: None
    interval: 0
    width: 400
    height: 300
    x: 0
    y: 0
    verbose: True
    logfile: None
2009-03-07 07:41:11,713 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_f29e7c2a-0ae2-11de-a3e0-00221591a554.jpg
2009-03-07 07:41:11,726 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/zet120/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Locale set to pl
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Looking for translation file for 'pl' under /usr/share/gtk-desktop-info/locale
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Translation file found for 'pl'
2009-03-07 07:41:11,732 - gtk-desktop-info.plugin_forecast - INFO - Translation installed for 'pl'
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Using default header template
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/usr/share/gtk-desktop-info/templates/forecast.template'
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-PLXX0060.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 382, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 106, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 146, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1457, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1289, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1238, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1194, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1081, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 971, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

```

---

### Post by HippyRandall on 2009-03-07
> **sanus|art said:**
> No, no worries, It is my fault - could've investigate the issue a bit more. The jumping is caused by the refresh rate "--interval=NUM" in the SH file, exam this by changing the default "--interval=1" to "--interval=20" for example. So all good.
Can I ask how you got the jquery script into the app? did you have to edit the py file or something?

---

### Post by kaivalagi on 2009-03-07
> **zet120 said:**
> Running default template and css :(
```

zet120@zet120-desktop:~$ gtk-desktop-info --verbose --plugin forecast
*** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: None
    interval: 0
    width: 400
    height: 300
    x: 0
    y: 0
    verbose: True
    logfile: None
2009-03-07 07:41:11,713 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_f29e7c2a-0ae2-11de-a3e0-00221591a554.jpg
2009-03-07 07:41:11,726 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/zet120/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Locale set to pl
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Looking for translation file for 'pl' under /usr/share/gtk-desktop-info/locale
2009-03-07 07:41:11,731 - gtk-desktop-info.plugin_forecast - INFO - Translation file found for 'pl'
2009-03-07 07:41:11,732 - gtk-desktop-info.plugin_forecast - INFO - Translation installed for 'pl'
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Using default header template
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/usr/share/gtk-desktop-info/templates/forecast.template'
2009-03-07 07:41:11,733 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-PLXX0060.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 382, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 106, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 146, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1457, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1289, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1238, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1194, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1081, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 971, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

```

Can you delete your .cache file and run it again, clutching at straws here

I really don't know why this is happening, I'll need to try and reproduce the problem myself if I have any hope of fixing it.

Can you post the config here so I can try to reproduce:
/home/mark/.config/gtk-desktop-info/plugin_forecast.config

---

### Post by zet120 on 2009-03-07
The larger problem. 
Now I'm at work and tested on a laptop, the result of the same.
```

zet120@zet120-[color=red]laptop:~$[/color] gtk-desktop-info --verbose --plugin forecast
....
ValueError: unconverted data remains: AM


```

**kaivalagi** if you have the time of the evening to share the remote desktop (SSH and / or GUI)

---

### Post by kaivalagi on 2009-03-07
> **zet120 said:**
> The larger problem. 
Now I'm at work and tested on a laptop, the result of the same.
```

zet120@zet120-[color=red]laptop:~$[/color] gtk-desktop-info --verbose --plugin forecast
....
ValueError: unconverted data remains: AM


```

**kaivalagi** if you have the time of the evening to share the remote desktop (SSH and / or GUI)

I'm at a Fiji day fund raiser tonight, and I'll be feeling it tomorrow..so remoting in will be an issue

Can you run the attached modified version of the forecast plugin, just swap it out in the /usr/share/gtk-desktop-info folder

It will print the following info around the problem area of code...

```
***** set.sunrise:6:27 AM
***** config.TIMEFORMAT:%H:%M

```

I am starting to think it might be an alternative format of sunrise time you get for your location code...

[COLOR="Blue"]edit: Also attached a test.py script, can you run this and post the results, probably easier then the first suggestion so try this first. Extract it and run using "python test.py". I get:

```

using sunrise data "6:18 AM"
using format data "%H:%M"
current code for formatting (2.4 compliant)...
06:18
current code for formatting (2.5 compliant)...
06:18

```

I am using the current data from weather.com and the default timeformat string...data from weather.com is like this:

```

<dayf>
<lsup>3/7/09 7:19 AM Local Time</lsup>
<day d="0" t="Saturday" dt="Mar 7">
<hi>4</hi>
<low>2</low>
<sunr>[COLOR="Red"]6:18 AM[/COLOR]</sunr>

```

ALso, what is the timeformat setting in your /home/USERNAME/.config/gtk-desktop-info/plugin_forecast.config file. I am expecting it's "TIMEFORMAT = %H:%M"


[/COLOR]

---

### Post by zet120 on 2009-03-07
**test.py**
```

zet120@zet120-desktop:~$ python /home/zet120/Pulpit/test.py 
using sunrise data "6:18 AM"
using format data "%H:%M"
current code for formatting (2.4 compliant)...
06:18
current code for formatting (2.5 compliant)...
06:18

```

plugin_forecast.config file setup with default.(without editing the file created automatically)
plugin_forecast.py or attached
```

zet120@zet120-desktop:~$ gtk-desktop-info --verbose --plugin forecast*** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: None
    interval: 0
    width: 400
    height: 300
    x: 0
    y: 0
    verbose: True
    logfile: None
2009-03-07 19:23:05,724 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_0086a80a-0b45-11de-a3e0-00221591a554.jpg
2009-03-07 19:23:05,752 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/zet120/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-07 19:23:05,753 - gtk-desktop-info.plugin_forecast - INFO - Locale set to pl
2009-03-07 19:23:05,753 - gtk-desktop-info.plugin_forecast - INFO - Looking for translation file for 'pl' under /usr/share/gtk-desktop-info/locale
2009-03-07 19:23:05,753 - gtk-desktop-info.plugin_forecast - INFO - Translation file found for 'pl'
2009-03-07 19:23:05,755 - gtk-desktop-info.plugin_forecast - INFO - Translation installed for 'pl'
2009-03-07 19:23:05,755 - gtk-desktop-info.plugin_forecast - INFO - Using default header template
2009-03-07 19:23:05,755 - gtk-desktop-info.plugin_forecast - INFO - Using default template
2009-03-07 19:23:05,755 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-UKXX0103.cache
***** set.sunrise:6:27 AM
***** config.TIMEFORMAT:%H:%M
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 388, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 107, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 147, in updateInfo
    pluginhtml = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1459, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1291, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1240, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1196, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1083, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 973, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

```

---

### Post by kaivalagi on 2009-03-07
> **zet120 said:**
> **test.py**
```

zet120@zet120-desktop:~$ ~/Pulpit/test.py 
from: can't read /var/mail/datetime
/home/zet120/Pulpit/test.py: line 2: import: polecenie nieodnalezione
/home/zet120/Pulpit/test.py: line 4: sunrise: polecenie nieodnalezione
/home/zet120/Pulpit/test.py: line 5: format: polecenie nieodnalezione
Warning: unknown mime-type for "using sunrise data "%s"%sunrise" -- using "application/octet-stream"
Error: no such file "using sunrise data "%s"%sunrise"
Warning: unknown mime-type for "using format data "%s"%format" -- using "application/octet-stream"
Error: no such file "using format data "%s"%format"
/home/zet120/Pulpit/test.py: line 10: try:: polecenie nieodnalezione
Warning: unknown mime-type for "current code for formatting (2.4 compliant)..." -- using "application/octet-stream"
Error: no such file "current code for formatting (2.4 compliant)..."
/home/zet120/Pulpit/test.py: line 12: b&#322;&#261;d sk&#322;adni w pobli&#380;u nieoczekiwanego tokenu '('
/home/zet120/Pulpit/test.py: line 12: `	srtime = datetime(*(time.strptime(sunrise, "%I:%M %p"))[0:6])'

```

Running file **plugin_forecast.py** from attached to the same error as the previous.

You need to run the test.py file like this:

```
python test.py
```

And what was the output for for sunset and time format with the replacement plugin_forecast.py? I know it won't work as I haven't fixed anything, but I wanted to know what it output as I added a couple of print statements in the code...

Also is your plugin_forecast.config file setup with default values or have you edited it? If edited please post that too.

---

### Post by xeddog on 2009-03-09
Haven't seen any new posts for a couple of days.  Is this thread dead or did y'all finally get a life and find something better to do?   :lolflag:

xeddog

---

### Post by kaivalagi on 2009-03-09
> **xeddog said:**
> Haven't seen any new posts for a couple of days.  Is this thread dead or did y'all finally get a life and find something better to do?   :lolflag:

xeddog

Very funny :)

I have a life at weekends, during the week I am a sad nerd...

---

### Post by paulus4605 on 2009-03-10
> **kaivalagi said:**
> Very funny :)

I have a life at weekends, during the week I am a sad nerd...

kaivalagi then you are blessed my friend I have a working life and when I get home my life is contains most of the time changing dipers and feeding the wife and kids. I just have a life for a couple of hours a day when I can spend some time on my computer, or I have to pay my wife to keep her eyes shut so I can play with my computer :D

Paul

---

### Post by kaivalagi on 2009-03-10
> **paulus4605 said:**
> kaivalagi then you are blessed my friend I have a working life and when I get home my life is contains most of the time changing dipers and feeding the wife and kids. I just have a life for a couple of hours a day when I can spend some time on my computer, or I have to pay my wife to keep her eyes shut so I can play with my computer :D

Paul

I feel for you, only 'cause I have been through that as well before now

Although some would argue changing diapers and cooking for the family is more of a life than sitting at a computer ;)

---

### Post by Bruce M. on 2009-03-10
> **xeddog said:**
> Haven't seen any new posts for a couple of days.  Is this thread dead or did y'all finally get a life and find something better to do?   :lolflag:

xeddog

I can't answer, I'm having a "get a life" crisis here. :D

Ohhhhhh, that is an answer.

"Huston, there is life at that keyboard!"

Have a nice life.
Bruce

---

### Post by kaivalagi on 2009-03-14
**[COLOR="DarkOrange"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Some changes fore forecast and pidgin plugins, see here for changes: [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.11_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.11_source.changes)

The apt package should be available shortly

Chimo

---

### Post by xeddog on 2009-03-15
I really have to apologize for this, but the upgraded subscription I have to weather.com was a free upgrade with a coupon code my son sent me.  He found it somewhere on the internet and told me about it.  I totally forgot about it.  Even so, the only benefits it mentions are no ads, longer radar animations, and ad-free U.S. forecasts and alerts through email.  Did not mention being able to get more that 4 days forecast.  

I think it might be expired now, but in case it isn't try this:

 [http://www.wunderground.com/members/signup.asp#benefits](http://www.wunderground.com/members/signup.asp#benefits)

And somewhere in there you can enter the coupon code BAVV5

xeddog

---

### Post by zet120 on 2009-03-16
Yes, yes, yes. 
After the recent update it works for me: 

[[IMG]http://pic.ipicture.ru/uploads/090316/thumbs/hb5pAAXfiP.png[/IMG]](http://ipicture.ru/Gallery/Viewfull/15663328.html)

The console shows errors, but I have it on my desktop. 
The problem occurs with the sunrise and sunset. 
Even a question as to how to get fonts to display characteristic of the Polish language?

P.S.
Contents of log file looks like this:
```
2009-03-16 08:08:51,215 - gtk-desktop-info - INFO - Using generated background image: /tmp/forecast_4d788970-11f9-11de-a3e0-00221591a554.jpg
2009-03-16 08:08:51,230 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/home/zet120/.config/gtk-desktop-info/plugin_forecast.config"
2009-03-16 08:08:51,230 - gtk-desktop-info.plugin_forecast - INFO - Locale set to pl
2009-03-16 08:08:51,230 - gtk-desktop-info.plugin_forecast - INFO - Looking for translation file for 'pl' under /usr/share/gtk-desktop-info/locale
2009-03-16 08:08:51,231 - gtk-desktop-info.plugin_forecast - INFO - Translation file found for 'pl'
2009-03-16 08:08:51,232 - gtk-desktop-info.plugin_forecast - INFO - Translation installed for 'pl'
2009-03-16 08:08:51,232 - gtk-desktop-info.plugin_forecast - INFO - Using custom header template file '/usr/share/gtk-desktop-info/templates/nullheader.template'
2009-03-16 08:08:51,233 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/home/zet120/Pulpit/xeddog/test3play.template'
2009-03-16 08:08:51,233 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-PLXX0021.cache
2009-03-16 08:08:51,243 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,243 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,243 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,244 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,244 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,244 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,244 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,245 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,245 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,245 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,245 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,246 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,246 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,246 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,246 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,247 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,247 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,247 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,247 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,248 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,248 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,248 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,248 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,249 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,249 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,249 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,249 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,250 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,250 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,250 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,285 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,285 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,286 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,286 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,286 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,286 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,287 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,287 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,287 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,288 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,288 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,288 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,288 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,288 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,289 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,289 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,289 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,289 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,290 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,290 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,290 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,291 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,315 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,315 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,315 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,315 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,316 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,316 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,316 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,316 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,317 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,317 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,317 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,318 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,318 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise from data using python 2.4 compliant code
2009-03-16 08:08:51,318 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,318 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,318 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,319 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 08:08:51,319 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,319 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract sunrise/sunset from data using python 2.4 compliant code
2009-03-16 08:08:51,319 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,322 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract update info from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 851, in getDatatypeFromSet
    output = self.getTimestampOutput(datetime.strptime(datetext, "%m/%d/%y %I:%M %p"), minuteshide)
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,322 - gtk-desktop-info.plugin_forecast - INFO - Attempting to extract update info from data using python 2.4 compliant code
2009-03-16 08:08:51,323 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract update info from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 856, in getDatatypeFromSet
    output = self.getTimestampOutput(datetime(*(time.strptime(datetext, "%m/%d/%y %I:%M %p"))[0:6]), minuteshide)
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 08:08:51,323 - gtk-desktop-info.plugin_forecast - ERROR - Unable to extract the Last update date from the dataset, using raw text without formatting
2009-03-16 08:08:51,326 - gtk-desktop-info - INFO - Outputting the following HTML:
<html>
<head>
<META HTTP-EQUIV='Pragma' CONTENT='no-cache'>
<link type="text/css" rel="stylesheet" media="all" href="file:///home/zet120/Pulpit/xeddog/green.css"/>
</head>
<body background="file:///tmp/forecast_4d788970-11f9-11de-a3e0-00221591a554.jpg" style="background-attachment:fixed;">
<!-- nullheader.template used, intentionally no html -->
<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
	 LT (Forecast:Low Temp,Current:Feels Like Temp),
	 HT (Forecast:High Temp,Current:Current Temp),
	 CC (Current Conditions),
	 CT (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->


<!--   Beginning of Primary Table  -->
<table cellpadding="0" cellspacing="0" border="0" bordercolor="white" >
<!--  Beginning of headline   -->
<tr align="center" border="0"> 
<td colspan="11" class="hugelight">Raport Pogodowy:  Katowice</td>  
</tr>
<!--  End ofd Headline  -->

<!--  Beginning of Pictorial Weather and Current Temp  -->
<tr>
	<td rowspan="2" align="center" valign="top"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/28.png" width="60"/></td>
	<td rowspan="2" align="center" class="hoy-cyan">2&deg;C</td>

<!--  Beginning of Top part of Current text data  -->
	<td rowspan="2" valign="bottom" align="right" >  
	<table cellpadding="2" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td align="right" class="ml-red">Dzisiaj.W.:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Dzisiaj.N:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green">Wind Chill:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
	</table>
	</td>  	
<!-- END: Top part of current text data -->


<!-- Beginning of Todays info data -->
	<td rowspan="2" valign="bottom" align="right" >
	<table cellpadding="2" cellspacing="0" border="0" valign="top" width="100" >
		<tr>
			<td class="ml-red">6&deg;C</td>
		</tr>
		<tr>
			<td class="ml-cyan">1&deg;C</td>
		</tr>
		<tr>
			<td class="ml-green">-2&deg;C</td>
		</tr>
		<tr>
			<td class="ml-yellow">0&nbsp;~&nbsp;Niskie</td>
		</tr>
	</table>
	</td>  	
<!-- END: Todays info data -->

<!-- Seven Day Outlook Headings for row 1  -->
	<td colspan="7" align="center" valign="center" class="big-yellow" width="50" > Prognoza siedmiodniowa </td>
</tr>
<!--  End of Seven Day Outlook Headings for row 1   -->

<!-- Beginning of 7 weekday names in Row 2 -->
<tr>   
	<td align="center" class="ml-wkday">Wtorek</td>
	<td align="center" class="ml-wkday">&#346;roda</td>
	<td align="center" class="ml-wkday">Czwartek</td>
	<td align="center" class="ml-wkday">Pi&#261;tek</td>
	<td align="center" class="ml-wkday">Sobota</td>
	<td align="center" class="ml-wkday">Niedziela</td>
	<td align="center" class="ml-wkday">Poniedzia&#322;ek</td>
</tr>  
<!--   end of 7 weekday names for row 2 -->

<!-- Beginning of Current Conditions  -->
<tr>
	<td rowspan="2" colspan="2" align="center" class="hugelight">&nbsp;&nbsp;Przewa&#380;nie Pochmurnie</td>
</tr>	
<!--   End of Current Conditions  -->


<!--  Beginning of Top part of Current text data  -->
	<td rowspan="2" valign="top" align="right" >  
	<table cellpadding="2" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td align="right" class="ml-red">Widocznosc:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">Wilgotnosc:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green">Punkt Rosy:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow">Cisnienie:</td>
		</tr>
		<tr>
			<td align="right" class="ml-wkday"><br><br>Deszcz %:</td>
		</tr>
	</table>
	</td>  	
<!-- END: Top part of current text data -->


<!-- Beginning of bottom part of Todays info data -->
	<td rowspan="2" valign="top" align="right" >
	<table cellpadding="2" cellspacing="0" border="0" valign="top" width="100" >
	<tr>
			<td class="ml-red">10.0km</td>
		</tr>
		<tr>
			<td class="ml-cyan">93%</td>
		</tr>
		<tr>
			<td class="ml-green">1&deg;C</td>
		</tr>
		<tr>
			<td class="ml-yellow">1025.1mb sta&#322;e</td>
		</tr>
		<tr>
			<td class="ml-wkday"><br>N/D</td>
		</tr>
	</table>
	</td>  	
<!-- END: bottom part of Todays info data -->

<!--  Beginning of 7 day forecast data  -->
<!-- Day 1 info -->
	<td>   
		<table   cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/11.png"width="80" /></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">7&deg;C </td>
			<td align="center" class="ml-green"> ~ </td> 
			<td align="left" class="ml-cyan">1&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" valign="top" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>  	<!--  end of Day 1 info


<!-- Day 2 info -->
	<td>
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/05.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">3&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">-1&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>	<!--  end of Day 2 info    -->


<!-- Day 3 info -->
	<td> 
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/14.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">2&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">-2&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>	<!--   End of Day 3 Info   -->


<!-- Day 4 info -->
	<td>
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/14.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">2&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">-2&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>  	<!--  End of Day 4 Info  -->

<!-- Day 5 info -->
	<td>
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/14.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">3&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">-1&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>  	<!--  End of Day 5 Info  -->

<!-- Day 6 info -->
	<td>
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/14.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">6&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">1&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>  	<!--  End of Day 6 Info  -->

<!-- Day 7 info -->
	<td>
		<table cellpadding="0" cellspacing="0" border="0" width="60">
		<tr>
			<td colspan="3" align="center"><img src="file:///usr/share/gtk-desktop-info/images/weathericons/14.png" width="80"/></td>
		</tr>
		<tr>
			<td align="right" class="ml-red">6&deg;C</td>
			<td align="center" class="ml-green"> ~ </td>
			<td align="left" class="ml-cyan">2&deg;C</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday"><br>60%</td>
		</tr>
		</table>
	</td>  	<!--  End of Day 7 Info  -->



<!--  Beginning of Wind Compass  -->
<tr>
	<td rowspan="3" align="center" class="ml-yellow"><img src="file:///usr/share/gtk-desktop-info/images/bearingicons/10.png" width="70"/><br>WNW 13kph<br>N/D</td>
</tr>	<!--  End of Wind Comnpass  ->>

<!--  Beginning of Moon Phase  -->
	<td rowspan="3" align="center" class="ml-yellow"><img src="file:///usr/share/gtk-desktop-info/images/moonicons/17.png" width="60"/><br><br>Garbaty</td>
	<td colspan="1">  
<!--  End of Moon Phase  -->


<!-- sunrise - sunset & daylight text -->
		<table cellpadding="2" cellspacing="2" border="0">
		<tr>
			<td align="right" class="ml-sr"><br>Wsch.S&#322;:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Zachód.S&#322;:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">D&#322;ugo&#347;&#263; Dnia:</td>
		</tr>
		</table>

	</td>
<!-- END: sunrise - sunset & daylight text -->

<!-- Today: sunrise - sunset & daylight values -->
	<td>
		<table cellpadding="2" cellspacing="2" border="0">
		<tr>
			<td align="left" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="left" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="left" class="ml-daylight">??:??</td>
		</tr>
		</table>

	</td>	<!-- END: Today: sunrise - sunset & daylight values -->

<!--Beginning of Day 1 sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!-- END: Day 1: sunrise - sunset & daylight values -->

<!-- Day 2: sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>

	</td>
<!-- END: Day 2: sunrise - sunset & daylight values -->

<!-- Beginning of Day 3: sunrise - sunset & daylight values -->
	<td align="center">

		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!-- END: Day 3: sunrise - sunset & daylight values -->

<!-- Day 4: sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!--  End of Day 4 sunrise, sunset, and daylight  -->

<!-- Day 5: sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!--  End of Day 5 sunrise, sunset, and daylight  -->

<!-- Day 6: sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!--  End of Day 6 sunrise, sunset, and daylight  -->

<!-- Day 7: sunrise - sunset & daylight values -->
	<td align="center">
		<table cellpadding="2" cellspacing="2" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">?:?? ??</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight">??:??</td>
		</tr>
		</table>
	</td>
<!--  End of Day 7 sunrise, sunset, and daylight  -->

</tr>

<!-- Start of Update and Fetch times -->
<tr>
	<td></td><td></td>
	<td colspan="4" valign="center" align="center" class="mediumlight">Last Update: 3/16/09 7:30 AM Local Time</td>
	<td colspan="3" valign="center" align="center" class="mediumlight">Last Fetch: 2009-03-16 07:55</td>
</tr>
</table>
<br><br><br>
<table cellpadding="0" cellspacing="0" border="0" bordercolor="white" >
<tr>	
		<td ><img src="/tmp/weathermap_76dd8358-11f7-11de-a3e0-00221591a554.jpg" width="700" /> </td>
</tr>
</table>

</body>
</html>

```
css and template files I got from xeddog, post NR:250

---

### Post by kaivalagi on 2009-03-16
@zet120

I changed the code to try using python 2.5+ compliant code for the sunset datetime formatting first, then use 2.4....nether seemed to have worked. I think your locale settings are putting the script out of whack...

I've changed the code again now, so if the formatting can't handle sunset/sunrise they'll be output without any formatting i.e. raw text from in xml

Can you swap out the "/usr/share/gtk-desktop-info/plugin_forecast.py" file with the one attached and let me know how you get on..

Cheers

---

### Post by zet120 on 2009-03-16
Hi,
Template and css from post Nr.250, plugin_forecast.py from attached.
Sunrise, sunset OK, option **Hours of DayLight** is error.

[[IMG]http://pic.ipicture.ru/uploads/090316/thumbs/1XU6PUnDwO.png[/IMG]](http://ipicture.ru/Gallery/Viewfull/15741307.html)

**LOG**
```

2009-03-16 19:39:47,612 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,612 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,613 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,613 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,613 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,614 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,614 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,614 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,615 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,615 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,615 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,616 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,616 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,616 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,617 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,617 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,617 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,618 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,626 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,626 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,627 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,627 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,627 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,628 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,628 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,628 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,629 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,629 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,629 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,630 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,630 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,630 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,631 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,631 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,631 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,632 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,632 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,632 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,633 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,633 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,633 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,634 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,649 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 979, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,650 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 985, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,650 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 993, in getDatatypeFromSet
    sstime = datetime.strptime(set.sunset, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,650 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunset datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 999, in getDatatypeFromSet
    sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,651 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1011, in getDatatypeFromSet
    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,651 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract sunrise/sunset from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1017, in getDatatypeFromSet
    srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: AM

2009-03-16 19:39:47,654 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract update datetime from data using standard codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 851, in getDatatypeFromSet
    output = self.getTimestampOutput(datetime.strptime(datetext, "%m/%d/%y %I:%M %p"), minuteshide)
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,654 - gtk-desktop-info.plugin_forecast - ERROR - Failed to extract update datetime from data using python 2.4 compliant codeTraceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 856, in getDatatypeFromSet
    output = self.getTimestampOutput(datetime(*(time.strptime(datetext, "%m/%d/%y %I:%M %p"))[0:6]), minuteshide)
  File "/usr/lib/python2.5/_strptime.py", line 333, in strptime
    data_string[found.end():])
ValueError: unconverted data remains: PM

2009-03-16 19:39:47,655 - gtk-desktop-info.plugin_forecast - ERROR - Unable to extract the Last update date from the dataset, using raw text without formatting

```

P.S.
Thank you for your perseverance and patience. 
If there is a need for such a proposal to my remote desktop to the current tests.

---

### Post by kaivalagi on 2009-03-16
@zet120

daylight hours needs sunrise and sunset in datetime format, and this is the problem you are having. I got around it with sunrise and sunset output by defaulting to the actual text in the feed, but can't get around the same problem to handle daylight hours calculations.

I'll take yet anothe rlook at why this problem might be occuring...ideally I need to debug on your machine but this would require eclipse and pydev being setup...

Maybe I can setup a test script to help identify exactly what is up...but that's not going to happen in the next day or so as work is becoming a little stressed of late.

[COLOR="Navy"]Edit: I am still thinking all these issues have something to do with your locale...

Looking at my LC_TIME locale using this:

```
locale -c LC_TIME
```

I get:

```
LC_TIME
Sun;Mon;Tue;Wed;Thu;Fri;Sat
Sunday;Monday;Tuesday;Wednesday;Thursday;Friday;Saturday
Jan;Feb;Mar;Apr;May;Jun;Jul;Aug;Sep;Oct;Nov;Dec
January;February;March;April;May;June;July;August;September;October;November;December
[COLOR="Red"]AM;PM[/COLOR]
%a %d %b %Y %T %Z
%d/%m/%y
%T
%l:%M:%S %P %Z






0
S
7
19971201
4
1
1
1

%a %b %e %H:%M:%S %Z %Y
UTF-8
```

What about you?

Also, can you follow these steps in a terminal window and tell me what is output:

[LIST=1]
[*]python [COLOR="Gray"]<enter>[/COLOR]
[*]import datetime [COLOR="Gray"]<enter>[/COLOR]
[*]datetime.datetime.strptime("4:56 AM","%I:%M %p") [COLOR="Gray"]<enter>[/COLOR]
[/LIST]

I see this:

```
python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:29:17) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import datetime
>>> datetime.datetime.strptime("4:56 AM","%I:%M %p")
datetime.datetime(1900, 1, 1, 4, 56)
>>> 
```


I really can't make any sense of the issue, the test.py works so the script should too.....
[/COLOR]

---

### Post by zet120 on 2009-03-16
In me is similar, but there is no **AM, PM**
```

zet120@zet120-desktop:~$ locale -c LC_TIME
LC_TIME
nie;pon;wto;&#347;ro;czw;pi&#261;;sob
niedziela;poniedzia&#322;ek;wtorek;&#347;roda;czwartek;pi&#261;tek;sobota
sty;lut;mar;kwi;maj;cze;lip;sie;wrz;pa&#378;;lis;gru
stycze&#324;;luty;marzec;kwiecie&#324;;maj;czerwiec;lipiec;sierpie&#324;;wrzesie&#324;;pa&#378;dziernik;listopad;grudzie&#324;
;
%a, %-d %b %Y, %T
%d.%m.%Y
%T







0
n
7
19971201
4
1
1
1

%a, %-d %b %Y, %T %Z
UTF-8


```

```

zet120@zet120-desktop:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import datetime
>>> datetime.datetime.strptime("4:56 AM","%I:%M %p")
datetime.datetime(1900, 1, 1, 4, 56)
>>> 
```

---

### Post by xeddog on 2009-03-17
Sounds like the coupon code still works.  Kool.

xeddog

---

### Post by RavUn on 2009-04-01
I'm trying to install this under xfce on 8.04 and I get this:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable
E: Broken packages

```

Is this because I'm on 8.04 instead of 8.10 or is there something else?  I tried installing libwebkitgtk1d and libwebkitgtk-dev but no luck.

---

### Post by Bruce M. on 2009-04-01
> **RavUn said:**
> Is this because I'm on 8.04 instead of 8.10 or is there something else?  I tried installing libwebkitgtk1d and libwebkitgtk-dev but no luck.

In a word: yes.  "python-webkitgtk" is in 8.10's repos.

Look here: [Python WebKit GTK+]("http://live.gnome.org/PyWebKitGtk")

Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-04-02
> **RavUn said:**
> I'm trying to install this under xfce on 8.04 and I get this:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable
E: Broken packages

```

Is this because I'm on 8.04 instead of 8.10 or is there something else?  I tried installing libwebkitgtk1d and libwebkitgtk-dev but no luck.

Maybe allowing backports will help? Just a guess...

---

### Post by RavUn on 2009-04-03
I was working on installing the dependencies but then there were conflicting dependencies.  I ended up just installing 8.10, it was only a testing VM anyway :P

I've gotta start playing with it some, now.

---

### Post by kaivalagi on 2009-04-03
> **RavUn said:**
> I was working on installing the dependencies but then there were conflicting dependencies.  I ended up just installing 8.10, it was only a testing VM anyway :P

I've gotta start playing with it some, now.

Have fun, and please post back any comments/suggestions/custom templates etc

I WILL migrate it to Jaunty once I have migrated, I normally wait until 1 week after the final release date before I upgrade then start on all my script packages. Hopefully the upgrade will be painless and all that wont take too long. I figure you might want to know about this as if you will be installing 9.04 soon this factors in :)

I do know that there have been some python niggles with Jaunty so far, because of the python 2.6 implementation....

---

### Post by RavUn on 2009-04-03
Wow this thing is really cool.  It took me a bit to get used to your plugins since I don't know python much but I've got things how I want em now.  I think I'll try playing with it some more.  Does flash only work when using the null plugin?  I tried, for testing, loading various sites and ones with flash died from a segmentation fault.  I wanna test some javascript next.  I imagine I can incorporate some perl or C into this, but I'm trying to figure out how your program works.

Great work!  Now you've inspired me to learn python.


EDIT: From what I can tell, it seems the main .py file reads the html spit out by the plugin which reads from the template.  Is there any way to make it so the main file can accept plugins without needing to edit that main file to incorporate it each time?  I'm wondering if I could write a perl script and include it as a plugin since I don't know python.

---

### Post by kaivalagi on 2009-04-04
> **RavUn said:**
> Wow this thing is really cool.  It took me a bit to get used to your plugins since I don't know python much but I've got things how I want em now.  I think I'll try playing with it some more.  Does flash only work when using the null plugin?  I tried, for testing, loading various sites and ones with flash died from a segmentation fault.  I wanna test some javascript next.  I imagine I can incorporate some perl or C into this, but I'm trying to figure out how your program works.

I think I got flash working before now, bear in mind though that it is using the gtk webkit library which is in it's easy stages. Java script works fine, the null plugin by default runs a javascript clock fine out of the template.

> **RavUn said:**
> 
Great work!  Now you've inspired me to learn python.


Glad you like :)

Eclipse and PyDev is what you need, and download Eclipse from the main site not from the repos!!!

> **RavUn said:**
> 
EDIT: From what I can tell, it seems the main .py file reads the html spit out by the plugin which reads from the template.  Is there any way to make it so the main file can accept plugins without needing to edit that main file to incorporate it each time?  I'm wondering if I could write a perl script and include it as a plugin since I don't know python.

Nope, the plugins currently need defining in the main file, and because template options are passed from the main file to the plugin, using alternatives to Python isn't ideal. I'll atleast look at removing the code dependency for names though so you can just pop a new py file into the folder and reference it in the options...

I would say forget Perl and C for this purpose, just learn Python and create what you need based on one of the existing simplier plugins, like the shell one maybe. If you can handle Perl and C then Python should be a piece of cake.

Any questions just ask

[COLOR="Navy"]edit: just modified gtk_desktop_info.py. I updated the plugin import to handle any name passed in to remove any code dependencies in the main script, so if --plugin=newscript is used the app will look for plugin_newscript.py. I've attached it for your benefit, I'll release it along with other changes soonish, but for now you could replace the one file to get what you need.[/COLOR]

---

### Post by RavUn on 2009-04-04
Awesome! Thanks a lot.  I'll look into python for a couple of days.

---

### Post by HippyRandall on 2009-04-08
been having a play with using jQuery with the rhythmbox plugin to show the album art and rating when you click on the artist and song info. here is what I have so far:

rhythmbox.template:
```
<script src="/home/hippy/gDinc/scripts/jquery-1.3.2.min.js" type="text/javascript"></script>
<script type="text/javascript">
  $(function(){
    $('.contentleft').click(function(){
      $('.contentright').fadeIn(2500);
      $('.contentright').fadeOut(2500);
    });
  });
</script>

<style type="text/css">
  .contentright{
    display: none;
  }

</style>
<div id="wrapper">
    <div class="contentleft">
        <div class="largedark">[--datatype=TI]</div>
        <div class="largelight">[--datatype=AR]</div>    
        <div class="largedark">[--datatype=AL]</div>
    </div>
    <div class="contentright">
        <div class="coverart"><img src="[--datatype=CA]" width="128"></div>
        <div class="rating"><img src="[--datatype=RT]" width="128"></div>
    </div>  
</div>
```rboxBar.template:
```
    <table width="[--datatype=PP]%" cellpadding="0" cellspacing="0"><tr><td class="bar">&nbsp;</td></tr></table><br>
        <div class="largedark">[--datatype=PT] / <span class="largelight">[--datatype=LE]</span> (<span class="largelight">[--datatype=PP]%</span>)</div>
```as you can see it is just the basic template that comes stock with gtk-desktop-info but split into 2 template files to resolve the issue of the --interval=xx refreshing in undesirable ways. the jQuery itself is pretty self explanatory in that fadeIn(2500) fades in the album art and rating over 2.5 seconds and fadeOut(2500) does the reverse.
I think I am going to adapt this to the weather plugin so that on click anywhere in the forecast area it will display the current radar map.

Enjoy,
Hippy

Edit: here is the link to download jquery [http://jquery.com/](http://jquery.com/)

---

### Post by HippyRandall on 2009-04-08
updated my jquery for the rhythmbox so that when you hover over the artist, album, etc the album art and rating will show. when you mouse off they will disappear. I am also putting all the jquery in it's own file and calling it with:
```
<script src="/home/hippy/gDinc/scripts/jquery-1.3.2.min.js" type="text/javascript"></script>
<script src="/home/hippy/gDinc/scripts/scripts.js" type="text/javascript"></script>

<div id="wrapper">
    <div class="contentleft">
        <div class="largedark">[--datatype=TI]</div>
        <div class="largelight">[--datatype=AR]</div>    
        <div class="largedark">[--datatype=AL]</div>
    </div>
    <div class="contentright">
        <div class="coverart"><img src="[--datatype=CA]" width="128"></div>
        <div class="rating"><img src="[--datatype=RT]" width="128"></div>
    </div>  
</div>
```

and the scripts.js file:

```
$(function() { 
    $('.contentright img').animate({"opacity": .0 }); 
 
    $('.contentleft').hover(function() { 
        $('.contentright img').stop().animate({ "opacity": 1 }); 
    }, function() { 
        $('.contentright img').stop().animate({ "opacity": .0 }); 
    }); 
});
```

---

### Post by kaivalagi on 2009-04-08
Very nice Hippy...I recently went on a 4 day ajax/jquery course (mostly ajax) and didn't even think to add some bells and whistles to the app using it.

Once you've had a good play and have got a few effects in place I'll build them into the default templates, and add the jquery source to the package.

I'll email you the course exercise code...it's mostly ajax but you should pickup some mean javascript ideas from it...:)

Oh, have you installed firebug into firefox yet?

---

### Post by HippyRandall on 2009-04-08
> **kaivalagi said:**
> Oh, have you installed firebug into firefox yet?

But of course! perish the thought of living without firebug ;)
You know what would be nice is a --updateOnSongChange type option for the rbox plugin that would get the message from dbus that the song has changed and do a forced refresh of the album, artist, etc. Not sure that it is even possible but a guy can dream right? :lolflag:

---

### Post by Bruce M. on 2009-04-08
> **HippyRandall said:**
> updated my jquery for the rhythmbox so that when you hover over the artist, album, etc the album art and rating will show. when you mouse off they will disappear. I am also putting all the jquery in it's own file and calling it with:


**WoW!** I almost want to start playing music on my PC now. Cheapy speakers stop me, but this is **GREAT WORK Hippy!** And should not go unnoticed by even us non users.

> **kaivalagi said:**
> Very nice Hippy...I recently went on a 4 day ajax/jquery course (mostly ajax) and didn't even think to add some bells and whistles to the app using it.

Once you've had a good play and have got a few effects in place I'll build them into the default templates, and add the jquery source to the package.

I'll email you the course exercise code...it's mostly ajax but you should pickup some mean javascript ideas from it...:)

Oh, have you installed firebug into firefox yet?

Go for it K. This is really neat.

What's firebug?

Have a nice day guys.
Bruce

---

### Post by HippyRandall on 2009-04-08
> **Bruce M. said:**
> **WoW!** I almost want to start playing music on my PC now. Cheapy speakers stop me, but this is **GREAT WORK Hippy!** And should not go unnoticed by even us non users.

Thanks bud!

> **Bruce M. said:**
> 
Go for it K. This is really neat.

What's firebug?

Have a nice day guys.
Bruce
from [getfirebug.co]("http://getfirebug.com/")m:[FONT=Lucida Console]
[FONT=Fixedsys]> Firebug integrates with Firefox to put a wealth of web development tools at your fingertips while you browse. You can edit, debug, and monitor CSS, HTML, and JavaScript live in any web page[/FONT][/FONT]

---

### Post by Bruce M. on 2009-04-08
> **HippyRandall said:**
> Thanks bud!


from [getfirebug.co]("http://getfirebug.com/")m:[FONT=Lucida Console]
[FONT=Fixedsys][/FONT][/FONT]

> live in any web page

You mean I can edit pages on your site with this?

Oh I gotta go look!  :shock:

---

### Post by HippyRandall on 2009-04-08
> **Bruce M. said:**
> You mean I can edit pages on your site with this?

Oh I gotta go look!  :shock:
sort of. you can edit the css of the page but it is only good for that session/visit to the page. as soon as you refresh the page or go to another link on a site the changes are undone. it is great for live testing of css changes before implementing them in your code and also to see which style sheet is affecting the code. if you go to my site you will see that there are a few different style sheets in use. without firebug it would take forever to figure out which sheet was affecting the bit of code you wanted to change.

Hope that clears it up
Hippy

---

### Post by kaivalagi on 2009-04-09
I use firebug mainly to debug javascript, it supports breakpoints for javascript code so you can step through line by line to see what is going on :)

---

### Post by Bruce M. on 2009-04-09
I got it, and it is kinda neat - but not being a programmer it's a bit over my head. Amazing how many places one visits on the web and it says there is an error though. :)

My wife was panicking after I put it in, she didn't know, "He Bruce, we have a "ERROR" what do I do!" :lolflag:

Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-04-16
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Quite a few changes mostly based on changes made to related conky scripts over the last month or so. Also an update to nl and adding of de translations. Take a look at the package changes below for more details.

**Note** that if you receive any errors in relation to your config file contents then you'll need to update yours (found in ~/.config/gtk-desktop-info/) based on the default ones (found in /usr/share/gtk-desktop-info/config/)

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.12_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.12_source.changes)

**gtk-desktop-info-data:** [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.07_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info-data_0.07_source.changes)

The apt packages should be available shortly

Chimo

[COLOR="Blue"]**Edit:** Found a bug with the google calendar plugin, so a further update to gtk-desktop-info has just gone out, changes here:  [https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.13_source.changes](https://launchpad.net/%7Em-buck/+archive/ppa/+files/gtk-desktop-info_0.13_source.changes)[/COLOR]

---

### Post by Gnounc on 2009-04-16
dont forget stylish! its at userstyles.org

If you want your firebug changes to be permanant, use stylish.

If you want scripts to be permanant of course, use Greasemonkey.

(if you're a hotkey junie, I made a stumbleupon bar shrinker, I also made
a hackaday userstyle, but it doesnt quite work, and I'm too lazy to go to fix it, so dont expect much there)

---

### Post by Gnounc on 2009-04-16
ooh, I'd be interested in the ajax course exercises! Might I?

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by HippyRandall on 2009-04-18
Found out something kind of neat. You can use widgets from google in this app. Some that I tried did not work due to issues with cookies or other errors but some worked. Just a heads up if anyone wanted to use them.

Hippy

[COLOR=Blue]Edit: I used the --plugin=null option to run them with the relevant code saved to a template file.[/COLOR]

---

### Post by Bruce M. on 2009-04-18
> **HippyRandall said:**
> Found out something kind of neat. You can use widgets from google in this app. Some that I tried did not work due to issues with cookies or other errors but some worked. Just a heads up if anyone wanted to use them.

Hippy

[COLOR=Blue]Edit: I used the --plugin=null option to run them with the relevant code saved to a template file.[/COLOR]

Oh sure - and not even a screenie.  :(

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Red"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Updated deluge plugin to retrieve data items for each torrent based on a finite list rather than all of them, this stops an error occurring with python 2.6 and xmlrpc in Jaunty, see here for changes: [https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.14_source.changes](https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.14_source.changes)

The apt packages should be available shortly

[COLOR="Red"]**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...[/COLOR]

Chimo

---

### Post by ehunt123 on 2009-04-20
Just have to say a great "wow" for this. Finally combining all of the nice Conky stuff together into an app is quite helpful. Thanks.

---

### Post by kaivalagi on 2009-04-20
> **ehunt123 said:**
> Just have to say a great "wow" for this. Finally combining all of the nice Conky stuff together into an app is quite helpful. Thanks.

Glad you like it

It's arguably more tweak-able than conky too with javascrip/image support etc, so if you have any good ideas/templates etc please share...it may go into a future package for everyone to get something from...

Cheers

---

### Post by martynp on 2009-04-20
Hi Mark,

Hope you are well?

I haven't been following the development of this as close as I should as I don't use a number of the apps it supports. However, the URL function is going to be very useful to me for embedding [http://www.twitzap.com](http://www.twitzap.com) in my destkop as a low resource usage Twitter App.

Is your app able to store usernames and passwords or cookies yet as I don't want to have to type and retype my login credentials every time I open the page?

Or perhaps you can think of a solution?

Many Thanks,

Martyn

---

### Post by kaivalagi on 2009-04-21
> **martynp said:**
> Hi Mark,

Hope you are well?

I haven't been following the development of this as close as I should as I don't use a number of the apps it supports. However, the URL function is going to be very useful to me for embedding [http://www.twitzap.com](http://www.twitzap.com) in my destkop as a low resource usage Twitter App.

Is your app able to store usernames and passwords or cookies yet as I don't want to have to type and retype my login credentials every time I open the page?

Or perhaps you can think of a solution?

Many Thanks,

Martyn

In theory because the app uses webkit it is a mini browser and so should support all that. If you login and choose to remember the login it may work...To be honest I have never tried this out so don't really know. Have you actually tried doing this to see what happens?

The app also supports javascript, so _maybe_ using the null plugin with a template which has a javascript function to login and point to the site might work...but again I have no idea and this might not work...

---

### Post by HippyRandall on 2009-04-21
in my experimentation with google widgets I received a couple of errors about the page I was viewing not be able to store a cookie. I don't think this works but lots of other fun things can be done with jQuery.

Hippy

---

### Post by martynp on 2009-04-21
Hi Guys,

Yeah, I tried all that and it doesn't work. Also, It seems to refresh the page at regular intervals (even if I set --interval=0) and this doesn't sit well with the particular page I am trying to use.

I'll monitor this thread for now but sadly, Mark, I will have to go back to Prism for now to make this work for me.

Kind Regards,

Martyn

---

### Post by kaivalagi on 2009-04-21
> **martynp said:**
> Hi Guys,

Yeah, I tried all that and it doesn't work. Also, It seems to refresh the page at regular intervals (even if I set --interval=0) and this doesn't sit well with the particular page I am trying to use.

I'll monitor this thread for now but sadly, Mark, I will have to go back to Prism for now to make this work for me.

Kind Regards,

Martyn

Don't set the interval option at all, the output should never get refreshed then...

It looks like we need a better webkit package which supports cookies better...I'll do some digging.

Is there no rss feed for the twitter content you want to see? I am thinking of creating a generic rss feed plugin at some point :)

---

### Post by martynp on 2009-04-21
Mark,

With or without the refresh set (I had already tried it without first) this site [http://www.twitzap.com](http://www.twitzap.com) is being refreshed in your program every x seconds returning you from wherever you are to the start page. Also, login credentials are not remembered.

In Prism, this site as a webapp is not refreshed and remembers login credentials.

As for the RSS feed........ that's soooooo 2008 :-)

I do use a CLI app called Twidge if i want that info in it's rawest format.

I have forsaken standalone twitter apps like TweetDeck, Gwibber etc for TwitZap embedded in the desktop as notification is provided nicely by the Gnome Do microblogging plugin.

Hope this all makes sense :-)

Prism downside is that it uses far more memory than gtk-desktop-info

---

### Post by HippyRandall on 2009-04-21
forsake tweetdeck!
BLASPHEMY!!!!!!
;):);)
I would be lost without it.

---

### Post by martynp on 2009-04-21
> **HippyRandall said:**
> forsake tweetdeck!
BLASPHEMY!!!!!!
;):);)
I would be lost without it.

LOL

DestroyTwitter is far better than TweetDeck IMHO

---

### Post by HippyRandall on 2009-04-21
> **martynp said:**
> LOL

DestroyTwitter is far better than TweetDeck IMHO
ooh smexy
checking it out now. thanks

---

### Post by martynp on 2009-04-21
> **HippyRandall said:**
> ooh smexy
checking it out now. thanks

and don't panic that it doesn't have groups. It will do by the end of the week. Also, check out the themes at the site.

---

### Post by HippyRandall on 2009-04-21
> **martynp said:**
> and don't panic that it doesn't have groups. It will do by the end of the week. Also, check out the themes at the site.
let me rephrase....SUPAH SMEXY
thanks a ton for this


































and now back to gDinc support

---

### Post by martynp on 2009-04-21
> **HippyRandall said:**
> let me rephrase....SUPAH SMEXY
thanks a ton for this


































and now back to gDinc support


You are welcome!

Follow the developer.... he is a really nice guy. I am testing the next beta with groups right now!

Enjoy!

---

### Post by kaivalagi on 2009-04-21
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Added a new plugin called feedparser, which handles rss feed output. This is very simple right now, so if anyone has any suggestions for further info to display let me know!

gtk-desktop-info changes: [https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.15_source.changes](https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.15_source.changes)

gtk-desktop-info-data changes: [https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.08_source.changes](https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.08_source.changes)

The apt packages should be available shortly, they are taking a little longer than normal today...

[COLOR="Red"]**REMEMBER:** To get this update you will need to change your repository settings for my new PPA locations available for Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...[/COLOR]

Chimo

---

### Post by HippyRandall on 2009-04-21
getting this error for data and the main app:

```
gtk-desktop-info-data:
  Depends: python-central (>=0.6.11) but 0.6.7ubuntu1 is to be installed

```

What's u[ with that?

---

### Post by kaivalagi on 2009-04-21
> **HippyRandall said:**
> getting this error for data and the main app:

```
gtk-desktop-info-data:
  Depends: python-central (>=0.6.11) but 0.6.7ubuntu1 is to be installed

```

What's u[ with that?

Uh Oh, looks like building the jaunty package first on launchpad then copying the package binary across to Intrepid leaves behind some dependencies that Intrepid can't fulfil...I'm still figuring out the launchpad options available :)

I will have to release a new version and copy the package across from Jaunty to Intrepid with the re-build option instead.

Dealing with it now...

[COLOR="Blue"]edit: not that simple, I can't rebuild the package...the only answer seems to be building for intrepid then copying to jaunty...gonna have to wait until tomorrow now[/COLOR]

---

### Post by Gnounc on 2009-04-22
I havent made much progress in learning python, I'm not having an easy time with it.

But I made a bit of a copy paste job, and I was hoping you could tell me 
if it's anywhere close to workable as is (at least on the python side of it)

[http://pastebin.com/m143abb1](http://pastebin.com/m143abb1)

It's supposed to be a single taskbar icon that changes icons 
both when a message is recieved from a specific buddy, and when you click on the icon to make the notification go away.

---

### Post by kaivalagi on 2009-04-22
> **Gnounc said:**
> I havent made much progress in learning python, I'm not having an easy time with it.

But I made a bit of a copy paste job, and I was hoping you could tell me 
if it's anywhere close to workable as is (at least on the python side of it)

[http://pastebin.com/m143abb1](http://pastebin.com/m143abb1)

It's supposed to be a single taskbar icon that changes icons 
both when a message is recieved from a specific buddy, and when you click on the icon to make the notification go away.

Can you PM me with this sort of stuff, I would like to try and keep the thread on track. I'll have a read and come back via PM ;)

---

### Post by kaivalagi on 2009-04-22
**[COLOR="DarkOrange"][SIZE="4"]UPDATE (AGAIN)[/SIZE][/COLOR]**

Had a few hiccups with launchpad package copying for supporting both Jaunty and Intrepid but I think I've sussed it now, so a few versions later with the same content :)

Sooooo as before, added a new plugin called feedparser, which handles rss feed output. This is very simple right now, so if anyone has any suggestions for further info to display let me know!

gtk-desktop-info changes: [https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.18_source.changes](https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.18_source.changes)

gtk-desktop-info-data changes: [https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.10_source.changes](https://launchpad.net/%7Em-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.10_source.changes)

The apt packages should be available shortly...**in 2 hours according to Launchpad!!**

[COLOR="DarkOrange"]**REMEMBER: To get this update you will need to change your repository settings for my new PPA locations available for Intrepid and Jaunty versions of Ubuntu. See the first post install instructions for details...**[/COLOR]

Chimo

---

### Post by Bruce M. on 2009-04-22
Hi Folks,

I start conky (ducking) with **ssc.sh** - click it's on - click - it's off.
```
#!/bin/sh
# click to start, click to stop

if pidof conky | grep [0-9] > /dev/null
then
 exec killall conky
else

#sleep 3  # sleep not required for xfce on startup - 30 or more for others
conky -c ~/Conky/conkymain &
#sleep 3
conky -c ~/Conky/conkytext &
#sleep 3
conky -c ~/Conky/conkyemail &
#sleep 3
#conky -c ~/Conky/conkyforecast &

# test conkys
#sleep 3
#conky -c ~/Conky/Test/bottom &
#sleep 3
#conky -c ~/Conky/Test/colours &
#sleep 3
#conky -c ~/Conky/Test/test &
#sleep 3
#conky -c ~/Conky/Test/test-2 &
#sleep 3
#conky -c ~/Conky/Test/test-3 &
#sleep 3
#conky -c ~/Conky/Test/basic_conky &
#sleep 3
#conky -c ~/Conky/Test/bruce &
#sleep 3
#conky -c ~/Conky/Test/text_bar &
 exit
fi
```

and I start gtk-desktop-info with: **gtk.sh**
```
#!/bin/sh

# kill all instances of the app before starting new ones
#pkill -f gtk_desktop_info.py

# wait for a sec
# sleep 1

# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```

and kill gtk with: **kill-gtk.sh**
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py
```

Is there a way to "rewrite" those so it equals the function of **ssc.sh**

ie: click....
if gtk is not running - run it.
if gtk is running - kill it.

That way, it could be added to "AutoStart" and used as a launcher on my panel for those times of editing.  :) "kill-gtk" is on my panel with K's avatar.  :)

Have a nice day.
Bruce

---

### Post by HippyRandall on 2009-04-22
> **Bruce M. said:**
> Hi Folks,
...

Is there a way to "rewrite" those so it equals the function of **ssc.sh**

ie: click....
if gtk is not running - run it.
if gtk is running - kill it.

That way, it could be added to "AutoStart" and used as a launcher on my panel for those times of editing.  :) "kill-gtk" is on my panel with K's avatar.  :)

Have a nice day.
Bruce

Don't know but it would be nice.

Oh and you better be ducking! CONKY! pfft:lolflag:

---

### Post by kaivalagi on 2009-04-23
Try this, I just plugged together bits from all scripts:
```
#!/bin/sh
# click to start, click to stop

if pidof gtk_desktop_info.py | grep [0-9] > /dev/null
then
 exec pkill -f gtk_desktop_info.py
else
 # start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
 gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
fi
```

Why do this though, when you can right click on the forecast output and select refresh...;)

---

### Post by arindom on 2009-04-23
This is really an excellent application. It's a great work. I have been using this for couple of weeks now and it feels great!

I have a question here. Actually I was thinking of replacing Conky with this one. In Conky it is possible to get the top 5/6/any number of running processes sorted as per % of memory taken. 

I am sure that must be possible here too, but because of my lack of knowledge on how to get that info, I request anyone here to please help with the relevant command that will work to get the top 5/6 processes that are running.

Thanks for your help.

---

### Post by HippyRandall on 2009-04-23
> **kaivalagi said:**
> Try this, I just plugged together bits from all scripts:
```
#!/bin/sh
# click to start, click to stop

if pidof gtk_desktop_info.py | grep [0-9] > /dev/null
then
 exec pkill -f gtk_desktop_info.py
else
 # start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
 gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
fi
```Why do this though, when you can right click on the forecast output and select refresh...;)
 
I have noticed in my playing around with templates, especially when implementing jquery, that a refresh does not always cut it. Sometimes in order to see the effects of the changes I made I _had_ to quit and restart it.

2cents more for ya Bruce,
Hippy

---

### Post by HippyRandall on 2009-04-23
> **arindom said:**
> This is really an excellent application. It's a great work. I have been using this for couple of weeks now and it feels great!

I have a question here. Actually I was thinking of replacing Conky with this one. In Conky it is possible to get the top 5/6/any number of running processes sorted as per % of memory taken. 

I am sure that must be possible here too, but because of my lack of knowledge on how to get that info, I request anyone here to please help with the relevant command that will work to get the top 5/6 processes that are running.

Thanks for your help.
  
There are a few things that are not in this app that you can do in Conky. Dynamic content like what you are talking about is one of them. Also the bars and graphs that we had in conky have yet to be figured out. Not sure even where to begin really other than javascript. If you have an urge you could always check out [jQuery]("http://jquery.com") and see what you can come up with to push this along.

Hippy

---

### Post by Bruce M. on 2009-04-23
> **HippyRandall said:**
> Don't know but it would be nice.

Yea, I think so, and for the same reason you said in a post or two later. Plus the fact I'm still helping people with ConkyForecast so at times I need that showing, and refreshing gtk does show the conkyForecast that would be under gtk-weather.  :) 

Autostart and a launcher, for Stop/Start is the best of both worlds.  :)

> **HippyRandall said:**
> Oh and you better be ducking! CONKY! pfft:lolflag:

What for, if you had noticed I use three of K's scripts out of the 4 conkys I use:

```
conky -c ~/Conky/conkytext &
#sleep 3
conky -c ~/Conky/conkyemail &
#sleep 3
#conky -c ~/Conky/conkyforecast &
```

And since 75% of my conkys are as a result of K's work and the other display on my desktop is K's work as well (gtk), I'll "Walk Tall" thank you!

That would be 5x :KS's for K!

The only conky I have is the stuff that gtk doesn't display, I think, unless there have been a LOT of improvements.

It's sad that in this thread people don't show screenshots of what they use gtk for. I think it would become much more popular if they did.

CHIMO!
Bruce

---

### Post by Bruce M. on 2009-04-23
> **kaivalagi said:**
> Try this, I just plugged together bits from all scripts:

Why do this though, when you can right click on the forecast output and select refresh...;)

Tried this - all it does is refresh it.  :(

Sometimes I need to turn it off to show people ConkyForecast.

CHIMO!

---

### Post by kaivalagi on 2009-04-23
> **Bruce M. said:**
> Tried this - all it does is refresh it.  :(

Sometimes I need to turn it off to show people ConkyForecast.

CHIMO!

Did you try the script I posted, I haven't but it looks like it should turn it off if running and vice versa...

---

### Post by kaivalagi on 2009-04-23
> **arindom said:**
> This is really an excellent application. It's a great work. I have been using this for couple of weeks now and it feels great!

I have a question here. Actually I was thinking of replacing Conky with this one. In Conky it is possible to get the top 5/6/any number of running processes sorted as per % of memory taken. 

I am sure that must be possible here too, but because of my lack of knowledge on how to get that info, I request anyone here to please help with the relevant command that will work to get the top 5/6 processes that are running.

Thanks for your help.

Looking into the libstatgrab and pystatgrab libraries to get a hold of process info such as memory and cpu use, we can then have a plugin for process stats which is sortable high to low for memory or cpu usage and can limit output to a number of items...

Call the plugin "processinfo" ?

---

### Post by Bruce M. on 2009-04-23
> **kaivalagi said:**
> Did you try the script I posted, I haven't but it looks like it should turn it off if running and vice versa...

Oh sorry for the confusion.

Yes, I have that script you posted - it just refreshes gtk.  :(

**ss-gtk.sh**
```
#!/bin/sh
# click to start, click to stop

if pidof gtk_desktop_info.py | grep [0-9] > /dev/null
then
 exec pkill -f gtk_desktop_info.py
else
 # start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
 gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
fi
```

CHIMO!
Bruce

---

### Post by kaivalagi on 2009-04-23
There you go Bruce, that's another few stars ;)

pidof only works finding python but not the app running within it, so we have to get the pid a bit more creatively...if you want to use this for other plugin types (only one at a time but right now) chane "plugin=forecast" to whatever the command line option would be for it...don't add the -- too as this upsets grep.

Have fun :)

```
#!/bin/sh
# click to start, click to stop

# get the pid of the forecast gtk process, if we can...
pid=`ps -C python -f | grep "plugin=forecast" | cut -c10-15`

# do we have a valid pid value for killing :)
if test -z "$pid"
then
	# no pid so starting...
	echo 'starting process'
	# start gtk-desktop weather - Monitor 17" "Res: 1280 x 1024 - Bottom left - See: x= and y=
	gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=600 --width=750 --height=245 --x=0 --y=755 --windowmanager=xfce4 --css=/home/bruloo/gtk-desk/my_forecast.css --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
else
	# valid pid so killing...
	echo 'killing process'
	kill $pid	
fi

```

---

### Post by Bruce M. on 2009-04-23
> **kaivalagi said:**
> There you go Bruce, that's another few stars ;)

pidof only works finding python but not the app running within it, so we have to get the pid a bit more creatively...if you want to use this for other plugin types (only one at a time but right now) chane "plugin=forecast" to whatever the command line option would be for it...don't add the -- too as this upsets grep.

Have fun :)

YES! Those stars are for YOU! :KS:KS:KS:KS:KS

This works perfectly! So there we are, side by each on the panel. You control gtk, I control conky. Gotta find one for Hippy now!

Darn it, I look fat on the panel  :)

CHIMO!

---

### Post by arindom on 2009-04-23
> **kaivalagi said:**
> Looking into the libstatgrab and pystatgrab libraries to get a hold of process info such as memory and cpu use, we can then have a plugin for process stats which is sortable high to low for memory or cpu usage and can limit output to a number of items...

Call the plugin "processinfo" ?

Yes, "processinfo" would be great.

---

### Post by kaivalagi on 2009-04-24
> **arindom said:**
> Yes, "processinfo" would be great.

Early days but would the attached be enough information? i.e. Name, pid, cpu % and memory used

I just ran top and stripped the data from it's output in code

---

### Post by HippyRandall on 2009-04-24
> **kaivalagi said:**
> Early days but would the attached be enough information? i.e. Name, pid, cpu % and memory used

I just ran top and stripped the data from it's output in code
ooh 
cross one more thing off the list K! looks good to me.
Downloading the 9.04 alt cd now. I need something to do tomorrow ;):)

---

### Post by kaivalagi on 2009-04-24
> **HippyRandall said:**
> ooh 
cross one more thing off the list K! looks good to me.
Downloading the 9.04 alt cd now. I need something to do tomorrow ;):)

I have one problem in that I have no easy way to define headings for the output, as the template represents output per process...

Any ideas? May require 2 templates per plugin (3 including header)...one for overall layout and one (if needed) to define the inner html of the repeating parts...messy to design and understand though

---

### Post by arindom on 2009-04-24
> **kaivalagi said:**
> Early days but would the attached be enough information? i.e. Name, pid, cpu % and memory used

I just ran top and stripped the data from it's output in code

Sorry Kaivalagi, I was late in my response. 

Yes this looks good to me. May be you can even consider the %of memory being used in the output. Because that info is also very helpful.

For your kind reference, here is a screenshot of the Conky that I always refer when some process does behave strangely.

Once this part is done we can later concentrate on the other parts like the File System, Network etc.

Many thanks Kaivalagi for deciding and working on the new plugin.

---

### Post by xeddog on 2009-04-26
Hey guys - "simple" question.

In the UG it says that the default path for different things is 

/usr/share/gtk-desktop-info/xx  where xx is "styles", "templates", or "config".  So in my command line to run gtk-desktop-info I have coded 

```
gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=/usr/share/gtk-desktop-info/styles/green.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/usr/share/gtk-desktop-info/templates/test3play.template --noheader  --plugin=forecast --config=/usr/share/gtk-desktop-info/config/plugin_forecast.config &
```

Now if I understand the UG, I should be able to remove the path names and shorten the command line to: 

```
gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=green.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=test3play.template --noheader  --plugin=forecast --config=plugin_forecast.config &
```


But if I do that, gtk-desktop-info cannot find the style sheet, template, or config file.  

So if all of my style sheets and templates are in the default directories, why do I have to include the entire pathname in the command??

TIA,

xeddog

---

### Post by HippyRandall on 2009-04-26
> **xeddog said:**
> Hey guys - "simple" question.

In the UG it says that the default path for different things is 

/usr/share/gtk-desktop-info/xx  where xx is "styles", "templates", or "config".  So in my command line to run gtk-desktop-info I have coded 

```
gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=/usr/share/gtk-desktop-info/styles/green.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/usr/share/gtk-desktop-info/templates/test3play.template --noheader  --plugin=forecast --config=/usr/share/gtk-desktop-info/config/plugin_forecast.config &
```Now if I understand the UG, I should be able to remove the path names and shorten the command line to: 

```
gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=green.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=test3play.template --noheader  --plugin=forecast --config=plugin_forecast.config &
```
But if I do that, gtk-desktop-info cannot find the style sheet, template, or config file.  

So if all of my style sheets and templates are in the default directories, why do I have to include the entire pathname in the command??

TIA,

xeddog

Technically you do not need to define any of those if you are using the defaults. The only thing that you would need to do is use the --colour=green option to change to the green style sheet. if a template is not specifically called then it falls back to the default and the default place to look for the .config files are in ~/.config/gtk-desktop-info so you don't need to define that, just make the changes to that config file and not the ones in /usr/share/gtk-desktop-info

Hope that helps
Hippy

---

### Post by xeddog on 2009-04-26
Thanks Hippy,

But . . .

when I remove the --css option from the command line and replace it with --colour=green, it doesn't get the style sheet that I want.  It changes a couple of the heading colors but most of the text is still black.  So if I understand correctly, the only way for me to get the green.css sheet that I want is to specify the complete path even if it is in the default directory?? (and same goes for templates?)

Thanks,

xeddog

---

### Post by xeddog on 2009-04-26
Now I have another question.  My system is using an nvidia graphics card, and I have dual monitors setup using Twinview.  I have found (elsewhere on this forum), a perl script that places a different wallpaper on each of my two monitors.  It does this by selecting two different wallpaper files from a folder and putting the two together to make one large wallpaper for the virtual desktop.  So in my case, it will take two images, size them to 1280x1024, and then combine them into one image that is 2560x1024.  

So far so good.  It works great.  Then I set up a cron job to do this every 5 minutes (for now), and it changes the wallpapers every 5 minutes as planned.  Also great.

Here is where the problem starts.  When the 5 minutes expires and the script runs again and changes the wallpapers, it does not change them for gtk-desktop-info.  So when the new wallpaper is displayed, gtk-desktop-info is still using the old wallpaper.  

I coded up a little script as follows, and execute it in the cron job.  I call it Do_desk.sh.

```
#!/bin/sh
# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py
# wait for a sec
sleep 1
# Run the Wallpaper Changer
~/Desktop_mods/changer.pl 
#Sleep again
sleep 2
#Run the Weather app 
~/Desktop_mods/mydesktop.sh 

```

When I run this script for the first time, everything works.  No error messages in the log files or dmesg, and I get a new wallpaper.  AND, gtk-desktop-info will use the new wallpaper when it starts so it looks like a transparent backgound.  Kool.

Then the timer kicks off after 5 minutes and I get new wallpaper.  The script kills the gtk-desktop-info processes (I run two), but gtk-desktop-info does not come back.  If I run dmesg I see this:

```
[21791.171045] python[19300]: segfault at 0 ip b7440097 sp bfd15d50 error 4 in libgtk-x11-2.0.so.0.1600.1[b71ed000+3a9000]
```

When I look at the gtk-desktop-info log file I see this:

```
2009-04-26 13:45:08,548 - gtk-desktop-info - ERROR - Failed to setup a wallpaper, using nothing...
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 210, in generateBackground
    disp = display.Display()
  File "/var/lib/python-support/python2.6/Xlib/display.py", line 85, in __init__
    self.display = _BaseDisplay(display)
  File "/var/lib/python-support/python2.6/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.6/Xlib/protocol/display.py", line 45, in __init__
    name, host, displayno, screenno = connect.get_display(display)
  File "/var/lib/python-support/python2.6/Xlib/support/connect.py", line 67, in get_display
    return mod.get_display(display)
  File "/var/lib/python-support/python2.6/Xlib/support/unix_connect.py", line 53, in get_display
    raise error.DisplayNameError(display)
DisplayNameError: Bad display name ""

```


Now, If I go to a terminal and run D0_desk.sh manually, everything starts up again with no error messages.

What the . . .????   HHHHEEEEEEEEEELLLP

xeddog

---

### Post by kaivalagi on 2009-04-27
@xeddog

I think running gtk... through cron should be okay as long as it is running under your user and not root...that maybe where the problem is...? You could try creating a script which loops with a 5 minute sleep in it, then kick this off from your startup applications (sessions) rather than using cron...if that works then you know it is a cron specific issue

Also, everything Hippy mentioned is correct, --colour=green should then get the app using the appropriate plugin_<plugin>_green.css stylesheet...and you ought to edit the .config file for the plugin located in the ~/.config/gtk-desktop-info folder and not use the --config argument at all...unless you need to use 2 different configs for the same plugin and then you'll need to specifically reference at least one alternative.

---

### Post by _mikec_ on 2009-04-29
gtk-desktop-info looks cool, the guide is not telling all in my opinion, for exemple i dont know where to put templates either in css or html, my configs i guess should go in ~/.configs/gtk-desktop-info 
for some reason first post from user in this topic should of have included a more complete exemple showing more than just the clock with a white background when trying to run gtk-desktop-info for the first time from shell... i am running xfce i was thinking on adding gtk-desktop-info to the autostarted apps but now i realise i need a full command line.. i will use google to find some exemples i can use and modify to my needs so i dont have to start from scratch.

---

### Post by kaivalagi on 2009-04-29
> **_mikec_ said:**
> gtk-desktop-info looks cool, the guide is not telling all in my opinion, for exemple i dont know where to put templates either in css or html, my configs i guess should go in ~/.configs/gtk-desktop-info 
for some reason first post from user in this topic should of have included a more complete exemple showing more than just the clock with a white background when trying to run gtk-desktop-info for the first time from shell... i am running xfce i was thinking on adding gtk-desktop-info to the autostarted apps but now i realise i need a full command line.. i will use google to find some exemples i can use and modify to my needs so i dont have to start from scratch.

Where to put _your_ config/template/css files etc is down to you. The app provides options to provide full paths to files if you wish to override the defaults, so anywhere is fine...

I never mentioned calling the app with no arguments in the first post? What I did say is read the guide. In the guide there is mention of the **example shell script which shows various ways of calling the app for the various plugins**. You can find the example script here: **/usr/share/gtk-desktop-info/example/gtk-desktop-info.sh**

I think if you search via google all you will find is content here. As the author I have not published any info elsewhere.

Hope that helps...

**<rant ignore="optional">**
You are probably right that I could have made the guide clearer for all user abilities, but this is a hobby not a professional piece of software...I do not get paid for this and do what I can to help others make good use of it, I think that is more than what is required of me. I could have created this app and not published it and only used it for myself but I didn't...

If you wish to contribute to the first post/guide in some constructive way that would be good, pass on any edits/usable details via a PM to me and I'll add what I think is sensible in the future.

For further examples of use I would hope you could go through this thread looking at what users have come up with, unfortunately most users haven't shared their experiences for others to benefit from...but some users have posted details

Next time rather that merely criticizing someone's work why not try to ask more useful questions, be more constructive and help where you can - or try your luck via google
**</rant>**

---

### Post by _mikec_ on 2009-04-29
thanks for your work share, i forgot to mention it in my previous post but i did find it nice from you from sharing it in my mind. thanks for the share man.
 
I did read the guide though and google was not much of help for this. Perhaps the reason why people didn't share their scripts it's because you did not either beside the 'exemple' which only shows, as i mentioned before, only a clock with a white background. I did modified my compiz config as mentioned in the guide.
 
i hope i will get a chance to make your script work in my desktop, i was looking something like this beside conky.

---

### Post by kaivalagi on 2009-04-30
> **_mikec_ said:**
> thanks for your work share, i forgot to mention it in my previous post but i did find it nice from you from sharing it in my mind. thanks for the share man.[http://ubuntuforums.org/editpost.php?do=updatepost&postid=7182104#](http://ubuntuforums.org/editpost.php?do=updatepost&postid=7182104#)
 
I did read the guide though and google was not much of help for this. Perhaps the reason why people didn't share their scripts it's because you did not either beside the 'exemple' which only shows, as i mentioned before, only a clock with a white background. I did modified my compiz config as mentioned in the guide.
 
i hope i will get a chance to make your script work in my desktop, i was looking something like this beside conky.

The example script displays a whole host of plugin output...normally

I run gnome and therefore it works out the box for me, but you are using xfce right? if so you also need to use the --windowmanager=xfce4 option so the script knows how to retrieve the wallpaper settings.

From "gtk-desktop-info -h":

```
--windowmanager=NAME  default:[gnome] Tell the app which windows manager is
                        in use, options are gnome, kde3, kde4, xfce4, compiz
                        (compiz option is not implemented yet!)
```

If you are using compiz for your wallpaper settings then I am afraid that you'll have to tell the app where your wallpaper is usinf the --wallpaper option:

```
--wallpaper=FILE      Override the wallpaper filepath in case it isn't found
                        automatically
```

If it is not working then try looking in the logfile any errors are logged to, the example uses /tmp/gtk-desktop-info.log...or add a --verbose option to a single command to see in more detail what is happening...then post back with any questions...

Example script below, each plugin highlighted in red:

```
#!/bin/sh
# example use of gtk-desktop-info, for a screen resolution of 1680x1050
# will display on all desktops, and log to a single logfile
# Note:	that if used on a smaller screen bad cropping of wallpaper can take play
#		causing unwanted side effects
################################################################################

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

# use the shell plugin to display the default output of date and time
# update every second
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1 --width=130 --height=50 --x=1560 --y=30 --plugin=[COLOR="Red"]shell[/COLOR] &

# use the null plugin to display the default output of an analog clock
# No interval as no refresh needed (coolclock: http://randomibis.com/coolclock/)
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --width=120 --height=120 --x=1570 --y=80 --plugin=[COLOR="Red"]null[/COLOR] &

# use the email plugin to display email details
# This will error until proper details are provided in a template file (see guide for info), update every 5 minutes
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=300 --width=280 --height=170 --x=1280 --y=30 --plugin=[COLOR="Red"]email[/COLOR] &

# use the googlecalendar plugin to display the default of the next 7 days events
# This will error until proper details are provided in a config file (see guide for info), update every 30 minutes 
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=400 --height=780 --x=1280 --y=200 --plugin=[COLOR="Red"]googlecalendar[/COLOR] &

# use the rhythmbox plugin to display song information
# update every second
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1 --width=300 --height=300 --x=980 --y=30 --plugin=[COLOR="Red"]rhythmbox[/COLOR] &

# use the forecast plugin to display weather info
# The default location is mine, the config file requires updating for custom locations (see guide for info), update every 30 minutes
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=400 --x=980 --y=330 --plugin=[COLOR="Red"]forecast[/COLOR] &

# use the pidgin plugin to display buddy information
# update every minute
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=60 --width=300 --height=250 --x=980 --y=730 --plugin=[COLOR="Red"]pidgin[/COLOR] &

# use the deluge plugin to display bit torrent information
# update every 10 seconds
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=10 --width=300 --height=500 --x=680 --y=30 --plugin=[COLOR="Red"]deluge[/COLOR] &

# use the tomboy plugin to display current notes
# update every 30 minutes
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=400 --x=680 --y=530 --plugin=[COLOR="Red"]tomboy[/COLOR] &

# NOT ENOUGH ROOM FOR THE BELOW, SO COMMENTED OUT :)

# use the feedparser plugin to display rss feed info
# update every 30 minutes
#gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=400 --x=680 --y=530 --plugin=[COLOR="Red"]feedparser[/COLOR] &

# use the twitter plugin to display statuses of friends
# update every 30 minutes
#gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=300 --height=400 --x=680 --y=530 --plugin=[COLOR="Red"]twitter[/COLOR] &

# use the processinfo plugin to display process information
# update every 5 seconds
#gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=5 --width=300 --height=400 --x=680 --y=530 --plugin=[COLOR="Red"]processinfo[/COLOR] &
```

Oh, and I did share all my scripts, they are the default templates/css/config settings, just look in sub-folders in /usr/share/gtk-desktop-info/.....I am starting to feel a little less helpful from here on in :mad:

---

### Post by sirjoebob on 2009-04-30
I have wondered for the longest time why there wasn't a good Conky replacement that allows images, etc. I think I may love you.

---

### Post by HippyRandall on 2009-04-30
> **_mikec_ said:**
> thanks for your work share, i forgot to mention it in my previous post but i did find it nice from you from sharing it in my mind. thanks for the share man.
 
I did read the guide though and google was not much of help for this. Perhaps the reason why people didn't share their scripts it's because you did not either beside the 'exemple' which only shows, as i mentioned before, only a clock with a white background. I did modified my compiz config as mentioned in the guide.
 
i hope i will get a chance to make your script work in my desktop, i was looking something like this beside conky.
I think that if people would take the time to look around here, look around in the install directory, read the guide, and/or simply type ```
gtk-desktop-info --help
``` in a terminal window there would not be questions like this. As K stated there is no use in using google to search since this is the only place you will find any info on the app. 

Don't mean to offend or just say 'RTFM' but everything was in the first post and in the guide.

Hippy

---

### Post by sirjoebob on 2009-04-30
I may have messed up the config file and template for the forecast plugin. Is there anywhere I can download just those files or reset them in any way?

---

### Post by kaivalagi on 2009-04-30
> **sirjoebob said:**
> I may have messed up the config file and template for the forecast plugin. Is there anywhere I can download just those files or reset them in any way?

Uninstall and reinstall the package through Synaptic to reset everything, that's probably the easiest solution.

Alternatively you could visit the launchpad site where the source files are hosted, you can download each file individually by navigating starting here: [http://bazaar.launchpad.net/~m-buck/+junk/gtk-desktop-info/files](http://bazaar.launchpad.net/~m-buck/+junk/gtk-desktop-info/files)

The config file for a plugin will be copied across to ~/.config/gtk-desktop-info folder when you first run the app for that plugin, so you should eit the version there. I would suggest you use a copy of the template file in your home directory next time so you can edit to your hearts content and still have the original to fall back to :)

Also, I think you may benefit from reading through the guide in detail, it should highlight some things to you.

Have fun

P.S Don't love me, love open source :)

---

### Post by sirjoebob on 2009-04-30
> Also, I think you may benefit from reading through the guide in detail, it should highlight some things to you.

Wow. I feel very noobish today. I am VERY impressed with this software and your fast, helpful response. I will reinstall and RTFM this time! Thanks so much

---

### Post by xeddog on 2009-04-30
I found out why my cron job wasn't working.  Apparently Jaunty must either have a bug in it, or something got changed.  But to get gtk-desktop-info to work in cron, I had to edit the crontab and add 
DISPLAY=:0.0 as the first line.

So now I get a new wallpaper on each monitor every 5 min (for now), then I pkill gtk-desktop-info and restart it to reconstruct the background so it looks transparent.  All automagically in cron.   Life is good again.

xeddog

---

### Post by kaivalagi on 2009-05-01
> **xeddog said:**
> I found out why my cron job wasn't working.  Apparently Jaunty must either have a bug in it, or something got changed.  But to get gtk-desktop-info to work in cron, I had to edit the crontab and add 
DISPLAY=:0.0 as the first line.

So now I get a new wallpaper on each monitor every 5 min (for now), then I pkill gtk-desktop-info and restart it to reconstruct the background so it looks transparent.  All automagically in cron.   Life is good again.

xeddog

Glad to hear you got it sorted, I guess the first line you added is to tell cron that the "local" screen is your one not something to do with root?

---

### Post by xeddog on 2009-05-01
I don't think this had anything to do with running as root or not.  The thread I got this from was talking about this problem having to do with python specifically.  

xeddog

---

### Post by Bruce M. on 2009-05-01
**[COLOR="Red"]Warning Partial quotes:[/COLOR]**

> **kaivalagi said:**
> I am starting to feel a little less helpful from here on in :mad:

> **kaivalagi said:**
> P.S Don't love me, love open source :)

My friend some of us love you for creating the *Open Source* you have sweat and toiled over to share with us to use.  :)

There are a LOT of people here (and other distros I might add) that appreciate the work you have done and the support you give.

[B][SIZE="5"]Lets hear it for K!

HIP HIP ...[/SIZE][/B]
{listening}

---

### Post by HippyRandall on 2009-05-01
> **Bruce M. said:**
> **[COLOR=Red]Warning Partial quotes:[/COLOR]**





My friend some of us love you for creating the *Open Source* you have sweat and toiled over to share with us to use.  :)

There are a LOT of people here (and other distros I might add) that appreciate the work you have done and the support you give.

[B][SIZE=5]Lets hear it for K!

HIP HIP ...[/SIZE][/B]
{listening}[B][SIZE=5]
...RY RANDALL!!! 
damnit
HOORAY!!![/SIZE][/B]

---

### Post by Bruce M. on 2009-05-01
Well ok, just for my friend:

[B][SIZE="5"]Hip Hip-py Randall!
HOO-RAW![/SIZE][/B]

:lolflag:

---

### Post by VCoolio on 2009-05-02
Thanks for this amazing app. For anyone who's interested: it works fine with Enlightenment / e17 too (bling module, provided that your gnome wallpaper is the same as your e17 one; ecomorph gives difficulties with black outline).

---

### Post by kaivalagi on 2009-05-02
> **VCoolio said:**
> Thanks for this amazing app. For anyone who's interested: it works fine with Enlightenment / e17 too (bling module, provided that your gnome wallpaper is the same as your e17 one; ecomorph gives difficulties with black outline).

Would it be worth me adding e17 to the --windowmanager option?

How would I go about getting the wallpaper settings programmactically within enlightenment? Any config file that stores the path??? command line tool to call etc?

On the ecomorph front, is there an equivalent option in it like the one I mention for the compiz workaround in the guide?

---

### Post by VCoolio on 2009-05-02
Hi, thought about adding e17 but it works with .edj files in which the wallpaper is stored, so that may be too much asked (you would have to somehow extract the .edj-file and then get the wallpaper; but the --wallpaper option works fine and also it uses the gnome-wallpaper by default, which then must be the same as the e17-wallpaper of course). 

And thanks for the tip, but I don't know yet what the black outline exactly is (it belongs to the window border I think, but disabling window borders doesn't help). When I find out I'll post here. But while e17 as a whole works pretty good despite pre-alpha status ecomorph still has some flaws. As said, with bling no problems.

---

### Post by kaivalagi on 2009-05-08
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

I have put together two new plugins

[LIST]
[*]“twitter” - this plugin provides information on all your twitter friends, shown newest to oldest - **[COLOR="Green"]note: to get running at the very least enter your username and password into the config file copied to ~/.config/gtk-desktop-info/plugin_twitter.config[/COLOR]**

[*]“processinfo” - this plugin provides process information, telling you a processes id, cpu usage and memory usage. The information can be sorted by cpu or memory usage
[/LIST]

The plugins are accompanied with default config, style and template files.

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.19_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.19_source.changes)

**gtk-desktop-info-data:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.11_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.11_source.changes)

The apt packages for both intrepid and jaunty should be available shortly

Chimo

[COLOR="Green"]Edit: I've aded a couple of screenshots showing the default output for the new plugins (for the --colour=green option which I use)[/COLOR]

---

### Post by sirjoebob on 2009-05-08
Fantastic. Running Jaunty here. Will update ASAP. Thanks for your continued efforts!

---

### Post by arindom on 2009-05-09
Thanks kaivalagi for adding processinfo. This is wonderful.

---

### Post by cailamaia on 2009-05-09
Hi! I'm still new to linux, and trying to learn how everything works. I can't quite seem to work out how to get this up and running. I seem to have managed to get everything to install properly, but I have no idea how to get the scripts to run. ^^;;

Is there a tutorial somewhere out there that one of y'all could be kind enough to post for me?

Thanks.

---

### Post by kaivalagi on 2009-05-10
> **cailamaia said:**
> Hi! I'm still new to linux, and trying to learn how everything works. I can't quite seem to work out how to get this up and running. I seem to have managed to get everything to install properly, but I have no idea how to get the scripts to run. ^^;;

Is there a tutorial somewhere out there that one of y'all could be kind enough to post for me?

Thanks.

Take a look at the guide, it talks you through the significant areas and gives details on an example script which runs the app several times for various plugin options. Also by running "gtk-desktop-info -h" you will get some brief details on options too.

You can open the guide by running the "gtk-desktop-info.guide" command, it assumes you have evince (pdf viewer) installed. Alternatively the pdf file can be found in /usr/share/gtk-desktop-info/

---

### Post by exegeses on 2009-05-10
hullo, i have read every little post before posting and I would like to say, gtk-desktop-info is awesome!

second, I have never used conky, I know what it is, but, never used it.

third:

> **Bruce M. said:**
> OK, as promised here's what mine looks like. It's the straight out of the box config with LOCALE = es (Spanish)

Here is what it looks like:
[CENTER][[IMG]http://img21.imageshack.us/img21/4342/desktopjg0.th.gif[/IMG]](http://img21.imageshack.us/my.php?image=desktopjg0.gif)


[[IMG]http://img502.imageshack.us/img502/4968/desktop2kg7.th.gif[/IMG]](http://img502.imageshack.us/my.php?image=desktop2kg7.gif)[/CENTER]

...
Bruce

great work!! I've tried this, and in Spanish. cool, congrats man.
buen trabajo! Intenté este , y en español. copado, felicitaciones, man.

> **Bruce M. said:**
> [CENTER]:guitar: **[COLOR="DarkRed"][SIZE="5"]Papa's got a brand new screen![/SIZE][/COLOR]** :guitar:

[[IMG]http://img7.imageshack.us/img7/2179/13feb09ix8.th.gif[/IMG]](http://img7.imageshack.us/my.php?image=13feb09ix8.gif)[/CENTER]

Take a look at the top left K!

**mydesktop.sh** - Note: *test.template* and *--noheader* I've put it in the test.template:
```
#!/bin/sh

# kill all instances of the app before starting new ones
pkill -f gtk_desktop_info.py

# wait for a sec
sleep 1

gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=750 --height=240 --x=0 --y=750 --windowmanager=xfce4 --template=/home/bruloo/gtk-desk/test.template --noheader --plugin=forecast &
```
and my: **test.template**
```
<div id="wrapper">
<table cellpadding="0" cellspacing="0" border="0">
<tr>
<td><table cellspacing="0" cellpadding="0" border="0">
	<tr>
		<td><img src="file:///home/bruloo/Images/Captain_Canuck/SgtCanuck_256_QS.png" border="0" width="50"/></td>
		<td valign="middle" class="largedarkitalic">&nbsp; Estado del Tiempo</td>
	</tr>
</table></td>
<td rowspan="2">	<div class="contenttop"><br>
		<span class="mediumlight">los próximos días</span>
	</div>
	<div class="forecast">
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=1]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=1] - [--datatype=SS --startday=1]</span>
		  <span><img src="[--datatype=WF --startday=1 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=1 --hideunits] / [--datatype=LT --startday=1 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=1]</span><br><br>
		  <span class="mediumlight">[--startday=1 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=2]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=2] - [--datatype=SS --startday=2]</span>
		  <span><img src="[--datatype=WF --startday=2 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=2 --hideunits] / [--datatype=LT --startday=2 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=2]</span><br><br>
		  <span class="mediumlight">[--startday=2 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=3]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=3] - [--datatype=SS --startday=3]</span>
		  <span><img src="[--datatype=WF --startday=3 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=3 --hideunits] / [--datatype=LT --startday=3 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=3]</span><br><br>
		  <span class="mediumlight">[--startday=3 --datatype=CC]</span>
		</div>
		<div class="day">
		  <span class="mediumlight">[--datatype=DW --startday=4]</span><br>
		  <span class="mediumdark">[--datatype=SR --startday=4] - [--datatype=SS --startday=4]</span>
		  <span><img src="[--datatype=WF --startday=4 --spaces=3]" width="60"/></span><br>
		  <span class="mediumdark">[--datatype=HT --startday=4 --hideunits] / [--datatype=LT --startday=4 --hideunits]</span><br>
		  <span class="mediumdark">[--datatype=PC --startday=4]</span><br><br>
		  <span class="mediumlight">[--startday=4 --datatype=CC]</span>
		</div>
	</div>
	<div class="contentbottom" align="right"><br>
		<span class="smalllight">Fetched: </span><span class="smalldark">[--datatype=LF]</span>
	</div></td>
</tr>
<tr>
<td valign="top">	<div class="contenttop" align="center">
		<span class="hugelight">[--datatype=CC]</span>
	</div>
	<div>
		<div class="contentleft">
			<div class="current">
			<img src="[--datatype=WF]" width="80"/> 
			[--datatype=HT --hideunits] / [--datatype=LT --hideunits]
			</div>      
			<div class="moon"><br>
			<img src="[--datatype=MF]" width="60"/> 
			[--datatype=MP]
			</div>      
			<div class="wind"><br>
			<img src="[--datatype=BS]" width="60"/> 
			[--datatype=WD]<br>
			[--datatype=WS]
			</div>
		</div>
		<div class="contentright"><br><br>
		  <span class="mediumlight" align="left">UV: </span>[--datatype=UI] - [--datatype=UT]<br>
		  <span class="mediumlight" align="right">Humedad: </span>[--datatype=HM]<br>
		  <span class="mediumlight" align="right">Punto de Rosco: </span>[--datatype=DP --hideunits]<br>
		  <span class="mediumlight" align="right">Presión: </span>[--datatype=BR]<br><br>

		  <span class="mediumlight" align="right">Salida del Sol: </span>[--datatype=SR]<br>
		  <span class="mediumlight" align="right">Oscuro: </span>[--datatype=SS]
		</div>
	</div></td>
</tr>
</table>
</div>
```
How sweet it is! :KS

Have a nice day.
Bruce

simply awesome!
also tried it, thanks

> **useResa said:**
> I justed learned about this app from Bruce and have not done any tweaking (yet).
Just like to inform that it also runs nicely on Xubuntu Jaunty. If I am correct this has not yet been posted and/or confirmed.

Attached a screenshot of the app running in Xubuntu Jaunty that I have installed on an old PIII (933 MHz) with 256 Mb memory. Amazing how little resources it uses.

Compliments to the dev.
liked this. great!


###################################################################3
###################################################################3
###################################################################3

well, now, the question goes like this: 
I would also like to view the disk space total/used/free as shown in this screenshot (attatched)

can anyone point me in the right direction?
thanks in advance!

---

### Post by Bruce M. on 2009-05-10
> **exegeses said:**
> well, now, the question goes like this: 
I would also like to view the disk space total/used/free as shown in this screenshot (attatched)

can anyone point me in the right direction?
thanks in advance!

Hola exegeses

WOW!! Gracias! So glad you like my work.

**Offtopic:**

To answer your question, it's pure conky and should be posted in a thread like: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") but it's a simple request:

```
fs_bar 	(height),(width) fs 	 Bar that shows how much space is used on a file system. height is the height in pixels. fs is any file on that file system.
fs_bar_free 	(height),(width) fs 	Bar that shows how much space is free on a file system. height is the height in pixels. fs is any file on that file system.
fs_free 	(fs) 	Free space on a file system available for users.
fs_free_perc 	(fs) 	Free percentage of space on a file system available for users.
fs_size 	(fs) 	File system size.
fs_type 	(fs) 	File system type.
fs_used 	(fs) 	File system used space.
fs_used_perc
```

so the three you want are:
Total = **fs_size**
Used: = **fs_used**
Free: = **fs_free**

Que tengas un buen día
Bruce

---

### Post by exegeses on 2009-05-11
> **Bruce M. said:**
> Hola exegeses

WOW!! Gracias! So glad you like my work.

**Offtopic:**

To answer your question, it's pure conky and should be posted in a thread like: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") but it's a simple request:

```
fs_bar 	(height),(width) fs 	 Bar that shows how much space is used on a file system. height is the height in pixels. fs is any file on that file system.
fs_bar_free 	(height),(width) fs 	Bar that shows how much space is free on a file system. height is the height in pixels. fs is any file on that file system.
fs_free 	(fs) 	Free space on a file system available for users.
fs_free_perc 	(fs) 	Free percentage of space on a file system available for users.
fs_size 	(fs) 	File system size.
fs_type 	(fs) 	File system type.
fs_used 	(fs) 	File system used space.
fs_used_perc
```

so the three you want are:
Total = **fs_size**
Used: = **fs_used**
Free: = **fs_free**

Que tengas un buen día
Bruce

thanks!! now I have my conky up and running.
have a nice week!

---

### Post by KhaaL on 2009-05-12
Thanks for a superb app! now for a bug report, are you aware that there is a problem with character encoding? this is with google calendar...

11.15 tandläkarebesök, 6:e våningen
becomes instead:
11.15 tandlÃ¤karebesÃ¶k, 6:e vÃ¥ningen

Also a feature I'd like to request is alternative login method so you don't have to type in your password in clear text in the config file.

---

### Post by kaivalagi on 2009-05-12
> **KhaaL said:**
> Thanks for a superb app! now for a bug report, are you aware that there is a problem with character encoding? this is with google calendar...

11.15 tandläkarebesök, 6:e våningen
becomes instead:
11.15 tandlÃ¤karebesÃ¶k, 6:e vÃ¥ningen

Also a feature I'd like to request is alternative login method so you don't have to type in your password in clear text in the config file.

Your welcome

The google calendar problem also exists with the equivalent conky script, it is a real pain.

When work gets a little less stressful I'll take some serious time to track down the problem. Unicode in python IMHO sucks...

Clear text in config files shouldn't be a concern so long as it is in your home folder, it is secure. To provide an alternative would mean creating a small app to encrypt the password before putting it in the config file...

---

### Post by KhaaL on 2009-05-12
Oh, I was thinking of loggin in by an existing cookie or something similiar - i think i've seen somthing similiar in other applications so I assumed it would be possible :)

---

### Post by kaivalagi on 2009-05-12
> **KhaaL said:**
> Oh, I was thinking of loggin in by an existing cookie or something similiar - i think i've seen somthing similiar in other applications so I assumed it would be possible :)

Cookies are fine if you login to the calendar via the browser. I don't, I have it setup in thunderbird (lightning) and using this app.

Also what if you have 2 calendars with separate logins, this is supported by the plugin. Only one calendar could be fetched when using cookies though.

---

### Post by pemur1 on 2009-05-23
Oh, oh. Looks like I found something else I want to work on.

You better run away now, Bruce. This may take longer than getting my conky up and running. :D

---

### Post by Bruce M. on 2009-05-23
> **pemur1 said:**
> Oh, oh. Looks like I found something else I want to work on.

You better run away now, Bruce. This may take longer than getting my conky up and running. :D

Ahhhh but I'm not an expert on this one. All I have is the weather.  :)

---

### Post by pemur1 on 2009-05-23
> **Bruce M. said:**
> Ahhhh but I'm not an expert on this one. All I have is the weather.  :)

Well,,, that's a start. And that's all I need. :)

---

### Post by Bruce M. on 2009-05-25
> **pemur1 said:**
> Well,,, that's a start. And that's all I need. :)

It's [here]("http://ubuntuforums.org/showpost.php?p=6729212&postcount=68") :)

Have a nice day.
Bruce

---

### Post by kaivalagi on 2009-06-19
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

I have fixed a few things and added a couple of interesting new options

[LIST]
[*]Added --backgroundblend and --backgroundcolour options for visual seperation of output from wallpaper if required
[*]Fixed song length output in the rhythmbox plugin when songs are an hour long or more
[*]Added copy option to right click, enabling the copying of html content to the clipboard for testing
[*]Moved common functions into a plugin_common module
[/LIST]

I've attached an image with some screenshots showing the possibilities with the new --backgroundblend and --backgroundcolour options. Details in the image, and from the help:

```
--backgroundblend=NUMBER
                      default:[0] The optional blending ratio for the
                      backgroundcolour which is set. The default of 0 does
                      no blending, the maximum of 100 will blend "out" all
                      the wallpaper. Use this option to give some visual
                      separation to the output from the wallpaper.
--backgroundcolour=RGBValues
                      default:[0,0,0] The optional colours to use for
                      blending into the background. They should be input in
                      the form "R,G,B". Not used if --backgroundblend=0

```

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.20_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.20_source.changes)

The apt packages for both intrepid and jaunty should be available shortly

Chimo

---

### Post by kaivalagi on 2009-06-21
**[COLOR="Green"][SIZE="4"]UPDATE[/SIZE](frenzy :))[/COLOR]**

I have added rounding to the blended output, see the screenshot for the idea

[LIST]
[*]Added --backgroundcorner option for setting the radius (in pixels) used for the rounding of blended output corners, only used if --backgroundblend not zero
[*]Updated verbose output to display all options
[/LIST]

An additional option has been added, from help:

```
  --backgroundcorner=NUMBER
                        default:[10] The optional corner radius (in pixels) to
                        use when applying background blending. Not used if
                        --backgroundblend=0
```

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.21_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.21_source.changes)

The apt packages for both intrepid and jaunty should be available shortly

Chimo

---

### Post by NorthCarolina01 on 2009-06-21
Thanks for nice blog .

julie

---

### Post by kaivalagi on 2009-06-21
> **NorthCarolina01 said:**
> Thanks for nice blog .

julie

Are you referring to the redirect to here from my site?

It's just that I had my site forum spammed so I turned it off for now :)

edit: replaced with wordpress, will be posted to over time...

---

### Post by HippyRandall on 2009-06-21
very cool! Haven't done any playing around with this app or any other for a while...maybe it's time to start up again ;)

---

### Post by kaivalagi on 2009-06-21
> **HippyRandall said:**
> very cool! Haven't done any playing around with this app or any other for a while...maybe it's time to start up again ;)

Nice you see you in here Hippy, have a tinker and as always any ideas/niggles/feedback just let me know.....I am getting my head around the python image library, in code manipulation of images :)

Just got the bare essentials in for kaivalagi.com - using wordpress...any suggestions on that front let me know too!

---

### Post by Bruce M. on 2009-06-21
> **HippyRandall said:**
> very cool! Haven't done any playing around with this app or any other for a while...maybe it's time to start up again ;)

Yo Hippy how ya doing bud? Good to see you around.  :)

CHIMO!

---

### Post by HippyRandall on 2009-06-21
Still healing up from a third back surgery but getting better. I know I haven't updated my site for a bit but the pain killers make me less than focused ;)

---

### Post by Bruce M. on 2009-06-22
> **HippyRandall said:**
> Still healing up from a third back surgery but getting better. I know I haven't updated my site for a bit but the pain killers make me less than focused ;)

Yea, that makes sense. But at least you're on the downhill slope now and that's really good to hear.  Unless there's more surgery scheduled for the future or is that the final one?

Have a GREAT day!
Bruce

---

### Post by kaivalagi on 2009-06-22
I thought I'd share a simple use of the --plugin=null option for all the UK BBC license payers out there. When I am drinking my coffee early in the morning and catching up on the emails/feeds/twitter/news I like to amongst other things watch bbc news.

I have setup a very simple html template to use on the desktop to watch bbc streams at the click of a button, fullscreen is supported too :)

See off.jpg for what it looks like at startup, and on.jpg when watching tv (BBC2 in this case)

To achieve this call the app using something like the following (ensure the template path is correct for where you put the file):

```
gtk-desktop-info --plugin=null --template=/home/USER/.config/gtk-desktop-info/tv/url.livetv.template --width=550 --height=500 --x=930 --y=25 --backgroundblend=30 &
```

The null plugin is used because no python code is needed to generate the html output, it is driven solely off html/css/javascript in the template and from web content.

The template looks like this:

```
<table border=0 cellpadding=0 cellspacing=0 width="100%">
	<tr align="center">
		<td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_news24/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbcnews.png" /></a></td>
		<td>&nbsp;</td>
		<td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_one_london/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc1.png" /></a></td>
		<td>&nbsp;</td>
		<td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_two_england/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc2.png" /></a></td>
		<td>&nbsp;</td>
		<td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_three/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc3.png" /></a></td>
		<td>&nbsp;</td>
		<td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_four/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc4.png" /></a></td>
		<td>&nbsp;</td>
		<td><a href="#" onclick="javascript:document.all.tv.src=''"><img src="file:///home/mark/.config/gtk-desktop-info/tv/off.png" /></a></td>
	</tr>
</table><br>
<iframe width="528" height="429" id="tv" src=""></iframe>
```

Note: The template will need adjustment to ensure the image paths are correct for where you put the files.

I've attached the template and accompanying png images in a tarball in case anyone wants to use them :)

Chimo

---

### Post by Bruce M. on 2009-06-22
> **kaivalagi said:**
> I thought I'd share a simple use of the --plugin=null option for all the UK BBC license payers out there.

Chimo

> Don't forget, to watch TV online as it's being broadcast, you still need a TV licence.

**TV Licence?** :confused: To "watch TV"?

CHIMO!
Bruce

PS: Will it work in Argentina?

---

### Post by kaivalagi on 2009-06-23
> **Bruce M. said:**
> **TV Licence?** :confused: To "watch TV"?

CHIMO!
Bruce

PS: Will it work in Argentina?

I manage to watch tv when surfing, I am watching the news right now :)

Never tried watching bbc in Argentina, in theory I could because I have a TV licence...but I bet the streaming is limited to the UK only

---

### Post by HippyRandall on 2009-06-23
> **Bruce M. said:**
> Yea, that makes sense. But at least you're on the downhill slope now and that's really good to hear.  Unless there's more surgery scheduled for the future or is that the final one?

Have a GREAT day!
Bruce

*fingers crossed and knocking on wood*...this should be the last surgery. the implant works well but they had to do a lamenectomy ( basically, grind away a portion of my spine ) to insert the lead and that has been the bulk of the recovery. quite a painful operation.

---

### Post by HippyRandall on 2009-06-23
> **Bruce M. said:**
> **TV Licence?** :confused: To "watch TV"?

CHIMO!

DITTO!! Licence for TV?!?!

---

### Post by kaivalagi on 2009-06-23
> **HippyRandall said:**
> DITTO!! Licence for TV?!?!

"Only in the UK"....makes a change as it's normally "Only in the US"

[http://www.bbc.co.uk/info/licencefee/](http://www.bbc.co.uk/info/licencefee/)

With any BBC channels there are NO commercial adverts :)

---

### Post by snkiz on 2009-06-23
quick question could this be adapted to output to an actual web page? I love to use it for server stats. Got a place all ready on my page :D

---

### Post by HippyRandall on 2009-06-23
> **kaivalagi said:**
> "Only in the UK"....makes a change as it's normally "Only in the US"

[http://www.bbc.co.uk/info/licencefee/](http://www.bbc.co.uk/info/licencefee/)

With any BBC channels there are NO commercial adverts :)
that is the most bizarre thing I have heard of. my initial reaction was "damn I am glad we don't have that on this side of the pond." and then I realized how many dumbass commercials I seen every hour of every day. Now I want it!

---

### Post by kaivalagi on 2009-06-23
> **HippyRandall said:**
> that is the most bizarre thing I have heard of. my initial reaction was "damn I am glad we don't have that on this side of the pond." and then I realized how many dumbass commercials I seen every hour of every day. Now I want it!

On face value is seems wrong but the quality of tv production with the BBC is first rate, the documentaries and news are excellent

---

### Post by kaivalagi on 2009-06-23
> **snkiz said:**
> quick question could this be adapted to output to an actual web page? I love to use it for server stats. Got a place all ready on my page :D

You can either use the --url option to display a page directly in the window or use can use the null plugin as I have with an <iframe...> tag to load contents into a width/height restricted "sub" page. This could in theory hold a bunch of web pages in one window :)

Help on iframe tags can be found here: [http://www.w3schools.com/TAGS/tag_iframe.asp](http://www.w3schools.com/TAGS/tag_iframe.asp)

---

### Post by Bruce M. on 2009-06-23
> **kaivalagi said:**
> "Only in the UK"....makes a change as it's normally "Only in the US"

[http://www.bbc.co.uk/info/licencefee/](http://www.bbc.co.uk/info/licencefee/)

With any BBC channels there are NO commercial adverts :)

WoW! Expensive. Does this price include "cable" or antenna?

But for no adverts that might be worth it, I hate the damn things.
The few British shows we get here are the same, once it starts it runs until it finishes.

Loved the "Carry on Gang! movies and "On the Buses" (shows my age huh!)

CHIMO!

---

### Post by snkiz on 2009-06-23
> **kaivalagi said:**
> You can either use the --url option to display a page directly in the window or use can use the null plugin as I have with an <iframe...> tag to load contents into a width/height restricted "sub" page. This could in theory hold a bunch of web pages in one window :)

Help on iframe tags can be found here: [http://www.w3schools.com/TAGS/tag_iframe.asp](http://www.w3schools.com/TAGS/tag_iframe.asp)

good to know. lol I've just dipped a toe in web devlopment and thats page has been invaluable

---

### Post by kaivalagi on 2009-06-24
I just thought I'd post my latest screenshot using all the features I have recently added (the music desktop art comes from the rhythmbox desktop art plugin). I have both BBC live streams and music lyrics supported from one area, I've posted a second screenshot showing the lyrics running rather than the iplayer.

I'm using the whole of my second monitor which is 1440x900 :)

I've also attached all the custom templates (minus the email) and the startup script in an archive

A little credit goes to eightmillion for his song lyrics script which I use from the shell plugin - it is also in the archive

Chimo

---

### Post by kaivalagi on 2009-07-02
For better or for worse I have made the switch from Rhythmbox to Banshee, as it seems it will be the default music player in Karma Koala. 

So.....A Banshee plugin is in progress, shouldn't be too far away from completion now :)

---

### Post by martynp on 2009-07-02
Thanks for making my day!

---

### Post by kaivalagi on 2009-07-03
**[COLOR="DarkRed"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

I have added a banshee plugin with the same behaviours as the exaile and rhythmbox ones, and also done a couple of other things...

[LIST]
[*]Added **Banshee plugin** and default templates
[*]Added SORTBY option in config of deluge plugin, takes either "progress", "queue", "eta", "download", "upload" or "ratio". Also note that a torrent's state supersedes anything else for sorting, in the order, from top to bottom: downloading, seeding, queued, paused, unknown
[*]Updated default connection timeout to be 60 seconds for the googlecalendar plugin, lots of timeouts recently...you can also change it via your ~/.config/gtk-desktop-info/plugin_googlecalendar.config file
[/LIST]

**Deluge SORTBY**

If you have a previous version of the app installed and want to use the SORTBY method for the deluge plugin, take a look at the default config file in /usr/share/gtk-desktop-info/config after updating and alter your own version which resides in ~/.config/gtk-desktop-info to suit your needs

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.22_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.22_source.changes)

**gtk-desktop-info-data:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.12_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.12_source.changes)

The apt packages for intrepid, jaunty **_and karma_** should be available shortly - eta from launchpad is approx 1 hour from this post

Chimo

---

### Post by stepper on 2009-07-07
Hey Mark, any good python tutorials I can study? I'm still on the mission to get exaile plugin a playback control function. 
I'm using the [adeskbar]("https://launchpad.net/adeskbar") to control exaile since its written in pygtk I guess it can be merged with gtk-desktop info. Any help appreciated.

---

### Post by kaivalagi on 2009-07-07
> **stepper said:**
> Hey Mark, any good python tutorials I can study? I'm still on the mission to get exaile plugin a playback control function. 
I'm using the [adeskbar]("https://launchpad.net/adeskbar") to control exaile since its written in pygtk I guess it can be merged with gtk-desktop info. Any help appreciated.

As this app generates output as html you wont be able to control exaile through python, there is no feed back through to the app from the rendered html (one way only)

You could see what you can done w.r.t. using javascript to run command line calls maybe?

Alternatively have a look at the Rhythmbox-Desktop-Art package in my repo to get ideas on what you could create for exaile from that angle...

---

### Post by kaivalagi on 2009-07-07
There seems to be new issues with the weather.com forecast, it no longer supports more than 4 days forecast, regardless of the licence you use. The current URL used in the code has also slightly changed.

I have a lot of other changes currently in this app which are not ready to rollout yet, so can't release a proper fix right now.

To get over the problem for the short term please the attached file in your installs by doing the following:

[LIST=1]
[*]Extract .py file from the attached tarball to /tmp/
[*]Run the following "sudo cp /tmp/plugin_forecast.py /usr/share/gtk-desktop-info"
[/LIST]

I will update the package soon, although I have more important things to worry about other than my scripts at the mo :)

---

### Post by Bruce M. on 2009-07-08
> **kaivalagi said:**
> There seems to be new issues with the weather.com forecast, it no longer supports more than 4 days forecast, regardless of the licence you use. The current URL used in the code has also slightly changed.

Thats the third time since Dec 2007 that they have changed things. 

[Dec 25, 2007]("http://ubuntuforums.org/showpost.php?p=4013119&postcount=1173") - My first contact with **weather.sh** - when that stopped working it was lvlph that came to the rescue on Jan 13 2008 - [Conky Weather Revisited V2]("http://ubuntuforums.org/showthread.php?p=4130735#post4130735") ... when that stopped working because of changes... along comes kaivalagi and [Conky Weather Forecast]("http://ubuntuforums.org/showthread.php?t=869328") 24 July 08, almost a year ago to the day.

Was kaivalagi happy - noooooooo he had to go farther and create this gem (that's a huge thanks mate.) and today it's not working. {sigh} see image.

PANIC so I come here, only to see a fix - WoW mate, you are better than good.

Curious part is my Conky Weather Forecast is working fine :confused:

Thanks.
CHIMO!
Bruce

---

### Post by Bruce M. on 2009-07-08
Now that's better.

**Thanks K! Your The M of the Year!**

---

### Post by kaivalagi on 2009-07-08
> **Bruce M. said:**
> Curious part is my Conky Weather Forecast is working fine :confused:

I had removed some of the url content from the gtk forecast plugin to allow for forecasts up to 9 days using a "special" registration key pair, I didn't do this with the conky script...the change they have made to the xoap service at weather.com means the url content I removed is now forced back in, and this limits the forecast back to 4 days ahead only :(

---

### Post by Bruce M. on 2009-07-08
> **kaivalagi said:**
> I had removed some of the url content from the gtk forecast plugin to allow for forecasts up to 9 days using a "special" registration key pair, I didn't do this with the conky script...the change they have made to the xoap service at weather.com means the url content I removed is now forced back in, and this limits the forecast back to 4 days ahead only :(

):P Well, like they say you can only live one day at a time. Todays weather I'm not "so" interested in, looks out window, open if nice, close if not.

However, knowing what the weekend will (possibly ... maybe) be like is a plus.

CHIMO!
Bruce

---

### Post by dumblebee100 on 2009-07-25
Well this is my Gtk-desktop-info deluge setup 

if any one likes my setup please comment on it ..

and Im in a lot of problems with gtk-desktop-info 

I will ask you later ..bcz its already late today ....bcz thats a big story to write up

---

### Post by kaivalagi on 2009-07-26
> **dumblebee100 said:**
> Well this is my Gtk-desktop-info deluge setup 

if any one likes my setup please comment on it ..

and Im in a lot of problems with gtk-desktop-info 

I will ask you later ..bcz its already late today ....bcz thats a big story to write up

You have my attention :)

What issues are you having.....

---

### Post by dumblebee100 on 2009-07-26
As I said I have some problems regarding gtk-desktop-info 
here we go 

lately I tried deluge plugin and I changed all the templates css and other stuff for my tastes ..

Then I tried forecast plugin simply because Its really more graphical than conky and it provides map of my area ..that was cool 

Here is my config file(plugin_forecast.config) 
```
# config settings for forecast plugin

# Template file determining the format for the top of the info.
HEADERTEMPLATE = 

# The template file to generate output. A displayable item in the file is in the form [--datatype=HT --startday=1].
# The following are possible options within each item:
# --location=CODE : The location code for weather data.
# --datatype=TYPE : The data type options are: DW (Day of Week), WF (Weather Font output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), VI (Visibility), WD (Wind Direction), WA (Wind Angle - in degrees), WS (Wind Speed), WG (Wind Gusts), BF (Bearing Font), BS (Bearing font with Speed), CN (City Name), CO (Country), OB (Observatory), SR (SunRise), SS (SunSet), DL (DayLight), MP (Moon Phase), MF (Moon Font), BR (Barometer Reading), BD (Barometer Description), UI (UV Index), UT (UV Text), DP (Dew Point), LU (Last Update at weather.com), LF (Last Fetch from weather.com)
# --startday=NUMBER : Define the starting day number, if omitted current conditions are output
# --endday=NUMBER : Define the ending day number, if omitted only starting day data is output
# --night : switch output to night data, if omitted day output will be output
# --shortweekday : Shorten the day of week data type to 3 characters
# --imperial : request imperial units, if omitted output is in metric
# --beaufort : request beaufort scale for wind speeds, if omitted output is either metric/imperial
# --hideunits :  Hide units such as mph or C, degree symbols (°) are still shown
# --hidedegreesymbol : Hide the degree symbol used with temperature output, this is only valid if used in conjunction with --hideunits
# --spaces=NUMBER : Define the number of spaces between ranged output
# --minuteshide=NUMBER : Works only with LU and LF. If present, hides the date part of the LU or LF timestamp if the day of the timestamp is today. The time part is also hidden, if the timestamp is older than minutes specified in this argument. If set to 0, the time part is always shown. If set to -1, the value EXPIRY_MINUTES from the config file is used
TEMPLATE = 

# The location code for weather data.
# Use the following url to determine your location code by city name:
# http://xoap.weather.com/search/search?where=Norwich
LOCATION = INXX0057

# How long before the cache is deemed out-of-date, so next refresh it will be updated from the weather.com website
EXPIRY_MINUTES = 30

# The format of time output
TIMEFORMAT = %H:%M

# The format of date output
DATEFORMAT = %Y-%m-%d

# with no setting the default locale of the system is used, if supported.
# If no translation is available then the plugin defaults to english
LOCALE = 

# Your registered partner id
XOAP_PARTNER_ID =  1113851283

# Your registered licence key
XOAP_LICENCE_KEY = 241b4cd9bac9846c

# maximum days forecast range, only change this if you have an extended license
MAXIMUM_DAYS_FORECAST = 4

# If set to true new weather data will retrieved each time the plugin runs
REFETCH = false

# The folder where forecast data cache files are stored. Best to leave the default setting
CACHE_FOLDERPATH = /tmp/

# Define the number of seconds before a connection timeout can occur. 
# Not applicable at command line when using templates
CONNECTION_TIMEOUT = 10

```

well this is my plugin_forecast.py

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-
###############################################################################
# plugin_forecast.py is a plugin for gtk-desktop-info to display weather
# conditions and forecasting information. It uses the weather.com xoap service
#
#  Author: Kaivalagi
# Created: 23/11/2008
from datetime import datetime, timedelta
from optparse import OptionParser
from plugin_common import getHTMLText, getSpaces, getTypedValue, getHoursMinutesStringFromSeconds, isNumeric
from xml.dom import minidom
import codecs
import fileinput
import gettext
import locale
import logging
import os
import re
import shutil
import socket
import sys
import time
import traceback
import urllib2
import uuid

try:
    import cPickle as pickle
except ImportError:
    import pickle

app_name = "gtk-desktop-info"
app_path = os.path.dirname(os.path.abspath(__file__))
module_name = __file__.replace(os.path.dirname (__file__) + "/", "").replace(".pyc","").replace(".py", "")

# default to standard locale translation
domain = module_name
localedirectory = app_path + "/locale"
gettext.bindtextdomain(domain, localedirectory)
gettext.textdomain(domain)
gettext.install(domain)

# start ignoring translations required at runtime
def _(text): return text

class ForecastText:

    # translatable dictionaries
    conditions_text = {
        "0": _(u"Tornado"),
        "1": _(u"Tropical Storm"),
        "2": _(u"Hurricane"),
        "3": _(u"Severe Thunderstorms"),
        "4": _(u"Thunderstorms"),
        "5": _(u"Mixed Rain and Snow"),
        "6": _(u"Mixed Rain and Sleet"),
        "7": _(u"Mixed Precipitation"),
        "8": _(u"Freezing Drizzle"),
        "9": _(u"Drizzle"),
        "10": _(u"Freezing Rain"),
        "11": _(u"Light Rain"),
        "12": _(u"Rain"),
        "13": _(u"Snow Flurries"),
        "14": _(u"Light Snow Showers"),
        "15": _(u"Drifting Snow"),
        "16": _(u"Snow"),
        "17": _(u"Hail"),
        "18": _(u"Sleet"),
        "19": _(u"Dust"),
        "20": _(u"Fog"),
        "21": _(u"Haze"),
        "22": _(u"Smoke"),
        "23": _(u"Blustery"),
        "24": _(u"Windy"),
        "25": _(u"N/A"),
        "26": _(u"Cloudy"),
        "27": _(u"Mostly Cloudy"),
        "28": _(u"Mostly Cloudy"),
        "29": _(u"Partly Cloudy"),
        "30": _(u"Partly Cloudy"),
        "31": _(u"Clear"),
        "32": _(u"Clear"),
        "33": _(u"Fair"),
        "34": _(u"Fair"),
        "35": _(u"Mixed Rain and Hail"),
        "36": _(u"Hot"),
        "37": _(u"Isolated Thunderstorms"),
        "38": _(u"Scattered Thunderstorms"),
        "39": _(u"Scattered Showers"),
        "40": _(u"Heavy Rain"),
        "41": _(u"Scattered Snow Showers"),
        "42": _(u"Heavy Snow"),
        "43": _(u"Heavy Snow"),
        "44": _(u"N/A"),
        "45": _(u"Scattered Showers"),
        "46": _(u"Snow Showers"),
        "47": _(u"Isolated Thunderstorms"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
    }

    day_of_week_short = {
        "Today": _(u"Now"),
        "Monday": _(u"Mon"),
        "Tuesday": _(u"Tue"),
        "Wednesday": _(u"Wed"),
        "Thursday": _(u"Thu"),
        "Friday": _(u"Fri"),
        "Saturday": _(u"Sat"),
        "Sunday": _(u"Sun")
    }

    # font based character sets, untranslatable

    # ConkyWeather.ttf based output
    conditions_weather_font = {
        "0": u"1", #Tornado
        "1": u"2", #Tropical Storm
        "2": u"3", #Hurricane
        "3": u"n", #Severe Thunderstorms
        "4": u"m", #Thunderstorms
        "5": u"x", #Mixed Rain and Snow
        "6": u"x", #Mixed Rain and Sleet
        "7": u"y", #Mixed Precipitation
        "8": u"s", #Freezing Drizzle
        "9": u"h", #Drizzle
        "10": u"t", #Freezing Rain
        "11": u"h", #Light Rain
        "12": u"i", #Rain
        "13": u"p", #Snow Flurries
        "14": u"p", #Light Snow Showers
        "15": u"8", #Drifting Snow
        "16": u"q", #Snow
        "17": u"u", #Hail
        "18": u"w", #Sleet
        "19": u"7", #Dust
        "20": u"0", #Fog
        "21": u"9", #Haze
        "22": u"4", #Smoke
        "23": u"6", #Blustery
        "24": u"6", #Windy
        "25": u"-", #N/A
        "26": u"f", #Cloudy
        "27": u"D", #Mostly Cloudy - night
        "28": u"d", #Mostly Cloudy - day
        "29": u"C", #Partly Cloudy - night
        "30": u"c", #Partly Cloudy - day
        "31": u"A", #Clear - night
        "32": u"a", #Clear - day
        "33": u"B", #Fair - night
        "34": u"b", #Fair - day
        "35": u"v", #Mixed Rain and Hail
        "36": u"5", #Hot
        "37": u"k", #Isolated Thunderstorms - day
        "38": u"k", #Scattered Thunderstorms - day
        "39": u"g", #Scattered Showers - day
        "40": u"j", #Heavy Rain
        "41": u"o", #Scattered Snow Showers - day
        "42": u"r", #Heavy Snow
        "43": u"r", #Heavy Snow
        "44": u"-", #N/A
        "45": u"G", #Scattered Showers - night
        "46": u"O", #Scattered Snow Showers - night
        "47": u"K", #Isolated Thunderstorms - night
        "na": u"-", #N/A
        "-": u"-" #N/A
    }

    conditions_moon_icon = {
        "0": u"24",
        "1": u"01",
        "2": u"02",
        "3": u"03",
        "4": u"04",
        "5": u"05",
        "6": u"06",
        "7": u"07",
        "8": u"08",
        "9": u"09",
        "10": u"10",
        "11": u"11",
        "12": u"12",
        "13": u"13",
        "14": u"13",
        "15": u"13",
        "16": u"14",
        "17": u"15",
        "18": u"16",
        "19": u"17",
        "20": u"18",
        "21": u"19",
        "22": u"20",
        "23": u"21",
        "24": u"22",
        "25": u"23",
        "26": u"23",
        "27": u"23",
        "28": u"23",
        "29": u"24",
        "N/A": u"",
        "na": u"",
        "-": u""
    }

    # this now returns ascii code
    bearing_icon = {
        "calm": "00",
        "VAR": "01",
        "S": "05",
        "SSW": "06",
        "SW": "07",
        "WSW": "08",
        "W": "09",
        "WNW": "10",
        "NW": "11",
        "NNW": "12",
        "N": "13",
        "NNE": "14",
        "NE": "15",
        "ENE": "16",
        "E": "17",
        "ESE": "18",
        "SE": "19",
        "SSE": "20"
    }

    # New translatable strings
    # foppeh >> These arrays are here so they get translated even if they
    #           are not used in the code.

    # first all about moon phases
    moon_phase = {
    "New": _(u"New"),
    "First Quarter": _(u"First Quarter"),
    "Full": _(u"Full"),
    "Last Quarter": _(u"Last Quarter"),
    "Waning Crescent": _(u"Waning Crescent"),
    "Waning Gibbous": _(u"Waning Gibbous"),
    "Waxing Crescent": _(u"Waxing Crescent"),
    "Waxing Gibbous": _(u"Waxing Gibbous")
    }

    # foppeh >> Something is going on with these string. I don't know if they are valid.
    #           The weird thing is they are in lower case and the XML seems to spit
    #           text with too many Uppercase. So I don't know if strings presented here
    #           will ever be a valid output from weather.com. Yet I stored them here for
    #           future reference (and because of the French translation).

    # all about weather conditions
    # 'blowing dust'                 => 'temp&#65475;&#65450;te de sable',
    # 'blowing snow'                 => 'temp&#65475;&#65450;te de neige',
    # 'blowing snow and windy'       => 'blizzard',
    # 'clear'                        => 'clair     ',
    # 'cloudy'                       => 'nuageux',
    # 'cloudy and windy'             => 'nuageux et venteux',
    # 'drizzle'                      => 'bruine',
    # 'drifting snow'                => 'accumulation de neige',
    # 'fair'                         => 'clair',
    # 'fair and windy'               => 'clair et venteux',
    # 'fog'                          => 'brouillard',
    # 'haze'                         => 'smog',
    # 'heavy drizzle'                => 'bruine intense',
    # 'heavy rain'                   => 'pluie intense',
    # 'heavy rain and windy'         => 'pluie intense et venteux',
    # 'heavy snow'                   => 'neige intense',
    # 'heavy snow and windy'         => 'neige intense et venteux',
    # 'heavy t-storm'                => 'orage &#65475;&#65449;lectrique intense',
    # 'light drizzle'                => 'faible bruine',
    # 'light drizzle and windy'      => 'bruine l&#65475;&#65449;g&#65475;&#65448;re  et venteux',
    # 'light freezing drizzle'       => 'bruine l&#65475;&#65449;g&#65475;&#65448;re verglassante',
    # 'light freezing rain'          => 'faible pluie verglassante',
    # 'light rain'                   => 'faible pluie',
    # 'light rain shower'            => 'faible averse de pluie',
    # 'light rain and fog'           => 'faible pluie et brouillard',
    # 'light rain and freezing rain' => 'pluie faible et pluie erglassante',
    # 'light rain with thunder'      => 'faible pluie avec tonnerre',
    # 'light rain and windy'         => 'faible pluie et venteux',
    # 'light snow'                   => 'faible neige',
    # 'light snow shower'            => 'faible averse de neige',
    # 'light snow and sleet'         => 'leichter Schneefall und Schneeregen',
    # 'light snow and windy'         => 'leichter Schneefall und windig',
    # 'mist'                         => 'brume',
    # 'mostly cloudy'                => 'nuageux avec &#65475;&#65449;claircies',
    # 'mostly cloudy and windy'      => 'venteux et nuageux avec &#65475;&#65449;claircies',
    # 'partial fog'                  => 'partiellement brumeux',
    # 'partly cloudy'                => 'partiellement nuageux',
    # 'partly cloudy and windy'      => 'partiellement nuageux et venteux',
    # 'patches of fog'               => 'partielles de brouillard',
    # 'rain'                         => 'pluvieux',
    # 'rain and sleet'               => 'pluie et gr&#65475;&#65449;sil',
    # 'rain and snow'                => 'pluie et neige',
    # 'rain shower'                  => 'averse de pluie',
    # 'rain and fog'                 => 'pluie et brouillard',
    # 'rain and windy'               => 'pluvieux et venteux',
    # 'sand'                         => 'sable',
    # 'shallow fog'                  => 'brouillard mince',
    # 'showers in the vicinity'      => 'averses &#65475;&#65440; proximit&#65475;&#65449;',
    # 'sleet'                        => 'gr&#65475;&#65449;sil',
    # 'smoke'                        => 'fum&#65475;&#65449;e',
    # 'snow'                         => 'neige',
    # 'snow and fog'                 => 'neige et brouillard',
    # 'snow and freezing rain'       => 'neige et pluie verglassante',
    # 'snow grains'                  => 'neige intermittante',
    # 'snow showers'                 => 'averse de neige',
    # 'snow and windy and fog'       => 'neige, brouillard et venteux',
    # 'squalls and windy'            => 'vent et gr&#65475;&#65449;sil',
    # 'sunny'                        => 'ensoleill&#65475;&#65449;',
    # 'sunny and windy'              => 'ensoleill&#65475;&#65449; et venteux',
    # 't-storm'                      => 'Orage &#65475;&#65417;lectrique',
    # 'thunder'                      => 'tonnerre',
    # 'thunder in the vicinity'      => 'tonnerre aux alentours',
    # 'unknown precip'               => 'pr&#65475;&#65449;cipitation inconnue',
    # 'widespread dust'              => 'vents de poussi&#65475;&#65448;re',
    # 'wintry mix'                   => 'conditions hivernales variables',


    # some general things...
    general = {
     "n/a": _(u"n/a"),
    'N/A': _(u"N/A"),
    'Not Available': _(u"Not Available"),
    'unknown': _(u"unknown"),
    'NONE': _(u"NONE"),
    'day': _(u"day"),
    'night': _(u"night")
    }

    # UV index ...
    UV_index = {
    "Extreme": _(u"Extreme"),
    "Very high": _(u"Very High"),
    "High": _(u"High"),
    "Moderate": (u"Moderate"),
    "Low": _(u"Low")
    }

    # tendencies used for barometric pressure
    bar_pressure = {
    "Very Low": _(u"Very Low"),
    "Moderate": _(u"Moderate"),
    "rising": _(u"rising"),
    "falling": _(u"falling"),
    "steady": _(u"steady"),
    "calm": _(u"calm")
    }


    # wind directions long
    wind_directions_long = {
    "East": _(u"East"),
    "East Northeast": _(u"East Northeast"),
    "East Southeast": _(u"East Southeast"),
    "North": _(u"North"),
    "Northeast": _(u"Northeast"),
    "North Northeast": _(u"North Northeast"),
    "North Northwest": _(u"North Northwest"),
    "Northwest": _(u"Northwest"),
    "South": _(u"South"),
    "Souteast": _(u"Southeast"),
    "South Southeast": _(u"South Southeast"),
    "South Southwest": _(u"South Southwest"),
    "Southwest": _(u"Southwest"),
    "variable": _(u"variable"),
    "West": _(u"West"),
    "West Northwest": _(u"West Northwest"),
    "West Southwest": _(u"West Southwest")
    }

    wind_directions_short = {
    "E": _(u"E"),
    "ENE": _(u"ENE"),
    "ESE": _(u"ESE"),
    "N": _(u"N"),
    "NE": _(u"NE"),
    "NNE": _(u"NNE"),
    "NNW": _(u"NNW"),
    "NW": _(u"NW"),
    "S": _(u"S"),
    "SE": _(u"SE"),
    "SSE": _(u"SSE"),
    "SSW": _(u"SSW"),
    "SW": _(u"SW"),
    "W": _(u"W"),
    "WNW": _(u"WNW"),
    "WSW": _(u"WSW")
    }

    days_of_week = {
    "Today": _(u"Today"),
    "Monday": _(u"Monday"),
    "Tuesday":_(u"Tuesday"),
    "Wednesday":_(u"Wednesday"),
    "Thursday": _(u"Thursday"),
    "Friday": _(u"Friday"),
    "Saturday": _(u"Saturday"),
    "Sunday": _(u"Sunday")
    }

# end ignoring translations
del _

class ForecastConfig:
    HEADERTEMPLATE = None
    TEMPLATE = None
    LOCATION = "INXX0057"
    EXPIRY_MINUTES = 30
    TIMEFORMAT = "%H:%M"
    DATEFORMAT = "%Y-%m-%d"
    LOCALE = None # with no setting the default locale of the system is used
    XOAP_PARTNER_ID = "1113851283" # need config with correct partner id
    XOAP_LICENCE_KEY = "241b4cd9bac9846c" # need config with correct licence key
    MAXIMUM_DAYS_FORECAST = 4 # only change if you are used an extended license
    IMAGESIZE = 48
    REFETCH = False
    CACHE_FOLDERPATH = "/tmp/"
    CONNECTION_TIMEOUT = 10

class ForecastDataset:
    def __init__(self, last_update, day_of_week, low, high, condition_code, condition_text, precip, humidity, wind_dir, wind_dir_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country, weathermap):
        self.last_update = last_update
        self.day_of_week = day_of_week
        self.low = low
        self.high = high
        self.condition_code = condition_code
        self.condition_text = condition_text
        self.precip = precip
        self.humidity = humidity
        self.wind_dir = wind_dir
        self.wind_dir_numeric = wind_dir_numeric
        self.wind_speed = wind_speed
        self.wind_gusts = wind_gusts
        self.sunrise = sunrise
        self.sunset = sunset
        self.moon_phase = moon_phase
        self.moon_icon = moon_icon
        self.bar_read = bar_read
        self.bar_desc = bar_desc
        self.uv_index = uv_index
        self.uv_text = uv_text
        self.dew_point = dew_point
        self.observatory = observatory
        self.visibility = visibility
        self.city = city
        self.country = country
        self.weathermap = weathermap

class ForecastLocation:
    timestamp = None

    def __init__(self, current, day, night, timestamp):
        self.current = current
        self.day = day
        self.night = night
        self.timestamp = timestamp #datetime.today()

    def outdated(self, mins):
        if datetime.today() > self.timestamp + timedelta(minutes=mins):
            return True
        else:
            return False

class Output:

    # design time variables
    options = None
    config = None
    forecast_data = {}
    # a list of locations for which an attempt was made to load them
    # locations in this list are not loaded again (if there was an error,
    # this makes sure it doesn't reapeat over and over)
    loaded_locations = []
    error = ""
    errorfound = False

    # design time settings
    #CONFIG_FILENAME = ".plugin_forecast.config"
    CACHE_FILENAME_TEMPLATE = ".plugin_forecast-LOCATION.cache"

    template_options = """
        --location : location code for weather data [default: %default],Use the following url to determine your location code by city name: http://xoap.weather.com/search/search?where=Norwich")
        --datatype : The data type options are: DW (Day of Week), WF (Weather Font output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), VI (Visibility), WD (Wind Direction), WA (Wind Angle - in degrees), WS (Wind Speed), WG (Wind Gusts), BF (Bearing Font), BS (Bearing font with Speed), CN (City Name), CO (Country), OB (Observatory), SR (SunRise), SS (SunSet), DL (DayLight), MP (Moon Phase), MF (Moon Font), BR (Barometer Reading), BD (Barometer Description), UI (UV Index), UT (UV Text), DP (Dew Point), LU (Last Update at weather.com), LF (Last Fetch from weather.com), WM (weather map). Not applicable at command line when using templates.")
        --startday : define the starting day number, if omitted current conditions are output. Not applicable at command line when using templates.")
        --endday : define the ending day number, if omitted only starting day data is output. Not applicable at command line when using templates.")
        --spaces : Define the number of spaces between ranged output. Not applicable at command line when using templates.")
        --template : define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=HT --startday=1]. The following are possible options within each item: --location,--datatype,--startday,--endday,--night,--shortweekday,--imperial,--beaufort,--hideunits,--hidedegreesymbol,--spaces,--minuteshide. Note that the short forms of the options are not supported! If any of these options is set from the commandline, it sets the default value of the option for all template items.")
        --locale : override the system locale for language output (en=english, es=spanish, fr=french, bg=bulgarian, cs=czech, more to come)")
        --imperial : request imperial units, if omitted output is in metric.")
        --beaufort : request beaufort scale for wind speeds, if omitted output is either metric/imperial.")
        --night : switch output to night data, if omitted day output will be output.")
        --shortweekday : Shorten the day of week data type to 3 characters.")
        --hideunits : Hide units such as mph or C, degree symbols (°) are still shown.")
        --hidedegreesymbol : Hide the degree symbol used with temperature output, this is only valid if used in conjunction with --hideunits.")
        --minuteshide : Works only with LU and LF. If present, hides the date part of the LU or LF timestamp if the day of the timestamp is today. The time part is also hidden, if the timestamp is older than minutes specified in this argument. If set to 0, the time part is always shown. If set to -1, the value EXPIRY_MINUTES from the config file is used.")
        """

    def __init__(self, options):
        self.options = options
        self.logger = logging.getLogger(app_name+"."+module_name)
        self.loadConfigData()
        self.loadTranslation()

        # setup timeout for connections
        # TODO: seems like this doesn't work in all cases..
        socket.setdefaulttimeout(self.config.CONNECTION_TIMEOUT)



    def loadTranslation(self):
        try:
            # set the locale
            if self.config.LOCALE == None:
                self.config.LOCALE = locale.getdefaultlocale()[0][0:2]

            self.logger.info("Locale set to " + self.config.LOCALE)

            # if not the default "en" locale, configure the i18n language translation
            if self.config.LOCALE != "en":

                self.logger.info("Looking for translation file for '%s' under %s" % (self.config.LOCALE, localedirectory))

                if gettext.find(domain, localedirectory, languages=[self.config.LOCALE]) != None:
                    self.logger.info("Translation file found for '%s'" % self.config.LOCALE)

                    try:
                        trans = gettext.translation(domain, localedirectory, languages=[self.config.LOCALE])
                        trans.install(unicode=True)
                        self.logger.info("Translation installed for '%s'" % self.config.LOCALE)

                    except Exception, e:
                        self.logger.error("Unable to load translation for '%s' %s" % (self.config.LOCALE, e.__str__()))
                else:
                    self.logger.info("Translation file not found for '%s', defaulting to 'en'" % self.config.LOCALE)
                    self.config.LOCALE = "en"

        except Exception, e:
            self.logger.error(e.__str__()+"\n"+traceback.format_exc())

    def loadConfigData(self):
        try:

            self.config = ForecastConfig()

            if self.options.config != None:
                # load the config based on options passed in from the main app
                configfilepath = self.options.config
            else:
                # load plugin config from home directory of the user
                configfilepath = os.path.join(os.path.expanduser('~'), ".config/"+app_name+"/"+module_name+".config")

            if os.path.exists(configfilepath):

                self.logger.info("Loading config settings from \"%s\""%configfilepath)

                for line in fileinput.input(os.path.expanduser(configfilepath)):
                    line = line.strip()
                    if len(line) > 0 and line[0:1] != "#": # ignore commented lines or empty ones

                        name = line.split("=")[0].strip().upper() # config setting name on the left of =
                        value = line.split("=")[1].split("#")[0].strip() # config value on the right of = (minus any trailing comments)

                        if len(value) > 0:
                            if name == "HEADERTEMPLATE":
                                self.config.HEADERTEMPLATE = getTypedValue(value, "string")
                            elif name == "TEMPLATE":
                                self.config.TEMPLATE = getTypedValue(value, "string")
                            elif name == "LOCATION":
                                self.config.LOCATION = getTypedValue(value, "string")
                            elif name == "CACHE_FOLDERPATH":
                                self.config.CACHE_FOLDERPATH = getTypedValue(value, "string")
                            elif name == "CONNECTION_TIMEOUT":
                                self.config.CONNECTION_TIMEOUT = getTypedValue(value, "integer")
                            elif name == "EXPIRY_MINUTES":
                                self.config.EXPIRY_MINUTES = getTypedValue(value, "integer")
                            elif name == "TIMEFORMAT":
                                self.config.TIMEFORMAT = getTypedValue(value, "string")
                            elif name == "DATEFORMAT":
                                self.config.DATEFORMAT = getTypedValue(value, "string")
                            elif name == "LOCALE":
                                self.config.LOCALE = getTypedValue(value, "string")
                            elif name == "XOAP_PARTNER_ID":
                                self.config.XOAP_PARTNER_ID = getTypedValue(value, "integer")
                            elif name == "XOAP_LICENCE_KEY":
                                self.config.XOAP_LICENCE_KEY = getTypedValue(value, "string")
                            elif name == "MAXIMUM_DAYS_FORECAST":
                                self.config.MAXIMUM_DAYS_FORECAST = getTypedValue(value, "integer")
                            elif name == "IMAGESIZE":
                                self.config.IMAGESIZE = getTypedValue(value, "integer")
                            elif name == "REFETCH":
                                self.config.REFETCH = getTypedValue(value, "boolean")
                            else:
                                self.logger.error("Unknown option in config file: " + name)
            else:
                self.logger.info("Config data file %s not found, using defaults and setting up config file for next time" % configfilepath)

                userconfigpath = os.path.join(os.path.expanduser('~'), ".config/"+app_name+"/")
                configsource = os.path.join(app_path, "config/"+module_name+".config")

                if os.path.exists(userconfigpath) == False:
                    os.makedirs(userconfigpath)

                shutil.copy(configsource, configfilepath)

        except Exception, e:
            self.logger.error(e.__str__()+"\n"+traceback.format_exc())

    def checkAndLoad(self, location):

        # define CACHE_FILEPATH based on cache folder and location code
        cachefilepath = os.path.join(self.config.CACHE_FOLDERPATH, self.CACHE_FILENAME_TEMPLATE.replace("LOCATION", location))

        # if the location was not loaded before (or attempted to load)
        if not location in self.loaded_locations:
            # add it to the list so it doesn't get loaded again (or attempted to load)
            self.loaded_locations.append(location)

            if not self.forecast_data.has_key(location):
                if os.path.exists(cachefilepath):
                    try:
                        self.logger.info("Loading cache file " + cachefilepath)
                        file = open(cachefilepath, 'rb')
                    except Exception, e:
                        self.logger.error("Unable to read the cache file %s: %s" % (cachefilepath, e.__str__()+"\n"+traceback.format_exc()))
                    else:
                        self.forecast_data[location] = pickle.load(file)
                    finally:
                        file.close()

        # check the data in the dictionary and update if outdated
        # if there was an update, store the new data in the cache file
        if self.checkAndUpdate(location) == True:
            try:
                self.logger.info("Saving updated cache file " + cachefilepath)
                file = open(cachefilepath, 'wb')
            except Exception, e:
                self.logger.error("Unable to save cache file %s: %s" % (cachefilepath, e.__str__()+"\n"+traceback.format_exc()))
            else:
                pickle.dump(self.forecast_data[location], file)
            finally:
                file.close()
        # if the location is still not in cache, print an error and return false to writeOutput()
        if self.forecast_data.has_key(location):
            return True
        else:
            self.logger.error("Location %s is not in cache." % self.config.LOCATION)
            return False

    def checkAndUpdate(self, location):
        # if the location is outdated or the refetch is forced..
        if not self.forecast_data.has_key(location) or \
           self.forecast_data[location].outdated(self.config.EXPIRY_MINUTES) or \
           self.config.REFETCH == True:

            # obtain current conditions data from xoap service
            try:
                url = "http://xoap.weather.com/weather/local/" + location + "?cc=*&dayf=10&link=xoap&prod=xoap&par=" + str(self.config.XOAP_PARTNER_ID) + "&key=" + self.config.XOAP_LICENCE_KEY + "&unit=m"
                #url = "http://xoap.weather.com/weather/local/" + location + "?cc=*&dayf=10&link=xoap&par=" + str(self.config.XOAP_PARTNER_ID) + "&key=" + self.config.XOAP_LICENCE_KEY + "&unit=m"

                print "\n\n\n\nurl:"+url+"\n\n\n\n"
                
                self.logger.info("Fetching weather data from " + url)

                usock = urllib2.urlopen(url)
                xml = usock.read()
                usock.close()

            except Exception, e:
                self.logger.error("Server connection error: " + e.__str__()+"\n"+traceback.format_exc())

            else:
                # interrogate weather data
                try:
                    # parse the XML
                    self.weatherxmldoc = minidom.parseString(xml)

                    weather_n = self.weatherxmldoc.documentElement

                    # check for an error and raise an exception
                    if len(weather_n.getElementsByTagName('err')) > 0:
                        raise Exception, self.getText(weather_n, 'err')

                    #head_n = self.getChild(weather_n, 'head')
                    #visibility_unit = self.getText(head_n, 'ud')

                    location_n = self.getChild(weather_n, 'loc')
                    city, country = self.getText(location_n, 'dnam').split(',')
                    country = country.strip()

                    # current conditions data
                    day_of_week = _(u"Today")
                    precip = _(u"N/A")
                    sunrise = self.getText(location_n, 'sunr')
                    sunset = self.getText(location_n, 'suns')

                    current_condition_n = self.getChild(weather_n, 'cc')
                    last_update = self.getText(current_condition_n, 'lsup')
                    observatory = self.getText(current_condition_n, 'obst')
                    # remove the ", country" from the string (the string is in form "location_name, country")
                    observatory = observatory[:observatory.rfind(',')]
                    current_desc = self.getText(current_condition_n, 't')
                    current_code = self.getText(current_condition_n, 'icon')
                    current_temp = self.getText(current_condition_n, 'tmp')
                    current_temp_feels = self.getText(current_condition_n, 'flik')

                    bar_n = self.getChild(current_condition_n, 'bar')
                    bar_read = self.getText(bar_n, 'r')
                    bar_desc = self.getText(bar_n, 'd')

                    wind_n = self.getChild(current_condition_n, 'wind')
                    wind_speed = self.getText(wind_n, 's')
                    wind_gusts = self.getText(wind_n, 'gust')
                    wind_direction_numeric = self.getText(wind_n, 'd')
                    wind_direction = self.getText(wind_n, 't')

                    humidity = self.getText(current_condition_n, 'hmid')
                    visibility = self.getText(current_condition_n, 'vis')
                    #if isNumeric(visibility):
                    #    visibility = visibility + visibility_unit

                    uv_n = self.getChild(current_condition_n, 'uv')
                    uv_index = self.getText(uv_n, 'i')
                    uv_text = self.getText(uv_n, 't')

                    dew_point = self.getText(current_condition_n, 'dewp')

                    moon_n = self.getChild(current_condition_n, 'moon')
                    moon_icon = self.getText(moon_n, 'icon')
                    moon_phase = self.getText(moon_n, 't')

                    weathermap = self.getImageSrcForWeatherMap(location)

                    current_forecast_data = ForecastDataset(last_update, day_of_week, current_temp_feels, current_temp, current_code, current_desc, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country, weathermap)

                    # collect forecast data
                    observatory = _(u"N/A")
                    bar_read = _(u"N/A")
                    bar_desc = _(u"N/A")
                    visibility = _(u"N/A")
                    uv_index = _(u"N/A")
                    uv_text = _(u"N/A")
                    dew_point = _(u"N/A")
                    moon_phase = _(u"N/A")
                    moon_icon = _(u"N/A")

                    forecast_n = self.getChild(weather_n, 'dayf')
                    last_update = self.getText(forecast_n, 'lsup')

                    day_nodes = forecast_n.getElementsByTagName('day')

                    day_forecast_data_list = []
                    night_forecast_data_list = []

                    for day in day_nodes:
                        day_of_week = day.getAttribute('t')

                        high_temp = self.getText(day, 'hi')
                        low_temp = self.getText(day, 'low')
                        sunrise = self.getText(day, 'sunr')
                        sunset = self.getText(day, 'suns')

                        # day forecast specific data
                        daytime_n = self.getChild(day, 'part')
                        condition_code = self.getText(daytime_n, 'icon')
                        condition = self.getText(daytime_n, 't')

                        wind_n = self.getChild(daytime_n, 'wind')
                        wind_speed = self.getText(wind_n, 's')
                        wind_gusts = self.getText(wind_n, 'gust')
                        wind_direction_numeric = self.getText(wind_n, 'd')
                        wind_direction = self.getText(wind_n, 't')

                        precip = self.getText(daytime_n, 'ppcp')
                        humidity = self.getText(daytime_n, 'hmid')

                        day_forecast_data = ForecastDataset(last_update, day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country, weathermap)
                        day_forecast_data_list.append(day_forecast_data)

                        # night forecast specific data
                        daytime_n = self.getChild(day, 'part', 1)
                        condition_code = self.getText(daytime_n, 'icon')
                        condition = self.getText(daytime_n, 't')

                        wind_n = self.getChild(daytime_n, 'wind')
                        wind_speed = self.getText(wind_n, 's')
                        wind_gusts = self.getText(wind_n, 'gust')
                        wind_direction_numeric = self.getText(wind_n, 'd')
                        wind_direction = self.getText(wind_n, 't')

                        precip = self.getText(daytime_n, 'ppcp')
                        humidity = self.getText(daytime_n, 'hmid')

                        night_forecast_data = ForecastDataset(last_update, day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_direction_numeric, wind_speed, wind_gusts, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc, uv_index, uv_text, dew_point, observatory, visibility, city, country, weathermap)
                        night_forecast_data_list.append(night_forecast_data)

                    self.forecast_data[location] = ForecastLocation(current_forecast_data, day_forecast_data_list, night_forecast_data_list, datetime.today())

                    return True

                except Exception, e:
                    self.logger.error("Error reading weather data: " + e.__str__()+"\n"+traceback.format_exc())

    def getTimestampOutput(self, timestamp, minuteshide):
        # minuteshide:
        # None = disabled
        # -1 = hide days and use config.EXPIRY_MINUTES
        # 0 = hide days and always show hours

        output = u""

        today = datetime.today()
        days = today.day - timestamp.day
        if days or minuteshide == None:
            output += timestamp.strftime(self.config.DATEFORMAT)

        if minuteshide == -1:
            minuteshide = self.config.EXPIRY_MINUTES

        delta = today - timestamp
        if days or minuteshide == None or minuteshide == 0 or delta.seconds > minuteshide * 60:
            if (len(output) > 0):
                output += " "
            output += timestamp.strftime(self.config.TIMEFORMAT)

        return output


    def getDatatypeFromSet(self, location, datatype, set, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide):
        output = u""

        try:
            if datatype == "LU":
                datetext, timezone = re.match(r"(\d{1,2}/\d{1,2}/\d{2} \d{1,2}:\d{2} [A|P]M)\s(\w*\s*\w*)",set.last_update).groups()
                if datetext != None:
                    try:
                        output = self.getTimestampOutput(datetime.strptime(datetext, "%m/%d/%y %I:%M %p"), minuteshide)
                    except:
                        self.logger.error("Failed to extract update datetime from data using standard code" + traceback.format_exc())
                        try:
                            self.logger.info("Attempting to extract update datetime from data using python 2.4 compliant code")
                            output = self.getTimestampOutput(datetime(*(time.strptime(datetext, "%m/%d/%y %I:%M %p"))[0:6]), minuteshide)
                        except:
                            self.logger.error("Failed to extract update datetime from data using python 2.4 compliant code" + traceback.format_exc())
                            output = ""

                    if timezone != None and timezone != "Local Time" and len(output) > 0:
                        output = output + " " + timezone

                if len(output) == 0:
                    self.logger.error("Unable to extract the Last update date from the dataset, using raw text without formatting")
                    output = set.last_update.strip()

            elif datatype == "LF":
                output = self.getTimestampOutput(self.forecast_data[location].timestamp, minuteshide)
            elif datatype == "DW":
                if shortweekday == True:
                    output = _(ForecastText.day_of_week_short[set.day_of_week])
                else:
                    output = _(set.day_of_week)
            elif datatype == "WF":
                #output = ForecastText.conditions_weather_font[set.condition_code]
                output = self.getImageSrcForConditionCode(set.condition_code)
            elif datatype == "LT":
                if isNumeric(set.low) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.low)
                    else:
                        string = set.low
                    string = string + tempunit
                else:
                    string = _(set.low)
                output = string
            elif datatype == "HT":
                if isNumeric(set.high) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.high)
                    else:
                        string = set.high
                    string = string + tempunit
                else:
                    string = _(set.high)
                output = string
            elif datatype == "CC":
                output = _(ForecastText.conditions_text[set.condition_code])
            elif datatype == "CT":
                #output = _(set.condition_text)
                output = _(ForecastText.conditions_text[set.condition_code])
            elif datatype == "PC":
                if isNumeric(set.precip) == True:
                    string = set.precip + u"%"
                else:
                    string = _(set.precip)
                output = string
            elif datatype == "HM":
                if isNumeric(set.humidity) == True:
                    string = set.humidity + u"%"
                else:
                    string = _(set.humidity)
                output = string
            elif datatype == "WD":
                output = _(set.wind_dir)
            elif datatype == "BF":
                if set.wind_speed == "calm":
                    output = self.getImageSrcForBearing(ForecastText.bearing_icon["calm"])
                else:
                    try:
                        #4 = strongest, 16 = offset
                        output = self.getImageSrcForBearing(int(ForecastText.bearing_icon[set.wind_dir])+(3*16))
                    except KeyError:
                        # if the value wasn't found in ForecastText.bearing_icon, use calm code
                        output = self.getImageSrcForBearing(0)
            elif datatype == "BS":
                if set.wind_speed == "calm":
                    output = self.getImageSrcForBearing(ForecastText.bearing_icon["calm"])
                elif isNumeric(set.wind_speed) == True:
                    if (set.wind_dir == "VAR"):
                        #TODO: need speed factored in once we have bearing icons with speed and direction...
                        #output = self.getImageSrcForBearing(ForecastText.bearing_icon[set.wind_dir])
                        output = self.getImageSrcForBearing(int(ForecastText.bearing_icon[set.wind_dir]) + self.getWindLevel(set.wind_speed))
                    else:
                        try:
                            #TODO: need speed factored in once we have bearing icons with speed and direction...
                            #output = self.getImageSrcForBearing(ForecastText.bearing_icon[set.wind_dir])
                            output = self.getImageSrcForBearing(int(ForecastText.bearing_icon[set.wind_dir]) + self.getWindLevel(set.wind_speed)*16)
                        except KeyError:
                            # if the value wasn't found in ForecastText.bearing_icon, use calm code
                            output = self.getImageSrcForBearing(0)
                else:
                    try:
                        output = self.getImageSrcForBearing(ForecastText.bearing_icon[set.wind_dir])
                    except KeyError:
                        # if the value wasn't found in ForecastText.bearing_icon, use calm code
                        output = self.getImageSrcForBearing(0)

            elif datatype == "WA":
                output = _(set.wind_dir_numeric)
            elif datatype == "WS":
                if isNumeric(set.wind_speed) == True:
                    if beaufort == True:
                        string = self.convertKPHtoBeaufort(set.wind_speed)
                    elif imperial == True:
                        string = self.convertKilometresToMiles(set.wind_speed)
                    else:
                        string = set.wind_speed
                    string = string + speedunit
                else:
                    string = _(set.wind_speed)
                output = string
            elif datatype == "WG":
                if isNumeric(set.wind_gusts) == True:
                    if beaufort == True:
                        string = self.convertKPHtoBeaufort(set.wind_gusts)
                    elif imperial == True:
                        string = self.convertKilometresToMiles(set.wind_gusts)
                    else:
                        string = set.wind_gusts
                    string = string + speedunit
                else:
                    string = _(set.wind_gusts) # need to define translations
                output = string
            elif datatype == "SR":

                try:
                    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
                    output = srtime.strftime(self.config.TIMEFORMAT)
                except:
                    self.logger.error("Failed to extract sunrise datetime from data using standard code" + traceback.format_exc())
                    try:
                        self.logger.info("Attempting to extract sunrise datetime from data using python 2.4 compliant code")
                        srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
                        output = srtime.strftime(self.config.TIMEFORMAT)
                    except:
                        self.logger.error("Failed to extract sunrise datetime from data using python 2.4 compliant code" + traceback.format_exc())
                        output = set.sunrise

            elif datatype == "SS":
                try:
                    sstime = datetime.strptime(set.sunset, "%I:%M %p")
                    output = sstime.strftime(self.config.TIMEFORMAT)
                except:
                    self.logger.error("Failed to extract sunset datetime from data using standard code" + traceback.format_exc())
                    try:
                        self.logger.info("Attempting to extract sunset datetime from data using python 2.4 compliant code")
                        sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
                        output = sstime.strftime(self.config.TIMEFORMAT)
                    except:
                        self.logger.error("Failed to extract sunset datetime from data using python 2.4 compliant code" + traceback.format_exc())
                        output = set.sunset

            elif datatype == "DL":

                srtime = None
                sstime = None

                try:
                    srtime = datetime.strptime(set.sunrise, "%I:%M %p")
                    sstime = datetime.strptime(set.sunset, "%I:%M %p")
                except:
                    self.logger.error("Failed to extract sunrise/sunset from data using standard code" + traceback.format_exc())
                    try:
                        self.logger.info("Attempting to extract sunrise/sunset from data using python 2.4 compliant code")
                        srtime = datetime(*(time.strptime(set.sunrise, "%I:%M %p"))[0:6])
                        sstime = datetime(*(time.strptime(set.sunset, "%I:%M %p"))[0:6])
                    except:
                        self.logger.error("Failed to extract sunrise/sunset from data using python 2.4 compliant code" + traceback.format_exc())

                if srtime != None and sstime != None:
                    delta = sstime - srtime
                    output = getHoursMinutesStringFromSeconds(delta.seconds)
                else:
                    output = "??:??"

            elif datatype == "MP":
                output = _(set.moon_phase) # need to define translations
            elif datatype == "MF":
                output = self.getImageSrcForMoonCode(ForecastText.conditions_moon_icon[set.moon_icon])
            elif datatype == "BR":
                if isNumeric(set.bar_read) == True:
                    if imperial == True:
                        string = self.convertMillibarsToInches(set.bar_read,2)
                    else:
                        string = set.bar_read
                    string = string + pressureunit
                else:
                    string = _(set.bar_read)
                output = string
            elif datatype == "BD":
                output = _(set.bar_desc) # need to define translations
            elif datatype == "UI":
                output = _(set.uv_index)
            elif datatype == "UT":
                output = _(set.uv_text)
            elif datatype == "DP":
                if isNumeric(set.dew_point) == True:
                    if imperial == True:
                        string = self.convertCelsiusToFahrenheit(set.dew_point)
                    else:
                        string = set.dew_point
                    string = string + tempunit
                else:
                    string = _(set.dew_point)
                output = string
            elif datatype == "OB":
                output = set.observatory
            elif datatype == "VI":
                if isNumeric(set.visibility) == True:
                    if imperial == True:
                        string = self.convertKilometresToMiles(set.visibility,1)
                    else:
                        string = set.visibility
                    string = string + distanceunit
                else:
                    string = _(set.visibility)
                output = string
            elif datatype == "CN":
                output = set.city
            elif datatype == "CO":
                output = set.country
            elif datatype == "WM": #weathermap
                output = set.weathermap
            else:
                self.logger.error("Unknown datatype requested: " + datatype)

        except KeyError, e:
            self.logger.error("Unknown value %s encountered for datatype '%s'! Please report this!" % (e.__str__()+"\n"+traceback.format_exc(), datatype))

        output = getHTMLText(output)
        return output

    def getDatasetOutput(self, location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide):

        output = u""

        # Check if the location is loaded, if not, load it. If it can't be loaded, there was an error
        # needs to be done here to ensure that any location used in a template is up-to-date (multiple locations are supported)
        if not self.checkAndLoad(location):
            self.logger.error("Failed to load the location cache")
            return u""

        # define current units for output
        if hideunits == False:
            if imperial == False:
                tempunit = u"°C"
                speedunit = u"kph"
                distanceunit = u"km"
                pressureunit = u"mb"
            else:
                tempunit = u"°F"
                speedunit = u"mph"
                distanceunit = u"m"
                pressureunit = u"in"

            # override speed units if beaufort selected
            if beaufort == True:
                speedunit = u""
        else:
            # remove degree symbol if not required
            if hidedegreesymbol == False:
                tempunit = u"&deg;"
            else:
                tempunit = u""

            speedunit = u""
            distanceunit = u""
            pressureunit = u""

        if startday == None:
            output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].current, shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
        else: # forecast data

            # ensure startday and enday are within the forecast limit

            if startday < 0:
                startday = 0
                self.logger.error("--startday set beyond forecast limit, reset to minimum of 0")
            elif startday > self.config.MAXIMUM_DAYS_FORECAST:
                startday = self.config.MAXIMUM_DAYS_FORECAST
                self.logger.error("--startday set beyond forecast limit, reset to maximum of " + str(self.config.MAXIMUM_DAYS_FORECAST))

            if endday == None: # if no endday was set use startday
                endday = startday
            elif endday < 0:
                endday = 0
                self.logger.error("--endday set beyond forecast limit, reset to minimum of 0")
            elif endday > self.config.MAXIMUM_DAYS_FORECAST:
                endday = self.config.MAXIMUM_DAYS_FORECAST
                self.logger.error("--endday set beyond forecast limit, reset to maximum of " + str(self.config.MAXIMUM_DAYS_FORECAST))

            for daynumber in range(startday, endday + 1):

                if night == True:
                    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].night[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
                else:
                    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)

                if daynumber != endday:
                    output += getSpaces(spaces)

        return output

    def getTemplateItemOutput(self, template_text):

        # keys to template data
        LOCATION_KEY = "location"
        DATATYPE_KEY = "datatype"
        STARTDAY_KEY = "startday"
        ENDDAY_KEY = "endday"
        NIGHT_KEY = "night"
        SHORTWEEKDAY_KEY = "shortweekday"
        IMPERIAL_KEY = "imperial"
        BEAUFORT_KEY = "beaufort"
        HIDEUNITS_KEY = "hideunits"
        HIDEDEGREESYMBOL_KEY = "hidedegreesymbol"
        SPACES_KEY = "spaces"
        MINUTESHIDE_KEY = "minuteshide"

        location = self.config.LOCATION
        datatype = None
        startday = None
        endday = None
        night = False
        shortweekday = False
        imperial = False
        beaufort = False
        hideunits = False
        hidedegreesymbol = False
        spaces = None
        minuteshide = None

        for option in template_text.split('--'):
            if len(option) == 0 or option.isspace():
                continue

            # not using split here...it can't assign both key and value in one call, this should be faster
            x = option.find('=')
            if (x != -1):
                key = option[:x].strip()
                value = option[x + 1:].strip()
                if value == "":
                    value = None
            else:
                key = option.strip()
                value = None

            try:
                if key == LOCATION_KEY:
                    location = getTypedValue(value, "string")
                elif key == DATATYPE_KEY:
                    datatype = getTypedValue(value, "string")
                elif key == STARTDAY_KEY:
                    startday = getTypedValue(value, "integer")
                elif key == ENDDAY_KEY:
                    endday = getTypedValue(value, "integer")
                elif key == NIGHT_KEY:
                    night = True
                elif key == SHORTWEEKDAY_KEY:
                    shortweekday = True
                elif key == IMPERIAL_KEY:
                    imperial = True
                elif key == BEAUFORT_KEY:
                    beaufort = True
                elif key == HIDEUNITS_KEY:
                    hideunits = True
                elif key == HIDEDEGREESYMBOL_KEY:
                    hidedegreesymbol = True
                elif key == SPACES_KEY:
                    spaces = getTypedValue(value, "integer")
                elif key == MINUTESHIDE_KEY:
                    if value != None:
                        minuteshide = getTypedValue(value, "integer")
                    else:
                        minuteshide = -1
                else:
                    self.logger.error("Unknown template option: " + option)

            except (TypeError, ValueError):
                self.logger.error("Cannot convert option argument to number: " + option)
                return u""

        if datatype != None:
            output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
            return output
        else:
            self.logger.error("Template item does not have datatype defined")
            return u""

    def getOutputFromTemplate(self, template):
        output = u""
        end = False
        a = 0

        # a and b are indexes in the template string
        # moving from left to right the string is processed
        # b is index of the opening bracket and a of the closing bracket
        # everything between b and a is a template that needs to be parsed
        while not end:
            b = template.find('[', a)

            if b == -1:
                b = len(template)
                end = True

            # if there is something between a and b, append it straight to output
            if b > a:
                output += template[a : b]
                # check for the escape char (if we are not at the end)
                if template[b - 1] == '\\' and not end:
                    # if its there, replace it by the bracket
                    output = output[:-1] + '['
                    # skip the bracket in the input string and continue from the beginning
                    a = b + 1
                    continue

            if end:
                break

            a = template.find(']', b)

            if a == -1:
                self.logger.error("Missing terminal bracket (]) for a template item")
                return u""

            # if there is some template text...
            if a > b + 1:
                output += self.getTemplateItemOutput(template[b + 1 : a])

            a = a + 1

        return output

    def getOutput(self):

        if self.options.noheader == True:
            headertemplatefilepath = app_path+"/templates/nullheader.template"
            self.logger.info("Using custom header template file '%s'"%headertemplatefilepath)
        elif self.options.headertemplate != None and os.path.exists(os.path.expanduser(self.options.headertemplate)) == True:
            headertemplatefilepath = self.options.headertemplate
            self.logger.info("Using custom header template file '%s'"%headertemplatefilepath)
        elif self.config.HEADERTEMPLATE != None and os.path.exists(os.path.expanduser(self.config.HEADERTEMPLATE)) == True:
            headertemplatefilepath = self.config.HEADERTEMPLATE
            self.logger.info("Using custom header template file '%s'"%headertemplatefilepath)
        else:
            headertemplatefilepath = app_path+"/templates/forecastheader.template"
            self.logger.info("Using default header template")

        try:
            inputfile = codecs.open(os.path.expanduser(headertemplatefilepath), encoding='utf-8')
        except Exception, e:
            self.logger.error("Error loading header template file: " + e.__str__()+"\n"+traceback.format_exc())
        else:
            headertemplate = inputfile.read()
        finally:
            inputfile.close()

        if self.options.template != None:
            templatefilepath = self.options.template
            self.logger.info("Using custom template file '%s'"%templatefilepath)
        elif self.config.TEMPLATE != None and os.path.exists(os.path.expanduser(self.config.TEMPLATE)) == True:
            templatefilepath = self.config.TEMPLATE
            self.logger.info("Using custom template file '%s'"%templatefilepath)
        else:
            templatefilepath = app_path+"/templates/forecast.template"
            self.logger.info("Using default template")

        # load the file
        try:
            inputfile = codecs.open(os.path.expanduser(templatefilepath), encoding='utf-8')
        except Exception, e:
            self.logger.error("Error loading template file: " + e.__str__()+"\n"+traceback.format_exc())
        else:
            template = inputfile.read()
        finally:
            inputfile.close()

        output = headertemplate
        output = output + self.getOutputFromTemplate(template)

        return output.encode("utf-8")

    def getText(self, parentNode, name):
        try:
            node = parentNode.getElementsByTagName(name)[0]
        except IndexError:
            raise Exception, "Data element <%s> not present under <%s>" % (name, parentNode.tagName)

        rc = ""
        for child in node.childNodes:
            if child.nodeType == child.TEXT_NODE:
                rc = rc + child.data
        return rc

    def getChild(self, parentNode, name, index = 0):
        try:
            return parentNode.getElementsByTagName(name)[index]
        except IndexError:
            raise Exception, "Data element <%s> is not present under <%s> (index %i)" % (name, parentNode.tagName, index)

    def convertCelsiusToFahrenheit(self, temp, dp=0):
        value = ((float(temp) * 9.0) / 5.0) + 32
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def convertKilometresToMiles(self, dist, dp=0):
        value = float(dist) * 0.621371192
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def convertKPHtoBeaufort(self, kph, dp=0):
        value = pow(float(kph) * 0.332270069, 2.0 / 3.0)
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def convertMillibarsToInches(self,mb,dp=0):
        value = float(mb)/33.8582
        if dp == 0:
            return str(int(round(value,dp))) # lose the dp
        else:
            return str(round(value,dp))

    def getWindLevel(self, speed):
        beaufort = int(self.convertKPHtoBeaufort(speed))
        if beaufort < 4:
            return 0
        elif beaufort < 7:
            return 1
        elif beaufort < 10:
            return 2
        else:
            return 3

    def getImageSrcForConditionCode(self, conditioncode):
        if isNumeric(conditioncode) == False:
            conditioncode = "25" # N/A image

        imagesrc = "file://%s/images/weathericons/%s.png"%(app_path, str(conditioncode).rjust(2,"0"))
        return imagesrc

    def getImageSrcForMoonCode(self, mooncode):
        imagesrc = "file://%s/images/moonicons/%s.png"%(app_path, str(mooncode).rjust(2,"0"))
        return imagesrc

    def getImageSrcForBearing(self, bearingcode):
        if int(bearingcode) > 0 and int(bearingcode) <= 4:
            fileext = "gif" # use animated gif for VAR output
        else:
            fileext = "png"
        imagesrc = "file://%s/images/bearingicons/%s.%s"%(app_path, str(bearingcode).rjust(2,"0"),fileext)
        return imagesrc

    def getImageSrcForWeatherMap(self, location):
        imagetag = ""
        try:
            url = "http://www.weather.com/outlook/travel/businesstraveler/map/" + location

            self.logger.info("Fetching satellite image page from " + url)

            usock = urllib2.urlopen(url)
            html = usock.read()
        except Exception, e:
            self.logger.error("Error downloading the satellite image page: " + e.__str__()+"\n"+traceback.format_exc())
        else:
            regex = """<IMG NAME="mapImg" SRC="([^\"]+)" WIDTH=([0-9]+) HEIGHT=([0-9]+) BORDER"""
            result = re.findall(regex, html)
            if result and len(result) == 1:
                imagesrc, width, height = result[0]
        finally:
            usock.close()

        try:

            self.logger.info("Fetching satellite image from " + imagesrc)

            usock = urllib2.urlopen(imagesrc)
            img = usock.read()
        except Exception, e:
            self.logger.error("Error downloading the satellite image file: " + e.__str__()+"\n"+traceback.format_exc())
        else:
            # save the image using a uuid firname and contruct an image tag
            imgfilepath = "/tmp/weathermap_"+str(uuid.uuid1())+".jpg"
            imgfile = open(imgfilepath,'wb')
            imgfile.write(img)

        finally:
            usock.close()
            imgfile.close()

        return imgfilepath

def getHTML(options):
    output = Output(options)
    html = output.getOutput()
    del output
    return html

# to enable testing in isolation
if __name__ == "__main__":

    parser = OptionParser()
    parser.add_option("--noheader", dest="noheader", default=False, action="store_true", help=u"Turn off header output. This will override any header template setting to be nothing")
    parser.add_option("--headertemplate", dest="headertemplate", type="string", metavar="FILE", help=u"Override the header template for the plugin, default or config based template ignored.")
    parser.add_option("--template", dest="template", type="string", metavar="FILE", help=u"Override the template for the plugin, default or config based template ignored.")
    parser.add_option("--verbose", dest="verbose", default=False, action="store_true", help=u"Outputs verbose info to the terminal")
    parser.add_option("--version", dest="version", default=False, action="store_true", help=u"Displays the version of the script.")
    parser.add_option("--logfile", dest="logfile", type="string", metavar="FILE", help=u"If a filepath is set, the script logs to the filepath.")

    (options, args) = parser.parse_args()

    output = Output(options)
    html = output.getOutput()
    del output
    print html

```

Even though I mentioned all the data even in plugin-forecast.py and my config file ..like my location code ..key and password ...but the script takes it as only **UKXX0103**
When there is no word like **UKXX0103** in the plugin_forecast.py or plugin_forecast.config file then where from this come when fetching the weather data ..I really dont understand this behaviour ....is it because of my location ..I mean LOCALE in the script
for that information I live in Hyderabad India (INXX0057) and u have my ID and password ....if at all you can get my weather in your scripts then I want to know why my script is error and at last I would like to have working copy of forecast plugin 

I live in India and I dont want some UK map or UKXX0103 weather at all ...

for your info ..the conky weather is showing exactly my location weather ...see screenshot for reference ...well conky got my location right with the same ID and password ...so why gtk-desktop-info gives me only UKXX0103  even after mentioning my location

well I have to mention one more thing ..Im having
gtk-desktop-info v 0.22 
in that also the forecast plugin is not working ..I mean more errors than the present bug ( it goes on downloads the weather data with the URL in the screenshot but it never completes ) 

so I got another script from the same thread and #439 post 

now Im working with that script ..and the screenshot is generated from that script ..may be its the latest ones so I tried but even that not working for me

---

### Post by kaivalagi on 2009-07-26
> **dumblebee100 said:**
> Even though I mentioned all the data even in plugin-forecast.py and my config file ..like my location code ..key and password ...but the script takes it as only **UKXX0103**

When I take my own config and switch it's location settings to be yours I get good output, screenshot attached.

I can't really figure out what is wrong, all looks like it should work...all I can suggest is that you start again using the example template and default config (rename the existing one and a new one will be copied across on a fialed first execution), just changing the location code at first to see whether all is okay at that point.

---

### Post by Bruce M. on 2009-07-26
> **dumblebee100 said:**
> 
Here is my config file(plugin_forecast.config) 


One quick question, the "plugin_forecast.config" you are showing us, is it located here:

~/.config/gtk-desktop-info/plugin_forecast.config

*It should be.*

May seem like a silly question, but it's better to cover all tracks.

Have a nice day.
Bruce

PS: I like your conky and conkyForecast. :popcorn:

---

### Post by diggedy on 2009-07-26
probably going to get shouted down for asking this but ive installed it, read the guide but I still have no idea how to actually get it to display on my screen?

---

### Post by kaivalagi on 2009-07-26
> **diggedy said:**
> probably going to get shouted down for asking this but ive installed it, read the guide but I still have no idea how to actually get it to display on my screen?

Take a look at the example script: /usr/share/gtk-desktop-info/example/gtk-desktop-info.sh

That should get you started, you'll probably want to save a script similar to the example, with it calling the application once for each plugin you use.

When you run an instance of the app for a particular plugin it uses that plugins config file to load default values, if there are any. All the config files are first copied to ~/.config/gtk-desktop-info/ when a  plugin is called, you can edit the files ending in .config to see changes take place for any given plugin.

It is safe to say you really need to be a tinkerer for this app, if you figured conky out then this should be do-able too.

Have a crack at it, if you're stuck ask specific questions and we can try and help out.

Read the guide 2 more times to be sure you understand what is possible. Play close attention to the help output from the app (run "gtk-desktop-info -h")

I hope that helps

---

### Post by dumblebee100 on 2009-07-27
> **Bruce M. said:**
> One quick question, the "plugin_forecast.config" you are showing us, is it located here:

~/.config/gtk-desktop-info/plugin_forecast.config

*It should be.*

May seem like a silly question, but it's better to cover all tracks.

Have a nice day.
Bruce

PS: I like your conky and conkyForecast. :popcorn:


Hye BRUCE you made my day buddy....I was trying a lot from 10 days to get my location weather ...but now I got it by your way ..Thanks buddy

[COLOR="Red"]I like your conky and conkyForecast[/COLOR]

Thanks buddy ..but anyways thats yours config ..and I just made my changes to my taste

well comming to another problem ...Im getting map of some china afghanistan ..and some other countries ....In the map of gtk-desktop-info forecast plugin there is not even a border of India ...so I cant even expect Hyderabad to be in it ..

well weather is correct but map is not ....

I switched from conky to gtk-desktop-info only for the same reason ..a graphical map of my location .....bcz many a times my parents asks me whats today weather ..can we go out or not ...is there a rain ..so map is even more friendly to tell them ...

Is there any other way to get my location weather map correctly ...

In the screenshot I get the weather correct but Hyderabad,India  is no where in the map
**one can see the enlarged map in the image viewer in the left**

In the second screenshot which I took from weather.com site for the same location INXX0057 
[url=http://in.weather.com/weather/today-Hyderabad-INXX0057?fromSearch=true]("http://in.weather.com/weather/today-Hyderabad-INXX0057?fromSearch=true")

Well I did changes to the script ie., I changed the URL in the lines of 1398 of file plugin_forecast.py
to 
```
url = "http://www.weather.com/outlook/travel/businesstraveler/map/" + location + "?bypassredirect=true&mapdest=International_Satellite:asia20"
```

well that gave me the map like this screenshot-7.png

The present weather map is more better than the earlier china afghanistan map ....

The problem is solved temporarily but still I could not get a perfect map ..Hope I should suffice with this

---

### Post by kaivalagi on 2009-07-27
> **dumblebee100 said:**
> Well I did changes to the script ie., I changed the URL in the lines of 1398 of file plugin_forecast.py
to 
```
url = "http://www.weather.com/outlook/travel/businesstraveler/map/" + location + "?bypassredirect=true&mapdest=International_Satellite:asia20"
```well that gave me the map like this screenshot-7.png

The present weather map is more better than the earlier china afghanistan map ....

The problem is solved temporarily but still I could not get a perfect map ..Hope I should suffice with this

Problem is we need a weather map URL which works for all users, you have manipulated the url for your requirements and as much as I'd love to alter the script to match, I can't because it wont work for anyone else...

If you can find any other generic URL that brings back an image for a variety of location codes around the globe, I'll be more than happy to change the script to suit...

Chimo

---

### Post by Bruce M. on 2009-07-27
> **dumblebee100 said:**
> Hye BRUCE you made my day buddy....I was trying a lot from 10 days to get my location weather ...but now I got it by your way ..Thanks buddy

[COLOR="Red"]I like your conky and conkyForecast[/COLOR]

Thanks buddy ..but anyways thats yours config ..and I just made my changes to my taste

:)  I've seen a lot of my conky floating around with various personal mod's, it's normal.  But it feels good that I can tell it's based on mine, means I did something right.  :)

> **dumblebee100 said:**
> well comming to another problem ...Im getting map of some china afghanistan ..and some other countries ....In the map of gtk-desktop-info forecast plugin there is not even a border of India ...so I cant even expect Hyderabad to be in it ..

well weather is correct but map is not ....

Yea, same with me, it put me in the capital of Venezuela, as if Buenos Aires, Argentina isn't big enough to grab, so I just cut the map out.

> **dumblebee100 said:**
> I switched from conky to gtk-desktop-info only for the same reason

I use both, I have conkyforecast & gtk-forecast. GTK sits in the same are as conkyForecast and is layed out almost the same.

BTW, in your conkyForecast change **P. de R.** to "Dew Point"

Have a nice day.
Bruce

---

### Post by dumblebee100 on 2009-07-27
Well at last I have done something right for my preferences ..I played with tables ..css files templates and all that ..and now I got some working copy of the weather forecast ..now I can show it to my parents without any problem ..

well I have one more problem 

```
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=510 --height=300 --x=-5 --y=691 --plugin=forecast --css=/usr/share/gtk-desktop-info/style/plugin_forecast_custom.css --noheader &
```

well that is my code ..I gave x=-5 and y=691

but when I execute the same thing with in terminal or else through some script during startup ..the window just places itself to x=0 and y=675 ...why doesn't it take my values 

but when I move the window using ALT it places correctly ...I just dont want to place the window everytime my ubuntu starts ..

do you people have any ideas


well I have one more problem with rhythmbox plugin( rating stars doesn't display) ...and I will ask tomorrow ...bcz today its too late ..grrrrrrrrr ..Im sleepy

---

### Post by kaivalagi on 2009-07-27
> **dumblebee100 said:**
>  I gave x=-5 and y=691 but when I execute the same thing with in terminal or else through some script during startup ..the window just places itself to x=0 and y=675 ...why doesn't it take my values 

but when I move the window using ALT it places correctly ...I just dont want to place the window everytime my ubuntu starts ..

do you people have any ideas

well I have one more problem with rhythmbox plugin( rating stars doesn't display) ...and I will ask tomorrow ...bcz today its too late ..grrrrrrrrr ..Im sleepy

The app displays a standard gtk window without decoration, if started in a position off the screen it will automatically be shifted to the edge on load. Not sure whether that is X, gnome, compiz or pygtk...? not my doing though

The app is okay to use once you get your head around the options and configuration. Could do with more documentation I guess :)

---

### Post by dumblebee100 on 2009-07-28
Well I got some time to explain my problem with rhythmbox plugin of gtk-desktop-info

The problem is I don't get rating stars for the rhythmbox plugin even though in rhythmbox there is 5 star rating for a song ....I tested out many times ..and everytime I get error like this ...

so the problem would be related to this code 

```
2009-07-28 17:46:33,622 - gtk-desktop-info.plugin_rhythmbox - ERROR - Output instance has no attribute 'isNumeric'
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_rhythmbox.py", line 355, in getOutputData
    if self.musicData.rating == None or self.isNumeric(self.musicData.rating) == False:
AttributeError: Output instance has no attribute 'isNumeric'

```

that error will repeat itself for every second ..because my update interval is 1 second 

well for more information ..I post the screenshot of the window and terminal output

well tried other plugins like exaile and banshee also ...banshee is not even close to working ..for some songs its not even updating the information ...and exaile is so far so better ..its displaying even rating stars but its kinda difficult because even a album has some cover exaile plugin doesn't show ..I mean it shows only for some ....anyways I don't want to use banshee or exaile because it takes more memory but rhythmbox just uses 22 mb ..remaining are above 50mb ..and I can't afford that much

---

### Post by Flossy on 2009-07-28
hi there

just wonderign if there is any sort of GUI available for us who would of like to install this briliant looking app but who for various reasons (in my case mild dyslexia and a severe lack of css/python/html nowlegde) will go nowher near a comand line if possible.

I think that if this is to be roled out to the masses, it needs such a option.


Flossy

---

### Post by kaivalagi on 2009-07-29
> **dumblebee100 said:**
> Well I got some time to explain my problem with rhythmbox plugin of gtk-desktop-info

The problem is I don't get rating stars for the rhythmbox plugin even though in rhythmbox there is 5 star rating for a song ....I tested out many times ..and everytime I get error like this ...

so the problem would be related to this code 

```
2009-07-28 17:46:33,622 - gtk-desktop-info.plugin_rhythmbox - ERROR - Output instance has no attribute 'isNumeric'
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/plugin_rhythmbox.py", line 355, in getOutputData
    if self.musicData.rating == None or [COLOR=Red]**self.**[/COLOR]isNumeric(self.musicData.rating) == False:
AttributeError: Output instance has no attribute 'isNumeric'

```that error will repeat itself for every second ..because my update interval is 1 second 

well for more information ..I post the screenshot of the window and terminal output

well tried other plugins like exaile and banshee also ...banshee is not even close to working ..for some songs its not even updating the information ...and exaile is so far so better ..its displaying even rating stars but its kinda difficult because even a album has some cover exaile plugin doesn't show ..I mean it shows only for some ....anyways I don't want to use banshee or exaile because it takes more memory but rhythmbox just uses 22 mb ..remaining are above 50mb ..and I can't afford that much

It's a bug, replace the /usr/share/gtk-desktop-info/plugin_rhythmbox.py file with the one attached - that _**should**_ fix the issue.

At line 355 the use of the "self." portion of self.isNumeric is erroring. This function was moved into a common module and it looks like I missed the reference which is trying to use a "local" function that isn't there anymore.

There  may be the same issue with plugin_exaile.py too....

I am really busy right now with work so don't expect any package updates any time soon...

---

### Post by kaivalagi on 2009-07-29
> **Flossy said:**
> hi there

just wonderign if there is any sort of GUI available for us who would of like to install this briliant looking app but who for various reasons (in my case mild dyslexia and a severe lack of css/python/html nowlegde) will go nowher near a comand line if possible.

I think that if this is to be roled out to the masses, it needs such a option.


Flossy

Yes, it would be nice but I have a day job :)

If someone wants to help with a GUI for it that would be great, however right now I don't see this as important as other things I am working on. If you are a conky user then the command line is a necessity, nothing is different here either.

Why not have a crack at the command line side of things, loads of people on the forums can help you with that...and your dyslexia shouldn't inhibit you really...the command line has auto-completion :)

---

### Post by wmsheep on 2009-07-31
Well, I finally figured out where things were hidden and got myself a very basic setup running (time, mail, weather).

Now to start the tweaking/experimenting!!

Great stuff

Thanks

Mark

---

### Post by kaivalagi on 2009-07-31
> **wmsheep said:**
> Well, I finally figured out where things were hidden and got myself a very basic setup running (time, mail, weather).

Now to start the tweaking/experimenting!!

Great stuff

Thanks

Mark
Look forward to see what you come up with....

---

### Post by kaivalagi on 2009-08-01
**[COLOR="Purple"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Quite a few changes and additions, see the list below or the change logs for more info.

[LIST]
[*]Updated sorting functionality of deluge plugin, still takes either "progress", "queue", "eta", "download", "upload" or "ratio".
[*]Added **sysgraph plugin**, an attempt at producing graph based info for cpu and memory loads (_work in progress..._)
[*]Fixed issues with forecast plugin after weather.com changed some url requirements
[*]Added **track lyrics support** (--datatype=TL) to the banshee, exaile and rhythmbox plugins, output text is sourced from lyricwiki.org and tidied up for output.
[*]Re-ordered right click menu, refresh then copy then quit
[*]Overridden default navigation behaviour so that **links open in the system browser rather than the webview**, to get the old behaviour use the --internalbrowsing option flag.
[*]Added **automatic link insertion** for any urls found in the following plugin areas - feedparser title, googlecalendar description, pidgin status message, tomboy text and twitter text
[*]Added a javascript **reference to jquery** in the head of all html output, any other good javascript references worth adding?
[/LIST]

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.23_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.23_source.changes)

**gtk-desktop-info-data:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.13_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info-data_0.13_source.changes)

The apt packages for intrepid, jaunty and karma are available now

Chimo

---

### Post by xeddog on 2009-08-01
I don't know if this has been addressed yet, but I found out how to get my full 7 days of weather forecast data back.  For the last month or so I could only get 4 days.  Then I read in another forum somewhere that weather.com has changed the url from xoap.weather.com.... to xml.weather.com.....

So.  I edited /usr/share/gtk-desktop-info/plugin_forecast.py and just changed the generated url to reflect that change and now I have my 7 day forecast back.  Just have to change it in ONE place and that is the generated url.  Unfortunately I cannot give a line number but . . .



xeddog

P.S.  That forum I found this on is called the rainmeter forum located [here]("http://www.rainmeter.net/forum/viewtopic.php?f=4&t=588&sid=5d36f49091d101bfbcc02f3af87ca699&start=30").

---

### Post by kaivalagi on 2009-08-01
> **xeddog said:**
> I don't know if this has been addressed yet, but I found out how to get my full 7 days of weather forecast data back.  For the last month or so I could only get 4 days.  Then I read in another forum somewhere that weather.com has changed the url from xoap.weather.com.... to xml.weather.com.....

So.  I edited /usr/share/gtk-desktop-info/plugin_forecast.py and just changed the generated url to reflect that change and now I have my 7 day forecast back.  Just have to change it in ONE place and that is the generated url.  Unfortunately I cannot give a line number but . . .



xeddog

P.S.  That forum I found this on is called the rainmeter forum located [here]("http://www.rainmeter.net/forum/viewtopic.php?f=4&t=588&sid=5d36f49091d101bfbcc02f3af87ca699&start=30").

Thanks for the heads up

I think what I'll do is move the "base" url into a config setting, with the default as is. Then if weather.com chop and change again if won't need a new release...

---

### Post by xeddog on 2009-08-01
I read further in that forum and some of the responders didn't think that the xml...  would stay around very long.   It doesn't seem like anyone really knows though, so an easy way to change the url would be good.

xeddog

---

### Post by Bruce M. on 2009-08-01
> **xeddog said:**
> I don't know if this has been addressed yet, but I found out how to get my full 7 days of weather forecast data back.  For the last month or so I could only get 4 days.  Then I read in another forum somewhere that weather.com has changed the url from xoap.weather.com.... to xml.weather.com.....


> **kaivalagi said:**
> Thanks for the heads up

I think what I'll do is move the "base" url into a config setting, with the default as is. Then if weather.com chop and change again if won't need a new release...

Don't like the name of the thread this news came from: [Weather.com cuts off 3500 locations (XOAP XML)]("http://www.rainmeter.net/forum/viewtopic.php?f=4&t=588&sid=e631959cdee7ce7447567948b7f52d2e") - that's the first post.

> cut 3500 and relegated 2500 of theses addresses to their pay only widget service

so it may not work for long.  :) or :(

WooHoo!!  Just did the same to conkyForcast.py (line 783)

```
                url = "http://xml.weather.com/weather/local/" + location + "?cc=*&dayf=8&link=xoap&prod=xoap&par=" + self.config.XOAP_PARTNER_ID + "&key=" + self.config.XOAP_LICENCE_KEY + "&unit=m"
```

And sure enough - a highly trimmed and slightly modified, with the ----- lines, cache file shows:

```
-----
VSaturday
p69
sg45
-----
VSunday
p82
sg45
V62
-----
VMonday
p97
sg45
V68
-----
VTuesday
p111
sg45
V70
-----
VWednesday
p123
sg45
V78
-----
VThursday
p137
sg45
V62
-----
VFriday
p149
sg45
```

**YES!**  *Time to play* ***- again!***
gtk-desktop and conky here I come.

Have a great day.
Bruce

---

### Post by kaivalagi on 2009-08-01
> **xeddog said:**
> I read further in that forum and some of the responders didn't think that the xml...  would stay around very long.   It doesn't seem like anyone really knows though, so an easy way to change the url would be good.

xeddog

I read that too, hence the config based setting...it will have placeholders in the text for the code to replace the location and the 2 keys, and if it isn't even there a default in code will be used (as before)

Might have something before the end of the weekend...maybe :)

p.s. I am using the xml.weather.com feed and all is fine..thx

---

### Post by Bruce M. on 2009-08-02
> **kaivalagi said:**
> p.s. I am using the xml.weather.com feed and all is fine..thx

:cry: NOT FAIR!! :cry:

I changed conkyForecast (I know, not gtk-desktop-info, but they use the same .py file) and I get:

```
Mon Tue Wed Thu Thu Thu Thu
```

Like I said before:

> cut 3500 and relegated 2500 of theses addresses to their pay only widget service
I must be in the "2500" group. {grumble grumble grumble}

**@ K**: You may find this interesting: [ALL AccuWeather feed elements]("http://www.rainmeter.net/forum/viewtopic.php?f=19&t=396#p2313")

CHIMO!
Bruce

---

### Post by kaivalagi on 2009-08-02
> **Bruce M. said:**
> :cry: NOT FAIR!! :cry:

I changed conkyForecast (I know, not gtk-desktop-info, but they use the same .py file) and I get:

```
Mon Tue Wed Thu Thu Thu Thu
```

Like I said before:


I must be in the "2500" group. {grumble grumble grumble}

**@ K**: You may find this interesting: [ALL AccuWeather feed elements]("http://www.rainmeter.net/forum/viewtopic.php?f=19&t=396#p2313")

CHIMO!
Bruce

There is a hard coded limit in the conkyForecast script of 4 days ahead, if you try and go beyond that it resets to the last "limited" forecast day...I'll be changing that too so it is in the config file for tweaking.

For now if you find this line in the conkyForecast.py file:

```
MAXIMUM_DAYS_FORECAST = 4
```

And change it to this:

```
MAXIMUM_DAYS_FORECAST = 10
```

You should be good to go :)

---

### Post by Bruce M. on 2009-08-02
> **kaivalagi said:**
> I'll be changing that too so it is in the config file for tweaking.

For now if you find this line in the conkyForecast.py file:

```
MAXIMUM_DAYS_FORECAST = 4
```

And change it to this:

```
MAXIMUM_DAYS_FORECAST = 10
```

You should be good to go :)

That line does not exist in my conkyForecast.py file.
So I searched for "maximum" and found:

# = line number
```
#1240                self.logError("--startday set beyond forecast limit, reset to maximum of " + str(self.MAX_DAY_NUMBER))
#1249                self.logError("--endday set beyond forecast limit, reset to maximum of " + str(self.MAX_DAY_NUMBER))

#625    MAX_DAY_NUMBER = 4
```

So I changed that to 10 from 4 and the results are: **SUCCESS!**

You always come to my aid K!  That's a HUGE Thanks, mate.

Of course, now I have to consider changing my layout and attacking gtk-desktop-info as well.

**[SIZE="5"]CHIMO![/SIZE]**
Bruce

---

### Post by kaivalagi on 2009-08-02
> **Bruce M. said:**
> You always come to my aid K!  That's a HUGE Thanks, mate.

No worries, just note to stop errors with templates which go beyond the actual data available the max day value ought to be adjusted to suit what is available from weather.com

> **Bruce M. said:**
> Of course, now I have to consider changing my layout and attacking gtk-desktop-info as well.

Just bear in mind the forecast restrictions are likely to return (they have previously)

---

### Post by Bruce M. on 2009-08-02
> **kaivalagi said:**
> Just bear in mind the forecast restrictions are likely to return (they have previously)

Changed 10 to 7 and I copied my old template to a 7weather.template because I do remember that previous restriction.  :)

If it comes, I simply point back to the old template.  :)

CHIMO!
Bruce

---

### Post by xeddog on 2009-08-04
Just got a question.  I was playing around with the number of days forecast I can get and it seems the answer is 9.  I built a new template called tenday.template and of course made appropriate changes.  But when I change the config file to MAXIMUM_DAYS_FORECAST = 10, I get the following:

> twoblues@Stealth:~/Desktop_mods$ ./tenday_command
twoblues@Stealth:~/Desktop_mods$ Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 524, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 137, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 181, in updateInfo
    documentplugin = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1434, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1313, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1262, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1218, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1131, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
IndexError: list index out of range

If I change the config file to MAXIMUM_DAYS_FORECAST = 9 it works with the exception, of course, that the 10th day is a copy of day 9, and I get a lot of errors about the template still having 10 days in it, but that was expected.

Anyway, just curious about what the cause may be.  Could it be that I only get the current day plus 9 more for a total of 10 days?  Or should I be able to get the current info plus 10 days forecast?  Bug in my template somewhere that I need to find?  Or heaven forbid a bug in your program?   :-)

TIA,

xeddog

---

### Post by kaivalagi on 2009-08-04
> **xeddog said:**
> Just got a question.  I was playing around with the number of days forecast I can get and it seems the answer is 9.  I built a new template called tenday.template and of course made appropriate changes.  But when I change the config file to MAXIMUM_DAYS_FORECAST = 10, I get the following:



If I change the config file to MAXIMUM_DAYS_FORECAST = 9 it works with the exception, of course, that the 10th day is a copy of day 9, and I get a lot of errors about the template still having 10 days in it, but that was expected.

Anyway, just curious about what the cause may be.  Could it be that I only get the current day plus 9 more for a total of 10 days?  Or should I be able to get the current info plus 10 days forecast?  Bug in my template somewhere that I need to find?  Or heaven forbid a bug in your program?   :-)

TIA,

xeddog

The easiest way to understand what is happening is to run the app in verbose mode and look at the url used for the forecast, then put it into your browser and have a look at the xml.

I think that start/end day = 9 is the max, if you were to look in the xml it would go no further. When the script "knows" that the max day is 9 if 10 is requested it will post an error but handle the issue by using the max day of 9, hence your duplicates.

If using verbose doesn't work (I can't be absolutely certain) the url is built up as below, you could substitute the values inside <> from your config etc run that in the browser:
```

http://xoap.weather.com/weather/local/<LOCATION>?cc=*&dayf=10&link=xoap&prod=xoap&par=<XOAP_PARTNER_ID>&key=<XOAP_LICENCE_KEY>&unit=m
```

I hope that helps explain things...it should be obvious when looking at the xml which section of data is for which forecast day etc...

---

### Post by xeddog on 2009-08-04
Thanks Kai,

I ran the url as posted (changing my location, partnerid, and license key) and only got 4 days data back.  When I changed the xoap.weather.com... to xml.weather.com... I got 9 days.  I guess that answers that question.

Thanks for your help, not to mention this app.

xeddog

---

### Post by kaivalagi on 2009-08-04
> **xeddog said:**
> Thanks Kai,

I ran the url as posted (changing my location, partnerid, and license key) and only got 4 days data back.  When I changed the xoap.weather.com... to xml.weather.com... I got 9 days.  I guess that answers that question.

Thanks for your help, not to mention this app.

xeddog

A quick heads up, this is how the url will be created in the next release (no eta yet as I have other stuff to do with the app too)

```
url = self.config.BASE_XOAP_URL.replace("<LOCATION>",location).replace("<XOAP_PARTNER_ID>",str(self.config.XOAP_PARTNER_ID)).replace("<XOAP_LICENCE_KEY>",self.config.XOAP_LICENCE_KEY)
```

As mentioned further up in the posts the base url will be config based, so you can tweak without messing with the code :)

---

### Post by carpetbelly on 2009-08-05
Hi, sorry to quote the full post below but I can't wait to get home and give this a try... I've played with conky a little and it winds the misses up no end as all she hears is me typing away and being unsociable lol...
 
anyway, I digress. I was wondering if you think this could be adjusted somewhat for TV catchup.com? Now, my html is very limited but pft why not give it a try eh, what's the worst that can happen. I just didnt fancy getting home later tonight and giving it a try and it being futile. I'm sure there probably is a way, i just wanted to see if it had been done or not. Cheers :)
 
> **kaivalagi said:**
> I thought I'd share a simple use of the --plugin=null option for all the UK BBC license payers out there. When I am drinking my coffee early in the morning and catching up on the emails/feeds/twitter/news I like to amongst other things watch bbc news.
 
I have setup a very simple html template to use on the desktop to watch bbc streams at the click of a button, fullscreen is supported too :)
 
See off.jpg for what it looks like at startup, and on.jpg when watching tv (BBC2 in this case)
 
To achieve this call the app using something like the following (ensure the template path is correct for where you put the file):
 
```
gtk-desktop-info --plugin=null --template=/home/USER/.config/gtk-desktop-info/tv/url.livetv.template --width=550 --height=500 --x=930 --y=25 --backgroundblend=30 &
```
 
The null plugin is used because no python code is needed to generate the html output, it is driven solely off html/css/javascript in the template and from web content.
 
The template looks like this:
 
```
<table border=0 cellpadding=0 cellspacing=0 width="100%">
    <tr align="center">
        <td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_news24/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbcnews.png" /></a></td>
        <td>&nbsp;</td>
        <td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_one_london/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc1.png" /></a></td>
        <td>&nbsp;</td>
        <td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_two_england/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc2.png" /></a></td>
        <td>&nbsp;</td>
        <td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_three/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc3.png" /></a></td>
        <td>&nbsp;</td>
        <td><a href="#" onclick="javascript:document.all.tv.src='http://www.bbc.co.uk/iplayer/console/bbc_four/colour/black'"><img src="file:///home/mark/.config/gtk-desktop-info/tv/bbc4.png" /></a></td>
        <td>&nbsp;</td>
        <td><a href="#" onclick="javascript:document.all.tv.src=''"><img src="file:///home/mark/.config/gtk-desktop-info/tv/off.png" /></a></td>
    </tr>
</table><br>
<iframe width="528" height="429" id="tv" src=""></iframe>
```
 
Note: The template will need adjustment to ensure the image paths are correct for where you put the files.
 
I've attached the template and accompanying png images in a tarball in case anyone wants to use them :)
 
Chimo

---

### Post by kaivalagi on 2009-08-05
> **carpetbelly said:**
> Hi, sorry to quote the full post below but I can't wait to get home and give this a try... I've played with conky a little and it winds the misses up no end as all she hears is me typing away and being unsociable lol...
 
anyway, I digress. I was wondering if you think this could be adjusted somewhat for TV catchup.com? Now, my html is very limited but pft why not give it a try eh, what's the worst that can happen. I just didnt fancy getting home later tonight and giving it a try and it being futile. I'm sure there probably is a way, i just wanted to see if it had been done or not. Cheers :)

You'll need to at the very least substitute this part for each channel:

```
.src='http://www.bbc.co.uk/iplayer/console/bbc_news24/colour/black'
```

to use the url for a stand alone player...

The url will then be loaded in the iframe at the bottom if the button is clicked

---

### Post by carpetbelly on 2009-08-06
Thanks, I'll see about giving that a try tonight... went distro hopping last night so need to get things set back up again. I might adjust it a little more just because I think tv catchup like to have the control of the channel selectors and with the logins and what not. I dont want to violate their tos as need to make sure the adverts are shown as well without jumping into the streams. 

If it's cool with you I'm gonna hack up the code and give it a shot later :D
Cant wait, tv directly in my desktop... Man, I get excited about the lamest of things lol.

---

### Post by kaivalagi on 2009-08-06
> **carpetbelly said:**
> Thanks, I'll see about giving that a try tonight... went distro hopping last night so need to get things set back up again. I might adjust it a little more just because I think tv catchup like to have the control of the channel selectors and with the logins and what not. I dont want to violate their tos as need to make sure the adverts are shown as well without jumping into the streams. 

If it's cool with you I'm gonna hack up the code and give it a shot later :D
Cant wait, tv directly in my desktop... Man, I get excited about the lamest of things lol.

Just bear in mind that gtk-desktop-info is basically a browser, albeit one without controls...for a quick and dirty solution you could just use the --url option to load the page . Just make sure the app is sized and positioned appropriately in the options you call it with..

---

### Post by arindom on 2009-08-07
Need help on the RSS display issue.

I am attaching here a screenshot of how I am getting the RSS Feeds on my desktop. As you will note, the links news feeds per source, are showing up in a continuous mode. 

That means one news is followed immediately by another news like : 
Feed 1
NEWS item 1 NEWS item
2 NEWS item 3 NEWS it
em 4

Feed 2
NEWS item 1 NEWS item
2 NEWS item 3 NEWS it
em 4

Can you please help so that I can show the feeds properly like :
Need help on the RSS display issue.

I am attaching here a screenshot of how I am getting the RSS Feeds on my desktop. As you will note, the links news feeds per source, are showing up in a continuous mode. 

That means one news is followed immediately by another news like : 
Feed 1
NEWS item 1
NEWS item 2
NEWS item 3
NEWS item 4

Feed 2
NEWS item 1
NEWS item 2
NEWS item 3
NEWS item 4

Here is how the Template that I am using looks :

<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 -->

<table class="contentbottom" border="0" cellspacing="0" cellpadding="0">
	<tr><td class="mediumlight" width="50" valign="top">Times of India</td></tr>
	<tr><td class="mediumlight" valign="top">Reuters:</td></tr>
	<tr><td class="mediumdark">[--url=http://feeds.reuters.com/reuters/topNews --limit=5 --connectiontimeout=10]</td></tr>
	<tr><td colspan="1">&nbsp;</td></tr>
	<tr><td class="mediumlight" valign="top">Fox News:</td></tr>
	<tr><td class="mediumdark">[--url=http://feeds.foxnews.com/foxnews/latest --limit=5 --connectiontimeout=10]</td></tr>
	<tr><td colspan="1">&nbsp;</td></tr>
	<tr><td class="mediumlight" valign="top">AP:</td></tr>
	<tr><td class="mediumdark">[--url=http://hosted.ap.org/lineups/TOPHEADS-rss_2.0.xml?SITE=CADIU&SECTION=HOME --limit=3 --connectiontimeout=10]</td></tr>

</table>

I will also add here that I am looking for a News ticker type scroller in Gnome. As because gtk-desktop-info has been a great tool now, will it be possible to show the RSS news as a scrolling ticker probably at the top of bottom of the screen.

Many thanks for this wonderful application.

---

### Post by kaivalagi on 2009-08-07
> **arindom said:**
> Need help on the RSS display issue.

The only issue I can see is that if the text for each feed items link is too long it wraps to the next line, this is current default behaviour. Each series of items for a feed is put into an unordered list (<ul> tag). By increaing the width the of window via the --width option on calling the app you could address the wrapping.

You can right click on the window and "copy" to clipboard the html that is output and paste it into notepad etc to view the results (it may help you realise what can be done), see below:

```
<html>
<head>
<META HTTP-EQUIV='Pragma' CONTENT='no-cache'>
<link type="text/css" rel="stylesheet" media="all" href="file:///usr/share/gtk-desktop-info/style/plugin_feedparser_default.css"/>
<script type="text/javascript" src="file:///usr/share/gtk-desktop-info/js/jquery-latest.pack.js"></script>
</head>
<body bgcolor="black" style="background-image:url('/tmp/feedparser_bg_ebca62b4-831f-11de-94a7-001a927d44a5.png');background-attachment:fixed;">
<table border="0" cellspacing="0" cellpadding="0">
	<tr>
		<td width="32"><img src="file:///usr/share/gtk-desktop-info/images/plugin_feedparser.png" border="0" width="32"/></td>
		<td valign="middle" class="largedarkitalic">&nbsp;Feeds</td>
	</tr>
</table>
<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 -->

<table class="contentbottom" border="0" cellspacing="0" cellpadding="0">
<tr><td class="mediumlight" width="50" valign="top">Times of India</td></tr>
<tr><td class="mediumlight" valign="top">Reuters:</td></tr>
<tr><td class="mediumdark"><ul><a href="http://feeds.reuters.com/~r/reuters/topNews/~3/7UNlQMTlcUw/idUSTRE57604E20090807">Autos "clunker" extension cleared, rebates top $920 million</a>
<a href="http://feeds.reuters.com/~r/reuters/topNews/~3/IpZSJzOZ3U4/idUSTRE5755FS20090806">Senate confirms Sotomoayor, first Hispanic on Supreme Court</a>
<a href="http://feeds.reuters.com/~r/reuters/topNews/~3/tfl4otimFZ8/idUSTRE57565P20090807">Pakistan says Taliban chief is likely dead</a>
<a href="http://feeds.reuters.com/~r/reuters/topNews/~3/L_i7gZ0d2fk/idUSTRE5752PD20090807">U.S. jobless claims fall sharply, buoy recovery hopes</a>
<a href="http://feeds.reuters.com/~r/reuters/topNews/~3/rvdN6z_SJ90/idUSTRE5760V120090807">Security on agenda at North America summit</a>
<ul></td></tr>
<tr><td colspan="1">&nbsp;</td></tr>
<tr><td class="mediumlight" valign="top">Fox News:</td></tr>
<tr><td class="mediumdark"><ul><a href="http://feeds.foxnews.com/~r/foxnews/latest/~3/td7bdUw4MwI/0,2933,537727,00.html">Pakistani Taliban Chief Killed, Intel Officials Say</a>
<a href="http://feeds.foxnews.com/~r/foxnews/latest/~3/7MMofiVJpH8/0,2933,537781,00.html">Fewer Layoffs Expected as Recession Loosens Grip</a>
<a href="http://feeds.foxnews.com/~r/foxnews/latest/~3/iGy6k8g7fSk/0,2933,537761,00.html">Couple Seeks New Home for Statue of Soldier</a>
<a href="http://feeds.foxnews.com/~r/foxnews/latest/~3/B3olF2iCLnk/">'Clunkers' Refill Passed by Congress</a>
<a href="http://feeds.foxnews.com/~r/foxnews/latest/~3/UKptnjv2cyQ/0,2933,537624,00.html">At Least 60 Feared Dead in Tonga Ferry Sinking</a>
<ul></td></tr>
<tr><td colspan="1">&nbsp;</td></tr>
<tr><td class="mediumlight" valign="top">AP:</td></tr>
<tr><td class="mediumdark"><ul><a href="http://hosted.ap.org/dynamic/stories/A/AS_PAKISTAN?SITE=CADIU&SECTION=HOME&TEMPLATE=DEFAULT">Intel officials: Taliban leader Mehsud dead</a>
<a href="http://hosted.ap.org/dynamic/stories/U/US_ECONOMY?SITE=CADIU&SECTION=HOME&TEMPLATE=DEFAULT">Fewer layoffs expected as recession winds down</a>
<a href="http://hosted.ap.org/dynamic/stories/U/US_SOTOMAYOR_SENATE?SITE=CADIU&SECTION=HOME&TEMPLATE=DEFAULT">Sotomayor OK'd for Supreme Court in historic vote</a>
<ul></td></tr>
</table>


</body>
</html>
```

> **arindom said:**
> I will also add here that I am looking for a News ticker type scroller in Gnome. As because gtk-desktop-info has been a great tool now, will it be possible to show the RSS news as a scrolling ticker probably at the top of bottom of the screen.

There is no scrolling option that I could create easily, maybe something could be done with javascript (jquery) but it wouldn't be easy to integrate.

Other than scrolling do you have any other suggestions on how the output could be changed to be better?

> **arindom said:**
> Many thanks for this wonderful application.

My pleasure, keep the suggestions coming and I'll try to accommodate them, some times though it is just too time consuming for me to look at...just bear in mind you now have jquery functionality available which can be incorporated into any template, this is very powerful and may enable functionality you want. Take a look at [http://docs.jquery.com/How_jQuery_Works]("http://docs.jquery.com/How_jQuery_Works") for more on that. Just bear in mind all template content goes into the body of the document.

If you have a crack at any html/css/javascript formatting of the output I can help you after you've got started on it. It's all down to how much understanding you have of the technologies I guess - and how much time is available...

Sorry I couldn't be of more help

---

### Post by arindom on 2009-08-07
> **kaivalagi said:**
> By increaing the width the of window via the --width option on calling the app you could address the wrapping.

Actually I am using the --width option and it is quite high. But here the problem is if the text is shorter than the width then the next item is also shown in the same line. For example if my width is 300 and the text is 200, then the next item is starting to come up in the same line. This makes it difficult to read the items. 

Take this example :
Here the news is being shown like :

AP :
Fellow commander says Taliban leader Mehsud dead Fewer layoffs expected as recession winds down Sotomayor's swearing in to court set for Saturday Feds to issue new swine flu advice to schools Clinton wants S. Africa to press Zimbabwe reform

I think it should have been better if it is shown like :
AP :
Fellow commander says Taliban leader Mehsud dead
Fewer layoffs expected as recession winds down
Sotomayor's swearing in to court set for Saturday 
Feds to issue new swine flu advice to schools 
Clinton wants S. Africa to press Zimbabwe reform

So had there been a line break between each feeds then there would have been no problem.

> **kaivalagi said:**
> Other than scrolling do you have any other suggestions on how the output could be changed to be better?

The best part is, from the desktop we can click on the news feeds and it directly opens the site and shows the news in detail. This is a great thing already. 

The only other idea that is coming in my mind at this stage is, if we point our mouse on any news item then some part of the detail news will pop up in a fixed width popup notification. That I think will be a good addition.

About JQuery, I am sorry that I am of no help here. May be either someone else can be of help here or we can see the scroller thing implemented later.

---

### Post by arindom on 2009-08-07
I think I found some way here. If we use the following code :

```
<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 -->

<table class="contentbottom" border="0" cellspacing="0" cellpadding="0">
	<tr><td class=".mediumdark"><MARQUEE bgcolor="#000080" 
direction="left" loop="50" width="75%">[Reuters : [--url=http://feeds.reuters.com/reuters/topNews --limit=5 --connectiontimeout=10]  Fox News : [--url=http://feeds.foxnews.com/foxnews/latest --limit=5 --connectiontimeout=10] AP : [--url=http://hosted.ap.org/lineups/TOPHEADS-rss_2.0.xml?SITE=CADIU&SECTION=HOME --limit=5 --connectiontimeout=10]</MARQUEE></td></tr>
</table>
```

then the attached screenshot is being generated. The result does not look good. But the good part is there seems to be an way to show scrolling text. 

The problems that I noted are :
a) Speed too fast.
b) Feeds are showing up in different lines instead of one line.

If we get some help here then I believe the above code can be modified to show everything in one line in a proper manner.

Sorry for my unfinished attempt and not so good result.

---

### Post by carpetbelly on 2009-08-07
> **kaivalagi said:**
> Just bear in mind that gtk-desktop-info is basically a browser, albeit one without controls...for a quick and dirty solution you could just use the --url option to load the page . Just make sure the app is sized and positioned appropriately in the options you call it with..
 
didnt get a chance to play yet but yes, I'm aware from what I've seen that it's just a browser, but you've done such a good job of implementing it and others with their own takes on your design I just have to join that geek club hehe. No harm in playing and if I manage to get something decent I'll post it up :P

---

### Post by kaivalagi on 2009-08-07
> **carpetbelly said:**
> didnt get a chance to play yet but yes, I'm aware from what I've seen that it's just a browser, but you've done such a good job of implementing it and others with their own takes on your design I just have to join that geek club hehe. No harm in playing and if I manage to get something decent I'll post it up :P

The possibilities are huge! I'm good at development but not so much on the design front so I hope that some good web designers get into using it and produce some interesting output...

---

### Post by arindom on 2009-08-08
Now the scroller looks better, the speed is also easily controllable. 

I am now using a single feed, so overall it gives the feeling of a scrolling news ticker, although the source is a single RSS feed. Please find attached the new screeenshot. 

The code is here : 
```

<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 -->
<table class="contenttop" border="0" cellspacing="0" cellpadding="0"> <marquee scrollamount=1 scrolldelay="90" direction="left" width="100%" onMouseOut=this.start() onMouseOver=this.stop() >[--url=http://timesofindia.indiatimes.com/rssfeedsdefault.cms --limit=15 --connectiontimeout=15]
</marquee>
</table>

```

Just to note here that the mouseout effect is not working properly. I will welcome any help here to improve this code because I am sure there are scope of improvements.

Thanks again to kaivalagi for such a great application. I really feel that the scope is huge.

---

### Post by kaivalagi on 2009-08-08
> **arindom said:**
> Now the scroller looks better, the speed is also easily controllable. 

I am now using a single feed, so overall it gives the feeling of a scrolling news ticker, although the source is a single RSS feed. Please find attached the new screeenshot. 

The code is here : 
```

<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 -->
<table class="contenttop" border="0" cellspacing="0" cellpadding="0"> <marquee scrollamount=1 scrolldelay="90" direction="left" width="100%" onMouseOut=this.start() onMouseOver=this.stop() >[--url=http://timesofindia.indiatimes.com/rssfeedsdefault.cms --limit=15 --connectiontimeout=15]
</marquee>
</table>

```

Just to note here that the mouseout effect is not working properly. I will welcome any help here to improve this code because I am sure there are scope of improvements.

Thanks again to kaivalagi for such a great application. I really feel that the scope is huge.

Nicely done

I think what is wrong with the code is that each item doesn't have a <li> tag (list item) which means each item can be on the same line. If I add line item tags or line breaks into the code for each item the scrolling won't work right?

The code which generate the html looks like this (I've added in red where the line item tags would go):

```
            output = output + "<ul>"
            for feeditem in feed['entries']:
                count += 1

                output = output + "[COLOR="Red"]**<li>**[/COLOR]<a href=\"%s\">%s</a>[COLOR="Red"]**</li>**[/COLOR]\n"%(feeditem.link, feeditem.title)

                if limit != None and count >= limit:
                    break

            output = output + "<ul>"

            return output
```

What do you think? I can update the code to do the above but then your marque code would be screwed I think.

See the attached screenshot for what the output is like when I add the <li> tags in...I've also attached the modified plugin_feedparser.py file if you want to update your current install before a package would go out with the change in it. You'll just need to overwrite the file here: /usr/share/gtk-desktop-info/plugin_feedparser.py

[COLOR="Blue"]Edit:[/COLOR] to enable scrolling after this change the <ul>, </ul>, <li> and </li> tags need removing from the output, maybe there is a need for an option you could add in the template per feed to either have a single feeds items displayed as in the screenshot attached (proper list) or just line a couple of spaces between each. If --nolistoutput is included inside the [] for a feed this would turn of list output?

[COLOR="Blue"]Edit (post dev):[/COLOR] I've made the code changes for a --nolistoutput option and have updated the .py file attached. I have a template based on your original one which has one feed using your marque code and the other with standard list based output.

```
<!-- FeedParser Template Options used in square brackets: --url=URL --limit=5, --connectiontimeout=10 --nolistoutput -->

<table class="contentbottom" border="0" cellspacing="0" cellpadding="0">
<tr><td class="mediumlight" width="50" valign="top">Times of India</td></tr>
<tr><td class="mediumlight" valign="top">Reuters:</td></tr>
<tr><td class="mediumdark"><marquee scrollamount=1 scrolldelay="90" direction="left" width="100%" onMouseOut=this.start() onMouseOver=this.stop() >[--url=http://feeds.reuters.com/reuters/topNews --limit=5 --connectiontimeout=10 **[COLOR="Red"]--nolistoutput[/COLOR]**]</marquee></td></tr>
<tr><td colspan="1">&nbsp;</td></tr>
<tr><td class="mediumlight" valign="top">Fox News:</td></tr>
<tr><td class="mediumdark">[--url=http://feeds.foxnews.com/foxnews/latest --limit=5 --connectiontimeout=10]</td></tr>
<tr><td colspan="1">&nbsp;</td></tr>
<tr><td class="mediumlight" valign="top">AP:</td></tr>
<tr><td class="mediumdark">[--url=http://hosted.ap.org/lineups/TOPHEADS-rss_2.0.xml?SITE=CADIU&SECTION=HOME --limit=3 --connectiontimeout=10]</td></tr>
</table>
```

Either are now supported :) Let me know what you think, if it tests out okay for you I'll commit the updates and they'll be out in the next release.

---

### Post by arindom on 2009-08-08
> **kaivalagi said:**
> Either are now supported :) Let me know what you think, if it tests out okay for you I'll commit the updates and they'll be out in the next release.

Excellent! Many thanks Kaivalagi for the changes in the python script. After I started using the new script, now the multiple feed works perfect. Per item Bullets are also showing up which makes each feed reading easy.

About the scrolling feed that one is also now working great. Mouseover effect is working correctly. 

I think you can please include this new changes in your next release.

About the scrolling feeds though, I have some questions :
a) Will it be possible to show multiple feeds in the scrolling news feed. That means presently I can only use one feed. Is there any chance that I can add more feeds there?

b) Can the items in the scrolling feed be made to show the news sources as well? That means it will show up like this :
AP : News item1 News item 2 BBC News : News Item1 News Item 2

---

### Post by kaivalagi on 2009-08-08
> **arindom said:**
> Excellent! Many thanks Kaivalagi for the changes in the python script. After I started using the new script, now the multiple feed works perfect. Per item Bullets are also showing up which makes each feed reading easy.

About the scrolling feed that one is also now working great. Mouseover effect is working correctly. 

I think you can please include this new changes in your next release.

About the scrolling feeds though, I have some questions :
a) Will it be possible to show multiple feeds in the scrolling news feed. That means presently I can only use one feed. Is there any chance that I can add more feeds there?

b) Can the items in the scrolling feed be made to show the news sources as well? That means it will show up like this :
AP : News item1 News item 2 BBC News : News Item1 News Item 2

Nice ideas but overly complicated to handle whilst also providing current functionality...

The loop which goes through each item for a feed is just that, it can't traverse multiple feeds as is..doing so would be possible but would seriously complicate the standard functionality. I think what we have now is as good as it will get...hopefully that's good enough.

Q: is there no way you can have an "aggregate feed" of multiple feeds accessible on the net as one url somehow?

---

### Post by arindom on 2009-08-08
> **kaivalagi said:**
> Nice ideas but overly complicated to handle whilst also providing current functionality...

The loop which goes through each item for a feed is just that, it can't traverse multiple feeds as is..doing so would be possible but would seriously complicate the standard functionality. I think what we have now is as good as it will get...hopefully that's good enough.

I understand. No problem. This is really good. 

> **kaivalagi said:**
> Q: is there no way you can have an "aggregate feed" of multiple feeds accessible on the net as one url somehow?

I think there must be such sources. I will try to look for such sources but the problem may be, they will probably not have the sources you may like.

But upto this I think it's really great. I am really liking the way news is being shown on the top so that I can keep an eye on it even when working on other things.

---

### Post by kaivalagi on 2009-08-08
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Quite a few changes, see the list below or the change log for more info.

[LIST]
[*]Updated config file reader code in all plugins to allow for further equals signs in the config values
[*]Moved base url setting for the forecast plugin into the config file, with default in code
[*]Fixed list item issue with feedparser plugin and added a --nolistoutput option to the feedparser plugin to output all feed items in a single line (example scrolling html in default template but commented out).
[*]Updated banshee, exaile and rhythmbox plugins to now provide a link to LyricWiki for the song lyrics as lyrics text is now unavailable. The function now uses the formal SOAP service and only makes requests when the song changes.
[*]Fixed exaile and rhythmbox plugins rating output bug
[/LIST]

**_Package changes_**

**gtk-desktop-info:** [https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.24_source.changes](https://launchpad.net/~m-buck/+archive/gtk-desktop-info/+files/gtk-desktop-info_0.24_source.changes)

The apt packages for intrepid, jaunty and karma are available now

Chimo

---

### Post by kaivalagi on 2009-08-08
> **arindom said:**
> I think there must be such sources. I will try to look for such sources but the problem may be, they will probably not have the sources you may like.

I was thinking of possible web services out there where you can setup your own feeds against an account and call one rss feed to bring all of your feeds down...similar to the way twitter works for example...

---

### Post by arindom on 2009-08-09
> **kaivalagi said:**
> I was thinking of possible web services out there where you can setup your own feeds against an account and call one rss feed to bring all of your feeds down...similar to the way twitter works for example...

Yes, there are actually quite a few sites available. Some of them don't even need to create any account, we have to just mention the URL's and get a mix URL. 

Thanks Kaivalagi for the ideas.

---

### Post by dariusdwtt on 2009-08-13
This is very exciting!!!

It's pretty much turning your entire desktop into a browser, brilliant!

Launchers should be easy, as in a proper browser if you click a "mailto:" e-mail thingy your e-mail app will launch, or if we look at the Kubuntu browser, that is half browser half file manager!

With what you are doing you should soon be able to do near anything, bringing new meaning to "active desktop"-like behaviour.

It would be amazing to give this to some web devs and graphic artists and see what they can cook up :)

Beautiful Kaivalagi, absolutely beautiful.

Could devilspie be used with this to give transparency with compiz?
or would using a large clear .png as the background bring about transparency?

Perhaps this app could be turned into a plug-in for compiz? so that your html page is rendered as the desktop instead of on top of it...

I will def be back!

---

### Post by dariusdwtt on 2009-08-13
So far Devilspie works very well with it, so a degree of transparency can be achieved, also just as a quick test it doesn't complain about the wallpaper in compiz when I don't tell it, about compiz... and I use the noresize option and a dummy wallpaper (a 1kb transparent .png) :)

---

### Post by kaivalagi on 2009-08-13
> **dariusdwtt said:**
> So far Devilspie works very well with it, so a degree of transparency can be achieved, also just as a quick test it doesn't complain about the wallpaper in compiz when I don't tell it, about compiz... and I use the noresize option and a dummy wallpaper (a 1kb transparent .png) :)

It has transparency built in, based on a crop of your wallpaper used for a background. It then has the opacity type overlay if partial transparency is needed. Transparency is default, and the overlay can be set using the below:

```
  --backgroundblend=NUMBER
                        default:[0] The optional blending ratio for the
                        backgroundcolour which is set. The default of 0 does
                        no blending, the maximum of 100 will blend "out" all
                        the wallpaper. Use this option to give some visual
                        separation to the output from the wallpaper.

```

Are you talking about when using the --url option?

It app definitely does have prospects - until google android widgets are supported in Ubuntu that is...I love my HTC Hero and google android :)

---

### Post by dariusdwtt on 2009-08-16
I don't think you quite understand what I'm saying. Here is a picture to "clarify"...

That is not default, and it's not built in... ;)

What I would really like to do is have it only on the rear work-space with the writing all backwards, so that it appears forwards, when viewed from the 1st work-space.... so that it's floating deep within the screen...

It seams I wont be able to round the corners tho :( and with the opacity the writing becomes a little harder to read, not too much of an issue but would be nice if it didn't...

---

### Post by sirjoebob on 2009-08-16
> **dariusdwtt said:**
> I don't think you quite understand what I'm saying. Here is a picture to "clarify"...

That is not default, and it's not built in... ;)

What I would really like to do is have it only on the rear work-space with the writing all backwards, so that it appears forwards, when viewed from the 1st work-space.... so that it's floating deep within the screen...

It seams I wont be able to round the corners tho :( and with the opacity the writing becomes a little harder to read, not too much of an issue but would be nice if it didn't...

That seems pretty ambitious without flipping the whole viewpoint. There may be a way to do that.

---

### Post by wmsheep on 2009-08-17
Hi all

Right then, I`ve sort of got things up to a basic level of running, but there are a couple of things I would like to do before I run things for real.

1) how do I get rid of that really horrible shtty brown background to everything (I just want a plain black or transparent b/g)

2) How do I change the font colours to ones that suit my system?

thank you

---

### Post by kaivalagi on 2009-08-17
> **wmsheep said:**
> 1) how do I get rid of that really horrible shtty brown background to everything (I just want a plain black or transparent b/g)

Right click, change desktop background and then pick something else...

If you are running gnome then the app should create transparencies using the set wallpaper automatically

> **wmsheep said:**
> 2) How do I change the font colours to ones that suit my system?

The fonts can be changed by using a custom css file, take a look at the css files in /usr/share/gtk-desktop-info/style for the defaults and go from there. To use a custom css use the --css option. More details on all the options can be found by either:

[LIST=1]
[*]run **gtk-desktop-info.guide** in the terminal
[*]run **gtk-desktop-info -h** in the terminal
[/LIST]

HTH

---

### Post by wmsheep on 2009-08-17
> **kaivalagi said:**
> Right click, change desktop background and then pick something else...

If you are running gnome then the app should create transparencies using the set wallpaper automatically

Sorry, I should have been clearer on this I dont want to change my desktop wallpaper, just the background to the wonderful application you have built.


> **kaivalagi said:**
> 
The fonts can be changed by using a custom css file, take a look at the css files in /usr/share/gtk-desktop-info/style for the defaults and go from there. To use a custom css use the --css option. More details on all the options can be found by either:

[LIST=1]
[*]run **gtk-desktop-info.guide** in the terminal
[*]run **gtk-desktop-info -h** in the terminal
[/LIST]

HTH

All very nice, but I already have that info printed out from the .pdf file (and I still dont get it!!)

Ok, what I SHOULD have asked is:-

**_Which_** is the default .css file used for each of the plug-ins?

Can I happily delete all of the others for each plug-in without problems arising, and then edit the default files to my liking?

Thanks


WMS

ps. I`m using KDE4

---

### Post by kaivalagi on 2009-08-17
> **wmsheep said:**
> Sorry, I should have been clearer on this I dont want to change my desktop wallpaper, just the background to the wonderful application you have built.




All very nice, but I already have that info printed out from the .pdf file (and I still dont get it!!)

Ok, what I SHOULD have asked is:-

**_Which_** is the default .css file used for each of the plug-ins?

Can I happily delete all of the others for each plug-in without problems arising, and then edit the default files to my liking?

Thanks


WMS

ps. I`m using KDE4

Each css file is named after the plugin it is for, with a *_default file being one for the default colours, and the others being used for --colour options.

If I were you and you wanted to customise the css then copy and edit somewhere else, then use the --css option to point at it. Otherwise any future release will potentially remove any edited files from the install folders.
 
KDE4 should handle transparencies okay, it was tested some time ago by myself but as I don't tend to use it I am uncertain if newer releases cause issues...

Does the following command in the terminal produce the wallpaper settings you have setup?

```
grep 'wallpaper=' ~/.kde/share/config/plasma-appletsrc | tail --bytes=+11
```

If not, for now, you can use the --wallpaper option to define the wallpaper you are using so the output is as slick as it can be :)

---

### Post by wmsheep on 2009-08-17
Ok, sorted out the yucky orange background (errr, that was me not realising that I also somehow have gnome installed on my machine!!! - sorry)

Edited the relevant default .css files (and copied them to a safe place) to get the colours I desire - no problems apart from the analogue clock, which still insists on being bright orange; could anyone give me a clue as to which file I should be editing to change the colours on that.

Thanks

WMS

---

### Post by kaivalagi on 2009-08-18
> **wmsheep said:**
> Ok, sorted out the yucky orange background (errr, that was me not realising that I also somehow have gnome installed on my machine!!! - sorry)

Edited the relevant default .css files (and copied them to a safe place) to get the colours I desire - no problems apart from the analogue clock, which still insists on being bright orange; could anyone give me a clue as to which file I should be editing to change the colours on that.

Thanks

WMS

For the clock you'll need to make a copy of /usr/share/gtk-desktop-info/templates/null.template and edit the skins section in the javascript for the clock, it shouldn't be too difficult, I did it for a green/black/blue clock (see attached)

---

### Post by wmsheep on 2009-08-18
OK, thanks for the info.


Edit - 
Right then, got the sort of basic set up I want now

Odds and sods still to lok at? - just a bit of eye candy behind the weather pics and figuring out how to restrict which desktop toe app should appear on out of my available 5.

Big thanks for everyone who has helped me getting things set up.

[IMG]http://i12.photobucket.com/albums/a213/Rudolphhooker/GTK-desk-01.jpg[/IMG]

---

### Post by kaivalagi on 2009-08-18
> **wmsheep said:**
> OK, thanks for the info.

I forgot to mention, you will want to use the following option for kde4 when you call the app to get the correct wallpaper settings:

```
--windowmanager=kde4
```

I suspect you have already found this out though...

---

### Post by kaivalagi on 2009-08-18
@wmsheep

Looks good!

Not sure why you are not seeing the icons  for your buddies, I guess they are not setup?

Also, you could override any specific fonts in the template files using the "style" attrib inside tags...

I know the app has it's complexities as it was originally by me for me, but it is fully customisable after some understanding of how it works :)

Maybe when I get back from my hols all rejuvenated I'll tackle a decent customising section in the guide...

---

### Post by wmsheep on 2009-08-18
> **kaivalagi said:**
> @wmsheep

Looks good!

Not sure why you are not seeing the icons  for your buddies, I guess they are not setup?

Decided against it - I know who people are. LOL

> **kaivalagi said:**
> 
Also, you could override any specific fonts in the template files using the "style" attrib inside tags...

That`ll be something for me to play about with in the near future.

> **kaivalagi said:**
> 
I know the app has it's complexities as it was originally by me for me, but it is fully customisable after some understanding of how it works :)

Maybe when I get back from my hols all rejuvenated I'll tackle a decent customising section in the guide...

I think it needs something that`s fairly noob friendly.

Thanks again and have a good holiday.

---

### Post by dumblebee100 on 2009-08-18
Hey Developer I have some problem with gtk-desktop-info plugin rhythmbox

when I play some songs in rhythmbox it plays fine and my gtk-desktop-info rhythmbox plugin shows all fine 
but when I press PLAY button again then (I mean when I PAUSE the song) 
the gtk-desktop-info plugin shows this wrong information ...

I have given status after the name in top of the template ..so when the song is playing in rhythmbox then it shows playing ..but when I pause the song then also it shows playing ..which I expect it to be something like paused ...

for more information see this screenshot which I got after pausing the song ..but it shows playing in status

---

### Post by kaivalagi on 2009-08-18
> **dumblebee100 said:**
> Hey Developer I have some problem with gtk-desktop-info plugin rhythmbox

when I play some songs in rhythmbox it plays fine and my gtk-desktop-info rhythmbox plugin shows all fine 
but when I press PLAY button again then (I mean when I PAUSE the song) 
the gtk-desktop-info plugin shows this wrong information ...

I have given status after the name in top of the template ..so when the song is playing in rhythmbox then it shows playing ..but when I pause the song then also it shows playing ..which I expect it to be something like paused ...

for more information see this screenshot which I got after pausing the song ..but it shows playing in status

Added to my TODO list, I'll take a look after my hols...mid September (long well needed holiday)

If you are just slightly python savvy you may be able to figure it out whilst I'm gone... ;)

---

### Post by dumblebee100 on 2009-08-18
> **kaivalagi said:**
> Added to my TODO list, I'll take a look after my hols...mid September (long well needed holiday)

If you are just slightly python savvy you may be able to figure it out whilst I'm gone... ;)

If I know that programming language or any other .I would readily help you but I just know only c and java basics .and that too little ...so dont expect much from me ...Im die hard ubuntu user nothing much

---

### Post by dumblebee100 on 2009-08-18
Well I need to know something about gtk-desktop-info 

the developer said that it is a light weight program ..so I expected something less than 20mb is ok kind of..

but when I look at my system monitor I was shocked to get the inner details of gtk-desktop-info 

The details from the screenshot-13.png

1st python ---> 49.5 mb     deluge
2nd python ---> 24.8 mb     rhythmbox
3rd python ---> 22.1 mb     forecast
-------------------------------------
3 plugins  ---> 96.4 mb     almost equal to my firefox without much of tabs ( I mean I open minimum of 10 tabs when I browse anything ) 

is there any other way to decrease the memory it takes in memory .because I dont want to launch another firefox without tabs just for knowing some eye candy details .....


A light weight program should be a light weight program and not this weighted ones

---

### Post by kaivalagi on 2009-08-18
It is normally a light weight program...it uses low cpu on average and doesn't in my experience use the sort of memory you are talking about. I can't deal with it now but I will when I get back from my hols...again if anyone can assist I would appreciate it...

The processes start off at around 250-260K each, which is acceptable, and have stayed that way whilst I've watched them for 15-20 minutes...there must be a slow memory leak somewhere?

If you are seeing a more rapid increase (i.e. in 10 minutes there is a change in memory usage) let me know what with (command line options / templates etc) and I will try to reproduce and diagnose.

BTW, my forum name is Kaivalagi, not "The developer". Can I be called that from now on...thanks

---

### Post by dumblebee100 on 2009-08-18
> **kaivalagi said:**
> It is normally a light weight program...it uses low cpu on average and doesn't in my experience use the sort of memory you are talking about. I can't deal with it now but I will when I get back from my hols...again if anyone can assist I would appreciate it...

The processes start off at around 250-260K each, which is acceptable, and have stayed that way whilst I've watched them for 15-20 minutes...there must be a slow memory leak somewhere?

If you are seeing a more rapid increase (i.e. in 10 minutes there is a change in memory usage) let me know what with (command line options / templates etc) and I will try to reproduce and diagnose.

BTW, my forum name is Kaivalagi, not "The developer". Can I be called that from now on...thanks


250-260 .that would be a dream come true for me 

when I start my ubuntu it starts with similar values in my other reply ..I mean  above 20 mb +

well I use this code to start my gtk-desktop-info ..I used this script from bruce
```
#!/bin/sh
pkill -f gtk_desktop_info.py
rm -f /tmp/*.jpg
rm -f /tmp/.plugin_forecast*

sleep 20

#weather forecast
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1800 --width=510 --height=300 --x=-5 --y=691 --plugin=forecast --css=/usr/share/gtk-desktop-info/style/plugin_forecast_custom.css --noheader &

#deluge
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1 --width=270 --height=455 --x=696 --y=0 --plugin=deluge --css=/usr/share/gtk-desktop-info/style/plugin_deluge_custom.css &

#rhythmbox
gtk-desktop-info --allworkspaces --logfile=/tmp/gtk-desktop-info.log --interval=1 --width=270 --height=164 --x=696 --y=456 --plugin=rhythmbox --css=/usr/share/gtk-desktop-info/style/plugin_rhythmbox_custom.css --noheader &

```

Im also attaching my 3 main folders ..config ..style ..templates in the archive ...when I installed the new version I got defauly css styles so I replaced them with the files created by me ..I mean I replaced the original folders with the custom folders which have my custom css styles and which I backuped from the older version

I think the main reason would be --interval=1 ..because the script would update for every second in my case ...would you people also use the same interval time or what ?

---

### Post by kaivalagi on 2009-08-18
> **dumblebee100 said:**
> I think the main reason would be --interval=1 ..because the script would update for every second in my case ...would you people also use the same interval time or what ?

I have a refresh every 10 seconds for Deluge, 1 second for Rhythmbox

I'll need some time to look into this...I am not back in the UK until mid-sept for a start

---

### Post by converted on 2009-08-19
This is fantastic -- after a tiny bit of headscratching I "get" how it's supposed to work, and config isn't so bad.  :)

However, I can't seem to figure out what option will change the default sort option for the "processinfo" plugin.  I would like to have one instance that sorts by Memory (default) and another that sorts by CPU time.  The comments indicate that this is possible, but I don't see any indication of how to do it.

Can you nudge me in the right direction?

Great work here, I love it!


Edit: Nevermind, for some reason I looked at the template file, not the config file.  Doh!

Edit2: So is there an easy way to run more than one instance of something?  I can see how to specify a custom template, but if I want one instance of processinfo sorted by memory and another by CPU how can I make that happen?

---

### Post by Bruce M. on 2009-08-20
> **kaivalagi said:**
> I am not back in the UK until mid-sept for a start

Ah HA! A "Globetrotter" .. must be nice.  :)

Laying around in the sun, fishing line tied to the big toe, a cool drink in hand, warm breeze.  {sigh}  Some people have all the luck.  :)

OK, meantime is this something to be concerned with:


> Setting up python-xml (0.8.4-10.1ubuntu1) ...
/usr/lib/python2.5/site-packages/oldxml/_xmlplus/xpath/ParsedAbbreviatedAbsoluteLocationPath.py:27: Warning: 'as' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/oldxml/_xmlplus/xpath/ParsedAbbreviatedAbsoluteLocationPath.py:28: Warning: 'as' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/oldxml/_xmlplus/xpath/ParsedAbbreviatedRelativeLocationPath.py:31: Warning: 'as' will become a reserved keyword in Python 2.6
/usr/lib/python2.5/site-packages/oldxml/_xmlplus/xpath/ParsedAbbreviatedRelativeLocationPath.py:32: Warning: 'as' will become a reserved keyword in Python 2.6

**? ? ?**

Have a GREAT vacation!  Sip a cool one for me!
CHIMO!
Bruce

---

### Post by dariusdwtt on 2009-08-22
This is what I have so far...

bottom right corner. It's not much but I didn't want to be too ordinary...

It's the "Important Announcement" (frame) section from my university website, so I'll never be left "unnotified". The page is downloaded with curl, saved as a template, and edited with the css style sheet. It is scrollable so I can see the rest by simply scrolling down... didn't want it to be too obtrusive :) feeling quite smart...

One gripe tho, as with one or two others, this little widget is costing me +- 25Mb

gtk-desktop-info = 68kb
devilspie = 1Mb
python = 23.5Mb

It only updates every hour...
Devilspie I need going for the border - if you look real close you'll see the cool transparent border.
and if anyone was wondering the word behind it is faith.

Any thoughts on the Memory usage???

---

### Post by wmsheep on 2009-08-23
Ok, following on from my colour co-ordinating the other day, I`ve sort of co-ordinated the icons that came with the app (errr, hope I`m allowed to do this) simply by putting them on a button type background.

It may not be much to some, but I`m more than pleased with my first attempt at doing anything serious with The GIMP!!

[IMG]http://ubuntuforums.org/picture.php?albumid=1322&pictureid=4643[/IMG]

[IMG]http://ubuntuforums.org/picture.php?albumid=1322&pictureid=4642[/IMG]


Anyway, on a slightly more serious note, for some reason the Pidgin plugin has sudenly stopped working for me - it wont even show up on my desktop.
Any suggestions??

Oh, also, is there any way to get the app to just show on one desktop, as opposed to all of them??(I would assume that if it IS possible, it would be to do with the lines that contain
[PHP]gtk-desktop-info --allworkspaces [/PHP]
but what to change the "allworkspaces" to is the question!!)

Thanks

Mark

---

### Post by dariusdwtt on 2009-08-23
Just leave out "  [COLOR=#000000][COLOR=#007700]--[/COLOR][COLOR=#0000BB]allworkspaces  [/COLOR][/COLOR]"

---

### Post by wmsheep on 2009-08-23
> **dariusdwtt said:**
> Just leave out "  [COLOR=#000000][COLOR=#007700]--[/COLOR][COLOR=#0000BB]allworkspaces  [/COLOR][/COLOR]"

Oh, as simple as that!!

Ta for that!!

---

### Post by dariusdwtt on 2009-08-23
Tell me if this has already been answered... I was a bit lazy and didn't read all the posts.

@HippyRandall

> can't figure out how to launch an app from the html. I am thinking that a new plugin is needed with some default options like [text] for text editor, [brower] for FF or web browser, etcYou're gonna kick yourself!!!

for an app launcher all you need is this

```
<a href="file:///home/HippyRandall/Desktop/file.tar.gz">file-roller</a>
<a href="file:///home/HippyRandall/Desktop/file.txt">gedit</a>
<a href="file:///home/HippyRandall/Desktop/file.jpg">imager</a>
<a href="file:///home/HippyRandall/Desktop/file.xcf">gimp</a>
```You need to specify a dummy file and your default system app will handle it.

php is an option, but that'll take some figuring out, anything browser specific will not work as this is not a browser.

It's a bit of a hack but is much better than rewriting everything...

and naturally you can add icons to your liking.
Have fun :lolflag:

P.S. there is the odd worrying terminal output, but hey every good app has lots :)

I'm gonna be having some fun with mouse over events and the like, so that the launcher pops out and moves about, etc....

top left corner of image

---

### Post by Copernicus1234 on 2009-08-29
Amazing app. This will be fun to play with and write some stuff for. :)

---

### Post by dumblebee100 on 2009-09-17
Now I changed to karmic alpha 5 but there seems to be problem with gtk-desktop-info

everytime I enter the command for gtk-desktop-info Im getting this output
```
console message:  @0: Not allowed to load local resource: file:///usr/share/gtk-desktop-info/style/plugin_shell_default.css
console message:  @0: Not allowed to load local resource: file:///usr/share/gtk-desktop-info/js/jquery-latest.pack.js

```

since this is just a null plugin Im getting only 2 errors ...but if I select some other plugin I get repeated errors of these ...

anyone has solutions?

---

### Post by kaivalagi on 2009-09-17
> **dumblebee100 said:**
> Now I changed to karmic alpha 5 but there seems to be problem with gtk-desktop-info

everytime I enter the command for gtk-desktop-info Im getting this output
```
console message:  @0: Not allowed to load local resource: file:///usr/share/gtk-desktop-info/style/plugin_shell_default.css
console message:  @0: Not allowed to load local resource: file:///usr/share/gtk-desktop-info/js/jquery-latest.pack.js

```

since this is just a null plugin Im getting only 2 errors ...but if I select some other plugin I get repeated errors of these ...

anyone has solutions?

I haven't got a clue, I am still running Jaunty and will be until Karmic has it's final non-alpha/beta release.

Could this be a bug in Karmic causing the issues?

---

### Post by dariusdwtt on 2009-10-16
Been busy with other stuff... and a bit lazy to be honest, but I've made the icons change with mouse hover... Not much but pretty cool :)

I also realized that although the app may take 25mb, what you're getting for that is a whole lot, considering that cairo dock uses quite a bit of memory too... and you are limited, while with this you can implement any of the same widgety type stuff, but in way cooler ways. As we have seen Kaivalagi do.

You can't watch the news through cairo dock lol

---

### Post by kaivalagi on 2009-10-16
> **dariusdwtt said:**
> Been busy with other stuff... and a bit lazy to be honest, but I've made the icons change with mouse hover... Not much but pretty cool :)

I also realized that although the app may take 25mb, what you're getting for that is a whole lot, considering that cairo dock uses quite a bit of memory too... and you are limited, while with this you can implement any of the same widgety type stuff, but in way cooler ways. As we have seen Kaivalagi do.

You can't watch the news through cairo dock lol

Nice, post the template/css/js files! I still want to add some user custom template into a sub-folder in the installer, having an app launcher would be really cool

---

### Post by jjrp78 on 2009-10-17
Awesome application! congrats!

One question, I hope this hasnt been asked before, I didnt read the whole thread.

I managed to put some statistics from work on the desktop thanks to gtk-desktop-info but there is one anoying detail.

When my desktop is full of windows and I want to minimize everything in one shot by pressing ctrl-D so I can check my statistics...they are also gone ! :( is there any way to prevent gtk-desktop-info from minimizing?

much appreciated for your replies

---

### Post by kaivalagi on 2009-10-17
> **jjrp78 said:**
> Awesome application! congrats!

One question, I hope this hasnt been asked before, I didnt read the whole thread.

I managed to put some statistics from work on the desktop thanks to gtk-desktop-info but there is one anoying detail.

When my desktop is full of windows and I want to minimize everything in one shot by pressing ctrl-D so I can check my statistics...they are also gone ! :( is there any way to prevent gtk-desktop-info from minimizing?

much appreciated for your replies

I'll have to look into that, it hasn't come up before.

Hopefully there is a way to bypass the minimizing function for a gtk window....maybe

If I get a chance I'll have a good look tomorrow

---

### Post by HippyRandall on 2009-10-18
isn't there a setting in compiz to override this behaviour?
[COLOR=Blue]
Edit:
I can't find a way to disable it in compiz. I thought sure there was a way.[/COLOR]

---

### Post by kaivalagi on 2009-10-19
> **HippyRandall said:**
> isn't there a setting in compiz to override this behaviour?
[COLOR=Blue]
Edit:
I can't find a way to disable it in compiz. I thought sure there was a way.[/COLOR]

Long time no see Hippy, been busy with your site?

Could be a setting in compiz, but what if the user is not running it. It might be a short term answer for the issue but I do need to look into it in code too I think.

---

### Post by bobtfish on 2009-10-19
Hi, I just found this, and I think it's great, thanks for putting in all the work. I'll certainly be playing around with this to get it how I like it.
About stopping it minimizing: I know nothing about python, but I do know Google: [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-type-hint]("http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-type-hint")
After some playing, I added this line to gtk_desktop_info.py (on line 107 beneath self.createLogger()), and it now doesn't minimize when I click the button in the bottom corner, which it was before, and it doesn't seem to have destroyed anything else:
```
	self.set_type_hint(gtk.gdk.WINDOW_TYPE_HINT_DOCK)
```
This is in a pretty standard Ubuntu 9.04 Gnome setup, with compiz effects on.

---

### Post by kaivalagi on 2009-10-19
> **bobtfish said:**
> [http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-type-hint]("http://www.pygtk.org/docs/pygtk/class-gtkwindow.html#method-gtkwindow--set-type-hint")


Thanks! That's great, I'll be sure to add the window hint in for the next release...[COLOR="Blue"]edit: added at line 150 straight after other self.set_* method calls[/COLOR]


**@ALL**
I have one outstanding nasty to take care of now, with deluge 1.2.0 (rc1) the old means to get torrent data has been removed and the new way is with reactor based callbacks (asynchronous). This doesn't quite line up well with a timer based updating app like this one (synchronous)...once I have figured this one out I'll do a release.

On the topic, does any one know anything about reactor and twisted? The same code which works with my conkyDeluge script fails with this app because the code is in a plugin module imported in rather than the main top level script...on reactor.run() the execution is blocked and nothing happens?

---

### Post by dariusdwtt on 2009-10-19
Hello there.

This is what I've been using for my launcher prototype:

**This is what I use to start the launcher:**

  ```
gtk-desktop-info --interval=600 --width=290 --height=100 --x=20 --y=30 --plugin=null --wallpaper=/opt/1.png --backgroundblend=55 --noresize --backgroundcolour=208,208,208 --backgroundcorner=1
```
1.png is a 1 pixel transparent png image. I use it to avoid confusions with compiz...

the interval could be anything.

and the rest is up to you.

**null.template**

  ```
<a href="file:///home/USERNAME/YOURFILE.tar.gz"><img src="file:///home/USERNAME/YOURFILE.png" alt="Hover" onmouseover="this.src='file:///home/USERNAME/YOURFILE.png';" onmouseout="this.src='file:///home/USERNAME/YOURFILE.png';" width="64px" height="64px" /></a>
<a href="file:///home/USERNAME/YOURFILE.txt"><img src="file:///home/USERNAME/YOURFILE.png" alt="Hover" onmouseover="this.src='file:///home/USERNAME/YOURFILE.png';" onmouseout="this.src='file:///home/USERNAME/YOURFILE.png';" width="64px" height="64px" /></a>
<a href="file:///home/USERNAME/YOURFILE.jpg"><img src="file:///home/USERNAME/YOURFILE.png" alt="Hover" onmouseover="this.src='file:///home/USERNAME/YOURFILE.png';" onmouseout="this.src='file:///home/USERNAME/YOURFILE.png';" width="64px" height="64px" /></a>
<a href="file:///home/USERNAME/YOURFILE.xcf"><img src="file:///home/USERNAME/YOURFILE.png" alt="Hover" onmouseover="this.src='file:///home/USERNAME/YOURFILE.png';" onmouseout="this.src='file:///home/USERNAME/YOURFILE.png';" width="64px" height="64px" /></a>
<div class="mediumlight" align="center">7zip&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gedit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Evince&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gimp</div>
```
_**REMEMBER TO CHANGE "*YOURFILE*" AND "*USERNAME*"**_

I was chatting to someone named choki recently and for some reason it wouldn't work on his setup... not sure why that would be...

He got the following error

```
Error occured while reset 800b: errno=5
TypeError: can't convert return value to desired type
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_get_int: assertion `G_VALUE_HOLDS_INT (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_reset: assertion `G_IS_VALUE (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_set_int: assertion `G_VALUE_HOLDS_INT (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_unset: assertion `G_IS_VALUE (value)' failed
  gtk.main()
```I sometimes get the error from line 2 till the end, but never the first line, which is probably why it didn't work for him?

---

### Post by kaivalagi on 2009-10-19
> **dariusdwtt said:**
> Hello there.

...

He got the following error

```
Error occured while reset 800b: errno=5
TypeError: can't convert return value to desired type
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_get_int: assertion `G_VALUE_HOLDS_INT (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_reset: assertion `G_IS_VALUE (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_set_int: assertion `G_VALUE_HOLDS_INT (value)' failed
  gtk.main()
/usr/share/gtk-desktop-info/gtk_desktop_info.py:480: Warning: g_value_unset: assertion `G_IS_VALUE (value)' failed
  gtk.main()
```I sometimes get the error from line 2 till the end, but never the first line, which is probably why it didn't work for him?

Hi Darius, nice alternative use of the app :)

I've never seen that error before, I think it relates to GTK when first starting the main loop for the window...unfortunately it is one of those errors without much info behind it, unless I can reproduce it I won't be able to figure it out (99% sure of that anyway)

What version of Ubuntu are you both running? Is your friend even running Ubuntu? Also, if 9.10 then I can't help until at least a week after it is fully released as I don't upgrade until 1 week after it's final, ever...

---

### Post by HippyRandall on 2009-10-19
> **dariusdwtt said:**
> Hello there.

This is what I've been using for my launcher prototype:

**null.template**

<div class="mediumlight" align="center">7zip&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gedit&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Evince&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Gimp</div>[/code]

A neater and potentially better way to do this would be with different divs for each label ie:

```
<div class="labels">7zip</div>....etc
```and then use CSS padding to align to your images, colorize your text etc

Just another 2cents worth :)
Hippy

[COLOR=Blue]here's a neat css dock example I found. not sure how it would work in this app but check it out here: [/COLOR][http://www.ndesign-studio.com/blog/mac/css-dock-menu](http://www.ndesign-studio.com/blog/mac/css-dock-menu)

---

### Post by HippyRandall on 2009-10-19
> **kaivalagi said:**
> Long time no see Hippy, been busy with your site?

Not so much. Just been a lurker I guess you could call me. I have been forced to run Ubuntu in a virt machine since my wireless has decided that it doesn't want to work 99.9% of the time and the only other way I have to connect to the internet is with a USB network adapter that causes Ubuntu to freeze up on me. Consequently I do not run Ubuntu as often as I used to, or as much as I would like.

Hippy

---

### Post by kaivalagi on 2009-10-20
> **HippyRandall said:**
> Not so much. Just been a lurker I guess you could call me. I have been forced to run Ubuntu in a virt machine since my wireless has decided that it doesn't want to work 99.9% of the time and the only other way I have to connect to the internet is with a USB network adapter that causes Ubuntu to freeze up on me. Consequently I do not run Ubuntu as often as I used to, or as much as I would like.

Hippy

Have you tried 9.10 yet, just in case that copes better with your wi-fi dongle?

---

### Post by dariusdwtt on 2009-10-20
I'm using Jaunty, and I think he is too...

That css dock is awesome! and I have it working, but with the odd niggle...

gtk-dektop-info doesn't seam to like html that calls external css, so it has to be specified in the command, and the anti-aliasing could be better. In firefox it looks great but there is a slight drop in picture quality when it's on the desktop. I'm sure that it could be specified somewhere in compiz or in the nvidia manager to force better anti-aliasing in gtk-desktop-info...

Command:

```
gtk-desktop-info --interval=600 --width=1024 --height=120 --x=0 --y=0 --plugin=null --template=path/css-dock-menu/css-dock-top.html --css=path/css-dock-menu/style.css --wallpaper=/opt/1.png --backgroundblend=70 --noresize --backgroundcolour=0,0,0 --backgroundcorner=1
```Template:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml"> 
<head> 
<meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" /> 
<title>CSS Mac Dock</title> 
<script type="text/javascript" src="/home/d/Desktop/css-dock-menu/js/jquery.js"></script> 
<script type="text/javascript" src="/home/d/Desktop/css-dock-menu/js/interface.js"></script> 
 
<link href="style.css" rel="path/css-dock-menu/stylesheet" type="text/css" /> 
</head> 
<body> 
<div class="dock" id="dock"> 
  <div class="dock-container"> 
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/home.png" alt="home" /><span>Home</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/email.png" alt="contact" /><span>Contact</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/portfolio.png" alt="portfolio" /><span>Portfolio</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/music.png" alt="music" /><span>Music</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/video.png" alt="video" /><span>Video</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/history.png" alt="history" /><span>History</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/calendar.png" alt="calendar" /><span>Calendar</span></a>  
  <a class="dock-item" href="YOURDUMMYFILE"><img src="path/rss.png" alt="rss" /><span>RSS</span></a>  
</div> 
</div> 
<script type="text/javascript"> 
     
    $(document).ready( 
        function() 
        { 
            $('#dock').Fisheye( 
                { 
                    maxWidth: 50, 
                    items: 'a', 
                    itemsText: 'span', 
                    container: '.dock-container', 
                    itemWidth: 45, 
                    proximity: 60, 
                    halign : 'center' 
                } 
            ) 
        } 
    ); 
 
</script> 
</body> 
</html> 
```The template is pretty much just what you download from that link... to the css dock site...

[http://www.zoopy.com/data/media/88711/original.jpg](http://www.zoopy.com/data/media/88711/original.jpg)

---

### Post by kaivalagi on 2009-10-20
> **dariusdwtt said:**
> I'm using Jaunty, and I think he is too...

That css dock is awesome! and I have it working, but with the odd niggle...

gtk-dektop-info doesn't seam to like html that calls external css, so it has to be specified in the command, and the anti-aliasing could be better. In firefox it looks great but there is a slight drop in picture quality when it's on the desktop. I'm sure that it could be specified somewhere in compiz or in the nvidia manager to force better anti-aliasing in gtk-desktop-info...

No settings in compiz or nvidia manager would change things, this will solely be down to webkit, the html renderer used in the app (same sort of core as safari/chrome)

The head of the document is populated by the app and can't be set in the template, otherwise you'll have strange html/head/body tag combinations. The template should be all html found inside the body tags...this means external js files etc can't be used...

Although for custom css you should be okay defining a path to an external source, this css source will get plugged in to the head of the html doc output by the app.

You have another option, although transparency wont work then, you could host the html on a local web server and refer to it using the --url option?

I'll do some more thinking on this, maybe we could have an option to set the head template of a document too (not too be confused with the headertemplate option :)), which could override any functionality in the app to build the head of the html document up...then you could take the web page you have in two parts, head and body, and refer to the 2 files which hold that html? Needs some more thought I think....

[COLOR="Blue"]**[SIZE="3"]Update[/SIZE]**

I've attached a zipped up gtk_desktop_info.py file you could replace locally after extracting as follows:

```
sudo cp /path/downloaded/to/gtk_desktop_info.py /usr/share/gtk-desktop-info/
```

Then you can use the --overridehead option it provides to point to the template holding the text inside the <head>...</head> tags, option as follows:

```

--overridehead=FILE   Override the default html head construction of the
                        app, opting for a user based template instead.
```

You'll need to strip out text from the html you have so that you can then use these options in the exec:

```
--overridehead=path/to/head/html --template=path/to/body/html
```

Note that none of these templates should include the actual <head> or <body> tags, just what's inside...

Any questions just shout...

[/COLOR]

---

### Post by xeddog on 2009-10-21
Hi all,

I have been using gtk-desktop-info with the weather plugin for  a while.  Started out with current weather and 7 day forecast.  Then I added a radar image.  But then all the bad winter/spring weather changed and I no longer needed the radar image.  SO I took my 7 day forecast, added two days and made a 9 day forecast, and it has been working fine all summer.  Now that the weather is starting to have some volatility again, I want to go back to the 7day forecast with the radar image.

That is where my problems began.  I still had the original 7 day forecast template and config files so it seemed like it should just be a simple matter of using the startup command that I had saved to produce the 7day forecast and radar image. Not so.  When I did that I would get the radar image ok, but not the weather information.  So I decided to go back to the 9 day forecast until I could figure out what was going wrong.  NOW IT DOESN'T WORK EITHER!  What the *&^$#!! The exact same command, config, and template files.

I looked in the /tmp directory and the .png files for the radar image and the background for the forecast data get created.  The log file gets created, but it is empty.  No sign of any error messages until I run the command from a terminal.  Then I get:

```
twoblues@Stealth:~$ gtk-desktop-info --logfile=/tmp/gtk-desktop-info1.log --css=/usr/share/gtk-desktop-info/style/blue.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/usr/share/gtk-desktop-info/templates/7day.template --noheader  --plugin=forecast --config=/usr/share/gtk-desktop-info/config/7day.config &
[1] 12012
twoblues@Stealth:~$ Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 524, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 137, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 181, in updateInfo
    documentplugin = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1441, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1320, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1269, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1225, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1138, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
IndexError: list index out of range

```

I have been going over this and I just can't find a problem.  Someone please tell me how easy this is to fix.

Attached are the config and template files I use.  Just one note.  The config file 7day-xx.config has been modified to hide my partner id and license key.  Normally I wouldn't care, but I really don't want to lose this.

TIA for anyone who can help.

xeddog

---

### Post by xeddog on 2009-10-21
Almost forgot one small detail.  When I boot my system the application works.  Even the 7-day forecast.  But I do not set wallpaper when I boot and select a couple later.  I have dual displays and I picked up a Perl script that will select wallpapers at random from a directory I specify, stick them together to make one large wallpaper,and then display it.  If I don't want the two selected I run it again until I get two that I like.  I have been doing this for months with no problems so I don't think that is an issue, but . . . .

After I set the wallpaper, I run the same gtk-desktop-info script that gets run at boot but now it will not display the data.  This script sets the path, does a pkill on the gtk-desktop-info process, sleeps 1 second, and then runs the startup command again.

xeddog

---

### Post by hachel on 2009-10-22
sorry if it has asked before, i couldn't find any reference in the guide.

you said it could do anything html can do, does that mean you can do hyperlinks on the desktop?

that way you could add events to a google-calendar for example

---

### Post by LaneLester on 2009-10-22
I suspect that somewhere in the 55 pages of this thread, the answer to this question exists, but a cursory scanning didn't turn it up.

I'm running Ubuntu Karmic, and I followed the procedure in the first post of this thread. All went well until the last step which ended with this message:
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable

Synaptic gives the same error when I try to install gtk-desktop-info with it.

Lane

---

### Post by kaivalagi on 2009-10-23
> **LaneLester said:**
> I suspect that somewhere in the 55 pages of this thread, the answer to this question exists, but a cursory scanning didn't turn it up.

I'm running Ubuntu Karmic, and I followed the procedure in the first post of this thread. All went well until the last step which ended with this message:
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable

Synaptic gives the same error when I try to install gtk-desktop-info with it.

Lane

I replied to your email, short of it is that you are using a beta release and I think there are not all the dependencies in place it seems. I'll upgrade a week after the final release as I always do so can figure it out properly then. Maybe by then the problem is resolved anyway...

---

### Post by kaivalagi on 2009-10-23
> **xeddog said:**
> Almost forgot one small detail.  When I boot my system the application works.  Even the 7-day forecast.  But I do not set wallpaper when I boot and select a couple later.  I have dual displays and I picked up a Perl script that will select wallpapers at random from a directory I specify, stick them together to make one large wallpaper,and then display it.  If I don't want the two selected I run it again until I get two that I like.  I have been doing this for months with no problems so I don't think that is an issue, but . . . .

After I set the wallpaper, I run the same gtk-desktop-info script that gets run at boot but now it will not display the data.  This script sets the path, does a pkill on the gtk-desktop-info process, sleeps 1 second, and then runs the startup command again.

xeddog

Can you run it in the terminal with --verbose option on and post the full trace?

It might be that you need to use the --wallpaper option as you have a custom wallpaper setup

---

### Post by xeddog on 2009-10-23
Thanks for the reply - 

I added the --wallpaper= parameter to the gtk-desktop-info command using the filename of the perl script output, and it had no affect.  It still doesn't display the weather information after changing the wallpaper.  

But here is something odd.  Once in a while it will work properly.  SOMETIMES, I can change my wallpaper, rerun the gtk-desktop-info script and it actually WILL work.  Using the exact same process (reboot, change wallpaper, run script), maybe one time in 10 or 15 reboots it will work properly.

I am beginning to think that I should just wipe this Jaunty installation and do a fresh install, BUT I DON'T WANT TO (he said in his whiniest crybaby voice).  Seems like there is always something happening that a reboot will take care of.  Maybe my bluetooth mouse won't work, or an application won't launch any more, or one time the drag-and-drop wouldn't work, or any number of other little PITA things that a reboot usually fixes.  But this one is (almost) consistant.

Anyway, you asked me to run it in a terminal with the verbose option, so here is the result:

```
twoblues@Stealth:~$ gtk-desktop-info --wallpaper=/tmp/change_wallpaper_output.jpg --logfile=/tmp/gtk-desktop-info1.log --css=/usr/share/gtk-desktop-info/style/blue.css --interval=300 --width=905 --height=350 --x=0 --y=674 --template=/usr/share/gtk-desktop-info/templates/7day.template --noheader  --plugin=forecast --config=/usr/share/gtk-desktop-info/config/7day.config --verbose &
[1] 4382
twoblues@Stealth:~$ *** INITIAL OPTIONS:
    url: None
    plugin: forecast
    css: /usr/share/gtk-desktop-info/style/blue.css
    interval: 300.0
    width: 905
    height: 350
    x: 0
    y: 674
    colour: default
    noheader: True
    headertemplate: None
    template: /usr/share/gtk-desktop-info/templates/7day.template
    config: /usr/share/gtk-desktop-info/config/7day.config
    allworkspaces: False
    wallpaper: /tmp/change_wallpaper_output.jpg
    noresize: False
    windowmanager: gnome
    backgroundblend: 0
    backgroundcolour: 0,0,0
    backgroundcorner: 10
    verbose: True
    logfile: /tmp/gtk-desktop-info1.log
2009-10-23 09:46:01,263 - gtk-desktop-info - INFO - Using background image: /tmp/forecast_bg_8bc4fd50-bff3-11de-a837-00241d759617.png
2009-10-23 09:46:01,316 - gtk-desktop-info - INFO - Loaded the "forecast" plugin, using "plugin_forecast.py"
2009-10-23 09:46:01,316 - gtk-desktop-info.plugin_forecast - INFO - Loading config settings from "/usr/share/gtk-desktop-info/config/7day.config"
2009-10-23 09:46:01,317 - gtk-desktop-info.plugin_forecast - INFO - Locale set to en
2009-10-23 09:46:01,317 - gtk-desktop-info.plugin_forecast - INFO - Using custom header template file '/usr/share/gtk-desktop-info/templates/nullheader.template'
2009-10-23 09:46:01,317 - gtk-desktop-info.plugin_forecast - INFO - Using custom template file '/usr/share/gtk-desktop-info/templates/7day.template'
2009-10-23 09:46:01,317 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-USCA1100.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 524, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 137, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 181, in updateInfo
    documentplugin = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1441, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1320, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1269, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1225, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1138, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
IndexError: list index out of range

```

Thanks again for your help.

xeddog

---

### Post by kaivalagi on 2009-10-23
> **xeddog said:**
> 
```
2009-10-23 09:46:01,317 - gtk-desktop-info.plugin_forecast - INFO - Loading cache file /tmp/.plugin_forecast-USCA1100.cache
Traceback (most recent call last):
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 524, in <module>
    info = GTKDesktopInfo(options)
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 137, in __init__
    self.updateInfo()
  File "/usr/share/gtk-desktop-info/gtk_desktop_info.py", line 181, in updateInfo
    documentplugin = self.plugin.getHTML(self.options)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1441, in getHTML
    html = output.getOutput()
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1320, in getOutput
    output = output + self.getOutputFromTemplate(template)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1269, in getOutputFromTemplate
    output += self.getTemplateItemOutput(template[b + 1 : a])
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1225, in getTemplateItemOutput
    output = self.getDatasetOutput(location, datatype, startday, endday, night, shortweekday, imperial, beaufort, hideunits, hidedegreesymbol, spaces, minuteshide)
  File "/usr/share/gtk-desktop-info/plugin_forecast.py", line 1138, in getDatasetOutput
    output += self.getDatatypeFromSet(location, datatype, self.forecast_data[location].day[daynumber], shortweekday, imperial, beaufort, tempunit, speedunit, distanceunit, pressureunit, minuteshide)
IndexError: list index out of range

```


Delete that /tmp/.plugin_forecast-USCA1100.cache file and try again...although it is in /tmp so shouldn't cause persistent problems...
Each time you change your .config i.e. change max days to use etc you should delete it, it represents what you have requested before, if you request something different it will not line up

Looks like you are asking for a day range that is too large...

*fingers crossed*...

---

### Post by markp1989 on 2009-10-23
i just tried using this with the deluge plugin , its nice, but it doesnt seem to update?

thanks Markp1989

edit: sorted that out using the interval option, how to i set the weather location?

i have your conky weather working, but i cant get this 1, get error? 


2009-10-23 23:03:15,275 - gtk-desktop-info.plugin_forecast - ERROR - Location UKXX0103 is not in cache.
2009-10-23 23:03:15,275 - gtk-desktop-info.plugin_forecast - ERROR - Failed to load the location cache

---

### Post by markp1989 on 2009-10-23
> **Bruce M. said:**
> **[CENTER][COLOR="DarkRed"][SIZE="5"]Under Construction![/SIZE][/COLOR][/CENTER]**

And for that reason no template at this time. Sorry about that folks!

[CENTER][[IMG]http://img264.imageshack.us/img264/3771/underconstructionrw6.th.png[/IMG]](http://img264.imageshack.us/my.php?image=underconstructionrw6.png)[/CENTER]

):P useResa & Paul!

Have a nice day!
Bruce

thats cool, i wouldl like to see your template files if you still have them

---

### Post by kaivalagi on 2009-10-23
> **markp1989 said:**
> i just tried using this with the deluge plugin , its nice, but it doesnt seem to update?

thanks Markp1989

edit: sorted that out using the interval option, how to i set the weather location?

i have your conky weather working, but i cant get this 1, get error? 


2009-10-23 23:03:15,275 - gtk-desktop-info.plugin_forecast - ERROR - Location UKXX0103 is not in cache.
2009-10-23 23:03:15,275 - gtk-desktop-info.plugin_forecast - ERROR - Failed to load the location cache

deluge 1.2.0rc changed how everything works, I haven't been able to get a working solution for the change yet...

---

### Post by xeddog on 2009-10-24
Kaivalagi - 

I think you are on to something with the /tmp/.plugin_forecast-USCA1100.cache file.  I deleted it and then ran my script to run gtk-desktop-info and it worked.  I changed wallpaper and reran gtk-desktop-info three times, but the fourth time (and later) it quit working again.  Deleted the tmp file and it worked again. 

So at least I know how to get it running again.  I will change my startup script to delete that file first and then start gtk-desktop-info so that should take care of everyting.  But I am still curious about two things.  Why does it work "sometimes", and why is that cache file causing it to happen.

Thanks.

xeddog

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by HippyRandall on 2009-11-06
sadly, I am trying out Karmic in a VM and I am getting issues with installing this app.

```
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable

```
did they leave this out of karmic? been a while since I have been on nix so bare with me.

---

### Post by kaivalagi on 2009-11-06
> **HippyRandall said:**
> sadly, I am trying out Karmic in a VM and I am getting issues with installing this app.

```
The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable

```
did they leave this out of karmic? been a while since I have been on nix so bare with me.

Hi Hippy, good to see you...no nix - my gawd!

Yep, I was upgrading to 9.10 to see how to fix it properly when it screwed up, now I am on Arch :) I have no idea of the dependancy issue fix now because of having no Ubu any more.

All my scripts are, for the most part, on hold. I have Arch to setup and a busy job, both should keep me fairly well occupied until the end of the year

Try manually copying the tarball contents instead, bypassing the dependancies, just to see if it works? Maybe the dependant packages have been consolidated???

---

### Post by HippyRandall on 2009-11-06
meh. oh well. how is arch working out for you? throw me a link if you have one for newbie installers and I'll give it a go on my VM

---

### Post by kaivalagi on 2009-11-06
> **HippyRandall said:**
> meh. oh well. how is arch working out for you? throw me a link if you have one for newbie installers and I'll give it a go on my VM

I am liking Arch a lot, I know where all the settings are for everything (or atleast know where to start looking). I had OpenBox running, now I have shifted to gnome and compiz for a while (old habits). Very snappy and the AUR is awesome...and no more 6 monthly updates from hell, all bit by bit from now on...

Once I have arch as I want it (for the first time anyway) I'll began looking at package creation on Arch and getting it working 100% for me. After that back to addressing a couple of issues I have with it - the 1.2.0 deluge api change is causing issues...if christmas gets a bit boring then I can probably get quite a bit done :)

---

### Post by xeddog on 2009-11-22
Kaivalagi - 

I just did a 64-bit Karmic install on a second disk drive and gtk-desktop-info was one of the first apps I have been trying to install.  I see in a previous post that the someone else is getting the same error a I am.  That being:

> gtk-desktop-info: Depends: python-webkitgtk but it is not installable

I looked in the synaptic listing and the only thing similar is python-webkit but not python-webkitgtk.  But!!  The description for python-webkit says: 
> PyWebKitGtk provides an API for developers to program WebKit/Gtk using Python.

So could it be as "simple" as changing the name?  If so, how would I go about changing the dependency to try it out, or is that something that can even be done?

Thanks,

xeddog

---

### Post by kaivalagi on 2009-11-23
> **xeddog said:**
> Kaivalagi - 

I just did a 64-bit Karmic install on a second disk drive and gtk-desktop-info was one of the first apps I have been trying to install.  I see in a previous post that the someone else is getting the same error a I am.  That being:



I looked in the synaptic listing and the only thing similar is python-webkit but not python-webkitgtk.  But!!  The description for python-webkit says: 


So could it be as "simple" as changing the name?  If so, how would I go about changing the dependency to try it out, or is that something that can even be done?

Thanks,

xeddog

It might be a little tricky, the dependancy settings are found in <package>/control.tar.gz/./control

You should be able to extract the contents and manipulate the control file and package it back up, but the initial "." folder has always stumped me...maybe it's just me and you'll figure it out fine.

The other option you have it grabbing the source and building the package, I've attached the build script I use for my builds (used to anyway) which you can use with the source once you have edited the control file and it to represent your directory structures...you can get the source tarball from launchpad (see the first post). The script does more than you probably want, just look at the binary build bit - should be obvious

Let me know if I can be of help...I wish I could make the update and "dput" the source package for building on launchpad but for some reason dput will not build and install for me on Arch and I am not willing to revert back to Ubuntu, I have travelled too far if you know what I mean :)

It might be worth installing by building the install package anyway as this may turn out to be the only option going forwards...I still have the job of writing a howto for that but it will essentially be using the script I have attached

The other option is you switch to Arch - I've just added the following packages in the AUR for gtk-desktop-info:

[LIST]
[*]gtk-desktop-info-bzr
[*]gtk-desktop-info-data-bzr
[/LIST]

They build directly from the source branch on install ;) 

I'll be doing the same for other apps in time, where people have not done so already - my apps have got everywhere! Oh how I am starting to love Arch...

Hope that helps

---

### Post by Bruce M. on 2009-11-23
> **markp1989 said:**
> thats cool, i wouldl like to see your template files if you still have them

Sorry I didn't see this, do I still have that.  Hmmmmmmmm

Yup, good think I'm a packrat I'm not even using Ubuntu anymore let alone gtk-desktop-info.

Here is is:

weather.template
```
<html>
<head></head>
<body>

<!-- --datatype : The data type options are:
	 DW (Day of Week),
	 WF (Weather Font output),
Today:	 LT - Feels Like Temp  - WITHOUT: "--startday=0" [--datatype LT]
Today:	 HT - Current Temp - WITHOUT: "--startday=0" [--datatype HT]
Today:	 LT - Forcasted Low Temp: - WITH: "--startday=0" [-- startday=0 --datatype LT]
Today:	 HT - Forecasted High Temp: - WITH: "--startday=0" [-- startday=0 --datatype HT]
Fore:	 LT - Low Temp - use with --startday=1 to 4 [-- startday=1 --datatype LT]
Fore:	 HT - High Temp - use with --startday=1 to 4 [-- startday=1 --datatype HT]
	 CC (Current Conditions),
	 CC (Conditions Text),
	 PC (Precipitation Chance),
	 HM (Humidity),
	 VI (Visibility),
	 WD (Wind Direction),
	 WA (Wind Angle - in degrees),
	 WS (Wind Speed),
	 WG (Wind Gusts),
	 BF (Bearing Font),
	 BS (Bearing font with Speed),
	 CN (City Name),
	 CO (Country),
	 OB (Observatory),
	 SR (SunRise),
	 SS (SunSet),
	 DL (Hours of DayLight),
	 MP (Moon Phase),
	 MF (Moon Font),
	 BR (Barometer Reading),
	 BD (Barometer Description),
	 UI (UV Index),
	 UT (UV Text),
	 DP (Dew Point),
	 LU (Last Update at weather.com),
	 LF (Last Fetch from weather.com),
	 WM (weather map) -->

<table cellpadding="0" cellspacing="5" border="0">
<tr>
	<td rowspan="3" align="center" valign="top"><img src="[--datatype=WF]" width="100"/></td>
	<td rowspan="3" align="center" class="hoy-cyan">[--datatype=HT --hideunits]</td>
	<td rowspan="3" align="right" valign="center">
<!-- High, Low, ST -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-red">M&#225;x:</td>
		</tr>
		<tr>
			<td align="right" class="ml-cyan">M&#237;n:</td>
		</tr>
		<tr>
			<td align="right" class="ml-green"><br>ST:</td>
		</tr>
		<tr>
			<td align="right" class="ml-wkday">PC:</td>
		</tr>
		</table>
<!-- END: High, Low, ST -->
	</td>
	<td rowspan="3" align="right" valign="middle">
<!-- high, low, st values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td class="ml-red">[--datatype=HT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-cyan">[--datatype=LT --startday=0 --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-green"><br>[--datatype=LT --hideunits]</td>
		</tr>
		<tr>
			<td class="ml-wkday">[--datatype=PC --startday=0]</td>
		</tr>
		</table>
<!-- END: high, low, st values -->
	</td>
	<td colspan="3" rowspan="4" align="right" valign="top">
<!-- Todays info text -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top">
		<tr>
			<td align="right" class="ml-yellow">UV:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Visibilidad:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Humedad</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Punto&nbsp;del&nbsp;Roc&#237;o:</td>
		</tr>
		<tr>
			<td align="right" class="ml-yellow"><br>Pres&#237;on:</td>
		</tr>
		</table>
<!-- END: Todays info text -->	
	</td>
	<td rowspan="4" valign="top">
<!-- Todays info data -->	
		<table cellpadding="0" cellspacing="0" border="0" valign="top" width="80">
		<tr>
			<td class="ml-cyan">[--datatype=UI]&nbsp;~&nbsp;[--datatype=UT]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=VI]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=HM]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=DP]</td>
		</tr>
		<tr>
			<td class="ml-cyan"><br>[--datatype=BR]<br>[--datatype=BD]</td>
		</tr>
		</table>
<!-- END: Todays info data -->
	</td>
	<td colspan="4" align="center" valign="bottom" class="ml-yellow">los pr&#243;ximos d&#237;as</td>
</tr>
<tr><!-- 4 weekday names -->
	<td align="center" class="ml-wkday">[--datatype=DW --startday=1]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=2]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=3]</td>
	<td align="center" class="ml-wkday">[--datatype=DW --startday=4]</td>
</tr>
<tr>
	<td><!-- Day 1 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=1]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=1 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=1 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=1]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 2 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=2]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=2 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=2 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=2]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 3 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=3]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=3 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=3 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=3]</td>
		</tr>
		</table>
	</td>
	<td><!-- Day 4 info -->
		<table cellpadding="0" cellspacing="0" border="0" width="70">
		<tr>
			<td colspan="3" align="center"><img src="[--datatype=WF --startday=4]" width="40"/></td>
		</tr>
		<tr>
			<td align="center" class="ml-red">[--datatype=HT --startday=4 --hideunits]</td>
			<td align="center" class="ml-green">~</td>
			<td align="center" class="ml-cyan">[--datatype=LT --startday=4 --hideunits]</td>
		</tr>
		<tr>
			<td colspan="3" align="center" class="ml-wkday">[--datatype=PC --startday=4]</td>
		</tr>
		</table>
	</td>
</tr>
<tr>
	<td colspan="4" class="hugelight">&nbsp;&nbsp;[--datatype=CC]</td>
	<td colspan="4" class="hugelight">&nbsp;</td>
</tr>
<tr>
	<td rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=BS]" width="50"/><br><br>[--datatype=WD] [--datatype=WS]</td>
	<td colspan="3" rowspan="2" align="center" class="ml-yellow"><img src="[--datatype=MF]" width="50"/><br><br>[--datatype=MP]</td>
	<td colspan="3">
<!-- sunrise - sunset & daylight text -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr>
			<td align="right" class="ml-sr">Salida&nbsp;del&nbsp;Sol:</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">Puesto del Sol:</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>Horas de Luz:</td>
		</tr>
		</table>
<!-- END: sunrise - sunset & daylight text -->
	</td>
	<td align="center">
<!-- Today: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL]</td>
		</tr>
		</table>
<!-- END: Today: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 1: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=1]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=1]</td>
		</tr>
		</table>
<!-- END: Day 1: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 2: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=2]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=2]</td>
		</tr>
		</table>
<!-- END: Day 2: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 3: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=3]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=3]</td>
		</tr>
		</table>
<!-- END: Day 3: sunrise - sunset & daylight values -->
	</td>
	<td align="center">
<!-- Day 4: sunrise - sunset & daylight values -->
		<table cellpadding="0" cellspacing="0" border="0">
		<tr align="center">
			<td align="right" class="ml-sr">[--datatype=SR --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="md-ss">[--datatype=SS --startday=4]</td>
		</tr>
		<tr>
			<td align="right" class="ml-daylight"><br>[--datatype=DL --startday=4]</td>
		</tr>
		</table>
<!-- END: Day 4: sunrise - sunset & daylight values -->
	</td>
</tr>
<tr>
	<td colspan="5" align="right" valign="bottom" class="smalldark">Last Update: [datatype=LU]</td>
	<td colspan="3" align="right" valign="bottom" class="smalldark">Last Fetch: [datatype=LF]</td>
</tr>
</table>



</body>
</html>
```

Now that conky does images I use that totally:
[Weather with Images]("http://conky.linux-hardcore.com/?page_id=2305")
[Conky v1.7.2 with LUA rings]("http://conky.linux-hardcore.com/?page_id=3459")
amd my latest: [1-2-3-liner]("http://conky.linux-hardcore.com/?page_id=3651") see the bottom of the page for the weather template.

Have a nice day.
Bruce

---

### Post by xeddog on 2009-11-23
Thanks for that.  I took a look at ARCH.  While I like the clean, simple, and customizable parts of it, I am the type that just like to push a couple of buttons and the thing will recognize all of my hardware, install proper drivers, and then install itself.  GUI and all.  In general I don't care to complile my own [excrement].  Gimme a package and away I go.  

I might go to Arch someday, but probably no time soon.  Although it does look like there are quite a few times in the Linux community that you have to compile your own [excrement], or do without.  I should probably start learning how do do that.

Thanks again,

xeddog

---

### Post by xeddog on 2009-12-02
Kai - 

I found a way to edit the control file for the deb package.  I changed ..webkitgtk to ..webkit, and the package installs.  Still doesn't work, but I gave it a shot.  I have not done ANY investigation yet as to why it didn't work, and I'm not sure if I will.  If I do look into it further I will post what I find.  Hopefully it won't be some really simple "doh!" mistake.  :-)

xeddog

---

### Post by xeddog on 2009-12-06
Kaivalage - 

I have managed to get the gtk-desktop-info package installed on my Karmic 64-bit install.  As far as I can tell I have all of the dependencies taken care of.  As I said before, I changed the ..webkitgtk to ..webkit and the package installes without any error messages.  But when I run it I get:

```
GLib-ERROR **: The thread system is not yet initialized.
aborting...
Aborted
```


I have no clue what this means so any light that you can shed would be GREATLY appreciated.

xeddog

---

### Post by kaivalagi on 2009-12-07
> **xeddog said:**
> Kaivalage - 

I have managed to get the gtk-desktop-info package installed on my Karmic 64-bit install.  As far as I can tell I have all of the dependencies taken care of.  As I said before, I changed the ..webkitgtk to ..webkit and the package installes without any error messages.  But when I run it I get:

```
GLib-ERROR **: The thread system is not yet initialized.
aborting...
Aborted
```


I have no clue what this means so any light that you can shed would be GREATLY appreciated.

xeddog

Not sure as I dont run Ubuntu but I did find this bug report:

```
http://code.google.com/p/pywebkitgtk/issues/detail?id=43
```

I might be seeing things but maybe putting the following just after the imports of the gtk_desktop_info.py file might help:

```
gobject.threads_init()
```

I have been a bit pre-occupied of late with tropical fish issues, the PC has not been sat at half as much...I haven't even tried to run this app on Arch yet...

---

### Post by kanorhu on 2009-12-07
Karmic users:
python-webkitgtk was a real package in intrepid, got renamed to python-webkit in jaunty, and the transitional package was not even included in karmic repos
But if you install the jaunty transitional package that just checks that you have installed the python-webkit package you will get rid of this error
[http://packages.ubuntu.com/search?keywords=python-webkitgtk](http://packages.ubuntu.com/search?keywords=python-webkitgtk)
direct link to deb:
[http://mirror.rootguide.org/ubuntu/pool/universe/p/pywebkitgtk/python-webkitgtk_1.0.2-1ubuntu1_i386.deb](http://mirror.rootguide.org/ubuntu/pool/universe/p/pywebkitgtk/python-webkitgtk_1.0.2-1ubuntu1_i386.deb)

However I still cant run gtk-desktop-info because of strange errors:

```

TypeError: can't convert return value to desired type

```

I would like soo much to feel the experience of gtk-desktop-info, no luck :(

---

### Post by kaivalagi on 2009-12-07
Okay, I have the app working again but in Arch not tested in Ubuntu...as a consequence I can't publish the changes to my ppa and provide packages to install. Not sure if that will change either...

There is a risk anyway that what changes I have made to get it working in Arch mean it won't work in Ubuntu, but lets hope not...

There are some new features in in the main app, to allow for custom head sections in the html output, so support for various javascript content can be provided by the user.

For now, anyone trying to get the app working can try doing the following:

[LIST=1]
[*]Extract the attached .py file
[*]Copy the file over the top of the old one using "sudo cp /path/to/new/gtk_desktop_info.py /usr/share/gtk-desktop-info/"
[*]Run the app as per normal...
[/LIST]

Run gtk-desktop-info --help as before to see the options, the below is the new one i mentioned above:

```
  --overridehead=FILE   Override the default html head construction of the
                        app, opting for a user based template instead.

```

Hope that helps, and sorry for the awkwardness of it all...

I do have more changes in the plugin code elsewhere but for now I figure getting the app working with existing plugin code would be best

I'll try and help where I can with issues but I have a lot on and other concerns...not so much playtime anymore :(

---

### Post by xeddog on 2009-12-07
kaivalagi - 

[SIZE="7"]YOODAMAN!!!!!!![/SIZE]

WOOOOOOOOOHOOOOOOOOOO!  This was the last thing keeping me from upgrading my 32-bit Jaunty to the 64-bit Karmic, so I will probably do that this coming weekend.

To recap everything I did (at least the things that I think made it work) - 

1.  Edited the deb file to change the dependency of the package gtk-desktop-info_0.24_all.deb from python-webkitgtk to python-webkit.

2.  Installed the package

3.  Copied the new gtk-desktop-info.py file you gave us to the Karmic disk.  

NOTE:  I made sure that ```
gobject.threads_init()
``` after the includes was there.  I added it to the "old" version I had and it got me past the threads error but gave me tons of other errors that this new program did not.

4.  copied all of my templates, config files, etc, from my 32-bit Jaunty disk to my 64-bit Karmic disk.


After all this, I have to say that I still don't have my radar map working, but I am confident now that it is something minor and I just need to go thru everything again and find what is missing or wrong.  But I am now a happy man.  (Doesn't take much, does it.)


Thanks again Kai,

xeddog

---

### Post by kaivalagi on 2009-12-08
> **xeddog said:**
> 
After all this, I have to say that I still don't have my radar map working, but I am confident now that it is something minor and I just need to go thru everything again and find what is missing or wrong.  But I am now a happy man.  (Doesn't take much, does it.)


Thanks again Kai,

xeddog

Glad to you you got it working, the webkit library had changed slightly and caused issues. My main worry was that the version in Arch was different in Ubuntu but all looks okay :)

At some point I'll be changing the install instructions to install it without the deb packages so I can support all Linux distros properly. Once I am happy that the install process is covered off I'll be updating the source on launchpad and installs can be done from the command line easily enough. The new install process would come from the inner working of the Arch PKGBUILD attached, it should make sense to you, it's just a bunch of commands to run...let me know what you think

---

### Post by xeddog on 2009-12-09
Kai - 

Looks like I might have been a little premature when I said it was working.  Some of it does . . .sorta.

I run the gtk-desktop-info command twice.  Once for weather and forecast data, and a second time just for the weather map (radar image).

The first command to display the current weather data and the forecast data is a little odd to me.  When I first run the command, nothing happens for a while.  I'm not sure, but I don't think I get the weather data until the first "interval=" expires.  Then it displays the data.  When I run the command from a terminal I get no messages and the log file remains 0 bytes.

When I run the command for the weather map, I get the "cell" where the map should be displayed.  It creates the background and then has the Weather Channel icon in the upper left and the header.  Nothing else.

I can't give any diagnostic messages because it doesn't seem to do the same thing two times in a row as far as messages goes.  One time I tried running each command in a separate terminal window.  The First command to display the current and forecast data produced no messages.  The command for the radar map put out a whole bunch of stuff.  The next time neither put out any messages (logfiles were 0 butes too).  One time as I was watching the /tmp/ directory I saw where one of them apparently went into a loop and started creating the weathermap_... files over and over and over and . . .   In a space of about two minutes there were probably 50 of them.  Had to kill both commands to get it to stop.

Anyway, I am going to keep playing with it for a while.  I think I will be ok just running the weather data and skip the radar image until I can get it figured out.

xeddog


EDIT:  Well, two more times it has started a loop creating the temporary files in the /tmp directory.  I just checked again and there must have been over 200 of them.  [substitute your favorite word for EXCREMENT here]!!!

---

### Post by kaivalagi on 2009-12-09
> **xeddog said:**
> Kai - 

Looks like I might have been a little premature when I said it was working.  Some of it does . . .sorta.

I run the gtk-desktop-info command twice.  Once for weather and forecast data, and a second time just for the weather map (radar image).

The first command to display the current weather data and the forecast data is a little odd to me.  When I first run the command, nothing happens for a while.  I'm not sure, but I don't think I get the weather data until the first "interval=" expires.  Then it displays the data.  When I run the command from a terminal I get no messages and the log file remains 0 bytes.

When I run the command for the weather map, I get the "cell" where the map should be displayed.  It creates the background and then has the Weather Channel icon in the upper left and the header.  Nothing else.

I can't give any diagnostic messages because it doesn't seem to do the same thing two times in a row as far as messages goes.  One time I tried running each command in a separate terminal window.  The First command to display the current and forecast data produced no messages.  The command for the radar map put out a whole bunch of stuff.  The next time neither put out any messages (logfiles were 0 butes too).  One time as I was watching the /tmp/ directory I saw where one of them apparently went into a loop and started creating the weathermap_... files over and over and over and . . .   In a space of about two minutes there were probably 50 of them.  Had to kill both commands to get it to stop.

Anyway, I am going to keep playing with it for a while.  I think I will be ok just running the weather data and skip the radar image until I can get it figured out.

xeddog


EDIT:  Well, two more times it has started a loop creating the temporary files in the /tmp directory.  I just checked again and there must have been over 200 of them.  [substitute your favorite word for EXCREMENT here]!!!

mmmmm, I'll take a look in the next couple of days, when I ran it myself before providing the new .py file I got weather data straight away but can't recall what happened with the weather map. I still haven't setup my system to use it yet as I've been playing with xmonad and haskell instead. At the weekend I'll try setting it up properly based on my previous config settings which worked in Ubuntu and see what I find.

Just got in from a software release at work, it's currently 3:20am so I can't really make much sense of it right now :) I can't sleep now and am mentally drained, grrrrhhhh - movie time I think

---

### Post by xeddog on 2009-12-10
> Just got in from a software release at work, it's currently 3:20am so I can't really make much sense of it right now  I can't sleep now and am mentally drained, grrrrhhhh - movie time I think 

Oh man!  I remember those loooooooong implementation days (or weekends).  Rest up.  This isn't important.

xeddog

---

### Post by kaivalagi on 2010-01-09
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```
Then follow the modified first post instructions for the scripts
[/COLOR]

---

### Post by Mahngiel on 2010-01-09
i'm really interested in this, but i can't seem to find the python-webkitgtk, it's broken

---

### Post by kaivalagi on 2010-01-09
> **Mahngiel said:**
> i'm really interested in this, but i can't seem to find the python-webkitgtk, it's broken

They changed the name of the webkit package on new versions of Ubuntu affecting this packages dependencies, hence broken. Now we have the conkyhardcore PPA I should be able to get a fix out. For now though, while you wait, you could install it from the tarball found on the ppa. See the first post for details of the url.

---

### Post by jjrp78 on 2010-05-17
Hello,

Any release for Ubuntu 10.04 in the oven?

---

### Post by kaivalagi on 2010-05-17
Development has pretty much stopped now as I am too busy and have also moved distro so without setting up Ubuntu just to test it for other users I am a bit stuck.

If you want to try it you may be able to install it using the install instructions for jaunty..it's python based so should be fine, only dependencies might be an issue but you could force the install and then track down the packages needed as I am sure they'll be there but may have changed names,

---

### Post by karthick87 on 2010-06-12
> **kaivalagi said:**
> [SIZE=1][COLOR=RoyalBlue]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR=Blue][SIZE=3]IMPORTANT NEWS[/SIZE][/COLOR]**[COLOR=Blue]

All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.

The ppa can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/%7Econkyhardcore/+archive/ppa")

To use this ppa first delete the old ppa files using this:
```
sudo rm /etc/apt/sources.list.d/m-buck*
```Then follow the modified first post instructions for the scripts
__________________________________________________________________________________________________________________________________[/COLOR]

[COLOR=Green][B]If you create any good custom templates and styles, please post them. I plan on adding a custom templates and styles folder in the long term....
Also, any developers out there that want to include a new plugin of thier own, just speak up...I'd always be happy to add functionality if it's any good[/B][/COLOR]

**_[SIZE=3][COLOR=Blue]Intro[/COLOR][/SIZE]_**

gtk-desktop-info is a python tool to display various pieces of information directly on the desktop, using plugins for html rendering, with html templates and css style sheets for formatting.

The application has been created off the back of existing python scripts used with Conky. The reason for it's creation is a simple one, Conky is great but formatting can suck sometimes...html seemed the obvious choice of formatting giving the user the ability to construct output in a variety of styles based on understood techniques.

Please, please, please, before asking any questions have a good read of the attached guide.

General points to note about the app are:
[LIST]
[*]Very lightweight and low cpu usage
[*]Creates cropped images of the background wallpaper and uses them for the generated html background, effectively making the window transparent.
[*]Utilises webkit html rendering engine and supports images, javascript and flash as you would expect in the browser
[*]Ability to customise any output within the boundaries of what can be done with html, and as it's html there are plenty of editors out there which can help with design
[*]All output content is scrollable, so the window size remains unchanged. Using the scroll wheel on a mouse will alway you to see the extra content
[*]Variety of plugins available and you also have the ability to use external scripts for rendering content too
[/LIST]

**_[SIZE=3][COLOR=Blue]Plugins[/COLOR][/SIZE]_**

All the plugins have come from my conky tinkering of the past, and have been adapted to output html based information, including weather/moon/wind icons for forecasts, and coverart for music. Plugins are defined using the –plugin option of the main application.

Below is a summary of each plugin.

[LIST]
[*]“deluge” – this plugin provides a breakdown of bit torrent information, when bit torrents are managed by Deluge. It can provide detailed and/or summary info.
[*]“email” - this plugin provides email account information, a count of unread emails and optionally details of the sender and subject of the emails.
[*]“exaile” - this plugin displays Exaile based song information, cover art, rating, progress etc
[*]“feedparser” - this plugin provides rss/atom feed information
[*]“forecast” - this plugin provides weather forecast information from weather.com for a given location. It includes weather, moon and wind images, detailing the weather.
[*]“googlecalendar” - this plugin provides Google Calendar event information.
[*]“null” - this plugin provides a means to use html, javascript and flash only content. By default is displays a javascript clock.
[*]“pidgin” - this plugin provides pidgin buddy information, telling you who is online and what their status is.
[*]“processinfo” - this plugin provides process information, telling you a processes id, cpu usage and memory usage. The information can be sorted by cpu or memory usage
[*]“rhythmbox”  - this plugin displays Rhythmbox based song information, cover art, rating, progress etc
[*]“shell” - this plugin provides a means to execute scripts and commands from within a template. Whatever can be done on the command line can be done here too.
[*]“tomboy” - this plugin provides information on Tomboy based notes, keeping most formatting from the notes intact in the output.
[*]“twitter” - this plugin provides information on all your twitter friends, shown newest to oldest - note: to get running at the very least enter your username and password into the config file copied to ~/.config/gtk-desktop-info/plugin_twitter.config
[/LIST]

Note: The shell plugin will provide the equivalent functional to that used with exec/execi calls in Conky. The big difference however, is that it sources all the results from execs inside [] from within a template file, meaning that formatting of command line results is much simpler and neater. A lyrics scripts would work nicely in it for example ;)

**_[SIZE=3][COLOR=Blue]Current Limitations[/COLOR][/SIZE]_**

Compiz wallpaper settings are not supported yet, however gnome, xfce, kde3, and kde4 are.

If tiling or simple background colours are used, the application will no handle these well.

I am attempting to find a better way to handle system wallpaper, independently from the window manager type, so that the only thing this application will be dependant on is gtk, webkit and python libraries. However this may be some time off. If you have issues with wallpapers and the fake transparency is not working, I suggest you use the –wallpaper option, as described in the guide.


**_[SIZE=3][COLOR=Blue]Basic Install[/COLOR][/SIZE]_**

**[COLOR=Blue]Method 1: Using apt[/COLOR]**

1) Create the necessary list file for access to the repository by running one of these:

Karmic Koala:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-karmic.list -O /etc/apt/sources.list.d/conkyhardcore-karmic.list
```Jaunty Jackalope:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-jaunty.list -O /etc/apt/sources.list.d/conkyhardcore-jaunty.list
```Intrepid Ibex:
```
sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-intrepid.list -O /etc/apt/sources.list.d/conkyhardcore-intrepid.list
```2) Add the gtk-desktop-info repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-key.gpg -O- | sudo apt-key add -
```3) Now that is done simply run the following to install

```
sudo apt-get update && sudo apt-get install gtk-desktop-info

```**[COLOR=Blue]Method 2: Using tar.gz file[/COLOR]**

**Only go this route if you know what you're doing, you are not likely to get much help if you get stuck!**

1) Go to [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/%7Econkyhardcore/+archive/ppa") and download the latest tar.gz files for gtk-desktop-info and gtk-desktop-info-data packages.

2) Extract all the contents of the tar.gz files to an appropriate folder of your choice, the default location is /usr/share/gtk-desktop-info

3) Copy the gtk-desktop-info and gtk-desktop-info.guide script files to /usr/bin, edit them to point to the folder you extracted everything to, and make them executable

There are several dependencies for the app to run, these are:
[LIST]
[*]Python Google GData API
[*]Python PyWebKitGtk libraries
[*]Python Imaging library
[*]Python Xlib Libraries
[/LIST]
Unless you are using a non-Debian based OS I don't suggest this. Users of Debian/Ubuntu flavour OS's should ideally use the first method as all dependencies will be handled. You will not receive updates using this method either.

Any further details on setup are orientated around the deb package based install, so may differ from what you choose your setup to be, if done using the tarball.


**_[SIZE=3][COLOR=Blue]Usage Help[/COLOR][/SIZE]_**

Refer to the attached guide for a detailed explanation of the application, along with information on the command line usage etc. The guide is also available within the install, it can be opened by running the following (evince is expected to be installed):

```
gtk-desktop-info.guide
```You can also see the available options by running this in a terminal:

```
gtk-desktop-info -h
```
**_[SIZE=3][COLOR=Blue]Development History[/COLOR][/SIZE]_**

Development history going forwards can be seen here [https://code.launchpad.net/~m-buck/+junk/gtk-desktop-info]("https://code.launchpad.net/%7Em-buck/+junk/gtk-desktop-info")

All packages available from me can be found here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/%7Econkyhardcore/+archive/ppa")


How to install **gtk-desktop-info **it in ubuntu 10.04(Lucid)

---

### Post by kaivalagi on 2010-06-12
> **getyourkarthick said:**
> How to install **gtk-desktop-info **it in ubuntu 10.04(Lucid)

I've not even tested in lucid as I don't run ubuntu any more...I've just copied over the packages from a previous version (all python so if not depreciated then all should be fine...big if mind you

The first post is updated now with the details for lucid, the packages should be available shortly.

---

### Post by karthick87 on 2010-06-12
```
karthick@Ubuntu-desktop:~$ sudo wget -q http://www.kaivalagi.com/ubuntu/ppa/conkyhardcore-lucid.list -O /etc/apt/sources.list.d/conkyhardcore-lucid.list
karthick@Ubuntu-desktop:~$ sudo apt-get update && sudo apt-get install gtk-desktop-info
Get:1 http://ppa.launchpad.net lucid Release.gpg [307B]                        
Ign http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/ lucid/main Translation-en_IN
Hit http://ppa.launchpad.net lucid Release.gpg                                 
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ lucid/main Translation-en_IN
Get:2 http://ppa.launchpad.net lucid Release [57.3kB]                          
Hit http://download.virtualbox.org lucid Release.gpg                           
Ign http://download.virtualbox.org/virtualbox/debian/ lucid/non-free Translation-en_IN
Get:3 http://security.ubuntu.com lucid-security Release.gpg [189B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_IN
Hit http://download.virtualbox.org lucid Release                               
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_IN   
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_IN
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_IN
Get:4 http://security.ubuntu.com lucid-security Release [38.5kB]               
Hit http://download.virtualbox.org lucid/non-free Packages                     
Hit http://ppa.launchpad.net lucid Release                                     
Ign http://ppa.launchpad.net lucid Release                                     
Get:5 http://ppa.launchpad.net lucid/main Packages [1,828B]                    
Get:6 http://ppa.launchpad.net lucid/main Sources [1,525B]                     
Hit http://ppa.launchpad.net lucid/main Packages                               
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]      
Hit http://in.archive.ubuntu.com lucid Release.gpg                             
Get:8 http://security.ubuntu.com lucid-security/main Packages [34.6kB]
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_IN          
Get:9 http://security.ubuntu.com lucid-security/multiverse Packages [1,668B]   
Get:10 http://security.ubuntu.com lucid-security/universe Packages [13.2kB] 
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_IN      
Ign http://in.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_IN
Get:11 http://in.archive.ubuntu.com lucid-updates Release.gpg [189B]
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_IN
Ign http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_IN
Hit http://in.archive.ubuntu.com lucid Release                                 
Get:12 http://in.archive.ubuntu.com lucid-updates Release [38.5kB]             
Hit http://in.archive.ubuntu.com lucid/main Packages                           
Hit http://in.archive.ubuntu.com lucid/restricted Packages                     
Hit http://in.archive.ubuntu.com lucid/main Sources                            
Hit http://in.archive.ubuntu.com lucid/restricted Sources                      
Hit http://in.archive.ubuntu.com lucid/universe Packages                       
Hit http://in.archive.ubuntu.com lucid/universe Sources                        
Hit http://in.archive.ubuntu.com lucid/multiverse Packages                     
Hit http://in.archive.ubuntu.com lucid/multiverse Sources                      
Get:13 http://in.archive.ubuntu.com lucid-updates/restricted Packages [2,102B] 
Get:14 http://in.archive.ubuntu.com lucid-updates/main Packages [196kB]        
Get:15 http://in.archive.ubuntu.com lucid-updates/multiverse Packages [1,993B] 
Get:16 http://in.archive.ubuntu.com lucid-updates/universe Packages [47.2kB]   
Fetched 435kB in 9s (46.5kB/s)                                                 
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1E5D5E8D66AE0775
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gtk-desktop-info: Depends: python-webkitgtk but it is not installable
E: Broken packages

```

I have tried,but unable to install :(

---

### Post by kaivalagi on 2010-06-13
Dependency package names have changed....it will require a change to the package but I am in no position to do that right now...

To be honest I now use conky anyway instead of this, as conky supports images and cairo and can do nifty stuff these days.

---

### Post by tomski on 2010-07-31
i guess this is end of life then unless someone can work out what needs to done & takes over this once great sys info widget

i had had great plans to use this & have compiz have it in the widget layer

thanks for what you created though
edit:
was going to ask bout the change to arch but i read ya blog ....nice :)

---

### Post by kaivalagi on 2010-07-31
I may continue it some day, not sure...for now though I just don't have the time or energy...sorry

---

### Post by sh4r4d on 2012-04-28
Hi Kav,
I am trying to install it into oneiric ubuntu 11.10
but I am not successful to get is working

As no installation were  here I have setup it using setup.py


It open my default browser conkeror and than one empty window.


Any idea what could be the reason.

--
Thanks

---

### Post by kaivalagi on 2012-04-28
I wouldn't even attempt to install it to be honest, the dependencies for packages would be out of sync due to python3 arriving proper and general changes between versions of Ubuntu. I am no longer supporting the script as I don't have the time :(

---

### Post by b.bhargav on 2013-02-20
> **kaivalagi said:**
> I wouldn't even attempt to install it to be honest, the dependencies for packages would be out of sync due to python3 arriving proper and general changes between versions of Ubuntu. I am no longer supporting the script as I don't have the time :(
@kaivalagi I really appreciate what you've done. I'm using ubuntu 12.10 with conky but managing the UI with conky is a bit tough job for me.(Took me about 4 hours just to change a few minor things). May be something like this needs to come back to life again.
trying somethings from here:
[http://ubuntuforums.org/showthread.php?p=6097476](http://ubuntuforums.org/showthread.php?p=6097476)

---

### Post by wildmanne39 on 2013-02-20
kaivalagi great job!!! Old thread closed.

---

