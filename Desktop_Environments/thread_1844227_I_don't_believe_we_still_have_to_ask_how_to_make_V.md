---
title: "I don't believe we still have to ask how to make VLC default medial player!"
date: 2011-09-14
forum: Desktop Environments
---

### Post by A Traveller on 2011-09-14
Hi All.

I am running 11.04 and have already tried the following without success. Is there any other way? Thanks.

System - Preferences - Preferred Applications - Multimedia - Custom - vlc %f - Close

System - Preferences - Preferred Applications - Multimedia - Custom - vlc %u - Close

Right-click on a media file - Properties - Open With - VLC - Close

I have also tried restarting my pc after each attempt.

---

### Post by A Traveller on 2011-09-14
I see the age old issue of the equaliser not remaining set is still present as well! I think I have managed to set them at least!

Have got brand new problems also!

Whenever I play a file in VLC, for the first 2 or 3 seconds the sound stutters every time.

I have to close VLC every time after playing a file if I want to play another file, so if I want to listen to 5 media files, I have to close and open VLC 5 times!

Is anyone else having these problems or know of a cure?

Any help would be very appreciated!

Thanks.

---

### Post by raja.genupula on 2011-09-14
> **A Traveller said:**
> I see the age old issue of the equaliser not remaining set is still present as well! I think I have managed to set them at least!

Have got brand new problems also!

Whenever I play a file in VLC, for the first 2 or 3 seconds the sound stutters every time.

I have to close VLC every time after playing a file if I want to play another file, so if I want to listen to 5 media files, I have to close and open VLC 5 times!

Is anyone else having these problems or know of a cure?

Any help would be very appreciated!

Thanks.
Hi

for this go to tools --> preference-->interface -->instances 

here you are going to have the options for  as allow instance , this will open only one vlc for all files , if you enable en queue,   then all those files add to your playlist . 

all the best

---

### Post by A Traveller on 2011-09-15
Hi raja. Thanks for you reply, it solved the re-starting VLC problem! That now leaves 2 problems.

The first few seconds of a media file stutters whenever opened

and

How to make VLC the default medial player

Thanks.

---

### Post by raja.genupula on 2011-09-15
hi  , actually  i know , what you did for setting as a default media player . i dont know any other technique . i am also following this thread to know that thing .

---

### Post by raja.genupula on 2011-09-15
> **A Traveller said:**
> Hi raja. Thanks for you reply, it solved the re-starting VLC problem! That now leaves 2 problems.

The first few seconds of a media file stutters whenever opened

and

How to make VLC the default medial player

