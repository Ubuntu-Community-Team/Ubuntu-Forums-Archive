---
title: "Open office sound problem in 8.10 didn't happen on 8.04"
date: 2008-12-04
forum: General Help
---

### Post by josemaster2228 on 2008-12-04
There is an audio problem in power point presentations on 8.10 this didn't happen in 8.04 what is the problem when there is music on the powerpoint it sounds choppy there is no problem with other audio playback it is only the presentation this is very annoying because lots of mails that i get are power point with music i have made already 3 threads about this problem and I can't get it solved till now seriously considering to go back to windows so somebody better know how to fix this or share the same problem

---

### Post by josemaster2228 on 2008-12-04
Bump nobody else has this problem ?

---

### Post by Sef on 2008-12-04
Please wait 24 hours before bumping your thread. Sometimes answers can come quick and sometimes they come slow.   thank you

How did you install Ibex: upgrade or clean install?

---

### Post by josemaster2228 on 2008-12-04
Oh sorry for that well it was a clean install and one time I 
tried upgrade and after the upgrade the audio got screwed
i also tried un-install OO 2.4 and putting OO 3 but OO3 just made it worse instead of choppy sound there is no sound:(
hope you can help me thanks):P

---

### Post by David Oxland on 2008-12-29
I have he same problem, I believe.
Presentation sound is on and off about every second just like a flashing traffic light.

---

### Post by ionraedt on 2009-01-17
Glad to see I'm not the only one with that annoying problem.
Now we need a solution and then we can continue life as usual.
I have two ubuntu 8.10 installs :
1 clean install
1 upgrade from 8.04
Both systems show exactly the same choppy sound when playing a OO-presentation. Other progs with sound-output do not show that problem, so I guess it must be something in OO-presentation.
Any suggestion is welcome !

---

### Post by Rowd on 2009-01-18
I've got the same problem, it seems to be a bug in the mp3 decoder that openoffice uses, because I've seen presentations with wav audio that are ok.

AFAIK, openoffice is based on java, so the mp3 decoder that openoffice uses should be java too, and its different to the one that other applications use.

That could be the reason that makes only openoffice to have the problem and not any other program.

Maybe we should fill a bug report, if its not already reported.

---

### Post by ionraedt on 2009-01-23
just for completeness...
I installed OO 3.0 and the choppy-sound-problem remains the same (Ubuntu 8.10 comes standard with OO 2.4).
This, together with the fact that the problem (according to some posts) only begins after upgrading from 8.04 to 8.10, looks as if it is not a Java-problem within OO  but rather an Ubuntu 8.10 problem.
Greetings
Ivo

---

### Post by ajcham on 2009-01-23
Just as a test, would it perhaps be possible for you to upload a copy of a presentation that causes the problem for you?  I understand that, depending on the nature of the file, it may not be possible for copyright or personal privacy reasons, but if others such as myself could test it it would help to establish whether this is a repeatable bug, or a small number of isolated incidents.

You'd have to zip the file to upload it here, and even then it would still have to be under 1MB.  If it is larger you would have to upload it to another source (box.net or megaupload for example) and link it here.

---

### Post by ionraedt on 2009-01-23
Hi Ajcham
Can I send you such a presentation to your personal email ?
FYI, the problem is there with EACH presentation containing sound.
Plse answer giving your email address to my email ==> [email]ivo@onraedt.be[/email]
Thank you for your help !
Ivo

---

### Post by ionraedt on 2009-01-23
Please be aware that we are talking about MS POWERPOINT presentations (.pps) here, so not native OO-presentations !
Thought it was useful to repeat this here.
Ivo

---

### Post by ajcham on 2009-01-23
> **ionraedt said:**
> Hi Ajcham
Can I send you such a presentation to your personal email ?
FYI, the problem is there with EACH presentation containing sound.
Plse answer giving your email address to my email ==> [email]ivo@onraedt.be[/email]
Thank you for your help !
Ivo

I've sent an email to that address, so you should be able to send me the file now.  Did you receive the email OK?

---

