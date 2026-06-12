---
title: "How to correctly enable the Login sound in Xubuntu 16.04 and new versions"
date: 2016-12-20
forum: Desktop Environments
---

### Post by Roger_Peartree on 2016-12-20
I'm posting this because I discovered that by using the old methods that were posted in the Ubuntu Forum (CLOSED thread here: [https://ubuntuforums.org/showthread.php?t=1869787](https://ubuntuforums.org/showthread.php?t=1869787)) the login sound won't play because the /sounds folder is owned by "root" so it's not possible to play the sound from a user login, it would need "sudo", which is impossible or "root login" which is not advisable. And the other problem is that the "play" binary is not installed in the new Xubuntu (or any other Ubuntu versions), it was substituted by the "aplay" binary, and "aplay" will ONLY play .wav files, not .oga or .ogg as "play" would. Personally I think this substitution was a super wrong way to go. The older "play" would play anything just fine but I'm not a developer...
So that you know, "play" is still used in Linux Mint, and since I use Linux Mint 18 Xfce on my netbook, this tutorial would be much short and simple. But I do love Xubuntu 16.04.1 in my PC!
So here are the steps:

**1** - First we have to take ownership of the /usr/share/sounds folder by opening the Terminal and doing:

[B]sudo chown -R your-username-here:root /usr/share/sounds
[/B]
**2** - Then we need to open "Session and Startup" and go to the "Application Autostart" tab and click on the "Add+" button.
     You'll see 3 fields "Name", "Description" and "Command". I personally used "Login Sound" as Name "Play the login sound" as Description and now the Command is as follows.
     Click the folder icon at the right side of "Command" and then navigate like this: choose File System then /usr/bin and select the "aplay" binary, it's right on top, alphabetically sorted.
That path will appear in the "Command field, so that's the executable player. Then you'll need to give a Space and add the path to your desired login sound, like /usr/share/sounds/...
     Or just copy and paste this into the Command field:
 [B]
/usr/bin/aplay /usr/share/sounds/your-login-sound.wav
 
[/B]But of course first you'll need to place your chosen login sound in .wav format in the "sounds" folder. Just put it into that folder or if you wish to have a collection of different login sounds you can make a sub-folder but then you'll have to change the path to your .wav file in "Command", like /usr/share/sounds/LoginSoundsCollection/login-sound.wav.
     Because Xubuntu only comes with the "freedesktop" sounds, in .oga format ("aplay only plays .wav files!) and there's no login sound there too to convert to .wav and the Alsa .wav files are      not meant for login sounds (just open that folder and you'll see why), you'll have to find a cool .wav file for your login (don't choose a very long one, mine has only 10 seconds but I suppose you can have a little more, like 20 seconds). For this you can choose a good ringtone for instance which are widely available in the Internet for Phones these days, or you can trim part of a song using mhWaveEdit (super simple to operate) or Audacity (a bit more complex to operate) which are already in the Ubuntu Repositories, you can just do: **sudo apt install mhwaveedit**.
Remember that these ringtones are usually in .mp3 format and "aplay" only plays .wav files so, once again, you'll have to convert any file to .wav.
Or you can download a sound theme from the Internet. Here's what I use: [http://pulicoti.deviantart.com/art/Dream-SystemSounds-103772795](http://pulicoti.deviantart.com/art/Dream-SystemSounds-103772795) the download button is in the upper right. This one is a very cool theme but the files are in .ogg format, so you can use mhWaveEdit or Audacity to convert them to .wav. To save you some time I have attached the ZIP file of the theme to this post, it's only 785,5 Kb so it's small, you'll just have to download it and unzip it, you can do "extract here" because you'll need to convert the files, the files you want are either "desktop-login.ogg (this is what I use in .wav format) or desktop-logout.ogg, both are cool but you may not like them so use your freedom of choice and imagination. Converting files is super easy, you just open the .ogg file (or .mp3) that you want in mhWaveEdit and then click "File" and choose "Save as" and in the file manager title bar just change the extension .ogg to .wav. Or use the bar at the bottom to choose "Microsoft WAV" as the format to save to. That's as easy as that!

Once the "Command" is complete and correctly inserted in the field just click "ok" and your new Login Sound entry will appear in the "Application Autostart" menu.
If you wish to change the login sound then just open "Applications Autostart", choose "Login Sound (Play the login sound)", these are my example names for "Name" and "Description" remember? You can have different names, of course, then click the "edit" button and alter the "Command" line of the path to the .wav file you wish to be your new login sound.

Well that's it, it's done the proper way. Now just Log Out and login again to hear your new login sound. Any problems you might encounter just post them on this thread and I'll do my best to solve them, or one of the moderators of the Forum will reply to you (and they know a lot about Linux and Ubuntu, trust me!). Have a nice Login Sound!

---

### Post by oldos2er on 2016-12-21
We have a [Tutorials]("https://ubuntuforums.org/forumdisplay.php?f=100") subforum for this type of post, in the future if you wish to post tutorials please post them there, and be sure they meet our [posting criteria]("https://ubuntuforums.org/showthread.php?t=2143602").

Thanks.

---

### Post by Roger_Peartree on 2016-12-22
I'm really sorry oldos2er! I should have read the "posting criteria", after all I'm a member of the Forum since September 2015 so it's inexcusable. I'm gonna read it now, it's here: [https://ubuntuforums.org/showthread.php?t=2158945](https://ubuntuforums.org/showthread.php?t=2158945) If I could, I would move the post to Tutorials but I don't have the necessary authorization to do it. Perhaps you could do that, but only when you have a little spare time. Being a Super Moderator you must always be busy working plus you have your personal life, so I'll leave that decision to you. Like I said: only if you have some spare time. This post is not very important, I understand that. I wish you a very Merry Christmas and an excellent 2017.
My best regards,

Roger Peartree

---

### Post by oldos2er on 2016-12-22
No need to be sorry, I was just posting "FYI." If you care to, you could develop your tutorial a bit further and then post it to Tutorials, in your own time, of course.

Merry Xmas to you too.

---

### Post by SantaFe on 2016-12-24
I just made a startup entry Called it Startup Sound & put this in the command area: /usr/bin/canberra-gtk-play -f /usr/share/sounds/mate/ome.wav

Of course that's assuming you have canberra installed.  Just point it to the folder where you're sound file is and it should play it upon login.

---

