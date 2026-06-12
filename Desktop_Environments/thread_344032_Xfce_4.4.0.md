---
title: "Xfce 4.4.0"
date: 2007-01-22
forum: Desktop Environments
---

### Post by Hossie on 2007-01-22
Hi,

XFCE 4.4.0 is released, are there any repositories for installing it on Edgy? I couldnt find anything on the forums yet...

Did someone try if the Debian Testing .debs work with Ubuntu?

---

### Post by scrooge_74 on 2007-01-22
Debian testing is the base for Ubuntu

didi you check in synaptic for it?

---

### Post by josys36 on 2007-01-22
They won't put this version in the repos until maybe Feisty. I would just use their graphical installer to install XFCE. That is what I do anyway. 

Jason

---

### Post by Hossie on 2007-01-22
I think I'll try the installer tomorrow.

---

### Post by Pobega on 2007-01-22
Xfce 4.4.0? Is there an online changelog anywhere, I don't plan on downloading the package.

---

### Post by josys36 on 2007-01-22
> **Pobega said:**
> Xfce 4.4.0? Is there an online changelog anywhere, I don't plan on downloading the package.

xfce.org should have what you are looking for.

Jason

---

### Post by Pobega on 2007-01-22
> **josys36 said:**
> xfce.org should have what you are looking for.

Jason

Nope, I checked there before I posted; No changelog.

---

### Post by josys36 on 2007-01-22
I just installed this and it worked fine. The only thing I am disapointed with is that when you make the panel transparent, all the icons and clock go with it. I would have thought they would have fixed this by now. Oh well maybe someone here knows how to do that.

Jason

---

### Post by Pobega on 2007-01-22
> **josys36 said:**
> I just installed this and it worked fine. The only thing I am dissapointed with is that when you make the panel transparent, all the icons and clock go with it. I would have thought they would have fixed this by now. Oh well maybe someone here knows how to do that.

JasonIs there anything noticeably different about it? I'm not going to bother installing it unless they changed it noticeably, I've come to learn that most "updates" are really just one or two tiny new features thrown on; Not worth the time spent compiling.

---