### Post by ajcham on 2009-01-23
OK, I can confirm the problem when using the PPT file you sent me (I'm using OOo3 on Intrepid) - the sound seems to cycle on/off every half-second or so.  As for the ODP, I cannot test that one as the audio is not present; It seems that while the PPT file specification embeds the audio into the file, the ODP spec has the audio linked separately. A line in the XML shows that it is looking for a wav file which of course I don't have:
```
<presentation:sound xlink:href="../../.openoffice.org/3/user/gallery/Miscellaneous-pictures.wav"
```

Here's where it gets interesting: I resaved the PPT as an ODP, which resulted in the .wav file being saved separately.  I navigated to the file in nautilus and used the mouse-hover technique to preview the file - this gave me the same choppy output as OpenOffice.  At first I thought that the file must get corrupted in the import process, but when I actually opened the file (I tried both Audacity and Mplayer) it played perfectly.

Presumably then, the error lies in the WAV codec used by Ubuntu* (I expect that OpenOffice and Nautilus both use the same one).  I'd search the forum a bit to see if someone has a fix for bad .wav processing, and if not create a new thread specifically on that topic (linking back to this thread to give it some context).

* One point I should make is that Audacity did complain about the file when opening it: *"The Audio may be bogus &#8230; try changing the file extension"*.  Although it still imported and played the file, it may be the case that the import process in OOo is responsible for creating a corrupt file - just maybe Audacity and MPlayer are better at resolving the corruption than Nautilus and OOo.  Are you the author of the presentations? If so I assume you have the original wav files from before they were embedded?  You could try accessing these in Ubuntu - try using the mouse-hover preview in Nautilus.  This will show whether the bad WAV processing is inherent in Ubuntu or a result of the .wav file being altered in the embedding/importing process.

---

### Post by ionraedt on 2009-01-23
Thank you for your support !
Now I understand a little bit better what's the matter, thank you for that.
I will search for eventual solution to the wav-codec problem within OO or Nautilus. If nothing found, I will try to start a new thread (have to find out "howto" first ;) ).

---

### Post by ionraedt on 2009-01-23
Again for completeness and to help other people having the same problem.
I also installed wine with pptview (2 versions).
This didn't solve anything at all, on the contrary, sometimes ppt-files didn't play at all or the PC hung. 
BTW, this is no criticism towards the people that are working on wine, in some cases it was the only solution for me ! and I am very thankful for that.
Ivo

---

### Post by ajcham on 2009-01-23
FYI, I've just downloaded a random WAV file from the web, and it exhibits the same behaviour when previewing in Nautilus, but plays fine when opened in another app, so we can rule out the possibility of OpenOffice introducing file corruption.

I expect the fix is as simple as downloading some alternative wav decoder in synaptic, but I'm not sure what that would be.  If I come across the solution I will of course let you know.

---

### Post by ionraedt on 2009-01-23
So it means we have to make OO use another wav-codec.
As I understand now, OO uses the standard Ubuntu 8.10 wav-codec (just like Nautilus) It would mean we have to find out how to make Ubuntu 8.10 use another (better) codec. Is that right ? I found some sites that enable us to download codecs for Ubuntu. Is this the way to go ???
Sorry for my basic knowledge, just trying ;)

Ivo

---

### Post by ajcham on 2009-01-23
I'm not sure - I think it may be an issue with the decoder, but on the other hand I've just downloaded another file from the Web, and this one plays without problems.  I don't have an in-depth knowledge of the WAV file format, but I suspect that there must be multiple specifications - the decoder handles some better than others.

FWIW, I have the ubuntu-restricted-extras and w32codecs installed, although these haven't helped in playing the first two files I tried (your Powerpoint WAV and a soundbite downloaded via a Google search).

