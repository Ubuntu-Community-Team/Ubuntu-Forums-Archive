---
title: "Changing desktop wallpaper without a GUI."
date: 2008-02-07
forum: Desktop Environments
---

### Post by cvp on 2008-02-07
I have KDE set up to change my desktop wallpaper from a long list of wallpapers every 20 minutes. That's working fine.
What I'd like, though, is some mechanism to change it to another random wallpaper if I for some reason don't like the wallpaper currently up. I know I can go back into **kcontrol** and set the settings again, but that's too far out of my way.

I figured I'd write a script that does this for me, and then set some global hotkey for it.
I found **kdesktoprc**, which lists the current wallpaper and the list of wallpapers in rotation, and wrote a very simple program called **kde_chwall**:
```
#!/usr/bin/perl

open(IN, "/home/cvp/.kde/share/config/kdesktoprc"); @lines = <IN>; close IN;

for $line (@lines) {
	next unless ($line =~ /^WallpaperList=/);
	@walls = split(/,/, $'); last; }

open(OUT, ">/home/cvp/.kde/share/config/kdesktoprc");
for $line (@lines) {
	if ($line =~ /^CurrentWallpaperName/) { $line = "CurrentWallpaperName=".$walls[int(@walls * rand)]."\n"; }
	print OUT $line; }

close OUT;

```

This does exactly what I intended - looks at the list of wallpapers I have on rotation, picks a random one, and changes the string "CurrentWallpaperName=[whatever]" to a random wallpaper.

**The Problem:** The wallpaper doesn't update. In editing **kdesktoprc**, I noticed that the file itself was being overwritten by another program every 20 minutes, so I didn't see why my own overwriting of **kdesktoprc** wouldn't work. I figure that whatever service alters **kdesktoprc** also sends some sort of "update" signal to the desktop that re-reads **kdesktoprc** to get the proper background.
Anyone know about this?

Thanks in advance!
-cvp

---

### Post by tcommbee on 2008-02-08
maybe you could use this? [http://usalug.org/phpBB2/viewtopic.php?t=9821](http://usalug.org/phpBB2/viewtopic.php?t=9821)

---

### Post by cvp on 2008-02-13
**tcommbee,**

Yes! That's exactly what I was looking for.

Thanks!

-cvp

---

