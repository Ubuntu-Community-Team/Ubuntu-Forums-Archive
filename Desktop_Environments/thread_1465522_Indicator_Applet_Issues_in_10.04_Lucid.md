---
title: "Indicator Applet Issues in 10.04 Lucid"
date: 2010-04-29
forum: Desktop Environments
---

### Post by Mad-Halfling on 2010-04-29
I use a widescreen laptop so vertical space is more important to me than horizontal, hence I run my main bar on the right hand side of the screen.  When I upgraded to Lucid, I noticed my battery indicator and volume control had disappeared, and I have since found they they are on the indicator applet.  However, adding this to the panel only shows the bluetooth icon - the applet doesn't work vertically and only displays the icons across (if I move the bar to the top, it displays them all).  Also, how can you hide the individual icons on it - I use only online services for my mail, etc, so the envelope icon is just wasting precious space (and I don't think there will be room for it, once the applet works vertically).

---

### Post by wtalbott on 2010-05-01
Even in horizontal displays, I'm not pleased with the integration of battery power, volume, and the little envelope into one panel applet.  Is there any way to separate those capabilities so I could see how the battery is charged without having to see the volume or envelope?

---

### Post by dagurb on 2010-05-01
I would also like to know this. I have no use for the envelope thing. Also, I used to be able to just mouse over the volume icon to see what it was set to and then scroll to adjust it. The mouseover info doesn't show up anymore so that doesn't work.

---

### Post by jerrylamos on 2010-05-01
> **dagurb said:**
> I would also like to know this. I have no use for the envelope thing. Also, I used to be able to just mouse over the volume icon to see what it was set to and then scroll to adjust it. The mouseover info doesn't show up anymore so that doesn't work.

A whole bunch of us testing Lucid Lynx complained bitterly about the "indicator thing" to basically no satisfactory response.  

There are applets on there that I never use and can't get rid of without taking some of the ones I use with them, and it is a real pain to try to get the ones I want back on without the useless ones.

That's the way Ubuntu development wants it to work.  Bundle stuff together with no regard to what the users want.  Goes against the basic customizable principles that Shuttleworth espoused when he started Ubuntu.

Sorry 'bout that.  We're stuck with it if we run Lucid Gnome.
Jerry

---

### Post by dagurb on 2010-05-01
> **jerrylamos said:**
> A whole bunch of us testing Lucid Lynx complained bitterly about the "indicator thing" to basically no satisfactory response.  

There are applets on there that I never use and can't get rid of without taking some of the ones I use with them, and it is a real pain to try to get the ones I want back on without the useless ones.

That's the way Ubuntu development wants it to work.  Bundle stuff together with no regard to what the users want.  Goes against the basic customizable principles that Shuttleworth espoused when he started Ubuntu.

Sorry 'bout that.  We're stuck with it if we run Lucid Gnome.
Jerry

Wow! If that's the attitude they've taken then maybe I should just switch to Debian or Mint. I can make my peace with moving the window buttons since that's somewhat easily configurable but this simply will not stand.

---

### Post by deja on 2010-05-02
Surely there is a way around this.  We can't be stuck not able to control what shows up on our taskbars.  This isn't Windows.

---

### Post by XubeNoob on 2010-05-02
I agree. With UNR 9.10 I could put the cursor over the battery indicator to check status. Can't do that now for the battery, but doing the same for the wireless indicator right next to it still works. This is progress?

---

### Post by CptPicard on 2010-05-02
And on my new Lucid installation there even isn't a battery state indicator on the indicator applet... I guess I'll be back to KDE pretty soon... but any ideas how to actually configure the indicators on the indicator applet?

---

### Post by CBung on 2010-05-02
Alternatively there is XFCE, I believe they're still doing it right, try Xubuntu... I'm going to be forced to move there now as well...

I'm glad to hear you guys complained bitterly, because I was really upset the last few days about it. I'm sorry to hear they did not pay attention, I am very unimpressed with the new version. It makes absolutely no sense to bundle, or to remove right click functions.

