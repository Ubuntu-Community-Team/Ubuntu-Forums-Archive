---
title: "How to change login tune"
date: 2010-08-26
forum: Desktop Environments
---

### Post by satimis on 2010-08-26
Hi folks,

Ubuntu 1004

Can I change the login tune?  If YES please advise how?.  TIA

B.R.
satimis

---

### Post by DavidOfLondon on 2010-08-26
Three answers for you:

"Hi and you can use system, administration, login window and then choose the accessibility tab and change the sound there."

"Actually, I think what you want is in System->Preferences->Sound and go to the Sounds tab on that."

"Found it (KDE)
Click on Control Center > Sound & Multimedia > System  Notifications > then highlight: KDE is starting up. Then - Actions  and tour the various sound files. "

With Ubuntu there is more than one way to skin a cat - unlike with Microsoft, which thinks it knows better than you what colour socks you ought to be wearing.

---

### Post by satimis on 2010-08-26
> **DavidOfLondon said:**
> Three answers for you:

"Hi and you can use system, administration, login window and then choose the accessibility tab and change the sound there."

"Actually, I think what you want is in System->Preferences->Sound and go to the Sounds tab on that."

"Found it (KDE)
Click on Control Center > Sound & Multimedia > System  Notifications > then highlight: KDE is starting up. Then - Actions  and tour the various sound files. "

With Ubuntu there is more than one way to skin a cat - unlike with Microsoft, which thinks it knows better than you what colour socks you ought to be wearing.

Hi 

Thanks for your advice.

I'm running GNOME.

System -> Administration -> Login Screen
Login Screen Settings
There is no accessibility tab

System -> Preferences -> Sound
Sound Preferences
-> Sound Effects tab
Sound them
Only Ubuntu and "No sounds"


B.R.
satimis

---

### Post by JBAlaska on 2010-08-26
Go to **System -> Preferences -> Starup Applications**
Look for **“GNOME Login Sound**” in the list. 
To change the sound, press the edit button. Then in the command field you’ll see

**/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”**

Change **“desktop-login”** to the name of the sound file you want, without a file extension.
Click Save and close.

With root permission, copy your new (.ogg) sound file to:

**/usr/share/sounds/ubuntu/stereo/**


That should do it.

---

### Post by satimis on 2010-08-26
> **JBAlaska said:**
> Go to **System -> Preferences -> Starup Applications**
Look for **“GNOME Login Sound**” in the list. 
To change the sound, press the edit button. Then in the command field you’ll see

**/usr/bin/canberra-gtk-play –id=”desktop-login” –description=”GNOME Login”**

Change **“desktop-login”** to the name of the sound file you want, without a file extension.
Click Save and close.

With root permission, copy your new (.ogg) sound file to:

**/usr/share/sounds/ubuntu/stereo/**


That should do it.

Hi,

Thanks for your advice.

$ ls /usr/share/sounds/ubuntu/stereo/```

bell.ogg               dialog-error.ogg         phone-outgoing-busy.ogg
button-pressed.ogg     dialog-information.ogg   service-login.ogg
button-toggle-off.ogg  dialog-question.ogg      service-logout.ogg
button-toggle-on.ogg   dialog-warning.ogg       system-ready.ogg
desktop-login.ogg      message-new-instant.ogg  window-slide.ogg
desktop-logout.ogg     phone-incoming-call.ogg

```

Changing "desktop-login"
to "window-slide"

Logout and relogin.  NO sound.  Also tried "system-ready" including reboot.  Still there was no sound on login.

Is it only *.ogg file works for Ubuntu?  No .wav and.mp3?

B.R.
satimis

---

### Post by DavidOfLondon on 2010-08-26
I'm assuming your .ogg guess is correct.

Look, the thing is that with Linux OSs you can change these settings and reboot and it won't kill your comp. If an mp3 doesn't work just change it again. 

Google "convert mp3 to .ogg" something will come up.

The beauty is that unlike windows, changing a login tune on Linux won't kill your entire PC.

:)

That's why Linux wins.

---

### Post by satimis on 2010-08-27
> **DavidOfLondon said:**
> I'm assuming your .ogg guess is correct.

Look, the thing is that with Linux OSs you can change these settings and reboot and it won't kill your comp. If an mp3 doesn't work just change it again. 

Google "convert mp3 to .ogg" something will come up.

- snip -


Still fails

$ ls /usr/share/sounds/ubuntu/stereo/```

bell.ogg                dialog-question.ogg
Bizet.mp3               dialog-warning.ogg
button-pressed.ogg      message-new-instant.ogg
button-toggle-off.ogg   phone-incoming-call.ogg
button-toggle-on.ogg    phone-outgoing-busy.ogg
desktop-login.ogg       service-login.ogg
desktop-logout.ogg      service-logout.ogg
dialog-error.ogg        system-ready.ogg
dialog-information.ogg  window-slide.ogg

```

Non of them can work except desktop-login

I think there is another control

System -> Prefereces -> Sound -> Sound Effects (tab)

Sound theme
only - No sounds and ubuntu

selecting ubuntu starts desktop-login tune

ls /usr/share/sounds/ubuntu/```

index.theme  stereo

```

B.R.
satimis

---

