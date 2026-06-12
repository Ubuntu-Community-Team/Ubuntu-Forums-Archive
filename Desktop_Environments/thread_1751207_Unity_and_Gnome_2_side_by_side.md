---
title: "Unity and Gnome 2 side by side?"
date: 2011-05-06
forum: Desktop Environments
---

### Post by adpads on 2011-05-06
Firstly - I have to say that I don't mind Unity all that much! Certainly not as much as I had expected to, given what I had been reading before the upgrade from Maverick. I'd like to go on playing around with it. However, I would also like to continue to be able to use Gnome 2 sometimes, with Compiz and Emerald, as I have done in the past.

The trouble is that whenever I log into the "Ubuntu classic" desktop, it loads compiz, complete with the Unity plugin. Then I have to disable the Unity plugin manually every time, and do the same (with no panel) whenever I log into Unity.

Is there a way I can configure it to only load the Unity plugin in the Unity desktop, but not in the Gnome 2 desktop?

---

### Post by Krytarik on 2011-05-06
Make sure you have different profiles selected in both sessions:
"CompizConfig Settings Manager -> Preferences (bottom left) -> Profile".

Use "Default" for classic Gnome, and "Unity" for ...well... :P

Greetings.

---

### Post by adpads on 2011-05-07
Thank you very much for directing me to that profile settings page. I hadn't seen that.

How can I set it to load a different profile in each session? I have managed to save two different profiles, but I am not able to make it load one for Unity and one for Gnome.
thanks!

---

### Post by Krytarik on 2011-05-07
Doesn't it remain set for either session?
Generally, it should do so.

---

### Post by Frogs Hair on 2011-05-07
Try CCSM > Preferences > Import / Export. I used this to create a profile to to get my cube running . I exported the default profile and saved in my home folder and imported the new profile after saving changes I made . I was required to rename the new profile . I hope that is helpful .

---

### Post by adpads on 2011-05-07
> **Krytarik said:**
> Doesn't it remain set for either session?
Generally, it should do so.

I'm afraid it doesn't - for some reason it just uses the previously used profile. So if log out from Unity with the Unity ccsm profile loaded, and log into the Classic gnome desktop, it loads the Unity profile.

I have managed to export and import to create a "unity" and a "classic" profile, but the login manager doesn't seem to know to load the appropriate one. I am using kdm - could that have something to do with it?

---

### Post by adpads on 2011-05-14
As it turns out, this does work fine when I switch to gdm - so kdm doesn't seem to be working yet for this at the moment!

I guess we could mark this solved, since the problem has gone away - but is kdm going to be got working in the future?

---

### Post by Krytarik on 2011-05-14
Interesting, thanks for reporting. Sorry for not replying to your earlier question, but I didn't really expect that there is a difference.

Actually, I'm wondering how Compiz gets aware which profile it shall load. The info which session option has been chosen must get somehow passed to it, and it seems KDM doesn't do that.

---

### Post by adpads on 2011-05-17
Sounds like time to file a bug report.. my instinct is to file it against Ubuntu's implementation of kdm, rather than against kdm itself, since for the moment this would be an Ubuntu feature to add to the upstream package.

Even though this functionality is not a part of kdm as it is, it seems to me that Ubuntu could be called broken until kdm functions this way..

---

### Post by wildmanne39 on 2011-05-17
> **adpads said:**
> Firstly - I have to say that I don't mind Unity all that much! Certainly not as much as I had expected to, given what I had been reading before the upgrade from Maverick. I'd like to go on playing around with it. However, I would also like to continue to be able to use Gnome 2 sometimes, with Compiz and Emerald, as I have done in the past.

The trouble is that whenever I log into the "Ubuntu classic" desktop, it loads compiz, complete with the Unity plugin. Then I have to disable the Unity plugin manually every time, and do the same (with no panel) whenever I log into Unity.

Is there a way I can configure it to only load the Unity plugin in the Unity desktop, but not in the Gnome 2 desktop?

Hi a bug report may be needed, I have been running ubuntu classic with compiz for 2 days now and it saves my settings, so it must be an issue with kde.

---

