---
title: "Thumbnailer chose a spoiler."
date: 2009-04-06
forum: General Help
---

### Post by brownbat on 2009-04-06
Is there any way to veto gnome-thumbnailer's frame selection?

Usually it's quite good at picking a memorable frame, but for this film or television show it picked a frame where a major character takes a bullet to the forehead.

I don't want to turn off thumbnailing, it's usually quite impressive. This was just uncanny.

Maybe I can run gnome-video-thumbnailer on the file and just change an option a bit. I know the gnome-video-thumbnailer has an -l (lowercase L) switch to "not limit the thumbnailing time to 30 seconds." That might do it.

But I seem to be getting the usage wrong on gnome-video-thumbnailer, because it just keeps spitting back help information when I try to run it on the file.

```
gnome-video-thumbnailer -s 128 '/home/thomas/Desktop/Some Show s01e01.avi'

```

And I guess I would need to rename the file to some hash key, and move it to a hidden directory?

1. Can thumbnail replacement be done? 
2. If so, am I heading the right direction by trying to just change a switch on gnome-video-thumbnailer? Maybe there's an easier way, or maybe this won't really work?
3. If not, what command should I use to make thumbnailer do this thing?

---

### Post by Brucevdk on 2009-04-17
> **brownbat said:**
> Usually it's quite good at picking a memorable frame, but for this film or television show it picked a frame where a major character takes a bullet to the forehead.

Ouch!

> **brownbat said:**
> Is there any way to veto gnome-thumbnailer's frame selection?

I haven't actually looked into this very much but it looks like you can edit the options for the thumbnailer using gconf-editor (search for thumbnailer using Edit->Find). Also the way thumbnailers work is indeed by hashing (MD5) the entire URI for the file and placing it somewhere in ~/.thumbnails. See the [Freedesktop.org thumbnail specification](http://jens.triq.net/thumbnail-spec/thumbsave.html).

---

