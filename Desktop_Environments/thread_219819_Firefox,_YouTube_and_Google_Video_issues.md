---
title: "Firefox, YouTube and Google Video issues"
date: 2006-07-20
forum: Desktop Environments
---

### Post by MacLeod_1980 on 2006-07-20
I have seen a few posts scattered about this issue, but none of them seem to resolve my problem.

I having issues with veiwing video in YouTube and Google Video, but only in Firefox. I have opened up Mozilla and viewed videos from both sources without any problem - so I don't think that it is an issue with flash versions, like some people have been suggesting.

Does any one have any idea how I can resolve this problem, or is there any way I can provide you with additional information to help me solve my issue.

Thanks for reading!

---

### Post by Lord Illidan on 2006-07-20
More information is essential in this case.

What kind of issues? Sound issues?

---

### Post by Chuckaluphagus on 2006-07-20
I have exactly the same situation, and it occurred only recently  (about a week ago).  Sound in Flash when played in a Firefox window worked up until then.

All other sound works fine on my system: streaming music over the Internet, local CDs, MP3s, video, etc.  Sound works with Flash when a site is accessed through Mozilla but not through Firefox.  The problem appears to be quite specific to Flash as well; I can watch Quicktime trailers with sound in Firefox using the Mplayer plugin, for example.

If more information is required, just let me know what you need.  Thanks for any assistance.

---

### Post by MacLeod_1980 on 2006-07-23
> **Lord Illidan said:**
> More information is essential in this case.

What kind of issues? Sound issues?

Sorry I didn't get back to you any sooner. I thought I had subscribed to the thread but must have forgotten.

Anyway the issues I have is not just sound related, it is video related also. The players do not appear correclty on the screen, so I can't start them and don't hear anything. However if I look at exactly the same link in Mozilla the video works fine. This is a new problem I am having, it must be due to some updates that were installed approximately a week ago.

I thought it may have something to do with the default Java version I was using, but I installed Sun Java 1.5.0 or whatever and made it my default - no joy though...

This is a big problem for me as I love my Firefox but since I can't look at some online content (videos) I have been forced to use Mozilla. In all fairness Mozilla isn't bad - just not as customized as my Firefox setup.

If there is any more information I can provide please feel free to ask. Thanks for looking.

---

### Post by bluntu on 2006-08-06
I'm also suffering from this problem.

Other sites with flash is OK but with Google and YouTube that is where the problem is. It plays a few second and then stop and would freeze if I try to close the browser.

Anyway, where can I get Mozilla so I can watch stuff on google and youtube?

---

### Post by someguyouknow on 2006-08-06
i had the same sort of issue and it turned out to be sound related.....
i did this.....
sudo apt-get install alsa-oss

sudo kate /etc/firefox/firefoxrc

FIREFOX_DSP="aoss"

for some, aoss may not work (like for me) so i put auto instead.....
i can watch google video and youtube with no problems now.....
hope this helps someone....

---

### Post by bluntu on 2006-08-06
Wow. That solved it. THanks!

---

### Post by bluntu on 2006-08-06
Some videos have very small sound. Is there anyway I can increase it? In windows I can do this with the Volume control without a problem (It's much louder) but in Ubuntu the Volume control is very weak.

Is there anyway I can make the sound a little louder?

---

### Post by someguyouknow on 2006-08-06
are you sure your system sound it high enough?.....
or maybe its just that video.....

---

### Post by thedude98 on 2006-08-06
Videos on YouTube would stream but without sound.  This fix worked!  Now the only problem is the videos are in German.  You don't have a command line for that one do you? ;)  Thanks for sharing.

---

### Post by philipacamaniac on 2006-08-06
This is some kind of (firefox?) regression, because I was previously able to watch YouTube and Google videos all the time without issue.

---

### Post by bluntu on 2006-08-07
It's strange that the volume controller (found at the taskbar) has no effect on the videos at video.google.com

I turn it down to mute and still hear sound...

---

### Post by Roasted on 2006-08-07
I turn mine to mute and still hear sound too, but I thought that was because I have a home stereo hooked up to my computer via auxillary port and the stereo's volume always remains at 25/50.

---

### Post by TheRo0sTer on 2008-04-19
I tried the sudo kate/ect/firefox command and it told me it couldn't find that command. 

I still have no sound at youtube.

---

### Post by OzFitzy on 2008-04-19
> **TheRo0sTer said:**
> I tried the sudo kate/ect/firefox command and it told me it couldn't find that command. 

I still have no sound at youtube.

Me too - couldn't find "kate".
I have sound but very jerky video and of course if you download an FLV file the player won't handle it. :(

---

### Post by tomissi on 2008-04-28
hi im new in linux and new on this forum, i came across because im having the same problem, i get no sound on you tube and no movies on google video, i tried the kate on the command line and i got this: command not found

is there any who can assist me? thx in advance. 

tomissi

---

### Post by JCM3000 on 2008-05-09
tomissi, I don't know if you solved your problem yet.  'Kate' is a text editor for KDE which you won't have with a standard Ubuntu install.

Below is the command I used to solve the youtube etc sound issue with a fresh install of Ubuntu Hardy:

```

sudo apt-get install alsa-oss

sudo gedit /etc/**firefox-3.0**/firefoxrc

```

** Note that I am using Firefox 3 Beta 5 which came as standard with Hardy, you may wish to change the folder name in bold if using a different FF version.

I then added FIREFOX_DSP="auto" into the empty file and saved it.  A quick reboot and youtube etc work fine.

Hope this helps you or someone else.

---

### Post by tomissi on 2008-05-16
JCM thanks for your answer. Finally I tried that code line that you suggested me, firefosxrc or so. Though Youtube works with sound now, i can´t controll it, and in general the picture is not running so well and there are some strange bity sounds sometimes. And in some other online movies not from youtube i get no picture at all, like in the ones embebed on some blogsites. So when i show my friends the Ubuntu when we come to youtube it made water. 
Could be my lousy graphic card? who knows...
Cheers mate and thanxs for the interest.
Tomissi.

---

