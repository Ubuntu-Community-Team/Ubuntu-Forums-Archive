---
title: "Fullscreen Video Frame Rate Decrease with Compiz-Fusion"
date: 2007-11-01
forum: Desktop Effects &amp; Customization
---

### Post by meowsus on 2007-11-01
Hey guys. I've been an Ubuntu user for about 6 months now and i've gotten by on scouring the Forums for all my answers, but never posted. Until today!

Okay.

When i'm watching video in fullscreen the frame rate drops to that point there its not unwatchable, but just extremely annoying. Like its driving me crazy. Like "hulk! smash!" crazy.

The weird thing is i can take the VLC window (i use VLC usually, btw), and stretch it out to be full screen and its smooth as glass. Its just something about the whole fullscreen thing, the computers just not liking it anymore.

I say "anymore" because i used to run Ubuntu Feisty with Compiz 0.4 and i never ran into this issue. And i've got a monitor set to use 1600x1200 resolution and it handled it jus' fine.

The one workaround i came up with is to set up another profile in the Compiz settings panel with pretty much all options stripped out. When i'm gonna watch something in fullscreen i just switch the profile to the stripped out one and press play. 

It works, but i kinda want something more... automatic.

If anyone can give me a tip or two i would be very, very grateful. 

Thanks :P

---

### Post by meowsus on 2007-11-02
I've got a bad feeling no one is going to reply to this one.

---

### Post by Zorael on 2007-11-02
I don't have much to reply with if I don't have an answer, or a suggestion.

If it improves on an "empty" profile, have you tried disabling plugins one by one to see which (if one) is the culprit? Meaning, basic troubleshooting. :>

---

### Post by meowsus on 2007-11-02
> **Zorael said:**
> I don't have much to reply with if I don't have an answer, or a suggestion.

If it improves on an "empty" profile, have you tried disabling plugins one by one to see which (if one) is the culprit? Meaning, basic troubleshooting. :>

But... But theres so many! 

Haha, yeah i've slowly been making it thru them and i haven't found the culprit yet. 

I'll keep truckin'.

---

### Post by maino82 on 2007-11-07
I have the same issue. I generally use totem-xine, but have tried totem-gstreamer and vlc as well and can confirm that it is a problem in all three with full screen enabled. It seems to be an xgl issue with me (I have an ATI Radeon Xpress 1100), rather than a compiz issue. When I disable compiz, but keep xgl installed and running, I have the problem. When I also uninstall xgl, then the problem goes away. 

Any ideas? Thoughts? Any help you could offer would be greatly appreciated.

Just for reference:
Ubuntu 7.10 - 64 bit
Kernel 2.6.22-14-generic
Compiz 0.6.1
Xserver-xgl 1.1.99.1
Fglrx 7.1.0-8.37.6+2.6.22.4-14.9

ATI Radeon Xpress 1100
2GB Ram
AMD Turion 64 X2

---

### Post by jadz0r on 2007-11-08
I had this problem as well, up until the other day.

I created a new session that was 'emerald --reload' so that it uses emerald and not meta-city. Video frame rate is back up to 100%.

Give that a go and see how you go dude

---

### Post by meowsus on 2007-11-08
> **jadz0r said:**
> I had this problem as well, up until the other day.

I created a new session that was 'emerald --reload' so that it uses emerald and not meta-city. Video frame rate is back up to 100%.

Give that a go and see how you go dude

Now see, i would have thought that emerald would have caused MORE problems, but i guess it makes sense that Compiz-Fusion would be more used to using emerald, as it's been packaged with Beryl for years. I cant wait to get home and test that out.

(Actually, i cant wait to rebuild my computer at work as an ubuntu box... ZING!)

---

### Post by meowsus on 2007-11-08
Also, i've noticed a decrease in quality in my video playback. I had changed settings in VLC to output for (i think) X11, to fix the issue i had with my video playback being just a black screen when i was running Compiz-Fusion.

But now the video is really pixilated when i maximize the window to fullscreen. The videos i'm playing arent the best quality, but they seemed to be more anti-aliased before. Maybe i'm crazy. I'll try to rock out a screenshot of what i'm talking about when i get home.

---

### Post by maino82 on 2007-11-08
> **jadz0r said:**
> I had this problem as well, up until the other day.

I created a new session that was 'emerald --reload' so that it uses emerald and not meta-city. Video frame rate is back up to 100%.

Give that a go and see how you go dude

Sorry, I'm a bit slow this morning, so as my brain warms up maybe it'll come to me, but what do you mean by "create a new session?" Is that something that I should put in my session startup commands or do I need to create a new entry for GDM or some other option that I can't think of?

Any insight you could give would be greatly appreciated!

---

### Post by jadz0r on 2007-11-09
> Sorry, I'm a bit slow this morning, so as my brain warms up maybe it'll come to me, but what do you mean by "create a new session?" Is that something that I should put in my session startup commands or do I need to create a new entry for GDM or some other option that I can't think of?

Any insight you could give would be greatly appreciated!

System -> Preferences -> Sessions

Then add the command "emerald --reload" without the quotes

---

### Post by meowsus on 2007-11-09
> **jadz0r said:**
> I had this problem as well, up until the other day.

I created a new session that was 'emerald --reload' so that it uses emerald and not meta-city. Video frame rate is back up to 100%.

Give that a go and see how you go dude

That actually made it worse for me. 

Hrm.

---

### Post by jimerickso on 2007-11-09
have you tried selecting xshm as the video driver in vlc? this may help.

---

### Post by meowsus on 2007-11-09
> **jimerickso said:**
> have you tried selecting xshm as the video driver in vlc? this may help.

I believe i have VLC set to "X11" now and Totem (thru GStreamer) set to "X Window System (No Xv)" which, im guessing, are essentially the same thing, since the video output not only looks very similar, but they both clip when in full screen.

But i will check the Xshm settings too, and a few others to try to get a good result out of it.

I found a post thats helped a few people out. The second post suggests the use of Xshm too. [Here is a link to the aforementioned thread](http://ubuntuforums.org/showthread.php?t=415012&highlight=compiz-fusion+video+xshm)

It also explained that the settings i have my video players set to cause the blockyness and clipping because they use the CPU instead of the graphics card, which makes sense. I have a gig in my machine... Maybe its time to upgrade, if i cant get this to easily resolve with changing settings.

Understanding things sometimes sucks.

---

### Post by miketech on 2007-12-15
Hi,

any news about this topic? Because I have the same problem. Videos in fullscreen with compiz aren't working well here.

Greetings

Mike

---

### Post by meowsus on 2007-12-17
> **miketech said:**
> Hi,

any news about this topic? Because I have the same problem. Videos in fullscreen with compiz aren't working well here.

Greetings

Mike

Mike, 

I haven't really gotten anywhere, but i've noticed an improvement using GNOME MPlayer. 

My usual Video Player is VLC, but as soon as i started using MPlayer, everythings been better.

Hope that helps a little. If you get a good resolution, plz, let us know!

Curdo

---

