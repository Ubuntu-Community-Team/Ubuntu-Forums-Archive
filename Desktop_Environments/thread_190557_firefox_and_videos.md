---
title: "firefox and videos"
date: 2006-06-06
forum: Desktop Environments
---

### Post by shiznatix on 2006-06-06
Howdy!

Ok I am trying to get the mplayer plugin for firefox to work properly but alas, no success. I have installed mozilla-mplayer, mplayer, I upgraded firefox, I even installed some totem thing to no avail.

Every time I go to a site with some sort of video like ebaumsworld.com it just does the 'you need additional plugins' firefox dance.

Oddly I got everything working on my desktop by just running automatix but my laptop is where I am having the problems. All these videos play fine if I download them and play them in totem or whatever.

Help please.

---

### Post by Emx on 2006-06-06
[QUOTE=shiznatix]Howdy!

Ok I am trying to get the mplayer plugin for firefox to work properly but alas, no success. I have installed mozilla-mplayer, mplayer, I upgraded firefox, I even installed some totem thing to no avail.

Every time I go to a site with some sort of video like ebaumsworld.com it just does the 'you need additional plugins' firefox dance.

Oddly I got everything working on my desktop by just running automatix but my laptop is where I am having the problems. All these videos play fine if I download them and play them in totem or whatever.

Help please.[/QUOTE]

It should work if you have installed right packages and if you have needed version of firefox (maybe you tried to install mplayer plugin for firefox, i suppose 1.5, and you may be using older version, not compatible)...Try to check all these problems...

---

### Post by shiznatix on 2006-06-06
my firefox version is 1.5.0.3 and I tried to even upgrade my mozilla-mplayer with apt-get and it said it is the newest version.

---

### Post by eeclark on 2006-06-06
did you close the browser and reopen it?

---

### Post by shiznatix on 2006-06-06
:) as often as I am sure that actually fixes the problem yes, I restarted the browser, rebooted the computer, all of the standard stuff.

---

### Post by mrtrick on 2006-06-06
Have you tried installing it using Automatix? That seemed to make the mplayer firefox plugin work excellent for me.

---

### Post by msak007 on 2006-06-06
What do you get when you type ```
about:plugins
``` in the address bar? It should open a page with a section for each plugin installed, and you should see a section in there for mplayer. Most likely it's missing if the videos don't work, so do that and post the output of what you get.

---

### Post by shiznatix on 2006-06-06
after reading that no, the plugin does not exist.

Why? I tried to look at the mplayerplug-in site and install the stuff manually but thats a bit out of my league right now. Why won't it auto-install when I use apt-get? Any easy way to do this?

---

### Post by arizonagroovejet on 2006-06-06
FWIW I have used mplayer-plugin in the past but now use  totem-xine-firefox-plugin as I find it more reliable. Try installing totem-xine-firefox-plugin and libxine-extracodecs. Remove the mozilla-mplayer package if you have that installed.  

Also, to view the videos at ebaumsworld.com videos I found I needed to install the  w32 codecs.
See [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for details.

hth.

---

### Post by shiznatix on 2006-06-06
[QUOTE=arizonagroovejet]FWIW I have used mplayer-plugin in the past but now use  totem-xine-firefox-plugin as I find it more reliable. Try installing totem-xine-firefox-plugin and libxine-extracodecs. Remove the mozilla-mplayer package if you have that installed.  

Also, to view the videos at ebaumsworld.com videos I found I needed to install the  w32 codecs.
See [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats) for details.

hth.[/QUOTE]

This did not work sadly. The same problem exactally.

---

### Post by msak007 on 2006-06-06
Just out of curiosity, are you using Breezy or Dapper, and did you install Firefox from the repositories or manually from source?

---

### Post by shiznatix on 2006-06-06
I am using dapper and I got firefox from the repositories.

---

### Post by arizonagroovejet on 2006-06-06
[QUOTE=shiznatix]I am using dapper and I got firefox from the repositories.[/QUOTE]

Same as me, and for me it works. Huh. Can you post a screenshot of the message that comes up? Might help in diagnosis.

---

### Post by shuttleworthwannabe on 2006-06-06
This may not be exactly what you are looking for; I have been back and forth with this issue as well. Wht I discovered is the sequence of multimedia codecs installations. I installed the media players and then launched them one by one (to create a hiddem profile folder in ~/)
Then installed the w32codecs.

Automatix for some reason works fine, and I think it does things differently.
Thanks

---

### Post by msak007 on 2006-06-06
I'm not sure what the problem you're having is then. When I installed Firefox, I downloaded it from Mozilla's web site and extracted it to /opt/firefox. The mplayer plugins package installed the plugins to /usr/lib/mozilla-firefox/plugins/ (I also found them in /usr/lib/firefox/plugins/). What I had to do was copy all the files in that folder to /opt/firefox/plugins. After that mplayer worked. Open a terminal and type ```
find -name mplayer*
``` and then look for any entries that contain Firefox.

---

