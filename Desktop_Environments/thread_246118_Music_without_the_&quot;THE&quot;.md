---
title: "Music without the &quot;THE&quot;"
date: 2006-08-28
forum: Desktop Environments
---

### Post by declaration on 2006-08-28
Hi,

I have been using Ubuntu for about 6 months now. Just have a couple of issues left,

One is-

On Windows I use iTunes, which when sorting my music alphatetically removes the "the". Lots of my music has "the" in the band name and I would like this removed when sorting alphabetically,

I am presently using Rhythmbox- does anyone knowhow to remove the "the" when sorting or can suggest some other software?

Thankyou very much in advance,

x

---

### Post by declaration on 2006-09-05
bump
anyone got any ideas?
Cheers

---

### Post by Westerberg on 2006-09-05
Not a solution but a workaround:
Remove the leading "The" from the filenames altogether, since it doesn't really add any information.
```
rename 's/[tT]he[\ \_]//' [Tt]he*

```

---

### Post by canadianwriterman on 2006-09-05
I use Rhthymbox as my main music library and player and have not figured out how to take the "The" out automatically. I just right click to Properties and take it out manually.

---

### Post by aysiu on 2006-09-05
Rhythmbox sorts on the ID3 tags of the file and not the file name, so this would be a two-step process, I think--unless you're really handy with command-line tools.

Using KRename, strip the *the* out of all the file names. Then use TagTool to rename the ID3 tags based on the file names.

---

### Post by frego on 2006-09-05
Amarok is a really nice player that will do what you ask.  ie.  "Beatles, The".  I have it running on Ubuntu 6.06.  I had to install much of KDE though I use Gnome, many extra libraries were required.  Ultimately by following the amarok installation how to at [http://amarok.kde.org/wiki/Installation_HowTo](http://amarok.kde.org/wiki/Installation_HowTo) I got it working.  It's well worth the effort.  It's the best player I've used.

---

### Post by declaration on 2006-09-05
Amarok does this by default?

I've tried amarok but I dont remember it having this option. I really dont want to have to mess around with my filenames and tags so would love it if the option existed somewhere.

I'll give it a try tomorrow. 

Cheers.

---

### Post by danhm on 2006-09-05
Amarok does it by default (and it's the best music player for linux!).

I don't think you need to do much more than a sudo apt-get install amarok to get it installed.

---

### Post by declaration on 2006-09-06
Thanks very much.

Have installed Amarok and I love it! Much much much better than iTunes imho.

---

### Post by frego on 2006-09-07
Cool!  Another Amarok convert. Using synaptic to pull in Amarok did work for me, but to get some cool scripts and extras working I did have to pull in other libraries suggested on the amarok site that the package manager didn't have dependencies on.  I wish I had kept notes on what it was.  But it wasn't too hard.  I highly recommend Amarok to all.  And it also makes tagging files quite easy.  Between Amarok and "Audio Tag Tool" I've cleaned up nearly all my MP3s in the last week.

---

