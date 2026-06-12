---
title: "Changing window list (and other) color in gnome-panel"
date: 2006-11-05
forum: Desktop Environments
---

### Post by towsonu2003 on 2006-11-05
I changed the background image of my gnome panel to a gradient of blue. It looks nice to me, but the "buttons" of the window list (see marked button in screenshot attached) doesn't change... 

When a window is active, it has a dark grey color. I would like to make that a darker blue color. When I hover the mouse over a button of a window, its color changes from [none] to a light grey. I wanna change that to a light blue color. 

The problem also exist with the clock (on the left of the panel). when you hover it's light grey, when you click on it, it is dark grey... 

How do I change these things' colors? For now, I cannot use my panel background color bc it just looks ugly...  

I'd appreciate any help very much :)

PS. I tried putting a .gtkrc-2.0 file in my home folder and restarting gnome-panel but that didn't work (probably bc I didn't know what I was doing)

PSS. I also attached my panel background image in case someone likes it.

---

### Post by Camden on 2006-11-28
Yep, I got the same problem and haven't had any luck.

---

### Post by bluevoodoo1 on 2006-12-19
I have wondered how to do this as well.

---

### Post by featherking on 2007-01-20
Dont know if any of you figured it out yet, but i stumbled on a program that works perfectly, it lets you configure basically every color you can think of in gnome, even the panel stuff!

I tried to make a deb file for it, it is attached to this post, if it doesnt work you can find the source [[COLOR="Red"]here[/COLOR]]("http://www.gnome-look.org/content/show.php?content=47349")

Good Luck!

EDIT: This deb is updated to fetch the dependencies as it installs

EDIT: Changed deb requirements to match source requirements (Package tested in edgy, doesnt work in dapper without updating many dependencies :( )

---

### Post by SqdnGuns on 2007-01-20
> **featherking said:**
> Dont know if any of you figured it out yet, but i stumbled on a program that works perfectly, it lets you configure basically every color you can think of in gnome, even the panel stuff!

I tried to make a deb file for it, it is attached to this post, if it doesnt work you can find the source [[COLOR="Red"]here[/COLOR]]("http://www.gnome-look.org/content/show.php?content=47349")

Good Luck!

This needs to be installed to work with your package:

libglademm-2.4-1c2a
C++ wrappers for libglade2 (shared library)

Thanks for the package..............working for me now.

---

### Post by featherking on 2007-01-20
Ive updated the deb file to check for dependencies just for anyone who uses it in the future. Glad you got it working.

Finally a completely customized gnome desktop..!

---

### Post by towsonu2003 on 2007-01-20
do you know the backend it uses (where does it make the changes so you see color changes, somewhere in gconf?)? thanks :)

---

### Post by sloggerkhan on 2007-01-20
Hi, I have a black theme with white text, but in firefox I often get white text on white background. Is there A way I could fix this using this app? I've tried using specific colors for firefox, but the overlap a lot of images for some weird dreason.

---

### Post by Lord Illidan on 2007-01-20
> **towsonu2003 said:**
> do you know the backend it uses (where does it make the changes so you see color changes, somewhere in gconf?)? thanks :)
No, I believe it uses the .gtkrc-2.0 file in your home directory.

---

### Post by featherking on 2007-01-20
It uses .gtkrc-2.0 and then it points to a file called .gtk-2.0-gnome-color-chooser, all the values you set in it are saved in that file

@sloggerkahn
Sorry not sure about using it in firefox, i was mainly using it for the panel colors...

---

### Post by sloggerkhan on 2007-01-26
I've used it to help with the firefox problem. It was just a matter of figuring out what colors controlled what.

---

### Post by tweedledee on 2007-01-27
> **featherking said:**
> Ive updated the deb file to check for dependencies just for anyone who uses it in the future. Glad you got it working.

Finally a completely customized gnome desktop..!

