---
title: "Nice font rendering in 8.04 Hardy"
date: 2008-05-20
forum: Desktop Environments
---

### Post by dulus on 2008-05-20
It is pretty easy, all libraries as freetype, cairo, libxft are allready patched with all that LCD-cleartype-subpixel-autohint stuff. We need just turn it on, because they are disabled by default. Just adjust symlinks in /etc/fonts/conf.d to apropriate files in /etc/fonts/conf.avail - look at left pane in mc to see what should be symlinked.

[[IMG]http://hmm.iglu.sk/~dulus/ubuntu/fonts/m03-symlinks.png[/IMG]]("http://hmm.iglu.sk/~dulus/ubuntu/fonts/03-symlinks.png")

Here you can compare default rendering to MS Windows rednering, windows fonts doesn't look good, shapes and size are wrong.

[[IMG]http://hmm.iglu.sk/~dulus/ubuntu/fonts/m01-original-ugly.png[/IMG]]("http://hmm.iglu.sk/~dulus/ubuntu/fonts/01-original-ugly.png")

After symlinking correct settings they now apear very close to windows rendering.

[[IMG]http://hmm.iglu.sk/~dulus/ubuntu/fonts/m04-tuned-nice.png[/IMG]]("http://hmm.iglu.sk/~dulus/ubuntu/fonts/04-tuned-nice.png")

Another screenshot with font settings window as I like it.

[[IMG]http://hmm.iglu.sk/~dulus/ubuntu/fonts/m02-settings.png[/IMG][HTML][/HTML]]("http://hmm.iglu.sk/~dulus/ubuntu/fonts/02-settings.png")

---

### Post by sdennie on 2008-05-20
Font settings are very subjective.  I do think your fonts look nice but it's impossible to say that particular font settings are, "The finest font settings available to humanity".  I like the inclusion of contrasting screenshots though.  Like going to an optometrist, it's difficult to decide whether 1 or 2 is better without seeing them side by side.

---

### Post by bekirserifoglu on 2008-05-22
hey i have been looking for this for a long time. can you explain it more clearly? How we should do do it?

---

### Post by bullon on 2008-05-22
> **bekirserifoglu said:**
> can you explain it more clearly? How we should do do it?

yes please!

---

### Post by dulus on 2008-05-23
Ok, so more descriptive guide for beginers is here. It assumes you are logged in terminal as root, if not type **sudo** before each **rm** and **ln** commands. It makes also backup of /etc/fonts directory if something goes wrong.


```
root@hardy:~# cd /etc/fonts
root@hardy:/etc/fonts# tar czf /tmp/etc-fonts-backup.tgz * 
root@hardy:/etc/fonts# cd conf.d
root@hardy:/etc/fonts/conf.d# rm 10-antialias.conf 10-hinting-medium.conf 10-no-sub-pixel.conf 70-no-bitmaps.conf
root@hardy:/etc/fonts/conf.d# ln -s ../conf.avail/10-autohint.conf 10-autohint.conf
root@hardy:/etc/fonts/conf.d# ln -s ../conf.avail/10-hinting-full.conf 10-hinting-full.conf
root@hardy:/etc/fonts/conf.d# ln -s ../conf.avail/10-sub-pixel-rgb.conf 10-sub-pixel-rgb.conf
root@hardy:/etc/fonts/conf.d# ln -s ../conf.avail/70-yes-bitmaps.conf 70-yes-bitmaps.conf
```

Now just CTRL+ALT+Backspace or reboot, and go to System -> Preferences -> Appearance, click Fonts tab, click Details and set properties as you see on 4th screenshot. Now you should see changes.

---

### Post by kerry_s on 2008-05-23
basically your doing manually what-> sudo dpkg-reconfigure fontconfig-config
does.

i choose:

autohinter
automatic
yes

in most cases you want "no" for bitmaps, but i'm using it for other languages, so i made a ~/.fonts.conf file to straighten out the crappy ms fonts.

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Helvetica</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Verdana</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Arial</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Lucida</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Sans</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Times</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Roman</string>
 </edit>
</match>

<match target="pattern" >
 <test name="family" qual="any" >
 <string>Courier</string>
 </test>
 <edit mode="assign" name="family" >
 <string>Nimbus Mono</string>
 </edit>
</match>

</fontconfig>

```

---

### Post by VMC on 2008-05-23
> **kerry_s said:**
> basically your doing manually what-> sudo dpkg-reconfigure fontconfig-config
does.
i choose:
autohinter
automatic
yes

in most cases you want "no" for bitmaps, but i'm using it for other languages, so i made a ~/.fonts.conf file to straighten out the crappy ms fonts.
...

Thanks for this. I wasn't aware of this handy utility. You said "crappy ms fonts". I'm guessing you mean the ms emulation fonts. Because for me in Windows I prefer their fonts over most of what I've seen in Linux. I tried to copy, for example, Opera font names from Windows to the equivilent Linux names. All to no avail. Maybe now this utility will come to my rescue. Ubuntu default fonts have at least the best of the bunch, but I prefer to fine tune. I thought all along it was Windows True Type fonts that were the issue.

---

### Post by Twilight in Zero on 2008-07-09
Sorry to revive an old post, but I'm having problems with autohinting. I have a thread posted in General, but it seems threads there go to the void within an hour. Posting here might be better.

Your Sans looks incredibly awesome. But mine doesn't. I followed this howto perfectly, but my Sans looks like [http://launchpadlibrarian.net/12505687/Screenshot.png](http://launchpadlibrarian.net/12505687/Screenshot.png) (see bottom window) instead. Autohinting made Sans look bigger, and certain characters, such as an f and i right next to each other, are sized smaller than the rest of the font. Is there any way I can fix this? I found that second screenshot at [https://bugs.edge.launchpad.net/ubun...or/+bug/199557](https://bugs.edge.launchpad.net/ubun...or/+bug/199557).

Any and all help is greatly appreciated.

---

### Post by dulus on 2008-07-16
> **Twilight in Zero said:**
> Autohinting made Sans look bigger, and certain characters, such as an f and i right next to each other, are sized smaller than the rest of the font. Is there any way I can fix this?

Mine font looks smaller, i have Sans 9 in Application font. Try with this size and compare with screenshots. Also DPI settings can change a lot, I use 96.

---

### Post by Twilight in Zero on 2008-08-04
Yeah, Sans 9 did it for me. I compared the appearance of my fonts to yours when I toggled it on, and everything looked right. Thank you.

It's so weird though. With the bytecode hinter, there is little difference between Sans 9 and Sans 10, except for the apparent spacing in lists and such. But with the autohinter, the difference is dramatic.

---

### Post by ESM on 2008-10-22
[QUOTE=kerry_s;5024418]basically your doing manually what-> sudo dpkg-reconfigure fontconfig-config
does.

i choose:

autohinter
automatic
yes

in most cases you want "no" for bitmaps, but i'm using it for other languages, so i made a ~/.fonts.conf file to straighten out the crappy ms fonts.
[/quote}

Thanks man, this made my Ubuntu 8.10 a lot nicer! Wow....

---

### Post by Ledger on 2008-12-09
Mac fonts with the normal Ubuntu 8.10 looks a hole lot better than this :p

---

### Post by dowoshek on 2009-02-12
Can we make it work not only in Gnome but also in Fluxbox (or any other WM)?

----

Have the answer already :)
What we need is to run gnome-seetings-daemon. So, in Fluxbox we have to modify ~/.fluxbox/startup file and add:
```
gnome-settings-daemon &
```
just before
```
exec /usr/bin/fluxbox
```

And then... damn, it rocks! :) Beatiful Fluxbox, like never before :)

---

### Post by techflat on 2009-02-26
Hi there,

I've read this post and tried the "dpkg-reconfigure fontconfig-config" method. Howevere, I have a couple of questions.

1) Is there a difference between creating symlinks in [post #1]("http://ubuntuforums.org/showpost.php?p=5000192&postcount=1") and trying the dpkg method in [post #6]("http://ubuntuforums.org/showpost.php?p=5024418&postcount=6")?

2) Even after you do either methods do yo have to go to the font settings window and tune it up? (Like suggested in the last image of [post #1]("http://ubuntuforums.org/showpost.php?p=5000192&postcount=1"))

3) If the las question's answer is yes, what's the difference between using the font settings window and doing any of the methods proposed here?


Cheers

---

