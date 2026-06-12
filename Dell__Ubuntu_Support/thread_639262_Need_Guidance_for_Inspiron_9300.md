---
title: "Need Guidance for Inspiron 9300"
date: 2007-12-13
forum: Dell  Ubuntu Support
---

### Post by Artsaypunk on 2007-12-13
Anyone out there have an Inspiron 9300 with Gutsy installed?

Well, I do, and I'm looking for some help.  I installed gutsy about two weeks ago and I'm really loving it.  However, I have run into numerous problems, most relating to the Dell Hardware.

I've figured out how to fix some of the problems, others I'm having more trouble with.  Since I'm a newcomer to Linux and Ubuntu, I'm never sure if I've solved something "correctly" or in the best way.  Tweaking involves a lot of trial and error for me, and I want to make sure I get things right.  I would like to figure out as much as I can, do a fresh install and apply everything once and for all.  

So, if anyone has already been through all this with their machine, could you let me know what you had to do to get everything running up to snuff?  If not, perhaps this can be the start of a thread for those with similar laptops.

---

### Post by Artsaypunk on 2007-12-13
Here are some of the issues I've run across.  The frustrating part is that it seems like every time I fix one, another one crops up.

I'm at work right now, so this will be from memory.  Apologies, I'll update when I get my hands on my list at home.


Issue 1:  Extremely Long Boot Time with a Black Screen.
Problem: Plain blank screen with no ubuntu logo, taking a good 2 minutes to load.
Fix:      I fixed this with help from [this]("http://ubuntuforums.org/showthread.php?t=580903&highlight=slow+boot+weird") thread.  Now I'm down from a 2 minute boot to 30 seconds, with the splash screen.

Issue 2:  ATI Mobility Radeon x300
Problem:  Apparently ATI cards are just a problem in general, but getting better.
Fix:  I followed the instructions [here]("http://ubuntuforums.org/showpost.php?p=3547657&postcount=7") to load the restricted drivers from the repository and install compiz.
Questions: Things are working, but not all that great.  Compiz effects are a bit choppy, and so is full screen video; 3d screensavers crash immediately.  Perhaps there are some settings for fglrx I could try?
Note: I also followed the wiki and installed the new, proprietary ATI driver.  I found it didn't help matters and made things run even worse.  After which, I did a fresh install and started over.

Issue 3: Monitor and Resolution questions
Problem:  I don't know if the default configuration for my monitor and resolution are good enough, or if I should attempt to change them... wide screen for example.

Issue 4: Sound Mixing Issues
Problem:  It seems the internal speakers and the subwoofer have independent volumes, so when you first install, pressing mute only mutes the speakers and not the subwoofer.
Fix:  Well, you can kind of fix the problem by right clicking on the Alsa Mixer volume control and selecting preferences.  Then you can hold down cntrl and select whichever sliders you want the master volume to control.  Master Mono seems to be the subwoofer.
Questions:  One thing this laptop does have going for it is decent sound quality.  Are there any alternate solutions, that will mix the subwoofer properly?  I don't think subwoofer volume is normally set to the same volume as the master.  Or am I wrong?

Issue 5: Media Buttons
Problem: Mute, Vol Up, Vol Down, and Play/Pause seem to work on install.  Rewind, Fastforward and stop do not.
Fix: None as yet.
Questions: After you link the volume controls described above, the volume controls work ok.  Any recommendations?  I've tried keytouch and found that it generally made life more difficult, and I could no longer link the volume controls together.

Issue 6: Firefox and Flash
Problem:  I know this isn't a Dell issue, but I spent so much time finding an answer, I figure that if someone finds it faster here, it'll make it worthwhile.  Firefox tries to download the flash plugin, but continues to ask for it, all the time telling you that you already have it installed.
Fix:  Turns out Firefox (or synaptic) doesn't install the plugin, but it doesn't tell you this unless you click on the details (By the way, if that is the case, shouldn't the installer tell you about the failure instead of saying "plugin installed"?)  There is a checksum error between plugin versions and it refuses to install.  To fix it, download the repaired package [here.]("http://ubuntuforums.org/showthread.php?p=3923465")

Issue 7: Keyboard bursts
Problem:  Sometimes, particularly in Firefox, a single keypress will repeat continuously for a whole string of whatever you pressed.  
Fix:  No idea
Questions: This isn't just in firefox, as I had a similar problem yesterday trying out the tetris game included in the install.  There also seems to be delay in scrolling sometimes in firefox.  Perhaps these are related to some other system problem that stalls the resources?

Issue 8: Hard Drive Load Cycle Bug
Problem:  Okay, this sounds like a really scary bug for laptop owners.  How do I find out if I'm affected by it?
Fix:  No idea if it's even a problem

Issue 9: Fan noise
Problem:  I often hear a random fan coming up to speed.  Is this the video card?  I don't remember it happening, or at least not as often, in Win XP.
Fix: No idea if it's even a problem or not

Issue 10:  Wifi Light
Problem:  This is a silly one I'll tack on at the end.  The wifi seems to work gangbusters, I was just wondering if there's a setting to turn the onboard LED on when it connects.

Wow, I remembered a lot more than I thought.  Sorry about the long post, and maybe if would be better to split these all up.  But again, if there is some Ubuntu Guru out there that has already fixed all of these for the Inspiron 9300, I'd be extremely grateful for some advice.

---

### Post by zhouxing on 2007-12-24
I am also running ubuntu 7.10 on Inspiron 9300. Try to use Swiftfox instead of Firefox, then you don't need to bother with flash problems.

[www.getswiftfox.com](www.getswiftfox.com)

---

