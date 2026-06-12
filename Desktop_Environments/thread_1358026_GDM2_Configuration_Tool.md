---
title: "GDM2 Configuration Tool"
date: 2009-12-17
forum: Desktop Environments
---

### Post by exosyst on 2009-12-17
Hey guys, I wrote a tool to let you configure a bit more of the new GDM that comes with Karmic Koala.

It took me nearly a whole day (i've not used GTK with python before!) so I hope it helps someone as i'll consider it a success. **Note that it requires imagemagick** to work correctly and to enable you to do fancy stuff to the background image (blur is only available option in this currently).

It's fairly late now and I'm tired but from what I can see it works on my system but standard disclaimer applies (IT'S YOUR OWN FAULT :P) as I can't promise your curtains/cat won't catch fire due to it.

Enjoy

***UPDATE***: So the awesome Growlf has done some great work based on my original and there is now a Gladey version available that doesn't depend on ImageMagick. Maybe we can get the Ubuntu guys to include this in lieu of the current one if nothing new comes along for Lucid?

**How to install:**
Add the new repository
```
sudo add-apt-repository ppa:gdm2setup/gdm2setup
```
update your packages
```
sudo apt-get update
```
install it!
```
sudo apt-get install python-gdm2setup
```

This should now appear under System>Administration>Login Screen(GDM2Setup). Run it and see how you get on!

Any feedback, post in this thread, or [join the group and do some development!]("https://launchpad.net/gdm2setup") :D


The original script is included still if you just want to mess with it but the preferred way is to use the PPA
When you download it you have to make it executable using:
```
chmod u+x ./gdm-setup.py
```
and then you can run it as often as needed with:
```
gksudo ./gdm-setup.py
```
all from within the terminal.

---

### Post by prmcafee on 2009-12-17
> **exosyst said:**
> Hey guys, I wrote a tool to let you configure a bit more of the new GDM that comes with Karmic Koalas.

It took me nearly a whole day (i've not used GTK with python before!) so I hope it helps someone as i'll consider it a success. Note that it requires imagemagick to do fancy stuff to the background image you choose, I never added an option to choose if you want to blur but left it on by default as it's pretty tasteful.

It's fairly late now and I'm tired but from what I can see it works on my system but standard disclaimer applies (IT'S YOUR OWN FAULT :P) as I can't promise your curtains/cat won't catch fire due to it.

Enjoy

Works beautifully!  Thanks!

---

### Post by exosyst on 2009-12-18
This is it at the moment:
[IMG]http://imgur.com/dVVXU.png[/IMG]

---

### Post by guerreau on 2009-12-27
thanks to exosyt

l. 159
self.ShowUserList  >>>  self.ShowUserlist

---

### Post by dzon65 on 2009-12-27
Hi,tweaked my xsplash and gdm but this looks so good.But,how do I install this?

---

### Post by Yanneck on 2009-12-27
1.) Download the Code.

2.) Copy it into /home/<your user-name>

3.) Open a console and make the file executable:

```

chmod a+x gdm-setup.py

```

4.) Start Script with

```

gksu ./gdm-setup.py

```

Here we go. :-)

Sry 4 bad english.

---

### Post by dzon65 on 2009-12-27
Yep,that's what I did but can't find it.
Ps:my english's worse.

---

### Post by Yanneck on 2009-12-27
Sry. 

You have to do this:

```

gksu ./gdm-setup.py

```

---

### Post by dzon65 on 2009-12-27
Terminal is pointing me to this theme error.Deleted some pieces in the gtkrc,but don't understand why this could interfere with installing this.
Where should I find it,system>login or am I getting it wrong.Anyhow,here's the outcome when I put it in a terminal.
yui@ubuntu:~$ gksu ./gdm-setup.py
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:34: Kan invoegbestand ‘styles/panelstyles’ niet vinden
/home/yui/.themes/Kuler 2 v3/gtk-2.0/gtkrc:624: error: invalid string constant "panel", expected valid string constant
yui@ubuntu:~$

---

### Post by dzon65 on 2009-12-27
Quickly reinstalled those "missing"parts,error doesn't pop up but no install.

---

### Post by Yanneck on 2009-12-27
Have you tried it with another theme?

---

### Post by dzon65 on 2009-12-28
I allready "fixed" the theme.Now I changed the theme alltogether.But nowI'm getting this:
yui@ubuntu:~$ chmod a+x gdm-setup.py
yui@ubuntu:~$ gksu ./gdm-setup.py
Traceback (most recent call last):  File "./gdm-setup.py", line 305, in <module>
    ConfigWindow()
  File "./gdm-setup.py", line 159, in __init__
    self.showUserList.set_active(True)
