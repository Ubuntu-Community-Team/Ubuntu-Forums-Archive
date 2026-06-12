---
title: "Totem unable to play DVDs"
date: 2006-07-25
forum: Desktop Environments
---

### Post by Quitch on 2006-07-25
Hey there,

Rather new to Ubuntu.  Needed a machine to play DVDs, but couldn't be bothered to dig out my XP CD, so perfect excuse to try Ubuntu I thought.

Anyway, trying to get the Totem Movie Player to play a DVD for me.  I know by default that CSS protected discs aren't supported, so after some searching I downloaded Automatix and installed the AUD - DVD codecs and CheckGmail via the GUI as a user-admin.

My DVDs didn't seem to be mounting anymore, so I restarted.

DVD now mounted, but on loading Totem and telling it to play the DVD I got the following:

"Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it"

Yet having looked at the package manager it seems Totem should play DVDs, and the AUD-DVD codec thing installed by Automatix should, I believe, take care of the CSS side of things.  Yet it doesn't seem to be working and I'm a little stumped.

I couldn't find CheckGmail after installation either.

---

### Post by catlett on 2006-07-25
For dvd playback capability you need this as well

```
sudo apt-get install libdvdcss2
```

P.S. I don't know what automatix installs but here is a list of codecs you should have
```
sudo apt-get install libxine-extracodecs 
``````
sudo apt-get install gstreamer0.10-ffmpeg
``````
 sudo apt-get install gstreamer0.10-gl
``````
 sudo apt-get install gstreamer0.10-plugins-base
``` ```
sudo apt-get install gstreamer0.10-plugins-good 
``````
sudo apt-get install gstreamer0.10-plugins-bad
``` ```
sudo apt-get install gstreamer0.10-plugins-bad-multiverse 
``````
sudo apt-get install gstreamer0.10-plugins-ugly 
``````
sudo apt-get install gstreamer0.10-plugins-ugly-multiverse
```

Plus you should get the win32codecs and basic mp3 and vorbis support
```
wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
```
```
sudo dpkg -i w32codecs_20060611-0.0_i386.deb
```
```
sudo apt-get install mpg321 vorbis-tools
```

P.S.S The mpg321 and vorbis-tools are the packages that give you (what I think is cool) the ability to play a file by hovering your mouse over the file. It is the biggest WOW I get from windows users when they look at my linux desktop (nevermind the security and stablity, they love the hover/play a file on your desktop without opening itunes or winamp, go figure :D )

---

### Post by JoWilly on 2006-07-25
You might also want to try xine (and totem-xine) wich has the best support for dvd menus and more codecs.

And as said above, don't forget libdvdcss.

---

### Post by arnieboy on 2006-07-25
> **Quitch said:**
> Hey there,

Rather new to Ubuntu.  Needed a machine to play DVDs, but couldn't be bothered to dig out my XP CD, so perfect excuse to try Ubuntu I thought.

Anyway, trying to get the Totem Movie Player to play a DVD for me.  I know by default that CSS protected discs aren't supported, so after some searching I downloaded Automatix and installed the AUD - DVD codecs and CheckGmail via the GUI as a user-admin.

My DVDs didn't seem to be mounting anymore, so I restarted.

DVD now mounted, but on loading Totem and telling it to play the DVD I got the following:

"Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it"

Yet having looked at the package manager it seems Totem should play DVDs, and the AUD-DVD codec thing installed by Automatix should, I believe, take care of the CSS side of things.  Yet it doesn't seem to be working and I'm a little stumped.

I couldn't find CheckGmail after installation either.
there was a bug in the last version of automatix which prevented the installation of DVD codecs.
Upgrade to the latest version of automatix and install AUD-DVD codecs again.

---

### Post by Anduu on 2006-07-25
> **JoWilly said:**
> You might also want to try xine (and totem-xine) wich has the best support for dvd menus and more codecs.

And as said above, don't forget libdvdcss.

Yup install totem-xine....no matter what I did totem-gstreamer refused to play DVD's even though I could play them with just about any othermedia player.

---

### Post by Quitch on 2006-07-26
What's the xine signify?

---

### Post by Quitch on 2006-07-26
> **arnieboy said:**
> there was a bug in the last version of automatix which prevented the installation of DVD codecs.
Upgrade to the latest version of automatix and install AUD-DVD codecs again.

I had only downloaded Automatix say, 30 minutes before my post.  Was the new version released since then?  I assume that running as a user-admin is enough to install this stuff?

Where would Check(G?)mail appear once installed?  I assumed I'd see an icon or something.  Do I need to track down the folder?

Thanks for your help.

---

### Post by JoWilly on 2006-07-26
> **Quitch said:**
> What's the xine signify?

I don't understand your question.

Did you mean : what does xine signify ?

Xine is a media player, totem-xine uses xine as its backend to play media...

---

### Post by shawnrgr on 2006-07-26
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability)

---

