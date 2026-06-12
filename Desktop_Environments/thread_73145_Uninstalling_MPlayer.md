---
title: "Uninstalling MPlayer"
date: 2005-10-08
forum: Desktop Environments
---

### Post by DeathOnJuice on 2005-10-08
I just installed MPlayer so I could play .wmv files. Like a few other programs, I compiled it from source with no problems. Then, I remembered that I forgot to put the codecs in the correct directory, where they have to be BEFORE the install. I've never uninstalled a program that I compiled from source, but I've heard about going into the directory you downloaded and issuing a "make clean" command, so I tried that. All it did was give this output: **"rm -f *.o *~  codecs.conf.h"**. I know that's a command, but should I issue it? Would that uninstall it? Also, what does the *~ part do? I know that it would have to be ~/* for it to delete everything in my home folder, but I'm still kind of worried about that home sign. So, can anyone help me uninstall this so I can reinstall it with the codecs?

---

### Post by ow50 on 2005-10-08
I believe the correct  command would have been "make uninstall", while "make clean" removes the files generated during "make" phase in the **source directory**.

~ is a common suffix for temporary- and backup files.

---

### Post by Wolki on 2005-10-08
To prevent such issues in the future, install checkinstall; then instaed of doing "sudo make install" do "sudo checkinstall". It will create a .deb package and install that, so you can uninstall it with synaptic later.

---

### Post by ow50 on 2005-10-08
With MPlayer source code you can do proper Debian packages as well, since MPlayer ships with the "debian" directory. Just run "dpkg-buildpackage -rfakeroot -uc" in the source directory. If you want to change the configure flags, edit the file debian/rules.

---

### Post by DeathOnJuice on 2005-10-08
OK, make uninstall didn't seem to work either, so I just downloaded the codecs, put them in the correct folder, did ./configure, make, and make install again. All seemed to be going well, so I tried to play the wmv file. The screen went blank, so I hardbooted my computer (NOT a proper shutdown). Now, when I try to use MPlayer on any video file, it acts like it's working (it has the little status thing going), but there's one problem: it doesn't show the video or have sound. The sound part is understandable, because most programs can't open the sound device (/dev/dsp) on my computer for some reason, but I don't get the video part. In any case, I got the codecs working for xine (totem, vlc, mplayer, and xmms still don't work), but I'd still like to know how to get MPlayer working.

---

### Post by DeathOnJuice on 2005-10-09
This post is just being made to bring this topic back to the top of the list.

---

### Post by Wolki on 2005-10-09
Do you use esd? If so, did you enable esd output in the mplayer preferences?

---

### Post by DeathOnJuice on 2005-10-09
How would I go about doing that?

---

### Post by Wolki on 2005-10-09
[QUOTE=DeathOnJuice]How would I go about doing that?[/QUOTE]

um, i don't have mplayer installed right now, so this is from memory... Start gmplayer. Go to preferences, there should be a tab that contains sound options. There is a box where you can choose different audio outputs. You should be able to choose esd (if not, you have to compile it with esd support. check the mplayer documentation for that).

Try the following: execute "killall esd", then start mplayer and see it it works.

---

### Post by DeathOnJuice on 2005-10-11
Thank you so much about the "killall esd" command; now my sound works! One question, though; will "esd" start again when I restart, and if it does, how can I keep it from starting?

OK, when I try to run gmplayer, it says that it doesn't exist. So now, mplayer's sound is working, but the video still doesn't pop up.

---

### Post by Wolki on 2005-10-11
[QUOTE=DeathOnJuice]Thank you so much about the "killall esd" command; now my sound works! One question, though; will "esd" start again when I restart, and if it does, how can I keep it from starting?

OK, when I try to run gmplayer, it says that it doesn't exist. So now, mplayer's sound is working, but the video still doesn't pop up.[/QUOTE]

hm, you compiled it youself. Did you compile it with GUI support?
The problem with the video is probably similar, i guess it's trying tu use an output that's not available.

mplayer docs are here: [http://mplayerhq.hu/DOCS/HTML/en/index.html](http://mplayerhq.hu/DOCS/HTML/en/index.html)

Yes, esd will start again. It makes sure you're able to hear more than one sound, so I'm not sure you really want to disable it permanently. These issues should finally be resolved with Breezy, though you will probably still need to configure applications to use esd if you want multiple sounds. Try starting mplayer with the "-ao esd" option to enable esd support in mplayer - of course with esd running.

---

