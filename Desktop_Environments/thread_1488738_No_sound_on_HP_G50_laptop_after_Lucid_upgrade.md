---
title: "No sound on HP G50 laptop after Lucid upgrade"
date: 2010-05-20
forum: Desktop Environments
---

### Post by sdegrace on 2010-05-20
I upgraded to Lucid a week or two ago. Sound has worked fine, then suddenly, yesterday, I have no sound for any application. The Gnome sound applet shows the volume normally, and have the Mute All option greyed out (not selectable). Nothing stands out as wrong or unusual under sound preferences, and I didn't change anything, although I did recently install a set of updates. There is no physical mute button on this laptop. IT is not account-specific, there are no sound effects even before you log in.

As well, since the upgrade I have intermittently not had the networking icon in the notification area appear, it is covered over by a fragment of some other graphic. It is most usable with the Human these, it is completely unusable with any of the new themes.

Anyone know a fix for either of these two issues, especially the first?

Finding Lucid extremely flaky, particularly the signature themes. I like some aspects of it, such as the fact the wireless button on my laptop works now, but overall, not an impressive effort - someone whose first introduction to Ubuntu is Lucid and sees that the notification area doesn't even work correctly is not likely to stick around.

---

### Post by UnknownFear on 2010-05-20
Seems like you and I have the exact same problem! The mute all is greyed out as well on my end. Really hope there is a fix for this.

---

### Post by andthewings on 2010-05-20
I experienced the same thing too after I performed the latest update.  Sound came back after I updated but then my background was missing.  I have to agree with you about Lucid.  Perhaps they should have waited a bit longer for a more stable release.

---

### Post by sdegrace on 2010-05-22
My sound is evidently back - for now. I didn't do anything different and multiple reboots didn't fix the problem before - there hasn't even been another update. The only thing that might be different is someone else logged into the computer recently, but I guarantee that he didn't try to do anything.

The thing I hate about these Lucid problems is the intermittency. Intermittent problems are the worst to try and solve.

Another problem I have is that when I try to shut down, sometimes (not predictable) instead of shutting down it logs me out. When it does that you cannot make Ubuntu shut down using the Gnome controls at all, the shutdown from the login screen is ignored and the shutdown from your account just logs you out again. This problem too is intermittent.

Lucid is really lovely in many ways, but I wish Ubuntu would save the ground-breaking stuff that may introduce new problems for ordinary releases and try to be more conservative with LTS releases. Instead it seems like the strive double for the "wow" factor in the LTS releases. I remember having enormous problems with Hardy as well, which didn't really seem to get better until Intrepid.

Doing things this way is not good business, IMO, because if anything, conservative users are going to be encouraged to try the LTS releases, the very releases which we are led to expect will be the most conservative but which are in fact the least. Such users are likely to be very turned off, and it doesn't help Ubuntu's reputation or rate of adoption. I hope Lucid's stability issues are resolved quickly and that we finally learn our lesson.

---

### Post by itkeepsrepeating on 2010-06-06
Same laptop, same issues, with one to add. First, I'll add the problem I was searching for a solution to when I found this post:

Upon adding a monitor, specifically, HDMI out to a vizio tv, sometimes it works, others it doesn't. I'm adding thru the nvidia settings manager. When I say it doesn't work, sometimes there is no obvious effect, sometimes it works more or less fine, and sometimes it blanks the laptop screen, never to return without hard reset.

As far as the sound problem, I've noticed that I can go into the pulseaudio eq, and fiddle with 'enabled' and 'keep settings' boxes to make it come back. 

The network manager can be fixed by opening system monitor, ending the process nm-applet, then alt+f2 and running same applet.

I will say I like the different implementation of the wifi status light on this laptop with the lucid install. It's original purpose [with vista32 OEM] was to be blue for on, red for off. In previous ubuntu distributions, it would stay red all the time, but the button works. Now, it flickers on actual transmitted data rates. I like it, and have no desire to change it, as I first did.

The only other problems with this laptop are heat [I get sudden shutdowns sometimes] and the touchpad button. This button has the opposite problem as the wifi button. The light switches white to red and back, but doesn't actually shut the touchpad off. 

Hope my suggestions helped you with your sound issue, feel free to PM me on the other issues.

---

