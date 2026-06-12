---
title: "Changing event sounds in 10.04"
date: 2010-05-03
forum: Desktop Environments
---

### Post by yevgeni on 2010-05-03
Ever since 9.04 or thereabouts, I have noticed that it's impossible to change individual system event sounds in System -> Preferences -> Sounds. It only gives me a few lame choices of "themes". While it *used* to be possible to define my own sounds for startup, shutdown, new e-mail, etc, I can't find ANY dialog to facilitate this in newer versions of Ubuntu.

A question: HOW do I do this without having to hack apart my stock system sounds? There should be a way, but google and forum searching turns up nothing. 

A comment: Ubuntu continuing to "nerf" their dialogs like this is infuriating, especially when the underlying system works so well. I actually don't know if Ubuntu or Gnome is responsible, but either way taking *away* rock-bottom basic functionality like this only hurts the OS and Linux's cause.

---

### Post by Nafetitive on 2010-05-07
I feel your pain.
Two upgrades ago I was able to personalize my sounds, now I cannot figure out how. There is no "Sound" option in System>Administration, as well with System>Preferences. I like the most recent upgrade (10.04) "lucid", but am disappointed that they did not bring back the sounds option. I can't even figure out how to change my login/start-up sound. The default Ubuntu start-up sound has lost its lustre with me. I know how to able/disable it, but not customize it.
On a positive note, one of the major things I LOVE about Ubuntu, is that I keep "getting to know" my computer, as though I just got it. I'm never bored. Annoyed, at times, but never bored.
Many Thanks!

---

### Post by tech3g on 2010-05-15
Actually if you check the ubuntu software repository you will find themes and tweaks, it would appear that gnome,kde,and xfce were separated as native support I would have to say that the new system has alot to be desired for hopefully next system

---

### Post by Dr.grUDgE on 2011-01-29
Hey, I am a relative beginner with Ubuntu and even I am looking for a way to assign various event sounds...Is there no one who has done this? 'Coz I couldn't really find anything with Google.:(:mad:

---

### Post by Krytarik on 2011-01-29
@Dr.grUDgE: This should be quite simple:

- make a copy of "/usr/share/sounds/ubuntu"
- give it a desired name
- edit the file "index.theme" in it (open it from within the text editor)
- enter the chosen name instead of "Ubuntu"
- place your custom sounds in the subdirectory  "stereo"
- rename them according to existing ones, after renaming/deleting each existing one before
- check/correct the permissions accordingly
- select your newly created sound theme via "System -> Preferences -> Sounds"

Greetings.

---

### Post by Dr.grUDgE on 2011-01-30
ok..i'll try that, but what about if I want to define a sound for some event other than these, for eg. like for opening folders, etc. Can this be done with this method? What should I name the sound files if yes?
Thanx in advance :)

---

### Post by Krytarik on 2011-01-30
> **Dr.grUDgE said:**
> ok..i'll try that, but what about if I want to define a sound for some event other than these, for eg. like for opening folders, etc. Can this be done with this method? What should I name the sound files if yes?
Thanx in advance :)
I don't believe that it's possible, but you may google that, if you have the leisure.;)

---

### Post by alfh on 2011-02-11
> **Krytarik said:**
> @Dr.grUDgE: This should be quite simple:

- make a copy of "/usr/share/sounds/ubuntu"
- give it a desired name
- edit the file "index.theme" in it (open it from within the text editor)
- enter the chosen name instead of "Ubuntu"
- place your custom sounds in the subdirectory  "stereo"
- rename them according to existing ones, after renaming/deleting each existing one before
- check/correct the permissions accordingly
- select your newly created sound theme via "System -> Preferences -> Sounds"

Greetings.

Like always, its possible to change stuff, but to have to edit text files to customize sounds feels a bit awkward - especially knowing how simple it was just a few distros ago. I can understand design decisions to make things simpler, but at least give users an option to "revert" to older behaviour.

---

### Post by Krytarik on 2011-02-11
> **alfh said:**
> Like always, its possible to change stuff, but to have to edit text files to customize sounds feels a bit awkward - especially knowing how simple it was just a few distros ago. I can understand design decisions to make things simpler, but at least give users an option to "revert" to older behaviour.
I agree. Though I don't know the history of the system sounds, since I always turn them off completely. But as you will probably know, it's a similar case with the ability to customize the login screen.

---

### Post by RifRaf1961 on 2011-07-02
There is a quite easy way to change the annoying drum beating sound at login for 10.04 (Lucid). First get the path to the sound file you want to use. Then System->Preferences and then "Startup Applications".  Scroll down to "GNOME Login Sound" and double click it. It has the familiar [Browse] button to search for the sound file you want. Don't use it! Using the browse button will wipe out the preceding command in the command box. There is no option to revert to the original sound either. I had to boot my Lucid CD in test mode to get the command that was missing and it is fixed now.

This is what needs to be in the box to change your startup sound:

/usr/bin/canberra-gtk-play --file=[COLOR="Red"]/path/filename[/COLOR]

Obviously, change the [COLOR="Red"]/path/filename[/COLOR] to the path and filename of your file. For example, mine happened to be:

/home/rif/sounds/lightstrike.wav

This WILL NOT change any other system sounds. So depending on the theme you chose, you will still be stuck with all those other defined sounds. I haven't attempted the method described by "Krytarik" yet though... so there is still hope. BTW, some sounds are controlled by programs, such as new mail arrival detection.

---

### Post by RifRaf1961 on 2011-07-02
I'm sorry... My previous post gave misleading information initially if followed and I corrected it with a second post. I soon after decided to just correct the initial post and delete the second. I fixed the first but it looks like I only have edit rights, not delete. The edit button says, Edit/Delete when mouseovered, but it just goes into edit mode. It's most likely operator error on my part, but I don't see how to delete this message

---

