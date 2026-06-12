---
title: "MP3 Tag Writing Problems - Permissions?"
date: 2008-12-02
forum: General Help
---

### Post by jdorenbush on 2008-12-02
This happens with a couple random MP3 files out of my collection. Like 15 out of 1x,xxx or something. I've tried to troubleshoot the problem as much as I could, this is what I have came up with.

Software: Rhythmbox 0.11.6
Music Storage: External HDD
File Type: MP3

Initial Problem
1. While in Rhythmbox I right click on the song in-question and click Properties.
2. Then I change the genre, for testing purposes, lets use 'X'.
3. It changes. A few seconds later it reverts back to what it originally was.

Testing
1. Bring MP3 file from external hdd to my desktop.
2. Bring MP3 file into Rhythmbox.
3. Change genre information. It works this time.
4. Bring MP3 file back to external hdd and import into Rhythmbox. It reverts back to old genre tag.

EDIT: Just noticed that in Songbird there is no problems with displaying the correct genre tag. It only seems to be a Rhythmbox problem.

---

### Post by jdorenbush on 2008-12-05
Bump

---

### Post by SomeGayDude on 2008-12-05
It almost sounds like the read and write permisions are wrong.  Have you tried it in kid3 or easytag??

---

### Post by p_quarles on 2008-12-05
My guess is that you are using a filesystem that doesn't handle Unix permissions well, rather than that the permissions are wrong *per se*.

How is the external drive formatted?

---

### Post by SomeGayDude on 2008-12-05
Im getting tierd.  Thanks, I missread internal.  I had the same problem when I used a HD formated with ntfs.

---

### Post by jdorenbush on 2008-12-05
> **p_quarles said:**
> My guess is that you are using a filesystem that doesn't handle Unix permissions well, rather than that the permissions are wrong *per se*.

How is the external drive formatted?

FAT32

Is that a problem?

---

### Post by p_quarles on 2008-12-05
> **jdorenbush said:**
> FAT32

Is that a problem?
It doesn't support permissions at all, so you will encounter problems depending upon how you mount the external volume. 

Unfortunately, I don't use HAL to mount USB devices ever, instead using pmount, which works fine for this kind of thing. Someone else will have to tell you how to fix up this drive so it doesn't give you permissions problems.

---

### Post by SomeGayDude on 2008-12-05
I am thinking.  If it was a permission issue, wouldn't their be an error message saying it couldn't write to the file?  I was also thinking that their are two different versions of tags (ID3v2.3.0 and ID3v2.4.0)  If both are on one file, could Rhythmbox be writing one and reading the other?

---

### Post by MarblePanther on 2008-12-05
Ex Falso is a program in the repos specifically for editing tags that works nicely
There is also gtkpod

---

### Post by p_quarles on 2008-12-05
> **SomeGayDude said:**
> I am thinking.  If it was a permission issue, wouldn't their be an error message saying it couldn't write to the file?  I was also thinking that their are two different versions of tags (ID3v2.3.0 and ID3v2.4.0)  If both are on one file, could Rhythmbox be writing one and reading the other?
Good point. Or even editing a temporary file somewhere.

I second the suggestion to try another mp3 tagging application (any of the ones listed will do) and see if perhaps this problem is unique to Rhythmbox.

---

### Post by jdorenbush on 2008-12-05
Installed Ex Falso.

Opened up one of the songs in question.

Genre displayed 'Soundtrack' (correct). However in Rhythmbox it is still 'Electronic' (incorrect). This is bizarre.

---

### Post by p_quarles on 2008-12-05
You'll likely need to update Rhythmbox's database. Be sure to do that before giving up on it. ;)

---

### Post by jdorenbush on 2008-12-05
> **p_quarles said:**
> You'll likely need to update Rhythmbox's database. Be sure to do that before giving up on it. ;)

How do I 'update' it?

---

### Post by p_quarles on 2008-12-05
I don't use Rhythmbox, so I don't know. Presumably, though, there's an option to rescan your music directories, and that's what I'm talking about.

---

### Post by MarblePanther on 2008-12-05
If you google rhythmbox rescan or anything similar, it seems people are having the same problem as you--it isn't really updating the files.  I would move to another music player if i were you.  I use exaile although audacious and a few others work nicely.