I installed this briefly to take a look and decided it was easier to keep playing with my themes via text editors (since I've mostly figured out how those work and this was a complete mystery at first glance).  When I uninstalled, it tried to remove /usr/local/bin, /usr/local/share, and /usr/local.  You might want to modify your .deb to leave those folders alone, as they are supposed to be there (it failed, as I had other things them in, but still...).

---

### Post by ardchoille42 on 2007-01-27
> **featherking said:**
> Ive updated the deb file to check for dependencies just for anyone who uses it in the future. Glad you got it working.

Finally a completely customized gnome desktop..!

Not quite. Your .deb requires libcairomm-1.0.so.1 on a default Dapper install.. which the source doesn't even require for compilation. Your .deb installs on Dapper without problems, but it won't run on Dapper due to missing deps. See below:

```

[initial @ 16:41:39] gnome-color-chooser
gnome-color-chooser: error while loading shared libraries: libcairomm-1.0.so.1: cannot open shared object file: No such file or directory

```

There is no package with "libcairomm" in the name in the repos for Dapper. Is there any way you can fix your package so I can use it?

---

### Post by featherking on 2007-01-28
@ardchoille42

I edited my original post and added that libcairomm package.

@tweedledee

not sure how to configure the package to leave those directories alone, i have uninstalled/reinstalled as well and have not had any problems. Dpkg will never remove a folder when something else other than its contents is in it so i would think you would be okay (as long as you dont use the force option)

---

### Post by ardchoille42 on 2007-01-28
> **featherking said:**
> @ardchoille42

I edited my original post and added that libcairomm package.



I don't understand why you added libcairomm. AFAIK, the proper method of packaging is to take pristine sources and build and package from that. If you added or removed anything to/from the pristine sources, then it can possibly break something. It is also no longer the original app, you changed it.. it's now a fork. The sources for gnome-color-chooser don't require libcairomm but you have added it. If the app works from the original sources, why did you add something to it? I'm just trying to understand why you broke packaging policy and I don't mean to anger anyone or hurt anyone's feeling. Can you repackage the app from the original sources so I can run the app from your .deb? Could it be that the way you have broken from packaging policy is the reason myself and tweedledee are having problems with your package?

---

### Post by featherking on 2007-01-28
Short Version: Do it yourself then

Long Version: I havent written this program or anything, i stumbled upon it and it worked on my machine, i compiled the source into a binary, made a package and uploaded it so not everyone would have to go through compiling sources. I am not a package expert, however doing it this way for me makes it much easier to uninstall later on as you have a package to remove. I havent changed anything from the original sources so i dont know what you are talking about. Obviously the sources do require the libcairomm package if you are not able to run it because **i did not change anything, i have only compiled the program.** I am done trying to help with this when obviously it is easy for you to criticize without actually understanding what is going on.

---

### Post by ardchoille42 on 2007-01-28
> **featherking said:**
> I havent changed anything from the original sources so i dont know what you are talking about.

Well, to install your .deb libcairomm is required. Compling from the original sources does not require libcairomm. You stated earlier that you added the libcairomm as a dep. Why did you add libcairomm as a dep when the original sources do not require libcairomm as a dep. You indeed did change something because your .deb will install but it won't run due to missing deps.

As I said before, I am not criticising, I am only trying to understand why your .deb **will** install (since I do not have libcairomm) but it **won't** run because I don't have libcairomm.. and why you added libcairomm as a dep when the original sources don't require it.

If you don't want to work and help your users with your packages, why do you offer them to the public?

---

### Post by featherking on 2007-01-28
libcairomm is not a dependancy and it is not a dependancy of the program or package, no one else has mentioned this problem so obviously it is specific to your machine. I uploaded it for you as a quick fix **to YOUR issue**. Perhaps you should look at your machine specifically or try compiling the source for yourself, as those debs dont work for **you**. Your conspiracy theories about me **altering the program** and **breaking packaging policy** are completely unfounded.

As for supporting users, i am more than willing but you are making these wild accusations. Go ahead and remove my package and compile the source for gnome-color-chooser and see if that works for you. I dont know why **your** machine requires it, perhaps contact the developer on that one

---

### Post by ardchoille42 on 2007-01-28
> **featherking said:**
> libcairomm is not a dependancy and it is not a dependancy of the program or package, no one else has mentioned this problem so obviously it is specific to your machine. I uploaded it for you as a quick fix **to YOUR issue**. Perhaps you should look at your machine specifically or try compiling the source for yourself, as those debs dont work for **you**. Your conspiracy theories about me **altering the program** and **breaking packaging policy** are completely unfounded.

As for supporting users, i am more than willing but you are making these wild accusations. Go ahead and remove my package and compile the source for gnome-color-chooser and see if that works for you. I dont know why **your** machine requires it, perhaps contact the developer on that one

I installed your .deb of gnome-color-choose a few days ago. When I ran gnome-color-chooser I got this:

```

[initial @ 16:41:39] gnome-color-chooser
gnome-color-chooser: error while loading shared libraries: libcairomm-1.0.so.1: cannot open shared object file: No such file or directory

```

So, libcairomm is definitely a dependency of either the app itself, or your package. When I compile the app from its original sources, I don't get a libcairomm dep problem, so that leads me to believe the dep problem is with your package or the way you compiled the app.

When trying to install your libcairomm .deb, I get this:

```

[downloads @ 17:47:08] ls
gnome-color-chooser_0.1.3_i386.deb  libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb
[downloads @ 17:47:11] sudo dpkg -i libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb
Password:
Selecting previously deselected package libcairomm-1.0-1.
(Reading database ... 84808 files and directories currently installed.)
Unpacking libcairomm-1.0-1 (from libcairomm-1.0-1_1.2.0-0ubuntu1_i386.deb) ...
dpkg: dependency problems prevent configuration of libcairomm-1.0-1:
 libcairomm-1.0-1 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.2.
 libcairomm-1.0-1 depends on libcairo2 (>= 1.2.2); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 libcairomm-1.0-1 depends on libgcc1 (>= 1:4.1.1-11ubuntu1); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 libcairomm-1.0-1 depends on libstdc++6 (>= 4.1.1-11ubuntu1); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
dpkg: error processing libcairomm-1.0-1 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libcairomm-1.0-1
[downloads @ 17:47:32]

```

What am I doing wrong here?

---

### Post by towsonu2003 on 2007-01-28
chill out :KS  and have a look at the code of conduct before this evolves into a flame war: [http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)

in the meantime, if anyone has any pointers on how to change some text files to tweak various colors of gnome-panel, I'm still looking for one :)

---

### Post by ardchoille42 on 2007-01-28
> **towsonu2003 said:**
> .. if anyone has any pointers on how to change some text files to tweak various colors of gnome-panel, I'm still looking for one :)

I'd like very much to learn how to do this too :)

Is it possible that someone can properly package gnome-color-chooser for Ubuntu and get it into the repos?

---

### Post by towsonu2003 on 2007-01-28
> **ardchoille42 said:**
> 
Is it possible that someone can properly package gnome-color-chooser for Ubuntu ... ?

I'll bite and hijack my own post... I think this was a little disrespectful to the user who packaged and attached a deb file for us just to help. 

as per
> Is it possible that someone can ... get it into the repos?
have a look at [https://wiki.ubuntu.com/MOTU/Packages/New](https://wiki.ubuntu.com/MOTU/Packages/New) , which describes how to request packages for *newer releases* of Ubuntu. 

but I think, for the version you are using now, you are pretty much on your own (afaik they don't upload new packages to the repos)...

---

### Post by DarkN00b on 2007-01-28
> **towsonu2003 said:**
> chill out :KS  and have a look at the code of conduct before this evolves into a flame war: [http://www.ubuntu.com/community/conduct](http://www.ubuntu.com/community/conduct)

in the meantime, if anyone has any pointers on how to change some text files to tweak various colors of gnome-panel, I'm still looking for one :)

Try this:

Create a plain text file in your home directory and name it .gtkrc-2.0

Open the new file in gedit and paste the following text into it:

```

include "~/.gnome2/panel-fontrc" style "desktop-icon"

{
NautilusIconContainer::frame_text = 0
text[NORMAL] = "#000000"
NautilusIconContainer::normal_alpha = 5
}
class "GtkWidget" style "desktop-icon"

#NautilusIconContainer::dark_info_color="#888888" #These 3 lines control what your system-wide icon text looks like. Uncomment the line you want to edit and edit the hex numbers after the pound sign.
#NautilusIconContainer::light_info_color="#bbbbbb"
#NautilusIconContainer::highlight_alpha=200

style "panel"
{

fg[NORMAL] = "#FFFFFF" #This value changes the color of your panel text for all except the focused window.
# fg[PRELIGHT] = "#000000&#8243;
# fg[ACTIVE] = "#000000"
# fg[SELECTED] = "#000000&#8243;
# fg[INSENSITIVE] = "#8A857C"
# bg[NORMAL] = "#000000&#8243;
bg[PRELIGHT] = "#FFFFFF" #This changes the color of window buttons on the panel when you hover you mouse pointer above it.
# bg[ACTIVE] = "#D0D0D0&#8243;
# bg[SELECTED] = "#D8BB75&#8243;
# bg[INSENSITIVE] = "#EFEFEF"
# base[NORMAL] = "#ffffff"
# base[PRELIGHT] = "#EFEFEF"
# base[ACTIVE] = "#D0D0D0&#8243;
# base[SELECTED] = "#DAB566&#8243;
# base[INSENSITIVE] = "#E8E8E8&#8243;
# text[NORMAL] = "#161616&#8243;
# text[PRELIGHT] = "#FFFFFF&#8243;
# text[ACTIVE] = "#000000&#8243;
# text[SELECTED] = "#ffffff"
# text[INSENSITIVE] = "#8A857C"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"

```

Then do this:

```
sudo aptitude install gcolor2
```

Use gcolor2 as a color picker to choose your colors.

Uncomment any line in the .gtkrc-2.0 file you want to change and edit the hex value to whatever you want.

EDIT: You need to log out and back in for the changes to take effect.

---

### Post by featherking on 2007-01-29
@ardchoille42
the reason you get those errors trying to install libcairomm is because ubuntu doesnt upgrade the packages in the repositories until each new version of ubuntu. You are in dapper and are using the packages that were frozen in the repositories at that time. So because im on edgy i can just apt-get install all the newer dependencies for libcairomm. To get libcairomm to install on your machine you will have to satisfy all the dependencies listed in your terminal output.
> 
Is it possible that someone can properly package gnome-color-chooser for Ubuntu

It is packaged fine, many people have it working you just have to satisfy the dependencies

I have updated my deb.These are the package requirements i have just found from the developers rpm package, and wierd, it looks like libcairomm is required after all just like i said
```
libatk1.0-0 (>= 1.12.1), libc6 (>= 2.4-1), libcairo2 (>= 1.2.4), libcairomm-1.0-1, libgcc1 (>= 1:4.1.1-12), libglade2-0 (>= 1:2.5.1), libglademm-2.4-1c2a, libglib2.0-0 (>= 2.12.0), libglibmm-2.4-1c2a, libgtk2.0-0 (>= 2.10.3), libgtkmm-2.4-1c2a, libpango1.0-0 (>= 1.14.5), libsigc++-2.0-0c2a (>= 2.0.2), libstdc++6 (>= 4.1.1-12), libxml2 (>= 2.6.26)
```

The developer did not have most of these listed on the main page for his source, thats why my package didnt require them. I have updated the dependencies of the deb, so it should install/work now regardless of what you are running. As long as you can satisfy the **developers** dependencies.

If someone would test that package i would appreciate it. This should run flawless on edgy

---

### Post by orb9220 on 2007-01-29
Just installed deb on my edgy and is working like a champ.
Even has menu entry in System>Prefs

Thanks Featherking!

---

### Post by randiroo76073 on 2007-01-29
Featherking, thanks for deb, I'll try install in Dapper and see what pops for dependancies then work from there :)

---

### Post by featherking on 2007-01-29
@orb9220
      im glad you got it working, this furthers my theory that it runs perfect under edgy.

i think i will take partial blame for the package not working sooner, i only had a few dependencies of the program that i pulled off the developers website, now that ive found a more complete list this package should work on edgy perfectly.

My only concern is about the dependencies for dapper, im not sure of an easy way to resolve them.. Possibly adding the edgy repos temporarily to install? That could be more work than its worth though...

---

### Post by m1215 on 2007-01-29
i installed the .deb in edgy, works good. thanks for the file featherking. now im able to see text on by desktop with the theme i use. also worked for changing the panel and menu color. beats editing the files by hand.

---

### Post by ardchoille42 on 2007-01-29
> **featherking said:**
> @orb9220
      im glad you got it working, this furthers my theory that it runs perfect under edgy.

i think i will take partial blame for the package not working sooner, i only had a few dependencies of the program that i pulled off the developers website, now that ive found a more complete list this package should work on edgy perfectly.

My only concern is about the dependencies for dapper, im not sure of an easy way to resolve them.. Possibly adding the edgy repos temporarily to install? That could be more work than its worth though...

Thank you for trying to get this fixed for me. I figured that if the package installed without problems, then the app should work without problems, which wasn't the case. However, the package won't install at all now:

```

[downloads @ 20:11:30] sudo dpkg -i gnome-color-chooser_0.1.3_i386.deb
Password:
Selecting previously deselected package gnome-color-chooser.
(Reading database ... 85278 files and directories currently installed.)
Unpacking gnome-color-chooser (from gnome-color-chooser_0.1.3_i386.deb) ...
dpkg: dependency problems prevent configuration of gnome-color-chooser:
 gnome-color-chooser depends on libatk1.0-0 (>= 1.12.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 gnome-color-chooser depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.2.
 gnome-color-chooser depends on libcairo2 (>= 1.2.4); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.
 gnome-color-chooser depends on libcairomm-1.0-1; however:
  Package libcairomm-1.0-1 is not installed.
 gnome-color-chooser depends on libgcc1 (>= 1:4.1.1-12); however:
  Version of libgcc1 on system is 1:4.0.3-1ubuntu5.
 gnome-color-chooser depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not installed.
 gnome-color-chooser depends on libglib2.0-0 (>= 2.12.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 gnome-color-chooser depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.
 gnome-color-chooser depends on libpango1.0-0 (>= 1.14.5); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 gnome-color-chooser depends on libstdc++6 (>= 4.1.1-12); however:
  Version of libstdc++6 on system is 4.0.3-1ubuntu5.
 gnome-color-chooser depends on libxml2 (>= 2.6.26); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.
dpkg: error processing gnome-color-chooser (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-color-chooser
[downloads @ 20:11:53]

```

I don't think this app is going to work in Dapper. I will just learn how to manually edit ~/.gtkrc-2.0.

@featherking Thank you for your help and your willingness to try and fix this for Dapper.

---

### Post by DarkN00b on 2007-01-30
Just another satisfied user reporting that this works well in Edgy. :D

---

### Post by featherking on 2007-01-30
@ardchoille42 - sorry but i believe you are correct that this will not work in dapper, it doesnt look like the libraries in the dapper repos are up to date enough

@DarkN00b - that is **very** good to hear! I will say i have learned alot about building deb packages from this experience and i **really** like being able to so easily change my colors in gnome

Massive props to the developer, i just packaged it but [[COLOR="Red"]he[/COLOR]]("http://www.gnome-look.org/content/show.php?content=47349") built it :)

---

### Post by JackTheDipper on 2007-02-06
@Featherking:
Thank you very much for packaging! The current alpha version of gnome-color-chooser 0.2.0 brings a little installation script which makes use of "checkinstall", but is completely untested yet. Would be nice if you and the guys which have had problems with your package can try whether it works.

@all who are missing features:
Please mail your requests and proposals to me ;-)

btw what do you think how the final GUI should look like? Like the kcontrol/Windows way (click on a part of a preview and configure it) or does someone have a better idea?

Thank you very much in advance,
JackTheDipper

---

### Post by featherking on 2007-02-06
@Jack
   My package was built primarily with checkinstall but i edited the .deb control file from scratch. at first checkinstall would not do the dependencies correctly. But for the actual installed files, it worked great building the .deb structure. Once i edited the control file to add all necessary dependencies, it seemed to work flawless for everyone running edgy. 

Props for your program its much better than editing the files by hand.

---

### Post by ardchoille42 on 2007-02-06
> **JackTheDipper said:**
> @Featherking:
Thank you very much for packaging! The current alpha version of gnome-color-chooser 0.2.0 brings a little installation script which makes use of "checkinstall", but is completely untested yet. Would be nice if you and the guys which have had problems with your package can try whether it works.

@all who are missing features:
Please mail your requests and proposals to me ;-)

btw what do you think how the final GUI should look like? Like the kcontrol/Windows way (click on a part of a preview and configure it) or does someone have a better idea?

Thank you very much in advance,
JackTheDipper

I took apart featherking's .deb and opened the glade file in glade2 and I have to say the UI for your app is awesome. This will be one of the first apps I install in Edgy.

---

### Post by wickstopher on 2007-02-07
Hey, I installed the package, but I can't figure out how to access the program!  Any help?  Thanks!

---

### Post by sloggerkhan on 2007-02-07
try typing its name or looking in system menu.

---

### Post by wickstopher on 2007-02-07
Sorry, I should've reposted.  It appeared in the system menu after a reboot!  Works great in edgy!

---

### Post by erkki70 on 2007-02-07
Thanks a lot Featherking!!!
Works like a charm in Edgy :-)
Cheers,

---

### Post by featherking on 2007-02-07
Np, and congrats

---

### Post by JBAlaska on 2007-10-11
Thanks featherking, I had been looking for this little program for some time.

Worked perfectly on Feisty!

---

### Post by LukeCarrier on 2008-02-12
Just in case there's any 64-bit users here like me, you can a version of this that runs without any buggy 32-bit libraries from here. I tried running the 32-bit version with some 32-bit binaries and it didn't work.

Download it from [here]("http://download.tuxfamily.org/upure64/pool/feisty-upure64/main-amd64/gnome-color-chooser_0.2.2-0ubuntu1%7Eupure64_amd64.deb").

---

