---
title: "WMV no audio with mplayer, no video with vlc"
date: 2006-02-05
forum: Desktop Environments
---

### Post by gormine on 2006-02-05
Just what the title says... I get video with no audio in mplayer and audio with no video in vlc.

edit: apparently there is video in some wmv files with vlc but not all.

---

### Post by jrib on 2006-02-05
[QUOTE=gormine]Just what the title says... I get video with no audio in mplayer and audio with no video in vlc.

edit: apparently there is video in some wmv files with vlc but not all.[/QUOTE]

install the w32codecs (see [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28w32codecs%29#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28w32codecs%29#head-fda9cc5147253891fe3047263b82d787ab025bba) ).  That should help you in mplayer.  VLC won't play the latest wmv encoding unless you recompile it.

---

### Post by gormine on 2006-02-05
[QUOTE=_jason]install the w32codecs (see [https://wiki.ubuntu.com/RestrictedFormats?highlight=%28w32codecs%29#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28w32codecs%29#head-fda9cc5147253891fe3047263b82d787ab025bba) ).  That should help you in mplayer.  VLC won't play the latest wmv encoding unless you recompile it.[/QUOTE]


Thank you. I actually already had the w32codecs but uninstalling them and reinstalling did the trick.

---