---

### Post by teachop on 2010-05-02
> **dagurb said:**
> Wow! If that's the attitude they've taken then maybe I should just switch to Debian or Mint. I can make my peace with moving the window buttons since that's somewhat easily configurable but this simply will not stand.

Sadly it appears that Mint 9 is also going to use this indicator panel according to their blog post, even though the screen shots seem to still show the more functional versions we are used to.

It is possible to get a functioning volume control restored, but the tooltip battery status for what I can tell is gone.

I am thinking the removal of tooltips is related to a least common denominator, where they remove that capability because you cannot "hover" with a touch screen device - just a guess...

---

### Post by charles_shipp on 2010-05-02
i seen something you could type in the terminal to get rid of the envelope I'll try and find it for you

---

### Post by dl7und on 2010-05-03
[This]("http://ubuntuforums.org/showpost.php?p=9165116&postcount=2") may be what you are looking for...

---

### Post by linuxturtle on 2010-05-03
Ooh, thanks dl7und, that's excellent, and got rid of the annoying/redundant/useless envelope icon.  This whole new indicator scheme is really irritating.  I really miss being able to get power and volume status by simply hovering over the icon.

---

### Post by dl7und on 2010-05-04
On a netbook with netbook remix UI things are even worse: There is usually no taskbar (only 600px vertical) and the space in the menu bar not occupied by open applications is now **entirely** taken by the indicator applet. No way to add any sensor applets...:confused:

Well, at least the envelope is gone, that's a start...

---

### Post by jbcfarina on 2010-05-05
In[ 10.10 ]("http://www.omgubuntu.co.uk/2010/05/mark-shuttleworth-no-gnome-shell-in.html")they will keep this "issue"....:S maybe it's time to grow up and use Debian XD

---

### Post by Theist17 on 2010-05-05
What if we want the envelope back, and never had a battery icon to begin with?

That's my case.

---

### Post by Elzigzag on 2010-05-06
What if I'm  ok  with the envelope thing, the battery indicator AND audio indicator BUT the network/connection indicator is rather odd. When I tried Live CD the network indicator was modern, good taste  (you know, the waves going upwards). But when I finished installing I was appalled to see this old-fashioned icon (two monitors, one behind the other as in Windows, remember?). Don't know what the... went wrong. Can anybody help me? Is there any possibility to re-install just the Indicator Applet?

---

### Post by TariBuntu on 2010-05-07
Hello fellow ubuntees.

Reading all of the above, I felt an urge to also add how frustrating - windozish even - this new indicator concept is...

I hope someone will come up with a way to get our tooltips back sooner or later. It's kind of awkward that I have to open Transmission to see what it's doing - let alone volume and whatnot!

---

### Post by obscenic on 2010-05-10
YES! FINALLY FOUND SOME MINIMAL CUSTOMIZATION!

I had to dig this up because evolution just totally disappeared from the applet one day....

Head on over to /usr/share/indicators/messages/applications

In there you'll find the applications that are listed under the messages icon. You can add and remove them.  Each entry is a text file. The format is just 1 line, and the file should be named the same as the application ie "evolution".
Format: 

```
/usr/share/applications/evolution.desktop
```

etc... You can head on over to /usr/share/applications to check out the name of the application you're trying to add if you're trying to add one that disappeared.

---

### Post by vevel on 2010-05-11
obscenic & dl7und:

Ah, thanks guys. 

I've upgraded five systems to lucid (starting with alphas), and done one fresh install.  Didn't have the issues on the fresh install, but had variations of these indicator problems on all the others.   Looks like the gnome 'typing break' indicator is still not working, but last I saw they were calling this a Gnome problem.    I'm pretty pleased overall though.

---

### Post by vevel on 2010-05-11
> **Elzigzag said:**
> What if I'm  ok  with the envelope thing, the battery indicator AND audio indicator BUT the network/connection indicator is rather odd. When I tried Live CD the network indicator was modern, good taste  (you know, the waves going upwards). But when I finished installing I was appalled to see this old-fashioned icon (two monitors, one behind the other as in Windows, remember?). Don't know what the... went wrong. Can anybody help me? Is there any possibility to re-install just the Indicator Applet?

