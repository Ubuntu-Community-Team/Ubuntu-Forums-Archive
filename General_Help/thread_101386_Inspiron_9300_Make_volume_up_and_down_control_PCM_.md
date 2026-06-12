---
title: "Inspiron 9300: Make volume up and down control PCM instead of Master volume."
date: 2005-12-09
forum: General Help
---

### Post by kwaanens on 2005-12-09
I'm running Breezy on a Dell Inspiron 9300.
There's no problem in getting the volume keys on the front of the computer work, but they control Master. That channel is for the main speakers, and the subwoofer is not affected, as it is on channel Master Mono. Does anyobody know how I can set them to control PCM instead?

- Ketil

---

### Post by sherman on 2005-12-25
*Nudge*

Does anyone know how to solve this issue?!

I have been searching ubuntuforums and notebookforums for a fix, but all I get is people asking for a fix, and people agreeing theres a problem...

I dont like to make threats, but VISTA IS JUST AROUND THE CORNER PEOPLE! This is an awesome OS, I really enjoy using it (especially the sudo feature ;), but if this is not solved... well... what can I say?

---

### Post by kwaanens on 2005-12-25
[QUOTE=sherman]I dont like to make threats, but VISTA IS JUST AROUND THE CORNER PEOPLE! This is an awesome OS, I really enjoy using it (especially the sudo feature ;), but if this is not solved... well... what can I say?[/QUOTE]

Are you kidding?!?
I mean, the volume button problem is annoying, that's why I started this thread. But... *This* will be what pushes you towards MS? Geez... 
Call mr. Gates and tell him to forget about open software. We don't care! External volume buttons are the most important feature!

:)

- Ketil

---

### Post by scelter on 2007-01-13
Somebody found a solution yet?

---

### Post by kwaanens on 2007-01-13
Nope, no such luck :(
And this was first present on Breezy, through Dapper, and now I'm on Edgy with the same problem.
However, I've learnt to live with it.

- Ketil

---

### Post by EnigMattic on 2007-05-27
**_PANEL VOLUME CONTROL:_**
1) Right-click the volume controller on the panel, hit 'Preferences' 
2) CTRL+Left-click 'Master', 'Master Mono' and 'PCM'
3) Close
[B][U]
FRONT PANEL BUTTONS:[/U][/B]
1) Go to *System --> Preferences --> Sound*
2) In the '*Devices*' tab, under '*Default Mixer Tracks*' use **_CTRL+Left-click_** to select  '**Master'**, '**Master Mono**' **_and_** '**PCM**'.
3) Close the *Sound Preferences*.
4) Check the controls on the front of your *Inspiron*
5) :guitar: **_Worship me as your God._**  :guitar:

---

### Post by aBitLater on 2008-02-14
> **EnigMattic said:**
> **_PANEL VOLUME CONTROL:_**
1) Right-click the volume controller on the panel, hit 'Preferences' 
2) CTRL+Left-click 'Master', 'Master Mono' and 'PCM'
3) Close
[B][U]
FRONT PANEL BUTTONS:[/U][/B]
1) Go to *System --> Preferences --> Sound*
2) In the '*Devices*' tab, under '*Default Mixer Tracks*' use **_CTRL+Left-click_** to select  '**Master'**, '**Master Mono**' **_and_** '**PCM**'.
3) Close the *Sound Preferences*.
4) Check the controls on the front of your *Inspiron*
5) :guitar: **_Worship me as your God._**  :guitar:

This is a great work-around, and thanks for posting it.  But, *master* volume should already control PCM.  This work-around makes it so the sliders slide PCM as well as Master volumes.  Master volume is still not fixed.

I saw an article on another website that said Master volume may not work if your hardware doesn't support it.  My HP Pavilion dv8000 is about a year-and-a-half old (purchased May, 2006), and is new enough that this shouldn't be a problem.  Besides, Master volume works fine in MS Windows.  I'm inclined to think this is a software problem with Gnome or ALSA or Linux or something in-between, though I don't understand enough about the issue to know for sure.

---

### Post by fbuchele on 2008-03-03
Theres definately a software problem, it worked fine for me on fiesty, but broke when i (*groan*) upgraded to gutsy.

But the workaround works great! thanks!

---