### Post by Wight_Rhino on 2007-01-22
[Here's a helpful Link]("http://www.smorgasbord.net/node/2944") for a Xubuntu upgrade.

They say it's a complete rewrite of xfce rather than an update, I'm going to upgrade tomorrow, (I'm at work:frown: )

---

### Post by Pobega on 2007-01-22
> **Wight_Rhino said:**
> [Here's a helpful Link]("http://www.smorgasbord.net/node/2944") for a Xubuntu upgrade.

They say it's a complete rewrite of xfce rather than an update, I'm going to upgrade tomorrow, (I'm at work:frown: )

**Edit:** Definitley don't choose ALSA support. Botched up my system for a while there.

**Edit2:** Anyone know how to remove these annoying icons off of my desktop?

---

### Post by Wight_Rhino on 2007-01-23
Upgrade went flawlessly, and I'm very impressed=D>  Very good work all round. I also installed The Volume-Manager and Archive Plugins to Thunar and overall I'm very pleased. Especially with the built-in compositor.

The Desktop icons can be turned off in the desktop preference applet; However, I have a Floppy disk showing up in my Thunar sidebar (I don't even have a floppy disk!) It won't delete, disable or unmount. Any ideas?

---

### Post by detyabozhye on 2007-01-23
> **Pobega said:**
> Is there anything noticeably different about it? I'm not going to bother installing it unless they changed it noticeably, I've come to learn that most "updates" are really just one or two tiny new features thrown on; Not worth the time spent compiling.

It is a major change from 4.2, but since you're an Edgy user, you already have the BETA 2 of 4.4, so the changes won't be that huge for you.

---

### Post by Pobega on 2007-01-23
Actually, in my opinion 4.4 is a downgrade. You're almost forced to use OSS for a lot of things, for example frozen-bubble is now using OSS (Previously ALSA). So I can't listen to the FB music and wait for the Jabber IM "ping" at the same time.

I'll just stick with the Xubuntu 6.10 version of Xfce, until they hopefully fix this problem.

---

### Post by Wight_Rhino on 2007-01-23
> **Pobega said:**
> Actually, in my opinion 4.4 is a downgrade. You're almost forced to use OSS for a lot of things, for example frozen-bubble is now using OSS (Previously ALSA). So I can't listen to the FB music and wait for the Jabber IM "ping" at the same time.

I'll just stick with the Xubuntu 6.10 version of Xfce, until they hopefully fix this problem.

Strange, I had no problem whatsoever with the sound. (I opted for Alsa-support) everything in that respect is working just as it was before the upgrade.

---

### Post by Pobega on 2007-01-23
Well when I installed it with ALSA support it didn't even load xfwm. So I reinstalled with OSS support, and it worked fine; But forced all of my apps to use OSS.

So I tried reinstalling all of my ALSA related stuffs (libraries, packages, etc.) and reinstalled Xfce4.4, but I ended up running into the same brick wall.

---

### Post by NoobieDoobieDo on 2007-01-24
I got XFCE 4.4 installed on Ubuntu (6.01?) but it wont let me install xfce goodies ..

Says I dont have this libusb (0.1.12)

---

### Post by randomusername on 2007-01-24
You should be able to fix that by opening up a console and entering:

```
sudo apt-get install libusb-0.1-4 
```

---

### Post by Pobega on 2007-01-24
Does anyone have any ideas on what ALSA packages I'd need to be able to use Xfce 4.4 with ALSA support? I'm currently using ALSA on my 4.4 beta (Xubuntu 6.10 default Xfce), but for some reason when updating it doesn't accept my current ALSA configurations.

---

### Post by teejay17 on 2007-01-24
> **Wight_Rhino said:**
> [Here's a helpful Link]("http://www.smorgasbord.net/node/2944") for a Xubuntu upgrade.

They say it's a complete rewrite of xfce rather than an update, I'm going to upgrade tomorrow, (I'm at work:frown: )
Does all this information work, even though it's not a release candidate anymore?

---

### Post by tman_ubuntu on 2007-01-24
Does Xfce 4.4.0 support a Theme Manager?  If so, where and how to use it?

---

### Post by Pobega on 2007-01-24
Applications - Settings - Window Manager Settings and User Interface Settings

---

### Post by chebe on 2007-01-25
> **Pobega said:**
> Does anyone have any ideas on what ALSA packages I'd need to be able to use Xfce 4.4 with ALSA support? I'm currently using ALSA on my 4.4 beta (Xubuntu 6.10 default Xfce), but for some reason when updating it doesn't accept my current ALSA configurations.

Because the path to modprobe and alsactl are different between debian and ubuntu, you need to create some link

```
sudo ln -s /sbin/alsactl /usr/sbin/alsactl
sudo ln -s /sbin/modprobe /usr/sbin/modprobe
```

and it will work !

---

### Post by maxamillion on 2007-01-25
> **scrooge_74 said:**
> Debian testing is the base for Ubuntu

didi you check in synaptic for it?

No, Ubuntu is a 6 month snapshot of their sid/unstable repositories that are then worked on, configured and made "ubuntu stable"

Currently 4.4-stable is feisty only, but i believe there is talk of it making its way into the backports repository.

---

### Post by -Phi- on 2007-01-26
I was having the same issues as **Pobega** with ALSA and got a hint from [this thread]("http://ubuntuforums.org/showthread.php?t=251350&page=6") to install **libasound2-dev**. I also did the symbolic link thing, but don't know if it made a difference or not.

My total additional installs (plus 90 odd dependencies) were: libgtk2.0-dev libxml2-dev libvte-dev libxpm-dev libxfce4mcs-dev libdbus-1-dev libdbus-glib-1-dev libdbh-4.5-dev xorg-dev libasound2-dev pkg-config liburi-perl libCGI-perl libwww-perl libxml-perl (I already had  build-essential and libxml-parser-perl installed)

I couldn't find libdbh1.0-dev, but libdbh-4.5-dev seemed to be equivalent.

What a lot of work for a few drop shadows :p

- Phi

---

### Post by Pobega on 2007-01-26
For some reason my panel is becoming transparent; How do I undo that?

And why did my desktop wallpaper disappear?


[[IMG]http://img176.imageshack.us/img176/3453/xfcerw1.th.png[/IMG]](http://img176.imageshack.us/img176/3453/xfcerw1.png)

---

### Post by psychicdragon on 2007-01-26
> **Pobega said:**
> For some reason my panel is becoming transparent; How do I undo that?
If compositing is enabled (which it obviously is on your box), the panel preferences allow you to set the opacity of the panel. Just set the transparency of the panel to 0%.

---

### Post by Pobega on 2007-01-26
[[IMG]http://img110.imageshack.us/img110/8613/xfce2to3.th.png[/IMG]](http://img110.imageshack.us/img110/8613/xfce2to3.png)

I don't see an option for it, but maybe I'm missing something obvious.

---

### Post by BoMbS14 on 2007-01-26
> I don't see an option for it, but maybe I'm missing something obvious.

right click on your panel, and it's under "customize panel"

---

### Post by Pobega on 2007-01-26
> **BoMbS14 said:**
> right click on your panel, and it's under "customize panel"

Ah, thanks, that fixed it.

**Edit:** And the background seems to have fixed itself, weird.

---

### Post by Pobega on 2007-01-26
I just want to bump to add...Am I the only one getting gksudo problems when using compositing? I turned compositing off and now my terminal says something like:> pobega@ackbar:~$ gksudo thunar
 broken.The program still runs, but the broken thing is kind of freaking me out.

---

### Post by locosmurf on 2007-01-26
Does anyone know how to get the Dock that DreamLinux has for Xubuntu? I have been searching for a while and haven't been able to find it. thanks in advance.

---

### Post by Ptero-4 on 2007-01-27
Anyone knows why xfwm4 compositing (edgy xfce) doesn't work in a ATI Rage 128 mobility (8MB VRAM)? The composite setting is there in the xorg.conf.

---

### Post by igknighted on 2007-01-27
> **locosmurf said:**
> Does anyone know how to get the Dock that DreamLinux has for Xubuntu? I have been searching for a while and haven't been able to find it. thanks in advance.

I think it is just an extra panel put on the bottom, centered and not stretched the whole way.  It doesn't have any kind of animations or effects if I remember from the last time I used it.

---

### Post by Pobega on 2007-01-27
> **locosmurf said:**
> Does anyone know how to get the Dock that DreamLinux has for Xubuntu? I have been searching for a while and haven't been able to find it. thanks in advance.

Put a new panel at the bottom, and make it freely movable and centered. There you go, it now looks like DreamLinux.

---

### Post by Pobega on 2007-01-27
Also...The way the desktop is set up now it doesn't seem to pick up external devices, is anyone else having this problem or is it just me?

---

### Post by detyabozhye on 2007-01-27
> **Ptero-4 said:**
> Anyone knows why xfwm4 compositing (edgy xfce) doesn't work in a ATI Rage 128 mobility (8MB VRAM)? The composite setting is there in the xorg.conf.

You gotta edit an XML file in the config somewhere. It's an Edgy bug. Dapper didn't have it and it's fixed in Feisty.

---

### Post by detyabozhye on 2007-01-27
> **locosmurf said:**
> Does anyone know how to get the Dock that DreamLinux has for Xubuntu? I have been searching for a while and haven't been able to find it. thanks in advance.

You can choose between the Xfce panel and Engage from Enlightenment DR17 there.

---

### Post by groggyboy on 2007-01-27
i tried installing Xfce4.4 final today, by using the installers off the Xfce website.

Xfce and thunar installed fine once i had the relevant packages.  However, both xfce-goodies and thunar-bundle exited with an error.  All dependencies were met for both (according to the installer).

The last few lines from the thunar error log:```
media-tags-provider.c:26:26: error: taglib/tag_c.h: No such file or directory
In file included from tag-renamer.c:37:
./audio-tags-page.h:50: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
./audio-tags-page.h:52: error: expected declaration specifiers or '...' before 'TagLib_File'
tag-renamer.c: In function 'tag_renamer_process':
tag-renamer.c:364: error: 'TagLib_File' undeclared (first use in this function)
tag-renamer.c:364: error: (Each undeclared identifier is reported only once
tag-renamer.c:364: error: for each function it appears in.)
tag-renamer.c:364: error: 'taglib_file' undeclared (first use in this function)
tag-renamer.c:365: error: 'TagLib_Tag' undeclared (first use in this function)
tag-renamer.c:365: error: 'taglib_tag' undeclared (first use in this function)
tag-renamer.c:366: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
tag-renamer.c:366: error: 'taglib_properties' undeclared (first use in this function)
tag-renamer.c:409: warning: passing argument 1 of 'g_strdup' makes pointer from integer without a cast
tag-renamer.c:410: warning: passing argument 1 of 'g_strdup' makes pointer from integer without a cast
make[2]: *** [thunar_media_tags_plugin_la-tag-renamer.lo] Error 1
make[2]: *** Waiting for unfinished jobs....
In file included from media-tags-provider.c:30:
./audio-tags-page.h:50: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
./audio-tags-page.h:52: error: expected declaration specifiers or '...' before 'TagLib_File'
media-tags-provider.c: In function 'media_tags_get_audio_file_supported':
media-tags-provider.c:149: error: 'TagLib_File' undeclared (first use in this function)
media-tags-provider.c:149: error: (Each undeclared identifier is reported only once
media-tags-provider.c:149: error: for each function it appears in.)
media-tags-provider.c:149: error: 'taglib_file' undeclared (first use in this function)
make[2]: *** [thunar_media_tags_plugin_la-media-tags-provider.lo] Error 1
make[2]: Leaving directory `/tmp/Thunar-Bundle-0.8.0-installer/thunar-media-tags-plugin-0.1.2/thunar-plugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/Thunar-Bundle-0.8.0-installer/thunar-media-tags-plugin-0.1.2'
make: *** [all] Error 2
!! Failed to build thunar-media-tags-plugin-0.1.2, see the errors above
!! for details on the problem.
```
and from xfce-goodies:```
verve.o -MD -MP -MF .deps/xfce4_verve_plugin-verve.Tpo -c -o xfce4_verve_plugin-verve.o `test -f 'verve.c' || echo './'`verve.c
verve.c:25:18: error: pcre.h: No such file or directory
verve.c: In function &#8216;verve_is_url&#8217;:
verve.c:197: error: &#8216;pcre&#8217; undeclared (first use in this function)
verve.c:197: error: (Each undeclared identifier is reported only once
verve.c:197: error: for each function it appears in.)
verve.c:197: error: &#8216;pattern&#8217; undeclared (first use in this function)
verve.c: In function &#8216;verve_is_email&#8217;:
verve.c:244: error: &#8216;pcre&#8217; undeclared (first use in this function)
verve.c:244: error: &#8216;pattern&#8217; undeclared (first use in this function)
make[3]: *** [xfce4_verve_plugin-verve.o] Error 1
make[3]: *** Waiting for unfinished jobs....
mv -f .deps/xfce4_verve_plugin-verve-plugin.Tpo .deps/xfce4_verve_plugin-verve-plugin.Po
make[3]: Leaving directory `/tmp/xfce-goodies-4.4.0-installer/verve-plugin/panel-plugin'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tmp/xfce-goodies-4.4.0-installer/verve-plugin/panel-plugin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/xfce-goodies-4.4.0-installer/verve-plugin'
make: *** [all] Error 2
!! Failed to build verve-plugin, see the errors above
!! for details on the problem.
```

any suggestions?

---

### Post by psychicdragon on 2007-01-27
apt-get install libpcre3-dev libtagc0-dev

---

### Post by Pobega on 2007-01-28
Okay, I give up on this new Xfce upgrade. I want to reinstall the old beta Xfce (The one in the repos, I guess). Is there any way I can go about doing this? And uninstall the new Xfce 4.4 as well.

---

### Post by groggyboy on 2007-01-28
> **psychicdragon said:**
> apt-get install libpcre3-dev libtagc0-dev

thanks!  that fixed the compile error.

Xfce FTW!

---

### Post by Pobega on 2007-01-28
No love here? I'm thinking of reinstalling Xubuntu again, I really can't stand this most recent update. Does anyone have an old .run file of Xfce? Preferably the one that comes default with Xubuntu 6.10

---

### Post by cendant on 2007-01-29
Guys, it is the full list of dependencies for using the graphic installer?

build-essential libxml-parser-perl libgtk2.0-dev libxml2-dev libvte-dev libxpm-dev libsm-dev libice-dev  libxfce4util-dev libxfce4mcs-dev libhal-storage-dev libdbus-1-dev libdbus-glib-1-dev  libdbh1.0-dev libdbh-4.5-dev xorg-dev libasound2-dev pkg-config liburi-perl libCGI-perl libwww-perl libxml-perl libpcre3-dev libtagc0-dev desktop-file-utils shared-mime-info libusb-0.1-4 libjpeg62-dev libstartup-notification0-dev

---

### Post by -Phi- on 2007-01-29
I'm kinda looking for a way to go back to Xubuntu's version too. 

~ Apparently the Trash, File System, and Home folders are permanent additions to the standard Xfce desktop (and apparently it was controversial of Xubuntu devs to remove them!). Personally I like clean desktops. Plus, my desktop icons no longer update when I delete/add a file to the desktop, so that's no good.

~ Suddenly my network manager is root only. It used to be like that with Ubuntu, but when I installed Xubuntu I rather appreciated that it was easier to change networks. Ahh well.

~ Compositing slows down my poor five year old computer too much, so no shadows/transparency for me. Plus I've decided I'm not a fan of transparent windows. They confuse me. But I guess I can pull out some Aero themes and freak people out if I feel so inclined :rolleyes: 

~ My USB drive registers, but as read only. I think I can fix this one.

On the up side, everything else seems to work just fine :) ie. exactly the way it used to. So I might just stick with this until Feisty and a new laptop come spring.

- Phi

---

### Post by Rommidze on 2007-01-31
Due to lack of the native, I manualy rebuilded [_xfce 4.4.0 packages for Ubuntu edgy_]("http://tech.tolero.org/blog/en/linux/xfce-440-packages-for-ubuntu-edgy") from Ubuntu fiesty reposiory. This is a good way to install xfce 4.4.0 to your edgy - later on whole system update to fiesty it will be easily rulled. This will not happen if you will install via official xfce.org installer.

---

### Post by videodrome on 2007-01-31
I like it, and the desktop icons can easily be removed like this:
Create the file
~/.config/xfce4/desktop/xfdesktoprc to look like this:

[file-icons]
show-filesystem=false
show-home=false
show-trash=false
show-removable=false

You can set ones you want hidden to 'false'.
If an entry is omitted, it defaults to 'true'.  You will need to restart
xfdesktop to make the settings take effect.

---

### Post by locosmurf on 2007-02-10
> **detyabozhye said:**
> You can choose between the Xfce panel and Engage from Enlightenment DR17 there.

How would I install Engage?

---

### Post by detyabozhye on 2007-02-11
> **locosmurf said:**
> How would I install Engage?

In Xubuntu? I dunno. I haven't tried myself, but a lot of people have reported that it's not too easy to do. In that distro? Should be an option.

---

