---
title: "How do I activate plys preview"
date: 2010-11-14
forum: Desktop Environments
---

### Post by Azyx on 2010-11-14
,,so when the cursor are over an mp3-file it's play the song. have 10.04LTS Ubuntu

---

### Post by mcduck on 2010-11-14
It should work automatically as long as you have the gstreamer plugin with mp3 codec installed. (You know you have that if you can play mp3 files in Rhythmbox or the Movie Player).

If you have the codec, and the previews aren't working, check the file manager's preferences and make sure sound file previews are enabled on the Preview-tab.

---

### Post by Azyx on 2010-11-14
> **mcduck said:**
> It should work automatically as long as you have the gstreamer plugin with mp3 codec installed. (You know you have that if you can play mp3 files in Rhythmbox or the Movie Player).

If you have the codec, and the previews aren't working, check the file manager's preferences and make sure sound file previews are enabled on the Preview-tab.

I canot find it.

---

### Post by Azyx on 2010-11-15
> **mcduck said:**
> It should work automatically as long as you have the gstreamer plugin with mp3 codec installed. (You know you have that if you can play mp3 files in Rhythmbox or the Movie Player).

If you have the codec, and the previews aren't working, check the file manager's preferences and make sure sound file previews are enabled on the Preview-tab.

I have looking in System-->Preference-->Preferred Application and selected 'Totem Movie Player'. I can play mp3 with totem (with visualization), but can't find "preview" anywhere.

If I in 'totem movie player' go to Edit-->Preference there are only General, Display and Audio.....

---

### Post by mcduck on 2010-11-15
> **Azyx said:**
> I have looking in System-->Preference-->Preferred Application and selected 'Totem Movie Player'. I can play mp3 with totem (with visualization), but can't find "preview" anywhere.

If I in 'totem movie player' go to Edit-->Preference there are only General, Display and Audio.....

The option is in the *file manager's* preferences.

I only mentioned Totem as a way of checking if you have the right codec installed.

---

### Post by Azyx on 2010-11-15
> **mcduck said:**
> The option is in the *file manager's* preferences.

I only mentioned Totem as a way of checking if you have the right codec installed.

Ahh. I find it but it shows:..Preference-->Preview Sound files:Preview sound files:'Always'.

:(

---

### Post by mcduck on 2010-11-15
You could try running the following command to test the preview with some file, and post any errors here:

```
totem-audio-preview file:///path/to/audio.file
```
(use a real path and filename, of course)

Also, while that's playing, go to Sound Preferences, Applications-tab, and make sure the volume for "Audio Preview" isn't muted.

---

### Post by Azyx on 2010-11-15
> **mcduck said:**
> You could try running the following command to test the preview with some file, and post any errors here:

```
totem-audio-preview file:///path/to/audio.file
```(use a real path and filename, of course)

Also, while that's playing, go to Sound Preferences, Applications-tab, and make sure the volume for "Audio Preview" isn't muted.

There was no error, and the song plays.....


I search and find that you need to have ICON-ViEW activated, as I never have....Strange, it worked before (on 6.04 or 8.04), with list-view? But then I think I installed something like 123mp3 or something...

---

### Post by mcduck on 2010-11-15
Indeed the preview doesn't work in list view, only in icon or compact view. (I can't say anything about it working in older versions or not, I never use the list view).

You also remember the mpg123/mpg321 thing correct, old Gnome versions used either one of those programs to provide the preview. But these days the previews are instead handled by the totem-audio-preview, which uses gstreamer for mp3 playback.

---

