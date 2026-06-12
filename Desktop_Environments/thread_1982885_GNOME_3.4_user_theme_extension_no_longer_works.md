---
title: "GNOME 3.4 user theme extension no longer works"
date: 2012-05-19
forum: Desktop Environments
---

### Post by Tornikee on 2012-05-19
I had my Ubuntu 12.04/GNOME 3.4 combination up and perfectly running since the release of 12.04 until recently. It began a some days ago with a status menu change (the 'log out' option has not been visible anymore), and now the 'Theme' section of the GNOME Tweak Tool shows an error icon that says "'Shell user-theme extension incorrectly installed" and the shell theme selection menu is grayed out.

Is this a known issue and how can I solve it?

---

### Post by pfnorris on 2012-05-19
When I  first installed 12.04 I had difficulty getting the user theme extension to install from the extensions web site. It kept saying it was out of date.

After a fair bit of head scratching and experimenting the solution for me was when I discovered that some other extensions were still in my .local/share/gnome-shell/extensions/ directory that were out of date. Removing those allowed things to proceed again and I was able to install and use the user themes extension.

Might be worth checking that location and /usr/share/gnome-shell/extensions and see what you find. Hope it helps.

Phil

---

### Post by Tornikee on 2012-05-19
I entirely removed GNOME Shell via Synaptic, installed it again from the Software Center, but now the shell fails to load at all. I can run apps via Synapse, and some GTK window contents do appear, but the shell does not.

---

### Post by pfnorris on 2012-05-19
Removing and re-installing gnome-shell will not necessarily remove any extensions installed  in your home folder under ./local/share/gnome-shell/extensions. Note the leading dot - this is a hidden directory. I have seen the behavior where  gnome-shell cannot load because of an out of date extension in here. 

I would strongly recommend removing any extensions that you find there and see if that solves your problem

Phil

---

### Post by Tornikee on 2012-05-19
I did check the directory and no extensions were there. Also, after uninstalling GNOME, Synaptic shows that all of the extensions have been removed as well. I guess the problem is more significant than some stray extension.

Thanks for your replies.

---

### Post by Tornikee on 2012-05-19
So anyone familiar with the issue of shell not appearing at all?

---

### Post by Tornikee on 2012-05-19
I got the shell to load, but the issue with extensions not working persists. I checked the usr/share/gnome-shell folder, but there's no 'extensions' folder. Is there another place I could look for them?

---

### Post by Tornikee on 2012-05-20
Or how can I reinstall user theme extension, except from the extensions.gnome.org?

---

### Post by Tornikee on 2012-05-21
Or at least, will formatting and clean Ubuntu install allow me to install the user theme extension correctly?

And maybe the absence of 'extensions' folder in usr/share/gnome-shell folder explains something?

---