Thanks.
well i got this 
hope this thing can help you for default issue .
[http://ubuntuforums.org/showthread.php?t=479841](http://ubuntuforums.org/showthread.php?t=479841)

all the best

---

### Post by mc4man on 2011-09-15
> I see the age old issue of the equaliser not remaining set is still present as well! I think I have managed to set them at least!
That just needs to be set in vlc's - tools > preferences as shown in screens
Show settings > all
1st click directly on Audio > Filters and enable it
Then open the equalizer and set as desired, click save
(setting made in the vlc interface itself are just for that instance of vlc, tools >  prefs are global

> How to make VLC the default medial player
"Right-click on a media file - Properties - Open With - VLC - Close"
That should be working just fine - any one file type done on, (.mp3, .flac, .whatever),   should then be set  to vlc as default for.
If not post this -
```
gedit  ~/.local/share/applications/mimeapps.list
```

Defaults for other things are also set individually -for Ex.  cd', dvd's in File management, -  nautilus > edit > preferences  
(audio cd's aren't properly handled from autoplay on cd insertion but that is fixable 
> The first few seconds of a media file stutters whenever opened
A link to one way at top of post, alternate below
[http://ubuntuforums.org/showthread.php?p=11126930](http://ubuntuforums.org/showthread.php?p=11126930)

---

### Post by Cpierce on 2011-09-15
Maybe this will help:
[http://superuser.com/questions/187440/set-default-ubuntu-video-player-as-vlc](http://superuser.com/questions/187440/set-default-ubuntu-video-player-as-vlc)

and this:
[http://ubuntuforums.org/showthread.php?t=1276575](http://ubuntuforums.org/showthread.php?t=1276575)

---

### Post by A Traveller on 2011-09-15
Hi raja. I tried the code at the link you provided (sudo chown -R atraveller:atraveller /home/theseeker), however, got the following message:-

chown: cannot access `/home/atraveller/.gvfs': Permission denied

I haven't tried the one in Italian as I would like to understand what they are saying and not just use the code without knowing.

Thanks for your help mc4man. That's how I set the equaliser as well. I was just annoyed that it had to be done this way and not just via the simple method.

When I run your command, I get the following:-

[Default Applications]
video/x-msvideo=vlc.desktop
video/mp4=vlc.desktop

[Added Associations]
video/x-msvideo=vlc.desktop;
video/mp4=vlc.desktop;

Thanks for the link about stuttering audio, I will give it a try and then post back to let you know if it worked.

Thanks for your suggestions Cpierce. I had already tried the instructions in the first link and had also come across the second webpage previously, however, I didn't carry out the steps because it seemed to be for making it default in Firefox, not Ubuntu.

Thanks.

---

### Post by A Traveller on 2011-09-15
Well done mc4man, the thread you linked to solved the problem of stuttering vlc!!!!

So that just leaves one problem, which is making VLC default.

I'd just like to mention something else in case anyone has a quick solution or knows why it is happening. I can hear static on my headphones when something happens, for example, if I move the mouse arrow or a webpage is loading or something is moving on the screen at a webpage. I think it is usually present whenever I install a new copy of Ubuntu (any version).

Thanks.

---

### Post by mc4man on 2011-09-15
> **A Traveller said:**
> 
So that just leaves one problem, which is making VLC default.


That is done as mentioned thru thr r. click on file (once per ext.), and in File Management, and in a browser for some online files.

Presently you've set vlc to be the default on .avi (msvideo) & .mp4

What else do you want it to be the default for?

As far as simple vs tools > pref.'s - they're 2 different things. Vlc allows temp, current instance settings, ('simple') and permanent, global settings. (tools > pref.'s

---

### Post by gordintoronto on 2011-09-15
> **A Traveller said:**
> So that just leaves one problem, which is making VLC default.
Thanks.

Right-click on a media file in the Nautilus file manager. Select "Properties." Select the "Open with" tab. Click the button for VLC.

You will need to do it for each type of media files, such as AVI, FLV, MKV, etc.

---

### Post by A Traveller on 2011-09-15
Thanks mc4man/gordintoronto. I am SO STUPID!!!! I have to admit user error for the making VLC default problem. It looks like I have managed to make VLC the default player, however, I don't know which method worked because I didn't play the files to check if it worked. I thought the icons for the files would change like I think they used to in older Ubuntu versions and when they didn't change, I thought it didn't work. I should have checked by playing the files! Sorry everyone for any inconvenience. I can now say that ALL the problems in this thread have been solved! Thanks everyone for all your help, it really has been appreciated.

Update - NOT SOLVED.

---

### Post by A Traveller on 2011-09-16
Oops, forgot that the static noise problem hasn't been solved yet! I've seen quite a few similar complaints from searching but no solutions apart from purchasing a sound card. I don't think this is necessary as the noise usually disappears on its own but it takes a LONG time of using the OS for that to happen, if ever! Maybe something somewhere is some kind of update or codec or something solves it.

---

### Post by Apanta on 2012-02-12
Hi.
I solved to make Vlc default player thanks to Ubuntu Tweak.

Ubuntu Tweak-->Sistem-->Managing File Types  and then double clic on the default player at the rigth side of the liste file types.
Select the application on vlc.
Pheraps it can help you
(sorry for my bad english).
Apanta :D

---

### Post by A Traveller on 2012-07-27
Thanks Apanta. Coincidentally, I just installed Ubuntu Tweak for the first time today!

---