---

### Post by jdorenbush on 2008-12-05
> **MarblePanther said:**
> If you google rhythmbox rescan or anything similar, it seems people are having the same problem as you--it isn't really updating the files.  I would move to another music player if i were you.  I use exaile although audacious and a few others work nicely.

I started using Songbird, but I've been having another set of problems with that. [See this thread]("http://ubuntuforums.org/showthread.php?t=1000133"). Songbird just feels sluggish. I feel like I am using web-based player or something on the Internet.

I'll try Exaile.

---

### Post by MarblePanther on 2008-12-05
Oddly enough I stopped using songbird awhile ago for the same reason -- it never updated my music.  I don't like songbird's web integration.

Exaile works great for me though.

I suggest using that along with gtkpod if you use an ipod.

---
edit:
exaile does have an ipod plugin, but i prefer gtkpod

---

### Post by jdorenbush on 2008-12-07
> **MarblePanther said:**
> Oddly enough I stopped using songbird awhile ago for the same reason -- it never updated my music.  I don't like songbird's web integration.

Exaile works great for me though.

I suggest using that along with gtkpod if you use an ipod.

---
edit:
exaile does have an ipod plugin, but i prefer gtkpod

Okay, I installed Exaile and I like the look and feel. The only thing I don't like is that when I click on a genre, artist, album, etc. in the Collection window it doesn't automatically add to the Playlist window. I have to right click and hit add.

---

### Post by MarblePanther on 2008-12-07
All you have to do is double-click or hit enter or drag to add the selection to the playlist

No need for right-clicking

Hope this helps

---

### Post by jdorenbush on 2008-12-07
> **MarblePanther said:**
> All you have to do is double-click or hit enter or drag to add the selection to the playlist

No need for right-clicking

Hope this helps

You are right, double-click works, except for Genre. You can't double-click to add an entire genre to the Playlist. :(

---

### Post by jdorenbush on 2008-12-16
I'd still like to get to the bottom of this problem in Rhythmbox - any ideas?

---

### Post by aheckler on 2008-12-16
SomeGayDude [was very close]("http://ubuntuforums.org/showpost.php?p=6315656&postcount=8") to the actual problem. It's not a permissions thing, it's a tags thing. Rhythmbox reads APE tags first, then ID3 tags. When you try to change the tags from within Rhythmbox, it only changes the ID3 kind, so what is displayed reverts back to the APE tag a few seconds later.

You need to download an app called EasyTAG (in the repos) and remove all APE tags from your files. They should then work as expected.

---

