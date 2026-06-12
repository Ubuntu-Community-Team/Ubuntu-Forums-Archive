---
title: "play torrent video while downloading them"
date: 2012-06-14
forum: Desktop Environments
---

### Post by forsubhi on 2012-06-14
I want to play torrent video while downloading them 
how could I do that ?

---

### Post by taylorkh on 2012-06-15
Based on my understanding of how bittorrent works I do not think that is possible. With torrent you are not downloading the file serially from start to finish. Rather you are getting random pieces of the file in parallel. Thus the file will contain only fragments of the video until it is complete.

On the other hand if I download a video from Usenet it is generally in the form of a rar archive. Provided I download the rar pieces in order I can sometimes extract a partial .avi or .ts file or the erly .vob files while the rest is still downloading. VLC player will sometimes play an incomplete .avi.  It will of course play a .ts file regardless of duration.

Ken

---

### Post by 3Miro on 2012-06-15
What taylorkh said.

If a 100 minute video torrent is 99% complete, it does mean that you have 99 minutes of video, but it doesn't mean that you have minutes 1-99. You may be missing one second here, another second there and so on. You may be able to watch the first few minutes, but any player will crash as soon as it reaches a spot that hasn't been downloaded yet.

---

### Post by haqking on 2012-06-15
Depending on your torrent client you can watch it whilst it is downloading using the preview function, the client may or may not let you know if preview is available.

Any preview or player will cease when watching an incomplete download though which is common sense as you cannot view what hasnt arrived yet.

Cheeers

---

### Post by SeijiSensei on 2012-06-15
If the torrent includes multiple files, you can often tell the client which files to download first.  Because of the nature of the Bittorrent protocol, it won't actually just download, say, the first file and ignore the others.  Rather it will give priority to packets from the files you wish to watch first.

---

### Post by drawkcab on 2012-06-15
I thought maybe utorrent has this option in their paid version.  If so, you could run it in wine.  The problem is that playback would still be contingent on the rapid availability of the torrent.  Not sure how this works really as I've never used the paid version.

As others have pointed out, if you're downloading multiple files you can prioritize the ones you want to watch first in transmission so that they're ready to go earlier than the others.

---

