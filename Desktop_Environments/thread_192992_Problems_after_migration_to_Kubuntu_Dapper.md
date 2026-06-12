---
title: "Problems after migration to Kubuntu Dapper"
date: 2006-06-09
forum: Desktop Environments
---

### Post by jalefkowit on 2006-06-09
Hey gang...

I've been a happy Ubuntu user since Hoary, but when Dapper came out I thought I'd try something different and see how I liked Kubuntu & KDE instead of Ubuntu & GNOME.  So I blew away my ext3 partition and did a fresh install of Kubuntu Dapper on there.

Mostly it's gone great.  However, there are a few problems that I haven't been able to resolve, even after extensive perusing of FAQs and forums.  So I was hoping maybe someone here could help me out... [-o< 

Here they are:

1) **Printing.**  I have a Lexmark Z43 inkjet printer (I know, I know).  When I first switched to Ubuntu it gave me all sorts of problems, but those were eventually sorted out by using the gimp-print driver, rather than the default z42 driver.  Under my new Kubuntu, though, it doesn't work, even if I choose gimp-print or gutenprint (which, if I understand correctly, is just the latest version of gimp-print).  The best I can get is to choose the gutenprint driver, and this recognizes incoming print jobs and fires up the printer, but nothing actually prints -- it just spits out blank pages.

2) **DVD playback.**  For some reason Kaffeine can play back the video tracks off my DVDs, but there's no audio.  I do get system notification sounds, so I know audio _can_ play.  I saw some forum posts that indicated that the reason might be misconfigured sound card (I have an old Sound Blaster Audigy), so I went into alsamixer to check.  The suggested fix in alsamixer was to turn on the channel marked "Audigy Analog/Digital Output Jack".  I did that, and the result was that *all* audio on my system went away, including notification sounds!  Oops!  So I'm stuck as to what the next step is.  (CDs don't seem to play back either.)

3) **Default browser.**  It's stuck for some reason on using Konqueror as the default browser.  The "set as default" option in Firefox doesn't seem to work, and there's no obvious control panel or config file to set it manually.  How do I make FF my default browser?

Those are the big ones so far... any help that can be provided will be GREATLY appreciated.  Thanks!

---

### Post by Jucato on 2006-06-09
I could only help with the 3rd question, as I have no experience with DVD and Printers (I don't have either).

From the K Menu, choose System Settings. Then click on KDE components. Then choose "Default Application" (left panel) and "Web Browser" (a little to the right). Then for the "Default Component", choose "in the following browser" and put *firefox %u* in there. That should do the trick.

---

### Post by jalefkowit on 2006-06-09
OK, set the Default Component as per your instructions and -- well, this is weird.   Kontact seems to respect that preference and launches FF when I click a link, but Thunderbird (which is my preferred mail client) does not.

Strange!

---

### Post by Jucato on 2006-06-09
Some people are having a problem with that. Someone had a solution I think. Search around the forums a bit (use the search function). It may yield something.

---

### Post by der_joachim on 2006-06-10
[QUOTE=jalefkowit]2) DVD playback. For some reason Kaffeine can play back the video tracks off my DVDs, but there's no audio. I do get system notification sounds, so I know audio _can_ play. I saw some forum posts that indicated that the reason might be misconfigured sound card (I have an old Sound Blaster Audigy), so I went into alsamixer to check. The suggested fix in alsamixer was to turn on the channel marked "Audigy Analog/Digital Output Jack". I did that, and the result was that all audio on my system went away, including notification sounds! Oops! So I'm stuck as to what the next step is. (CDs don't seem to play back either.)
[/QUOTE]

The next step is the undo step probably. Revert to your old settings. At least you'll have CD playback again.  Which audio engine are you using? I'm using the Xine engine with no problems whatsoever. 

[QUOTE=jalefkowit]OK, set the Default Component as per your instructions and -- well, this is weird. Kontact seems to respect that preference and launches FF when I click a link, but Thunderbird (which is my preferred mail client) does not.[/QUOTE]

Here's what I did:
- Open /etc/mozilla-firefox/global-config.js in your favourite text editor.
- Replace the following two lines:
```
pref("network.protocol-handler.app.http","mozilla-firefox");
pref("network.protocol-handler.app.https","mozilla-firefox");
```
by these two lines:
```
pref("network.protocol-handler.app.http","firefox");
pref("network.protocol-handler.app.https","firefox");
```
Or just add them if they aren't already there. Restart thunderbird and you should be fine.

---

### Post by jalefkowit on 2006-06-11
[QUOTE=der_joachim]The next step is the undo step probably. Revert to your old settings. At least you'll have CD playback again. [/QUOTE]

Unfortunately I installed Kubuntu by reformatting my ext3 partition and doing a clean install.  So there is no undo #-o

[QUOTE=der_joachim]Which audio engine are you using? I'm using the Xine engine with no problems whatsoever. [/QUOTE]

Tried it with both of them ("Kaffeine", which I think is Xine, and "Embedded MPlayer"), neither worked.  Interestingly, I ended up grabbing VLC and the DVD played back fine in that, audio and all...

[QUOTE=der_joachim]Here's what I did: (snip) [/QUOTE]

Woo!  That did it!  Thanks!

---

