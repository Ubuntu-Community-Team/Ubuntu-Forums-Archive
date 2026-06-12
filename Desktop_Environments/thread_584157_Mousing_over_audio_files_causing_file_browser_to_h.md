---
title: "Mousing over audio files causing file browser to hang"
date: 2007-10-20
forum: Desktop Environments
---

### Post by ilh on 2007-10-20
Just done a fresh install of gutsy alongside XP on another partition. When using the file browser, simply moving my cursor over an audio file causes it to hang and so I have to force quit the file browser. Only audio files as far as I can tell, it's happened with wavs, m4as, mp3s and oggs. I can play them fine if I locate them through amarok but the file browser doesn't like them.

Any ideas what's caused this or how to fix it?

Ta

ilh

---

### Post by TeaSwigger on 2007-10-20
Hello, 

Is this on ubuntu and its default file manager, Nautilus? If yes, then I suggest it's somehow related to the nifty but unnecessary feature of playing a few seconds of an audio clip when you mouse over the file. I need to go into ubuntu here to check how but you can turn this feature off until (and if) you care to find out why it's not working right.

---

### Post by TeaSwigger on 2007-10-20
Hello, I'm back with the work-around. Open Nautilus. In the Edit drop-down pick Preferences. Pick the "preview" tab. It lets you chose whether to "preview audio files." Choose "Never." That should do it. Now you can at least work with the files without it hanging.

As for why, that's harder to say. I'm not sure what player it uses, but if you can find out, try that player on its own and confirm it plays those files on its own. Maybe there's an application you removed, or maybe you need to add the codecs etc to play those files? Hope this helps anyway :)

---

### Post by ilh on 2007-10-21
Yea it was the preview thing. Turned it off and now I can hover over the files and move them around and whatnot. Double clicked an mp3 to see what the default program was for it and it was the movie player that came with gutsy. It needed to download the codec plugin GStreamer but that wasn't the cause as I turned the preview back on and tried hovering over the file again and it still hung. Hangs when hovering over ogg files as well which is already on ubuntu isn't it?

Anyways, i'm not too fussed about a preview as I know what my stuff is. Thanks a lot, you're a star! :)

---

