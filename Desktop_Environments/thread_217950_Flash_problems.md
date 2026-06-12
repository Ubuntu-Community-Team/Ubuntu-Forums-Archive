---
title: "Flash problems"
date: 2006-07-17
forum: Desktop Environments
---

### Post by ndyguy on 2006-07-17
I believe I'm having Flash problems.  I have Dapper Drake with Firefox 1.5.0.4.  The reason I'm not sure is when I go to this site [http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/") it shows that Flash player is working, but Shockwave player is not installed (even though I've read already that Linux doesn't have Shockwave).  In case this is expected for Ubuntu this is the original site that made me think I had problems: [http://www.tiesto.com/]("http://www.tiesto.com/")  When I load this page the animations work but the audio player doesn't.  It shows it buffering at 0% and doesn't change.  Also tried this site [http://www.myspace.com/tiesto]("http://www.myspace.com/tiesto")  The player just sits there saying "playing", but no audio.  (By the way, I'm sure my speakers are hooked up correctly and work).

So this is what I've already done:
I've been to the RestrictedFormats page and made sure I had all the packages in the How to Make Things Work in a Hurry and Enable Other Non-Free Formats sections.  I've entered the code under the w32codecs section in the terminal.  After I enter that it says: 
Unpacking replacement w32codecs ...
Setting up w32codecs (20060611-0.0) ...
something@something-desktop:~$
I've tried totem-xine and totem-gstreamer packages with no change (with mozilla plugins respectively).  I've got mplayer (with mozilla plugin).  Maybe a conflict with having mplayer _and_ totem at the same time?  I have flashplugin-nonfree package.  I entered sudo update-flashplugin in the terminal and got "installation failed," so I stopped there. 

Sorry if this is too long; just wanted to be thorough. Any help would be appreciated.

---

### Post by bruenig on 2006-07-17
make sure you have the [extra repositories enabled](https://help.ubuntu.com/community/Repositories/Ubuntu). Then do:
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Silver Streak on 2006-07-17
> **ndyguy said:**
> I believe I'm having Flash problems.  I have Dapper Drake with Firefox 1.5.0.4.  The reason I'm not sure is when I go to this site [http://www.adobe.com/shockwave/welcome/]("http://www.adobe.com/shockwave/welcome/") it shows that Flash player is working, but Shockwave player is not installed (even though I've read already that Linux doesn't have Shockwave).  In case this is expected for Ubuntu this is the original site that made me think I had problems: [http://www.tiesto.com/]("http://www.tiesto.com/")  When I load this page the animations work but the audio player doesn't.  It shows it buffering at 0% and doesn't change.  Also tried this site [http://www.myspace.com/tiesto]("http://www.myspace.com/tiesto")  The player just sits there saying "playing", but no audio.  (By the way, I'm sure my speakers are hooked up correctly and work).

So this is what I've already done:
I've been to the RestrictedFormats page and made sure I had all the packages in the How to Make Things Work in a Hurry and Enable Other Non-Free Formats sections.  I've entered the code under the w32codecs section in the terminal.  After I enter that it says: 
Unpacking replacement w32codecs ...
Setting up w32codecs (20060611-0.0) ...
something@something-desktop:~$
I've tried totem-xine and totem-gstreamer packages with no change (with mozilla plugins respectively).  I've got mplayer (with mozilla plugin).  Maybe a conflict with having mplayer _and_ totem at the same time?  I have flashplugin-nonfree package.  I entered sudo update-flashplugin in the terminal and got "installation failed," so I stopped there. 

Sorry if this is too long; just wanted to be thorough. Any help would be appreciated.

Keep in mind, that the Flash Player for Linux is only at version 7, and I've noticed that many things don't show up / animate / whatever properly, because most developers are exporting to Flash 8 files now. If you watch Homestarrunner, you'll notice that it's fine, because the developers export the file as a lower version (5? I'm not sure).

You could try getting Flash 8 to run under WINE, but it's a bit of work...

SS

---

### Post by ndyguy on 2006-07-18
Making progress!!  I enabled the extra repositories and tried what bruenig said, and terminal said I already have the newest version of flashplugin-nonfree, but when I tried the myspace page I mentioned above it worked.  I still can't get [http://www.tiesto.com/]("http://www.tiesto.com/") to play audio.  Any more suggestions?

---