### Post by aheckler on 2008-12-16
Actually, a simpler way to remove APE tags can be found here: [http://ubuntuforums.org/showthread.php?t=292111](http://ubuntuforums.org/showthread.php?t=292111)

---

### Post by jdorenbush on 2008-12-16
> **aheckler said:**
> Actually, a simpler way to remove APE tags can be found here: [http://ubuntuforums.org/showthread.php?t=292111](http://ubuntuforums.org/showthread.php?t=292111)

apetag won't work on 64-bit.

I don't see any options to edit/remove APE tags within  EasyTAG.

---

### Post by aheckler on 2008-12-16
Go here: [http://rarewares.org/debian/packages/unstable/](http://rarewares.org/debian/packages/unstable/)

Download this: apetag_1.7-0.1_i386.deb

You will need the package "libstdc++5" installed first, so:

```
sudo apt-get install libstdc++5
```

(There may be other dependencies, but libstdc++5 was the only one I needed.)

Then, in the directory with the apetag .deb file:

```
sudo dpkg --force-architecture -i apetag_1.7-0.1_i386.deb
```

Apetage will now be installed and functional. I just tested this on my 64-bit system, so you should be good to go.

---

### Post by jdorenbush on 2008-12-16
OK cool. Forcing it allowed it to install without any problems.

However...
```
$ apetag -i Ep 10 - Goldfrapp - Ooh La La.mp3 -m overwrite
E: could not open file
```

Also, I couldn't open my external harddrive files via apetag. I had to drag this file onto the Desktop to try and open it with apetag.

---

### Post by aheckler on 2008-12-16
If you have spaces in a filename, you have to enclose it in quotes, like this:

```
apetag -i "Ep 10 - Goldfrapp - Ooh La La.mp3" -m overwrite
```

That should work. I'm not sure about you external drive problem, that seems odd. Try either putting the path in as part of the filename, like so:

```
apetag -i "/path/to/drive/music/foler/Ep 10 - Goldfrapp - Ooh La La.mp3" -m overwrite
```

Or try changing directories to your external and running apetag from there.

```
cd /path/to/external/drive/music/folder
apetag -i "Ep 10 - Goldfrapp - Ooh La La.mp3" -m overwrite
```

Or maybe you already tried doing it those ways?

---

### Post by jdorenbush on 2008-12-17
Hmm, still getting that error - even after putting it in quotes.

---

### Post by aheckler on 2008-12-17
Try using sudo:

```
sudo apetag -i "Ep 10 - Goldfrapp - Ooh La La.mp3" -m overwrite
```

---

### Post by jdorenbush on 2008-12-21
> **aheckler said:**
> Try using sudo:

```
sudo apetag -i "Ep 10 - Goldfrapp - Ooh La La.mp3" -m overwrite
```

Same error message. Weird.

I gave up on it. I am back to Songbird - problem free. The problem only exists in Rythmbox, which sucks, because that is the media player I wanted to use. Oh well.

---

### Post by golovan on 2008-12-23
Are you absolute sure you gave the exact filename? I just tried this on some MP3's that have been driving me crazy for ages with their "changing back to wrong tag"-behaviour. All I did to make it work was cd to the exact location, sudo and then the command given above. First I got an "Cannot open" error, double checked and found that the filename was wrong, tried again, and voilá. Finished off with tagging the files "just right" in Rhythmbox.

---

### Post by jdorenbush on 2008-12-23
> **golovan said:**
> Are you absolute sure you gave the exact filename? I just tried this on some MP3's that have been driving me crazy for ages with their "changing back to wrong tag"-behaviour. All I did to make it work was cd to the exact location, sudo and then the command given above. First I got an "Cannot open" error, double checked and found that the filename was wrong, tried again, and voilá. Finished off with tagging the files "just right" in Rhythmbox.

Copied and pasted the filename. Multiple times. :(

---

### Post by golovan on 2008-12-25
ok. I tried with some other files now, and they didn't work either. some kind of "no apetag"-error (guess they don't have an apetag doh:) ). But at least the one's I overwrote earlier still holds on to their new tags. Hope you figure it out!

---

### Post by jdorenbush on 2008-12-26
> **golovan said:**
> ok. I tried with some other files now, and they didn't work either. some kind of "no apetag"-error (guess they don't have an apetag doh:) ). But at least the one's I overwrote earlier still holds on to their new tags. Hope you figure it out!

Songbird ftw. :)

---

### Post by jdorenbush on 2009-10-25
Found a bug report over here: [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/235945)

Seems as though others are experiencing. This problem is VERY annoying -- would like to fix.

---

### Post by jdorenbush on 2009-11-25
Anyone? Bump

---

### Post by jdorenbush on 2009-12-23
Now it is happening in Songbird 1.4.

I found a strange workaround in Songbird. If I edit the artist and genre tag in two different instances as well as first changing the artist and genre to a dummy name it seems to hold the changes. Even if the artist doesn't need to be edited, in order to rename the genre it seems as though I still have to follow all the workaround steps. Example:

Original Tag: Artist: Bloc Party / Genre: Alternative
1st Tag Change, change genre to dummy: Bloc Party / 1DUMMY
2nd Tag Change, change artist to dummy: 2DUMMY-Bloc Party / 1DUMMY
3rd Tag Change, change genre to correct: 2DUMMY-Bloc Party / Indie Rock
4th Tag Change, change artist back to correct: Bloc Party / Indie Rock

All that just to change the genre. Doesn't make any sense to me, but it works.

UPDATE: Okay, it gets even weirder. This workaround only works if I use a single character dummy genre, i.e. "z" or "x". If I use "xx" or anything more, it does not work.

---

