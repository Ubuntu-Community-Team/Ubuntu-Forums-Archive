---
title: "File icon problems"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by zeroLOGIK on 2008-04-15
I need help reverting a set of file icons back to the default set.

I tried to install RealPlayer, but somehow it failed. All it ended up doing was changing the file icons for audio and video media to a RM style icon. Needless to say this icon set is quite annoying to me for an undisclosed reason and I wish to revert them back to the default icon.

I looked through my installed packages to make sure I removed all of the RealPlayer packages and it seems I did, but I'm unsure. I'm still a fresh convert, so some things are still rather confusing to me, even though I've been using Ubuntu for a few months.

I'm running Ubuntu Linux 7.10 LTS. Any help would be appreciated, and I'm not afraid of the CLI.

EDIT: If this isn't in the right section mods feel free to move it.

---

### Post by Gen2ly on 2008-04-15
This has to do with the mime database settings.  Gnome has a file (or group of files?) that keep list of file types and the applications they belong to.  Looks like Real Player not only hijacked the mime types but didn't revert them back to their previous settings (windows installs do this - drives me friggin' crazy).  I don't see this too often if Linux though.  I never heard of a program that can adjust mime types but I figure there is probably one around.  One way to do this would just to right-click the files then properties and pick the new application to open the file type with in the "Open Width" tab.

---

### Post by erginemr on 2008-04-15
When you right click the desktop and select "Change Desktop Background", you should reach the "Appearance" applet. Try changing the theme to another one, and revert back to, say, "Human".

I f that doesn't work, you can try the "Customize..." button, "Icons" tab to re-select the previous icon scheme.

---

### Post by zeroLOGIK on 2008-04-15
I should have mentioned I already tried the GUI customization prompts. Also, I already tried changing the "Open with" settings and it didn't change the icon.

I also checked my home directory with hidden files shown, and I found a RealPlayer directory. I found some image files in a subdirectory so I just trashed the whole directory to make sure I got rid of the RealPlayer files. It seems that hasn't affected the icons at all though because they remain the same.

Is there any way to directly edit the mime settings to use the default icon?

---

### Post by erginemr on 2008-04-15
May I ask what theme you have been using? Is it a standard theme coming with Ubuntu, or a customized one you have downloaded from, say, gnome-look.org?

Alternatively, can you please try right-clicking on an audio file, select properties, click on its icon and point to the location & icon file I have given in the attachment?

---

### Post by zeroLOGIK on 2008-04-15
I'm using the standard Human theme. The only modification I made is I chose a custom background.

I have tried doing what you asked me to do, but it seems that my scalable icons either weren't there or have gone missing.

None the less, I changed one file's icon from the RealPlayer icon to a GNOME ogg format icon. Should it just change the single file's mime icon, because that's all it did.

EDIT: I almost forgot to memtion that I found no Human mime icons, they don't seem to be there, which seems to be the case for all of the scalable icons. It may be because I haven't installed any extra icon sets. Should I try to (re)install them with aptitude?

---

### Post by erginemr on 2008-04-15
Sorry, you are right. It changes only the icon for that particular single file also in my system. Strange behavior indeed... :-k

There should be a setting somewhere...

---

### Post by zeroLOGIK on 2008-04-15
Is it possible for the mime types to revert to default if I upgrade to Hardy? I wouldn't mind the upgrade, as long as my home directory stays largely in tact.

---

### Post by ajonat on 2008-04-28
I'm having the EXACT same problem with feisty. Real player 11 hijacked all the video/sound icons (except for .avi) and now i can't turn it back to the icon theme I was using (Gion, installed with Gnome Art). Changing themes didn't help and I just don't know what else to do :(

Please help!
Thanks in advance, Alex.

PS: I installed real player without any problem... I just want my original icons back :(

---

### Post by ajonat on 2008-04-29
I found a solution: the problem was that the themes I was using before installing real player had only a generic audio icon "audio-x-generic.png", and apparently the icons provided by real player were more specific (in the mime-type sense, like mp3, wav, etc) so they overrided the generic icon in the theme. The solution was to make a few symbolic links that pointed to the generic audio icon in the theme: audio-mpeg.png, audio-x-mpeg.png, audio-x-wav.png, audio-x-adpcm.png , audio-x-mp3-playlist.png, audio-x-ms-wma.png. The icons are in ~\.icons\[theme]\[sizexsize]\mimetypes.
Besides, you can edit ~/.local/share/applications/default.list to change the default application that open the audio mime-type's.

Have a nice day!
Alex.

P.S. Gnome should have a gui tool to make this easier!

---

### Post by neurostu on 2008-05-20
So None of the options outlined here worked for me, so this is what I had to do. I went to the following dir:
~/.local/share/icons/hicolor/48x48/mimetypes
and found that real player had taken over all of the symbolic links of anything associated with multimedia (THOSE JERKS)!

Anyway I got the file from:
 /usr/share/icons/gnome/scalable/mimetypes/audio-x-generic.svg
and using inkscape I exported it as a png. I then copied it over all of the audio related files in 48x48/mimetypes/ that realplayer had taken.

I know this fix is dirty, I wish there were a way to simply remove all the realplayer crap!  I certainly will not be installing it again when i upgrade to Hardy.

---

### Post by dwasifar on 2008-05-30
To reverse RealPlayer's icon mischief more completely, try the advice in this post: [http://ubuntuforums.org/showthread.php?p=5081742#post5081742]("http://ubuntuforums.org/showthread.php?p=5081742#post5081742")

---

### Post by neurostu on 2008-05-31
Thanks for the tip, I have sense done a clean install of Hardy to replace gutsy. I won't ever consider installing real player ever again after what happened.

---

