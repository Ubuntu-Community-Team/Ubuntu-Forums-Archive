---
title: "Mplayer Problems"
date: 2005-09-02
forum: Desktop Environments
---

### Post by sandmanfvr on 2005-09-02
Ok, I got everything to play from WMV's to MOV's in Mplayer (much better than Totem).  Now I need to know two things:

How can I make Mplayer default?
Why can I not play DVDs?  I get "Mplayer interupted by signal 11in module: video_read_properties.  

EDIT: I searched on this, but when an app locks up how do you kill it?

Thanks. :grin:

---

### Post by sandmanfvr on 2005-09-03
Will nobody help me?  I have searched the forums and I can't find an answer.

---

### Post by plb on 2005-09-03
killall -9 app_name usually does the trick

---

### Post by Hairy_Palms on 2005-09-03
i got the exact same error from mplayer, but if you install VLC i found it played DVDs fine, ive switched to suse for the last few months, but as long as nothings changed im pretty sure vlc will play DVDs

---

### Post by sandmanfvr on 2005-09-03
[QUOTE=Hairy_Palms]i got the exact same error from mplayer, but if you install VLC i found it played DVDs fine, ive switched to suse for the last few months, but as long as nothings changed im pretty sure vlc will play DVDs[/QUOTE]
 Well I installed ALL the codecs and did all the things the Ubuntu users guide said, but Totem and MPlayer will not play DVDs.

---

### Post by sandmanfvr on 2005-09-04
Well I messed Mplayer up, somehow.  I took these commands for xine:

gconftool-2 --type string --set /desktop/gnome/volume_manager/autoplay_dvd_command "xine dvd://"
sudo rm -f /usr/share/applnk/Multimedia/xine.desktop
sudo ln -fs /usr/share/xine/desktop/xine.desktop /usr/share/applications/
sudo cp /usr/share/applications/defaults.list /usr/share/applications/defaults.list_backup
sudo sed -e 's/totem.desktop/xine.desktop/g' /usr/share/applications/defaults.list_backup > /tmp/defaults.list
sudo mv /tmp/defaults.list /usr/share/applications/defaults.list

and replaced "xine" with "mplayer" hoping to get Mplayer the default player, now Mplayer is gone.  I hate Totem and it can't play WMV's or it just won't.  What should I do?  I need to fix this, thanks.

EDIT:  Well I installed Xine and it is now the default player and it plays dvds very nicely.  One thing:  some WMV's don't have sound, but they did under Mplayer, why?  Also the options I can't get to, how do I get to the options, run as root?  Thanks.

---

