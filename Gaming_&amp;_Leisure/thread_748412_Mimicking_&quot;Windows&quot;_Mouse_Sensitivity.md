---
title: "Mimicking &quot;Windows&quot; Mouse Sensitivity"
date: 2008-04-07
forum: Gaming &amp; Leisure
---

### Post by Pulani on 2008-04-07
When disabling mouse acceleration (xset m 0 0) on my Intellimouse 3.0, the sensitivity is very, very low.

The sensitivity slider has in the Mouse Preferences Window has NO effect at all, or I'm guessing it affects how much mouse acceleration you get (which I do not want)

I'm trying to make the full transition to Ubuntu, but this issue is really hampering any sort of competitive gaming (Warcraft 3, Starcraft, etc.)
Windows users will understand what I mean by a higher sensitivity with no mouse acceleration (enhance pointer precision turned off)

Is there any way to fix this problem?

---

### Post by rostamiani on 2008-11-06
I found a script that solved the problem
But I don't know how to use it
Please Help :)

Script:
[http://lists.x.org/archives/xorg-mentors/2006/000023.html](http://lists.x.org/archives/xorg-mentors/2006/000023.html)

---

### Post by rostamiani on 2008-11-13
> **rostamiani said:**
> I found a script that solved the problem
But I don't know how to use it
Please Help :)

