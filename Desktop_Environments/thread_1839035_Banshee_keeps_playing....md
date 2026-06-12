---
title: "Banshee keeps playing..."
date: 2011-09-04
forum: Desktop Environments
---

### Post by jim_naisium on 2011-09-04
Hi,

I like using the Banshee music player for playing music on, it works fine for playing music the problem that I have with it is that when I close it whatever song happens to be playing just keeps on playing as though the window was still open the only way that I can get it to stop is to do a logoff or a shutdown.

How do I get it to stop?

---

### Post by mc4man on 2011-09-04
What release of ubuntu are you using? & is banshee in your sound menu (indicator-sound

If banshee is in the sound menu indicator then when you close it with a track playing it just minimizes to the sound menu and keeps playing, you need to stop the track, then close banshee

If banshee isn't seen in sound pref,'s but keeps on playing after closing w/ a track going then it's likely the "Sound Menu Integration' **extension** is enabled but the 'Show Banshee in the sound menu' **general option** isn't

---

### Post by drs305 on 2011-09-04
If you are using Oneiric (but forget to post in the Ubuntu+1 forum), click the pause key first and then shut it down. Hopefully it will be fixed by the release date in October.

Added later: See post #12

---

### Post by jim_naisium on 2011-09-05
I am running Ubuntu v11.04.

Pardon me for being Mr. Obvious but when you close a program it is supposed to end everything it does and close.

Like Firefox doesn't keep the website you were just on displayed on the screen, a JPG doesn't keep the picture on the screen, and a music player shouldn't keep playing the music when you close it. "Movie Player" also plays music files and when I close it the music that was being played instantly stops, therefore Banshee' should also stop playing music when it is closed.

I have no idea what "Oneiric" is.

Banshee' is listed in: / Applications / Sounds and Video / Banshee Media Player /

I found it (thank you mc4man) the setting for "Show Banshee in the Sound Menu" was checked, I unchecked it when I closed Banshee the music instantly stopped.

---

### Post by coffeecat on 2011-09-05
> **jim_naisium said:**
> 
Pardon me for being Mr. Obvious but when you close a program it is supposed to end everything it does and close.

Closing a window is not necessarily the same as closing a program. That particular paradigm is a Windows thing. As you have discovered, when Banshee is integrated into the sound menu, simply closing the Banshee window does not close Banshee the process.

Nevertheless, I agree with you that the perceived behaviour is inconsistent with that of other applications. From drs305's comment, it seems that the inconsistency may be fixed in Oneiric. Oneiric, by the way, is part of the code name for the upcoming 11.10 release. 11.04 = Natty Narwhal; 11.10 = Oneiric Ocelot. You did not state in your OP which version of Ubuntu you were using. It is always helpful to do so, since features differ from release to release.

---

### Post by mc4man on 2011-09-05
> **drs305 said:**
> If you are using Oneiric (but forget to post in the Ubuntu+1 forum), click the pause key first and then shut it down. Hopefully it will be fixed by the release date in October.

Is there something that mentions this? As far as sound menu integration banshee acts as specified so don't see what is 'fixable' there.
(other than providing a 'quit' option in banshee vs. only having a close window

---

### Post by drs305 on 2011-09-05
> **mc4man said:**
> Is there something that mentions this? As far as sound menu integration banshee acts as specified so don't see what is 'fixable' there.
(other than providing a 'quit' option in banshee vs. only having a close window

My comment was based on what I've seen in the U+1 forums. Users were posting that Banshee wouldn't stop playing the tune *in Oneiric* and I believe several bug reports were made. Having not used Banshee prior to Oneiric I don't know how it behaves in earlier versions, but from the comments it appeared that in previous versions the music *stopped* although the *process* might still be running in background.

---

### Post by coffeecat on 2011-09-05
> **drs305 said:**
> Having not used Banshee prior to Oneiric I don't know how it behaves in earlier versions, but from the comments it appeared that in previous versions the music *stopped* although the *process* might still be running in background.

I'm in Oneiric atm because I wanted to remind myself what goes on. With Banshee open and playing, if I click on the X close button, or Media menu -> close, or right-click on the launcher icon -> Quit, the music keeps playing. I can see why people are saying that this is a bug, even though the behaviour is consistent with it being integrated into the sound menu. I would like a way of stopping the process short of killing it in the terminal.

If I remember correctly this is exactly the same as in Natty, but I shall reboot into Natty to check this.

(OT - I like the way Oneiric's Banshee detects my WD fileserver and can stream music from it without any configuring at all. I don't remember that in Natty. Nice one!)

---

### Post by coffeecat on 2011-09-05
> **coffeecat said:**
> If I remember correctly this is exactly the same as in Natty, but I shall reboot into Natty to check this.

In Natty now. Banshee close behaviour is this:

> With Banshee open and playing, if I click on the X close button, or Media menu -> close, or right-click on the launcher icon -> Quit, the music keeps playing.

... the same as in Oneiric.

Oh, and no sign of my WD fileserver in Natty's Banshee. I'm beginning to like Oneiric more and more! :)

---

### Post by drs305 on 2011-09-05
> **coffeecat said:**
> In Natty now. Banshee close behaviour is this:
... the same as in Oneiric.

Oh, and no sign of my WD fileserver in Natty's Banshee. I'm beginning to like Oneiric more and more! :)

Thanks for checking. 

I suspect the bug reports are from users, like me, that didn't use Banshee in earlier releases.

I've been using Oneiric almost exclusively for a few months and have had very few problems with it. :P

---

### Post by mc4man on 2011-09-05
During 11.04 dev there were a lot of issues w/ sound menu support in banshee, I believe they were all resolved by release (and or w/ a SRU update if the SRU has made it out of natty-proposed...

Can't see much changing about how to exit banshee or rhythmbox when using the sound-menu, would be nice if the sound-menu could close (quit) players, though don't think that was ever  mentioned in the design.

(Atm banshee seems pretty good in 11.10 - for me this is the most bothersome current bug 
[https://bugs.launchpad.net/banshee/+bug/834933](https://bugs.launchpad.net/banshee/+bug/834933)

---

### Post by pmontrasio on 2011-09-10
The workaround is Edit, Preferences, untick Show Banshee in the sound menu and it will work as expected.

The default behaviour of Banshee is surprising and very annoying with movies. It could be ok for music (but why should the player force me to use the menu to quit it?) but I was very surprised when the audio of the movie I was watching a few minutes ago kept going on after I closed the window. I see no point in letting me hear the sound and don't let me see the movie. If I close a window with a movie, it should stop and quit.

---

### Post by ckrishna on 2011-09-15
> **pmontrasio said:**
> The workaround is Edit, Preferences, untick Show Banshee in the sound menu and it will work as expected.

This will actually completely remove banshee from sound menu. If you just want it to stop playing after you quit and still want banshee to appear in the sound menu, go to Edit->Preferences->Extensions->Utilities and untick Sound menu integration.
          But I personally think playing after closing the window is a terrific feature. You can always pause it and then close it if you want banshee to stop playing

---

### Post by Copper Bezel on 2011-09-16
I don't understand the use case for the feature, because it just means that for that one application, closing and minimizing do exactly the same thing, and there's no way to just close the program immediately. I'm glad, though, there's a way to disable it in Banshee. No such luck in Rhythmbox. = P

---

