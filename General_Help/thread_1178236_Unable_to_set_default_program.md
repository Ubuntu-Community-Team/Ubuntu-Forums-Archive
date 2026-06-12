---
title: "Unable to set default program"
date: 2009-06-04
forum: General Help
---

### Post by Agent Smith on 2009-06-04
Hello. Could someone point me in the right direction of how to set mplayer to become the default dvd player. I have changed the "defaults.list" file,  but am still unable to set it up. It does not show up in nautilus when i goto "edit, preferences, media, dvd. Any help would be appreciated. Thanks Jon.

---

### Post by mcduck on 2009-06-04
> **Agent Smith said:**
> Hello. Could someone point me in the right direction of how to set mplayer to become the default dvd player. I have changed the "defaults.list" file,  but am still unable to set it up. It does not show up in nautilus when i goto "edit, preferences, media, dvd. Any help would be appreciated. Thanks Jon.

In Nautilus media preferences select "Open with other Application" and mplayer should appear in the list of available applications. If it doesn't, clikc the "Use a custom command"-option near the bottom of the dialog and set it to "/usr/bin/mplayer"

---

### Post by Agent Smith on 2009-06-04
Where do you mean exactly, as nautilus doesnt give me any options to open with other application.

---

### Post by mcduck on 2009-06-04
> **Agent Smith said:**
> Where do you mean exactly, as nautilus doesnt give me any options to open with other application.
The last entry in the list of available applications dropdown box.

I have following options in that box:
[LIST]
[*]Ask what to do
[*]Do Nothing
[*]Open Folder
[*]Open Movie Player
[*]Open Disc Copier
[*]Open VLC Media Player
[*]Open with other Application...
[/LIST]

---

### Post by Agent Smith on 2009-06-04
If i choose an .avi file i have the ability to open with other application, but not when i put a dvd in. I only get the standard open folder, do nothing, or open handbrake. If i right click the mounted dvd icon, i only get open, or open with handbrake.

---

### Post by mcduck on 2009-06-04
> **Agent Smith said:**
> If i choose an .avi file i have the ability to open with other application, but not when i put a dvd in. I only get the standard open folder, do nothing, or open handbrake. If i right click the mounted dvd icon, i only get open, or open with handbrake.

I'm not talking about the right-click menu in Nautilus, I mean the media options in Nautilus preferences.

In Nautilus, Edit/Preferences, Media-tab.

(In older Ubuntu versions the same settings were accessed directly in System/Preferences/Removable Drives and Media, I can't really remember when the settings moved under Nautilus preferences so check the Preferences menu if you don't have this tab in Nautilus preferences..)

---

### Post by Agent Smith on 2009-06-04
I went to the media tab in preferences first but i still ony have the open folder, ask what to do, or open with handbrake. There are no other options.

---

### Post by mcduck on 2009-06-04
> **Agent Smith said:**
> I went to the media tab in preferences first but i still ony have the open folder, ask what to do, or open with handbrake. There are no other options.

OK, it seems that the option is not there in 8.04. I can only but recommend upgrading to later Ubuntu release, but if you don't want to do that could you explain in detail what modifications you have done to defaults.list?

..or perhaps this will help: [http://ubuntuforums.org/showthread.php?t=895589]("http://ubuntuforums.org/showthread.php?t=895589")

---

