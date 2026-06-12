---
title: "File Structure For Rhythmbox"
date: 2012-10-03
forum: Desktop Environments
---

### Post by Acharn on 2012-10-03
I used to use Media Monkey on Windows XP before my hard drive crashed and I started using Ubuntu. I tried following a couple of tutorials to install it under Wine, but haven't been able to get it to work, so I've accepted that I have to use a Linux music app. I've tried  Rhythmbox, Banshee, and Exaile, and I'm not happy with any of them because none of them allow me to access my music by directories (or what seem to now be called "folders" -- a usage started by Windows which I have never liked).

Anyway, since I had to start from scratch replacing the music I lost, I've been downloading torrents. Most of them are single albums by one artist. I sometimes have to go in and do extensive editing of the ID3 tags. EasyEdit is great for that, better than anything I found on Windows. Lately I have a problem with Rhythmbox not detecting some albums. After Rhythmbox loads if I search for the newly added artist's names they aren't found. The album name is not found. The title of the directory is not found.

Is there some upper limit to the number of subdirectories you can have under the Music directory? What's the best organization to use for my files? Does it matter how individual files are named? Can anyone point me to good discussions of these problems? The documentation I've been able to find doesn't address these questions at all, acting as if it's perfectly obvious to everybody. Most of the discussions I've found have been about how to play poscasts or internet radio, which are not priorities for me.

---

### Post by cryptotheslow on 2012-10-03
I've not come across any directory or file limitations with Rhythmbox with several thousand tracks in many directories.

The filenames shouldn't matter, the ID3 tags are much more important. I've had some tracks which had some odd characters in some of the more obscure tag fields that prevented Rhythmbox importing or displaying them. I had to use a tag editer to clear **all** the ID2 and ID3 tags then repopulate just the useful tag fields back in.

As for how you organise you files - that's very much up to you. Personally I use a directory structure of:

/music/artist/album/

Then for the actual filenames:
*track# artist title*

So you end up for example with:
/music/Eminem/Curtain Call/03 Eminem - The Way I Am.mp3

I find it helpful to start the filename with the track number as even with a basic file explorer the tracks appear in the correct album order.

If you get your ID3 tags correct, there are plenty of automatic tag editors that will whizz through a whole bunch of directories of tracks, renaming each file according to the information in the tags and to a pattern of your choosing.

---

### Post by Acharn on 2012-10-05
Thanks for taking the trouble to reply. I guess I'll just have to keep fiddling with it. I have my albums in ~/Music/Albumname, with one directory names Various for the many single songs I had through Ares (mostly by either searching for titles or for particular artists). So I have, for example, "~/Music/Artie Shaw-Magnum-[TFM]-2011", which contains a subdirectory "Artie Shaw-Artie Shaw[TKO Magnum]", which contains 17 .flac files named by the convention you describe, plus a playlist (.mu3) file and a couple of others. I've worried about the spaces in the directory names, but Rhythmbox has no trouble with them; it finds all these songs fine.

Then I have a collection which just wasn't being seen at all when I had it in the Music directory, so I moved it to another directory named Other, which I use for miscellaneous, mostly video, downloads. Its name is "~/Other/Chess Blues-Box Set (1003). This directory contains five subdirectories: artwork, and disc1, disc2, disc3, and disc4. Each of the "disc" directories contains 25 .flac files, with filenames constructed of track number, song title, and artist. When it was in the Music directory, rhythmbox detected it as four files named "unknown", which I could find by typing "chess" in the search box. No album or artist with "chess" in the name was shown. After I moved it to the Other directory and imported it into Rhythmbox, I have an entry in the album box named Chess Blues, which comtains 100 tracks, four sets of tracks numbered 01-25, with the titles from the four directories. No way to select just one directory, except by manually selecting those tracks and adding them to a playlist. Of course I can select them one by one, too.

I've recently added some more, which just aren't being shown at all in Rhythmbox. It's very frustrating, and Banshee and Exaile do the same thing.

---

