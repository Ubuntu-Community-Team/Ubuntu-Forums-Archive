---
title: "Cannot add wallpapers"
date: 2007-11-19
forum: Desktop Effects &amp; Customization
---

### Post by Mman_ on 2007-11-19
Ok. I have been fighting with gdesklets and after a long battle I decided to give up... But I'd like to have my wallpapers back!

It all started when I installed gdesklets on Gutsy 64 and got the empty window -bug.
Found a "solution" by downloading gdesklets_0.35.4-1ubuntu1_amd64.deb which "worked", but messed up my mime types.
I uninstalled the whole gdesklets mess and managed to fix my mime types by:

```

sudo update-mime-database /usr/share/mime
sudo dpkg-reconfigure shared-mime-info
killall gnome-panel
killall nautilus

```

Now my system is almost back to normal, but I can't add wallpapers anymore.
When I'm in "Change Desktop background" -window (right-click on desktop -> Change Desktop...)  and click Add -button to add some other images, the file browser dialog doesn't show any image files (tested with .jpg and .png). The only way I can see image files on the file browser, is by changing the filter to display all files. When I have selected an image and click the Open -button, the filebrowser closes, but the file I selected doesn't get into the wallpaper selection window. There's still only the default walls.

I know there has to be another way of adding wallpapers (cp to some dir), but I'm not content on settling with that. Besided this problem clearly tells that there is something wrong in my system. Wrongs should be fixed :)

Any help appreciated.

Greets

---

### Post by pieisgood4589 on 2007-11-19
You should be able to just right click a picture, then select "set as wallpaper." Try that, then post with results.

---

### Post by Mman_ on 2007-11-19
There's no such option. The only image specific options are "Resize images..." and "Rotate images..."

---

### Post by Luna.jp on 2007-11-20
Try this...

Open up the terminal, go into the folder that has the images you want to use as your background.

ie:

```
cd /usr/share/backgrounds
```

That is the default one.
Then, copy your images ( if they aren't there already ) into that folder.
```

sudo cp world.jpg /usr/share/backgrounds
```

Next, chmod it to 666 like all the others in there

```
sudo chmod 666 world.jpg
```

Now try to add. It should work.

---

