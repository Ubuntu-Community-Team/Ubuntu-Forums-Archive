---
title: "Movie player crashes:How do I change default applicatn without right-click-properties"
date: 2009-06-16
forum: General Help
---

### Post by jesseg on 2009-06-16
The .MOV files I wish to play cause the default movie player to load then crash. Mplayer plays them fine, but mplayer is not the default player.

To save from having to right-click and choose "open with mplayer" each time, I would like to change the default application for .MOV to mplayer instead of whatever's there now.

But, since the default player crashes when opening these MOV files, it also crashes when I right click on the MOV file and click "Properties".  The dialog crashes and the icons vanish from my desktop... (Probably because the player crashes even when asked to extract a thumbnail I suppose.)

So, how can I change the default handler application for *.MOV without actually launching the default player? 

I just now thought of making an empty file named something.mov and right-clicking that, hopefully that wouldn't crash the player.

Feel free to be technical - been using and programming in Linux (Slackware) for years, just recently put Linux Mint 7 on a friend's laptop. (Would have put Ubuntu but didn't have a CD handy on short notice.)

Anyway, I'm sure not above editing some file or rooting around at the command line if that's what it takes.

Thanks very much,

-Jesse

(PS: Yes, I know how to spell Application. Ran out of room in title.)

---

### Post by mc4man on 2009-06-16
When you say mplayer do you mean the 'default' gui of mplayer (gmplayer)

> just now thought of making an empty file named something.mov and right-clicking that, hopefully that wouldn't crash the player.



That should work just fine and ignore or ck. out  below (mimeapps.list and the applications folder can be very useful to know about particularly for custom definitions 

What you can do is open mimeapps.list and edit the line for quicktime video if it exists or add it if it doesn't. (either browse or from terminal.

Ex.
```
gedit  ~/.local/share/applications/mimeapps.list

```
. 
I believe this line is for .mov (note that lines are added to mimeapps.list as 'defaults' for file types are added or default actions on media. On a fresh install the list doesn't exist.

> video/quicktime=

On my system I don't have gmplayer, so the gui would be smplayer.desktop and the line looks like this. (first listed is default
> 
video/quicktime=smplayer.desktop;vlc.desktop;

So figure out what mplayer.desktop to use, look for the line, if not there then create.



Ex. of mine on a recent hardy install (not many lines added yet

> [Added Associations]
x-content/audio-cdda=amarok-cd.desktop;rhythmbox.desktop;
x-content/video-dvd=vlc.desktop;totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/software=nautilus-autorun-software.desktop;
application/x-flash-video=vlc.desktop;
inode/directory=kde-amarok.desktop;smplayer.desktop;mplayer.desktop;vlc.desktop;
application/x-extension-mlp=vlc.desktop;gedit.desktop;
application/x-extension-txz=gedit.desktop;
video/3gpp=totem-xine.desktop;
audio/x-tta=vlc.desktop;userapp-mplay -WFEFVU.desktop;
application/x-trash=gedit.desktop;
application/x-executable=wine.desktop;
application/x-shorten=smplayer.desktop;
audio/x-ms-wma=userapp-mplay -Z54MVU.desktop;userapp-mplay -XMCLVU.desktop;mplayer.desktop;
audio/mpeg=userapp-mplay -QD2QVU.desktop;
audio/x-wav=userapp-mplay -ZMORVU.desktop;
application/x-shellscript=gedit.desktop;
application/xspf+xml=vlc.desktop;
[COLOR="Blue"]video/quicktime=smplayer.desktop;vlc.desktop;[/COLOR]

---

### Post by jesseg on 2009-06-16
> **mc4man said:**
> When you say mplayer do you mean the 'default' gui of mplayer (gmplayer)


I don't know. All I know is that when I double click the *.MOV in question, a player (which I think is titled "Movie Player" in the title bar) pops up and after a couple seconds vanishes.

But when I pop open a shell prompt and type mplayer "getting started.mov" it plays like a charm!

ffplay also plays it just fine. (which I got with apt-get install ffmpeg.)

Anyway, I'll try what you suggest and report back.

Thank you very much!

-Jesse

---

### Post by drs305 on 2009-06-16
There is also System > Preferences > Preferred Applications: Multimedia.  If your preferred app isn't an option you can use the custom command to point to the app of your choice.

---

### Post by mc4man on 2009-06-16
> I don't know. All I know is that when I double click the *.MOV in question, a player (which I think is titled "Movie Player" in the title bar) pops up and after a couple seconds vanishes.

look in Applications -> sound & video. you should see mplayer listed. Open it and see if it can play your .mov

When you go mplayer in the terminal your using the command line version, which if desired can be set as a default by creating a custom definition.
Custom definitions become userapp.desktops, the format being 
userapp-Appname-xxxxxx.desktop

Anyway if you simply made a text file, named it 1.mov, right clicked on -> properties -> open with and choose mplayer then the gui version of mplayer would become the default for .mov


While it can be done, setting a command line app as a  default for a file type can present a few challenges and limitations.

The first is without opening it in a terminal you'll have absolutely no control, the file will play with the 'player' in the background. It's better in these cases to use a gui when possible.
there are other small issues so no need to go thru atm.

---

### Post by jesseg on 2009-06-18
Thank you all very much for  the helpful replies!

I just created an empty file named something.mov, right clicked it, selected properties, and chose mplayer from the list, and it works perfectly now!

Thanks again,

-Jesse

---

