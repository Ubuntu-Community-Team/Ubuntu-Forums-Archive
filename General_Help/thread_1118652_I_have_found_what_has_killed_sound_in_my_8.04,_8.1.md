---
title: "I have found what has killed sound in my 8.04, 8.10 and 9.04"
date: 2009-04-07
forum: General Help
---

### Post by Fenris_rising on 2009-04-07
Hi all

Just a heads up on one sound issue I have had with 8.04, 8.10, and 9.04. I have not found a similar report despite some heavy searching.

Basically I initially had problems with sound in my PC install of 8.04 Which up until around 3 weeks ago worked fine no problems ever. Then out of the blue (or so it seemed) I lost sound in Totem, Mplayer, and Amarok which were my primary media players. Amarok was cured, eventually, by going into the engine tab and changing the auto detect to Alsa. A lucky guess on my part. Mplayer and Totem proved more problematic and I was unable to get them working. So having searched the forums for solutions I ended up unstalling SMplayer which worked fine, VLC has been tried and also worked, and xine player worked once I had set the sound and video types in it's preferences.

OK so far? Right then. Within days my easy peasy install on my eeepc 904HD went the same way, as did, a little later, my jaunty dual boot on the eeepc. These did cause much vexation as I was having to mess around all over the place to get sound. When I did get my sound back it was at the cost of not being able to use the desktop volume slider or the Fn keys to control the volume.

Last night I had a revelation!!!!!! There is one common factor in my troubles and I can now cause and fix the problem at will.

Around 3 weeks ago I created my own login screen for my PC. All well and good nothing to screw the sound up there. But I also went to the trouble of creating some sound samples to act as my 'login ready' and 'login successful'. Nothing wrong there either.

Now if you go to your System>Admin>Login window and look under the Accessibility tab. Under **sounds** only the 'Login ready screen' sound is ticked to be active.

With my sound samples I also ticked the 'login successful' sound to work.
and herein is the cause of all my sound problems.

When I boot up my PC/eeepc it plays the sound announcing it's ready.
When I login in it then plays my sound additional sample. 

After that I lose my sound in my media players and if I click the 'test' button for the sound samples in the 'login window' they don't work either.
Reboot the login sounds work but still nothing in system after that

The cure at this time is to **untick** the login successful sound and upon reboot I have all my sounds back. The odd thing is that when it gets to the  login the PC plays my sound sample as selected for the login but it follows the successful login with the default Ubuntu 'choral chime'. As I say I can kill my sounds at will simply by enabling the 'login success' sound and recover by unticking and rebooting.

Has anyone else had this problem?

regards

Fenris

---

### Post by kpkeerthi on 2009-04-07
I suggest you file a bug in launchpad so the devs know about this problem.

---

### Post by Fenris_rising on 2009-04-07
Done :)

---

### Post by kpkeerthi on 2009-04-07
Great. This will sure benefit some users.

---

### Post by Fenris_rising on 2009-04-07
Fingers crossed. It seems very specific. I keep doing it to both machines just to make sure :D and yes it still screws it up :D

regards

Fenris

---

### Post by LowSky on 2009-04-07
have you tried using a sound file of a different format, like ogg, mp3, or wav.

It could just be a conflict of just one codec, knowing if its one or all will help developers

---

### Post by Fenris_rising on 2009-04-07
Hi there

I did specify what file format I used in my bug report. But the thing is I checked what the existing file format was before I created my sample and changed them. It is still possible of course. I also find it strange, though, that the default 'Ubuntu login success' sound plays despite not being selected or indeed as the login success sound is un ticked at this time. 

I did mention that to, maybe a conflict due to the original sound running without being told to?

regards

Fenris

---

### Post by markbuntu on 2009-04-07
This is a long running problem that is very very low on the priority list. Someday maybe.....

---

### Post by pastalavista on 2009-04-07
Have you tried renaming the sounds you made to the same as the ubuntu sounds (first change the ubuntu sounds name to original.names.old) and then tick the box?... (old DOS trick)... just curious

---

### Post by Fenris_rising on 2009-04-07
Hi there

Ahhhh, Old problem rediscovered by me for me :D  Thats fair do's then.

I could try renaming them but I think it will not work because the Login ready is mine and is active and doesn't cause any issue.

The one that causes an issue seems to be the login successful tab. I presume it holds onto what ever sound module it uses after login. It should be noted that by default this one is not ticked to be active and yet the default 'chime' sounds regardless of this fact.

I can live with it! At least all my sounds work now :)

How long has this been an issue then?

regards

Fenris

---

### Post by Mimoo_Tz on 2009-04-07
thank you may , this is beautiful , ur experience in ubuntu

---

### Post by dcstar on 2009-04-08
> **Fenris_rising said:**
> 
........
The one that causes an issue seems to be the login successful tab. I presume it holds onto what ever sound module it uses after login.
........

There is an ongoing issue where the Pulse sound module is started as a User level app after login and then dies immediately on logout (ever tried getting a logoff sound to work since 7.10?......) instead of being run as a system level process.

This one sounds (pun intended...) like the sub-system process that outputs the various pre-login sounds is preventing the Pulse user-level sub-system functioning, probably because both cannot run simultaneously and by the time the system process has finished playing the login successful sound, the user process has died starting up - what a mess!

No wonder the developers have this as a low priority, it looks like it is fundamentally flawed and would be an absolute mongrel to sort out given the security issues of system and user level processes trying to use the same hardware.

---

### Post by Orc65 on 2009-04-13
I have had the same issue over the last two releases, sound works fine in all my media players, then at some stage, I'm assuming it's just after an update, sound to particular media players drops out. This time for me it was Mplayer and flash videos in Firefox. I found this thread a moment ago and followed Fenris' suggestion to disable start up sound and now I have sound back in both, thanks mate.

---

### Post by randogauci on 2009-04-30
Hi
I also had similar problems (very low sound volume). After disabling login sounds everything works fine..Thanks

---

### Post by babyfoxx on 2009-05-08
Wow, and here I thought I was going crazy. I had the same thing, low to no sound then enabled the login sound, restarted and vola...sound again. Thanks.

---

### Post by Foxblood on 2009-05-10
Thanks, Fenris_rising, that worked like a charm. Thanks again.

---