Yeah, you can even make a whole new 'panel.'  Right click on an empty spot on your existing panel and choose 'Add to panel...' or 'New Panel' to make a new panel.   The main applets I've had to delete and re-add during the course of things were:
Indicator Applet
Indicator Session Applet
Notifcation Area

I've attached screenshots of the 'Add to panel...' screens, just because the 'shutter' app is cool, and it makes nice arrows so well.

You might also want to make sure you are using the same theme that the live CD was running -- if you right click on your desktop, and choose 'Change Background', it will take you to Appearance Preferences, where you can also change the theme. 
Live CD was running either Ambiance or Radiance, I believe.

---

### Post by perky on 2010-05-11
> **CptPicard said:**
> And on my new Lucid installation there even isn't a battery state indicator on the indicator applet... I guess I'll be back to KDE pretty soon... but any ideas how to actually configure the indicators on the indicator applet?

> **teachop said:**
> It is possible to get a functioning volume control restored, but the tooltip battery status for what I can tell is gone.


> **linuxturtle said:**
> Ooh, thanks dl7und, that's excellent, and got rid of the annoying/redundant/useless envelope icon.  This whole new indicator scheme is really irritating.  I really miss being able to get power and volume status by simply hovering over the icon.

I too was annoyed at this... so wrote a [new battery applet]("http://ubuntuforums.org/showthread.php?p=9271002").  There goes a week of my life lol, not a complete loss though, learnt a new language :)

---

### Post by quixote on 2010-05-11
obscenic and dl7und: thanks for the tips!  I'm finally rid of that stupid envelope. 

By the way, dl7und, if you follow the link and follow the instructions there, it also dumped thunderbird on my system.  I don't know if that's something peculiar to my setup, or that's just the way it "works."  I was so desperate to get rid of the envelope (I hate useless stuff clogging up **my** desktop :)) I hit the "yes" anyway.  After reinstalling tbird, everything seems okay, so no harm done, but it's mega-annoying to find yourself uninstalling a critical program!  

Who comes up with some of these loony "dependencies," anyway?  Like the day I was trying to get rid of Evolution, hit "yes" and found out I'd uninstalled Ubuntu-desktop....

---

### Post by Clancy_s on 2010-05-17
obscenic, dl7und & perky: thanks from me too. :)

> **quixote said:**
> By the way, dl7und, if you follow the link and follow the instructions there, it also dumped thunderbird on my system

It wanted to delete thunderbird, a number of libs and a few other things on my system, which I didn't fancy: Thunderbird is my primary email program.

So instead I went to synaptic, searched for indicator-messages and removed that only, which worked.

---

### Post by Elzigzag on 2010-05-17
> **vevel said:**
> Yeah, you can even make a whole new 'panel.'  Right click on an empty spot on your existing panel and choose 'Add to panel...' or 'New Panel' to make a new panel.   The main applets I've had to delete and re-add during the course of things were:
Indicator Applet
Indicator Session Applet
Notifcation Area

I've attached screenshots of the 'Add to panel...' screens, just because the 'shutter' app is cool, and it makes nice arrows so well.

You might also want to make sure you are using the same theme that the live CD was running -- if you right click on your desktop, and choose 'Change Background', it will take you to Appearance Preferences, where you can also change the theme. 
Live CD was running either Ambiance or Radiance, I believe.

Vevel, thank you so much. That was really fun. I followed your guide and get just what I wanted and some new ideas popped up (ready to be tried).

---

### Post by wendall911 on 2010-05-22
To any dev without head lost up proverbial ***:

I logged in specifically to echo what a horrendously horrible idea and implementation the indicator-* crap is. Users are not idiots. Treating them as such, like not allowing me to even MOVE items is idiotic at best. Whoever implemented this doesn't deserve a kudos, but a big FU for creating useless garbage. Any fool can add and remove applets. In fact, it's a very cool system. Screwing it up is just absurd.

