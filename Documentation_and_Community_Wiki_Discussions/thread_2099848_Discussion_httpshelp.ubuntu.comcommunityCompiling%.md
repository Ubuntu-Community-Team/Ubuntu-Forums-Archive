---
title: "Discussion: https://help.ubuntu.com/community/Compiling%20MPlayer"
date: 2012-12-30
forum: Documentation and Community Wiki Discussions
---

### Post by andrew.46 on 2012-12-30
This thread is intended for discussion of the guide:

Compiling MPlayer
[https://help.ubuntu.com/community/Compiling%20MPlayer](https://help.ubuntu.com/community/Compiling%20MPlayer)

Please feel free to discuss any positive things about the guide here and also free to step in and fix any errors you can see. It is a wiki and thus community driver and edited...

---

### Post by andrew.46 on 2012-12-31
To kick this new thread off I have added in a short explanatory note on the wiki concerning bluray playback with MPlayer. Considering losing the MPlayer 2 section as well, the wiki page was designed to build the original MPlayer not the fork and quite frankly I don't even use MPlayer 2. Perhaps someone will keep this section up to date, mostly it is my work I guess...

---

### Post by aleblanc on 2013-03-12
On Ubuntu 12.04 I think the prefix should be /usr instead of /usr/local
Hence I use the following command for compilation:

```
cd $HOME/mplayer_build && \
svn checkout svn://svn.mplayerhq.hu/mplayer/trunk mplayer && \
cd mplayer && \
PKG_CONFIG_PATH="$HOME/mplayer_build/mplayer_deps/usr/lib/pkgconfig" \
./configure \
           --extra-cflags="-I$HOME/mplayer_build/mplayer_deps/usr/include" \
           --extra-ldflags="-L$HOME/mplayer_build/mplayer_deps/usr/lib" \
           --confdir=/etc/mplayer \
           --prefix=/usr && \
make -j 2 && make html-chunked && \
mkdir -vp doc-pak && \
cp -v DOCS/HTML/*/* AUTHORS Changelog LICENSE README doc-pak && \
sudo checkinstall -D --install=yes --fstrans=no --pakdir "$HOME/mplayer_build" \
   --pkgname mplayer --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default \
   --pkgversion "2:1.0~svn$(LC_ALL=C svn info 2> /dev/null | \
     grep Revision | cut -d' ' -f2)" --provides "mplayer,mencoder" && \
make distclean && sudo ldconfig

```

---

### Post by andrew.46 on 2013-03-12
I guess it depends how you want to organise your system, good to see the guide being modified to suit your needs!

---

### Post by adlin5000 on 2013-06-16
Just a heads-up, libggi-target-fbdev has been deleted from 13.04. Still compiled just fine without it. Will let you know if I have any playback problems. Also checkinstall fails saying rst2man missing. Installing python-docutils (along with a few other it recommends) fixes it.

Next, is there a way to install mplayer and mplayer2 alongside each other? That way you would only have to change the executable in the options to switch back and forth.

Also, I'd keep the mplayer2 section in there for now. Last time I checked, which was a while ago so things may have changed, mplayer2 was one of the only players on linux that could handle 10bit encodes. 

Lastly, thanks for all the work you have done for so long on this.

---

### Post by andrew.46 on 2013-06-17
Thanks for looking at the wiki! I confess that the main MPlayer action has moved back to the Tutorials section of these Forums:

Howto: Build the svn MPlayer under the latest release version of Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2149564](http://ubuntuforums.org/showthread.php?t=2149564)

where a 13.04 version is in place. Not sure of the fate of this wiki page now...

---