AttributeError: 'ConfigWindow' object has no attribute 'showUserList'
yui@ubuntu:~$ 
Could someone explain step by step how to install this.Must be doing something wrong here.
h,like I said before,I allready changed my splash and gdm before using this:[HowTO: Comprehensive Guide to Customising GDM and XSplash - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1333683")
I changed everything back to default,also changed automatic login back to show users list (which gave the above error),made a starter pointing to the file but now it sais it needs to be opened as root.

---

### Post by dzon65 on 2009-12-28
Ok,managed to get the configuration panel to open when taking root of the file.But I tried several size backgrounds and they all show very fuzzy.

---

### Post by Psumi on 2009-12-28
You also may want to realize that someone may not have the image in their xsplash directory:

```
Traceback (most recent call last):
  File "./gdm-setup.py", line 327, in <module>
    ConfigWindow()
  File "./gdm-setup.py", line 183, in __init__
    self.PreviewThumb.set_from_pixbuf(gtk.gdk.pixbuf_new_from_file(GetWallpaper()).scale_simple(150,150,gtk.gdk.INTERP_BILINEAR))
glib.GError: Failed to open file '/usr/share/images/xsplash/bg_2560x1600.jpg': No such file or directory
```

---

### Post by dzon65 on 2009-12-28
About that blurred background,I noticed on the shot there's an option to blur...which I don't have.Seems to be blurred all the time.[IMG]file:///tmp/moz-screenshot.png[/IMG]

---

### Post by exosyst on 2009-12-28
Hey dzon65:

I updated the script yesterday so try redownloading. With regards to themes, it should detect any themes in /usr/share/themes/ so if they're in there (and valid!) it should work.

If you want to do a screenshot - I recommend uploading it to somewhere like [http://imgur.com/](http://imgur.com/) and then you can use the "img" tags to link to it that way.

Everyone else:
Glad it's of use , any patches/fixes you guys want made either post the changes here or attach a diff or stick it up on [http://pastebin.com/](http://pastebin.com/) or somewhere.

Regards.

---

### Post by warriorpoet on 2009-12-29
Tried with my custom theme created in Appearance settings using bits, pieces and colors from standard themes.  Saved theme, checked location in themes folder, still can't use it.

edit: my apologies- it is not in the theme folder.  Don't know where the "Save As" button saves it, but not the theme folder.

edit2: your script also seems to delete changes made using "$gksudo -u gdm dbus-launch gnome-appearance-properties".  Might want to check that :)

---

### Post by exosyst on 2009-12-29
warriorpoet:

If you've made a custom theme it stores it in ~/.themes and if needs to go into /usr/share/themes to be accessible for GDM as far as the script is concerned.

With regards to the deletion of existing changes, I've looked through my code and can't see what/where/how I'd delete any existing changes except for when they're altered in the GUI whereupon they're committed immediately.

What does it delete your end? I tried your snippet here and got ```
I/O error : No such file or directory
``` spewed at me and it loaded two Accessibility panel icons so I decided not to change anything! :(

---

### Post by Sunny0815 on 2009-12-30
Even on the risk of sounding stupid: Where to download? I cannot find a link.  :confused:

---

### Post by Psumi on 2009-12-30
I'm guessing you're never going to fix that issue I brought up (Which should be fixed.)

---

### Post by exosyst on 2009-12-30
Psumi:

I can't replicate your error, It gets the GDM2 wallpaper from the gconf settings of the GDM user and if that's incorrect I suggest checking your setup as it's possible that something (someone?) has changed your GDM settings from the defaults.

It doesn't read from the xsplash directory unless that is the location set in gconf. You could add a check for the files existence before trying to set the icon but it SHOULD be there as far as I know.

If you have any changes/diffs please attach them and I'll add them to the script.

Hope that helps!

---

### Post by Psumi on 2009-12-30
> **exosyst said:**
> Psumi:

I can't replicate your error, It gets the GDM2 wallpaper from the gconf settings of the GDM user and if that's incorrect I suggest checking your setup as it's possible that something (someone?) has changed your GDM settings from the defaults.

It doesn't read from the xsplash directory unless that is the location set in gconf. You could add a check for the files existence before trying to set the icon but it SHOULD be there as far as I know.

If you have any changes/diffs please attach them and I'll add them to the script.

Hope that helps!

That's the default setup actually for ubuntu 9.10 (desktop i386 liveCD)

---

### Post by Baz00 on 2009-12-31
I got the same output as Psumi :
```
gksudo ./gdm-setup.py 
chmod: cannot access `/usr/share/images/xsplash': No such file or directoryTraceback (most recent call last):
  File "./gdm-setup.py", line 327, in <module>
    ConfigWindow()
  File "./gdm-setup.py", line 183, in __init__
    self.PreviewThumb.set_from_pixbuf(gtk.gdk.pixbuf_new_from_file(GetWallpaper()).scale_simple(150,150,gtk.gdk.INTERP_BILINEAR))
glib.GError: Failed to open file '/usr/share/images/xsplash/bg_2560x1600.jpg': No such file or directory

```
I don't really know how too fix that but I can provide more informations if that can help to find out.
Cheers

---

### Post by Psumi on 2009-12-31
By the way, it is there:

[img]http://i50.tinypic.com/8ys7f8.png[/img]

---

### Post by exosyst on 2010-01-01
Happy new year guys - Attached is a fixed version, can you try this out and then I'll replace the main version if this is all good.

As an additional bonus it now updates the picture preview because I think it's working correctly now but as you've not had it working correctly i figure you'd be the best beta testers :D

**Edit:** Had a couple of PMs say the tool works fine so I've updated the version on the first page and removed the attachment from this post.

Please remember to install imagemagick before using it as the selected background image is run through that:

```
sudo apt-get install imagemagick
```

---

### Post by shini-kire on 2010-01-02
I get this error when selecting the image.
 
```
***@****:~$ gksu ./gdm-setup.py
/bin/sh: convert: not found
```any suggestions?

User ubuntu 9.10 Karmic Koala.

Saludos From chile!

---

### Post by exosyst on 2010-01-02
> **shini-kire said:**
> I get this error when selecting the image.
 
```
***@****:~$ gksu ./gdm-setup.py
/bin/sh: convert: not found
```any suggestions?

User ubuntu 9.10 Karmic Koala.

Saludos From chile!


Hey buddy,
As it says on the first page, it requires imagemagick to handle the conversion which is where the 'convert' tool comes from.

```
sudo apt-get install imagemagick
```

should solve it. Regards!

---

### Post by shini-kire on 2010-01-02
> **exosyst said:**
> Hey buddy,
As it says on the first page, it requires imagemagick to handle the conversion which is where the 'convert' tool comes from.

```
sudo apt-get install imagemagick
```should solve it. Regards!

thanks. :P worked well in Relaid knew I was missing when I opened the gdm.py was checking what was the origin and there saw the beginning of the line

```
# Simple configuration for GDM, I used ImageMagick to make it easier, go install it

```
I knew I had not been installed and it installs and worked.
well thanks for topic screens soon.

greetings From Chile!

---

### Post by elcamilo on 2010-01-04
Hi, I've tried your work. It works and it's easy and clean and:
can you add a way to choose and change also the cursor theme?


(don't know why, but since when I've added kubuntu-desktop packages and all his dependencies, to give a try to KDE4, I've the oxygen cursor in my GDM session)

regards

---

### Post by momalle1 on 2010-01-04
This worked well with one exception, when I change the image, it will not accept any image file with spaces in it's name.

---

### Post by growlf on 2010-01-04
@momalle1 it is because the command being used is not escaping the spaces automaticly.  I suspect that @exosyst chose the method that he did for ease of install and overal simplicity by calling the ImageMagick command with popen instead of using one of the libraries that gives direct access to the utility.  This way you dont have to install anything more than just ImageMagic itself.

It is easy to resolve however.  Just add an escaped double-quote (  \"  ) to each side of the file call on line 54 as follows:

```
commandToDo = "convert" + (' -blur','')[not DoBlur] + (' 4x20','')[not DoBlur] + " \"" +WallpaperLocation+ "\" /usr/share/images/xsplash/bg.jpg"
```

Hope that helps.

@exosyst - you rock dude. Thank you for this utility.  Would love to see it in the cheeseshop for easy installation or something similar.  Especially if it could then use the library version of access to ImageMagic.

*G*

---

### Post by momalle1 on 2010-01-05
> **growlf said:**
> @momalle1 it is because the command being used is not escaping the spaces automaticly.  I suspect that @exosyst chose the method that he did for ease of install and overal simplicity by calling the ImageMagick command with popen instead of using one of the libraries that gives direct access to the utility.  This way you dont have to install anything more than just ImageMagic itself.

It is easy to resolve however.  Just add an escaped double-quote (  \"  ) to each side of the file call on line 54 as follows:

```
commandToDo = "convert" + (' -blur','')[not DoBlur] + (' 4x20','')[not DoBlur] + " \"" +WallpaperLocation+ "\" /usr/share/images/xsplash/bg.jpg"
```

Hope that helps.

@exosyst - you rock dude. Thank you for this utility.  Would love to see it in the cheeseshop for easy installation or something similar.  Especially if it could then use the library version of access to ImageMagic.

*G*

Thank you. It's not really a big issue for me, I just thought I'd give the author some feedback!

---

### Post by Falsanox on 2010-01-08
I got some trouble with the theme option. :? I tried to change the themes, but it did't change the gtk-theme to the one I had chosen, but to an ugly one that looks like "simple" and I don't see any icons now. Is there any other possibility to change the themes back to "HumanLogin" and "HumanLoginIcons"?

---

### Post by exosyst on 2010-01-09
You should be able to just choose those themes from the drop downs and it will be back as before.

At the moment, I've been in talks to refactor this program and it should be going up on launchpad (in lieu of any source code appearing from the Ubuntu team) as a fully fledged app rather than this scriptaculous version :D

Regards,
Nick

---

### Post by dzon65 on 2010-01-09
> **exosyst said:**
> You should be able to just choose those themes from the drop downs and it will be back as before.

At the moment, I've been in talks to refactor this program and it should be going up on launchpad (in lieu of any source code appearing from the Ubuntu team) as a fully fledged app rather than this scriptaculous version :D

Regards,
Nick

Mailed around to get this going on a regular menu base.Something should pop up.
Kind regards,John.

---

### Post by Falsanox on 2010-01-09
> **exosyst said:**
> You should be able to just choose those themes from the drop downs and it will be back as before.

At the moment, I've been in talks to refactor this program and it should be going up on launchpad (in lieu of any source code appearing from the Ubuntu team) as a fully fledged app rather than this scriptaculous version :D

Regards,
Nick

That's what I tried, but it doesn't work. It stays so ugly like it is :(

---

### Post by growlf on 2010-01-09
> **Falsanox said:**
> That's what I tried, but it doesn't work. It stays so ugly like it is :(

Run the following command and past the output here:

```
sudo -u gdm gconftool-2 -g /desktop/gnome/interface/gtk_theme
```That might shed some light.

---

### Post by dzon65 on 2010-01-09
Exosyst,Tinivole came up with this:
1) Install the script (or a wrapper for the script) in a bin directory.
 
Code:
---------
install gdm-setup /usr/bin
---------
2) Put a Desktop item in /usr/share/applications/gdm-setup.desktop
 
A typical example of it's contents:
 
Code:
---------
[Desktop Entry]
Version=1.0
Name=GDM2 Configuration Tool
Comment=Tool for editing Login Window
Categories=Application;System;
Exec=/usr/bin/gdm-setup
Terminal=false
Type=Application
---------
And it should appear in Applications->System->GDM2 Configuration Tool
 Hope you can do something with it.
Kind regards,John.

---

### Post by exosyst on 2010-01-10
Thanks for that guys!
;)

---

### Post by Falsanox on 2010-01-11
> **growlf said:**
> Run the following command and past the output here:

```
sudo -u gdm gconftool-2 -g /desktop/gnome/interface/gtk_theme
```That might shed some light.

The output is "HumanLoginIcons". Now it's getting strange: If the command shall show the gtk-theme, why the heck is the output the icon-theme? If the command shall show the icon-theme, why isn't it displayed wrong in the login-screen? :-s

(hope I don't abuse this thread for my problem)

---

### Post by growlf on 2010-01-11
Issue the following commands:

```
sudo -u gdm gconftool-2 -s /desktop/gnome/interface/icon_theme --type string HumanLoginIcons
sudo -u gdm gconftool-2 -s /desktop/gnome/interface/gtk_theme --type string Human

```...that should fix it for now.

I just checked the script, and it does set the correct theme to the correct conf section - so I have no idea why you are having this problem.  Have you used any other gdmconf oriented scripts?  ..or modified exosyst's script at all?

---

### Post by Falsanox on 2010-01-12
Thanks, the themes are fine again now. :) It seems like this was an individual case. I neither changed the script nor I used another script. Maybe these problems occurred, because my system was installed as Hardy and I updated it after every new release. But I think that's rather unlikely.

---

### Post by growlf on 2010-01-12
For anyone following this thread, exosyst and I are putting this thing up on Launchpad now so that we can make a PPA and installer available for ease of use and updates.  This will also allow for it to be placed in your "System Tools" menu upon installation.  

As soon as there is an installer and a PPA available, one of us will post a note here as well.  The current version will be maintained here:
[INDENT][https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)
[/INDENT]It is apparently available now on [Softpedia]("http://linux.softpedia.com/get/System/System-Administration/GDM2-Setup-53621.shtml") as well.

Several new features will be added shortly, such as an actual installer, deb support, accessibility options, message banner, and perhaps some other graphic mods for the wallpaper.  Suggestions are welcome.

---

### Post by growlf on 2010-01-12
Ok, thanks to dzon65, I have added the desktop file into the tarball on Launchpad as well as some basic install instructions.  It can be downloaded from here:

[http://launchpad.net/gdm2setup/origin/0.1/+download/GDM2Setup-0.1.1.tar.gz](http://launchpad.net/gdm2setup/origin/0.1/+download/GDM2Setup-0.1.1.tar.gz)

---

### Post by nilarimogard on 2010-01-17
Any news on the PPA?

---

### Post by r_avital on 2010-01-18
Fantastic, you guys,  a PPA would be great.  More power to both of you and THANKS!

---

### Post by growlf on 2010-01-19
The PPA will come after we have cleaned up the code and added the deb support - in that order.  There is a time-line and a list of blueprints at [Launchpad]("https://launchpad.net/gdm2setup") if you want to see them or would like to add your two cents.

For the moment, I have updated the code on [Launchpad]("https://launchpad.net/gdm2setup") with the newer interface, code changes, and added a couple of small features. New features include: 

[LIST=1]
[*]sorted lists instead of randomly concatenated ones (very noticeable if you have a huge list of icon or GTK themes installed like I do).
[*]the lists (except the auto-login user) all show the current selected value at startup now instead of blank.
[*]tabbed interface.
[*]alt-key accessibility additions for all options (gotta stay 508 compliant :) ).
[*]the dev files are now all separated out to allow folx that know glade to do UI and the folx that know Python to do core.  Even the gconf portion is in it's own file now as well (see the not below on this).
[*]code is simplified and has better error-checking in a most areas - but not all of them yet, we are working on it.
[*]installation instructions and a desktop shortcut file to make things easier for you until we get the PPA done.
[/LIST]
DEV NOTE: There is some difficulty using python-gconf due to security errors that are raised when changing the euid to the 'gdm' user.  This is, I am told, due to how Orbit works now.  So for the moment, and until the situation is resolved, we are using a temporary gconf lib file that is basically the original code calls and uses command line pass-thru type access to gconf, which is not optimal - but works. ;)

Please check out the code and file bug reports, suggestions, etc.  We welcome input!

Until we are sure there are no bugs (at which point we will make a new release tarball and begin working on the PPA) you can get the new beta by using bzr like so:

```
bzr branch lp:gdm2setup

```and then follow the INSTALL instructions.

Please note that this command will download the most recent version from the project trunk, and not necessarily the most stable version.  If you do not already have bzr installed you can do so by:
```
sudo apt-get install bzr
```or by using synaptic and searching for 'bzr' and then installing it.

---

### Post by nilarimogard on 2010-01-19
I cannot start the beta (bzr branch):

```
Traceback (most recent call last):
  File "./gdm2setup.py", line 221, in <module>
    app = GDM2Setup()
  File "./gdm2setup.py", line 131, in __init__
    if self.theme.GetAutoLogin():
  File "/home/andrei/gdm2setup/src/gdmgconf.py", line 60, in GetAutoLogin
    SetAutoLogin(False)
NameError: global name 'SetAutoLogin' is not defined
```

---

### Post by growlf on 2010-01-19
> **nilarimogard said:**
> I cannot start the beta (bzr branch):

Thank you @nilarimogard.  That helps!   It looks like I missed a line that checks for the autologin file existence in the old lib when I converted it.  I have resolved the issue and uploaded a new copy to LP.  Please let me know if there are any other issues that you run  into.

With any luck, I will be able to make a new tarball this evening (on schedual) and release 0.2 so that we can continue on with the installer portion.  Also, in response to your earlier question on the PPA, the plan is to release the working re-vamped core and gui this evening and then the beta installer by no later than the 1st.  ...and then going release 1.0 NLT the 10th.  I have decided to not hold 0.2 or 0.3 release up for the accessibility tab completion (or any other features) but it will still be a major background focus until it is finished.

After that, we are open to new suggestions for additions.  I am thinking of theme files export/import... and maybe a GDM1 Theme import option?  What do you guys think?

---

### Post by kc8hr on 2010-01-19
Man, this is excellent! Thanks for the work--I am a lousy coder, and I really miss the old gdm configuration tool.

---

### Post by nilarimogard on 2010-01-19
Everything is working fine now, thank you!

---

### Post by growlf on 2010-01-20
We have jumped ahead a bit (leaving a few features unfinished for the moment) to get to the beginnings of a distribution channel and an installer for this thing.  Version 0.3 is now available for testing and it is probably easiest to install it using the python installer like so:

```
sudo easy_install gdm2setup
```This will download ***and install*** the *entire* app - GUI, libraries **and** a System / Administration / Login Screen (GDM2Setup) menu item.  This command can be run again later to update the app.  If you have never used easy_install before, check out the docs at [http://peak.telecommunity.com/]("http://peak.telecommunity.com") and download at  [http://peak.telecommunity.com/dist/ez_setup.py](http://peak.telecommunity.com/dist/ez_setup.py)

This is a permanent home for the installer back-end, but we are now moving forward with the deb file and PPA which will still be on Launchpad. For those of you that actually look at the code - this version took on quite a bit of change to allow it to become an installable app.  The most current updates and info will continue to be either here or posted on Launchpad.

The other method of install is to [download it from LP]("http://launchpad.net/gdm2setup/0.2/0.3/+download/gdm2setup-0.3.0.tar.gz"), untar it and then from a terminal window in the resultant folder type: ```
sudo python setup.py install
```  This will also ***install*** the *entire* app - GUI, libraries **and** a System / Administration / Login Screen (GDM2Setup) menu item.  It will not however allow the app to be as easily update-able.

---

### Post by curtlee2002 on 2010-01-20
Great Job

---

### Post by growlf on 2010-01-20
Ok - one step closer!  The deb is now done and has had initial testing.  It is [available on LP]("http://launchpad.net/gdm2setup/0.2/0.3/+download/python-gdm2setup_0.3.0-1_all.deb")  for download and more testing.  Please report all bugs there so that we can track them and expedite any fixes that are needed.

Thank you, everyone, for all your help and praise.  I expect to have the PPA done in the next day or so now, and then we will get back to completing the rest of the original features and requests.  I suspect that once the PPA is up, we will be moving forward at a slightly more realistic pace however.

I  just want to say again that we are very interested in ideas for features and discussion on theme-file support / import of old GDM theme-files.  This forum node is as good a place as any for that discussion :)  Feel free - spout off! :D

---

### Post by growlf on 2010-01-22
If anyone is willing to test the PPA out and report any issues, here it is - finally :o.  Place the following lines in your /etc/apt/sources.list file:

```
# GDM2Setup
deb http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu karmic main #GDM2 Setup Utility
deb-src http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu karmic main #GDM2 Setup Utility (src)
```...add the key for authentication...```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 33C3C104
```...then do the usual...```
sudo apt-get update
sudo apt-get install python-gdm2setup
```The application will now update along with your other packages automatically.  

Thank you in advance for all testing and feedback.  Exosyst will probably update the front post to reflect this shortly.

---

### Post by Squirrel King on 2010-01-22
The PPA repository install worked like a charm, thanks very much :D
I'm looking forward to when it is finished.

---

### Post by Uncle Spellbinder on 2010-01-23
I've neglected the  Desktop Environments section of the forums for ages, visited today after far to long. Stumbled across this thread and I'm elated!  **_Thanks so much for GDM2 Configuration Tool._** Installed via the PPA repo and it works perfectly.

FINALLY! No more Ubuntu Cylon!

---

### Post by growlf on 2010-01-23
> **Uncle Spellbinder said:**
>   **_Thanks so much for GDM2 Configuration Tool._** Installed via the PPA repo and it works perfectly.
You are very welcome! :)  

Heads up to everyone!  There was a small bug in the userlist checkbox on build 0.3.1 that made it select the opposite of what you wanted and also not set the initial value.  This has been resolved and a new deb (0.3.2) is building on LP as I write this.  If you are using the PPA, you will automatically get the update in a few hours (when LP finishes building it).

Thank you for all your bug reports everyone!  They help a lot!

Here are a few screen shots of the new GUI (click to enlarge):

[[IMG]http://imgur.com/dTYg7s.jpg[/IMG]]("http://imgur.com/dTYg7.png")[[IMG]http://imgur.com/1roS9s.jpg[/IMG]]("http://imgur.com/1roS9.png")[[IMG]http://imgur.com/FgoIUs.jpg[/IMG]]("http://imgur.com/FgoIU.png")

---

### Post by kc8hr on 2010-01-23
***_Excellent!_***

---

### Post by hariks0 on 2010-01-25
> **growlf said:**
> If anyone is willing to test the PPA out and report any issues, here it is - finally :o.  Place the following lines in your /etc/apt/sources.list file:

```
# GDM2Setup
deb http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu karmic main #GDM2 Setup Utility
deb-src http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu karmic main #GDM2 Setup Utility (src)
```...add the key for authentication...```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 33C3C104
```...then do the usual...```
sudo apt-get update
sudo apt-get install python-gdm2setup
```The application will now update along with your other packages automatically.  

Thank you in advance for all testing and feedback.  Exosyst will probably update the front post to reflect this shortly.

Why don't you attach a screenshot ? We would love to see gdm2 back.:popcorn:

---

### Post by growlf on 2010-01-25
There are screen shots in the post just above..  #58 in fact.  No major changes have happened to the GUI since that posting (less than a day ago).  At least not yet.  :)  We are working on new features however, and expect that there will be some once they are implemented.

---

### Post by joeknoodle on 2010-01-25
Feature request:

Can this be made to do a random login screen for all my old GDM Logins?

---

### Post by nilarimogard on 2010-01-25
I suggest merging with XSplash Backround settings to get an even better app: [http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984](http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984)

---

### Post by growlf on 2010-01-25
Thank you both, for your suggestions!  

> **joeknoodle said:**
> Feature request:

Can this be made to do a random login screen for all my old GDM Logins?

I definitely think so.  I was kind of thinking about this already in a slightly difernt direction and now that I know there is some interest - I will look into it for real.  So, thank you for the encouragement!!  

The only issue that I see so far is that the old GDM themes don't have a lot that we can pull in - just the background images and an occasional icon. Please, someone, correct me if I am mistaken on this.  Still, that is worth something - yes? 


> **nilarimogard said:**
> I suggest merging with XSplash Backround settings to get an even better app: [http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984](http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984)

Hmmmm..   yeah.  Looking at that now.  I don't want to remake anything pre-existing, but tying xplash support into GDM2Setup could prove very nice.  Thank you for that suggestion!

---

### Post by growlf on 2010-01-25
> **nilarimogard said:**
> I suggest merging with XSplash Backround settings to get an even better app: [http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984](http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984)

Oh.  Wow.  I see what you mean.  I have just spidered a few hundred posts and what amounts to heresay documentation on it and... It is Absolutely a must with GDM2!!  It would seem an obvious omission if not in fact.  I had not understood that was where the throbber came from.    This fits with the theme portion very well also it seems.

I think I will target this first.  It is very integral to the login experience now.  Thank you for the pointer.

REQUEST:  This may require a change to an existing system file to affect a solution however... (/etc/gdm/Init/Default in particular) since there is absolutely NO provision yet for dynamic manipulation of XSplash within GDM otherwise.  Does anyone have any feelings / suggestions on this?

---

### Post by Psumi on 2010-01-25
> **growlf said:**
> REQUEST:  This may require a change to an existing system file to affect a solution however... (/etc/gdm/Init/Default in particular) since there is absolutely NO provision yet for dynamic manipulation of XSplash within GDM otherwise.  Does anyone have any feelings / suggestions on this?

do what you should do:

xmessage a warning saying "You must run this as root user." Or Invoke gksu automatically when opening the application.

Synaptic shortcut in the debian/gnome menu says "gksu synaptic" even though running synaptic from terminal runs it without root privledges (which I believe shouldn't be happening to be honest.)

---

### Post by nilarimogard on 2010-01-26
> **growlf said:**
> Oh.  Wow.  I see what you mean.  I have just spidered a few hundred posts and what amounts to heresay documentation on it and... It is Absolutely a must with GDM2!!  It would seem an obvious omission if not in fact.  I had not understood that was where the throbber came from.    This fits with the theme portion very well also it seems.

I think I will target this first.  It is very integral to the login experience now.  Thank you for the pointer.

REQUEST:  This may require a change to an existing system file to affect a solution however... (/etc/gdm/Init/Default in particular) since there is absolutely NO provision yet for dynamic manipulation of XSplash within GDM otherwise.  Does anyone have any feelings / suggestions on this?

Great news, can't wait for it :D

---

### Post by towheedm on 2010-01-28
Over the last 3 days or so I've been playing around with the files in /usr/share/images/xsplash and also with the gdm-greeter-login-window.glade file in /usr/share/gdm in order to customize GDM in Karmic.

Was just about to learn Python and PyGTK to write a similar app.  Very glad I came across this post.  Guess I'll Python and PyGTK some other time. ;)

Updating and installing as I type so I'll see how it goes.  Thanks for this. It's like pills for a headache.:D

Will definitely post back.

---

### Post by Psumi on 2010-01-28
> **growlf said:**
> If anyone is willing to test the PPA out and report any issues, here it is - finally :o.  Place the following lines in your /etc/apt/sources.list file:

Or just do this:

sudo add-apt-repository ppa:gdm2setup/gdm2setup

or add ppa:gdm2setup/gdm2setup to the software sources.

Then do the install step: sudo apt-get install python-gdm2setup

By the way, according to package details, it's built for i386 and not _all.

---

### Post by x-shaney-x on 2010-01-30
I just tried this tool but it doesn't change the background for me.
I've tried around a dozen different jpg and png images of different sizes but I still get the default.

The odd thing is, ?usr/share/images/xsplash shows the image I selected.

---

### Post by towheedm on 2010-01-31
I uninstalled GDM2Setup but the login screen does not return to the Ubuntu screen.  How do I get it back?

---

### Post by Psumi on 2010-01-31
> **towheedm said:**
> I uninstalled GDM2Setup but the login screen does not return to the Ubuntu screen.  How do I get it back?

This is because GDM2setup physically edits the configurations of GDM.

---

### Post by growlf on 2010-01-31
To get the original login screen back, you will probably want to re-install GDM2Setup and set the image back through it, and then also the decorations. Then un-install GDM2Setup again if desired.

---

### Post by towheedm on 2010-01-31
Thanks, that works, but my Login Sound does not play anymore although I checked it in GDM2.  How do I get my login sound back?

---

### Post by growlf on 2010-02-03
> **towheedm said:**
> Thanks, that works, but my Login Sound does not play anymore although I checked it in GDM2.  How do I get my login sound back?

run this command and tell us the output?

```
sudo -u gdm gconftool-2 -g /desktop/gnome/sound/event_sounds
``` Also what version of GDM2Setup are your running?

---

### Post by amjad_2020 on 2010-02-03
Thank you ^_^

---

### Post by towheedm on 2010-02-03
> run this command and tell us the output?

     Code:
     sudo -u gdm gconftool-2 -g /desktop/gnome/sound/event_sounds 
 Also what version of GDM2Setup are your running?
My mistake, I never did get my login sound to work.  I have two soundcards: a PCI SB Live! and a built-in Soundmax.  My SB was set as my default sound card.  The login sound was being played through the built-in Soundmax card.  I was able to hear the login sound after switching the speakers over to the Soundmax card.

My question now is this:  What string value should I specify in the /desktop/gnome/sound/sound_mixer_device key to get the login sound to play through my SB Live! card?  Should I use the 'Card x', the driver module name, the HW x:y, or something else?

Thanks again.

BTW, these are the values under the /desktop/gnome/sound key:

```
towheed@ga1a4ch:~$ sudo -u gdm gconftool-2 -R /desktop/gnome/sound
[sudo] password for towheed: 
 enable_esd = true
 event_sounds = true
 theme_name = ubuntu
 default_mixer_device = 
 default_mixer_tracks = []
 input_feedback_sounds = false
```

---

### Post by confused.brit on 2010-02-07
I have just tried to use this tool in Linux Mint Helena (which is Karmic based) and it works wonderfully.

Especially as the Mint Devs had a seriously eye-bleeding custom theme applied, your tool is just the tonic :)

Thanks, and keep up the good work!

---

### Post by growlf on 2010-02-10
> **towheedm said:**
> 
My question now is this:  What string value should I specify in the /T key to get the login sound to play through my SB Live! card?  Should I use the 'Card x', the driver module name, the HW x:y, or something else?


Hmm. I am sorry, I really have no idea.  Have you tried looking in the forums for existing answers to that one?  I just did a quick search and found this: [http://ubuntuforums.org/showthread.php?t=789578&highlight=soundblaster+live]("http://ubuntuforums.org/showthread.php?t=789578&highlight=soundblaster+live")  - not sure if that helps specifically, but it has quite a bit of info on the subject.

@[everyone] - on behalf of Exosyst and myself - you are welcome, and thank you for the feedback.

---

### Post by MES5464 on 2010-02-24
I installed GDM2 on my Karmic 64 laptop and none of the changes I make take effect. Could it be because I am using 64 bit? I don't see why that would matter since Python is installed.

---

### Post by El Zoido on 2010-02-26
Same thing for me, Karmic 64bit, no change takes place

---

### Post by MetalMusicAddict on 2010-02-28
Sorry if it's been asked, but is anyone using this on Lucid?

It works fine except changing of the background.

---

### Post by flyver on 2010-03-01
I have done this (as exosyst suggested):

Code:
sudo add-apt-repository ppa:gdm2setup/gdm2setup
update your packages
Code:
sudo apt-get update
install it!
Code:
sudo apt-get install python-gdm2setup

But then on exosyst's next post he/she shows us a screenshot but my GDM configuration tool looks nothing like that! (And it doesn't work.)

My ultimate goal is to install [this GDM]("http://gnome-look.org/content/show.php/Dust+Karmic+GDM+by+mickyz?content=107613") in Linux Mint Helena, but I'm having all sorts of issues.

Any help would be appreciated.

---

### Post by growlf on 2010-03-01
> **flyver said:**
> But then on exosyst's next post he/she shows us a screenshot but my GDM configuration tool looks nothing like that! (And it doesn't work.)

The app *has* changed quite a bit since those screenshots, yes :).    We are looking for a place to put a blog/screen-shot/forum presence for this app.  Once we have it selected and implemented, we will post it here.

> **flyver said:**
>  My ultimate goal is to install [this GDM]("http://gnome-look.org/content/show.php/Dust+Karmic+GDM+by+mickyz?content=107613") in Linux Mint Helena, but I'm having all sorts of issues.

Any help would be appreciated.
The GDM Theme you linked is for the older GDM - not the one that is included with Karmic or Lucid.  It will not work with the installed GDM manager of the newer Linux distrobutions.  If you REALLY want to install this theme you will have to downgrade your installed GDM manager - not recommended.  

GDM2Setup is a tool that bridges the gap created by the newer GDM and it's currently somewhat skeletal interface.  GDM2Setup does not (YET) perform compatibility conversion of older GDM Themes.  It ***is*** a planned feature however.

As to the 64 bit issues noted above - I do not have an available 64 bit system to test with and am a bit hogtied here.  Please give me as much info as you can from gconf of the settings before and after running GDM2Setup.  Also list any other related info - such as kernel version, python version and GDM2Setup version.  Finally - please use the Launchpad bug tracker - it helps make sure that we have all of this information and allows the people that are actually working on it, to all see the bugs as they are reported.  The Launchpad project can be found here: [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

That said - we are trying to look into these issues as rapidly as possible.

---

### Post by growlf on 2010-03-01
> **MetalMusicAddict said:**
> Sorry if it's been asked, but is anyone using this on Lucid?

It works fine except changing of the background.

To the best of my knowledge - yes it does.  Please let us know if you have any issues with it however.

[UPDATE]
A bug fix release was just put up on Launchpad - there was indeed an error that stopped the file from actually being copied into the XSplash directory.  My fault for being overly cautious in touching the /etc  :|  That is now resolved - and I suspect that this answers all of the 64 bit issues as well since it was not really related to it being 64 bit I dont think.

Also - yes, it appears to work well in Lucid.  The fine folx at OMG!Ubuntu have a side by side comparison of Lucid's current tool and ours on the screen here: [http://www.omgubuntu.co.uk/2010/02/change-gdm-login-screen-background-in.html](http://www.omgubuntu.co.uk/2010/02/change-gdm-login-screen-background-in.html)

The version is correctly reported now as well.

---

### Post by exosyst on 2010-03-02
I've been wondering about the themes situation guys. 

Do you think we could extract the relevant background image from the theme and then 'dynamically' generate a new Glade UI file from the other theme files?

I might have a look at this. It might be possible to go at least part way between bridging the two different theming styles (OK, it won't be an exact match as I don't know if we can do RGBA on the login screen for transparency but we might be able to approximate it).

I'll try and figure something out. In other news - thanks for being awesome everyone testing/using and contributing!

---

### Post by growlf on 2010-03-02
> **exosyst said:**
> Do you think we could extract the relevant background image from the themeYes.  That, I know we can do.  Already played with that part a little in fact.  The original themes are just a tar-gzip of needed files (images etc) and an XML doc that describes them and some settings. Several common and easy to use libraries are available in python for both functionalities needed. Not sure how to do the automatic file association/installation part like the old system had tho...

Just having GDM2Setup pull in the old wallpaper would be a great start I think.  Auto install old theme wallpaper on double click - also a great thing.

One question on that tho - what do we do for themes that we import partially in one version of GDM2Setup, after we add more functionality later?  Re-import them again manually?

> **exosyst said:**
> and then 'dynamically' generate a new Glade UI file from the other theme files? Now that part, is a tall order I suspect, and I am looking very forward to what you find out.  Be aware, however, as a few people have posted in the Answers area and elsewhere - the glade file for the login is not a current version (2.2 I think, not 2.6 - required for most "cool" features like transparency) - and upgrading it did not work for me or the other who posted to LP Answers.

I would like to echo Exosyst's **thanks to everyone** for testing and feedback - further, I would also like to thank everyone who is helping to spread the word by posting to other forums and web sites etc.  If we can get this "noticed" enough, maybe it will be there by **default in Lucid**.  Any help in that direction would be greatly appreciated.  A new version (v0.5.0) was just posted to LP that adds compatibility to the PPA for Lucid for this reason.

---

### Post by FatAngus on 2010-03-04
Thanks for this - works great :D

---

### Post by kiwited on 2010-03-07
I am trialling Lucid on my 64 bit machine. I installed GDM2 in order to change the login screen. It seems to start OK but the image I select does not seem to "stick". After clicking on Wallpaper the selection window comes up. I select a wallpaper and click OK. The initial window comes back, but still has the original image.

An earlier post mentioned that /usr/share/xsplash changed. This is also the case for me, the xsplash image changes but not on the login window or the GDM2 window.

I have also reinstalled GDM2 twice.

Any ideas?

Theo

---

### Post by Method X on 2010-03-07
Hi there!
Just want to say thanks for this program. Installed it today to customise annoying splash screen and made nice look on my system. :)

---

### Post by growlf on 2010-03-08
> **kiwited said:**
> An earlier post mentioned that /usr/share/xsplash changed. This is also the case for me, the xsplash image changes but not on the login window or the GDM2 window

Hmm.  this is very odd.  The XSplash image ***is*** the login window background, or *should* be...

Please post the version of the installed GDM2Setup and the appropriate settings from gconf. You can use the following command to retrieve the settings: ```
sudo -u gdm gconftool-2 -a "/desktop/gnome/background"
``` You should see something linke this:```
 picture_opacity = 100
 draw_background = true
 primary_color = #b06840
 color_shading_type = solid
 picture_options = zoom
 secondary_color = #b06840
 picture_filename = /usr/share/images/xsplash/bg_2560x1600.jpg
```Then make sure that the image at "/usr/share/images/xsplash/bg_2560x1600.jpg" (or what ever resolution your system has selected) is the correct one as well - use your file browser and look at it's thumbnail at least, or actually open it up and look at it in a viewer.

Let me know what you find.

[UPDATE]
Wild thought - also post an 'ls -la' of the '/usr/share/images/xsplash/' directory and contents?

---

### Post by kiwited on 2010-03-09
Thanks for your help.

My current login screen is the purple warty background. I used the tool to change the background to "mistymorning". The image on the Select Login Wallpaper changes as required. I click OK. That window closes and I am back at Configure Login Settings window and the image displayed is still Warty.

I open the file manager and go to /usr/share/images/xsplash and there are a number of thumbnail images of MistyMorning.

I log out and the login screen is still warty. I reboot the computer and the image is still warty but the xsplash directory shows thumbnails of MistyMorning.

I then run the codes you gave me.

theo@ubuntu-8:/usr/share/images/xsplash$ sudo -u gdm gconftool-2 -a "/desktop/gnome/background"
[sudo] password for theo: 
 picture_opacity = 100
 draw_background = true
 primary_color = #2c001e
 color_shading_type = solid
 picture_options = zoom
 picture_filename = /usr/share/backgrounds/warty-final-ubuntu.png
 secondary_color = #2c001e

and

theo@ubuntu-8:/usr/share/images/xsplash$ ls -la
total 512
drwxr-xr-x 2 root root   4096 2010-03-10 11:32 .
drwxr-xr-x 5 root root   4096 2009-10-30 17:32 ..
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1024x768.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1280x1024.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1280x800.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1440x900.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1680x1050.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_1920x1200.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_2560x1600.jpg -> /usr/share/images/xsplash/bg.jpg
lrwxrwxrwx 1 root root     32 2010-03-10 11:32 bg_800x600.jpg -> /usr/share/images/xsplash/bg.jpg
-rw-r--r-- 1 root root 178323 2010-03-10 11:32 bg.jpg
-rw-r--r-- 1 root root   9630 2009-10-30 04:52 logo_large.png
-rw-r--r-- 1 root root   7279 2009-10-30 04:52 logo_medium.png
-rw-r--r-- 1 root root   5231 2009-10-30 04:52 logo_small.png
-rw-r--r-- 1 root root  18016 2009-10-30 04:52 logo_xtra_large.png
-rw-r--r-- 1 root root  48270 2009-10-30 04:52 throbber_large.png
-rw-r--r-- 1 root root  48270 2009-10-30 04:52 throbber_medium.png
-rw-r--r-- 1 root root  35707 2009-10-30 04:52 throbber_small.png
-rw-r--r-- 1 root root 141038 2009-10-30 04:52 throbber_xtra_large.png

My screen resolution is set to 1680x1050

Theo

---

### Post by growlf on 2010-03-10
> **kiwited said:**
> Thanks for your help.
You bet!  Thank you - for patiently assisting us in tracking down the problem.
 > **kiwited said:**
> picture_filename = /usr/share/backgrounds/warty-final-ubuntu.png
 ...and this seems to be it.  Something changed the default property for the image setting (picture_filename) to the warty image.  It should be like the generic value I posted above in the earlier post.  Are you using (or have you used) any other login wallpaper choosers or XSplash configuration tools?  There are a few other users that have reported similar issues - and this may be why.  Please report back on this?

I am going to make a bug report over this issue - now that we know more about it - and see if we cant make this issue go away permanently.  In the meantime, try issuing the following command and see if all does not start going as expected:
```
sudo -u gdm gconftool-2 -t string -s /desktop/gnome/background/picture_filename /usr/share/images/xsplash/bg_1680x1050.jpg

```

[UPDATE]
Bug filed at [https://bugs.launchpad.net/gdm2setup/+bug/536712](https://bugs.launchpad.net/gdm2setup/+bug/536712)

---

### Post by kiwited on 2010-03-10
I ran the command. The first time the machine froze and required rebooting, the second time it dropped back to the login screen which was unchanged.

I then ran the GDM2 tool again but with the same result as before.

I logged out and the original login screen was still there.

I don't know if the following points are relevant.

My install of 10.04 is not a fresh install. It is an upgrade of 9.10, which in turn was an upgrade of earlier issues of Ubuntu. It is possible that something may exist from the past but a look through the applications list does not reveal anything.

My computer has an AMD64 X2 6400+ processor and an ATI Radeon 4350 video card. It functioned OK under 8.1 but under both 9.04 and 9.10 the display was poor, with windows failing to open and close as expected. There may have been a relationship to Firefox. It was for this reason I did not upgrade from 8.04 LTS for my day to day work.

In the current install of 10.04 the ATI driver does not work. I understand this is possibly close to a solution.

The login screen issue is not a biggie but may indicate some other problem.

Again, thanks for your time.

Theo

---

### Post by growlf on 2010-03-10
> **kiwited said:**
> I ran the command. The first time the machine froze and required rebooting, the second time it dropped back to the login screen which was unchanged. Well that is very starnge indeed.  The command I gave above if typed correctly, should not freeze the machine or do anything hinky at all.  This definitely indicates a deeper issue underlying the login screen not changing.

I am not ready to give up on this just yet though.  I wonder if you could check to see if (immediately after issuing the command I gave in the earlier post to set the value) you then run the command to check the value and see if it was indeed changed.  Or is it completely impossible to run 'gconftool-2' as the user 'gdm'?

Maybe we should also see if you can even run a basic command as 'gdm' and see if that freezes the system all by itself?  i.e. like: 'sudo -u gdm ls'

[UPDATE]
I updated the bug ticket ([https://bugs.launchpad.net/gdm2setup/+bug/536712](https://bugs.launchpad.net/gdm2setup/+bug/536712)) as well.

---

### Post by growlf on 2010-03-17
Version 0.5.2 is out for both Karmic and Lucid.  It fixes the "lost wallpaper" issue and is more compatible/stable with random or manual changes to gconf (or unexpected defaults  from the newer Lucid setup).  Use, test and enjoy - those using the PPA will already be using the newer version.

We are still trying to get this into Lucid - but we need compelling reasons as to why it should be allowed in after the feature freeze - suggestions of reasons are welcome, and desired.

---

### Post by metchebe on 2010-03-22
Hello.

May I suggest the following options be added to this tool?

[LIST]
[*]Font
[*]Hinting
[*]Compositing
[/LIST]

I currently modify them on my computer via a script:
```
# -- Options --
HINTING=full
FONT="Droid Sans 10"
COMPOSITING=true

sudo -u gdm gconftool-2 --set --type=string /desktop/gnome/font_rendering/hinting $HINTING
echo "Hinting set to $HINTING"
sudo -u gdm gconftool-2 --set --type=string /desktop/gnome/interface/font_name "$FONT"
echo "Font set to $FONT"
sudo -u gdm gconftool-2 --set --type=boolean /apps/metacity/general/compositing_manager $COMPOSITING
echo "Compositing set to $COMPOSITING"
```

Regards,
Marco

---

### Post by growlf on 2010-03-24
> **metchebe said:**
> Hello.

May I suggest the following options be added to this tool?

[LIST]
[*]Font
[*]Hinting
[*]Compositing
[/LIST]

Excellent!  Yes, I will add this into the blueprints and the worklist for our next roll-out.  Thank you for your suggestion.

---

### Post by anoknusa on 2010-05-03
> **kiwited said:**
> 
My install of 10.04 is not a fresh install. It is an upgrade of 9.10, which in turn was an upgrade of earlier issues of Ubuntu. It is possible that something may exist from the past but a look through the applications list does not reveal anything.


Indeed, that may be.  I'd been running Lucid since the first beta run, but decided to do a clean install upon the final release; lo and behold, */usr/share/images/xsplash* nole longer exists.  I'm also having a problem with the background not changing--the app won't even open an image--and I can't seem to find the folder containing this info. Any idea where the GDM2 config files are kept? Maybe I could manually change the file link.  Worst-case scenario, one could maybe make a backup copy of the "warty-final-ubuntu" image and replace it with another, renaming that image to "warty-final-ubuntu.png."  That's how I changed the login background and bootsplash image/throbber in Karmic. :-k

---

### Post by tsaowang on 2010-05-06
Hi,

Thanks a lot for this app it works, great.

I have a question though, where are the themes located ? Neither can I change gtk login theme nor icons. I can only select the default ones in the app. How can I add a gtk theme as well as a new icon theme ?

Thanks a lot for your quick reply.

---

### Post by KlavKalashj on 2010-05-19
> **growlf said:**
> Excellent!  Yes, I will add this into the blueprints and the worklist for our next roll-out.  Thank you for your suggestion.

Woot? Is it possible to have compositing, eg. shadows in the login window? Now  this sounds sweet, that's something i've been missing a long time!

---

### Post by towheedm on 2010-05-22
> **KlavKalashj said:**
> Woot? Is it possible to have compositing, eg. shadows in the login window? Now  this sounds sweet, that's something i've been missing a long time!

Not meaning to hijack this thread, but if you wanna add compositing to the login screen, then check out the link at the beginning of this thread:
[http://ubuntuforums.org/showthread.php?p=9068333#post9068333](http://ubuntuforums.org/showthread.php?p=9068333#post9068333)

---

### Post by hellblazer on 2010-07-08
thanks exosyt!!!

:D

---

### Post by WallaceS on 2010-07-12
Is any one else having trouble changing the background? I'm running Lucid on a couple of Dell machines - no problems on the laptop, but on the desktop I can select a new background image but when I click OK nothing happens. Nothing also happens if I press cancel - have to use the close X to get back to the initial gdm2setup screen.

---

### Post by Roasted on 2010-07-12
> **WallaceS said:**
> Is any one else having trouble changing the background? I'm running Lucid on a couple of Dell machines - no problems on the laptop, but on the desktop I can select a new background image but when I click OK nothing happens. Nothing also happens if I press cancel - have to use the close X to get back to the initial gdm2setup screen.

I am having the EXACT same issue. It enrages me that customizability was taken away from us with the newer GDM, not to mention the tool listed as the fix isn't even working. Sigh...

---

### Post by travisf on 2010-07-22
If you are having problems changing the background image check to make sure the "/usr/share/images/xsplash" directory actually exists. It did not in my installation and I had to manually create it. Until the directory exists background changes will not stick.

If using Gnome you can also play with GDM themes by using this command

"gksudo -u gdm dbus-launch gnome-appearance-properties"

It works for me but your mileage may vary.

---

### Post by hariks0 on 2010-07-23
BeforeI installed GDM2, there had been the user list in the login screen when I enabled autologin in 10 seconds. Now it is not there. I have to choose between Autologin or User list. Both are not available at the same time. What is the point in allowing 10 seconds for autologin if there is no user list?

Is there any setting I can change to get it back?

---

### Post by Izobalax on 2010-08-02
Is there a way for me to change the font used in the GDM2 login screen? I have GDM2Setup but there appears to be no font selection option. 

/izo\

---

### Post by towheedm on 2010-08-03
Check the link in post #102.

---

### Post by stevestark on 2010-08-05
i am using ubuntu 10.4 lts. I followed the instructions at the first post and installed python-gdm2setup. the program would not load up. can someone help please. imagemagick is installed

gdm2setup
Traceback (most recent call last):
  File "/usr/bin/gdm2setup", line 43, in <module>
    from gdm2.gdm2setup import GDM2Setup
  File "/usr/lib/pymodules/python2.6/gdm2/gdm2setup.py", line 30, in <module>
    from gdm2.gdm2gconf import GDM2Theme
  File "/usr/lib/pymodules/python2.6/gdm2/gdm2gconf.py", line 36, in <module>
    import ImageFilter, Image
ImportError: No module named ImageFilter

---

### Post by hariks0 on 2010-08-05
> **hariks0 said:**
> BeforeI installed GDM2, there had been the user list in the login screen when I enabled autologin in 10 seconds. Now it is not there. I have to choose between Autologin or User list. Both are not available at the same time. What is the point in allowing 10 seconds for autologin if there is no user list?

Is there any setting I can change to get it back?

Now it is solved. Just enabled Display user list in Ubuntu Tweak or Ailurus. :popcorn:

---

### Post by Nizarus on 2010-08-25
can some one give me default themes (gtk and icons) for lucid. thx.

---

### Post by deusdiabolus on 2010-09-09
I didn't see this covered in this thread, and I did a couple of searches with different keywords and couldn't find it, soooo...

Is there a way to configure GDM2 to show the current desktop wallpaper as the bootsplash background, the way it could be configured under Karmic?  That's all I want to do, is have whatever the last wallpaper was be the login background for Lucid.

Apologies in advance if I missed the explanation for this somewhere.

---

### Post by XiaolinDraconis on 2010-12-23
anyone having trouble with changing the login wallpaper make sure you have imagemagick (sudo apt-get install imagemagick) or install it from software center. plus verify that you have a folder /usr/share/images/xsplash if that folder does not exist then open terminal and type sudo nautilus and create the folder yourself

---

### Post by moseba on 2011-01-13
please can u help me
i have a problem in doing this
```
W: GPG error: http://ppa.launchpad.net maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 55708F1EE06803C5
W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/source/Sources.gz  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/maverick/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by pEW420 on 2011-01-26
^^
I have the same problem.. Seems like the Maverick-folder on the PPA-server is missing.. [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/) ??

I need help please =)

---

### Post by Inygknok on 2011-03-28
I'm wondering the same thing.  Can't get this on Maverick and I'd really love some information regarding the situation  :/

---

### Post by growlf on 2011-04-20
Looks like I am the only one from the team who is active any more - and I have been extremely distracted for several months now.  I will look at getting the current distros built for GDM2Setup as soon as I have a few moments to rub together.  Sorry about the delay folx.

---

