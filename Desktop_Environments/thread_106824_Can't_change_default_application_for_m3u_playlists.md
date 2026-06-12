---
title: "Can't change default application for m3u playlists"
date: 2005-12-21
forum: Desktop Environments
---

### Post by GabrielWolff on 2005-12-21
I ripped a CD with grip.
I got several tracks plus one .m3u file
When double clicking the .m3u the I get the screenshotly attached message.

So I changed the settigs to: open any .m3u file with xmms. But still the same.

The weird thing is: When I right click the file, and choose: Open with => xmms, everything's fine.

Whatwhat?

Gabriel

---

### Post by pmj on 2005-12-21
The thing is that when you select a .m3u file it is scanned and compared to the information in the mime database. A valid m3u file should begin with the text #EXTM3U and if you paste that into a text document and save as a .m3u you'll see that it'll open in your music player when you double click it just like you'd expect.

The problem is that almost no m3u playlists in the real world actually has the #EXTM3U text. I guess the creator of this mime type would rather get it "right" than actually get it working.

---

### Post by GabrielWolff on 2005-12-25
Great, worked, thanx

Gabriel

---

