---
title: "problems adding launcher for Terminal, Sound Widget not retaining Mute"
date: 2009-07-22
forum: Desktop Environments
---

### Post by Mutant Sushi on 2009-07-22
I'm a complete newbie to Linux...

**1)** I want to create a "Launcher" widget for the Terminal (sounds pretty reasonable, right?), but I've run into "insane" problems doing so:
I've used every application name possible I can think of to enter as the "command" in the Launcher Preferences ("Terminal", "terminal", "xterm", "bash") but I still doesn't work.  EVEN WIERDER, from within Terminal itself (opened from Applications>Accessories) when I type "Terminal", it reponds: (approximately) "Terminal is not installed... Install pkg blah blah".  The Applications>Accesories Terminal seems to offer NO alternate preference/info (i.e. via right-click) that I could identify the 'correct' file name/location/etc.

**2)** The sound control panel seems to retain the VOLUME SETTING, but it seems incapable of retaining the MUTE SETTING, or at least the Mute "Badge" disappears.  What the hell?


*There are some other issues I've run across so far, that I've at least found a work around for, but seem such basic problems, that I wonder if they're being worked on for next release, there IS a better (not in standard install) solution I couldn't find, or what...  If you're interested, I'm mostly judging this from much experience with Apple/OSX, though these are not about 'advanced' functions or fancy presentations, but basic stuff I would have expected 15+ years ago:*

I installed a bunch of apps/packages including codecs, AcidRip DVD Extractor, Audio CD extractor, Rhythmbox, possibly MPlayer (I'm not sure if it was already installed), but after those were installed, when I clicked on the Volume Widget (to re-mute it, as per above), I get an error message about some dependency issue with GStreamer (I believe)  ...But that now seems to have gone away with no action from me and it works 'normally'.  What the hell was that?

Using OpenOffice I am immediately confronted by a font menu overloaded with non-Western fonts.  Don't get me wrong, it's a great idea to HAVE these fonts available, mainly for when I come across web site in foreign scripts.  But HOW is it useful to have these in the same menu?  Why isn't a global Language setting implemented so (if in Western mode) non-Western fonts aren't displayed as options? 
The only 'solution' I found suggested from Linux forum was Fontmatrix, but all that does is 'activate' or 'deactivate' fonts - Which defeats (my) purpose of having the fonts in the first place, since in the occasional times I come across a foreign script website, and maybe even want to copy & paste into Google Translate, I would have to manually turn the fonts back on.  I ended up just removing them (saving them in my documents folder)... Which leads to my next issue:

To do that, I needed to move fonts out of their normal folder to my user folder, which required root.  To do that, I needed to open Terminal and sudo Thunar... WTF!?!?  When I install packages/change certain preferences, the relevant process just asks me to authenticate:  What is the impediment to Thunar doing this, i.e. in the same popup it uses currently to display a permissions error?  Why not have a GLOBAL function for this, so ANY process that attempts something needing higher permissions would automatically be intercepted with an option to authenticate (and complete the action if you provide root password).  ???
 
Also, while writing this very post, a huge issue comes up:  Apparently it's impossible to type any signifigant amount without the cursor CONSTANTLY switching place (typing in wrong line) or even selecting and deleting text, or scrolling down page (in browser).  This is INSANELY irritating! (I activated "prevent Focus stealing" but it hardly seems to do much)

Another wierd thing: I have bad eyes and I'd prefer a larger cursor.  That's apparently a core feature/option, but when activated, the large cursor will instantly 'flip' back to standard size over menus and some applications, which is so jarring I don't use this feature.  I get that there may be different GUI/display sub-systems i terfacing, but coming from OlSX experience, that actually sounds very familiar (with Cocoa/Carbon, PowerPC emulation, etc).  If there actually is multiple cursor image resources for different sub-systems, why doesn't the mouse preference modify ALL of them, much less sym link/alias to a single 'master' cursor resource?  That doesn't seem so advanced, but if there IS a difficulty somehow, why include such features that only HALF WORK?

---

### Post by Mutant Sushi on 2009-08-03
help?

---

### Post by john.nicholls on 2009-08-04
My launcher command for (Xfce) Terminal is:
```
exo-open --launch TerminalEmulator
```

---

### Post by Mutant Sushi on 2009-08-05
thanks, that works for me too.
i don't know what all the "exo launch --" stuff is for,
or why the firefox/help launchers don't have those terms, but i have what I need now!

---

