---
title: "Converting VOB to AVI"
date: 2006-06-29
forum: Desktop Environments
---

### Post by starNIX on 2006-06-29
Ok,  I ripped a DVD and then used "cat" to join the VOB files together into one.  It plays fine in my media players but now i want to save some space by re-encoding them to xvid.

I installed AVIDemux and I am not sure I am doing it right.  The audio is horribly out of sync.  How can I fix this?

I tried using the "Shift" option but it doesnt seem to do anything.

Any ideas?

---

### Post by simonn on 2006-06-29
I've been using mencoder quite a bit over the past few days and have found that doing a triple pass encode using xvid seems to sort out audio sync problems - even though I have seen references on the web saying this is not how to do it (I did not understand the reasonings why).

Have a play with acidrip (mencoder front end) ripping dvds and looking at the command line options that are generated. You should then get a good idea of how to rip the vob. Patience required though!

---

### Post by starNIX on 2006-06-29
Can you give me an example command line for mencoder to convert a VOB to an xvid file?

---

### Post by simonn on 2006-06-30
It is a little more complicated than that e.g. cropping, scaling (which you will more than likely have to do unless you want egg/thin-headed actors), no VOB file seems to be the same - some have audio which syncs easily some do not, different scaling, some look good at low bit rates, some look absolutely crap unles high bit rates are chosen etc etc etc

This is why I suggested you play around with acidrip. You can preview the changes you make. If you queue and export, it creates a script (acidrip.sh) in your home directory which is essentially a (or a series of depending on # of passes) mencoder command line. You will then get a feel for how mencoder works.

---

### Post by simonn on 2006-06-30
Ok.. here goes. **I am not an expert**, but the below appears to me to give good results.

First off, I have no NTSC DVDs to rip and test with, only PAL. NTSC has a weird frame rate so you NTSC users (US & Japan mainly) will need to read the mencoder doco and experiment.

Read at least [http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html](http://www.mplayerhq.hu/DOCS/HTML/en/encoding-guide.html),
particularily [http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-enc-libavcodec.html) (particularily the bits about using cropdetect) and 
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-xvid.html).

Seriously, read it. 30 mins spent reading it now **WILL save a few hours of your life**.

Before ripping you should detect how you need to crop the movie. Use the crop detect method mentioned in the second link above. Use a scene of the movie where there is a lot of contrast between the black bars and the actual movie on ALL sides of the screen.

I have been scaling the movie using the same width as the crop width and using -2 for height. Using -2 maintains the aspect ratio. You can of course scale it lower of higher, which will create a smaller or larger file respectively and will be faster or slower to encode respectively. Note that if you want smaller files there is probably a better way than using scaling (refer to links above). If you do not use scale, you may have stretched thin or squashed fat actors. Read the doco!

I have had good results from using:

```

mencoder dvd://1 -dvd-device [dvd device] -ovc xvid -xvidencopts bitrate=2000:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,crop=[W]:[H]:[H]:[V],scale=[W]:-2 -alang en -oac mp3lame -lameopts vbr=3 -o [movie.avi] 

```

(credit where credit is due, this was taken more or less from the mencoder doco).

Where you need to replace [dvd device], [W], [H], [H], [V] and [movie.avi].

If you have mirrored your dvd(s) to disk, you can replace [dvd device] with the mirror's path.

(starNIX, you should be able to replace "dvd://1 -dvd-device [dvd device]" with the path of your vob file).

**NOTE:** On my Sempron 64 3000 with 1Gb RAM, the above command line is taking between 2-3 minutes to encode one minute of video using the above, so this is an overnight/during day at work thing for a whole film. 

I would suggest that before you rip the whole movie, rip small 1-2 minute sections of it where there is (use -ss, -chapter etc - see doco):

a) Lots of dialog

b) Lots of action

Check them both, 

a) for audio sync 

b) blockiness 

I do not know what to do about audio sync, although one movie I ripped using acidrip defaults was 400ms out of sync. With the above command line it is at a  ~25ms seconds out (unfortunately mencoder cannot do negative audio sync), so only perceptable if you are actually looking for it. Others have seemed perfect to me.

For blockiness increase the bitrate, although 2000 above should be enough. you can of course decrease the bitrate if you want as well. This will mean a smaller file, but it will be of a lower quality. Scenes of high action will be where this is most apparent - seriously, check the scene with the most action, if this is good then the rest of the movie is very likely to be.

Once you have this sorted, you have all the info you need to complete the  command line.

I rip all the DVDs I am going to rip in a session to disk using vobcopy, work out the crop and scaling, then create a script so that they are all encoded one after another. I also preceed the mencoder command with nice -n 19 e.g.

```

nice -n 19 mencoder dvd://1 -dvd-device [dvd device] -ovc xvid -xvidencopts bitrate=2000:chroma_opt:vhq=4:bvhq=1:quant_type=mpeg -vf pp=de,crop=[W]:[H]:[H]:[V],scale=[W]:-2 -alang en -oac mp3lame -lameopts vbr=3 -o [movie.avi] 

```

nice -n 19 gives mencoder the lowest priority on you system so it will still be almost as responsive as if you were not running anything.

One final thing, turn your fans up! This is very processor intensive!

---

### Post by starNIX on 2006-07-01
I will definately read those links.  I found acidrip which is a frontend to mencoder.  It works beautifully.  Just need to experiment a little but so far so good.

I am niceing it to -15 because I have a "spare" 3.2ghz P4 with hyperthreading so no problem there.

The only thing I ran into is,  on the first movie I encoded,  every so often,  the picture gets blocky for a second or two.  Any way around that?

I am using 3 pass encoding.

---

### Post by simonn on 2006-07-01
[QUOTE=starNIX]The only thing I ran into is,  on the first movie I encoded,  every so often,  the picture gets blocky for a second or two.  Any way around that?[/QUOTE]

Try using the command line I gave, with a high bitrate e.g. 2000. I had a similar thing with one of the movies I encoded. I initially used a bitrate of 900, but that would get blocky when there was a lot, meaning a lot,  of movement. Is there a lot of movement when you get it?

---

### Post by starNIX on 2006-07-01
no,  it just happened randomly.  Maybe 3 times thru the whole movie.

---

### Post by southernman on 2007-07-10
simonn, that was a good read! Thank you!

Just one thing to add to your command, for those who may have problems with audio sync being off. 

Where you have:

> -vf pp=de,crop=[W]:[H]:[H]:[V],scale=[W]:-2

add

> ,harddup

to the end. No spaces between the "2" and the "," of the new variable.

I am working on a video that has truned out pretty well, except in low light shots, it's quality is off. Will be running some test encodes on those areas with different variables to see if the quality can increase while keeping the size down.

Mencoder all the way!

---