### Post by Frogs Hair on 2012-05-21
I have used this PPA for Gnome 3.2 and 3.4 . You may have another problem if the selections in the teak tool are unusable. [http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html](http://www.webupd8.org/2012/03/official-gnome-shell-extensions-weather.html)

---

### Post by Tornikee on 2012-05-21
I'm pretty sure I used that PPA, although installed it again using those commands. The issue persists: 

[IMG]https://lh3.googleusercontent.com/-udgW2GYtW9U/T7qL-MtkvbI/AAAAAAAAUGk/lSmrKTCOsmU/s0/Selection_001.png[/IMG]

---

### Post by BenginM on 2012-05-21
Try the following :

sudo purge gnome-tweak-tool

sudo apt-get install gnome-tewak-tool

go to extensions.gnome.org

turn on the User Themes extension 

open a terminal and execute the following :

sudo cp ~/.local/share/gnome-shell/extensions/user-theme@gnome-shell-extensions.gcampax.github.com/schemas/org.gnome.shell.extensions.user-theme.gschema.xml /usr/share/glib-2.0/schemas

# then 

sudo glib-compile-schemas /usr/share/glib-2.0/schemas

log out and log back in ..

install some them extensions .. search for em or check in

[http://gnome-shell.deviantart.com/gallery/28081982](http://gnome-shell.deviantart.com/gallery/28081982)

make sure they are Compatible with gnome-shell 3.4  

Next install Shell Restart User Menu Entry extension from extensions.gnome.org

select a shell theme using the tewak-tool Load the GNOME Tweak Tool and go to Shell Extensions and click the "Use Theme Extension" switch. Now go to "Theme" and click the Shell Theme box and locate your theme zip. Now you can select the theme in the dropdown box.

restart the shell using the Shell Restart User Menu Entry extension

---

### Post by Tornikee on 2012-05-21
Thanks a lot for the hint. Will do it first thing tomorrow.

---

### Post by lingceng on 2012-05-22
@Sary.sa Great thanks! that work for me. remember logout!

---

### Post by Tornikee on 2012-05-22
Tried these commands, but encountered several issues:

(1) Terminal says it can't find a 'purge' command. I removed GNOME Tweak Tool via Software Center and then installed through apt-get command;
(2) User Themes extension was already turned on at extensions.gnome.org; just disabled and then enabled it again;
(3) Executed those long command lines, but couldn't log out and back in, as my status menu doesn't show the log out command, also caused by the issue of broken user-themes-extension. So I just restarted, ran GNOME Tweak Tool, but found the same 'user-theme-extension incorrectly installed' error there.

---

### Post by BenginM on 2012-05-22
> **lingceng said:**
> @Sary.sa Great thanks! that work for me. remember logout!

[COLOR="Red"]Hey fellow ubuntuser :) , am glad it worked for you .
[/COLOR]

---

### Post by BenginM on 2012-05-22
Hey buddy , my bad it should be sudo apt-get --purge Package , or sudo apt-get remove --purge Package .

i guess when you removed it from software center it didn't not remove it's previous settings , that's when Purge comes in handy .. see man apt-get , or man aptitude , and man dpkg .

how is that he user-themes-extension is broken !

this is what happen when one uses an unofficial repo/ppa for an important part of the system ( DE , DM , WM ).

# PPAs are unsupported third-party packages, and you use them at your own risk.

[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

I'd use ppa-purge to remove that ppa for good .

[https://launchpad.net/ubuntu/+source/ppa-purge](https://launchpad.net/ubuntu/+source/ppa-purge)

for an example ,sudo ppa-purge ppa:webupd8team/gnome3

sudo apt-get update

or just disable the ppa from software center , or synaptic .



Now , follow those steps mentioned above , but first make sure you disable the user-theme-extension from extensions.gnome.org .. and that you remove the package " gnome-shell-extensions-user-theme " which was installed form that PPA , then enable the user-theme-extension from extensions.gnome.org again .

---

### Post by Tornikee on 2012-05-23
Cheers for the hint and the info. Will try that today.

---

### Post by Tornikee on 2012-05-23
OK that purged the package successfully, and I removed the PPA I used for GNOME Tweak Tool. But I still need the application for installing/switching extensions and themes so I should look for another, stable PPA for it, right?

Also, I can't find the user theme extension package in Synaptic to remove it. May have removed it already?

---

### Post by Tornikee on 2012-05-23
[ edited ]

---

### Post by jjiggens on 2012-05-23
I too have the same issue, all suggestions in this thread have been fruitless for me.

I have no idea what to try next.

---

### Post by Tornikee on 2012-05-24
I searched to find different PPAs for GNOME Tweak Tool, but the only one seems to be the one I used.

I guess I might just do a clean Ubuntu reinstall, it's just that I'm not sure if it's definitely going to solve the issue of broken user themes extension in GNOME.

---

### Post by jjiggens on 2012-05-24
> **Tornikee said:**
> I searched to find different PPAs for GNOME Tweak Tool, but the only one seems to be the one I used.

I guess I might just do a clean Ubuntu reinstall, it's just that I'm not sure if it's definitely going to solve the issue of broken user themes extension in GNOME.
It wont solve it, i'm on a brand new un-touched clean install right now. and i have the same issues. shell extensions is blank in tweak tool and i cannot change the shell theme. i have exhausted all tips and tricks i can find and none of them have worked for me.

---

### Post by Tornikee on 2012-05-24
Thanks for that info.

---

### Post by traditionalist on 2012-05-24
> **jjiggens said:**
> It wont solve it, i'm on a brand new un-touched clean install right now. and i have the same issues. shell extensions is blank in tweak tool and i cannot change the shell theme. i have exhausted all tips and tricks i can find and none of them have worked for me.

Same here, extensions remains blank whatever you do;

[[IMG]http://img443.imageshack.us/img443/4305/advancedsettings009q.th.png[/IMG]]("http://img443.imageshack.us/i/advancedsettings009q.png/")

[[IMG]http://img210.imageshack.us/img210/8365/advancedsettings012.th.png[/IMG]](http://img210.imageshack.us/i/advancedsettings012.png/)


But this solved all my problems with themes;

[http://ubuntuforums.org/showpost.php?p=11964456&postcount=86](http://ubuntuforums.org/showpost.php?p=11964456&postcount=86)

---

### Post by BenginM on 2012-05-25
> **Tornikee said:**
> I searched to find different PPAs for GNOME Tweak Tool, but the only one seems to be the one I used.

I guess I might just do a clean Ubuntu reinstall, it's just that I'm not sure if it's definitely going to solve the issue of broken user themes extension in GNOME.

You don't need a ppa to install gnome-teak-tool

look for it with apt-cache policy gnome-teak-tool

and see which repo you can install it from , you might need to enable that repo to install it.

---

### Post by BenginM on 2012-05-25
> **jjiggens said:**
> It wont solve it, i'm on a brand new un-touched clean install right now. and i have the same issues. shell extensions is blank in tweak tool and i cannot change the shell theme. i have exhausted all tips and tricks i can find and none of them have worked for me.

You need the user-theme-extension to be able to change themes.

---

### Post by BenginM on 2012-05-25
> **Tornikee said:**
> OK that purged the package successfully, and I removed the PPA I used for GNOME Tweak Tool. But I still need the application for installing/switching extensions and themes so I should look for another, stable PPA for it, right?

Also, I can't find the user theme extension package in Synaptic to remove it. May have removed it already?

You missed a point from my last post .. install the user-theme-extension from gnome shell extensions site , and follow the steps i mentioned in my last post .

---

### Post by BenginM on 2012-05-25
> **jjiggens said:**
> It wont solve it, i'm on a brand new un-touched clean install right now. and i have the same issues. shell extensions is blank in tweak tool and i cannot change the shell theme. i have exhausted all tips and tricks i can find and none of them have worked for me.

Your issue depends on how you installed the extensions in the first place ..

# someone please explain as to why it did worked with 'lingceng'. :popcorn:

---

### Post by jjiggens on 2012-05-26
> **Sary.sa said:**
> Your issue depends on how you installed the extensions in the first place ..

# someone please explain as to why it did worked with 'lingceng'. :popcorn:
extensions.gnome.org doesn't give me the button to turn the user theme plugin on or off, so i assume that they don't work with my version of gnome. the only extensions i can find for 3.4 are "gnome-shell-extensions" in the package manager. and that's not working clearly.

---

### Post by BenginM on 2012-05-27
> **jjiggens said:**
> extensions.gnome.org doesn't give me the button to turn the user theme plugin on or off, so i assume that they don't work with my version of gnome. the only extensions i can find for 3.4 are "gnome-shell-extensions" in the package manager. and that's not working clearly.

For the ON/OFF toggle button to show , your Gnome-Shell version needs to be compatible with that extension .

---

### Post by jjiggens on 2012-05-27
> **Sary.sa said:**
> For the ON/OFF toggle button to show , your Gnome-Shell version needs to be compatible with that extension .
guess the latest gnome shell that is on 12.04 is not compatible.

---

### Post by Tornikee on 2012-05-28
Are there users who had Ubuntu 12.04/GNOME Shell 3.4 combination with GNOME Tweak Tool and user-theme-extension, and still use all of this w/o any issues?

---

### Post by BenginM on 2012-05-30
> **jjiggens said:**
> guess the latest gnome shell that is on 12.04 is not compatible.

Not sure if you're been SMART or FUNNY ! ,  but yeah keep gussing .


# You should've provided more information about your system setup & stated your issue instead of acting and guessing  .

Now go figure !

---

### Post by t.rei on 2012-05-30
Now, don't be rude. The gnome-shell in the repository is not the latest there is, and not all components of gnome3 made it into the ubuntu repository. 

There are other ppa's (gnome3-team and ricotz testing ppa) but I would NOT recommend installing those in the usually nice and stable ubuntu 12.04.

Right now, the extension installation seems to be borked anyways - I can't install anything from the page. The "install?" question shows, and after that... nothing. Worst part: If I click on "update" the UNINSTALL works. But the upgraded version will not get installed. And it's a bit of a hassle to get all the tarballs from the respective extension website. :)

But running testing stuff and complaining about finding an error is STRANGE! Testing... Errors... Testing... Errors...

---

### Post by BenginM on 2012-05-30
> **Tornikee said:**
> Are there users who had Ubuntu 12.04/GNOME Shell 3.4 combination with GNOME Tweak Tool and user-theme-extension, and still use all of this w/o any issues?

I know i do , check it 

sary@sa-lap:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
sary@sa-lap:~$ 

sary@sa-lap:~$ apt-cache depends gnome-tweak-tool
gnome-tweak-tool
  Depends: python2.7
  Depends: python
  Depends: python
  Depends: gnome-shell
  Depends: gsettings-desktop-schemas
  Depends: python-gobject
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-gconf-2.0

sary@sa-lap:~$ apt-cache depends gnome-shell
gnome-shell
  Depends: gir1.2-atk-1.0
  Depends: gir1.2-clutter-1.0
  Depends: gir1.2-cogl-1.0
  Depends: gir1.2-coglpango-1.0
  Depends: gir1.2-folks-0.6
  Depends: gir1.2-freedesktop
  Depends: gir1.2-gdesktopenums-3.0
  Depends: gir1.2-gdkpixbuf-2.0
  Depends: gir1.2-gee-1.0
  Depends: gir1.2-glib-2.0
  Depends: gir1.2-gmenu-3.0
  Depends: gir1.2-gtk-3.0
  Depends: gir1.2-json-1.0
  Depends: gir1.2-mutter-3.0
  Depends: gir1.2-networkmanager-1.0
  Depends: gir1.2-pango-1.0
  Depends: gir1.2-soup-2.4
  Depends: gir1.2-telepathyglib-0.12
  Depends: gir1.2-telepathylogger-0.2
  Depends: gnome-icon-theme-full
 |Depends: dconf-gsettings-backend
  Depends: <gsettings-backend>
    dconf-gsettings-backend
  Depends: gconf-service
  Depends: gnome-bluetooth
  Depends: libatk1.0-0
  Depends: libc6
  Depends: libcairo2
  Depends: libcanberra0
  Depends: libclutter-1.0-0
  Depends: libcogl-pango0
  Depends: libcogl9
  Depends: libcroco3
  Depends: libdbus-glib-1-2
  Depends: libecal-1.2-10
  Depends: libedataserver-1.2-15
  Depends: libedataserverui-3.0-1
  Depends: libfolks25
  Depends: libgconf-2-4
  Depends: libgdk-pixbuf2.0-0
  Depends: libgee2
  Depends: libgirepository-1.0-1
  Depends: <libgjs0->
    libgjs0c
  Depends: libgjs0c
  Depends: libglib2.0-0
  Depends: libgnome-keyring0
  Depends: libgnome-menu-3-0
  Depends: libgstreamer0.10-0
  Depends: libgtk-3-0
  Depends: libical0
  Depends: libjson-glib-1.0-0
  Depends: libmozjs185-1.0
  Depends: libmutter0
  Depends: libmutter0
  Depends: libnm-glib4
  Depends: libnm-util2
  Depends: libpango1.0-0
  Depends: libpolkit-agent-1-0
  Depends: libpolkit-gobject-1-0
  Depends: libpulse-mainloop-glib0
  Depends: libpulse0
  Depends: libstartup-notification0
  Depends: libtelepathy-glib0
  Depends: libtelepathy-logger2
  Depends: libx11-6
  Depends: libxext6
  Depends: libxfixes3
  Depends: libxml2
  Depends: gnome-shell-common
  Depends: gir1.2-accountsservice-1.0
  Depends: gir1.2-caribou-1.0
  Depends: gir1.2-gconf-2.0
  Depends: gir1.2-gjsdbus-1.0
  Depends: gir1.2-gkbd-3.0
  Depends: gir1.2-gnomebluetooth-1.0
  Depends: gir1.2-polkit-1.0
  Depends: gir1.2-upowerglib-1.0
  Depends: gjs
  Depends: gnome-icon-theme-symbolic
  Depends: gnome-settings-daemon
  Depends: gsettings-desktop-schemas
  Depends: python
  Depends: telepathy-mission-control-5
  Recommends: cups-pk-helper
  Recommends: gnome-contacts
  Recommends: gnome-control-center
  Recommends: gnome-session-fallback
  Recommends: gnome-themes-standard
  Recommends: gnome-user-guide
  Breaks: <fglrx-driver>
  Breaks: gnome-control-center
  Breaks: gnome-session
  Breaks: gnome-tweak-tool

sary@sa-lap:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.4.1-0ubuntu2
  Candidate: 3.4.1-0ubuntu2
  Version table:
 *** 3.4.1-0ubuntu2 0
        500 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status

sary@sa-lap:~$ apt-cache policy gnome-tweak-tool
gnome-tweak-tool:
  Installed: 3.3.4-0ubuntu1
  Candidate: 3.3.4-0ubuntu1
  Version table:
 *** 3.3.4-0ubuntu1 0
        500 [http://sa.archive.ubuntu.com/ubuntu/](http://sa.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages
        100 /var/lib/dpkg/status

# a simple search came-up with ...

[http://askubuntu.com/questions/90419/gnome-shell-extensions-user-theme-wont-install-due-to-unmet-dependencies](http://askubuntu.com/questions/90419/gnome-shell-extensions-user-theme-wont-install-due-to-unmet-dependencies)

[http://askubuntu.com/questions/140037/trouble-installing-gnome-shell-extensions-user-theme-dependency-ppa-conflict](http://askubuntu.com/questions/140037/trouble-installing-gnome-shell-extensions-user-theme-dependency-ppa-conflict)

---

### Post by jjiggens on 2012-05-30
I'm compiling android right now, after this i will look at what i have and diff them from your list. however i'm not trying to be "SMART or FUNNY" So id appreciate it if we kept our comments to a technical and helpful nature.

I have installed a fresh copy of 12.04 lts on a new laptop, i have not added any impurities in the ppa sense and am using this in a out of the box state, i have followed your instructions that you say work, that were posted previously. They do not work for me.  extensions.gnome.org does not give me an option to install or uninstall, now you have mentioned this is because the version of gnome shell i have is not compatible, so my assumptions on guessing mine was not, was not meant to be smart nor funny. I do not appear to be the only one who cannot get your instructions to work either. 

I do have gnome-shell-extensions and gnome-shell-extensions-common installed, in fact those two packages are the only thing i have in my repositories that even mention extensions for gnome shell.

now failing that i fix this by some missing dependency which i don't think i have an issue with, please do tell what i'm missing since you seem to be portraying that i am doing something wrong here and you know what it is from your comments.

---

### Post by kohoutek1 on 2012-05-30
Looks like this conversation got a little off track and into some personal bickering. Let's get back to the point.

Tornikee:

> Is this a known issue and how can I solve it?

It is a known issue. I had it immediately after upgrading to Ubuntu 12.04 then updating the Shell. Extensions were breaking the Shell. This was due largely to outdated and in some cases redundant extensions. The problems kept piling up.

The good news was that the fix was quite general, and easy to do.

As pfnorris pointed out, the problem is in the two extension directories. 

Here's what I did, and I didn't need CL to do it:

Remove all extensions in both directories to trash, empty trash. This includes the theme extension. Reboot.

After this, you'll have a nice, fresh Shell to work with.

Then, get on over to extensions.gnome.org and begin reinstalling fresh extensions, one by one. You'll have your old shell back in a few minutes, minus a few ext's that haven't been ported to 3.4 yet.

The beauty of the shell is the .js building-block framework. Simplicity, directness.

I hope this works for you.

---

### Post by jjiggens on 2012-05-30
Here is my output. only notable diff is i am on a 64 bit system, needed because i have 16gb of ram.

LSB Version:     core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise

apt-cache depends gnome-tweak-tool
gnome-tweak-tool
Depends: python2.7
Depends: python
Depends: python
Depends: gnome-shell
Depends: gsettings-desktop-schemas
Depends: python-gobject
Depends: gir1.2-gtk-3.0
Depends: gir1.2-gconf-2.0

apt-cache depends gnome-shell
gnome-shell
Depends: gir1.2-atk-1.0
Depends: gir1.2-clutter-1.0
Depends: gir1.2-cogl-1.0
Depends: gir1.2-coglpango-1.0
Depends: gir1.2-folks-0.6
Depends: gir1.2-freedesktop
Depends: gir1.2-gdesktopenums-3.0
Depends: gir1.2-gdkpixbuf-2.0
Depends: gir1.2-gee-1.0
Depends: gir1.2-glib-2.0
Depends: gir1.2-gmenu-3.0
Depends: gir1.2-gtk-3.0
Depends: gir1.2-json-1.0
Depends: gir1.2-mutter-3.0
Depends: gir1.2-networkmanager-1.0
Depends: gir1.2-pango-1.0
Depends: gir1.2-soup-2.4
Depends: gir1.2-telepathyglib-0.12
Depends: gir1.2-telepathylogger-0.2
Depends: gnome-icon-theme-full
Depends: dconf-gsettings-backend
Depends: <gsettings-backend>
dconf-gsettings-backend
Depends: gconf-service
gconf-service:i386
Depends: gnome-bluetooth
Depends: libatk1.0-0
Depends: libc6
Depends: libcairo2
Depends: libcanberra0
Depends: libclutter-1.0-0
Depends: libcogl-pango0
Depends: libcogl9
Depends: libcroco3
Depends: libdbus-glib-1-2
Depends: libecal-1.2-10
Depends: libedataserver-1.2-15
Depends: libedataserverui-3.0-1
Depends: libfolks25
Depends: libgconf-2-4
Depends: libgdk-pixbuf2.0-0
Depends: libgee2
Depends: libgirepository-1.0-1
Depends: <libgjs0->
libgjs0c
Depends: libgjs0c
Depends: libglib2.0-0
Depends: libgnome-keyring0
Depends: libgnome-menu-3-0
Depends: libgstreamer0.10-0
Depends: libgtk-3-0
Depends: libical0
Depends: libjson-glib-1.0-0
Depends: libmozjs185-1.0
Depends: libmutter0
Depends: libmutter0
Depends: libnm-glib4
Depends: libnm-util2
Depends: libpango1.0-0
Depends: libpolkit-agent-1-0
Depends: libpolkit-gobject-1-0
Depends: libpulse-mainloop-glib0
Depends: libpulse0
Depends: libstartup-notification0
Depends: libtelepathy-glib0
Depends: libtelepathy-logger2
Depends: libx11-6
Depends: libxext6
Depends: libxfixes3
Depends: libxml2
Depends: gnome-shell-common
Depends: gir1.2-accountsservice-1.0
Depends: gir1.2-caribou-1.0
Depends: gir1.2-gconf-2.0
Depends: gir1.2-gjsdbus-1.0
Depends: gir1.2-gkbd-3.0
Depends: gir1.2-gnomebluetooth-1.0
Depends: gir1.2-polkit-1.0
Depends: gir1.2-upowerglib-1.0
Depends: gjs
Depends: gnome-icon-theme-symbolic
Depends: gnome-settings-daemon
Depends: gsettings-desktop-schemas
Depends: python
Depends: telepathy-mission-control-5
Recommends: cups-pk-helper
Recommends: gnome-contacts
Recommends: gnome-control-center
Recommends: gnome-session-fallback
Recommends: gnome-themes-standard
Recommends: gnome-user-guide
Breaks: <fglrx-driver>
Breaks: <fglrx-driver:i386>
Breaks: gnome-control-center
Breaks: gnome-control-center:i386
Breaks: gnome-session
Breaks: <gnome-session:i386>
Breaks: gnome-tweak-tool
Breaks: <gnome-tweak-tool:i386>
Conflicts: gnome-shell:i386

apt-cache policy gnome-shell
gnome-shell:
Installed: 3.4.1-0ubuntu2
Candidate: 3.4.1-0ubuntu2
Version table:
*** 3.4.1-0ubuntu2 0
500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages
100 /var/lib/dpkg/status

apt-cache policy gnome-tweak-tool
gnome-tweak-tool:
Installed: 3.3.4-0ubuntu1
Candidate: 3.3.4-0ubuntu1
Version table:
*** 3.3.4-0ubuntu1 0
500 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/universe amd64 Packages
100 /var/lib/dpkg/status

---

### Post by Tornikee on 2012-06-07
Could [http://bit.ly/NM7uzJ](http://bit.ly/NM7uzJ) this solve the issue? I'm not gonna be near my PC until later, so thought I'd ask if anyone has tried this.

---

### Post by Tornikee on 2012-06-07
Actually, it did solve the issue.

---

### Post by Cammigirl on 2012-07-21
> **kohoutek1 said:**
> Looks like this conversation got a little off track and into some personal bickering. Let's get back to the point.

Tornikee:



It is a known issue. I had it immediately after upgrading to Ubuntu 12.04 then updating the Shell. Extensions were breaking the Shell. This was due largely to outdated and in some cases redundant extensions. The problems kept piling up.

The good news was that the fix was quite general, and easy to do.

As pfnorris pointed out, the problem is in the two extension directories. 

Here's what I did, and I didn't need CL to do it:

Remove all extensions in both directories to trash, empty trash. This includes the theme extension. Reboot.

After this, you'll have a nice, fresh Shell to work with.

Then, get on over to extensions.gnome.org and begin reinstalling fresh extensions, one by one. You'll have your old shell back in a few minutes, minus a few ext's that haven't been ported to 3.4 yet.

The beauty of the shell is the .js building-block framework. Simplicity, directness.

I hope this works for you.
I'm having the same problem.  How is this done?

---

### Post by BenginM on 2012-10-26
> **Cammigirl said:**
> I'm having the same problem.  How is this done?

# follow the answer of " How do I uninstall my extensions? " 

[https://extensions.gnome.org/about/](https://extensions.gnome.org/about/)

---