Script:
[http://lists.x.org/archives/xorg-mentors/2006/000023.html](http://lists.x.org/archives/xorg-mentors/2006/000023.html)
Can anyone help ?

---

### Post by Endolith on 2009-01-04
For high speed without any acceleration at all, you'd use something like "xset m 5 1", so that the speed is 5× as fast and the "precision zone" where it drops to 1 pixel accuracy is only 1 pixel wide.

X Windows does not normally use real acceleration as I understand it.  It just has these two speeds (slow for moving one pixel at a time, and fast which is just a multiplier times the slow speed), and the transition from one speed to the other is set by traveling more than a certain number of pixels.  This is why the mouse is so jerky under Ubuntu.  I read a good article about this once but I can't find it anymore.

If you do "xset m 20 3" on a command line, you'll see a very exaggerated demonstration  of how this works. In this case, "acceleration" is 20x, and "threshold" is 3 pixels, so if you move slowly, you can point at individual pixels, but if you move quickly, it jumps by 20 pixels instead.  Totally useless, and this is why the default acceleration sucks.

I think the "Sensitivity" and "Acceleration" settings in Gnome Mouse Preferences do something different?  Maybe "Acceleration" maps to xset's "acceleration", and "Sensitivity" maps to xset's "threshold"?  The Gnome help screen uses these terms in a different way:

> **Table 8-15&#8195;Mouse Motion Preferences**

[LIST]
[*]                   Acceleration
[LIST]
[*]                 Use the slider to specify the speed at which your mouse pointer moves on your screen when you move your mouse.
[/LIST]
 
[*]                   Sensitivity
[LIST]
[*]                 Use the slider to specify how sensitive your mouse pointer is to movements of your mouse.  *(this seems to be the same as "threshold" in xset)*
[/LIST]
 
[*]                   Threshold
[LIST]
[*]                 Use the slider to specify the distance that you must move an item before the move action is interpreted as a **drag-and-drop action**. *(so "threshold" is unrelated to the mouse movement itself)*
[/LIST]
 
[/LIST]
However, there appears to be an actual smooth acceleration built in that isn't used by default:

>         mouse   The  m option controls the mouse parameters; it may be abbrevi&#8208;
                ated to &#8217;m&#8217;.  The parameters for the mouse  are  &#8216;acceleration&#8217;
                and &#8216;threshold&#8217;.  The acceleration can be specified as an inte&#8208;
                ger, or as a simple fraction.  The mouse, or  whatever  pointer
                the  machine  is  connected to, will go &#8216;acceleration&#8217; times as
                fast when it travels more than &#8216;threshold&#8217; pixels  in  a  short
                time.   This  way,  the mouse can be used for precise alignment
                when it is moved slowly, yet it can be set to travel across the
                screen  in  a  flick  of  the  wrist when desired.  One or both
                parameters for the m option can be omitted, but if only one  is
                given,  it  will  be  interpreted  as  the acceleration.  If no
                parameters or the flag &#8217;default&#8217; is used, the  system  defaults
                will be set.
 
                If  the **&#8216;threshold&#8217; parameter is provided and 0**, the &#8216;accelera&#8208;
                tion&#8217; parameter will be used in the exponent of a [B]more  natural
                and  continous  formula[/B], giving precise control for slow motion
                but big reach for fast motion, and [B]a progresive transition  for
                motions  in  between[/B].  Recommended &#8216;acceleration&#8217; value in this                case is 3/2 to 2, but not limited to that range.
[http://manpages.ubuntu.com/manpages/intrepid/en/man1/xset.1.html](http://manpages.ubuntu.com/manpages/intrepid/en/man1/xset.1.html)

When I use "xset m 11/8 0" I get a pretty usable smoothly-accelerating mouse.  Of course, this is not nearly sensitive enough for my touchpad.  Sigh.

---

### Post by AgentWD-40 on 2009-01-14
I can't quite seem to get my mouse at a decent setting either. It just doesn't seem to move like it should. For example, if I put the mouse pointer all the way to the left on my screen, then quickly flick my mouse to the right, the pointer just jumps around a little on the left side of the screen and doesn't end up far from where it started. It seems that with such a quick motion it should end up on the right side of the screen.

---

### Post by StarryTripper on 2009-01-18
> **AgentWD-40 said:**
> I can't quite seem to get my mouse at a decent setting either. It just doesn't seem to move like it should. For example, if I put the mouse pointer all the way to the left on my screen, then quickly flick my mouse to the right, the pointer just jumps around a little on the left side of the screen and doesn't end up far from where it started. It seems that with such a quick motion it should end up on the right side of the screen.

I just tried what you described, starting upper left with a quick flick to the right. It works as expected, smooth and not jitter.

However, I use a Logitech TrackMan Wheel...so, maybe that's why?

I could take a screenshot of my settings in System>Preferences>Mouse for you.

---

### Post by AgentWD-40 on 2009-01-19
> **StarryTripper said:**
> I just tried what you described, starting upper left with a quick flick to the right. It works as expected, smooth and not jitter.

However, I use a Logitech TrackMan Wheel...so, maybe that's why?

I could take a screenshot of my settings in System>Preferences>Mouse for you.

Could you please show me what your settings look like? Maybe it has something to do with my mouse being so old. It's just a blue 3-button Logitech (middle button being the scroll wheel) and it's about 7-8 years old. Thank you!

---

### Post by StarryTripper on 2009-01-19
> **AgentWD-40 said:**
> Could you please show me what your settings look like? Maybe it has something to do with my mouse being so old. It's just a blue 3-button Logitech (middle button being the scroll wheel) and it's about 7-8 years old. Thank you!

Here you go, I attached it!

I bet there's a way to just get the numbers from a config, but I don't know where/how.

---

### Post by doehlers on 2009-01-20
It would be nice if they made the x server mouse code exactly the same as the windows to allow the acceleration to be removed along with options for changing the mouse refresh rate from 125 250 500 in the gui. 

In the mean time see if its possible to use DGA mouse with wine. I tend to use DGA mouse input for all linux games that support it. If wine has support for it as well then it should remove the mouse acceleration.

---

### Post by AgentWD-40 on 2009-01-20
> **StarryTripper said:**
> Here you go, I attached it!

I bet there's a way to just get the numbers from a config, but I don't know where/how.

Thank you for uploading that image. My settings look almost identical to what you have. I've set up Ubuntu 8.10 on PCs for a few other people, but none of them have had this same problem. It's pretty strange. Could it have something to do with my motherboard/chipset (DFI LanParty UT) or USB? I've tried swapping USB ports, but that didn't help any. Somebody suggested booting a Fedora Core CD to see if the same thing happens there. I'm also tempted to just buy a new mouse for the sake of troubleshooting.

---

### Post by AgentWD-40 on 2009-01-20
> **doehlers said:**
> It would be nice if they made the x server mouse code exactly the same as the windows to allow the acceleration to be removed along with options for changing the mouse refresh rate from 125 250 500 in the gui. 

In the mean time see if its possible to use DGA mouse with wine. I tend to use DGA mouse input for all linux games that support it. If wine has support for it as well then it should remove the mouse acceleration.

That would be awesome if they fixed up the mouse code, but apparently this issue doesn't exist among all Ubuntu PCs. I'm hoping it will be better in the next distro. I'll try DGA Mouse with Wine if things get too annoying, but I'm trying to avoid Wine altogether if possible. Thank you for the help!

---

### Post by xzero1 on 2009-04-20
> The sensitivity slider has in the Mouse Preferences Window has NO effect at all, or I'm guessing it affects how much mouse acceleration you get (which I do not want)]I have posted a bug report about this. You could help to resolve the issue by posting in this report. This has not been fixed in Jaunty and will probably be ignored until enough people are interested in it.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/357204](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/357204).

---

### Post by Azure.Rise on 2009-04-20
Just did xset m 0 0 and my mouse (mx518) is still pretty damn sensitive when set to the highest sensitivity on it. Gonna try it in game later.

---

