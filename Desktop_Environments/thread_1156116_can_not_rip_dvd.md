---
title: "can not rip dvd"
date: 2009-05-11
forum: Desktop Environments
---

### Post by andrea000 on 2009-05-11
hello

I am trying to rip a dvd but the audio comes out all
messed up or out of sync with the video.How can i rip
this without this happening is there a better program
i'm using acidrip to do this.I think it is the copy
right protection (i'm not trying to steal it i'm only 
putting my dvd's on my PC)

---

### Post by RD1 on 2009-05-11
[HANDBRAKE!]("http://handbrake.fr/") :popcorn:

---

### Post by ghostborg on 2009-05-11
[http://www.dvdfab.com/free.htm]("http://www.dvdfab.com/free.htm")

Install Wine and then DVDFab HD decrypter.(FREE)

In DVDFab preferences(The green check top right) you need to use your mouse and arrow keys to navigate through the fields, a bug. Turn off Auto previews located under general==>  preview. To navigate left click on general then hit the down arrow continue this until you reach the preview section.
Rip whole DVD to Hard drive.

If you want to burn a disc then use DVDShrink to shrink it.

The newer versions of Handbrake do not rip encrypted DVD's, so I read.

Use Handbrake to encode it.

---

### Post by binbash on 2009-05-11
none of them are for linux...

---

### Post by RD1 on 2009-05-11
> The newer versions of Handbrake do not rip encrypted DVD's, so I read.

I doubted that was right so I just ripped an encrypted DVD to AVI using Handbrake. Worked great! :popcorn:

> none of them are for linux...

Handbrake is definitely for Linux. :)

---

### Post by andrea000 on 2009-05-11
Installed handbrake and i am ripping a dvd now i hope it 
takes the copy protecting off.I am storing all my dvd's 
on my pc that's the plan anyway.I'll watch them from there.

Thank you

---

### Post by RD1 on 2009-05-12
> Installed handbrake and i am ripping a dvd now i hope it
takes the copy protecting off.I am storing all my dvd's
on my pc that's the plan anyway.I'll watch them from there.


Just curious, did Handbrake perform to your satisfaction?

---

### Post by andrea000 on 2009-05-12
yes but it was slow and when it ripped the dvd 
something about the avi was corrupt so i will 
have to rip it again i could use any help that
someone could give me thank you

---

### Post by RD1 on 2009-05-13
> yes but it was slow and when it ripped the dvd
something about the avi was corrupt so i will
have to rip it again i could use any help that
someone could give me thank you

I don't know what the problem could be. 

These are the settings I use in Handbrake:

```
First page .... leave all settings as default except, change "Container" to AVI

Video Tab ....  "Video Codec" = Mpeg4 (Xvid)
                "Framerate" = Same As Source
                check both "2-Pass Encoding" & "Turbo First Pass"
                set "Target Size" to 1000 for an apx. 2 hour movie (1 hour TV shows I do at 500 and for a movie that goes over 2.5 hours I add 500 per half hour)

Audio/Suntitles Tan ... "Codec" = MP3 (Lame)
                        check "Allow Only Forced Subtitles"
                        leave all else as default unless movie is foreign language. Then, select "Preferred Audio Language" and "Subtitles"
```

These settings can be save as default on the right hand side of window.

Rip generally takes apx. the same time as the length of the movie on my 1.6GHz dual core Centrino with 2GB RAM ..... your mileage may vary.

---

### Post by coffeecat on 2009-05-13
**andrea000**, try k9copy. It's in the repos. It works for me and the version that comes with Jaunty is a great improvement over the Hardy and Intrepid ones (although they worked well enough).

For encrypted DVDs you must have libdvdcss2 from the Medibuntu repository installed. If k9copy crashes or hangs on you it's a good sign that libdvdcss2 is not installed. I learnt this the hard way. :(

**Edit:** by the way, k9copy (as you might guess) is a KDE app so, since you're running Ubuntu gnome, it'll bring a load of KDE dependencies in with it. But it works fine in gnome even if the KDE4 widgets look a bit out of place on the Gnome desktop.

---

### Post by andrea000 on 2009-05-25
Thank you all handbrake stalls on me i found k9copy but as i am only looking to rip it i didn't install it

---

### Post by ghostborg on 2009-10-20
Handbrake does have a Linux application with a gui.
Handbrake no longer decodes encrypted DVD's.

K9copy will not be able to decode some of the tougher protections
that is why I suggested using DVDFAB HD Decrypeter Free :guitar:under Wine.

---

