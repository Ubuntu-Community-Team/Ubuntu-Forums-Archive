---
title: "How do I convert ogg to mp3 &amp; rip to mp3"
date: 2006-07-25
forum: Desktop Environments
---

### Post by notiones on 2006-07-25
Let me start by apologizing for my lack of knowledge on this subject. I have lost a significant portion of my hearing and as a consequence do not play music on my computers. 

I setup a Gateway laptop for my 16 year old daughter with Breezy Badger. It's all good and she doens't miss Windows, but she just bought an 30GB IPOD and I am having trouble getting it all working. She is not happy and almost mentioned Wndows. I have worked hard to convert her to Linux and don't want to lose now.

The IPOD mounts no problem and gtkpod works, as far as I can tell. All of her music is in ogg format though and I need to convert it to mp3. I have no idea of where to start. I installed a program called nautilus-audio-convert, but it does nothing when asked to convert the ogg files to mp3. I need to set it up so that when she rips a cd it formats as mp3 as well. She is currently using Rythmbox. Are there plugins available for this. Some kind direction would be most appreciated.

---

### Post by encompass on 2006-07-25
sure there is a way... make sure that you can play an mp3 first..
can you do that?
And as for your daughter, good job on going with linux.  Ogg is better, but some companies like apple won't accept it.... you should feel lucky that they take mp3 and not just their own codec.
to convert anything to anything in audio I use a little prgram called lame.  You could also look into transcode.  it uses lame to convert files... and may be a little easier to use.  If you need help, I think I could even make a little script that would work on all files in a directory and convert them to mp3.  I am making a little script to do that very thing.  But to ogg. :P
Hope this helps.  I can help you mroe this evening, then I am at my linux computer.

---

### Post by reclusivemonkey on 2006-07-25
> **notiones said:**
> 
All of her music is in ogg format though and I need to convert it to mp3. I have no idea of where to start. I installed a program called nautilus-audio-convert, but it does nothing when asked to convert the ogg files to mp3. I need to set it up so that when she rips a cd it formats as mp3 as well. She is currently using Rythmbox. Are there plugins available for this. Some kind direction would be most appreciated.

I downloaded a Nautilus script to convert ogg to mp3 and it worked fine for me; was this the same thing? You have to place the script in the correct place and make it executable.

Anyhow, you may find its easier to use a GUI. There is a program called Sound Converter somewhere in the repos and it has a Gnome interface. I believe you can load all the ogg files you want into there and it will convert them to mp3. I am at work right now so I can't confirm this for sure but I will check when I get back home.

Rhythmbox _should_ rip to mp3. I recall that some of the ripping programs need you to add a custom line to gstreamer somewhere. Again, I will need to have a look when I get home. Sorry if my advice is a little hazy, I have a two and a half week year old son at home, so I don't get much sleep ATM :-S

---

### Post by gerkin on 2006-07-25
notiones

you could try "soundconverter", it has a very easy to use GUI and is in the repositories (but uses gstreamer8), make sure you have the "gstreamer0.8-lame_0.8.12-1_i386.deb" installed for mp3.

As per "reclusivemonkey" comments the Nautilus convert ogg to mp3 script, should be user executable (755) and also you need permission to read/write  the music files and the directory they are in.

hope this helps.... :-)

---

### Post by notiones on 2006-07-25
I installed soundconverter and can now convert ogg files to mp3 without error. I can also play mp3's. 

1) I cannot burn to mp3 with Sound Juicer.

2) Even with the volume turned up all of the way, files transferred to the ipod can barely be heard. I am assuming this has something to do with the computer and not the ipod. 

All great advice so far and very much appreciated. It's hard to believe that after all of this time using Linux I cannot get something as simple as an ipod to work. 

If I am lucky, I might be able to convert my other daughter to Linux as well. This might be wishful thinking though.

Thanks again.

---

### Post by reclusivemonkey on 2006-07-26
> **notiones said:**
> I installed soundconverter and can now convert ogg files to mp3 without error. I can also play mp3's. 

1) I cannot burn to mp3 with Sound Juicer.


I'm at home now :-) In Sound Juicer, go to "Edit" --> "Preferences", then down by "Output Format" click on "Edit Profiles". Add a "New" profile with the following;

Profile Name: MP3
Profile Description: MPEG Layer 3
GStreamer Pipeline: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=false bitrate=192 ! id3mux
File Extension: mp3

and tick the active box. You should now be able to rip in MP3.

> **notiones said:**
> 2) Even with the volume turned up all of the way, files transferred to the ipod can barely be heard. I am assuming this has something to do with the computer and not the ipod.

Are these the converted ogg files? The conversion process may have reduced the volume of them.

---

### Post by notiones on 2006-07-26
:D Thanks Gerkin and Reclusive Monkey!!! All is working well except the volume and I now think it is the ipod itself. I found a maxlimit in the ipod settings that is currently locked. I believe that if I can get a Windows box working I can unlock it and fix the problem. 

Again, many thanks to you both. Your advice was clear, concise, and ultimately just what I needed. 

I would just like to make a quick comment if I may be indulged. I am a certified Linux administrator for a major distribution and I keep finding myself working with Ubuntu because it works so well as a desktop o/s. I have to admit that I have even given serious consideration to installing it on my own laptop. I am pretty well wed to my distro so it is not likely to happen, but I think the people behind Ubuntu need a huge atta boy and thanks from everyone who loves Linux. I really believe it is a bit of a phenomenon and wish Ubuntu continued success.

---

