---
title: "Editing video, creating DVDs"
date: 2006-10-05
forum: Desktop Environments
---

### Post by mssever on 2006-10-05
I have a series of ten 90-minute TV programs that I recorded onto DVD. I want to edit the video (basic stuff like deleting extraneous frames), make a nice menu to replace the ugly one the recorder created, and burn the whole shebang to DVD. (BTW, the copyright holder allows their stuff to be redistributed, so I'm not trying to do anything illegal here.)

What software do I need to do this, and can someone point me to some appropriate documentation? I've never messed with video before, so I need to start from zero.
[FONT=Arial Narrow][SIZE=2][COLOR=Gray][B]
Additional Info:[/B]

I've tried to rip the DVD using dvd::rip. As far as I can tell, it rips OK, but it won't let me transcode to MPEG (do I even need to do this?) without changing the aspect ratio, etc--since I'm writing back to DVD, I don't want to change anything.

I've tried editing with kino, but the documentation seems to only deal with using DV. When I try to open a video file (either something on the DVD itself, a ripped file, an AVI, or an MPG), kino complains thus:
> This is not a DV file. Do you want to import it?
<Hit OK, then...>
The playlist is empty and the default preferences for video creation have not been specified - aborting.

Failed to load media fileI can't find anything in the preferences about defaults for video creation. What's wrong?[/COLOR][/SIZE][/FONT][SIZE=2][COLOR=Gray]
[/COLOR][/SIZE]

---

### Post by cd-r80 on 2006-10-05
Try Avidemux for edit & K3b for burning.

---

### Post by reclusivemonkey on 2006-10-05
> **cd-r80 said:**
> Try Avidemux for edit

You can, if you really want to use Kino, open your videos in Avidemux and export the frames as JPEGs to import into Kino. However, this will depend on how much HD space you have and how much you want to use Kino. I use this method for making videos of my goals in PES5. Not ideal, but it does work.

---

### Post by mssever on 2006-10-09
Thanks for the help. Here's what I've been doing (in case someone else has similar issues--or in case I forget :)):

DVD::rip is unnecessary. Copying the video_ts directory from the DVD does the job of ripping the video nicely, without having to worry about all of dvd::rip's craziness (such as trying to force you to chance the aspect ratio of your video).

I'm using avidemux to cut cruft from the video files. Unfortunately, the only editing avidemux can do is cutting. But that's all I need at this point. The settings I use are: 
Video: DVD (lavc)
Audio: Toolame
Format: MPEG PS A+V

I create the menu backgrounds in GIMP and save as JPEG, not PNG, despite the fact that PNG is superior for computer graphics. The dvdauthor tools (I presume that they're the culprit) convert PNGs to JPG using a low quality setting that introduces artefacts around the text on the background. Saving as JPG reduces these artefacts, but doesn't eliminate them.

I make the menus and assemble the DVD using DVDStyler (see [this tutorial]("http://www.pclinuxonline.com/wiki/CreatingVideoDVDCreate")). DVDStyler is a bit moody, but it's better than Tovid and I don't know of any other alternatives.

---

### Post by wishyjr on 2006-10-31
hi guys, have you possibly found a program similar to DVDStyler that supports more video formats like AVI? bar the lack of compatibility, i think that DVDStyler is really cool.

cheers anyway

---

### Post by BLTicklemonster on 2007-04-07
Excellent. Maybe now I can take all the episodes of Reboot I have and make a complete dvd set of all 4 seasons.

Thanks!

---

### Post by mister_p_1998 on 2007-04-08
Personally,  I would reccommend editting with ProjectX to chop out the ads and crap, then demux it as audio & video tracks, then load back into Avidemux, save as DVD Mpg, and finally create an ISO with DVDAuthor. I dont know if you can create Menu's with DVDAuthor, but you can put chapters in at a given length eg every 10 mins. then just burn the iso with K3B.
Steve

---

### Post by Brandel Valico on 2007-04-21
I use a program called mandvd to create and burn video dvd's myself. It allows you to make the menu and add music as well as converts the files into the correct formats all in one program. It also burns them.

[http://kde-apps.org/content/show.php?content=38347](http://kde-apps.org/content/show.php?content=38347)

Actually nix that. Just tried it again after awhile since having done so. It seems that it nolonger transcodes the Audio correctly.

---

### Post by wrongo on 2007-06-17
exactly. what the fuh...? the audio is awful. i had this problem on devede but fixed it typing "-afm ffmpeg" in the 'advanced>misc>mencoder' applet - but so far only mandvd can make menus - would LOVE to know fixes for audio 'white noise' issue in mandvd if anyone knows

---

### Post by Kujiro on 2008-02-17
I'm a novice and nave a question - how could they create a vid like this.

Low passing plane [http://www.youtube.com/watch?v=WsirCoxcfo4](http://www.youtube.com/watch?v=WsirCoxcfo4)

That guy explains everything but I need a more profound advice.

---