And for the last time Evolution is a crap application. There are several better mail applications. Quit trying to cram that **** down our throats. A little variety is good. Provide it as an option, not as the only option without wasting my time removing all that crap.

---

### Post by chaeron on 2010-06-10
> **wendall911 said:**
> To any dev without head lost up proverbial ***...

Nice rant!  I agree on all points.

Lucid has been a big letdown because of this kind of crap that was foisted on us long-time, long-suffering users.  What were they thinking?

Oh!

They obviously weren't!

In any case, there is a way to configure the indicator applet.  I had removed the stoopid envelope (I use Thunderbird, not Devolution), but in doing so, removed the whole indicator applet from my panel.

This post clued me in on how to add back the indicator applet with only the audio/battery indicators showing:

[http://ubuntuforums.org/showpost.php?p=9165116&postcount=2](http://ubuntuforums.org/showpost.php?p=9165116&postcount=2)

Hope this helps a bit.

---

### Post by geoffm on 2010-09-18
I have been so annoyed with the indicator applet that I downgraded to Karmic after a month of putting up with it.

I couldn't stand having to go through 2 submenus to get to show incoming message. When I receive a message in empathy/pidgin I want it to show when I left click in the tray, not having to do 3 clicks.

Same thing when I want to show rythmbox, what's the point of poping a menu when you leftclick and having to go click "show rhythmbox"? Rightclicks are normally used for menus, leftclicks for instant action.

Besides, I want information to appear when I hover the cursor on the app icon.

If they wanted to standardise the use of the system tray or however they call it, they could have done it without forcing a new design. I don't care that application icons in the tray behave differently, they're different applications with different functions, they should behave the way they are most useful and efficient, now the way the OS developers think it should be.

How could they think that having to click around 3 times as much is better interface design? Because now the icons' looks fit better together? I prefer usability over appearence. If this is the direction Ubuntu is taking now, maybe it is not for me anymore...

---

### Post by MichaelBurns on 2011-05-18
I found this thread in a google search for a related "feature", and it reminded me how much I also love the new "theme" of ubuntu.  Shamefully, I also tried to remove the envelope and x bubble icons from my panel, and fortunately ubuntu guided me to the repentance of my sins with the fitting punishment that I deserved.  How dare I attempt to use my computer without social networking; that's blasphemy!  (Never mind that I went through a period of two weeks thinking that I might actually have to fire up the Windows partition in order to configure my wireless to work.)  And what kind of a crazy world have I imagined in which an envelope and a battery are separate items?  Tremendous gratitude to the developers for ignoring the misguided pleas of the wicked testers who sought to alienate the poor defenseless applets from each other. Thank you for reminding me that I should never have a battery without an envelope; sometimes we, as humans, just tend to forget these fundamental truths.  I have a dream that one day all applets will live together in harmony, that no applet will ever have to live in fear of dying alone.  Maybe, instead of calling them applets, we should call them musketeers.  All for one and one for all!

*EDIT: No, seriously, ubuntu is free (of charge, at least).  I have no right to complain, and I will ultimately be forever grateful that it freed me from the Windows beast.  It just becomes increasingly challenging to reconcile what I have understood to be the mission of ubuntu with what each release of ubuntu actually "adds" to the distro.*

---

### Post by Elzigzag on 2011-05-19
> **MichaelBurns said:**
> ...And what kind of a crazy world have I imagined in which an envelope and a battery are separate items?  Tremendous gratitude to the developers for ignoring the misguided pleas of the wicked testers who sought to alienate the poor defenseless applets from each other. Thank you for reminding me that I should never have a battery without an envelope; sometimes we, as humans, just tend to forget these fundamental truths.  I have a dream that one day all applets will live together in harmony...*.*
  
Ha ha ha, you put a smile on my face this morning! I love those moments when one falls into despair (for some Ubuntu-tweaking related issue) and then the Muses come and inspire those poetic lines. It has happened to me too ;-)

---

