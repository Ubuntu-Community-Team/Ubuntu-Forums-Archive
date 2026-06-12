---
title: "thunderbird, kde, gtk warnings, artsdsp and WAV files"
date: 2006-09-11
forum: Desktop Environments
---

### Post by jamuir on 2006-09-11
I am using Kubuntu 6.06.1 and am having some minor problems with Thunderbird; more specifically I am observing numerous gtk warnings and .wav dat being dumped to stderr (and one time these warning ended up in my addressbook :confused: ).  The package I have installed is 

```
mozilla-thunderbird    1.5.0.5-0ubuntu0.6.06
```

When I run thunderbird from the command line, navigate to Edit \ Preferences \ General and, under the "When new messages arrive" submenu, preview my "Custom .wav file" here is what is dumped to stderr:

```
me@mybox:~$ mozilla-thunderbird
DOUBLE-CLICK: 250 --> -1 THRESHOLD: 8 --> -1
(mozilla-thunderbird-bin:5367): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `gdk_window_is_viewable (src)' failed

(mozilla-thunderbird-bin:5367): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(mozilla-thunderbird-bin:5367): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(mozilla-thunderbird-bin:5367): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(mozilla-thunderbird-bin:5367): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(mozilla-thunderbird-bin:5367): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(mozilla-thunderbird-bin:5367): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

### ...
### same sequence of seven warnings repeated approximately 10 times
### ...
/bin/sh: /usr/bin/esd: No such file or directory
/bin/sh: /usr/bin/esd: No such file or directory
RIFF.WAVEfmtdata
~~|y~Qhxvp_fofY]vgV_lh\\tlY_mj][poY[lj_Zjt][jk`Wfx`YgkcXa{aWeleZa}}cXdmg\a{fWblg[^uiX`kfYYtiX`keYZtjX`jfZYskX^jeYYqkX\hdXVmmY]ieYWmoZZig[Wkp[\ji^Ykt^\ll`Whxa[imbXdzbYfkcXb}~eZekcX`{hYdmfZ\vkZ_kh\[op\]ih^Xjs]\ij`Yhu_[ilc[gzc[hmeZc}e[flcX`}}dZejcX_{}dZdjcX_zfYdkdX^xgZdjdY]vgZdkdY\vhZckfZ\sj[cmh[]tl]cni]\rp^ank^Zms_^lk_Yju_]jk`Xhyc]ilcYe|e]gmf[b}~g\emg\^vi\cmi]^tm\bmj`_ro^`lka\ls__lk`[kua^llaZiwa^klbZgze^imdZd}g]gmg\b{i]eni^_uk]cmi_^sn]blja_qq_amlb\lt`_lka[kta`kka\kt``lkb[kua_kk`Ziwc`kk`XfwballbZgzd`mmbZh~zxvuuvwxz|}~}}~
```

Does this look familiar to any other Kubuntu users?  Note that I previously received many more gtk warnings but I eliminated those by commenting out the unnecessary "stylus", "cursor" and "eraser" devices in /etc/X11/xorg.conf .

What I really want is Thunderbird to play a .wav file when new mail arrives.  I bet this works flawlessly in Gnome...but I'm a KDE user.  I used to be able to accomplish this in KDE like so

```
me@mybox:~$ artsdsp mozilla-thunderbird
```

However, that was with an old version of artsdsp.  The current version of artsdsp (1.5.2) now checks whether its argument is an ELF binary.  If it isn't, artsdsp quits saying "artsdsp works only for binaries":

```
me@mybox:~$ artsdsp mozilla-thunderbird
artsdsp works only for binaries
```

Thunderbird seems to assume that /usr/bin/esd exists.  It tries to call esd with options from the file /etc/esound/esd.conf.  /usr/bin/esd doesn't exist in KDE.  I've tried making /usr/bin/esd a sym-links to various arts programs but no luck.

Any suggestions?  Should I submit this as a bug?  If so, any idea where to submit it to?  mozilla-thunderbird bugs aren't handled in launchpad.

-James

---

### Post by jamuir on 2006-09-12
I managed to solve most of the above problems so I thought I would report back so others might benefit.

The issue of all the GTK warnings was the result of my KDE (QT) style being applied to the Firefox and Thunderbird user-interfaces.  FF and TB are GTK application and it appears that dressing them in QT styles causes many warnings.  In fact, FF was throwing so many warnings into .xsession-errors that this file grew to about 4 MB.

It's possible that some users' home directories might get filled up by all the gtk warnings sent to .xsession-errors.

I think the gtk warnings that TB was throwing to stderr should instead be sent to .xsession-errors; this includes the WAV data.  As these errors/warnings were once piped into my addressbook (and appeared to wipe it out), I think this behaviour could be classified as a TB bug.

In any case, to stop the GTK errors you just have to tell KDE not to apply QT styles to GTK apps.  To do so, go to  System Settings / Appearance / GTK styles and fonts / GTK Styles.  Then select "Use another style" and pick one from the drop down menu.  I picked "Raleigh".  After starting a new X session the FF and TB user-interfaces look more plain, but the GTK warnings stop.

Now, getting TB to play a custom .wav file turned out to be very easy:

```
apt-get install esound
apt-get install esound-clients

```

-James

---

### Post by esaym on 2007-01-03
> **jamuir said:**
> I managed to solve most of the above problems so I thought I would report back so others might benefit.

The issue of all the GTK warnings was the result of my KDE (QT) style being applied to the Firefox and Thunderbird user-interfaces.  FF and TB are GTK application and it appears that dressing them in QT styles causes many warnings.  In fact, FF was throwing so many warnings into .xsession-errors that this file grew to about 4 MB.

It's possible that some users' home directories might get filled up by all the gtk warnings sent to .xsession-errors.

I think the gtk warnings that TB was throwing to stderr should instead be sent to .xsession-errors; this includes the WAV data.  As these errors/warnings were once piped into my addressbook (and appeared to wipe it out), I think this behaviour could be classified as a TB bug.

In any case, to stop the GTK errors you just have to tell KDE not to apply QT styles to GTK apps.  To do so, go to  System Settings / Appearance / GTK styles and fonts / GTK Styles.  Then select "Use another style" and pick one from the drop down menu.  I picked "Raleigh".  After starting a new X session the FF and TB user-interfaces look more plain, but the GTK warnings stop.

Now, getting TB to play a custom .wav file turned out to be very easy:

```
apt-get install esound
apt-get install esound-clients

```

-James


THANKS!:mrgreen: :mrgreen: :mrgreen:

---

