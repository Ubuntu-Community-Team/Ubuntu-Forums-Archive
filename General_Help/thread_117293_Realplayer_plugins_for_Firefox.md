---
title: "Realplayer plugins for Firefox"
date: 2006-01-14
forum: General Help
---

### Post by adana on 2006-01-14
I have searched the forum for this but I can't find a clear/consistent answer.

1)  I downloaded and installed firefox 1.5 from the command line.

2) I downloaded and installed realplayer 10 from the command line.

I did not use apt-install for either -- just ran the bin or tar files. 

Both installed sucessfully and work from the command line.  Of course, GNOME is not aware of either.

So I have 2 questions:

1) How do I register in GNOME an application I install manually?  With apt-install? But won't apt-install try to download and reinstall it over again?

2) How do I link realplayer into firefox since I installed both manually? Looks like I have to create symbolic links from firefox to realplayer?  But the mozilla website doesn't say how -- I can't find clear instructions for this.

Thanks for any help!

---

### Post by Mr_Grieves on 2006-01-14
I did this to get it working.

1) [www.ubuntuguide.org/#realplayer](www.ubuntuguide.org/#realplayer)
2) [http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer](http://www.real.com/linux/?rppr=rnwk&src=040104freeplayer)

It just worked..

---

### Post by adana on 2006-01-14
That's my question, though. If I use apt-install, won't it download and install all over again? I already installed realplayer.

I just need firefox to stop defaulting to totem, and use realplayer instead.

---

### Post by mlalkaka on 2006-01-14
This should do the trick.
The code below assumes that the variable...
a) FIREFOX_DIR is the absolute path to where Mozilla Firefox is installed.
b) REALPLAYER_DIR is the absolute path to where RealPlayer 10 is installed.

```

# Go to the Mozilla Firefox plugins directory:
cd $FIREFOX_DIR/plugins

# Backup the Totem plugins (backups are always a good idea):
mv libtotem_mozilla.a libtotem_mozilla.a_backup
mv libtotem_mozilla.la libtotem_mozilla.la_backup
mv libtotem_mozilla.so libtotem_mozilla.so_backup  
mv libtotem_mozilla.xpt libtotem_mozilla.xpt_backup

# Create links to the RealPlayer 10 plugins:
ln -s $REALPLAYER_DIR/mozilla/nphelix.so
ln -s $REALPLAYER_DIR/mozilla/nphelix.xpt

```

For your convenience, I have also attached the BASH script [ATTACH]5332[/ATTACH] to do this work for you (I had to add the .txt extension to upload it). To use the script, download it to a directory and do the following in that directory:
```

chmod +x InstallRealPlayerPlugins.txt
sudo ./InstallRealPlayerPlugins.txt --help

```
That will give you further instructions.

[CENTER]:) I hope that helps :)[/CENTER]

---

### Post by adana on 2006-01-15
Well, very frustrating.  I have created the links.  Here are my directories:

FIREFOX plugins:

-rwxr-xr-x  1 adana adana 19224 2005-11-11 19:00 libnullplugin.so
lrwxrwxrwx  1 adana adana    47 2006-01-14 15:23 nphelix.xpt -> /apps/realplayer/RealPlayer/mozilla/nphelix.xpt
lrwxrwxrwx  1 adana adana    46 2006-01-14 15:23 nphelix.so -> /apps/realplayer/RealPlayer/mozilla/nphelix.so

Still, when clicking on generic links on c-span, totem is invoked instead of realplayer.

If I click on "watch with realplayer", then realplayer properly opens.

Any ideas?

Thanks!

---

### Post by mlalkaka on 2006-01-15
I went to the C-SPAN website to get an idea of what you were talking about, and I'm a little confused now :???: . When you say "totem is invoked instead of realplayer", do you mean that Totem Media Player opens in a *new window*, or do you mean that the Totem *plugin* is invoked instead of the RealPlayer plugin? 

For example, when you go [here]("http://www.c-span.org/homepage.asp?Cat=Current_Event&Code=Bush_Admin&ShowVidNum=15&Rot_Cat_CD=BA&Rot_HT=&Rot_WD=&ShowVidDays=365&ShowVidDesc=&ArchiveDays=30"), if you click on a "Recent Program", it will open a separate media player.
But if you go to one of the "Live Streams" from the C-SPAN homepage, it will invoke a media player plugin.

The instructions I had given you were for configuring which plugin will open (the "Live Streams" case), not which media player will open.

---

### Post by adana on 2006-01-15
Yes, you are correct. Totem opens as a separate application and fails to play the video.

Realplayer works on the c-span live stream. So I guess the plugins are working!

So, how to I change the default player that opens when clicking on that 
"recent program" link? I see this file:  **/usr/share/applications/defaults.list**

Do I have to edit this file manually?

---

### Post by mlalkaka on 2006-01-16
[QUOTE=adana]
So, how to I change the default player that opens when clicking on that 
"recent program" link? I see this file:  **/usr/share/applications/defaults.list**

Do I have to edit this file manually?
[/QUOTE]

You can try editing that file, but I believe that file is for GNOME; unfortunately, Ubuntu hasn't merged the default application selection systems for GNOME and Firefox. I believe Firefox uses the mailcap system (~/.mailcap, /etc/mailcap, /etc/mime.types). If you look into these mailcap-related files, you will see some references to man pages that will help you edit the default applications. Also read the comments /etc/mailcap. 

By the way, on my system, Totem is able to watch those RealMedia files, including the ones on [http://www.c-span.org](http://www.c-span.org). I believe if you look in the file ~/.gnome2/totem_config, you can edit the location of the RealPlayer codecs to where they are located. Find the string "decoder.external.real_codecs_path".

---

### Post by adana on 2006-01-16
Hmm...I only have a directory called totem-addons. Nothing under that directory. 

Can't believe I can't change the default to realplayer or gxine.

---

### Post by Dafydd on 2006-04-19
[QUOTE=mlalkaka]This should do the trick.
The code below assumes that the variable...
[/QUOTE]

Tried this to no avail. It's so frustrating. Sometimes ubuntu seems like a long trail of problems (wireless, dns nameservers and now realplayer for firefox).

I don't want to go back to Windows (and will not) but still annoyed after losing so much time on this.

I've got around the realplayer/firefox problem  by adding links to the filename.rpm etc on bbc.co.uk. 

Dafydd

---

### Post by ruzle0 on 2006-04-20
hi i've had a look round the net and i'm in a similar situation.
on the c-span site recent programs send you to a rtsp:// protocol link, 
this you can then be bound to realplayer by adding the following line 

user_pref("network.protocol-handler.app.rtsp","realplay*");
*[or the path to realplayer]

to the file prefs.js
on my computer located is in ~/.mozilla/firefox/0tn2kn0b.default/
to edit this you must first close firefox or it will be over writen on exit
[adapted from here]("https://www.redhat.com/archives/fedora-list/2004-May/msg00214.html")

not sure how much of a hack this is or if there's an easier way but it works for c-span.

---

