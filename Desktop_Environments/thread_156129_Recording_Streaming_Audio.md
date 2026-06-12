---
title: "Recording Streaming Audio"
date: 2006-04-06
forum: Desktop Environments
---

### Post by Jeeevs2001 on 2006-04-06
Having read this post: 

[http://ubuntuforums.org/showthread.php?t=28356](http://ubuntuforums.org/showthread.php?t=28356)

I was very excited to see I would (at last) be able to download some interesting radio stations from the BBC. However having spent 2 - 3 hours last night trying to get it to work i couldn't get it right. Has anyone been able to get a stream from the BBC to work? I could not get it to stream or to record. 

However, if i navigate to the right page with Firefox, it uses the mplayer plugin and plays the stream ok. From here i copied the link to streamtuner (right click, copy link) but it wouldn't work! 

Any help would be greatly appreciated!

---

### Post by Furry_Fighter_20x66 on 2006-04-08
In the file /etc/mplayerplug-in.conf add the lines:

keep-download=1
dload-dir=$HOME/Streams

and add a directory called "Streams" to the home directory of the user account you will be listening to streams with on the net.

Now everytime Mplayer plays back a stream from the internet, a copy will be saved to that directory. Best to check it every few days and clean it out though ;)

---

### Post by Edward The Bonobo on 2006-04-11
I have a similar problem.  I'm trying to rip a .rm stream to .mp3.  Streamtuner will play it, but nothing happens when I record.  Any ideas?

---

### Post by dnccnd on 2006-04-15
[QUOTE=Furry_Fighter_20x66]In the file /etc/mplayerplug-in.conf add the lines:

keep-download=1
dload-dir=$HOME/Streams

and add a directory called "Streams" to the home directory of the user account you will be listening to streams with on the net.

Now everytime Mplayer plays back a stream from the internet, a copy will be saved to that directory. Best to check it every few days and clean it out though ;)[/QUOTE]

I have tried to change the text of the file mplayerplug-in.conf, but it wouldn't allow me to do so. Do you have any idea why?

I usually listen to a radio that stream in Real Player or Windows Media Player. The second option is not available for me in Ubuntu, is it? The first option works with Real Player in Ubuntu, but can I record this streaming? I tried to paste the link in Streemtuner but this application doesn't open the stream.

Thanks for any suggestion you might think of...

---

### Post by BrianMahoney on 2006-04-17
[QUOTE=dnccnd]I have tried to change the text of the file mplayerplug-in.conf, but it wouldn't allow me to do so. Do you have any idea why?

I usually listen to a radio that stream in Real Player or Windows Media Player. The second option is not available for me in Ubuntu, is it? The first option works with Real Player in Ubuntu, but can I record this streaming? I tried to paste the link in Streemtuner but this application doesn't open the stream.

Thanks for any suggestion you might think of...[/QUOTE]

When you attempted to edit the file, did you use sudo? Try:

sudo gedit /etc/mplayerplug-in.conf

then edit the file.

As far as the Windows Media Player files go, MPlayer should be able to handle those fine. If you're not comfortable configuring plug-ins, try using automatix.

[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

Hope this helps

---

### Post by Edward The Bonobo on 2006-04-18
I'm on the verge of writing a HowTo on this...

What I discovered here: [http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf](http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf)

Is that you need a combination of 
[LIST]
[*][COLOR="DarkSlateBlue"]Vsound[/COLOR] - to capture the .rm stream
[*][COLOR="darkslateblue"]Sox[/COLOR] - Once you've quit, it converts the captured stream to .wav (yeah, I know!  ***Hell*** of a large file!)
[*][COLOR="darkslateblue"]Lame[/COLOR] - Converts the .wav to .mp3 - or format of your choice
[/LIST]

This has all worked with me so far...up to a point.  The only wrinkle is that I've got a tiny, tiny hard drive, and you need twice the space of the resulting .wav, otherwise Vsound just crashes out after the first couple of seconds of recording but doesn't tell you.

Then, if you want, you can chop up the .mp3 into more manageable chunks with [COLOR="darkslateblue"]Audacity [/COLOR]- only I've had problems getting this from the Repositories because of a missing dependency.

One potential difficulty...finding the URL of the stream.  There seem to be various ways that sites use to hide them.  Here: [http://www.npr.org/templates/story/story.php?storyId=4834385](http://www.npr.org/templates/story/story.php?storyId=4834385) they've put inside a .smil file (Standard Integrated Multimedia Language) - but you just peek inside with a text editor.

On the BBC R4 site, it looks like they give the URLs for .ram streams if you select the 'play in stand-alone realaudio player' option - but I haven't tested that for this method.  There's more on digging out URLs, and on other recording methods here: [http://swen.antville.org/stories/735413/](http://swen.antville.org/stories/735413/)

---