This has been the result of my testing with those two files:
**Plays perfectly:**
MPlayer
Audacity (despite "Bogus Audio" warning)
**Causes choppy playback:**
Nautilus audio preview
Totem (gstreamer)
OpenOffice
Rhythmbox
**Won't open:**
VLC (*error: Can't recognise the input's format*)
Audacious (*No error message - just doesn't play*)
Amarok (*error: No available decoder*)

The third file (another soundbite found via a Google search, but from a different source) responded much better, although still failed to play in Audacious and Amarok.  It also caused the "Bogus Audio" warning in Audacity, but still played.

It may be worth creating a new thread to try to resolve this - someone here must have a better understanding of how WAV works. It's certainly piqued my interest, so I'll probably do a little research too and see if I can find an explanation.

---

### Post by ionraedt on 2009-01-24
Wouldn't it be better to transfer this issue to OpenOffice dev  ?
Ivo

---

### Post by isTHEr3mOr3 on 2009-02-20
Did anyone solve this issue? It is really an annoying problem, but I guess a lot of people just accept it.

---

### Post by isTHEr3mOr3 on 2009-02-22
An example of a presentation with this very annoying sound problem is this one:

[http://www.funnysite.org/index.php?page=powerpoint&ID=3](http://www.funnysite.org/index.php?page=powerpoint&ID=3)

I've installed Ubuntu 8.10 on a pc of a friend of mine and he receives tons of powerpoint presentations with this sound issue. I really need to solve this. He is quite pleased with Linux/Ubuntu, but he's tempted to go back to windows because of this.  

Also tried to install office with wine, but got major issues. 

This is costing me too much time.. hope someone has an easy solution.

---

### Post by Hemanti on 2009-02-23
OK, I join in. I have the same problem with a ppt file. Any more ideas popped up?

---

### Post by isTHEr3mOr3 on 2009-02-23
It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/298494](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/298494)

I've tried to install pulseaudio 0.9.14 , solved all dependencies for 'configure' but still got failures during 'make'. 
An easy package or other solution would be very nice.

---

### Post by isTHEr3mOr3 on 2009-02-24
Ok... 

New day, new attempt to solve this. 

sudo apt-get install esound
sudo apt-get remove pulseaudio

Result, still the same f..ng issue. So I guess pulseaudio isn't the main problem, but upgrading to 0.9.14 could be part of the solution.

---

### Post by isTHEr3mOr3 on 2009-04-04
This appears to be the solution:

Remove Gstreamer0.10-plugins-ugly 0.10.9 

Install [gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb]("http://launchpadlibrarian.net/24687939/gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb")

or install gstreamer0.10-plugins-ugly_0.10.6 (also bugfree)

Good luck!

---

### Post by canclan on 2009-04-18
> **isTHEr3mOr3 said:**
> This appears to be the solution:

Remove Gstreamer0.10-plugins-ugly 0.10.9 

Install [gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb]("http://launchpadlibrarian.net/24687939/gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb")

or install gstreamer0.10-plugins-ugly_0.10.6 (also bugfree)

Good luck!

Both my father and I have Toshiba notebooks with the same problem.  The fix worked!  Thank you for the info!

---

### Post by Andrew_P on 2009-11-22
> **isTHEr3mOr3 said:**
> This appears to be the solution:

Remove Gstreamer0.10-plugins-ugly 0.10.9 

Install [gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb]("http://launchpadlibrarian.net/24687939/gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb")

I removed [FONT="Courier New"]gstreamer0.10-plugins-ugly 0.10.9[/FONT], installed the down-level [FONT="Courier New"]gstreamer0.10-plugins-ugly_0.10.8-1_i386.deb[/FONT] on my Fry's Electronics RX-7335 laptop machine (Intel Celeron, 2.4GHz) and it fixed the choppy audio problem when viewing PowerPoint slide shows in OpenOffice.org Presentation.  Thereafter, the Update Manager icon became permanently visible in the top panel, because it wanted to "update" the package back to [FONT="Courier New"]gstreamer0.10-plugins-ugly 0.10.9[/FONT].  The fix for this is to open the Synaptic Package Manager (click System -> Administration -> Synaptic Package Manager), highlight the [FONT="Courier New"]gstreamer0.10-plugins-ugly_0.10.8[/FONT] package, then from the Package menu, click the "Lock Version " box. Close Synaptic Package Manager, then from the Applications menu, run Add/Remove, check for new updates; [FONT="Courier New"]gstreamer0.10-plugins-ugly 0.10.9[/FONT] should disappear from the suggested update list and the icon should disappear from the top panel.  Update Manager won't touch the downlevel version thereafter, and if a new version comes out, it won't bug you.

---

