---
title: "Snap Apps - are they the same as DEBs. I have a navigation issue."
date: 2018-01-11
forum: Desktop Environments
---

### Post by shag00 on 2018-01-11
I have been using VLC for years and I control it through Remote for VLC  [https://play.google.com/store/apps/details?id=uk.co.samicemalone.client.android.vlcremote&hl=en](https://play.google.com/store/apps/details?id=uk.co.samicemalone.client.android.vlcremote&hl=en) , essentially this is an android app that controls VLC through http.

The android app is fully functional on all versions of VLC downloaded via Synaptic, including the latest daily experimental build, version 4. This being the case I decided to install VLC from the Ubuntu software centre Snap store as I had successfully tested Remote for VLC on my system for VLC versions 3.0 RC5 and 4.0. This Snap store program is identified as ver. 3.0 RC3 (updated 26/12/17) and the app is not functional because I cannot browse most of my directories. My video files are located in /media/pool/Entertainment.

Now I can connect to my PC through the wi-fi interface and I can navigate to Ubuntu root and from there I can navigate to any file or directory in the main user's Home Directory. However I cannot browse any other users Home Directory (which is not a problem) but nor can I browse most other directories from the root directory (I can browse dev, lib, proc, sys, tmp), all attempts give this message, "No files were found. This may be because you do not have permission to access the directory." So I thought it was a simple permissions setting issue but upon checking, all directories in root are owned by root:root with permissions all set at 755. I next tried a link from within my home directory, which I could fully access, to the target directory but it met with the same result.

I am also pretty sure I used a Ver 3.0 RC3 in December and it worked but notwithstanding that there appears to be some difference in the Snap version versus the DEB version. I also strongly suspect that it is not a VLC issue as the interface appears unchanged since ver 2.1 and has worked on many subsequent versions without any need to change the settings on my android app.

Does anyone have more information on this or a possible solution?

---

### Post by deadflowr on 2018-01-12
Something something on snap's confinement designs:
[https://ubuntuforums.org/showthread.php?t=2344079]("https://ubuntuforums.org/showthread.php?t=2344079")

and no snaps and debs are not the same.
something something on that: [https://askubuntu.com/questions/761245/what-is-the-snap-packaging-format]("https://askubuntu.com/questions/761245/what-is-the-snap-packaging-format")

I hope you can glean something useful from those.

---

### Post by shag00 on 2018-01-12
Ah OK, a bug report was made over a year ago but appears there is no progress. Also appears that this restriction may be designed on purpose. I tried to google snap -devmode but got no hits, is there some info on this somewhere do you you know?

---

### Post by mc4man on 2018-01-12
You could try removing the the vlc snap installed thru ubuntu/gnome software
sudo snap remove vlc
Then install from cli using classic option
sudo snap install vlc --classic
(that removes some of the confinement

---

### Post by shag00 on 2018-01-12
Apologies for being a bit dense but I probably need a bit more help. I specifically need VLC version 3 RC3 or RC5 and not VLC version 4 which is still very much in the experimental stage. If I add the VLC ppa i always get version 4 when using synaptic. So my question is how do I get the specific version I want. FYI I need a late version 3 to play UHD movies which are on my server. The DEB version 2.6 also available in Ubuntu Software is also no good to me.

---

