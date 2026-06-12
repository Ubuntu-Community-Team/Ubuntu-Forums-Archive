---
title: "Ubuntu spills the pr0n"
date: 2010-02-08
forum: Desktop Environments
---

### Post by Alex Libman on 2010-02-08
These aren't what you'd call normal privacy or usability flaws, but nonetheless something to consider:


[LIST]
[*]Ubuntu could use an equivalent of the Windows [CCleaner]("http://en.wikipedia.org/wiki/CCleaner") utility, which in addition to Computer Janitor type functionality would provide a single place for clearing any or all user privacy data: all popular Web browsers, media player histories, shell histories, thumbnails cache, trash (which most users who don't keep that panel item simply forget about), etc, etc, etc.
[/LIST]

[LIST]
[*]Gnome's "Picture folder" screensaver seems to search the entirety of the user's $HOME path for images (that might only be the case if the user deletes the default ~/Pictures folder, but I imagine that many users do).  This can be quite unexpected just by itself, with the user thinking it will only display ~/pics and returning to find his laptop left in a public place blasting through JPEG's from ~/shared/p2p/IllegalIn30states/; but what makes this flaw most insidious is the "Picture folder" screensaver choice being buried on the bottom of the scrollable list, while the "Random" option is on the very top.  A user choosing a random screensaver might think he'll just get a different cutesy animation every time, without considering the possibility of it showing off his porn collection while he's away from his desk.
[/LIST]

[LIST]
[*]When [Totem]("http://en.wikipedia.org/wiki/Totem_%28media_player%29") (v2.28.2; GStreamer 0.10.25) concludes playing a video playlist, it seems to display the first frame from the first item on the playlist until you exit Full Screen and close the Totem window.  Imagine someone starting his big-screen media center experience with a little "Girls Gone Wild" while the wife is at work, and adding the Super Bowl to the playlist after that so he doesn't have to get up from the couch an extra time.  Half-way into the game the wife comes home, brings some company over, they join in to finish watching the game together, and then suddenly, WHAM, the title shot of "Girls Gone Wild" just appears on the screen for no reason!
[/LIST]

[LIST]
[*]I think the Escape key should close Totem, same as it does the Image Viewer (Eye of Gnome), because sometimes guys watching certain kinds of movies panic when intruded upon and need all the usability aids they can get.
[/LIST]
 
:lolflag:

---

### Post by Grenage on 2010-02-08
Valid points, and cheers for the smile. ^^

---

### Post by ajgreeny on 2010-02-08
Why do you think thgat many users get rid of the Pictures folder in /home.  I would have thought that the vast majority keep it intact and store their pictures there; perhaps I'm wrong.

However I do agree that it is a bit remiss of gnome not to have some easier way to configure the Pictures Folder screensaver than is available.  If I knew how, I would try to write a simple program or script file to do it, but I'm afraid it is a bit too complicated for a oldie like me.

For anyone who wants to do it the manual way with config file edits it is simple enough, but it is not well known or findable, from memory.

[COLOR=Red]Screensaver pictures folder change; edit

/usr/share/applications/screensavers/personal-slideshow.desktop

Edit the Pictures folder configuration file:
```
sudo gedit /usr/share/applications/screensavers/personal-slideshow.desktop

```Find the line
 "exec=slideshow." To customize the location, just add "--location=PATH," where PATH is the location of your pictures, for example
```
exec=slideshow --location=/path/to/your/Pictures_folder
```

[COLOR=Black]EDIT:

Sorry folks, the bit in red above no longer is of any use.  Those files do not exist any more.  Has anyone got any idea now how you can edit the folder used for the Pictures Folder screensaver?
[/COLOR][/COLOR]

---

### Post by TenPlus1 on 2010-02-08
BleachBit is the CCleaner equivalent on linux...

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by Alex Libman on 2010-02-08
> **ajgreeny said:**
> Why do you think thgat many users get rid of the Pictures folder in /home.  I would have thought that the vast majority keep it intact and store their pictures there; perhaps I'm wrong.

A lot of users who didn't start their computer experience with Windows 95+ have gotten into a habit of organizing their files a certain way that makes sense to them.  A lot of UNIX beards are specifically turned off by title-cased directory names (even without spaces).  Some people like to divide their stuff into base-level folders like "public", "work", "family", "personal", etc, which is what makes the most sense to me.  Furthermore, most multimedia the typical user will have will come from a P2P / RSS / IMAP / IRC / NNTP / etc downloader program which will have its own path hierarchies instead of separating files as audio, video, images, ebooks, etc.


> **ajgreeny said:**
> [...]  it is a bit remiss of gnome not to have some easier way to configure  [...]

I'm sure a knowledgeable user will find ways to reconfigure everything (and encrypt any compromising files on his computer, etc), but I believe the default settings should be convenient and privacy-enabling right off the bat, since most users won't bother change them.  

n00b-friendliness was what Ubuntu's all about.


> **TenPlus1 said:**
> [http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

Awesome!  Hope it gets included in the default Ubuntu desktop install once it is stable.  (And someone who isn't banned from Wikipedia for calling Global Warming a hoax might want to [write an article / stub for it]("http://en.wikipedia.org/wiki/BleachBit").)

---

### Post by pastalavista on 2010-02-08
I don't keep anything in my Pictures folder except specific pics for the screensaver and backgrounds. I made an Images folder for everything else.

As for Totem movie player, don't select the 'repeat' option.. and alt-f4 is almost as quick as escape if you have a thumb. :P

---

